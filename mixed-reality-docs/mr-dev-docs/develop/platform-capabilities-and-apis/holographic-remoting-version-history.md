---
title: Historial de versiones de comunicación remota holográfica
description: Manténgase al día sobre el historial de versiones de la característica de comunicación remota holográfica para HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 06/10/2021
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, historial de versiones, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: dae7bc0dac792cbe1a8472415d5e9fa34532e918
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908223"
---
# <a name="holographic-remoting-version-history"></a>Historial de versiones de comunicación remota holográfica

> [!IMPORTANT]
> Esta guía es específica de la comunicación remota holográfica en HoloLens 2.

## <a name="version-260-june-10-2021"></a>Versión 2.6.0 (10 de junio de 2021) <a name="v2.6.0"></a>
* La comunicación remota holográfica con la API de OpenXR ahora admite:
  * La nueva XR_MSFT_holographic_remoting_speech, que permite a las aplicaciones escuchar comandos de voz personalizados en varios idiomas.
  * La extensión XR_MSFT_scene_understanding, que proporciona a las aplicaciones una representación estructurada y de alto nivel de los planos, mallas y objetos en el entorno del usuario, lo que permite el desarrollo de aplicaciones con conocimiento espacial. Sin embargo, con la advertencia de XR_SCENE_COMPUTE_CONSISTENCY_OCCLUSION_OPTIMIZED_MSFT es la única coherencia admitida por xrComputeNewSceneMSFT.
  * La extensión XR_MSFT_spatial_graph_bridge, que permite a las aplicaciones crear identificadores XrSpace para realizar un seguimiento de los nodos de Spatial Graph de otras API o bibliotecas de plataformas de dispositivos Windows Mixed Reality dispositivos. Sin embargo, con la advertencia de que XR_SPATIAL_GRAPH_NODE_TYPE_STATIC_MSFT es el único tipo de nodo admitido por xrCreateSpatialGraphNodeSpaceMSFT. 
* La comunicación remota holográfica mediante Mixed Reality API ahora admite:
  * Las sobrecargas SpatialGraphInteropPreview.CreateCoordinateSystemForNode, que permiten a las aplicaciones realizar un seguimiento de los nodos estáticos de Spatial Graph para que los usuarios puedan razonar sobre los lugares y las cosas de su entorno.
* La comunicación remota holográfica con OpenXR y Mixed Reality API ahora admite:
  * El SDK Microsoft.MixedReality.SceneUnderstanding, que permite a las aplicaciones calcular una descripción de la escena que rodea al usuario (como paredes, plantas y superficies) que proporciona cuádros, mallas y indicaciones de colocación de contenido.
  * El SDK de Microsoft.MixedReality.QR, que permite a las aplicaciones realizar un seguimiento de la ubicación, el tamaño y el contenido de los códigos QR detectados.
* El ejemplo remoto de OpenXR se ha actualizado para incluir: 
  * Un ejemplo del uso de la XR_MSFT_holographic_remoting_speech extensión.
* El Mixed Reality ejemplo remoto se ha actualizado para incluir:  
  * Un ejemplo del uso del SDK Microsoft.MixedReality.SceneUnderstanding.
  * Un ejemplo del uso del SDK de Microsoft.MixedReality.QR (que reemplaza al mecanismo de detección de código QR anterior).
* El reproductor de Holographic Remoting ahora muestra una animación de carga mientras se establece la conexión.
* Se han corregido problemas con la compatibilidad de RenderDoc tanto en el entorno de ejecución de la API de OpenXR como en el ejemplo Mixed Reality API.
* Varias correcciones de errores y mejoras de estabilidad.

## <a name="version-250-february-12-2021"></a>Versión 2.5.0 (12 de febrero de 2021) <a name="v2.5.0"></a>
* La comunicación remota holográfica con [la API de OpenXR](../native/openxr.md) ahora admite:
  * XR_MSFT_spatial_anchor extensión. Esta extensión permite a una aplicación crear delimitadores espaciales, que son puntos de espacio libre arbitrarios en el entorno físico del usuario de los que el tiempo de ejecución realizará un seguimiento.
  * XR_MSFT_controller_model extensión. Esta extensión proporciona un mecanismo para cargar modelos GLTF para controladores.
  * Canales de datos personalizados como parte de la extensión XR_MSFT_holographic_remoting datos. Un ejemplo de esto se muestra en el ejemplo [remoto de OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).
* Sincronización mejorada entre el reproductor y el lado remoto. Esto permite cambiar dinámicamente la posición y el almacenamiento en búfer de fotogramas, lo que garantiza que el contenido representado de forma remota llega sin problemas a las pantallas a la velocidad de fotogramas de destino esperada.
* Rendimiento mejorado del reproductor de Holographic Remoting disponible a través del Microsoft Store. En HoloLens 2 el reproductor ahora se ejecuta sólido en 60 fotogramas por segundo.
* Transmisión optimizada de mallas de superficie espacial que una aplicación remota puede consultar a través de [SpatialSurfaceObserver.](/uwp/api/windows.perception.spatial.surfaces.spatialsurfaceobserver)
* Se ha corregido un problema en el que la llamada a métodos SpatialAnchorManager o la liberación de delimitadores provocaban excepciones al desconectarse.
* Se ha corregido un problema de subprocesos que provocaba bloqueos al cerrar instancias de PlayerContext o RemoteContext.
* Holographic Remoting Player on Desktop (Reproductor de comunicación remota holográfica en el escritorio): muestra un mensaje de error Windows Mixed Reality no está instalado en lugar de cerrarse en modo silencioso.
* Muchas otras correcciones de errores y mejoras de estabilidad.

## <a name="version-241-january-22-2021"></a>Versión 2.4.1 (22 de enero de 2021) <a name="v2.4.1"></a>

* Se ha corregido un problema con SpatialAnchorManager::RequestStoreAsync que no funcionaba de forma confiable cuando se llamaba al conectarse.
* Se ha corregido un problema con SpatialAnchorManager::TrySave no guardaba correctamente un delimitador si el delimitador en cuestión no se podía localizar.

## <a name="version-240-december-1-2020"></a>Versión 2.4.0 (1 de diciembre de 2020) <a name="v2.4.0"></a>

* La comunicación remota holográfica ahora admite la escritura de aplicaciones remotas mediante [la API de OpenXR.](../native/openxr.md) Consulte Escritura de una aplicación remota de comunicación remota holográfica con las API de [OpenXR](holographic-remoting-create-remote-openxr.md) para empezar a trabajar.
* Correcciones de errores y mejoras de estabilidad.

## <a name="version-231-october-10-2020"></a>Versión 2.3.1 (10 de octubre de 2020) <a name="v2.3.1"></a>

* Se ha corregido la regresión con la predicción de posición remota, lo que provocaba vibración visual.
* Se implementó PerceptionDeviceSetCreateFactoryOverride, lo que garantiza que PerceptionDevice.dll se incluye con la comunicación remota holográfica no interfiere con la versión enviada con Windows 10.

## <a name="version-230-october-2-2020"></a>Versión 2.3.0 (2 de octubre de 2020) <a name="v2.3.0"></a>

* Se han corregido bloqueos, que pueden producirse cuando se suspende holographic Remoting Player.
* Mejoras de estabilidad.

## <a name="version-223-august-28-2020"></a>Versión 2.2.3 (28 de agosto de 2020) <a name="v2.2.3"></a>

* Correcciones de errores y mejoras de estabilidad.

## <a name="version-222-july-10-2020"></a>Versión 2.2.2 (10 de julio de 2020) <a name="v2.2.2"></a>

* Se ha corregido un problema con [HolographicCamera.LeftViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) y [HolographicCamera.RightViewportParameters](/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) que no devolvía ningún vértice de malla de área oculta al transmitir desde un casco de Windows Mixed Reality.
* Se ha corregido un bloqueo, que puede producirse con una conexión de red deficiente.

## <a name="version-221-july-6-2020"></a>Versión 2.2.1 (6 de julio de 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> [Kit para la certificación de aplicaciones en Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) validación con [la versión 2.2.0](holographic-remoting-version-history.md#v2.2.0) producirá un error. En caso de que se encuentra en la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) y desea enviar la aplicación a la concesión p de Microsoft Store actualizada a la versión 2.2.1 como mínimo.
* Se han [Kit para la certificación de aplicaciones en Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) problemas de cumplimiento normativo.

## <a name="version-220-july-1-2020"></a>Versión 2.2.0 (1 de julio de 2020) <a name="v2.2.0"></a>

* El reproductor de Holographic Remoting ahora se puede instalar en equipos que ejecutan [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), lo que permite transmitir a cascos envolventes.
* [Los controladores](../../design/motion-controllers.md) de movimiento ahora son compatibles con la comunicación remota holográfica y los datos específicos del controlador se pueden recuperar a través [de SpatialInteractionSource.Controller.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
* [SpatialStageFrameOfReference](/uwp/api/windows.perception.spatial.spatialstageframeofreference) ahora se admite y la fase actual se puede recuperar a través [de SpatialStageFrameOfReference.Current.](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current) Además, se puede solicitar una nueva fase a través [de SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* En versiones anteriores, la predicción de la posición se controló en el lado del jugador mediante el reproductor de Holographic Remoting. A partir de la versión 2.2.0, la comunicación remota holográfica tiene sincronización de hora y la predicción la realiza completamente la aplicación remota. Los usuarios también deben esperar una estabilidad mejorada del holograma en situaciones de red difíciles.

## <a name="version-213-may-25-2020"></a>Versión 2.1.3 (25 de mayo de 2020) <a name="v2.1.3"></a>

* Se ha cambiado el [comportamiento del evento HolographicSpace.CameraAdded.](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) En versiones anteriores,  no se garantizaba que un [elemento HolographicCamera](/uwp/api/windows.graphics.holographic.holographiccamera) agregado también tenga un elemento [HolographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válido al crear el fotograma siguiente a través de [HolographicSpace.CreateNextFrame.](/uwp/api/windows.graphics.holographic.holographicspace.createnextframe) A partir de la versión 2.1.3, [HolographicSpace.CameraAdded](/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) se sincroniza con los datos de posición procedentes de Holographic Remoting Player. Los usuarios pueden esperar que cuando se agrega una cámara también haya un [holographicCameraPose](/uwp/api/windows.graphics.holographic.holographiccamerapose) válido disponible para esa cámara en el fotograma siguiente.
* Se ha **agregado Disabled a** DepthBufferStreamResolution, que se puede usar para deshabilitar el streaming de búfer de profundidad a través RemoteContext.ConfigureDepthVideoStream. Tenga en cuenta que si [se usa HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer,](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) se producirá un *error E_ILLEGAL_METHOD_CALL*.
* La pantalla de inicio de Holographic Remoting Player se ha rediseñado y ahora no bloquea la vista de los usuarios.
* Mejoras de estabilidad y correcciones de errores.

## <a name="version-212-april-5-2020"></a>Versión 2.1.2 (5 de abril de 2020) <a name="v2.1.2"></a>

* Se ha corregido un problema de compatibilidad con versiones anteriores de audio entre la versión más reciente del reproductor de Holographic Remoting y las aplicaciones remotas que usaban una versión inferior a la 2.1.0.
* Se ha corregido un problema de delimitador espacial, que cerró inesperadamente el reproductor de Comunicación remota holográfica. Este problema también afecta a los reproductores personalizados.

## <a name="version-211-march-20-2020"></a>Versión 2.1.1 (20 de marzo de 2020) <a name="v2.1.1"></a>

* Se ha corregido un problema de codificación de vídeo con aplicaciones remotas al usar GPU AMD.
* Mejoras de rendimiento de Holographic Remoting Player.

## <a name="version-210-march-11-2020"></a>Versión 2.1.0 (11 de marzo de 2020) <a name="v2.1.0"></a>

* Se cambió el transporte de red [para usar RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) a través de UDP. Las conexiones seguras [usan SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) ahora. Tenga en cuenta [que Holographic Remoting Player](holographic-remoting-player.md) sigue siendo compatible con todas las versiones anteriores de Holographic Remoting. Para beneficiarse del nuevo transporte de red, tanto holographic Remoting Player como la aplicación remota en cuestión deben usar la versión 2.1.0.
* Se ha agregado compatibilidad [con HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versión 2.0.20 (2 de febrero de 2020) <a name="v2.0.20"></a>

* Se han corregido varios errores que provocaron bloqueos.

## <a name="version-2018-december-17-2019"></a>Versión 2.0.18 (17 de diciembre de 2019) <a name="v2.0.18"></a>

* Se ha agregado compatibilidad con [HolographicViewConfiguration.](/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Se han corregido varios errores que provocaron bloqueos.
* Se ha corregido un error por el que se requería una devolución de llamada de HolographicSpace.CameraAdded para que holographicCamera se aceptara y se mostrara como cámara agregada en HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versión 2.0.16 (11 de noviembre de 2019) <a name="2.0.16"></a>

* Se ha corregido el interbloqueo en el seguimiento de código QR.
* Se ha corregido una excepción no detectada debido a una espera de bloqueo en el subproceso principal.

## <a name="version-2014-october-26-2019"></a>Versión 2.0.14 (26 de octubre de 2019) <a name="v2.0.14"></a>

* Compatibilidad con las nuevas API perceptionDevice (Windows 10 de noviembre de 2019).
* Se ha corregido un problema que impedía que SpatialGestureRecognizer desencadenara eventos de gestos de retención.
* Se ha corregido un problema de subprocesos al usar SpatialSurfaceObserver.SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versión 2.0.12 (18 de octubre de 2019) <a name="v2.0.12"></a>

* Se ha corregido un bloqueo en SpatialGestureRecognizer cuando se usa NavigationRail(X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versión 2.0.10 (10 de octubre de 2019) <a name="v2.0.10"></a>

* Se ha corregido el bloqueo al usar el botón de desencadenador de los controladores vr. La comunicación remota holográfica no admite totalmente controladores, solo el botón de desencadenador y el botón de Windows funcionan si están emparejados con HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versión 2.0.9 (19 de septiembre de 2019) <a name="v2.0.9"></a>

* Se ha agregado compatibilidad [con SpatialAnchorExporter](/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Se ha agregado una nueva ```IPlayerContext2``` interfaz (implementada por ```PlayerContext``` ) que proporciona los miembros siguientes:
  - [Propiedad BlitRemoteFrameTimeout.](holographic-remoting-create-player.md#BlitRemoteFrameTimeout)
* Se ha agregado ```Failed_RemoteFrameTooOld``` un valor a ```BlitResult```
* Mejoras de estabilidad y confiabilidad

## <a name="version-208-august-20-2019"></a>Versión 2.0.8 (20 de agosto de 2019) <a name="v2.0.8"></a>

* Se ha corregido el bloqueo al llamar a [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con [IDXGISurface2 como](/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) parámetro.
* Mejoras de estabilidad y confiabilidad

## <a name="version-207-july-26-2019"></a>Versión 2.0.7 (26 de julio de 2019) <a name="v2.0.7"></a>

* Primera versión pública de Holographic Remoting para HoloLens 2.

## <a name="see-also"></a>Consulte también

* [Escritura de una aplicación remota de comunicación remota holográfica Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de comunicación remota holográfica mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)