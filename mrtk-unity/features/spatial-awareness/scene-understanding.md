---
title: Observador de comprensión de la escena
description: describe Scene Understanding in MRTK (Descripción de la escena en MRTK)
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Scene Understanding
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176234"
---
# <a name="scene-understanding-observer"></a>Observador de comprensión de la escena

[Scene Understanding](/windows/mixed-reality/scene-understanding) devuelve una representación semántica de entidades de escena, así como sus formas geométricas __en__ HoloLens 2 (HoloLens no se admite 1.ª generación).

Algunos casos de uso esperados de esta tecnología son:
* Colocar objetos en la superficie más cercana de un tipo determinado (por ejemplo, la pared y el suelo)
* Construcción de una malla de navegación para juegos de estilo de plataforma
* Proporcionar geometría fácil de usar en el motor físico como cuadrándes
* Acelerar el desarrollo evitando la necesidad de escribir algoritmos similares

Scene Understanding se presenta como una __característica experimental__ en MRTK 2.6. Se integra en MRTK como un [observador espacial](spatial-awareness-getting-started.md#register-observers) denominado [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . Scene Understanding funciona tanto con la canalización XR heredada como con la canalización del SDK de XR (tanto OpenXR (a partir de MRTK 2.7) como Windows complemento XR). En ambos casos `WindowsSceneUnderstandingObserver` se usa .

> [!NOTE] 
> No se admite el uso de Scene Understanding en comunicación remota.

## <a name="observer-overview"></a>Información general del observador

Cuando se le pregunte, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) devolverá [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con atributos útiles para que la aplicación comprenda su entorno. La frecuencia de observación, el tipo de objeto devuelto (por ejemplo, la pared, el suelo) y otros comportamientos del observador dependen de la configuración del observador a través del perfil. Por ejemplo, si se desea la máscara de oclusión, el observador debe configurarse para generar quads. La escena observada se puede guardar como archivo serializado que se puede cargar más adelante para volver a crear la escena en modo de reproducción del editor.

## <a name="setup"></a>Configurar

> [!IMPORTANT]
> Scene Understanding solo se admite en HoloLens 2 y Unity 2019.4 y versiones posteriores.

1. Asegúrese de que la plataforma está establecida en UWP en la configuración de compilación.
1. Adquiera el paquete Scene Understanding a través [de Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Uso de Scene Understanding

La manera más rápida de empezar a trabajar con Scene Understanding es consultar la escena de ejemplo.

### <a name="scene-understanding-sample-scene"></a>Escena de ejemplo de Scene Understanding

En Unity, use el explorador de Project para abrir el archivo de escena en `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` y presione Reproducir.

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Solo se aplica a MRTK 2.6.0: al usar la herramienta de características de Mixed Reality o importar a través de UPM, importe el ejemplo Demos - SpatialAwareness antes de importar el ejemplo Experimental - SceneUnderstanding debido a un problema de dependencia. Consulte este [GitHub problema para](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) obtener más información.

::: moniker-end
En la escena se muestra lo siguiente:

* Visualización de objetos de escena observados con en la interfaz de usuario de la aplicación para configurar el observador
* Script `DemoSceneUnderstandingController` de ejemplo que muestra cómo cambiar la configuración del observador y escuchar los eventos pertinentes
* Guardar los datos de la escena en el dispositivo para el desarrollo sin conexión
* Carga de datos de escena previamente guardados (archivos .bytes) para admitir el flujo de trabajo de desarrollo en el editor

> [!IMPORTANT]
> De forma `ShouldLoadFromFile` predeterminada, la propiedad del observador se establece en false. Para ver la visualización de una sala de ejemplo serializada, consulte la sección configuración del servicio [de](#configuring-the-observer-service) observador a continuación y establezca la propiedad en true en el editor.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> La escena de ejemplo se basa en la canalización XR heredada. Si usa la canalización del SDK de XR, debe modificar los perfiles en consecuencia. El perfil del sistema de reconocimiento espacial de Scene Understanding proporcionado ( ) y los perfiles de observador de Scene Understanding ( y `DemoSceneUnderstandingSystemProfile` ) funciona para ambas `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` canalizaciones.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> La escena de ejemplo registra una `There is no active AsyncCoroutineRunner when an action is posted.` advertencia en determinadas circunstancias debido al orden de ejecución de inicialización o subproceso. Si puedes confirmar que el componente está asociado al GameObject "Demo Controller" y el componente/GameObject permanece habilitado o activo en la escena (el caso predeterminado), la advertencia se puede omitir de forma `AsyncCoroutineRunner` segura. **Sin embargo, al crear una escena con Scene Understanding, asegúrese de crear un objeto GameObject vacío en la raíz y adjuntar el script a ella; de lo contrario, Scene Understanding podría no funcionar `AsyncCoroutineRunner` correctamente.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Configuración del servicio de observador

Seleccione el objeto de juego "MixedRealityToolkit" y compruebe el inspector.

![descripción de la ubicación de la escena en la jerarquía](../images/spatial-awareness/MRTKHierarchy.png)

![Ubicación de MRTK en inspector](../images/spatial-awareness/MRTKLocation.png)

Estas opciones le permitirán configurar `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script de ejemplo

El script de _ejemplo DemoSceneUnderstandingController.cs_ muestra los conceptos principales para trabajar con el servicio Scene Understanding.

* Suscripción a eventos de Scene Understanding
* Control de eventos de Scene Understanding
* Configuración de en `WindowsSceneUnderstandingObserver` tiempo de ejecución

Los alternancias del panel de la escena cambian el comportamiento del observador de comprensión de la escena mediante una llamada a las funciones públicas de este script de ejemplo.

Al activar Crear instancias *prefabs,* se mostrará la creación de objetos de ese tamaño para ajustarse a todos [los objetos SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)recopilados perfectamente bajo un objeto primario.

![Opciones del controlador de demostración](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Notas de la aplicación integrada

Compile e implemente en HoloLens de la manera estándar. Una vez en ejecución, debería aparecer una serie de botones para reproducir con las características.

Tenga en cuenta que hay algunas dificultades en la realización de consultas al observador. La configuración incorrecta de una solicitud de captura hace que la carga del evento no contenga los datos esperados. Por ejemplo, si no se solicitan cuatros, no habrá texturas de máscara de oclusión. Como es aconsejable, no aparecerá ninguna malla de mundo si el observador no está configurado para solicitar mallas. El `DemoSceneUnderstandingController` script se encarga de algunas de estas dependencias, pero no todas.

Se puede acceder a los archivos de escena guardados a través del [portal del dispositivo](/windows/mixed-reality/using-the-windows-device-portal) en `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Estos archivos de escena se pueden usar en el editor si se especifican en el perfil de observador que se encuentra en el inspector.

![Portal de dispositivos ubicación del archivo de bytes](../images/spatial-awareness/BytesInDevicePortal.png)

![Bytes de escena serializados en el observador](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Consulte también

* [Información general sobre la comprensión de la escena](/windows/mixed-reality/scene-understanding)
* [Introducción al SDK de Scene Understanding](/windows/mixed-reality/scene-understanding-sdk)
