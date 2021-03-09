---
title: Documentación para desarrolladores de MRTK-Unity
description: Obtenga información sobre Mixed Reality Toolkit para Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 3ac16a1aae6681ddd7e144679b76b4d2b778306f
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237256"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>¿Qué es Mixed Reality Toolkit?

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

MRTK Unity es un proyecto controlado por Microsoft que proporciona un conjunto de componentes y características para acelerar el desarrollo de aplicaciones de MR multiplataforma en Unity. Estas son algunas de sus funciones:

* Proporciona el **sistema de entrada multiplataforma y los bloques de creación para las interacciones espaciales y la interfaz de usuario**.
* Permite la **creación rápida de prototipos** gracias a la simulación en el editor, que permite ver los cambios inmediatamente.
* Funciona como **plataforma extensible** que permite a los desarrolladores intercambiar los componentes principales.
* **Es compatible con una amplia gama de plataformas**, entre las que se incluyen:
  * OpenXR (Unity 2020.2 o posterior)
    * Microsoft HoloLens 2
    * Cascos de Windows Mixed Reality
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Cascos de Windows Mixed Reality
  * Oculus (Unity 2019.3 o posterior)
    * Oculus Quest
  * OpenVR
    * Cascos de Windows Mixed Reality
    * HTC Vive
    * Oculus Rift
  * Seguimiento de manos de Ultraleap
  * Dispositivos móviles, como iOS y Android

## <a name="getting-started-with-mrtk"></a>Introducción a MRTK

Si no está familiarizado con MRTK ni el desarrollo para realidad mixta en Unity, se recomienda instalar las herramientas necesarias y seguir la serie de tutoriales de HoloLens 2.

> [!div class="nextstepaction"]
> [Instalar las herramientas](install-the-tools.md)

> [!div class="nextstepaction"]
> [Serie de tutoriales de HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

¿Quiere conocer lo que se esconde bajo la superficie?
> [!div class="nextstepaction"]
> [Explorar MRTK en GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Documentación

| [![Notas de la versión](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-26-release-notes.md)<br/>[Notas de la versión](release-notes/mrtk-26-release-notes.md)| [![Información general de MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Información general de MRTK](architecture/overview.md)|[![Referencia de API](features/images/MRTK_Icon_APIReference.png)](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[Referencia de API](https://docs.microsoft.com/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>Estado de la compilación

| Rama | Estado de CI | Estado del documento |
|---|---|---|
| `mrtk_development` |[![Estado de CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Estado del documento](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Áreas de características

:::row:::
    :::column:::
       [![Sistema de entrada](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md) **[Sistema de entrada](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Seguimiento de manos (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md) **[Seguimiento de manos <br> (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Seguimiento ocular (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md) **[Seguimiento ocular <br/> (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Perfiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md) **[Perfiles](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Seguimiento de manos (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](features/cross-platform/leap-motion-mrtk.md) **[Seguimiento de manos <br/> (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![Controles de UI](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks) **[Controles de UI](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Solucionadores](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md) **[Solucionadores](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Administrador multiescena](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md) **[Administrador<br/> multiescena](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Reconocimiento espacial](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Reconocimiento <br/> espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Herramienta de diagnóstico](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md) **[Herramienta de <br/> diagnóstico](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Vista del sombreador MRTK Standard](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader) **[Vista de ejemplo del sombreador MRTK Standard](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Voz y dictado](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md) **[Voz](features/input/speech.md)<br/>y [dictado](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Sistema de límites](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md) **[Sistema de <br/>límites](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Simulación en el editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md) **[Simulación <br/> en el editor](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Características experimentales](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md) **[Características <br/> experimentales](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>Bloques de creación de la experiencia de usuario

:::row:::
    :::column:::
       [![Botón](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Botón](features/ux-building-blocks/button.md)**<br>
        Control de botón que admite varios métodos de entrada, incluida la mano articulada de HoloLens 2.
    :::column-end:::
    :::column:::
        [![Control de límites](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Control de límites](features/ux-building-blocks/bounds-control.md)**<br>
        Interfaz de usuario estándar para manipular objetos en el espacio 3D.
    :::column-end:::
    :::column:::
        [![Manipulador de objetos](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipulador de objetos](features/ux-building-blocks/object-manipulator.md)**<br>
        Script para manipular objetos con una o dos manos.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Claqueta](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Claqueta](features/ux-building-blocks/slate.md)**<br>
        Plano de estilo 2D que admite el desplazamiento con la entrada de mano articulada.
    :::column-end:::
    :::column:::
        [![Teclado del sistema](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) **[Teclado del sistema](features/ux-building-blocks/system-keyboard.md)**<br>
        Ejemplo de script de uso del teclado del sistema en Unity.
    :::column-end:::
    :::column:::
        [![Interactuable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactuable](features/ux-building-blocks/interactable.md)**<br>
        Un script para que los objetos interactúen con los estados visuales y la compatibilidad con temas.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Solucionador](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[Solucionador](features/ux-building-blocks/solvers/solver.md)**<br>
        Varios comportamientos de posicionamiento de objetos, como etiquetado, bloqueo del cuerpo, tamaño de vista constante y magnetismo de la superficie.
    :::column-end:::
    :::column:::
        [![Colección de objetos](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[Colección de objetos](features/ux-building-blocks/object-collection.md)**<br>
        Script para diseñar una matriz de objetos en una forma tridimensional.
    :::column-end:::
    :::column:::
        [![Información sobre herramientas](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[Información sobre herramientas](features/ux-building-blocks/tooltip.md)**<br>
        Interfaz de usuario de anotación con un sistema flexible de anclaje/dinamización que se puede usar para etiquetar controladores de movimiento y objetos.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Control deslizante](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[Control deslizante](features/ux-building-blocks/sliders.md)**<br>
        Interfaz de usuario del control deslizante para ajustar los valores que admiten la interacción directa de seguimiento de manos.
    :::column-end:::
    :::column:::
        [![Sombreador MRTK Standard](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[Sombreador MRTK Standard](features/rendering/mrtk-standard-shader.md)**<br>
        El sombreador MRTK Standard admite varios elementos de diseño de Fluent con rendimiento.
    :::column-end:::
    :::column:::
        [![Menú Mano](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) **[Menú Mano](features/ux-building-blocks/hand-menu.md)**<br>
        Interfaz de usuario bloqueada manualmente para un acceso rápido mediante el solucionador de restricciones de la mano.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Barra de aplicaciones](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[Barra de aplicaciones](features/ux-building-blocks/app-bar.md)**<br>
        Interfaz de usuario para la activación manual del control de límites.
    :::column-end:::
    :::column:::
        [![Punteros](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[Punteros](features/input/pointers.md)**<br>
        Información sobre los distintos tipos de punteros.
    :::column-end:::
    :::column:::
        [![Visualización de la punta del dedo](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualización de la punta del dedo](features/ux-building-blocks/fingertip-visualization.md)**<br>
        Prestación visual de la punta del dedo, lo que mejora la confianza para la interacción directa.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Menú Cerca](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[Menú Cerca](features/ux-building-blocks/near-menu.md)**<br>
        Interfaz de usuario de menú flotante para las interacciones cercanas.
    :::column-end:::
    :::column:::
        [![Introducción al reconocimiento espacial](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) **[Vista de reconocimiento espacial](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Haga que los objetos holográficos interactúen con los entornos físicos.
    :::column-end:::
    :::column:::
        [![Comando de voz](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Comando de voz](features/input/speech.md)**<br>
        Scripts y ejemplos para integrar la entrada de voz.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Indicador de progreso](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) **[Indicador de progreso](features/ux-building-blocks/progress-indicator.md)**<br>
        Indicador visual para comunicar el proceso o la operación de datos.
    :::column-end:::
    :::column:::
        [![Cuadro de diálogo](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[Cuadro de diálogo](features/ux-building-blocks/dialog.md)**<br>
        Interfaz de usuario para solicitar confirmación o reconocimiento del usuario.
    :::column-end:::
    :::column:::
        [![Asesor manual](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Asesor manual](features/ux-building-blocks/hand-coach.md)**<br>
        Componente que ayuda a guiar al usuario cuando no se ha enseñado el gesto.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Servicio de la física de la mano](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) **[Servicio de la física de la mano [experimental]](features/experimental/hand-physics-service.md)**<br>
        El servicio de la física de la mano permite eventos e interacciones de colisión de cuerpos rígidos con manos articuladas.
    :::column-end:::
    :::column:::
        [![Desplazamiento por la colección](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Desplazamiento por la colección](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Colección de objetos que desplaza objetos 3D de forma nativa.
    :::column-end:::
    :::column:::
        [![Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [experimental]](features/experimental/dock.md)**<br>
        Dock permite que los objetos entren y salgan de las posiciones predeterminadas.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Seguimiento ocular: selección de destino](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[Seguimiento ocular: selección de destino](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Combine la entrada ocular, de voz y de manos para seleccionar los hologramas de forma rápida y sencilla a lo largo de la escena.
    :::column-end:::
    :::column:::
        [![Seguimiento ocular: navegación](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[Seguimiento ocular: navegación](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Aprenda sobre cómo desplazarse por texto automáticamente o acercar de forma fluida el contenido donde está el foco en función de lo que está examinando.
    :::column-end:::
    :::column:::
        [![Seguimiento ocular: mapa térmico](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[Seguimiento ocular: mapa térmico](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Ejemplos para registrar, cargar y visualizar lo que los usuarios han estado examinando en la aplicación.
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Herramientas

|  [![Optimizar ventana](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [Optimizar ventana](features/tools/optimize-window.md) | [![Ventana de dependencia](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [Ventana de dependencia](features/tools/dependency-window.md) | ![Ventana de compilación](features/images/MRTK_Icon_BuildWindow.png) Ventana de compilación | [![Grabación de entrada](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) [Grabación de entrada](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatice la configuración de proyectos de Mixed Reality para optimizar el rendimiento. | Analice las dependencias entre recursos e identifique los recursos sin usar. |  Configure y ejecute un proceso de compilación de un extremo a otro para aplicaciones de realidad mixta. | Grabe y reproduzca los datos de movimiento y seguimiento de manos en el editor. |

## <a name="example-scenes"></a>Escenas de ejemplo

Explore los distintos tipos de interacciones y controles de interfaz de usuario de MRTK en [esta escena de ejemplo](features/example-scenes/hand-interaction-examples.md).

[![Escenas de ejemplo 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>MRTK Examples Hub

Con MRTK Examples Hub, puede probar varias escenas de ejemplo en MRTK.
Puede descargar paquetes de aplicaciones pregenerados para HoloLens (x86), HoloLens 2 (ARM) y cascos envolventes de Windows Mixed Reality (x64); para ello, seleccione el paquete "Ejemplos de Mixed Reality Toolkit" en [MR Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Asegúrese de [usar el Portal de dispositivos Windows para instalar aplicaciones en HoloLens (1.ª generación)](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). En HoloLens 2, puede descargar e instalar [MRTK Examples Hub a través de Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Consulte la [página Léame de Examples Hub](features/example-scenes/example-hub.md) para obtener información sobre cómo crear un centro de varias escenas con el sistema de escenas y el servicio de transición de escenas de MRTK.

[![Centro de escenas de ejemplo](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>Aplicaciones de ejemplo hechas con MRTK

| [![Tabla periódica de los elementos](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Explorador de la galaxia](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Aplicación de ejemplo Surfaces](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [Periodic Table of the Elements](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) es una aplicación de ejemplo de código abierto que muestra cómo usar el sistema de entrada de MRTK y los bloques de creación para crear una experiencia de aplicación para HoloLens y cascos envolventes. Lea la historia de la migración: [Incorporación de la aplicación Periodic Table of the Elements a HoloLens 2 con MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158). |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) es una aplicación de ejemplo de código abierto que se desarrolló originalmente en marzo de 2016 como parte de la campaña "Share Your Idea" de HoloLens. Galaxy Explorer se ha actualizado con las nuevas características de HoloLens 2, mediante MRTK v2. Lea la historia: [La creación de Galaxy Explorer para HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update). |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) es una aplicación de ejemplo de código abierto para HoloLens 2, que explora cómo podemos crear una sensación táctil con entrada visual, de audio y seguimiento de manos totalmente articuladas. Consulte [Aprendizajes de la aplicación Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) de la sesión Microsoft MR Dev Days para obtener información sobre el diseño y la historia de desarrollo. |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Vídeos de sesión de Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Tutorial sobre cómo crear una sencilla aplicación de MRTK de principio a fin. Obtenga información sobre los conceptos de interacción y las funcionalidades multiplataforma de MRTK. | Profundice en los bloques de creación de la experiencia de usuario de MRTK que le ayudarán a crear fantásticas experiencias de realidad mixta. | Introducción a las herramientas de rendimiento, tanto de MRTK como externas, e información general sobre el sombreador estándar de MRTK. |

Consulte [Mixed Reality Dev Days](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) para explorar más vídeos de sesiones.

## <a name="engage-with-the-community"></a>Interacción con la comunidad

* Únase a la conversación en torno a MRTK en [Slack](https://holodevelopers.slack.com/). Puede unirse a la comunidad de Slack a través del [remitente de invitación automática](https://holodevelopersslack.azurewebsites.net/).

* Formule preguntas sobre el uso de MRTK en [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) con la etiqueta **MRTK**.

* Busque [problemas conocidos](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) o presente un [nuevo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si encuentra algo mal en el código de MRTK.

* Si tiene preguntas sobre cómo contribuir con MRTK, vaya al canal [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) en Slack.

El proyecto ha adoptado el [Código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para obtener más información, vea las [Preguntas más frecuentes sobre el código de conducta](https://opensource.microsoft.com/codeofconduct/faq/), o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene preguntas o comentarios.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Recursos útiles en el Centro de desarrollo de realidad mixta

| ![Descubrir](features/images/mrdevcenter/icon-discover.png) [Descubrir](https://docs.microsoft.com/windows/mixed-reality/)| ![Diseñar](features/images/mrdevcenter/icon-design.png) [Diseñar](https://docs.microsoft.com/windows/mixed-reality/design)| ![Desarrollar](features/images/mrdevcenter/icon-develop.png) [Desarrollar](https://docs.microsoft.com/windows/mixed-reality/development)| ![Distribuir](features/images/mrdevcenter/icon-distribute.png) [Distribuir](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Aprende a crear experiencias de realidad mixta para HoloLens y cascos envolventes (VR).          | Obtenga guías de diseño. Cree interfaces de usuario. Aprenda sobre interacciones y entradas.     | Obtenga guías de desarrollo. Aprenda sobre la tecnología. Aprenda sobre la ciencia.       | Haga que la aplicación esté disponible para otros usuarios y considere la posibilidad de crear un iniciador 3D. |

## <a name="useful-resources-on-azure"></a>Recursos útiles en Azure

| ![Spatial Anchors](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/)| ![Servicios de Voz](features/images/mrdevcenter/icon-azurespeechservices.png) [Speech Services](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![Servicios de visión](features/images/mrdevcenter/icon-azurevisionservices.png) [Servicios de visión](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Spatial Anchors es un servicio multiplataforma que le permite crear experiencias de realidad mixta mediante objetos que conservan su ubicación en los dispositivos y a lo largo del tiempo.| Conozca e integre en su aplicación las funcionalidades de voz con tecnología de Azure como, por ejemplo, conversión de voz a texto, reconocimiento del hablante o traducción de voz.| Identifique y analice el contenido de sus imágenes o vídeos mediante servicios de visión como Computer Vision, detección de caras, reconocimiento de emociones o indexador de vídeo. |

## <a name="how-to-contribute"></a>Cómo contribuir

Obtenga información sobre cómo contribuir a MRTK en [Colaboración](contributing/contributing.md).

## <a name="getting-help"></a>Ayuda

Si surgen problemas debido a MRTK o tiene dudas sobre cómo hacer algo, hay algunos recursos que pueden resultar útiles:

* Para notificar errores, [registre un problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) en el repositorio de GitHub.
* Si tiene alguna pregunta, póngase en contacto con [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o con el [canal mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) en Slack. Puede unirse a la comunidad de Slack a través del [remitente de invitación automática](https://holodevelopersslack.azurewebsites.net/).
