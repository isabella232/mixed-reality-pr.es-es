---
title: 'Tutoriales de audio espacial: 1. Agregar audio espacial al proyecto'
description: Agregue el complemento de Microsoft Spatializer a su proyecto de Unity para acceder a la descarga de hardware de HoloLens 2 HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality, Unity, tutorial, hololens2, audio espacial, MRTK, kit de herramientas de realidad mixta, UWP, Windows 10, HRTF, función de transferencia relacionada con el encabezado, reverberación, Microsoft Spatializer
ms.openlocfilehash: cc7a4db5a3b4d853f2912a5e8e022fddd372e105
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635393"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. agregar audio espacial a su proyecto de Unity

## <a name="overview"></a>Información general

Este es el tutorial de audio espacial para Unity en HoloLens2. A través de esta serie de tutoriales, aprenderá a usar la descarga de la función de transferencia relacionada con el encabezado (HRTF) en HoloLens 2 y cómo habilitar reverberación al usar la descarga de HRTF.

El [repositorio de github de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutoriales.

Para obtener una descripción de lo que significa para espaciales con las tecnologías de espacialización basadas en HRTF y las recomendaciones para cuando pueda ser útil, consulte [diseño de sonido espacial](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>¿Qué es la descarga de HRTF?

El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculos especializados. HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, por lo que "descarga" el procesamiento de algoritmos basados en HRTF.  El complemento Microsoft spatializer proporciona una manera sencilla para que la aplicación aproveche el hardware de HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no sean de audio espacial.

## <a name="objectives"></a>Objetivos

* Importación y habilitación del complemento de Microsoft spatializer
* Habilitación del audio espacial en la estación de trabajo de desarrollador

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)
* Conocimientos básicos de programación de C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS montado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

Se **recomienda** completar la serie de tutoriales de [Introducción](mr-learning-base-01.md) o tener una experiencia previa básica con Unity y MRTK antes de continuar.

> [!IMPORTANT]
>
> * La versión de Unity recomendada para esta serie de tutoriales es Unity 2019 LTS. Sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*

1. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importar Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [Configurar el proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project)

1. [Crear y establecer la escena](mr-learning-base-02.md#creating-and-configuring-the-scene) y asignar a la escena un nombre adecuado, por ejemplo, *SpatialAudio*

Después, siga las instrucciones de la [opción de visualización cambiar el reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK para la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **oclusión**.

## <a name="adding-microsoft-spatializer-to-the-project"></a>Agregando Microsoft Spatializer al proyecto

Descargue e importe Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. unitypackage Tools </a>

>[!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitación del complemento Microsoft Spatializer

Después de importar la **Spatializer de Microsoft** , debe habilitarla. Abra **editar > configuración del proyecto-> audio** y cambie el **complemento Spatializer** a "Microsoft Spatializer".

![Configuración del proyecto que muestra el complemento spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitación del audio espacial en la estación de trabajo

En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada. Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas. Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **sonido espacial > Windows Sonic para auriculares**.

![Configuración de audio espacial de escritorio](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> Esta configuración solo es necesaria si tiene previsto probar el proyecto en el editor de Unity.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprenderá a importar y habilitar el complemento Microsoft Spatializer y también a habilitar el audio espacial en la estación de trabajo.
En el siguiente tutorial, aprenderá a agregar audio espacial en el proyecto de Unity.

> [!div class="nextstepaction"]
> [Siguiente tutorial: 2. Spatial los sonidos de interacción del botón](unity-spatial-audio-ch2.md)
