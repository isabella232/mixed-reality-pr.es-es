---
ms.openlocfilehash: 555360092a65b80a1298eb779736b29360f8c6e13bd1834994f316043843b47a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198422"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>Las API estándar de WinRT

La manera más común y fácil de usar WinRT es llamar a métodos desde WinSDK. Para ello, abra el archivo YourModule.Build.cs y agregue las líneas siguientes:

```csharp
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // These parameters are mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string[] { "shlwapi.lib", "runtimeobject.lib" });
    PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir,        
                                        "Include", 
                                        Target.WindowsPlatform.WindowsSdkVersion, 
                                        "cppwinrt"));
}
```

A continuación, debe agregar los siguientes encabezados de WinRT: 

```cpp
#if (PLATFORM_WINDOWS || PLATFORM_HOLOLENS) 
//Before writing any code, you need to disable common warnings in WinRT headers
#pragma warning(disable : 5205 4265 4268 4946)

#include "Windows/AllowWindowsPlatformTypes.h"
#include "Windows/AllowWindowsPlatformAtomics.h"
#include "Windows/PreWindowsApi.h"

#include <unknwn.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Perception.Spatial.h>
#include <winrt/Windows.Foundation.Collections.h>

#include "Windows/PostWindowsApi.h"
#include "Windows/HideWindowsPlatformAtomics.h"
#include "Windows/HideWindowsPlatformTypes.h"
#endif
```

El código de WinRT solo se puede compilar en las plataformas Win64 y HoloLens, por lo que la instrucción if impide que las bibliotecas de WinRT se incluyan en otras plataformas. se agregó unknwn.h para tener la interfaz IUnknown. 


## <a name="winrt-from-a-nuget-package"></a>WinRT desde un NuGet paquete

Es un poco más complicado si necesita agregar un paquete NuGet compatibilidad con WinRT. En este caso, Visual Studio realizar prácticamente todo el trabajo, pero el sistema de compilación de Unreal no puede hacerlo. Afortunadamente, no es demasiado difícil. A continuación se muestra un ejemplo de cómo descargar el paquete Microsoft.MixedReality.QR. Puede reemplazarlo por otro, solo tiene que asegurarse de no perder el archivo winmd y copiar el archivo DLL correcto. 

Windows El sistema operativo controla los archivos DLL del SDK de la sección anterior. NuGet los archivos DLL de debe administrarse mediante el código del módulo. Se recomienda agregar código para descargarlos, copiarlos en la carpeta de archivos binarios y cargarlos en la memoria del proceso al iniciar el módulo.

En el primer paso, debe agregar un packages.config ( en https://docs.microsoft.com/nuget/reference/packages-config) la carpeta raíz del módulo. Allí debe agregar todos los paquetes que quiera descargar, incluidas todas sus dependencias. Aquí he agregado Microsoft.MixedReality.QR como carga principal y otros dos como dependencias de ella. El formato de ese archivo es el mismo que en Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Ahora puede descargar el NuGet, los paquetes necesarios o consulte la documentación NuGet [.](/nuget/consume-packages/install-use-packages-nuget-cli)

Abra YourModule.Build.cs y agregue el código siguiente:

```csharp
// WinRT with Nuget support
if (Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.AddRange(new string [] { "shlwapi.lib", "runtimeobject.lib" });

    // prepare everything for nuget
    string MyModuleName = GetType().Name;
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    ExternalDependencies.Add("packages.config");

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if (!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
            // we aren't focusing on a specific nuget version, we can use any of them but the latest one is preferable
            myWebClient.DownloadFile(@"https://dist.nuget.org/win-x86-commandline/latest/nuget.exe", NugetExe);
        }
    }

    // run nuget to update the packages
    {
        var StartInfo = new System.Diagnostics.ProcessStartInfo(NugetExe, string.Format("install \"{0}\" -OutputDirectory \"{1}\"", Path.Combine(ModuleDirectory, "packages.config"), NugetFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get nuget packages.  See log for details.");
        }
    }

    // get list of the installed packages, that's needed because the code should get particular versions of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] { '\r', '\n' });

    // winmd files of the packages
    List<string> WinMDFiles = new List<string>();

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        string WinMDFile = Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd");
        SafeCopy(WinMDFile, Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())),
            Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        //add winmd file to the list for further processing using cppwinrt.exe
        WinMDFiles.Add(WinMDFile);
    }

    if (Target.Platform == UnrealTargetPlatform.Win64)
    {
        // Microsoft.VCRTForwarders.140 is needed to run WinRT dlls in Win64 platforms
        string VCRTForwardersPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.VCRTForwarders.140"));
        if (!string.IsNullOrEmpty(VCRTForwardersPackage))
        {
            string VCRTForwardersName = VCRTForwardersPackage.Replace(" ", ".");
            foreach (var Dll in Directory.EnumerateFiles(Path.Combine(NugetFolder, VCRTForwardersName, "runtimes/win10-x64/native/release"), "*_app.dll"))
            {
                string newDll = Path.Combine(BinariesFolder, Path.GetFileName(Dll));
                SafeCopy(Dll, newDll);
                RuntimeDependencies.Add(newDll);
            }
        }
    }

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if (!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach (var winmd in WinMDFiles)
        {
            WinMDFilesStringbuilder.Append(" -input \"");
            WinMDFilesStringbuilder.Append(winmd);
            WinMDFilesStringbuilder.Append("\"");
        }

        // generate winrt headers and add them into include paths
        var StartInfo = new System.Diagnostics.ProcessStartInfo(CppWinRTExe, string.Format("{0} -input \"{1}\" -output \"{2}\"", WinMDFilesStringbuilder, Target.WindowsPlatform.WindowsSdkVersion, CppWinRTFolder));
        StartInfo.UseShellExecute = false;
        StartInfo.CreateNoWindow = true;
        var ExitCode = Utils.RunLocalProcessAndPrintfOutput(StartInfo);
        if (ExitCode < 0)
        {
            throw new BuildException("Failed to get generate WinRT headers.  See log for details.");
        }

        PrivateIncludePaths.Add(CppWinRTFolder);
    }
    else
    {
        // fall back to default WinSDK headers if no winrt package in our list
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }
}
```

Deberá definir el método SafeCopy de la siguiente manera:

```csharp
private void SafeCopy(string source, string destination)
{
    if(!File.Exists(source))
    {
        Log.TraceError("Class {0} can't find {1} file for copying", this.GetType().Name, source);
        return;
    }

    try
    {
        File.Copy(source, destination, true);
    }
    catch(IOException ex)
    {
        Log.TraceWarning("Failed to copy {0} to {1} with exception: {2}", source, destination, ex.Message);
        if (!File.Exists(destination))
        {
            Log.TraceError("Destination file {0} does not exist", destination);
            return;
        }

        Log.TraceWarning("Destination file {0} already existed and is probably in use.  The old file will be used for the runtime dependency.  This may happen when packaging a Win64 exe from the editor.", destination);
    }
}
```

NuGet Los archivos DLL deben cargarse manualmente en la memoria de proceso de Win32; Se recomienda agregar la carga manual al método de inicio del módulo:

```cpp
void StartupModule() override
{
#if PLATFORM_WINDOWS
    const FString LibrariesDir = FPaths::ProjectPluginsDir() / "MyModule" / THIRDPARTY_BINARY_SUBFOLDER;
    FPlatformProcess::PushDllDirectory(*LibrariesDir);

    const FString DllName = "Microsoft.MixedReality.QR.dll";
    if (!FPlatformProcess::GetDllHandle(*DllName))
    {
        UE_LOG(LogHMD, Warning, TEXT("Dll \'%s\' can't be loaded from \'%s\'"), *DllName, *LibrariesDir);
    }

    FPlatformProcess::PopDllDirectory(*LibrariesDir);
#endif
}
```

Por último, puede incluir encabezados WinRT en el código como se describe en la sección anterior.

# <a name="425"></a>[4.25](#tab/425)

Unreal no compila código winRT de forma nativa en la versión 4.25, por lo que es su trabajo compilar un binario independiente que el sistema de compilación de Unreal pueda consumir. 

## <a name="objectives"></a>Objetivos

- Crear un archivo DLL Windows universal que abra un archivoSaveDialogue
- Vincular ese archivo DLL a un proyecto de juego de Unreal
- Guardar un archivo en el HoloLens de un plano técnico de Unreal mediante el nuevo archivo DLL

## <a name="getting-started"></a>Introducción

1. Compruebe que tiene todas las [herramientas necesarias](../tutorials/unreal-uxt-ch1.md) instaladas.
2. [Cree un nuevo proyecto de Unreal y](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) asízclalo **Consumewinrt.**
3. Habilitación de [los complementos necesarios](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para HoloLens desarrollo
4. [Configuración para la implementación](../tutorials/unreal-uxt-ch6.md) en un dispositivo o emulador

## <a name="creating-a-winrt-dll"></a>Creación de un archivo DLL de WinRT 

1. Abra un nuevo Visual Studio proyecto y cree un proyecto **DLL (Universal Windows)** en el mismo directorio que el archivo **uproject** del juego de Unreal. 

![Creación de un archivo DLL](../images/unreal-winrt-img-01.png)

2. Asigne al proyecto el nombre **HoloLensWinrtDLL** y establezca la ubicación como subdirectorio **ThirdParty** en el archivo uproject del juego de Unreal. 
    * Seleccione **Colocar solución y proyecto en el mismo directorio para** simplificar la búsqueda de rutas de acceso más adelante. 

![Configuración del archivo DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Una vez compilado el nuevo proyecto, preste especial atención a los archivos de encabezado y cpp en blanco, **denominados HoloLensWinrtDLL.cpp** y **HoloLensWinrtDLL.h,** respectivamente. El encabezado es el archivo de incluir que usa el archivo DLL en Unreal, mientras que cpp contiene el cuerpo de las funciones que exporte e incluye cualquier código WinRT que Unreal no podría compilar de otro modo. 

3. Antes de agregar código, debe actualizar las propiedades del proyecto para asegurarse de que el código WinRT que necesita puede compilar: 
    * Haga clic con el botón derecho en el proyecto HoloLensWinrtDLL y seleccione **propiedades.**  
    * Cambie la lista **desplegable Configuración** a Todas **las configuraciones** y la **lista desplegable** Plataforma a Todas **las plataformas.**  
    * En **Propiedades de configuración> C/C++> Todas las opciones**:
        * Agregue **await** a **Opciones adicionales** para asegurarse de que podemos esperar en tareas asincrónicas.  
        * Cambie **C++ Language Standard** a ISO **C++17 Standard (/std:c++17)** para incluir cualquier código WinRT

![Actualización de las propiedades del proyecto](../images/unreal-winrt-img-03.png)

El proyecto está listo para actualizar el código fuente del archivo DLL con código WinRT que abre un cuadro de diálogo de archivo y guarda un archivo en el HoloLens disco.  

## <a name="adding-the-dll-code"></a>Agregar el código DLL

1. Abra **HoloLensWinrtDLL.h** y agregue una función exportada dll para que Unreal la consuma: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Abra **HoloLensWinrtDLL.cpp y** agregue todos los encabezados que la clase usará:  

```cpp
#include "pch.h"
#include "HoloLensWinrtDLL.h"

#include <winrt/Windows.Storage.h>
#include <winrt/Windows.Storage.Streams.h>
#include <winrt/Windows.Storage.Pickers.h>
#include <winrt/Windows.Foundation.h>
#include <winrt/Windows.Foundation.Collections.h>

#include <string>
#include <vector>
#include <thread>
```

> [!NOTE]
> Todo el código WinRT se almacena en **HoloLensWinrtDLL.cpp,** por lo que Unreal no intenta incluir ningún código WinRT al hacer referencia al encabezado. 

3. Todavía en **HoloLensWinrtDLL.cpp,** agregue un cuerpo de función para OpenFileDialogue() y todo el código admitido: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Agregue una clase SaveGameManager a **HoloLensWinrtDLL.cpp** para controlar el cuadro de diálogo de archivo y guardar el archivo: 

```cpp
class SaveGameManager
{
public:
    SaveGameManager()
    {
    }

    ~SaveGameManager()
    {
        // Wait for currently running thread to complete before terminating.
        if(m_thread.joinable())
        {
            m_thread.join();
        }
    }

    void SaveGame()
    {
        OpenFileDialogueAction();
    }

private:
    winrt::Windows::Storage::StorageFile m_file = winrt::Windows::Storage::StorageFile(nullptr);
    std::thread m_thread;

    winrt::Windows::Foundation::IAsyncAction OpenFileDialogueAction()
    {
        std::vector<winrt::hstring> extensions;
        extensions.push_back(L".txt");

        auto picker = winrt::Windows::Storage::Pickers::FileSavePicker();

        // FileSavePicker needs a file type to open without errors.
        picker.FileTypeChoices().Insert(L"Plain Text",
                                        winrt::single_threaded_vector<winrt::hstring>(
                                        std::move(extensions)));

        // Opening the FilePicker must be done on the Game UI thread.
        // Any other IAsyncOperations should be done on a background thread.
        m_file = co_await picker.PickSaveFileAsync();

        if(m_file)
        {
            // Unreal's game thread is an STA, async tasks need to run on
            // a background MTA thread, or waiting on them will deadlock.    
            std::thread thread([this]() { RunThread(); });
            m_thread = std::move(thread);
        }
    }

    void RunThread()
    {
        // Ensure this thread is an MTA
        winrt::init_apartment();
        Run().get();
    }

    winrt::Windows::Foundation::IAsyncAction Run()
    {
        co_await winrt::Windows::Storage::FileIO::WriteTextAsync(
                m_file, L"Hello WinRT");
    }
};
```

5. Compile la solución para **Release > ARM64** para compilar el archivo DLL en el directorio secundario ARM64/Release/HoloLensWinrtDLL desde la solución DLL. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Adición del binario de WinRT a Unreal 
La vinculación y el uso de un archivo DLL en Unreal requiere un proyecto de C++. Si usa un proyecto de Blueprint, se puede convertir fácilmente en un proyecto de C++ agregando una clase de C++:  

1. En el editor de Unreal, abra **File > New C++ Class...** (Nueva clase de C++). y cree un **nuevo actor** denominado **WinrtActor** para ejecutar el código en el archivo DLL: 

![Creación de un nuevo actor](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Ahora se ha creado una solución en el mismo directorio que el archivo uproject junto con un nuevo script de compilación denominado Source/ConsumeWinRT/ConsumeWinRT.Build.cs.

2. Abra la solución, busque la **carpeta Games/ConsumeWinRT/Source/ConsumeWinRT** y **abra ConsumeWinRT.build.cs**:

![Apertura del archivo ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Vinculación del archivo DLL
1. En **ConsumeWinRT.build.cs,** agregue una propiedad para buscar la ruta de acceso de include para el archivo DLL (el directorio que contiene HoloLensWinrtDLL.h). El archivo DLL se encuentra en un directorio secundario a la ruta de acceso de include, por lo que esta propiedad se usará como directorio raíz binario:

```cs
using System.IO;

public class ConsumeWinRT : ModuleRules
{
    private string WinrtIncPath
    {
        get 
        {
            string ModulePath = Path.GetDirectoryName(
                   RulesCompiler.GetFileNameFromType(this.GetType()));

            // Third party directory is at the project root,
            // which is two directories up from the game .exe (Binaries/HoloLens)
            return Path.GetFullPath(
                   Path.Combine(ModulePath,
                   "../../ThirdParty/HoloLensWinrtDLL"));
        }
    }
}
```

2. En el constructor de clase, agregue el código siguiente para actualizar la ruta de acceso de include, vincular la nueva biblioteca y retrasar la carga y copiar el archivo DLL en la ubicación appx empaquetada:

```cs
public ConsumeWinRT(ReadOnlyTargetRules target) : base(Target)
{
    // This is the directory the DLL's include header is in.
    PublicIncludePaths.Add(WinrtIncPath);

    // The code in HoloLensWinrtDLL will only work in a Windows Store app.
    // Only link these binaries for HoloLens.
    // Similar code can be written for desktop and similarly linked 
    // to use the same features when using Holographic Remoting.
    if(Target.Platform == UnrealTargetPlatform.HoloLens)
    {
        // Link the lib
        PublicAdditionalLibraries.Add(Path.Combine(
              WinrtIncPath, "ARM64", "Release",
              "HoloLensWinrtDLL","HoloLensWinrtDLL.lib"));

        string winrtDLL = "HoloLensWinrtDLL.dll";
        // Mark the dll to be DelayLoaded
        PublicDelayLoadDLLs.Add(winrtDLL);
        // RuntimeDependencies are included in packaged builds.
        RuntimeDependencies.Add(Path.Combine(WinrtIncPath,
                "ARM64", "Release", "HoloLensWinrtDLL", winrtDLL));
    }

    // Preserve the original code in build.cs below:
}
```

3. Abra **WinrtActor.h y** agregue una definición de función, a la que llamará un plano técnico: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Abra **WinrtActor.cpp y** actualice BeginPlay para cargar el archivo DLL: 

```cpp
void AWinrtActor::BeginPlay()
{
    Super::BeginPlay();

    // Gets path to DLL location
    const FString BinDir = FPaths::ProjectDir() / 
        "ThirdParty" / "HoloLensWinrtDLL" / 
        "arm64" / "Release" / "HoloLensWinrtDLL";

    // Loads DLL into application
    void * dllHandle = FPlatformProcess::GetDllHandle(
        *(BinDir / "HoloLensWinrtDLL.dll"));
}

void AWinrtActor::OpenFileDialogue()
{
#if PLATFORM_HOLOLENS
    HoloLensWinrtDLL::OpenFileDialogue();
#endif
}
``` 

>[!CAUTION]
> El archivo DLL debe cargarse antes de llamar a cualquiera de sus funciones.

### <a name="building-the-game"></a>Creación del juego
1. Compile la solución de juego para iniciar el editor de Unreal abierto al proyecto de juego: 
    * En la **pestaña Colocar actores,** busque el **nuevo WinrtActor** y arrástrelo a la escena. 
    * Abra el plano técnico de nivel para ejecutar la función a la que se puede llamar en **WinrtActor.** 

![Colocación de WinrtActor en la escena](../images/unreal-winrt-img-06.png)

2. En **World Outliner**, busque **el windrtActor** que se ha eliminado previamente en la escena y arrástrelo al plano técnico de nivel: 

![Arrastrar WinrtActor al plano técnico de nivel](../images/unreal-winrt-img-07.png)

3. En el plano técnico de nivel, arrastre el nodo de salida desde WinrtActor, busque **Abrir** diálogo de archivo y, a continuación, enruta el nodo desde cualquier entrada del usuario.  En este caso, se llama al diálogo Abrir archivo desde un evento de voz: 

![Configuración de nodos en el plano técnico de nivel](../images/unreal-winrt-img-08.png)

4. [Empaquete este juego HoloLens,](../tutorials/unreal-uxt-ch6.md)impleméntelo y ejecute.  

Cuando Unreal llama a OpenFileDialogue, se abre un cuadro de diálogo de archivo en HoloLens que solicita un nombre .txt archivo.  Una vez guardado el archivo, vaya a la pestaña **Explorador de** archivos del portal del dispositivo para ver el contenido "Hello WinRT". 

## <a name="summary"></a>Resumen 

Le recomendamos que use este tutorial como punto de partida para consumir código WinRT en Unreal cuando necesite guardar archivos en el disco de HoloLens con el mismo cuadro de diálogo de archivo que Windows.  El mismo proceso se aplica a la exportación de funciones adicionales desde el encabezado HoloLensWinrtDLL y se usa en Unreal.  Preste especial atención al código DLL que espera en código de WinRT asincrónico en un subproceso MTA en segundo plano, lo que evita interbloquear el subproceso del juego de Unreal.