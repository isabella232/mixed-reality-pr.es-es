---
title: Solución de problemas y limitaciones de la comunicación remota holográfica
description: Encuentre recursos de solución de problemas e instrucciones para la característica de comunicación remota holográfica en dispositivos HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, Holographic Remoting, representación remota, representación en red, HoloLens, hologramas remotos, solución de problemas, ayuda, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 429ca7364d82e1713af059aa3c6da01852283120
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583832"
---
# <a name="holographic-remoting-troubleshooting"></a>Solución de problemas de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## <a name="spectre-mitigated-libraries-not-found"></a>No se encontraron bibliotecas mitigadas de Spectre.

Las aplicaciones de ejemplo de Holographic Remoting tienen habilitada la mitigación de Spectre (/Qspectre) en la configuración de versión.

Si obtiene el error irrecuperable de *vccorlib. lib* , asegúrese de que la carga de trabajo de Visual Studio incluye las [bibliotecas mitigadas de Spectre](/cpp/build/reference/qspectre)

## <a name="speech"></a>Voz

El reproductor de comunicación remota holográfica es compatible con una superposición de diagnósticos, que se puede habilitar diciendo ```Enable Diagnostics``` y deshabilitando ```Disable Diagnostics``` . Si tiene problemas con estos comandos de voz, también puede iniciar el reproductor de acceso remoto holográfica a través de un explorador Web usando ```ms-holographic-remoting:?stats``` como dirección URL.

## <a name="h265-video-codec-not-available"></a>Códec de vídeo de H265 no disponible

Instale las [extensiones de vídeo de HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) al usar el códec de vídeo H265 en la aplicación remota. Si surgen problemas en los que el códec está instalado pero no se pueden usar, consulte la guía de [solución de problemas](/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) .

## <a name="limitations"></a>Limitaciones

Actualmente **no** se admiten las siguientes API cuando se usa Holographic Remoting para HoloLens 2 y se producirá un ```ERROR_NOT_SUPPORTED``` error a menos que se indique lo contrario:

[Windows.Graphics.Holographic](/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - En versiones anteriores, siempre genera un error.
* [HolographicCamera.IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - En versiones anteriores, no se produce un error, pero no se cambia el tamaño de destino de representación.
* [HolographicCameraPose.OverrideProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose.OverrideViewport](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose.OverrideViewTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - Bermejo.
  - Compatible a partir de la versión [2.1.0](holographic-remoting-version-history.md#v2.1.0)
* [HolographicDisplay.TryGetViewConfiguration](/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - Al consultar HolographicViewConfigurationKind. PhotoVideoCamera, siempre se devolverá un ```nullptr``` .
  - Se admite a partir de la versión [2.0.18](holographic-remoting-version-history.md#v2.0.18)
  - En versiones anteriores, siempre genera un error.
* [HolographicSpace.CreateFramePresentationMonitor](/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay.GetDefault](/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - Notificará un error si se llama antes de que se establezca una conexión.


[Windows.Perception.Spatial](/uwp/api/windows.perception.spatial)

* [SpatialLocation. AbsoluteAngularAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation. AbsoluteAngularVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation. AbsoluteLinearAcceleration](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation. AbsoluteLinearVelocity](/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference. Current](/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
  - En versiones anteriores, siempre devuelven ```nullptr``` .
* [SpatialStageFrameOfReference.RequestNewStageAsync](/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)
* [SpatialAnchor.RemovedByUser](/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - En versiones anteriores, siempre devuelven ```nullptr``` . 
* [SpatialAnchorExporter.RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - Se admite a partir de la versión [2.0.9](holographic-remoting-version-history.md#v2.0.9). 
  - En versiones anteriores, la operación asincrónica siempre se completaba con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager. RequestAccessAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - La operación asincrónica siempre se completa con ```SpatialPerceptionAccessStatus.DeniedBySystem``` .
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - La operación asincrónica siempre se completa con ```false``` .
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - La operación asincrónica siempre se completa con ```nullptr``` .

[Windows.UI.Input.Spatial](/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource. Controller](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - Se admite a partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0)

[Windows.Perception.Spatial.Preview](/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>Consulte también
* [Historial de versiones de Holographic Remoting](holographic-remoting-version-history.md)
* [Escritura de una aplicación remota Holographic Remoting con las API de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting con las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)