---
title: Historial de versiones de Holographic Remoting
description: Manténgase al día sobre el historial de versiones de la característica de comunicación remota de Holographic para HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, historial de versiones, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 84caf761af15645410c7439660747fa2f369c6c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009525"
---
# <a name="holographic-remoting-version-history"></a>Historial de versiones de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## <a name="version-240-december-1-2020"></a>Versión 2.4.0 (1 de diciembre de 2020) <a name="v2.4.0"></a>

* Holographic Remoting ahora admite la escritura de aplicaciones remotas mediante la [API de OpenXR](../native/openxr.md). Consulte [escritura de una aplicación remota de Holographic Remoting con las API de OpenXR](holographic-remoting-create-remote-openxr.md) para comenzar.
* Correcciones de errores y mejoras de estabilidad.

## <a name="version-231-october-10-2020"></a>Versión 2.3.1 (10 de octubre de 2020) <a name="v2.3.1"></a>

* Se corrigió la regresión con la predicción de supuestos remotas, lo que causó vibraciones visuales.
* Implementó PerceptionDeviceSetCreateFactoryOverride, que garantiza que PerceptionDevice.dll distribuidas con Holographic Remoting no interfiere con la versión que se incluye con Windows 10.

## <a name="version-230-october-2-2020"></a>Versión 2.3.0 (2 de octubre de 2020) <a name="v2.3.0"></a>

* Se han corregido bloqueos, que pueden producirse cuando se suspende el reproductor de comunicación remota holográfica.
* Mejoras de estabilidad.

## <a name="version-223-august-28-2020"></a>Versión 2.2.3 (28 de agosto de 2020) <a name="v2.2.3"></a>

* Correcciones de errores y mejoras de estabilidad.

## <a name="version-222-july-10-2020"></a>Versión 2.2.2 (10 de julio de 2020) <a name="v2.2.2"></a>

* Se corrigió un problema con [HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters) y [HolographicCamera. RightViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters) que no devuelve ningún vértice de malla de área oculta cuando se transmite desde un casco de realidad mixta de Windows.
* Se ha corregido el bloqueo, lo que puede ocurrir cuando la conexión de red es deficiente.

## <a name="version-221-july-6-2020"></a>Versión 2.2.1 (6 de julio de 2020) <a name="v2.2.1"></a>

> [!IMPORTANT]
> La validación del [Kit de certificación de aplicaciones de Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) con la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) producirá un error. En caso de que se encuentre en la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) y desee enviar su aplicación a la concesión de Microsoft Store p actualizada a la versión 2.2.1 como mínimo.
* Problemas de compatibilidad con el [Kit de certificación de aplicaciones de Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versión 2.2.0 (1 de julio de 2020) <a name="v2.2.0"></a>

* El reproductor de comunicación remota holográfica ahora se puede instalar en equipos que ejecutan [Windows Mixed Reality](../../discover/navigating-the-windows-mixed-reality-home.md), lo que permite la transmisión por secuencias a auriculares envolventes.
* [Los controladores de movimiento](../../design/motion-controllers.md) ahora se admiten en la comunicación remota de Holographic y los datos específicos del controlador se pueden recuperar a través de [SpatialInteractionSource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* Ahora se admite [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) y la fase actual se puede recuperar a través de [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Además, se puede solicitar una nueva fase a través de [SpatialStageFrameOfReference. RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* En versiones anteriores, el reproductor remoto Holographic controlaba la predicción en el reproductor. A partir de la versión 2.2.0, Holographic Remoting tiene sincronización de hora y la aplicación remota realiza la predicción por completo. Los usuarios también deben esperar una mejor estabilidad del holograma en situaciones de red difíciles.

## <a name="version-213-may-25-2020"></a>Versión 2.1.3 (25 de mayo de 2020) <a name="v2.1.3"></a>

* Se ha cambiado el comportamiento del evento [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) . En versiones anteriores, **no** se garantizaba que un [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera) agregado también tenga un [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) válido al crear el siguiente fotograma a través de [HolographicSpace. CreateNextFrame](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe). A partir de la versión 2.1.3, [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded) se sincroniza con los datos de pose procedentes del reproductor remoto holográfica. Los usuarios pueden esperar que cuando se agrega una cámara, también haya un [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose) válido disponible para esa cámara en el fotograma siguiente.
* Se ha agregado **deshabilitado** a DepthBufferStreamResolution, que se puede usar para deshabilitar el streaming de búfer de profundidad a través de RemoteContext.ConfigureDepthVideoStream. Tenga en cuenta que, si se usa [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) , se producirá un error con *E_ILLEGAL_METHOD_CALL*.
* La pantalla de inicio del reproductor remoto Holographic se ha rediseñado y ahora no bloquea la vista de usuarios.
* Mejoras de estabilidad y correcciones de errores.

## <a name="version-212-april-5-2020"></a>Versión 2.1.2 (5 de abril de 2020) <a name="v2.1.2"></a>

* Se corrigió el problema de compatibilidad con versiones anteriores de audio entre el reproductor remoto Holographic y las aplicaciones remotas con una versión inferior a la 2.1.0.
* Problema fijo de delimitador espacial, que cerró inesperadamente el reproductor de comunicación remota holográfica. Este problema también afecta a los reproductores personalizados.

## <a name="version-211-march-20-2020"></a>Versión 2.1.1 (20 de marzo de 2020) <a name="v2.1.1"></a>

* Se corrigió el problema de codificación de vídeo con las aplicaciones remotas al usar GPU AMD.
* Mejoras en el rendimiento del reproductor remoto holográfica.

## <a name="version-210-march-11-2020"></a>Versión 2.1.0 (11 de marzo de 2020) <a name="v2.1.0"></a>

* Transporte de red conmutada para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) a través de UDP. Conexiones seguras use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) ahora. Tenga en cuenta que el [reproductor de comunicación remota holográfica](holographic-remoting-player.md) todavía es compatible con todas las versiones anteriores de Holographic Remoting. Para beneficiarse del nuevo transporte de red, el reproductor de comunicación remota holográfica y la aplicación remota en cuestión deben usar la versión 2.1.0.
* Compatibilidad agregada para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versión 2.0.20 (2 de febrero de 2020) <a name="v2.0.20"></a>

* Se corrigieron varios errores que provocan bloqueos.

## <a name="version-2018-december-17-2019"></a>Versión 2.0.18 (17 de diciembre de 2019) <a name="v2.0.18"></a>

* Compatibilidad agregada para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Se corrigieron varios errores que provocan bloqueos.
* Se corrigió un error en el que se necesitaba una devolución de llamada HolographicSpace. CameraAdded para que un HolographicCamera se aceptara y se mostrara como una cámara agregada en el HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versión 2.0.16 (11 de noviembre de 2019) <a name="2.0.16"></a>

* Se corrigió el interbloqueo en el seguimiento del código QR.
* Se corrigió la excepción unhandeled debido a una espera de bloqueo en el subproceso principal.

## <a name="version-2014-october-26-2019"></a>Versión 2.0.14 (26 de octubre de 2019) <a name="v2.0.14"></a>

* Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).
* Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.
* Problema de subprocesos corregido al usar SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versión 2.0.12 (18 de octubre de 2019) <a name="v2.0.12"></a>

* Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versión 2.0.10 (10 de octubre de 2019) <a name="v2.0.10"></a>

* Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR. Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versión 2.0.9 (19 de septiembre de 2019) <a name="v2.0.9"></a>

* Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Nueva interfaz agregada ```IPlayerContext2``` (implementada por ```PlayerContext``` ) que proporciona los siguientes miembros:
  - Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* ```Failed_RemoteFrameTooOld```Valor agregado a```BlitResult```
* Mejoras en la estabilidad y confiabilidad

## <a name="version-208-august-20-2019"></a>Versión 2.0.8 (20 de agosto de 2019) <a name="v2.0.8"></a>

* Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.
* Mejoras en la estabilidad y confiabilidad

## <a name="version-207-july-26-2019"></a>Versión 2.0.7 (26 de julio de 2019) <a name="v2.0.7"></a>

* Primera versión pública de Holographic Remoting para HoloLens 2.

## <a name="see-also"></a>Consulte también

* [Escritura de una aplicación remota Holographic Remoting con las API de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting con las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
