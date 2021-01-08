---
title: Agregar audio espacial al proyecto
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007475"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a>Incorporación de audio espacial al proyecto de Unity

Este es el tutorial de audio espacial para Unity en HoloLens2. Esta secuencia de tutorial muestra:
* Cómo usar la descarga relacionada con la función de transferencia (HRTF) en HoloLens 2 en Unity
* Cómo habilitar la reverberación al usar la descarga de HRTF

El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales. 

Para obtener una descripción sobre lo que significa espaciale los sonidos mediante tecnologías de espacialización basadas en HRTF y recomendaciones para cuando pueda ser útil, consulte [diseño de sonido espacial](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>¿Qué es la descarga de HRTF?

El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculos especializados. HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, por lo que "descarga" el procesamiento de algoritmos basados en HRTF.  El complemento Microsoft spatializer proporciona una manera sencilla para que la aplicación aproveche el hardware de HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no sean de audio espacial.

## <a name="objectives"></a>Objetivos

En este primer capítulo, hará lo siguiente:
* Creación de un proyecto de Unity e importación de MRTK
* Importar el complemento de Microsoft spatializer
* Habilitación del complemento Microsoft spatializer
* Habilitación del audio espacial en la estación de trabajo de desarrollador

## <a name="create-a-project-and-add-nuget-for-unity"></a>Creación de un proyecto y adición de NuGet para Unity

Comience con un proyecto de Unity vacío y, después, agregue y configure NuGet para Unity:
1. Descargue la versión más reciente de [NuGetForUnity. unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)
2. En la barra de menús de Unity, haga clic en **activos > importar paquete > paquete personalizado...** e instalar el paquete NuGetForUnity:

![Importar paquete personalizado](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a>Agregar el paquete de Windows Mixed Reality

La compatibilidad con Windows Mixed Reality en Unity 2019 y versiones posteriores se incluye en un paquete opcional. Para agregarlo al proyecto, abra el **Administrador de paquetes de > de ventana** desde la barra de menús de Unity:

![Menú del administrador de paquetes](images/spatial-audio/package-manager-menu.png)

A continuación, busque e instale el paquete de **Windows Mixed Reality** :

![Ventana del administrador de paquetes](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a>Instalación de MRTK y Microsoft Spatializer

Con NuGet para Unity, instale los complementos de MRTK y Microsoft Spatializer:
1. En la barra de menús de Unity, haga clic en **Nuget-> administrar paquetes NuGet**.

![Administrar paquetes NuGet](images/spatial-audio/manage-nuget-packages.png)

2. En el cuadro de **búsqueda** , escriba "Microsoft. MixedReality. Toolkit" e instale el paquete de MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation** .

![Paquete NuGet de MRTK](images/spatial-audio/mrtk-nuget-package.png)

El [paquete NuGet de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) tiene contexto y detalles adicionales.

4. En el cuadro de **búsqueda** , escriba "Microsoft. SpatialAudio" e instale el paquete de Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity** .

![Complemento NuGet de Spatializer](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a>Configuración de MRTK en el proyecto

1. Para abrir la ventana Configuración de compilación, vaya a **archivo-> configuración de compilación**.

2. Seleccione la _plataforma universal de Windows_ y haga clic en **cambiar plataforma**.

3. Haga clic en **configuración del reproductor** en la **ventana compilar** para abrir las propiedades de **configuración del reproductor** en el panel **Inspector** .
    * En **configuración de XR**, active la casilla **compatible con realidad virtual**
    * En **configuración de XR**, cambie el **modo de representación de estéreo** a instancia de **paso único**.
    * En **configuración de publicación**, active la casilla **percepción espacial** en la sección **capacidades** .

4. En la barra de menús, haga clic en **Kit de herramientas de realidad mixta: > agregar a la escena y configurar.** para agregar MRTK a la escena.

Para obtener instrucciones adicionales, incluida la forma de compilar la aplicación e implementarla en HoloLens 2, consulte [el capítulo 1 del módulo de base de aprendizaje Mr](../../../mrlearning-base-ch1.md).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitación del complemento Microsoft Spatializer

Habilite el complemento de **Microsoft Spatializer** . Abra **editar > configuración del proyecto-> audio** y cambie el **complemento Spatializer** a "Microsoft Spatializer". La sección **audio** de la **configuración del proyecto** tendrá ahora el siguiente aspecto:

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitación del audio espacial en la estación de trabajo

En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada. Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas. Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares**.

![Configuración de audio espacial de escritorio](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Audio espacial de Unity capítulo 2](unity-spatial-audio-ch2.md)

