---
ms.openlocfilehash: 6bed33ee9b41a4ee66ce4c1c579d398f0958143d
ms.sourcegitcommit: db01faaf76bccd4f0432cf6b383fefa04ab7a085
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/23/2020
ms.locfileid: "97745757"
---
# <a name="426"></a>[4.26](#tab/426)

## <a name="the-standard-winrt-apis"></a>Las API estándar de WinRT

La manera más común y más fácil de usar WinRT es llamar a métodos desde WinSDK. Para ello, abra el archivo YourModule.Build.cs y agregue las líneas siguientes:

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

El código de WinRT solo se puede compilar en las plataformas de Win64 y HoloLens, por lo que la instrucción If impide que las bibliotecas de WinRT se incluyan en otras plataformas. se agregó unknwn. h para tener la interfaz IUnknown. 


## <a name="winrt-from-a-nuget-package"></a>WinRT desde un paquete NuGet

Es un poco más complicado si necesita agregar un paquete de NuGet con compatibilidad con WinRT. En este caso, Visual Studio puede realizar prácticamente todo el trabajo, pero el sistema de compilación no es posible. Afortunadamente, no es demasiado complicado. A continuación se muestra un ejemplo de cómo se descargará el paquete Microsoft. MixedReality. QR. Puede reemplazarlo por otro, solo tiene que asegurarse de no perder el archivo winmd y copiar la dll correcta. 

El sistema operativo controla Windows SDK dll de la sección anterior. Los archivos dll de NuGet deben administrarse mediante el código del módulo. Se recomienda agregar código para descargarlos, copiarlos en la carpeta de archivos binarios y cargarlos en la memoria de proceso en el inicio del módulo.

En el primer paso, debe agregar un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) en la carpeta raíz del módulo). Debe agregar todos los paquetes que quiera descargar, incluidas todas sus dependencias. Aquí agregué Microsoft. MixedReality. QR como carga primaria y otros dos como dependencias. El formato de ese archivo es el mismo que en Visual Studio:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

Ahora puede descargar NuGet, los paquetes necesarios o hacer referencia a la [documentación](https://docs.microsoft.com/nuget/consume-packages/install-use-packages-nuget-cli)de Nuget.

Abra YourModule.Build.cs y agregue el código siguiente:

```csharp
if(Target.Platform == UnrealTargetPlatform.Win64 || Target.Platform == UnrealTargetPlatform.HoloLens)
{
    string MyModuleName = GetType().Name;

    // these parameters mandatory for winrt support
    bEnableExceptions = true;
    bUseUnity = false;
    CppStandard = CppStandardVersion.Cpp17;
    PublicSystemLibraries.Add("shlwapi.lib");
    PublicSystemLibraries.Add("runtimeobject.lib");

    // prepare everything for nuget
    string NugetFolder = Path.Combine(PluginDirectory, "Intermediate", "Nuget", MyModuleName);
    Directory.CreateDirectory(NugetFolder);

    string BinariesSubFolder = Path.Combine("Binaries", "ThirdParty", Target.Type.ToString(), Target.Platform.ToString(), Target.Architecture);

    PrivateDefinitions.Add(string.Format("THIRDPARTY_BINARY_SUBFOLDER=\"{0}\"", BinariesSubFolder.Replace(@"\", @"\\")));

    string BinariesFolder = Path.Combine(PluginDirectory, BinariesSubFolder);
    Directory.CreateDirectory(BinariesFolder);

    // download nuget
    string NugetExe = Path.Combine(NugetFolder, "nuget.exe");
    if(!File.Exists(NugetExe))
    {
        using (System.Net.WebClient myWebClient = new System.Net.WebClient())
        {
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
            
    // get list of the installed packages
    string[] InstalledPackages = Utils.RunLocalProcessAndReturnStdOut(NugetExe, string.Format("list -Source \"{0}\"", NugetFolder)).Split(new char[] {'\r', '\n' });

    // get WinRT package 
    string CppWinRTPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.Windows.CppWinRT"));
    if(!string.IsNullOrEmpty(CppWinRTPackage))
    {
        string CppWinRTName = CppWinRTPackage.Replace(" ", ".");
        string CppWinRTExe = Path.Combine(NugetFolder, CppWinRTName, "bin", "cppwinrt.exe");
        string CppWinRTFolder = Path.Combine(PluginDirectory, "Intermediate", CppWinRTName, MyModuleName);
        Directory.CreateDirectory(CppWinRTFolder);

        // search all downloaded packages for winmd files
        string[] WinMDFiles = Directory.GetFiles(NugetFolder, "*.winmd", SearchOption.AllDirectories);

        // all downloaded winmd file with WinSDK to be processed by cppwinrt.exe
        var WinMDFilesStringbuilder = new System.Text.StringBuilder();
        foreach(var winmd in WinMDFiles)
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
        // fall back to default WinSDK headers
        PrivateIncludePaths.Add(Path.Combine(Target.WindowsPlatform.WindowsSdkDir, "Include", Target.WindowsPlatform.WindowsSdkVersion, "cppwinrt"));
    }

    // WinRT lib for some job
    string QRPackage = InstalledPackages.FirstOrDefault(x => x.StartsWith("Microsoft.MixedReality.QR"));
    if (!string.IsNullOrEmpty(QRPackage))
    {
        string QRFolderName = QRPackage.Replace(" ", ".");

        // copying dll and winmd binaries to our local binaries folder
        // !!!!! please make sure that you use the path of file! Unreal can't do it for you !!!!!
        SafeCopy(Path.Combine(NugetFolder, QRFolderName, @"lib\uap10.0.18362\Microsoft.MixedReality.QR.winmd"), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));

        SafeCopy(Path.Combine(NugetFolder, QRFolderName, string.Format(@"runtimes\win10-{0}\native\Microsoft.MixedReality.QR.dll", Target.WindowsPlatform.Architecture.ToString())), 
        Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));

        // also both both binaries must be in RuntimeDependencies, unless you get failures in Hololens platform
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.dll"));
        RuntimeDependencies.Add(Path.Combine(BinariesFolder, "Microsoft.MixedReality.QR.winmd"));
    }

    if(Target.Platform == UnrealTargetPlatform.Win64)
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

Los archivos dll de NuGet deben cargarse manualmente en la memoria de proceso de Win32. se recomienda agregar la carga manual en el método de inicio del módulo:

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

Por último, puede incluir los encabezados de WinRT en el código tal y como se describe en la sección anterior.

# <a name="425"></a>[4.25](#tab/425)

No real no compila de forma nativa el código WinRT en la versión 4,25, por lo que es su trabajo crear un binario independiente que el sistema de compilación no real puede consumir. 

## <a name="objectives"></a>Objetivos

- Crear un archivo DLL de Windows universal que abra un FileSaveDialogue
- Vincular el archivo DLL a un proyecto de juego inreal
- Guardar un archivo en HoloLens desde un Blueprint real mediante el nuevo archivo DLL

## <a name="getting-started"></a>Introducción

1. Compruebe que tiene instaladas todas las [herramientas necesarias](../tutorials/unreal-uxt-ch1.md) .
2. [Cree un nuevo proyecto inreal](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) y asígnele el nombre **Consumewinrt**
3. Habilitación de los [Complementos necesarios](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para el desarrollo de HoloLens
4. [Configuración para la implementación](../tutorials/unreal-uxt-ch6.md) en un dispositivo o emulador

## <a name="creating-a-winrt-dll"></a>Creación de un archivo DLL de WinRT 

1. Abra un nuevo proyecto de Visual Studio y cree un proyecto de **dll (Windows universal)** en el mismo directorio que el archivo **uproject** del juego no real. 

![Crear un archivo DLL](../images/unreal-winrt-img-01.png)

2. Asigne al proyecto el nombre **HoloLensWinrtDLL** y establezca la ubicación como un subdirectorio **ThirdParty** en el archivo uproject del juego inreal. 
    * Seleccione **colocar solución y proyecto en el mismo directorio** para simplificar la búsqueda de rutas de acceso más adelante. 

![Configurar el archivo DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Una vez que se compila el nuevo proyecto, preste especial atención a los archivos CPP y de encabezado en blanco, denominados **HoloLensWinrtDLL. cpp** y **HoloLensWinrtDLL. h** , respectivamente. El encabezado es el archivo de inclusión que usa el archivo DLL en el modo inreal, mientras que el CPP contiene el cuerpo de las funciones exportadas e incluye cualquier código de WinRT que no se pueda compilar de otra manera. 

3. Antes de agregar cualquier código, debe actualizar las propiedades del proyecto para asegurarse de que el código de WinRT que necesita puede compilar: 
    * Haga clic con el botón derecho en el proyecto HoloLensWinrtDLL y seleccione **propiedades** .  
    * Cambie la lista desplegable **configuración** a **todas las configuraciones** y la lista desplegable **plataforma** a **todas las plataformas** .  
    * En **propiedades de configuración> C/C++> todas las opciones**:
        * Agregue **Await** a **opciones adicionales** para asegurarse de que se puede esperar en tareas asincrónicas  
        * Cambiar **estándar de lenguaje c++** a **estándar ISO C++ 17 (/STD: C++ 17)** para incluir cualquier código WinRT

![Actualización de las propiedades del proyecto](../images/unreal-winrt-img-03.png)

El proyecto está listo para actualizar el origen del archivo DLL con código de WinRT que abre un cuadro de diálogo de archivos y guarda un archivo en el disco de HoloLens.  

## <a name="adding-the-dll-code"></a>Agregar el código DLL

1. Abra **HoloLensWinrtDLL. h** y agregue una función exportada de dll para que sea no real para consumir: 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. Abra **HoloLensWinrtDLL. cpp** y agregue todos los encabezados que usará la clase:  

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
> Todo el código de WinRT se almacena en **HoloLensWinrtDLL. cpp** , por lo que no se intenta incluir código winrt al hacer referencia al encabezado. 

3. Todavía en **HoloLensWinrtDLL. cpp**, agregue el cuerpo de la función para OpenFileDialogue () y todo el código admitido: 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. Agregue una clase SaveGameManager a **HoloLensWinrtDLL. cpp** para controlar el cuadro de diálogo de archivo y guardar el archivo: 

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

5. Compile la solución para la **versión > ARM64** para compilar el archivo dll en el directorio secundario ARM64/Release/HoloLensWinrtDLL de la solución dll. 

## <a name="adding-the-winrt-binary-to-unreal"></a>Agregar el archivo binario de WinRT a no real 
La vinculación y el uso de una DLL en inreal requiere un proyecto de C++. Si utiliza un proyecto Blueprint, se puede convertir fácilmente en un proyecto de C++ agregando una clase de C++:  

1. En el editor desareal, Abra **archivo > nueva clase de C++...** y cree un nuevo **actor** denominado **WinrtActor** para ejecutar el código en el archivo dll: 

![Creación de un nuevo actor](../images/unreal-winrt-img-04.png)

> [!NOTE]
> Ahora se ha creado una solución en el mismo directorio que el archivo uproject, junto con un nuevo script de compilación denominado Source/ConsumeWinRT/ConsumeWinRT. Build. cs.

2. Abra la solución, busque la carpeta **Games/ConsumeWinRT/Source/ConsumeWinRT** y Abra **ConsumeWinRT.Build.CS**:

![Abrir el archivo ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a>Vincular el archivo DLL
1. En **ConsumeWinRT.Build.CS**, agregue una propiedad para buscar la ruta de acceso de inclusión para el archivo DLL (el directorio que contiene HoloLensWinrtDLL. h). El archivo DLL se encuentra en un directorio secundario de la ruta de acceso de inclusión, por lo que esta propiedad se usará como el directorio raíz binario:

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

2. En el constructor de clase, agregue el código siguiente para actualizar la ruta de acceso de inclusión, vincule el nuevo lib y cargue el retardo y copie el archivo DLL en la ubicación de appx empaquetada:

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

3. Abra **WinrtActor. h** y agregue una definición de función, una a la que llamará un Blueprint: 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. Abra **WinrtActor. cpp** y actualice BeginPlay para cargar el archivo dll: 

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
> El archivo DLL se debe cargar antes de llamar a cualquiera de sus funciones.

### <a name="building-the-game"></a>Compilación del juego
1. Compile la solución de juego para iniciar el editor inreal abierto en el proyecto de juego: 
    * En la pestaña **colocar actores** , busque el nuevo **WinrtActor** y arrástrelo a la escena. 
    * Abra el plano de nivel para ejecutar la función de Blueprint Callable en **WinrtActor** 

![Colocar WinrtActor en la escena](../images/unreal-winrt-img-06.png)

2. En el **contorno mundial**, busque el **WindrtActor** previamente colocado en la escena y arrástrelo al plano de nivel: 

![Arrastrar WinrtActor al plano de nivel](../images/unreal-winrt-img-07.png)

3. En el plano de nivel, arrastre el nodo de salida desde WinrtActor, busque el **cuadro de diálogo Abrir archivo** y, a continuación, enrute el nodo desde cualquier entrada del usuario.  En este caso, se llama al cuadro de diálogo Abrir archivo desde un evento de voz: 

![Configuración de nodos en el plano de nivel](../images/unreal-winrt-img-08.png)

4. [Empaquete este juego para HoloLens](../tutorials/unreal-uxt-ch6.md), impleméntelo y ejecútelo.  

Cuando el método no real llama a OpenFileDialogue, se abre un cuadro de diálogo de archivo en la solicitud de HoloLens para un nombre de archivo. txt.  Una vez guardado el archivo, vaya a la pestaña **Explorador de archivos** en el portal de dispositivos para ver el contenido "Hello WinRT". 

## <a name="summary"></a>Resumen 

Le recomendamos que use este tutorial como punto de partida para consumir código de WinRT en un lugar inreal cuando necesite guardar archivos en el disco de HoloLens con el mismo cuadro de diálogo de archivo que Windows.  El mismo proceso se aplica a la exportación de funciones adicionales desde el encabezado HoloLensWinrtDLL y que se usa en el mismo.  Preste especial atención al código DLL que espera en el código asincrónico de WinRT en un subproceso MTA en segundo plano, lo que evita el interbloqueo del subproceso de juego inreal. 

