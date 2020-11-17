---
title: WinRT en Unreal
description: Información general del complemento de audio espacial para Unreal Engine.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 07/08/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicación remota, realidad mixta, desarrollo, introducción, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, WinRT, DLL
ms.openlocfilehash: fd50e5ecd3186fc8852936affbfedc3d5fd4de75
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679814"
---
# <a name="winrt-in-unreal"></a><span data-ttu-id="2fcb0-104">WinRT en Unreal</span><span class="sxs-lookup"><span data-stu-id="2fcb0-104">WinRT in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2fcb0-105">Información general</span><span class="sxs-lookup"><span data-stu-id="2fcb0-105">Overview</span></span>

<span data-ttu-id="2fcb0-106">En el transcurso del desarrollo de HoloLens, puede que tenga que escribir una característica con WinRT.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-106">Over the course of your HoloLens development you may need to write a feature using WinRT.</span></span> <span data-ttu-id="2fcb0-107">Por ejemplo, al abrir un cuadro de diálogo de archivo en una aplicación de HoloLens, se necesitaría el archivo de encabezado FileSavePicker en winrt/Windows. Storage. Picker. h.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-107">For example, opening a file dialogue in a HoloLens application would need the FileSavePicker in winrt/Windows.Storage.Pickers.h header file.</span></span>  <span data-ttu-id="2fcb0-108">Puesto que no real no compila código WinRT de forma nativa, es su trabajo crear un binario independiente y que el sistema de compilación no es el que puede consumir.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-108">Since Unreal doesn't natively compile WinRT code, it's your job to build a separate binary and that can be consumed by Unreal’s build system.</span></span> <span data-ttu-id="2fcb0-109">Este tutorial le guiará a través de este escenario.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-109">This tutorial will walk you through just such a scenario.</span></span>

## <a name="objectives"></a><span data-ttu-id="2fcb0-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2fcb0-110">Objectives</span></span>
- <span data-ttu-id="2fcb0-111">Crear un archivo DLL de Windows universal que abra un FileSaveDialogue</span><span class="sxs-lookup"><span data-stu-id="2fcb0-111">Create a Universal Windows DLL that opens a FileSaveDialogue</span></span>
- <span data-ttu-id="2fcb0-112">Vincular el archivo DLL a un proyecto de juego inreal</span><span class="sxs-lookup"><span data-stu-id="2fcb0-112">Link that DLL to an Unreal game project</span></span>
- <span data-ttu-id="2fcb0-113">Guardar un archivo en HoloLens desde un Blueprint real mediante el nuevo archivo DLL</span><span class="sxs-lookup"><span data-stu-id="2fcb0-113">Save a file on the HoloLens from an Unreal blueprint using the new DLL</span></span>

## <a name="getting-started"></a><span data-ttu-id="2fcb0-114">Introducción</span><span class="sxs-lookup"><span data-stu-id="2fcb0-114">Getting started</span></span>
1. <span data-ttu-id="2fcb0-115">Compruebe que tiene instaladas todas las [herramientas necesarias](tutorials/unreal-uxt-ch1.md) .</span><span class="sxs-lookup"><span data-stu-id="2fcb0-115">Check that you have all [required tools](tutorials/unreal-uxt-ch1.md) installed</span></span>
2. <span data-ttu-id="2fcb0-116">[Cree un nuevo proyecto inreal](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) y asígnele el nombre **Consumewinrt**</span><span class="sxs-lookup"><span data-stu-id="2fcb0-116">[Create a new Unreal project](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) and name it **Consumewinrt**</span></span>
3. <span data-ttu-id="2fcb0-117">Habilitación de los [Complementos necesarios](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para el desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="2fcb0-117">Enable the [required plugins](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) for HoloLens development</span></span>
4. <span data-ttu-id="2fcb0-118">[Configuración para la implementación](tutorials/unreal-uxt-ch6.md) en un dispositivo o emulador</span><span class="sxs-lookup"><span data-stu-id="2fcb0-118">[Setup for deployment](tutorials/unreal-uxt-ch6.md) to a device or emulator</span></span>

## <a name="creating-a-winrt-dll"></a><span data-ttu-id="2fcb0-119">Creación de un archivo DLL de WinRT</span><span class="sxs-lookup"><span data-stu-id="2fcb0-119">Creating a WinRT DLL</span></span> 
1. <span data-ttu-id="2fcb0-120">Abra un nuevo proyecto de Visual Studio y cree un proyecto **dll (universal Windows)** en el mismo directorio que el archivo **uproject** del juego no real.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-120">Open a new Visual Studio project and create a **DLL (Universal Windows)** project in the same directory to the Unreal game’s **uproject** file.</span></span> 

![Crear un archivo DLL](images/unreal-winrt-img-01.png)

2. <span data-ttu-id="2fcb0-122">Asigne al proyecto el nombre **HoloLensWinrtDLL** y establezca la ubicación como un subdirectorio **ThirdParty** en el archivo uproject del juego inreal.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-122">Name the project **HoloLensWinrtDLL** and set the location as a **ThirdParty** subdirectory to the Unreal game’s uproject file.</span></span> 
    * <span data-ttu-id="2fcb0-123">Seleccione **colocar solución y proyecto en el mismo directorio** para simplificar la búsqueda de rutas de acceso más adelante.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-123">Select **Place solution and project in the same directory** to simplify looking for paths later.</span></span> 

![Configurar el archivo DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> <span data-ttu-id="2fcb0-125">Una vez que se compila el nuevo proyecto, desea prestar especial atención a los archivos CPP y de encabezado en blanco, denominados **HoloLensWinrtDLL. cpp** y **HoloLensWinrtDLL. h** , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-125">After the new project compiles, you want to pay special attention to the blank cpp and header files, named **HoloLensWinrtDLL.cpp** and **HoloLensWinrtDLL.h** respectively.</span></span> <span data-ttu-id="2fcb0-126">El encabezado es el archivo de inclusión que usa el archivo DLL en el modo inreal, mientras que el CPP contiene el cuerpo de las funciones exportadas e incluye cualquier código de WinRT que no se pueda compilar de otra manera.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-126">The header is the include file that uses the DLL in Unreal, while the cpp holds the body of any functions you export and includes any WinRT code that Unreal wouldn't otherwise be able to compile.</span></span> 

3. <span data-ttu-id="2fcb0-127">Antes de agregar cualquier código, debe actualizar las propiedades del proyecto para asegurarse de que el código de WinRT que necesita puede compilar:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-127">Before you add any code, you need to update the project properties to ensure the WinRT code you need can compile:</span></span> 
    * <span data-ttu-id="2fcb0-128">Haga clic con el botón derecho en el proyecto HoloLensWinrtDLL y seleccione **propiedades** .</span><span class="sxs-lookup"><span data-stu-id="2fcb0-128">Right click on the HoloLensWinrtDLL project and select **properties**</span></span>  
    * <span data-ttu-id="2fcb0-129">Cambie la lista desplegable **configuración** a **todas las configuraciones** y la lista desplegable **plataforma** a **todas las plataformas** .</span><span class="sxs-lookup"><span data-stu-id="2fcb0-129">Change the **Configuration** dropdown to **All Configurations** and the **Platform** dropdown to **All Platforms**</span></span>  
    * <span data-ttu-id="2fcb0-130">En **propiedades de configuración> C/C++> todas las opciones**:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-130">Under **Configuration Properties> C/C++> All Options**:</span></span>
        * <span data-ttu-id="2fcb0-131">Agregue **Await** a **opciones adicionales** para asegurarse de que se puede esperar en tareas asincrónicas</span><span class="sxs-lookup"><span data-stu-id="2fcb0-131">Add **await** to **Additional Options** to ensure we can wait on async tasks</span></span>  
        * <span data-ttu-id="2fcb0-132">Cambiar **estándar de lenguaje c++** a **estándar ISO C++ 17 (/STD: C++ 17)** para incluir cualquier código WinRT</span><span class="sxs-lookup"><span data-stu-id="2fcb0-132">Change **C++ Language Standard** to **ISO C++17 Standard (/std:c++17)** to include any WinRT code</span></span>

![Actualización de las propiedades del proyecto](images/unreal-winrt-img-03.png)

<span data-ttu-id="2fcb0-134">El proyecto está listo para actualizar el origen del archivo DLL con código de WinRT que abre un cuadro de diálogo de archivos y guarda un archivo en el disco de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-134">Your project is ready to update the DLL’s source with WinRT code that opens a file dialogue and saves a file to the HoloLens disk.</span></span>  

## <a name="adding-the-dll-code"></a><span data-ttu-id="2fcb0-135">Agregar el código DLL</span><span class="sxs-lookup"><span data-stu-id="2fcb0-135">Adding the DLL code</span></span>
1. <span data-ttu-id="2fcb0-136">Abra **HoloLensWinrtDLL. h** y agregue una función exportada de dll para que sea no real para consumir:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-136">Open **HoloLensWinrtDLL.h** and add a dll exported function for Unreal to consume:</span></span> 

```cpp
#pragma once

class HoloLensWinrtDLL
{
public:
    _declspec(dllexport) static void OpenFileDialogue();
};
```

2. <span data-ttu-id="2fcb0-137">Abra **HoloLensWinrtDLL. cpp** y agregue todos los encabezados que usará la clase:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-137">Open **HoloLensWinrtDLL.cpp** and add all headers the class will use:</span></span>  

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
> <span data-ttu-id="2fcb0-138">Todo el código de WinRT se almacena en **HoloLensWinrtDLL. cpp** , por lo que no se intenta incluir código winrt al hacer referencia al encabezado.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-138">All WinRT code is stored in **HoloLensWinrtDLL.cpp** so Unreal doesn't try to include any WinRT code when referencing the header.</span></span> 

3. <span data-ttu-id="2fcb0-139">Todavía en **HoloLensWinrtDLL. cpp**, agregue el cuerpo de la función para OpenFileDialogue () y todo el código admitido:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-139">Still in **HoloLensWinrtDLL.cpp**, add a function body for OpenFileDialogue() and all supported code:</span></span> 

```cpp
// sgm is declared outside of OpenFileDialogue so it doesn't
// get destroyed when OpenFileDialogue goes out of scope.
SaveGameManager sgm;

void HoloLensWinrtDLL::OpenFileDialogue()
{
    sgm.SaveGame();
}
```

4. <span data-ttu-id="2fcb0-140">Agregue una clase SaveGameManager a **HoloLensWinrtDLL. cpp** para controlar el cuadro de diálogo de archivo y guardar el archivo:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-140">Add a SaveGameManager class to **HoloLensWinrtDLL.cpp** to handle the file dialogue and saving the file:</span></span> 

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

5. <span data-ttu-id="2fcb0-141">Compile la solución para la **versión > ARM64** para compilar el archivo dll en el directorio secundario ARM64/Release/HoloLensWinrtDLL de la solución dll.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-141">Build the solution for **Release > ARM64** to build the DLL to the child directory ARM64/Release/HoloLensWinrtDLL from the DLL solution.</span></span> 

## <a name="adding-the-winrt-binary-to-unreal"></a><span data-ttu-id="2fcb0-142">Agregar el archivo binario de WinRT a no real</span><span class="sxs-lookup"><span data-stu-id="2fcb0-142">Adding the WinRT binary to Unreal</span></span> 
<span data-ttu-id="2fcb0-143">La vinculación y el uso de una DLL en inreal requiere un proyecto de C++.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-143">Linking and using a DLL in Unreal requires a C++ project.</span></span> <span data-ttu-id="2fcb0-144">Si utiliza un proyecto Blueprint, se puede convertir fácilmente en un proyecto de C++ agregando una clase de C++:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-144">If you're using a Blueprint project, it can be easily converted to a C++ project by adding a C++ class:</span></span>  

1. <span data-ttu-id="2fcb0-145">En el editor desareal, Abra **archivo > nueva clase de C++...**</span><span class="sxs-lookup"><span data-stu-id="2fcb0-145">In the Unreal editor, open **File > New C++ Class…**</span></span> <span data-ttu-id="2fcb0-146">y cree un nuevo **actor** denominado **WinrtActor** para ejecutar el código en el archivo dll:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-146">and create a new **Actor** named **WinrtActor** to run the code in the DLL:</span></span> 

![Creación de un nuevo actor](images/unreal-winrt-img-04.png)

> [!NOTE]
> <span data-ttu-id="2fcb0-148">Ahora se ha creado una solución en el mismo directorio que el archivo uproject, junto con un nuevo script de compilación denominado Source/ConsumeWinRT/ConsumeWinRT. Build. cs.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-148">A solution has now been created in the same directory as the uproject file along with a new build script named Source/ConsumeWinRT/ConsumeWinRT.Build.cs.</span></span>

2. <span data-ttu-id="2fcb0-149">Abra la solución, busque la carpeta **Games/ConsumeWinRT/Source/ConsumeWinRT** y Abra **ConsumeWinRT.Build.CS**:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-149">Open the solution, browse for the **Games/ConsumeWinRT/Source/ConsumeWinRT** folder, and open **ConsumeWinRT.build.cs**:</span></span>

![Abrir el archivo ConsumeWinRT.build.cs](images/unreal-winrt-img-05.png)

### <a name="linking-the-dll"></a><span data-ttu-id="2fcb0-151">Vincular el archivo DLL</span><span class="sxs-lookup"><span data-stu-id="2fcb0-151">Linking the DLL</span></span>
1. <span data-ttu-id="2fcb0-152">En **ConsumeWinRT.Build.CS**, agregue una propiedad para buscar la ruta de acceso de inclusión para el archivo DLL (el directorio que contiene HoloLensWinrtDLL. h).</span><span class="sxs-lookup"><span data-stu-id="2fcb0-152">In **ConsumeWinRT.build.cs**, add a property to find the include path for the DLL (the directory containing HoloLensWinrtDLL.h).</span></span> <span data-ttu-id="2fcb0-153">El archivo DLL se encuentra en un directorio secundario de la ruta de acceso de inclusión, por lo que esta propiedad se usará como el directorio raíz binario:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-153">The DLL is in a child directory to the include path, so this property will be used as the binary root dir:</span></span>

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

2. <span data-ttu-id="2fcb0-154">En el constructor de clase, agregue el código siguiente para actualizar la ruta de acceso de inclusión, vincule el nuevo lib y cargue el retardo y copie el archivo DLL en la ubicación de appx empaquetada:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-154">In the class constructor, add the following code to update the include path, link the new lib, and delay-load and copy the DLL to the packaged appx location:</span></span>

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

3. <span data-ttu-id="2fcb0-155">Abra **WinrtActor. h** y agregue una definición de función, una a la que llamará un Blueprint:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-155">Open **WinrtActor.h** and add one function definition, one that a blueprint will call:</span></span> 

```cpp
public:
    UFUNCTION(BlueprintCallable)
    static void OpenFileDialogue();
```

4. <span data-ttu-id="2fcb0-156">Abra **WinrtActor. cpp** y actualice BeginPlay para cargar el archivo dll:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-156">Open **WinrtActor.cpp** and update BeginPlay to load the DLL:</span></span> 

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
> <span data-ttu-id="2fcb0-157">El archivo DLL se debe cargar antes de llamar a cualquiera de sus funciones.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-157">The DLL must be loaded before calling any of its functions.</span></span>

### <a name="building-the-game"></a><span data-ttu-id="2fcb0-158">Compilación del juego</span><span class="sxs-lookup"><span data-stu-id="2fcb0-158">Building the game</span></span>
1. <span data-ttu-id="2fcb0-159">Compile la solución de juego para iniciar el editor inreal abierto en el proyecto de juego:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-159">Build the game solution to launch the Unreal editor opened to the game project:</span></span> 
    * <span data-ttu-id="2fcb0-160">En la pestaña **colocar actores** , busque el nuevo **WinrtActor** y arrástrelo a la escena.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-160">In the **Place Actors** tab, search for the new **WinrtActor** and drag it into the scene</span></span> 
    * <span data-ttu-id="2fcb0-161">Abra el plano de nivel para ejecutar la función de Blueprint Callable en **WinrtActor**</span><span class="sxs-lookup"><span data-stu-id="2fcb0-161">Open the level blueprint to execute the blueprint callable function in the **WinrtActor**</span></span> 

![Colocar WinrtActor en la escena](images/unreal-winrt-img-06.png)

2. <span data-ttu-id="2fcb0-163">En el **contorno mundial**, busque el **WindrtActor** previamente colocado en la escena y arrástrelo al plano de nivel:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-163">In the **World Outliner**, find the **WindrtActor** previously dropped into the scene and drag it into the level blueprint:</span></span> 

![Arrastrar WinrtActor al plano de nivel](images/unreal-winrt-img-07.png)

3. <span data-ttu-id="2fcb0-165">En el plano de nivel, arrastre el nodo de salida desde WinrtActor, busque el **cuadro de diálogo Abrir archivo** y, a continuación, enrute el nodo desde cualquier entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-165">In the level blueprint, drag the output node from WinrtActor, search for **Open File Dialogue**, then route the node from any user input.</span></span>  <span data-ttu-id="2fcb0-166">En este caso, se llama al cuadro de diálogo Abrir archivo desde un evento de voz:</span><span class="sxs-lookup"><span data-stu-id="2fcb0-166">In this case, Open File Dialogue is being called from a speech event:</span></span> 

![Configuración de nodos en el plano de nivel](images/unreal-winrt-img-08.png)

4. <span data-ttu-id="2fcb0-168">[Empaquete este juego para HoloLens](tutorials/unreal-uxt-ch6.md), impleméntelo y ejecútelo.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-168">[Package this game for HoloLens](tutorials/unreal-uxt-ch6.md), deploy it, and run.</span></span>  

<span data-ttu-id="2fcb0-169">Cuando el método no real llama a OpenFileDialogue, se abre un cuadro de diálogo de archivo en la solicitud de HoloLens para un nombre de archivo. txt.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-169">When Unreal calls OpenFileDialogue, a File Dialogue opens on the HoloLens prompting for a .txt file name.</span></span>  <span data-ttu-id="2fcb0-170">Una vez guardado el archivo, vaya a la pestaña **Explorador de archivos** en el portal de dispositivos para ver el contenido "Hello WinRT".</span><span class="sxs-lookup"><span data-stu-id="2fcb0-170">After the file is saved, go to the **File explorer** tab in the device portal to see the contents “Hello WinRT”.</span></span> 

## <a name="summary"></a><span data-ttu-id="2fcb0-171">Resumen</span><span class="sxs-lookup"><span data-stu-id="2fcb0-171">Summary</span></span> 

<span data-ttu-id="2fcb0-172">Le recomendamos que use el código de este tutorial como punto de partida para el consumo de código de WinRT en un lugar inreal.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-172">We encourage you to use the code in this tutorial as a starting point for consuming WinRT code in Unreal.</span></span>  <span data-ttu-id="2fcb0-173">Permite a los usuarios guardar archivos en el disco de HoloLens con el mismo cuadro de diálogo de archivo que Windows.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-173">It allows users to save files to the HoloLens disk using the same file dialogue as Windows.</span></span>  <span data-ttu-id="2fcb0-174">Siga el mismo proceso para exportar las funciones adicionales del encabezado HoloLensWinrtDLL y usarlas en un momento no real.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-174">Follow the same process to export any additional functions from the HoloLensWinrtDLL header and used in Unreal.</span></span>  <span data-ttu-id="2fcb0-175">Tenga en cuenta el código DLL que espera en cualquier código asincrónico de WinRT en un subproceso MTA en segundo plano, lo que evita el interbloqueo del subproceso de juego inreal.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-175">Note the DLL code that waits on any async WinRT code in a background MTA thread, which avoids deadlocking the Unreal game thread.</span></span> 

## <a name="next-development-checkpoint"></a><span data-ttu-id="2fcb0-176">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="2fcb0-176">Next Development Checkpoint</span></span>

<span data-ttu-id="2fcb0-177">Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-177">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2fcb0-178">Desde aquí, puede pasar a cualquier [tema](unreal-development-overview.md#3-platform-capabilities-and-apis) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.</span><span class="sxs-lookup"><span data-stu-id="2fcb0-178">From here, you can proceed to any [topic](unreal-development-overview.md#3-platform-capabilities-and-apis) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2fcb0-179">Implementación en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="2fcb0-179">Deploying to device</span></span>](unreal-deploying.md)

## <a name="see-also"></a><span data-ttu-id="2fcb0-180">Vea también</span><span class="sxs-lookup"><span data-stu-id="2fcb0-180">See also</span></span>
* [<span data-ttu-id="2fcb0-181">API/WinRT de C++</span><span class="sxs-lookup"><span data-stu-id="2fcb0-181">C++/WinRT APIs</span></span>](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [<span data-ttu-id="2fcb0-182">FileSavePicker (clase)</span><span class="sxs-lookup"><span data-stu-id="2fcb0-182">FileSavePicker class</span></span>](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [<span data-ttu-id="2fcb0-183">Bibliotecas de terceros no reales</span><span class="sxs-lookup"><span data-stu-id="2fcb0-183">Unreal Third-Party Libraries</span></span>](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
