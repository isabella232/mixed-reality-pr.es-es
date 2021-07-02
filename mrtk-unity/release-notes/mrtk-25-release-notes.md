---
title: Notas de la versión de MRTK 2.5
description: Notas de la versión de MRTK versión 2.5
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK,
ms.openlocfilehash: c9458e5236cc7de18eb27c3c3e13221a366c89a4
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177509"
---
# <a name="microsoft-mixed-reality-toolkit-25-release-notes"></a>Notas de la versión de Microsoft Mixed Reality Toolkit 2.5

> [!IMPORTANT]
> Hay un problema conocido del compilador que afecta a las aplicaciones compiladas para Microsoft HoloLens 2 mediante ARM64. Este problema se ha corregido actualizando Visual Studio 2019 a la versión 16.8 o posterior. Si no puede actualizar el Visual Studio, importe el `com.microsoft.mixedreality.toolkit.tools` paquete para aplicar una solución alternativa.

## <a name="whats-new-in-254"></a>Novedades de la versión 2.5.4

### <a name="fixes-a-bug-with-oculus-integration-when-using-upm"></a>Corrige un error con la integración de Oculus al usar UPM

Al usar UPM, OculusXRSDKDeviceManagerProfile siempre tendría sus [elementos prefabs establecidos en Ninguno al iniciar](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9160). Esta versión configura el Administrador de dispositivos para que apunte a un conjunto de trabajo de elementos prefabs durante el inicio.

### <a name="fixes-an-issue-with-openxr-via-upm"></a>Corrige un problema con OpenXR a través de UPM

Corrige un problema que provocaba que los proveedores de OpenXR no se agregasen a link.xml de forma predeterminada, lo que provocaba que los nuevos proyectos no se ejecutaran en el dispositivo al usar OpenXR y MRTK a través de la Administrador de paquetes de Unity. Los proyectos existentes que se actualicen seguirán necesitando esta adición manual.

## <a name="whats-new-in-253"></a>Novedades de la versión 2.5.3

### <a name="fixes-a-regression-with-oculus-introduced-in-252"></a>Corrige una regresión con Oculus introducida en la versión 2.5.2

2.5.2 introdujo un [problema de compilación al integrar el SDK de Oculus.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9083) Esta versión revierte ese problema.

## <a name="whats-new-in-252"></a>Novedades de la versión 2.5.2

### <a name="add-support-for-openxr"></a>Adición de compatibilidad con OpenXR

Se ha agregado compatibilidad inicial con el paquete de versión preliminar de OpenXR de Unity y el Mixed Reality openXR de Microsoft. Consulte la página de introducción de [MRTK/XRSDK,](../configuration/getting-started-with-mrtk-and-xrsdk.md)la publicación del foro de [Unity](https://forum.unity.com/threads/unity-support-for-openxr-in-preview.1023613/)o la documentación de [Microsoft](/windows/mixed-reality/develop/unity/openxr-getting-started) para obtener más información.

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020.3 y versiones posteriores.
> También admite compilaciones x64, ARM y ARM64.

### <a name="boundary-visualization-errors-fixed"></a>Errores de visualización de límites corregidos

Las visualizaciones de límites, como el suelo o las paredes, ahora se configurarán correctamente y estarán visibles en tiempo de ejecución según el perfil de límite.

### <a name="msbuild-for-unity-support"></a>MSBuild compatibilidad con Unity

La compatibilidad MSBuild para Unity se ha quitado a partir de la versión 2.5.2, para alinearse con la nueva guía de [paquetes de Unity.](https://forum.unity.com/threads/updates-to-our-terms-of-service-and-new-package-guidelines.999940/)

## <a name="whats-new-in-251"></a>Novedades de la versión 2.5.1

### <a name="package-dependency-errors-fixed"></a>Errores de dependencia de paquete corregidos

En esta versión se corrigen dependencias incorrectas de archivos entre paquetes (por ejemplo, los archivos de recursos estándar ya no hacen referencia incorrectamente a archivos en Foundation). La versión 2.5.1 también agrega una dependencia explícita en Text Mesh Pro.

### <a name="standard-assets-package-shaders-copied-to-assetsmrtkshaders"></a>Sombreadores de paquetes de recursos estándar copiados en Assets/MRTK/Shaders

Cuando el paquete de recursos estándar se instala a través de UPM, los sombreadores se copiarán en la carpeta Assets/MRTK/Shaders para que ya no sean inmutables. Esto resuelve el problema de los sombreadores actualizados para la canalización de representación universal (URP) que revierten el comportamiento heredado la próxima vez que se cargue el proyecto.

### <a name="fixed-teleport-cursor-sticking-to-hands"></a>Se ha corregido el cursor de teleport que se pegaba a las manos

En esta versión se corrige [un problema por](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8755) el que el cursor de destino de teleportador se puede pegar a los objetos visuales de mano.

## <a name="whats-new-in-250"></a>Novedades de la versión 2.5.0

### <a name="unity-package-manager-upm-support"></a>Compatibilidad Administrador de paquetes unity (UPM)

El Mixed Reality Toolkit ahora se puede administrar mediante el Administrador de paquetes de Unity.

![Paquete UPM de MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Hay algunos pasos manuales necesarios para importar los paquetes UPM de MRTK. Revise los [Mixed Reality Toolkit y unity Administrador de paquetes](../configuration/usingupm.md) para obtener más información.

### <a name="oculus-quest-xr-sdk-support"></a>Compatibilidad con el SDK XR de Oculus Quest

MRTK ahora admite la ejecución de cascos y controladores de Oculus Headsets y Deserción mediante la canalización nativa del SDK de XR. El seguimiento de manos también se admite con el paquete de Unity de integración de [Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) gracias al trabajo de [Eric Provencher](https://twitter.com/prvncher) en MRTK-Unity.

Para obtener instrucciones sobre cómo implementar el dispositivo en Oculus Quest mediante la nueva canalización, consulte la Guía [de configuración de Oculus Quest.](../supported-devices/oculus-quest-mrtk.md)

### <a name="scrolling-object-collection"></a>Desplazamiento por la colección de objetos

El componente de experiencia de usuario de MRTK se ha actualizado a partir de una característica experimental y ofrece más libertad para el diseño de contenido 3D de diferentes tamaños con compatibilidad adicional para objetos que no tienen ningún colisionador asociado. También se ha agregado una nueva opción para deshabilitar el enmascaramiento de contenido, lo que facilita la creación de prototipos.

Vea [Colección de objetos de desplazamiento](../features/ux-building-blocks/scrolling-object-collection.md) para obtener más información.

![Desplazamiento por la colección de objetos](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a>Mejoras en la animación, el control y el sonido de los punteros teleportado

El puntero de teleport ahora tiene animaciones mejoradas y comentarios de audio. También hemos mejorado el control del puntero teleportador para que se controle más suave al pasar de apuntar a superficies cercanas a superficies más lejanas.

### <a name="input-simulation-cheat-sheet"></a>Hoja de datos de simulación de entrada

La escena HandInteractionExamples ahora tiene un acceso directo configurable para mostrar una página de ayuda para la simulación de entrada.

![Hoja de datos de simulación de entrada](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a>Mirada con los ojos de simulación de entrada con el mouse

Los usuarios ahora pueden usar el mouse para simular el seguimiento de los ojos. Vea el `Eye Simulation Mode` campo en el perfil de simulación de entrada y esta establezca en Mouse. Esto reemplaza al campo `Simulate Eye Position` anterior.

![Mouse con mirada con los ojos](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a>Controlador de movimiento de simulación de entrada en el modo de reproducción del editor

Los usuarios ahora pueden simular el controlador de movimiento igual que las manos en el modo de reproducción del editor. Actualmente se admiten los botones de desencadenador, de toma y de menú.

### <a name="conical-grab-pointer"></a>Puntero de toma cónica

Los punteros de toma ahora se pueden configurar para consultar objetos cercanos mediante un cono desde el punto de toma en lugar de una esfera. Esto se parece más al comportamiento de la interfaz HoloLens 2 predeterminada, que consulta objetos cercanos mediante un cono. DefaultHoloLens2InputSystemProfile también se ha ajustado para usar el nuevo `ConicalGrabPointer` .

![Puntero de toma cónica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a>Paquete TestUtilities

Ahora hay un paquete (Microsoft.MixedReality.Toolkit. Unity.TestUtilities.2.5.0.unitypackage) que contiene la infraestructura de pruebas PlayMode y TestMode que usa MRTK para crear pruebas de un extremo a otro. Esta infraestructura ha sido muy útil para el propio equipo de MRTK y nos complace que los consumidores lo usen para agregar cobertura de prueba a sus propios proyectos.

En el código siguiente se muestra cómo crear una mano de prueba, mostrarla en una ubicación determinada, moverla y, a continuación, acercar y abrir.

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

Para obtener instrucciones sobre cómo escribir una prueba con estas TestUtilities, consulte esta sección sobre [la escritura de pruebas.](../contributing/unit-tests.md#writing-tests)

Para obtener ejemplos de pruebas existentes que usan esta infraestructura, vea [PlayModeTests de](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)MRTK.

### <a name="support-for-the-leap-motion-451-unity-modules"></a>Compatibilidad con los módulos de Unity leap motion 4.5.1

Se ha agregado compatibilidad con los módulos leap motion de Unity versión 4.5.1 y se ha quitado la compatibilidad con los recursos de la versión 4.4.0. Las versiones compatibles actuales de los módulos de Unity leap motion son 4.5.0 y 4.5.1.

También hay un paso adicional para la integración inicial de Leap Motion. Para más información, consulte [How to Configure the Leap Motion Hand Tracking in MRTK (Configuración](../supported-devices/leap-motion-mrtk.md) del seguimiento de mano de leap motion en MRTK).

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a>Observador de malla de reconocimiento espacial controla mejor la personalización de materiales

Con esta versión, los componentes y han mejorado `Windows Mixed Reality Spatial Mesh Observer` el control de material `Generic XR SDK Spatial Mesh Observer` visual. Los materiales ahora se conservan cuando el observador ha actualizado una malla en la que, anteriormente, se restablecían al valor predeterminado VisibleMaterial tal y como se configuró en el perfil.

Esto permite a los desarrolladores modificar el material de malla y no sobrescribir los cambios de forma inesperada.

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a>Link.xml en la carpeta MixedRealityToolkit.Generated

Con la introducción de MrTK del administrador de paquetes de Unity, MRTK ahora escribe un archivo en la carpeta, si `link.xml` `Assets/MixedRealityToolkit.Generated` no hay ninguno. Se recomienda agregar este archivo (y `link.xml.meta` ) al control de código fuente. Link.xml se usa para influir en la funcionalidad [de quitar código administrado](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) del vinculador de Unity.

Puede encontrar más información sobre el archivo de link.xml MRTK en el [artículo mrtk y](../updates-deployment/mrtk-and-managed-code-stripping.md) la extracción de código administrado.

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a>Unity 2019.3+: el cuadro de diálogo de configuración de MRTK ya no intenta habilitar la compatibilidad con XR heredada

Para evitar posibles conflictos al usar la plataforma XR de Unity, la opción para habilitar la compatibilidad con XR heredada se ha quitado del cuadro de diálogo de configuración de MRTK. Si lo desea, se puede habilitar la compatibilidad con XR heredada, en Unity 2019, con **Edit**  >  **Project Configuración**  >
 **Player**  >  **XR Configuración** Virtual  >  **Reality Supported**.

### <a name="reduction-in-initializeonload-overhead"></a>Reducción de la sobrecarga initializeOnLoad

Hemos estado trabajando para reducir la cantidad de trabajo que se ejecuta en controladores InitializeOnLoad, lo que debería dar lugar a mejoras en la velocidad de desarrollo del bucle interno. Los controladores InitializeOnLoad se ejecutan cada vez que se compila un script, antes de entrar en modo de reproducción y también en el inicio del editor. Estos controladores se ejecutan ahora en muchos menos casos, lo que da lugar a mejoras generales de capacidad de respuesta de Unity.

En algunos casos, se tuvo que realizar un intercambio:

- Consulte [Leap Motion Hand Tracking Configuration (Configuración](../supported-devices/leap-motion-mrtk.md) de leap motion hand tracking) para obtener el paso de integración adicional.
- Para aquellos que usan ARFoundation, ahora hay un paso manual adicional en sus pasos de introducción.
  Consulte [ARFoundation para](../supported-devices/using-ar-foundation.md#install-required-packages) ver los nuevos pasos.
- Para aquellos que van a usar la comunicación remota holográfica con la canalización [XR](../features/tools/holographic-remoting.md#legacy-xr-setup-instructions) heredada en HoloLens 2, ahora hay un [paso manual](../features/tools/holographic-remoting.md#dotnetwinrt_present-define-written-into-player-settings) que realizar.

### <a name="bounds-control-graduated"></a>Control de límites egresado

![Control Límites](../features/images/bounds-control/MRTK_BoundsControl_Main.png)

[El control de](../features/ux-building-blocks/bounds-control.md) límites se ha consolidado de forma experimental y viene con una serie de nuevas características y montones de correcciones de errores.
Aquí se muestra una lista de los aspectos destacados de esta actualización:

- Las propiedades se dividen en configuraciones, lo que facilita la configuración del control de límites.
- las configuraciones se pueden compartir a través de objetos que pueden incluirse en scripts
- cada propiedad o propiedad que admite scripts es configurable en tiempo de ejecución
- el control bounds ya no se vuelve a crear en los cambios de propiedad
- compatibilidad con identificadores de traducción
- compatibilidad con restricciones completa a través del administrador de restricciones
- integración del sistema elástico (experimental)

El cuadro de límite anterior está ahora en desuso y los objetos de juego existentes mediante el cuadro de límite se pueden actualizar mediante la herramienta de migración o el [inspector de rectángulo de selección](../features/ux-building-blocks/bounding-box.md#migrating-to-bounds-control). [](../features/tools/migration-window.md)

### <a name="constraint-manager-component"></a>Componente del administrador de restricciones

Ahora, el control de límites y el manipulador de objetos pueden usar restricciones a través del nuevo componente [del administrador de restricciones](../features/ux-building-blocks/constraint-manager.md). Ambos componentes crearán un administrador de restricciones de forma predeterminada y procesarán automáticamente las restricciones adjuntas.

Además, el administrador de restricciones de comportamiento automático también incluye un modo manual que permite a los usuarios decidir qué restricción se debe procesar.
Por este motivo, la forma en que se muestran las restricciones en el inspector de propiedades ha cambiado un poco.

<img src="../features/images/constraint-manager/ManualSelection.png" width="600" alt="Inspector view showing manual constraint manager selection">

Las restricciones que se aplican al componente ahora se muestran como una lista en el componente del administrador de restricciones, mientras que el componente que usa el administrador de [restricciones (control](../features/ux-building-blocks/bounds-control.md#constraint-system) de límites o manipulador de [objetos)](../features/ux-building-blocks/object-manipulator.md#constraint-manager)mostrará ahora el administrador de restricciones y el modo seleccionados (automático o manual).
Para obtener más información, lea [la sección del administrador](../features/ux-building-blocks/constraint-manager.md) de restricciones en nuestros documentos.

### <a name="hololens-2-button-material-update"></a>HoloLens 2 material del botón de actualización

Se HoloLens 2 material frontal del botón para quitar el color negro en MRC.

![HoloLens 2 material del botón de actualización](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a>Actualización del panel de descripción, escena de ejemplo móvil

Panel de descripción actualizado. (SceneDescriptionPanelRev.prefab) El nuevo diseño proporciona una barra superior que permite al usuario ajustar o mover toda la escena.

![Actualización del panel de descripción](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a>Visualización de malla espacial: pulse en el toque de aire

Se ha actualizado el ejemplo del sombreador de pulsos para que la malla espacial coincida HoloLens 2 comportamiento del shell de la aplicación.

![Pulse on air-tap](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system-experimental"></a>Sistema elástico (experimental)

![Elastic System2](../features/images/elastics/Elastics_Main.gif)

MRTK ahora incluye [](../features/experimental/elastic-system.md) un sistema de simulación elástica que incluye una amplia variedad de subclases extensibles y flexibles, que ofrece enlaces para sistemas de cuaternión de cuaternión de 4 dimensiones, sonidos de volumen tridimensionales y sistemas de spring lineales simples.

Actualmente, los siguientes componentes de MRTK que [admiten el administrador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) pueden aprovechar la funcionalidad de los elásticos:

- [Control Bounds](../features/ux-building-blocks/bounds-control.md#elastics-experimental)
- [Manipulador de objetos](../features/ux-building-blocks/object-manipulator.md#elastics-experimental)

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Expanding an elastic menu">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Grabbing an elastic coffee cup">

### <a name="joystick-experimental"></a>Estación (experimental)

Un ejemplo de interfaz de interfaz de interfaz que puede controlar un objeto de destino grande.

![Joystick](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a>Selector de colores (experimental)

Control experimental que facilita el cambio de colores de material en cualquier objeto en tiempo de ejecución.

![Tres métodos diferentes de control selector de colores](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)

![Cuatro métodos diferentes de control selector de colores](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

## <a name="breaking-changes"></a>Últimos cambios

### <a name="assembly-definition-files-changes"></a>Cambios en los archivos de definición de ensamblado

Algunos archivos asmdef se cambian y ahora solo admiten Unity 2018.4.13f1 o posterior. Los errores de compilación se mostrarán al actualizar a MRTK 2.5 en versiones anteriores de Unity. Para solucionarlo, vaya a en `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` la ventana del proyecto y quite la referencia que falta en el inspector. Repita esos pasos con `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` y `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` . Tenga en cuenta que debe revertir los cambios reemplazando esos tres archivos asmdef por los originales (es decir, sin modificar) al actualizar a Unity 2019.

### <a name="imixedrealitypointermediator"></a>IMixedRealityPointerMediator

Esta interfaz se ha actualizado para tener una nueva función:

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

Si tiene un mediador de puntero personalizado que no tiene la subclase DefaultPointerMediator, deberá implementar esta nueva función. Consulte [este problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) obtener más información sobre por qué se agregó esto. Esto se agregó para asegurarse de que las preferencias de puntero se pasarían explícitamente al mediador, en lugar de hacerlo implícitamente en función de la presencia de un constructor que tomaba IPointerPreferences.

### <a name="rest--device-portal-api"></a>Rest/Portal de dispositivos API

La `UseSSL` propiedad estática se ha movido de a `Rest` `DevicePortal` .

Si lo hizo anteriormente...

```csharp
Rest.UseSSL = true
```

Haga esto ahora...

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a>Link.xml

Si anteriormente una aplicación usaba la NuGet distribución de MRTK, el archivo se ha `link.xml` quitado del paquete foundation. Para restaurar las reglas de conservación de código, al abrir el proyecto en Unity una vez se creará un archivo `link.xml` predeterminado en `Assets/MixedRealityToolkit.Generated` . Se recomienda agregar este archivo (y ) al `link.xml.meta` control de código fuente.

### <a name="transform-constraint-changes"></a>Cambios de restricción de transformación

La propiedad TargetTransform se ha marcado como obsoleta, ya que el sistema de restricciones no la ha usado. La lógica de restricción se basa en la transformación que se pasa a los métodos Initialize y Apply. Las restricciones de usuario derivadas que se basan en esta propiedad pueden almacenar en caché TargetTransform en su implementación almacenando la transformación del componente de restricción para lograr el mismo comportamiento.

El tipo de datos pos del mundo inicial almacenado se ha cambiado de MixedRealityPose a MixedRealityTransform, que incluye el valor de escala `worldPoseOnManipulationStart` local del objeto manipulado. Con este cambio, ya no es necesario almacenar en caché los valores de escala iniciales por separado.

### <a name="new-property-in-imixedrealitydictationsystem"></a>Nueva propiedad en IMixedRealityDictationSystem

Se ha agregado `AudioClip` una nueva propiedad a la interfaz IMixedRealityDictationSystem. La `AudioClip` propiedad habilita el acceso al clip de audio asociado a la sesión de dictado actual. Los usuarios deben implementar la propiedad en sus scripts que implementan la interfaz .

### <a name="service-facades-turn-down"></a>Fachadas de servicio apagadas

Las fachadas de servicios se están apagando en la versión 2.5. Esta característica se agregó originalmente para facilitar la configuración de los perfiles de MRTK (mediante la creación de objetos GameObject falsos en la escena que representan cada uno de los servicios de MRTK). A largo plazo, queremos evitar la creación de objetos falsos en el juego e intentar mantenerlos sincronizados (ya que los problemas de sincronización de datos y "origen de verdad" son difíciles de escalar y hacer correctos).

En la versión 2.5, los controladores de la fachada de servicio se mantienen alrededor para asegurarse de que la actualización del proyecto se realiza sin problemas: el controlador de la fachada del servicio eliminará todas las fachadas que existan en el proyecto para asegurarse de que las escenas abiertas en la versión 2.5 se corrigirán automáticamente.

El código restante asociado a la característica de fachada de servicio se quitará en una versión futura.

### <a name="addition-of-motion-controller-to-input-simulation-service"></a>Adición del controlador de movimiento al servicio de simulación de entrada

La simulación del controlador de movimiento ahora se ofrece en el modo de reproducción del editor junto con la simulación de mano existente. Para habilitar este cambio, muchas funciones, campos o propiedades actuales están ahora marcados como obsoletos, con y `InputSimulationService.cs` `MixedRealityInputSimulationProfile.cs` obteniendo los cambios más significativos. La lógica y el comportamiento del código pertinente siguen siendo en gran medida los mismos, y la mayoría de las funciones obsoletas, etc., están relacionados con la sustitución de la referencia a "mano" por el término más genérico "controlador" (por ejemplo, de `DefaultHandSimulationMode` a `DefaultControllerSimulationMode` ). Además de obtener nuevos nombres, el tipo de valor devuelto de determinadas funciones nuevas se actualiza para que coincida con el cambio de nombre o comportamiento (por ejemplo, en función del valor devuelto original ahora en lugar `GetControllerDevice` `GetHandDevice` de `BaseController` `SimulatedHand` ).

`IInputSimulationService` ahora tiene nuevas propiedades `MotionControllerDataLeft` y `MotionControllerDataRight` . `MixedRealityInputSimulationProfile` ahora incluye nuevos campos para la asignación de teclado de determinados botones del controlador de movimiento.

## <a name="known-issues"></a>Problemas conocidos

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a>CameraCache puede crear una nueva cámara al apagar

En algunas situaciones (por ejemplo, cuando se usa el proveedor LeapMotion en el Editor de Unity), es posible que CameraCache vuelva a crear maincamera al apagarse. Consulte este [problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) obtener más información.

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a>FileNotFoundException cuando se importan ejemplos a través de Unity Administrador de paquetes

Dependiendo de la longitud de la ruta de acceso del proyecto, la importación de ejemplos a través de Unity Administrador de paquetes generar mensajes FileNotFoundException en la consola de Unity. La causa de esto es que la ruta de acceso al archivo "que falta" tiene más de MAX_PATH (256 caracteres). Para resolverlo, acorte la longitud de la ruta de acceso del proyecto.

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a>No se especificó ningún espacializador. La aplicación no admitirá sonido espacial

Aparecerá una advertencia "No spatializer was specified" (No se especificó ningún espacializador) si no se ha configurado un espacializador de audio. Esto puede ocurrir si no hay ningún paquete XR instalado, ya que Unity incluye espacializadores en estos paquetes.

Para resolverlo, asegúrese de que:

- **Ventana**  >  **Administrador de paquetes** tiene uno o varios paquetes XR instalados
- **Mixed Reality Toolkit**  >  **Utilidades**  >  **Configuración de unity Project** y realización de una selección para **El espacializador de audio**

  ![Selección del espacializador de audio](images/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a>NullReferenceException: referencia de objeto no establecida en una instancia de un objeto (SceneTransitionService.Initialize)

En algunas situaciones, la apertura puede provocar una excepción NullReferenceException en el `EyeTrackingDemo-00-RootScene` método Initialize de la clase SceneTransitionService.
Este error se debe a que el perfil de configuración del servicio Scene Transition no se ha conjunto. Para resolverlo, siga estos pasos:

- Navegar al objeto `MixedRealityToolkit` en la jerarquía
- En la ventana Inspector, seleccione `Extensions`
- Si no se expande, expanda `Scene Transition Service`
- Establezca el valor de `Configuration Profile` en **MRTKExamplesHubSceneTransitionServiceProfile.**

![Corregir transición de escena](images/FixSceneTransitionProfile.png)

### <a name="oculus-quest"></a>Oculus Quest

Actualmente hay un problema conocido para usar el complemento [XR de Oculus con al tener como](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/)destino plataformas independientes . Compruebe si hay actualizaciones en el seguimiento de errores de Oculus, los foros y las notas de la versión.

El error se significa con este conjunto de tres errores:

![Error del complemento Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a>UnityUI y TextMeshPro

Hay un problema conocido para las versiones más recientes de TextMeshPro (1.5.0+ o 2.1.1+), donde se ha modificado el tamaño de fuente predeterminado para las listas desplegables y el espaciado de caracteres de fuente en negrita.

![Imagen de TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

Esto se puede evitar si se degrada a una versión anterior de TextMeshPro. Consulte [el #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) para obtener más detalles.
