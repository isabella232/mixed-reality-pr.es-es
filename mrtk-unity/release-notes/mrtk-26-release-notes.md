---
title: Notas de la versión de MRTK 2.6
description: Notas de la versión de MRTK versión 2.6
author: polar-kev
ms.author: kesemple
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK,
ms.openlocfilehash: 452f0f352443620dea70b1680859bab4e2b3a0818de5f130accdb84c2798cfe0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206742"
---
# <a name="microsoft-mixed-reality-toolkit-26-release-notes"></a>Notas de la versión de Microsoft Mixed Reality Toolkit 2.6

> [!IMPORTANT]
> Hay un problema conocido del compilador que afecta a las aplicaciones compiladas para Microsoft HoloLens 2 mediante ARM64. Este problema se ha corregido actualizando Visual Studio 2019 a la versión 16.8 o posterior. Si no puede actualizar el Visual Studio, importe el `com.microsoft.mixedreality.toolkit.tools` paquete para aplicar una solución alternativa.

## <a name="whats-new-in-262"></a>Novedades de la versión 2.6.2

### <a name="corrects-parenting-of-the-spatial-mesh"></a>Corrige la matriz de la malla espacial.

Corrige el [problema por](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9819) el que las mallas espaciales no se encontraban correctamente después de mover el objeto Mixed Reality Playspace (por ejemplo, a través de un teleportador).

## <a name="whats-new-in-261"></a>Novedades de la versión 2.6.1

### <a name="fixes-openxr-not-running-on-hololens-2--uwp"></a>Corrige que OpenXR no se ejecuta en HoloLens 2 o UWP

Corrige una regresión que impedía que la compatibilidad con OpenXR de MRTK se ejecutara en UWP.

### <a name="fixes-leap-motion-objectmanipulator-not-rotating"></a>Corrige el objeto Leap MotionManipulator no girando

Corrige una regresión en la que el script ObjectManipulator no tuvo en cuenta la rotación de una mano de Leap Motion.

### <a name="sample-scene-updates"></a>Actualizaciones de escena de ejemplo

Actualiza la escena que entiende la escena de ejemplo para reflejar correctamente el estado enviado del complemento de Unity. También actualiza el ejemplo para que ya no tenga una dependencia en la escena de la muestra de reconocimiento espacial que se va a importar. Antes de actualizar a la versión 2.6.1, debe eliminar las muestras de reconocimiento de la escena importada y de reconocimiento espacial si están presentes en el proyecto para evitar posibles conflictos. Si no ha quitado esos ejemplos y ve conflictos relacionados con los de la consola, quite ambos ejemplos (o la carpeta) y vuelva a intentar `Assets/Samples/Mixed Reality Toolkit Examples` la importación.

Actualiza la escena de ejemplo de diálogo para describir correctamente los escenarios de diálogo actuales.

## <a name="whats-new-in-260"></a>Novedades de la versión 2.6.0

<iframe width="940" height="530" src="https://www.youtube.com/embed/qfONlUCSWdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
<br>

### <a name="add-support-for-openxr"></a>Adición de compatibilidad con OpenXR

Se ha agregado compatibilidad inicial con el paquete de versión preliminar de OpenXR de Unity y el Mixed Reality openXR de Microsoft. Consulte [la página de introducción de MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)la publicación del foro de [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentación de [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obtener más información.

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020.2 y versiones posteriores.
>
> Actualmente, también solo admite compilaciones x64 y ARM64.

### <a name="asset-swap-utility"></a>Utilidad de intercambio de recursos

Intercambie varios recursos en una escena de Unity con la nueva [utilidad asset swap](../features/tools/asset-swap-utility.md).

### <a name="hp-motion-controllers-now-supported-with-mrtk"></a>Los controladores de movimiento de HP ahora se admiten con MRTK

Los controladores de HP Reverb G2 ahora funcionan de forma nativa con MRTK.

### <a name="experimental-interactive-element--state-visualizer"></a>Elemento interactivo experimental + visualizador de estado

Interactive Element es un punto de entrada centralizado simplificado al sistema de entrada de MRTK. Contiene métodos de administración de estados, administración de eventos y la lógica de configuración de estado para los estados de interacción principal. Para obtener más información, [vea Interactive Element Documentation](../features/experimental/interactive-element.md).

![InteractiveElementAddCoreState](../features/images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

El visualizador de estado es un componente de animación que depende del elemento interactivo. Este componente crea clips de animación, establece fotogramas clave y genera una máquina de estado del animador. Para más información, consulte [la documentación del visualizador de estado.](../features/experimental/interactive-element.md#state-visualizer-experimental)

![StateVisualizerColorChangeOnFocus](../features/images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="teleportation-with-the-teleport-gesture-now-supported-on-all-platforms"></a>La teleportación con el gesto de teletransporte ahora se admite en todas las plataformas

Los usuarios ahora pueden usar el gesto de teleportar para moverse por su espacio de juego en todas las plataformas. Para teleportar con un controlador en dispositivos de MR con configuraciones predeterminadas, use la huella digital. Para teleportar con las manos articuladas, haga un gesto con la mano con la mano hacia arriba con el índice y el control de posición hacia el exterior, para lo que debe completar el teleportar rizado del dedo índice. Para teleportar con la simulación de entrada, consulte nuestra documentación [actualizada del servicio de simulación de entrada](../features/input-simulation/input-simulation-service.md).

![Gesto de teleportar](../features/images/teleport/handteleport.gif)

### <a name="scene-understanding-now-available-in-mrtk-as-an-experimental-spatial-awareness-observer"></a>Scene Understanding ya está disponible en MRTK como observador de reconocimiento espacial experimental

La compatibilidad experimental [de Scene Understanding](/windows/mixed-reality/scene-understanding) se introdujo en MRTK 2.6. Los usuarios pueden incorporar las funcionalidades de comprensión de la escena HoloLens 2 como observador de reconocimiento espacial en proyectos basados en MRTK. Lea la documentación [de Scene Understanding para](../features/spatial-awareness/scene-understanding.md) obtener más información.

> [!IMPORTANT]
> Scene Understanding solo se admite en HoloLens 2 y Unity 2019.4 y versiones posteriores.
>
> Esta característica requiere el paquete Scene Understanding, que ahora está disponible a través de [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).
> Al usar la herramienta de características Mixed Reality o importar de otro modo a través de UPM, importe el ejemplo Demos - SpatialAwareness antes de importar el ejemplo Experimental - SceneUnderstanding debido a un problema de dependencia. Consulte este [GitHub problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) obtener más información.

![Descripción de la escena](images/SceneUnderstanding.gif)

### <a name="runtime-profile-switching-support"></a>Compatibilidad con la conmutación de perfiles en tiempo de ejecución

MRTK ahora permite el cambio de perfil antes de la inicialización de la instancia de MRTK (es decir, el modificador de perfil de inicialización de MRTK anterior) y después de que un perfil haya estado en uso activo (es decir, conmutador de perfil activo). El modificador anterior se puede usar para habilitar componentes seleccionados en función de las funcionalidades del hardware, mientras que el último se puede usar para modificar la experiencia a medida que el usuario entra en una subparta de la aplicación. Lea la documentación [sobre el cambio de perfil para](../configuration/mixed-reality-configuration-guide.md#changing-profiles-at-runtime) obtener más información y ejemplos de código.

### <a name="directional-indicator-and-follow-solvers-graduated-from-experimental"></a>Indicador direccional y seguimiento de solucionadores que han pasado de ser experimentales

Dos nuevos solucionadores están listos para usarse con MRTK de línea principal.

![Solucionador de indicador direccional](images/DirectionalIndicatorExampleScene.gif)

### <a name="hand-coach-graduated-from-experimental"></a>Hand Coach se ha titulado de experimental

La característica Hand Coach ya está lista para usarse con MRTK de línea principal.

![Ejemplo de técnico de mano](/windows/mixed-reality/design/images/handcoach/airtap.gif)

### <a name="dialog-controls-graduated-from-experimental"></a>Controles de diálogo egresados de experimentales

Los controles de diálogo ya están listos para usarse con MRTK de línea principal.

![Controles de cuadro de diálogo](https://user-images.githubusercontent.com/13754172/101927792-3326e200-3c18-11eb-88d3-44b4b50c7f7d.png)

### <a name="pulse-shader-graduated-from-experimental"></a>Sombreador de pulsos ha pasado de ser experimental

Los scripts del sombreador Pulse han pasado de ser experimentales. Para obtener más información, vea: [Documentación de Pulse Shader.](../features/rendering/pulse-shader.md)

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

### <a name="input-recording-service-improvements"></a>Mejoras del servicio de grabación de entrada

`InputRecordingService` y `InputPlaybackService` ahora pueden grabar y reproducir la entrada de mirada con los ojos. La grabación se ha optimizado para garantizar una velocidad de fotogramas coherente durante todo el período de grabación, mientras que el tamaño del archivo de grabación y el tiempo de ahorro también se reducen en aproximadamente un 50 %. Ahora se puede guardar y cargar archivos de grabación de forma asincrónica. Tenga en cuenta que el formato de archivo de la grabación ha cambiado en esta versión de MRTK; consulte [aquí](../features/input-simulation/input-animation-file-format.md) para obtener más información sobre las especificaciones de la nueva versión 1.1.

### <a name="reading-mode"></a>Modo de lectura

Se ha agregado compatibilidad con [el modo de](/hololens/hololens2-display#what-improvements-are-coming-that-will-improve-hololens-2-image-quality) lectura HoloLens 2. El modo de lectura reduce el campo de vista del sistema, pero elimina un escalado de la salida de Unity. Un píxel representado por Unity se corresponderá con un píxel proyectado en HoloLens 2. Los autores de aplicaciones deben realizar pruebas con varios individuos para asegurarse de que se trata de un valor que quieren en su aplicación.

![Windows Mixed Reality de lectura](images/WMRReadingMode.gif)

### <a name="support-for-3d-app-launchers-on-uwp"></a>Compatibilidad con los iniciadores de aplicaciones 3D en UWP

Agrega la capacidad de establecer un [iniciador de aplicaciones 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para UWP. Esta configuración se expone tanto en la ventana de compilación de MRTK como en el Project Configuración MRTK, en Compilar Configuración. Se escribe automáticamente en el proyecto durante la compilación en Unity.

![Configuración de compilación](images/ProjectBuildSettings.png)

## <a name="breaking-changes"></a>Últimos cambios

### <a name="certain-fields-of-imported-gltf-objects-are-now-capitalized"></a>Algunos campos de objetos GLTF importados ahora están en mayúsculas

Debido a problemas relacionados con la deserialización, algunos campos de objetos GLTF importados comienzan ahora con letras mayúsculas. Los campos afectados son (en sus nuevos nombres): `ComponentType` , , , , , , `Path` , `Interpolation` `Target` `Type` `Mode` `MagFilter` `MinFilter` `WrapS` `WrapT` .

### <a name="input-animation-binary-file-has-an-updated-version-11-format"></a>El archivo binario de animación de entrada tiene un formato actualizado de la versión 1.1

El archivo binario de animación de entrada, usado por y , ahora tiene un formato de archivo actualizado para habilitar las optimizaciones `InputRecordingService` `InputPlaybackService` realizadas en esos dos servicios. Consulte aquí [para](../features/input-simulation/input-animation-file-format.md) obtener más información sobre las nuevas especificaciones de la versión 1.1.

### <a name="msbuild-for-unity-support"></a>MSBuild compatibilidad con Unity

La compatibilidad MSBuild para Unity se ha quitado a partir de la versión 2.5.2, para alinearse con la nueva guía de [paquetes de Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="known-issues"></a>Problemas conocidos

### <a name="openxr"></a>OpenXR

Actualmente hay un problema conocido con la comunicación remota holográfica y OpenXR, donde las uniones de mano no están disponibles de forma coherente.
Además, las escenas de ejemplo de seguimiento ocular no son compatibles actualmente, aunque el seguimiento ocular _funciona._

### <a name="some-mixed-reality-toolkit-standard-shader-features-require-the-foundation-package"></a>Algunas Mixed Reality Toolkit de sombreador estándar requieren el paquete Foundation

Cuando se importan a través de unity Administrador de paquetes, los scripts de utilidades del sombreador estándar de MRTK (p. ej.: HoverLight.cs) no se ubican de forma local con el sombreador en el paquete de recursos estándar. Para acceder a esta funcionalidad, las aplicaciones requerirán que se importe el paquete foundation.

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache puede crear una nueva cámara al apagar

En algunas situaciones (por ejemplo, cuando se usa el proveedor LeapMotion en el Editor de Unity), es posible que CameraCache vuelva a crear maincamera al apagarse. Consulte este [problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) obtener más información.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException cuando se importan ejemplos a través de Unity Administrador de paquetes

Dependiendo de la longitud de la ruta de acceso del proyecto, la importación de ejemplos a través de Unity Administrador de paquetes generar mensajes FileNotFoundException en la consola de Unity. La causa de esto es que la ruta de acceso al archivo "que falta" tiene más de MAX_PATH (256 caracteres). Para resolverlo, acorte la longitud de la ruta de acceso del proyecto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>No se especificó ningún espacializador. La aplicación no admitirá sonido espacial

Aparecerá una advertencia "No spatializer was specified" (No se especificó ningún espacializador) si no se ha configurado un espacializador de audio. Esto puede ocurrir si no hay ningún paquete XR instalado, ya que Unity incluye espacializadores en estos paquetes.

Para resolverlo, asegúrese de que:

- **Ventana**  >  **Administrador de paquetes** tiene uno o varios paquetes XR instalados
- **Mixed Reality Toolkit**  >  **Utilidades**  >  **Configuración de Project Unity** y selección de **Audio Spatializer**

  ![Selección del espacializador de audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: referencia de objeto no establecida en una instancia de un objeto (SceneTransitionService.Initialize)

En algunas situaciones, la apertura puede provocar una excepción NullReferenceException en el `EyeTrackingDemo-00-RootScene` método Initialize de la clase SceneTransitionService.
Este error se debe a que el perfil de configuración del servicio Scene Transition no está en estado de configuración. Para resolverlo, siga estos pasos:

- Vaya al objeto `MixedRealityToolkit` en la jerarquía.
- En la ventana Inspector, seleccione `Extensions`
- Si no se expande, expanda `Scene Transition Service`
- Establezca el valor de `Configuration Profile` en **MRTKExamplesHubSceneTransitionServiceProfile.**

![Corrección del perfil de transición de la escena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Actualmente hay un problema conocido para usar el complemento [Oculus XR con al](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)tener como destino plataformas independientes . Consulte el seguimiento de errores de Oculus, los foros y las notas de la versión para obtener actualizaciones.

El error se significa con este conjunto de 3 errores:

![Error del complemento XR de Oculus](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI y TextMeshPro

Hay un problema conocido para las versiones más recientes de TextMeshPro (1.5.0+ o 2.1.1+), donde se ha modificado el tamaño de fuente predeterminado para las listas desplegables y el espaciado de caracteres de fuente en negrita.

![Imagen de TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Esto se puede evitar si se degrada a una versión anterior de TextMeshPro. Consulte [el #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obtener más detalles.
