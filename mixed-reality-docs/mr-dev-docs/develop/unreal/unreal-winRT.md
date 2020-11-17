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
# <a name="winrt-in-unreal"></a>WinRT en Unreal

## <a name="overview"></a>Información general

En el transcurso del desarrollo de HoloLens, puede que tenga que escribir una característica con WinRT. Por ejemplo, al abrir un cuadro de diálogo de archivo en una aplicación de HoloLens, se necesitaría el archivo de encabezado FileSavePicker en winrt/Windows. Storage. Picker. h.  Puesto que no real no compila código WinRT de forma nativa, es su trabajo crear un binario independiente y que el sistema de compilación no es el que puede consumir. Este tutorial le guiará a través de este escenario.

## <a name="objectives"></a>Objetivos
- Crear un archivo DLL de Windows universal que abra un FileSaveDialogue
- Vincular el archivo DLL a un proyecto de juego inreal
- Guardar un archivo en HoloLens desde un Blueprint real mediante el nuevo archivo DLL

## <a name="getting-started"></a>Introducción
1. Compruebe que tiene instaladas todas las [herramientas necesarias](tutorials/unreal-uxt-ch1.md) .
2. [Cree un nuevo proyecto inreal](tutorials/unreal-uxt-ch2.md#creating-a-new-unreal-project) y asígnele el nombre **Consumewinrt**
3. Habilitación de los [Complementos necesarios](tutorials/unreal-uxt-ch2.md#enabling-required-plugins) para el desarrollo de HoloLens
4. [Configuración para la implementación](tutorials/unreal-uxt-ch6.md) en un dispositivo o emulador

## <a name="creating-a-winrt-dll"></a>Creación de un archivo DLL de WinRT 
1. Abra un nuevo proyecto de Visual Studio y cree un proyecto **dll (universal Windows)** en el mismo directorio que el archivo **uproject** del juego no real. 

![Crear un archivo DLL](images/unreal-winrt-img-01.png)

2. Asigne al proyecto el nombre **HoloLensWinrtDLL** y establezca la ubicación como un subdirectorio **ThirdParty** en el archivo uproject del juego inreal. 
    * Seleccione **colocar solución y proyecto en el mismo directorio** para simplificar la búsqueda de rutas de acceso más adelante. 

![Configurar el archivo DLL](images/unreal-winrt-img-02.png)

> [!IMPORTANT]
> Una vez que se compila el nuevo proyecto, desea prestar especial atención a los archivos CPP y de encabezado en blanco, denominados **HoloLensWinrtDLL. cpp** y **HoloLensWinrtDLL. h** , respectivamente. El encabezado es el archivo de inclusión que usa el archivo DLL en el modo inreal, mientras que el CPP contiene el cuerpo de las funciones exportadas e incluye cualquier código de WinRT que no se pueda compilar de otra manera. 

3. Antes de agregar cualquier código, debe actualizar las propiedades del proyecto para asegurarse de que el código de WinRT que necesita puede compilar: 
    * Haga clic con el botón derecho en el proyecto HoloLensWinrtDLL y seleccione **propiedades** .  
    * Cambie la lista desplegable **configuración** a **todas las configuraciones** y la lista desplegable **plataforma** a **todas las plataformas** .  
    * En **propiedades de configuración> C/C++> todas las opciones**:
        * Agregue **Await** a **opciones adicionales** para asegurarse de que se puede esperar en tareas asincrónicas  
        * Cambiar **estándar de lenguaje c++** a **estándar ISO C++ 17 (/STD: C++ 17)** para incluir cualquier código WinRT

![Actualización de las propiedades del proyecto](images/unreal-winrt-img-03.png)

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

![Creación de un nuevo actor](images/unreal-winrt-img-04.png)

> [!NOTE]
> Ahora se ha creado una solución en el mismo directorio que el archivo uproject, junto con un nuevo script de compilación denominado Source/ConsumeWinRT/ConsumeWinRT. Build. cs.

2. Abra la solución, busque la carpeta **Games/ConsumeWinRT/Source/ConsumeWinRT** y Abra **ConsumeWinRT.Build.CS**:

![Abrir el archivo ConsumeWinRT.build.cs](images/unreal-winrt-img-05.png)

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

![Colocar WinrtActor en la escena](images/unreal-winrt-img-06.png)

2. En el **contorno mundial**, busque el **WindrtActor** previamente colocado en la escena y arrástrelo al plano de nivel: 

![Arrastrar WinrtActor al plano de nivel](images/unreal-winrt-img-07.png)

3. En el plano de nivel, arrastre el nodo de salida desde WinrtActor, busque el **cuadro de diálogo Abrir archivo** y, a continuación, enrute el nodo desde cualquier entrada del usuario.  En este caso, se llama al cuadro de diálogo Abrir archivo desde un evento de voz: 

![Configuración de nodos en el plano de nivel](images/unreal-winrt-img-08.png)

4. [Empaquete este juego para HoloLens](tutorials/unreal-uxt-ch6.md), impleméntelo y ejecútelo.  

Cuando el método no real llama a OpenFileDialogue, se abre un cuadro de diálogo de archivo en la solicitud de HoloLens para un nombre de archivo. txt.  Una vez guardado el archivo, vaya a la pestaña **Explorador de archivos** en el portal de dispositivos para ver el contenido "Hello WinRT". 

## <a name="summary"></a>Resumen 

Le recomendamos que use el código de este tutorial como punto de partida para el consumo de código de WinRT en un lugar inreal.  Permite a los usuarios guardar archivos en el disco de HoloLens con el mismo cuadro de diálogo de archivo que Windows.  Siga el mismo proceso para exportar las funciones adicionales del encabezado HoloLensWinrtDLL y usarlas en un momento no real.  Tenga en cuenta el código DLL que espera en cualquier código asincrónico de WinRT en un subproceso MTA en segundo plano, lo que evita el interbloqueo del subproceso de juego inreal. 

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar las API y funcionalidades de la plataforma de realidad mixta. Desde aquí, puede pasar a cualquier [tema](unreal-development-overview.md#3-platform-capabilities-and-apis) o ir directamente a la implementación de la aplicación en un dispositivo o emulador.

> [!div class="nextstepaction"]
> [Implementación en el dispositivo](unreal-deploying.md)

## <a name="see-also"></a>Vea también
* [API/WinRT de C++](https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/)
* [FileSavePicker (clase)](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) 
* [Bibliotecas de terceros no reales](https://docs.unrealengine.com/Programming/BuildTools/UnrealBuildTool/ThirdPartyLibraries/index.html) 
