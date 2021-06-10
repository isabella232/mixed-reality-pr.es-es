---
title: Notas de la versión de MRTK 2.6
description: Notas de la versión 2.6 de MRTK
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 4ac82f7e07135e840886fef810844ff00ef1ac1e
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647192"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Notas de la versión de Microsoft Mixed Reality Toolkit 2.6

> [!IMPORTANT]
> Hay un problema conocido del compilador que afecta a las aplicaciones compiladas para Microsoft HoloLens 2 mediante ARM64. Este problema se ha corregido actualizando Visual Studio 2019 a la versión 16.8 o posterior. Si no puede actualizar el Visual Studio, importe el `com.microsoft.mixedreality.toolkit.tools` paquete para aplicar una solución alternativa.

## <a name="whats-new-in-262"></a>Novedades de la versión 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corrige los elementos primarios de la malla espacial

Corrige el [problema por](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) el que las mallas espaciales no se encontraban correctamente después de mover el objeto Mixed Reality Playspace (por ejemplo, a través de un teleportador).

## <a name="whats-new-in-261"></a>Novedades de la versión 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Corrige que OpenXR no se ejecuta en HoloLens 2 o UWP

Corrige una regresión que impedía que la compatibilidad con OpenXR de MRTK se ejecutara en UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Corrige El objeto Leap MotionManipulator no gira

Corrige una regresión en la que el script ObjectManipulator no tuvo en cuenta la rotación de una mano leap motion.

### <a name="sample-scene-updates"></a>Actualizaciones de escena de ejemplo

Actualiza la escena que entiende la escena de ejemplo para reflejar correctamente el estado enviado del complemento de Unity. También actualiza el ejemplo para que ya no tenga una dependencia en la escena de la muestra de reconocimiento espacial que se va a importar. Antes de actualizar a la versión 2.6.1, debe eliminar los ejemplos importados de reconocimiento de la escena y reconocimiento espacial si están presentes en el proyecto para evitar posibles conflictos. Si no ha quitado esos ejemplos y ve conflictos relacionados con los de la consola, quite ambos ejemplos (o la carpeta) y vuelva a intentar `Assets/Samples/Mixed Reality Toolkit Examples` la importación.

Actualiza la escena de ejemplo de diálogo para describir correctamente los escenarios de diálogo actuales.

## <a name="whats-new-in-260"></a>Novedades de la versión 2.6.0
<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Adición de compatibilidad con OpenXR

Se ha agregado compatibilidad inicial con el paquete de versión preliminar de OpenXR de Unity y el paquete Mixed Reality OpenXR de Microsoft. Consulte la página de introducción de [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)la publicación del foro de [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentación de [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obtener más información.

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020.2 y versiones posteriores.
>
> Actualmente, solo admite compilaciones x64 y ARM64.

### <a name="asset-swap-utility"></a>Utilidad de intercambio de recursos

Intercambie varios recursos en una escena de Unity con la nueva [utilidad de intercambio de recursos](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>Controladores de movimiento de HP ahora compatibles con MRTK

Los controladores de HP Reverb G2 ahora funcionan de forma nativa con MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Elemento interactivo experimental + visualizador de estado

Interactive Element es un punto de entrada centralizado simplificado para el sistema de entrada MRTK. Contiene métodos de administración de estado, administración de eventos y la lógica de configuración de estado para los estados de interacción principal. Para obtener más información, [vea Interactive Element Documentation](../features/experimental/interactive-element.md).

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

El visualizador de estado es un componente de animación que depende del elemento interactivo.  Este componente crea clips de animación, establece fotogramas clave y genera una máquina de estado del animador. Para obtener más información, consulte [la documentación del visualizador de estado.](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>La teleportación con el gesto de teleportar ahora se admite en todas las plataformas

Los usuarios ahora pueden usar el gesto de teleportar para desplazarse por su espacio de juego en todas las plataformas. Para teleportar con un controlador en dispositivos mr con configuraciones predeterminadas, use la herramienta thumbstick. Para teleportar con las manos articuladas, haga un gesto con la mano hacia arriba con el índice y el dedo del dedo hacia el exterior, para lo que debe completar el teleportador. Para realizar la teleportación con la simulación de entrada, consulte nuestra documentación [actualizada de Input Simulation Service](../features/input-simulation/input-simulation-service.md).

  ![Gesto de teleportar](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Scene Understanding ya está disponible en MRTK como observador de reconocimiento espacial experimental

La compatibilidad experimental [de Scene Understanding](/windows/mixed-reality/scene-understanding) se introdujo en MRTK 2.6. Los usuarios pueden incorporar las funcionalidades de comprensión de la escena HoloLens 2 como observador de reconocimiento espacial en proyectos basados en MRTK. Lea la documentación [de Scene Understanding para](../features/spatial-awareness/scene-understanding.md) obtener más información.

> [!IMPORTANT]
> Scene Understanding solo se admite en HoloLens 2 y Unity 2019.4 y versiones posteriores.
>
> Esta característica requiere el paquete Scene Understanding, que ahora está disponible a través de [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).
> Al usar la herramienta de características de Mixed Reality o importar de otro modo a través de UPM, importe el ejemplo Demos - SpatialAwareness antes de importar el ejemplo Experimental - SceneUnderstanding debido a un problema de dependencia. Consulte este [problema de GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) para obtener más información.

  ![Descripción de la escena](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Compatibilidad con la conmutación de perfiles en tiempo de ejecución

MRTK ahora permite la conmutación de perfiles antes de la inicialización de la instancia de MRTK (es decir, el modificador de perfil de inicialización previo a MRTK) y después de que un perfil haya estado en uso activo (es decir, modificador de perfil activo). El modificador anterior se puede usar para habilitar componentes seleccionados en función de las funcionalidades del hardware, mientras que el último se puede usar para modificar la experiencia a medida que el usuario entra en un subpart de la aplicación. Lea la documentación [sobre la conmutación de perfiles](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) para obtener más información y ejemplos de código.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicador direccional y solucionadores de seguimiento egresados de experimentales

Dos nuevos solucionadores están listos para su uso con MRTK de línea principal.

  ![Solucionador de indicadores direccionales](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Hand Coach se ha graduado de experimental

La característica Hand Coach ya está lista para su uso con MRTK de línea principal.
  ![Ejemplo de técnico de mano](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Controles de diálogo egresados de experimentales

Los controles de diálogo ya están listos para su uso con MRTK de línea principal.

  ![Controles de cuadro de diálogo](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Sombreador de pulsos se ha pasado de experimental

Los scripts del sombreador Pulse han pasado de ser experimentales. Para obtener más información, vea: [Documentación del sombreador de pulses](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Mejoras del servicio de grabación de entrada

`InputRecordingService` y `InputPlaybackService` ahora pueden grabar y reproducir la entrada de mirada con los ojos. La grabación se ha optimizado para garantizar una velocidad de fotogramas coherente a lo largo del período de grabación, mientras que el tamaño del archivo de grabación y el tiempo de ahorro también se reducen en aproximadamente un 50 %. Ahora se puede guardar y cargar archivos de grabación de forma asincrónica. Tenga en cuenta que el formato de archivo de la grabación ha cambiado en esta versión de MRTK; consulte [aquí](../features/input-simulation/input-animation-file-format.md) para obtener más información sobre las nuevas especificaciones de la versión 1.1.

### <a name="reading-mode"></a>Modo de lectura

Se ha agregado compatibilidad con [el modo de](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) lectura HoloLens 2. El modo de lectura reduce el campo de vista del sistema, pero elimina un escalado de la salida de Unity. Un píxel representado por Unity se corresponderá con un píxel proyectado en HoloLens 2. Los autores de aplicaciones deben realizar pruebas con varias personas para asegurarse de que se trata de un intercambio que desean en su aplicación.

  ![Windows Mixed Reality modo de lectura](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Compatibilidad con los iniciadores de aplicaciones 3D en UWP

Agrega la capacidad de establecer un [iniciador de aplicaciones 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para UWP. Esta configuración se expone tanto en la ventana de compilación de MRTK como en la configuración del proyecto de MRTK, en Configuración de compilación. Se escribe automáticamente en el proyecto durante la compilación en Unity.

  ![Configuración de compilación](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Últimos cambios

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Algunos campos de objetos GLTF importados ahora están en mayúsculas

Debido a problemas relacionados con la deserialización, algunos campos de objetos GLTF importados ahora comienzan con letras mayúsculas. Los campos afectados son (en sus nuevos nombres): `ComponentType` , , , , , , , , `Path` , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>El archivo binario de animación de entrada tiene un formato actualizado de la versión 1.1

El archivo binario de animación de entrada, usado por y , ahora tiene un formato de archivo actualizado para habilitar las optimizaciones `InputRecordingService` `InputPlaybackService` realizadas en esos dos servicios. Consulte aquí [para obtener](../features/input-simulation/input-animation-file-format.md) más información sobre las nuevas especificaciones de la versión 1.1.

### <a name="msbuild-for-unity-support"></a>Compatibilidad con MSBuild para Unity

La compatibilidad con MSBuild para Unity se ha quitado a partir de la versión 2.5.2, para alinearse con la nueva guía de [paquetes de Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Problemas conocidos

### <a name="openxr"></a>OpenXR

Actualmente hay un problema conocido con la comunicación remota holográfica y OpenXR, donde las juntas de mano no están disponibles de forma coherente.
Además, las escenas de ejemplo de seguimiento de los ojos no son compatibles actualmente, aunque el seguimiento de los ojos *funciona.*

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Algunas Mixed Reality Toolkit Standard Shader requieren el paquete Foundation

Cuando se importan a través de unity Administrador de paquetes, los scripts de utilidades del sombreador estándar de MRTK (p. ej.: HoverLight.cs) no se ubican con el sombreador en el paquete de recursos estándar. Para acceder a esta funcionalidad, las aplicaciones requerirán que se importe el paquete foundation.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache puede crear una nueva cámara al apagar

En algunas situaciones (por ejemplo, cuando se usa el proveedor LeapMotion en el Editor de Unity), es posible que CameraCache vuelva a crear maincamera al apagarse. Consulte este [problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) obtener más información.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException cuando se importan ejemplos a través de Unity Administrador de paquetes

Dependiendo de la longitud de la ruta de acceso del proyecto, la importación de ejemplos a través de Unity Administrador de paquetes generar mensajes FileNotFoundException en la consola de Unity. La causa de esto es que la ruta de acceso al archivo "que falta" tiene más de MAX_PATH (256 caracteres). Para resolverlo, acorte la longitud de la ruta de acceso del proyecto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>No se especificó ningún espacializador. La aplicación no admitirá sonido espacial

Aparecerá una advertencia "No spatializer was specified" (No se especificó ningún espacializador) si no se ha configurado un espacializador de audio. Esto puede ocurrir si no hay ningún paquete XR instalado, ya que Unity incluye espacializadores en estos paquetes.

Para resolverlo, asegúrese de que:

- **Ventana**  >  **Administrador de paquetes** uno o varios paquetes XR instalados
- **Mixed Reality Toolkit**  >  **Utilidades**  >  **Configuración del proyecto de Unity** y selección de Audio **Spatializer**

  ![Selección del espacializador de audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: referencia de objeto no establecida en una instancia de un objeto (SceneTransitionService.Initialize)

En algunas situaciones, la apertura puede provocar una excepción NullReferenceException en el `EyeTrackingDemo-00-RootScene` método Initialize de la clase SceneTransitionService.
Este error se debe a que el perfil de configuración del servicio Scene Transition está sin conjunto. Para resolverlo, siga estos pasos:

- Navegar al objeto `MixedRealityToolkit` en la jerarquía
- En la ventana Inspector, seleccione `Extensions`
- Si no se expande, expanda `Scene Transition Service`
- Establezca el valor de `Configuration Profile` en **MRTKExamplesHubSceneTransitionServiceProfile.**

![Corrección del perfil de transición de escena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Actualmente hay un problema conocido para usar el complemento [Oculus XR con al](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)tener como destino plataformas independientes .  Consulte el seguimiento de errores de Oculus, los foros y las notas de la versión para obtener actualizaciones.

El error se significa con este conjunto de 3 errores:

![Error del complemento XR de Oculus](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI y TextMeshPro

Hay un problema conocido para las versiones más recientes de TextMeshPro (1.5.0+ o 2.1.1+), donde se ha modificado el tamaño de fuente predeterminado para las listas desplegables y el espaciado de caracteres de fuente en negrita.

![Imagen de TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Esto se puede evitar si se degrada a una versión anterior de TextMeshPro. Consulte [el #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obtener más detalles.