---
ms.openlocfilehash: cc29a6e9d358ba35d1e1ddd336b9df88ba68739b
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/21/2021
ms.locfileid: "98689961"
---
# <a name="426"></a>[<span data-ttu-id="37297-101">4.26</span><span class="sxs-lookup"><span data-stu-id="37297-101">4.26</span></span>](#tab/426)

## <a name="the-standard-winrt-apis"></a><span data-ttu-id="37297-102">Las API estándar de WinRT</span><span class="sxs-lookup"><span data-stu-id="37297-102">The standard WinRT APIs</span></span>

<span data-ttu-id="37297-103">La manera más común y más fácil de usar WinRT es llamar a métodos desde WinSDK.</span><span class="sxs-lookup"><span data-stu-id="37297-103">The most common and easiest way to use WinRT is to call methods from WinSDK.</span></span> <span data-ttu-id="37297-104">Para ello, abra el archivo YourModule.Build.cs y agregue las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="37297-104">To do so, open YourModule.Build.cs file and add the following lines:</span></span>

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

<span data-ttu-id="37297-105">A continuación, debe agregar los siguientes encabezados de WinRT:</span><span class="sxs-lookup"><span data-stu-id="37297-105">Next, you need to add the following WinRT headers:</span></span> 

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

<span data-ttu-id="37297-106">El código de WinRT solo se puede compilar en las plataformas de Win64 y HoloLens, por lo que la instrucción If impide que las bibliotecas de WinRT se incluyan en otras plataformas.</span><span class="sxs-lookup"><span data-stu-id="37297-106">WinRT code can only be compiled in the Win64 and HoloLens platforms, so the if statement prevents WinRT libraries from being included on other platforms.</span></span> <span data-ttu-id="37297-107">se agregó unknwn. h para tener la interfaz IUnknown.</span><span class="sxs-lookup"><span data-stu-id="37297-107">unknwn.h was added for having the IUnknown interface.</span></span> 


## <a name="winrt-from-a-nuget-package"></a><span data-ttu-id="37297-108">WinRT desde un paquete NuGet</span><span class="sxs-lookup"><span data-stu-id="37297-108">WinRT from a NuGet package</span></span>

<span data-ttu-id="37297-109">Es un poco más complicado si necesita agregar un paquete de NuGet con compatibilidad con WinRT.</span><span class="sxs-lookup"><span data-stu-id="37297-109">It’s a little more complicated if you need to add a NuGet package with WinRT support.</span></span> <span data-ttu-id="37297-110">En este caso, Visual Studio puede realizar prácticamente todo el trabajo, pero el sistema de compilación no es posible.</span><span class="sxs-lookup"><span data-stu-id="37297-110">In this case, Visual Studio can do practically all job for you, but the Unreal build system can’t.</span></span> <span data-ttu-id="37297-111">Afortunadamente, no es demasiado complicado.</span><span class="sxs-lookup"><span data-stu-id="37297-111">Luckily, it’s not too difficult.</span></span> <span data-ttu-id="37297-112">A continuación se muestra un ejemplo de cómo se descargará el paquete Microsoft. MixedReality. QR.</span><span class="sxs-lookup"><span data-stu-id="37297-112">Below is an example of how you would go about downloading the Microsoft.MixedReality.QR package.</span></span> <span data-ttu-id="37297-113">Puede reemplazarlo por otro, solo tiene que asegurarse de no perder el archivo winmd y copiar la dll correcta.</span><span class="sxs-lookup"><span data-stu-id="37297-113">You can replace it with another, just make sure you don’t lose the winmd file and copy the correct dll.</span></span> 

<span data-ttu-id="37297-114">El sistema operativo controla Windows SDK dll de la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="37297-114">Windows SDK dlls from the previous section are handled by the OS.</span></span> <span data-ttu-id="37297-115">Los archivos dll de NuGet deben administrarse mediante el código del módulo.</span><span class="sxs-lookup"><span data-stu-id="37297-115">NuGet’s dlls must be managed by the code in your module.</span></span> <span data-ttu-id="37297-116">Se recomienda agregar código para descargarlos, copiarlos en la carpeta de archivos binarios y cargarlos en la memoria de proceso en el inicio del módulo.</span><span class="sxs-lookup"><span data-stu-id="37297-116">We recommend adding code to download them, copying into binaries folder, and load into the process memory at the module startup.</span></span>

<span data-ttu-id="37297-117">En el primer paso, debe agregar un packages.config ( https://docs.microsoft.com/nuget/reference/packages-config) en la carpeta raíz del módulo).</span><span class="sxs-lookup"><span data-stu-id="37297-117">At the first step, you should add a packages.config (https://docs.microsoft.com/nuget/reference/packages-config) into the root folder of your module.</span></span> <span data-ttu-id="37297-118">Debe agregar todos los paquetes que quiera descargar, incluidas todas sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="37297-118">There you should add all packages you want to download, including all their dependencies.</span></span> <span data-ttu-id="37297-119">Aquí agregué Microsoft. MixedReality. QR como carga primaria y otros dos como dependencias.</span><span class="sxs-lookup"><span data-stu-id="37297-119">Here I added Microsoft.MixedReality.QR as a primary payload and two others as dependencies to it.</span></span> <span data-ttu-id="37297-120">El formato de ese archivo es el mismo que en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="37297-120">The format of that file is same as in Visual Studio:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  <package id="Microsoft.MixedReality.QR" version="0.5.2102" targetFramework="native" />
  <package id="Microsoft.VCRTForwarders.140" version="1.0.6" targetFramework="native" />
  <package id="Microsoft.Windows.CppWinRT" version="2.0.200729.8" targetFramework="native" />
</packages>
```

<span data-ttu-id="37297-121">Ahora puede descargar NuGet, los paquetes necesarios o hacer referencia a la [documentación](/nuget/consume-packages/install-use-packages-nuget-cli)de Nuget.</span><span class="sxs-lookup"><span data-stu-id="37297-121">Now you can download the NuGet, the required packages, or refer to the NuGet [documentation](/nuget/consume-packages/install-use-packages-nuget-cli).</span></span>

<span data-ttu-id="37297-122">Abra YourModule.Build.cs y agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="37297-122">Open YourModule.Build.cs and add the following code:</span></span>

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

<span data-ttu-id="37297-123">Deberá definir el método SafeCopy de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="37297-123">You'll need to define the SafeCopy method as follows:</span></span>

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

<span data-ttu-id="37297-124">Los archivos dll de NuGet deben cargarse manualmente en la memoria de proceso de Win32. se recomienda agregar la carga manual en el método de inicio del módulo:</span><span class="sxs-lookup"><span data-stu-id="37297-124">NuGet DLLs needs to load into your Win32 process memory manually; we recommend adding manual loading into the startup method of your module:</span></span>

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

<span data-ttu-id="37297-125">Por último, puede incluir los encabezados de WinRT en el código tal y como se describe en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="37297-125">Finally, you can include WinRT headers into your code as described in the previous section.</span></span>

# <a name="425"></a>[<span data-ttu-id="37297-126">4.25</span><span class="sxs-lookup"><span data-stu-id="37297-126">4.25</span></span>](#tab/425)

<span data-ttu-id="37297-127">No real no compila de forma nativa el código WinRT en la versión 4,25, por lo que es su trabajo crear un binario independiente que el sistema de compilación no real puede consumir.</span><span class="sxs-lookup"><span data-stu-id="37297-127">Unreal doesn't natively compile WinRT code in version 4.25, so it's your job to build a separate binary that Unreal’s build system can consume.</span></span> 

## <a name="objectives"></a><span data-ttu-id="37297-128">Objetivos</span><span class="sxs-lookup"><span data-stu-id="37297-128">Objectives</span></span>

- <span data-ttu-id="37297-129">Crear un archivo DLL de Windows universal que abra un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="37297-129">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="37297-130">Vincular el archivo DLL a un proyecto de juego inreal</span><span class="sxs-lookup"><span data-stu-id="37297-130">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="37297-131">Guardar un archivo en HoloLens desde un Blueprint real mediante el nuevo archivo DLL</span><span class="sxs-lookup"><span data-stu-id="37297-131">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="37297-132">Introducción</span><span class="sxs-lookup"><span data-stu-id="37297-132">Getting started</span></span>

1. <span data-ttu-id="37297-133">Compruebe que tiene instaladas todas las [herramientas necesarias](../tutorials/unreal-uxt-ch1.md) .</span><span class="sxs-lookup"><span data-stu-id="37297-133">Check that you have all [required tools](../tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="37297-134">[Cree un nuevo proyecto inreal](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) y asígnele el nombre **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="37297-134">[Create a new Unreal project](../tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="37297-135">Habilitación de los [Complementos necesarios](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="37297-135">Enable the [required plugins](../tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="37297-136">[Configuración para la implementación](../tutorials/unreal-uxt-ch6.md) en un dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="37297-136">[Setup for deployment](../tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="37297-137">Creación de un archivo DLL de WinRT</span><span class="sxs-lookup"><span data-stu-id="37297-137">Creating a WinRT DLL</span></span> 

1. <span data-ttu-id="37297-138">Abra un nuevo proyecto de Visual Studio y cree un proyecto de **dll (Windows universal)** en el mismo directorio que el archivo **uproject** del juego no real.</span><span class="sxs-lookup"><span data-stu-id="37297-138">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory as the Unreal game’s **uproject** file.</span></span> 

![Crear un archivo DLL](../images/unreal-winrt-img-01.png)

2. <span data-ttu-id="37297-140">Asigne al proyecto el nombre **HoloLensWinrtDLL** y establezca la ubicación como un subdirectorio **ThirdParty** en el archivo uproject del juego inreal.</span><span class="sxs-lookup"><span data-stu-id="37297-140">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="37297-141">Seleccione **colocar solución y proyecto en el mismo directorio** para simplificar la búsqueda de rutas de acceso más adelante.</span><span class="sxs-lookup"><span data-stu-id="37297-141">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurar el archivo DLL](../images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="37297-143">Una vez que se compila el nuevo proyecto, preste especial atención a los archivos CPP y de encabezado en blanco, denominados **HoloLensWinrtDLL. cpp** y **HoloLensWinrtDLL. h** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="37297-143">After the new project compiles, pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="37297-144">El encabezado es el archivo de inclusión que usa el archivo DLL en el modo inreal, mientras que el CPP contiene el cuerpo de las funciones exportadas e incluye cualquier código de WinRT que no se pueda compilar de otra manera.</span><span class="sxs-lookup"><span data-stu-id="37297-144">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="37297-145">Antes de agregar cualquier código, debe actualizar las propiedades del proyecto para asegurarse de que el código de WinRT que necesita puede compilar:</span><span class="sxs-lookup"><span data-stu-id="37297-145">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="37297-146">Haga clic con el botón derecho en el proyecto HoloLensWinrtDLL y seleccione **propiedades** .</span><span class="sxs-lookup"><span data-stu-id="37297-146">Right-click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="37297-147">Cambie la lista desplegable **configuración** a **todas las configuraciones** y la lista desplegable **plataforma** a **todas las plataformas** .</span><span class="sxs-lookup"><span data-stu-id="37297-147">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="37297-148">En **propiedades de configuración> C/C++> todas las opciones**:</span><span class="sxs-lookup"><span data-stu-id="37297-148">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="37297-149">Agregue **Await** a **opciones adicionales** para asegurarse de que se puede esperar en tareas asincrónicas</span><span class="sxs-lookup"><span data-stu-id="37297-149">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="37297-150">Cambiar **estándar de lenguaje c++** a **estándar ISO C++ 17 (/STD: C++ 17)** para incluir cualquier código WinRT</span><span class="sxs-lookup"><span data-stu-id="37297-150">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Actualización de las propiedades del proyecto](../images/unreal-winrt-img-03.png)

<span data-ttu-id="37297-152">El proyecto está listo para actualizar el origen del archivo DLL con código de WinRT que abre un cuadro de diálogo de archivos y guarda un archivo en el disco de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="37297-152">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="37297-153">Agregar el código DLL</span><span class="sxs-lookup"><span data-stu-id="37297-153">Adding the DLL code</span></span>

1. <span data-ttu-id="37297-154">Abra **HoloLensWinrtDLL. h** y agregue una función exportada de dll para que sea no real para consumir:</span><span class="sxs-lookup"><span data-stu-id="37297-154">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="37297-155">Abra **HoloLensWinrtDLL. cpp** y agregue todos los encabezados que usará la clase:</span><span class="sxs-lookup"><span data-stu-id="37297-155">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="37297-156">Todo el código de WinRT se almacena en **HoloLensWinrtDLL. cpp** , por lo que no se intenta incluir código winrt al hacer referencia al encabezado.</span><span class="sxs-lookup"><span data-stu-id="37297-156">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="37297-157">Todavía en **HoloLensWinrtDLL. cpp**, agregue el cuerpo de la función para OpenFileDialogue () y todo el código admitido:</span><span class="sxs-lookup"><span data-stu-id="37297-157">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="37297-158">Agregue una clase SaveGameManager a **HoloLensWinrtDLL. cpp** para controlar el cuadro de diálogo de archivo y guardar el archivo:</span><span class="sxs-lookup"><span data-stu-id="37297-158">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="37297-159">Compile la solución para la **versión > ARM64** para compilar el archivo dll en el directorio secundario ARM64/Release/HoloLensWinrtDLL de la solución dll.</span><span class="sxs-lookup"><span data-stu-id="37297-159">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="37297-160">Agregar el archivo binario de WinRT a no real</span><span class="sxs-lookup"><span data-stu-id="37297-160">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="37297-161">La vinculación y el uso de una DLL en inreal requiere un proyecto de C++.</span><span class="sxs-lookup"><span data-stu-id="37297-161">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="37297-162">Si utiliza un proyecto Blueprint, se puede convertir fácilmente en un proyecto de C++ agregando una clase de C++:</span><span class="sxs-lookup"><span data-stu-id="37297-162">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="37297-163">En el editor desareal, Abra **archivo > nueva clase de C++...**</span><span class="sxs-lookup"><span data-stu-id="37297-163">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="37297-164">y cree un nuevo **actor** denominado **WinrtActor** para ejecutar el código en el archivo dll:</span><span class="sxs-lookup"><span data-stu-id="37297-164">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Creación de un nuevo actor](../images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="37297-166">Ahora se ha creado una solución en el mismo directorio que el archivo uproject, junto con un nuevo script de compilación denominado Source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="37297-166">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="37297-167">Abra la solución, busque la carpeta **Games/ConsumeWinRT/Source/ConsumeWinRT** y Abra **ConsumeWinRT.Build.CS**:</span><span class="sxs-lookup"><span data-stu-id="37297-167">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Abrir el archivo ConsumeWinRT.build.cs](../images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="37297-169">Vincular el archivo DLL</span><span class="sxs-lookup"><span data-stu-id="37297-169">Linking the DLL</span></span>
1. <span data-ttu-id="37297-170">En **ConsumeWinRT.Build.CS**, agregue una propiedad para buscar la ruta de acceso de inclusión para el archivo DLL (el directorio que contiene HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="37297-170">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="37297-171">El archivo DLL se encuentra en un directorio secundario de la ruta de acceso de inclusión, por lo que esta propiedad se usará como el directorio raíz binario:</span><span class="sxs-lookup"><span data-stu-id="37297-171">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="37297-172">En el constructor de clase, agregue el código siguiente para actualizar la ruta de acceso de inclusión, vincule el nuevo lib y cargue el retardo y copie el archivo DLL en la ubicación de appx empaquetada:</span><span class="sxs-lookup"><span data-stu-id="37297-172">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="37297-173">Abra **WinrtActor. h** y agregue una definición de función, una a la que llamará un Blueprint:</span><span class="sxs-lookup"><span data-stu-id="37297-173">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="37297-174">Abra **WinrtActor. cpp** y actualice BeginPlay para cargar el archivo dll:</span><span class="sxs-lookup"><span data-stu-id="37297-174">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="37297-175">El archivo DLL se debe cargar antes de llamar a cualquiera de sus funciones.</span><span class="sxs-lookup"><span data-stu-id="37297-175">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="37297-176">Compilación del juego</span><span class="sxs-lookup"><span data-stu-id="37297-176">Building the game</span></span>
1. <span data-ttu-id="37297-177">Compile la solución de juego para iniciar el editor inreal abierto en el proyecto de juego:</span><span class="sxs-lookup"><span data-stu-id="37297-177">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="37297-178">En la pestaña **colocar actores** , busque el nuevo **WinrtActor** y arrástrelo a la escena.</span><span class="sxs-lookup"><span data-stu-id="37297-178">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="37297-179">Abra el plano de nivel para ejecutar la función de Blueprint Callable en **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="37297-179">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Colocar WinrtActor en la escena](../images/unreal-winrt-img-06.png)

2. <span data-ttu-id="37297-181">En el **contorno mundial**, busque el **WindrtActor** previamente colocado en la escena y arrástrelo al plano de nivel:</span><span class="sxs-lookup"><span data-stu-id="37297-181">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Arrastrar WinrtActor al plano de nivel](../images/unreal-winrt-img-07.png)

3. <span data-ttu-id="37297-183">En el plano de nivel, arrastre el nodo de salida desde WinrtActor, busque el **cuadro de diálogo Abrir archivo** y, a continuación, enrute el nodo desde cualquier entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="37297-183">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="37297-184">En este caso, se llama al cuadro de diálogo Abrir archivo desde un evento de voz:</span><span class="sxs-lookup"><span data-stu-id="37297-184">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configuración de nodos en el plano de nivel](../images/unreal-winrt-img-08.png)

4. <span data-ttu-id="37297-186">[Empaquete este juego para HoloLens](../tutorials/unreal-uxt-ch6.md), impleméntelo y ejecútelo.</span><span class="sxs-lookup"><span data-stu-id="37297-186">[Package this game for HoloLens](../tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="37297-187">Cuando el método no real llama a OpenFileDialogue, se abre un cuadro de diálogo de archivo en la solicitud de HoloLens para un nombre de archivo. txt.</span><span class="sxs-lookup"><span data-stu-id="37297-187">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="37297-188">Una vez guardado el archivo, vaya a la pestaña **Explorador de archivos** en el portal de dispositivos para ver el contenido "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="37297-188">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="37297-189">Resumen</span><span class="sxs-lookup"><span data-stu-id="37297-189">Summary</span></span> 

<span data-ttu-id="37297-190">Le recomendamos que use este tutorial como punto de partida para consumir código de WinRT en un lugar inreal cuando necesite guardar archivos en el disco de HoloLens con el mismo cuadro de diálogo de archivo que Windows.</span><span class="sxs-lookup"><span data-stu-id="37297-190">We encourage you to use this tutorial as a starting point for consuming WinRT code in Unreal when you need to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="37297-191">El mismo proceso se aplica a la exportación de funciones adicionales desde el encabezado HoloLensWinrtDLL y que se usa en el mismo.</span><span class="sxs-lookup"><span data-stu-id="37297-191">The same process applies to exporting additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="37297-192">Preste especial atención al código DLL que espera en el código asincrónico de WinRT en un subproceso MTA en segundo plano, lo que evita el interbloqueo del subproceso de juego inreal.</span><span class="sxs-lookup"><span data-stu-id="37297-192">Pay special attention to the DLL code that waits on async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span>