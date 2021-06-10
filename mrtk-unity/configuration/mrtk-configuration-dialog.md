---
title: Cuadro de diálogo de configuración de MRTK
description: Configuración de MRTK en el proyecto de Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Unity
ms.openlocfilehash: fd05f7f3b579522a1225e11b0411b255a43e1e3f
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345098"
---
# <a name="mrtk-project-configuration-dialog"></a>Cuadro de diálogo de configuración del proyecto de MRTK

El cuadro de diálogo de configuración de MRTK se muestra cuando Unity carga un proyecto y se determina que una o varias opciones de configuración necesitan la atención del desarrollador.

![Aplicar ignore posterior](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

Para aplicar los cambios, haga clic en **el botón** Aplicar. El **botón** Más adelante aplazará los cambios hasta que el proyecto se vuelva a cargar en un momento futuro.

> [!NOTE]
> El cuadro de diálogo de configuración volverá a aparecer si se deja desactivada una o varias de las opciones recomendadas. Para evitar que esto ocurra, aplique las opciones deseadas y, a continuación, vuelva a iniciar el cuadro de diálogo a través de utilidades de **Mixed Reality Toolkit** Configure Unity Project (Configurar proyecto de  >    >  **Unity)** y haga clic **en Omitir**. Esto impedirá que el cuadro de diálogo de configuración vuelva a aparecer automáticamente.

## <a name="common-settings"></a>Configuración común

Todos los destinos de compilación comparten una colección de opciones comunes.

![Configuración común](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a>Forzar la serialización de recursos de texto y Habilitar metadatos visibles

Esta configuración ayuda a simplificar el trabajo con proyectos de Unity y sistemas de control de código fuente (por ejemplo, Git).

### <a name="enable-vr-supported"></a>Habilitación de VR compatible

**Unity 2018**

Configura las opciones Del SDK de Virtual Reality Compatible y Virtual Reality en **Configuración del** reproductor Configuración  >  **de XR.**

### <a name="set-single-pass-instanced-rendering-path"></a>Establecer la ruta de acceso de representación de instancia de paso único

Configura la configuración del **reproductor XR** Settings Stereo Rendering Mode (Modo de representación estéreo de configuración de  >  **XR)**  >   en Single **Pass Instanced (Instancia de paso único).**

### <a name="set-default-spatial-awareness-layer"></a>Establecer la capa de reconocimiento espacial predeterminada

Registra el reconocimiento espacial como nivel 31 para permitir una configuración sencilla y coherente de las opciones de difusión por rayos y física.

### <a name="audio-spatializer"></a>Espacializador de audio

Los espacializadores de audio son los componentes que desbloquean la potencia del sonido espacial y el audio posicional para que las experiencias de realidad mixta sean realmente envolventes.

> [!NOTE]
> Si establece el espacializador de audio en Ninguno, se deshabilitarán las características de audio posicionales.

#### <a name="common-spatializers"></a>Espacializadores comunes

- Microsoft Spatializer

Espacializador proporcionado por Microsoft que admite el uso de la aceleración de hardware en HoloLens 2.

Este espacializador está disponible a través [de NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) y [GitHub.](https://github.com/microsoft/spatialaudio-unity)

Puede encontrar más detalles sobre Microsoft Spatializer en la documentación [de sonido espacial](/windows/mixed-reality/spatial-sound-in-unity).

- Espacializador HRTF de MS

Espacializador de Microsoft Windows proporcionado por Unity como parte de los paquetes Windows Mixed Reality y windows XR Platform.

- Audio desaía

Espacializador multiplataforma de Google proporcionado por Unity.

Puede encontrar más información en el sitio de documentación [de Audio de resalte.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)

## <a name="universal-windows-platform-settings"></a>Plataforma universal de Windows configuración

![Configuración de UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a>Funcionalidades de UWP

Habilita funcionalidades de aplicación específicas para Plataforma universal de Windows aplicación. Estas funcionalidades permiten a la plataforma informar y solicitar permiso para habilitar una funcionalidad específica.

- Micrófono

  Habilita la captura de sonido a través del micrófono.

- Cliente de Internet

  Habilita la compatibilidad con el acceso a los recursos en Internet.

- Percepción espacial

  Habilita la compatibilidad con el uso del entorno real.

- Mirada con los ojos

  **Unity 2019.3 y versiones más recientes**

  Habilita la compatibilidad para realizar el seguimiento de la mirada con los ojos del usuario.

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a>Evitar el bloqueo "PlayerSettings.graphicsJob" de Unity

**Unity 2019.3 y versiones más recientes**

En la versión más reciente de Unity 2019, cuando se habilita "Trabajos de gráficos", la aplicación se bloqueará cuando se implemente en un HoloLens 2.
Esta configuración está habilitada de forma predeterminada en Unity: aunque este error existe (consulte Error de [Unity),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)el configurador establecerá de forma predeterminada trabajos de gráficos en "false" (lo que permite que las aplicaciones implementadas en HoloLens 2 no se bloquean).

## <a name="android-settings"></a>Configuración de Android

Opciones de configuración para admitir aplicaciones de AR en dispositivos con tecnología Android.

![Configuración de Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a>Deshabilitar la representación multiproceso

Deshabilita la **configuración del reproductor Otra**  >  **configuración**  >  **Representación multiproceso** según sea necesario para la compatibilidad con AR de Android.

### <a name="set-minimum-api-level"></a>Establecer el nivel mínimo de API

Establece el valor de Configuración del **reproductor** Otro  >  **nivel** mínimo  >  **de API para** aplicar los requisitos del sistema operativo para las aplicaciones de AR.

## <a name="ios-settings"></a>Configuración de iOS

Opciones de configuración para admitir aplicaciones ar en dispositivos con tecnología iOS.

![Configuración de iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a>Establecer la versión necesaria del sistema operativo

Establece el valor de Configuración del **reproductor**  >  **Otras configuraciones** Versión mínima de  >  **iOS para** aplicar los requisitos del sistema operativo para las aplicaciones de AR.

### <a name="set-required-architecture"></a>Establecer la arquitectura necesaria

Establece el valor de Configuración del **reproductor** Otra  >  **arquitectura de configuración**  >  **para** aplicar los requisitos de plataforma para las aplicaciones de AR.

### <a name="set-camera-usage-descriptions"></a>Establecer descripciones de uso de la cámara

Establece el valor de Player **Settings** Other Settings Camera Usage Description (Configuración del reproductor Descripción del uso de la cámara de configuración que se usa para solicitar  >    >   permiso para usar la cámara del dispositivo).