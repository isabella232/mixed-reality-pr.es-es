---
title: 'Tutoriales de audio espacial: 1. Adición de audio espacial al proyecto'
description: Agregue el complemento Microsoft Spatializer al proyecto de Unity para acceder a HoloLens 2 descarga de hardware HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403366"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a>1. Adición de audio espacial al proyecto de Unity

## <a name="overview"></a>Información general

Le damos la bienvenida al tutorial de audio espacial para Unity en HoloLens2. A través de esta serie de tutoriales, aprenderá a usar la descarga de la función de transferencia relacionada con la cabeza (HRTF) en HoloLens 2 y a habilitar la reverberación al usar la descarga de HRTF.

El [repositorio de GitHub de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) tiene un proyecto de Unity completado de esta secuencia de tutorial.

Para comprender lo que significa espacializar sonidos mediante tecnologías de espacialización basadas en HRTF y recomendaciones para cuándo puede ser útil, consulte [diseño de sonido espacial](/windows/mixed-reality/spatial-sound-design).

## <a name="what-is-hrtf-offload"></a>¿Qué es la descarga de HRTF?

El procesamiento de audio mediante algoritmos basados en HRTF requiere una gran cantidad de cálculo especializado. HoloLens 2 incluye hardware dedicado que se puede usar para evitar sobrecargar el procesador de aplicaciones, lo que "descarga" el procesamiento de algoritmos basados en HRTF.  El complemento espacializador de Microsoft proporciona una manera sencilla de que la aplicación aproveche el hardware HRTF dedicado para que la aplicación pueda usar más del procesador de aplicaciones para operaciones que no son el audio espacial.

## <a name="objectives"></a>Objetivos

* Importación y habilitación del complemento espacializador de Microsoft
* Habilitación del audio espacial en la estación de trabajo para desarrolladores

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)
* Conocimientos básicos de programación de C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS montado y el módulo de compatibilidad Plataforma universal de Windows compilación agregado

Se **recomienda encarecidamente completar** la serie [de](mr-learning-base-01.md) tutoriales de introducción o tener alguna experiencia previa básica con Unity y MRTK antes de continuar.

> [!Important]
> Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o windows XR Plugin y también Unity 2019 LTS (actualmente 2019.4.x) si usa el complemento WSA o Windows XR heredado. Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*

1. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)

1. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [Importación de Mixed Reality Toolkit y configuración del proyecto de Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. [Crear y configurar la escena y](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) dar a la escena un nombre adecuado, por ejemplo, *SpatialAudio*

A continuación, siga las instrucciones de Cambio de la opción [de](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) visualización de reconocimiento espacial para asegurarse de que el perfil de configuración de MRTK de la escena es **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **Oclusión.**

## <a name="adding-microsoft-spatializer-to-the-project"></a>Agregar Microsoft Spatializer al proyecto

Descargue e importe Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a>

>[!TIP]
> Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](mr-learning-base-02.md#importing-the-tutorial-assets).

## <a name="enable-the-microsoft-spatializer-plugin"></a>Habilitación del complemento Microsoft Spatializer

Una vez que importe Microsoft Spatializer en el proyecto de Unity, aparecerá la ventana **MrTK Project Configurator** (Configurador de proyectos de MRTK), use la lista desplegable **Espacializador** de audio para seleccionar **Microsoft Spatializer** y, a continuación, haga clic en el botón Aplicar para aplicar la configuración:

![Configurador de proyectos de MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

También puede habilitar manualmente Microsoft **Spatializer:** abra **Editar -> Configuración** del proyecto -> Audio y cambie el complemento Spatializer a "Microsoft Spatializer".

![Configuración del proyecto que muestra el complemento espacializador](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a>Habilitación del audio espacial en la estación de trabajo

En las versiones de escritorio de Windows, el audio espacial está deshabilitado de forma predeterminada. Para habilitarlo, haga clic con el botón derecho en el icono de volumen de la barra de tareas. Para obtener la mejor representación de lo que oirá en HoloLens 2, elija **Spatial sound -> Windows Sonic para auriculares**.

![Configuración de audio espacial de escritorio](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> Esta configuración solo es necesaria si planea probar el proyecto en el editor de Unity.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido a importar y habilitar el complemento Espacializer de Microsoft y también a habilitar el audio espacial en la estación de trabajo.
En el siguiente tutorial, aprenderá a agregar audio espacial en el proyecto de Unity.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 2. Espacialización de los sonidos de interacción del botón](unity-spatial-audio-ch2.md)
