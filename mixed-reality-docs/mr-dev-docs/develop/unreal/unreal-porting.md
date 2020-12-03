---
title: Actualización de proyectos en Unreal
description: Información general de los pasos de actualización de la versión y las API en desuso en proyectos de Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, códigos qr, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual
ms.openlocfilehash: efad783ee199ed42c7355917a180855b3ec4f11b
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355768"
---
# <a name="upgrading-projects-in-unreal"></a>Actualización de proyectos en Unreal

Cuando se realice una actualización a una nueva versión de Unreal, las funciones en desuso se mostrarán como advertencias al compilar el plano técnico o empaquetar el proyecto.  Las funciones pasan a estar en desuso cuando se ha agregado una nueva función que se debe usar en su lugar. 

## <a name="426-upgrades"></a>Actualizaciones de la versión 4.26
 
En la versión 4.26, todas las plataformas de AR y VR se han refactorizado a fin de agregar interfaces comunes y mantener la plataforma de código de aplicación independiente.  Debido a esta refactorización, es posible que los proyectos de HoloLens que se actualicen a la versión 4.26 vean más advertencias de lo habitual.  Se recomienda realizar la actualización a las nuevas API para que el proyecto se pueda migrar más fácilmente a otras plataformas.

Los mensajes de advertencia mostrarán qué función se encuentra en desuso y la función que se va a utilizar en su lugar.  Todas las funciones en desuso seguirán funcionando en esta versión, pero es posible que no funcionen en versiones futuras.  Las funciones en desuso ya no aparecerán en la lista al buscar funciones de un plano técnico.

![Plano técnico de la función Create Named ARPin](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>Desusos de la versión 4.25

| Funcionalidad en desuso | Nueva función |
| --- | --- |
| CreateNamedARPin | ![Plano técnico de la función Pin Component](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![Plano técnico de la función Load ARPins from Local Store](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![Plano técnico de la función Save ARPin to Local Store](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![Plano técnico de la función Remove ARPin from Local Store](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![Plano técnico de la función Set Enabled XRCamera](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![Plano técnico de la función Resize XRCamera](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![Plano técnico de la función Toggle ARCapture para iniciar la captura de la cámara](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![Plano técnico de la función Toggle ARCapture para detener la captura de la cámara](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![Plano técnico de la función Toggle ARCapture para iniciar la captura del código QR](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![Plano técnico de la función Toggle ARCapture para detener la captura del código QR](images/unreal-porting-img-11.png) |
| En la versión 4.25, la asignación espacial se iniciaba automáticamente, pero en la versión 4.26 se debe activar o desactivar. | ![Plano técnico de la función Toggle ARCapture para habilitar la asignación espacial](images/unreal-porting-img-12.png) |
| ShowKeyboard | Se quitó en la versión 4.26 porque el teclado se mostraba automáticamente cuando se ponía el foco en un widget de texto. |
| HideKeyboard | Se quitó en la versión 4.26 porque el teclado se ocultaba automáticamente cuando se quitaba el foco de un widget de texto. |
| SupportsHandTracking | ![Plano técnico de la propiedad Supports Hand Tracking](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![Plano técnico de la propiedad IsDisplayOpaque](images/unreal-porting-img-14.png) |
| GetHandJointTransform, GetPointerPoseInfo, GetControllerTrackingStatus | ![Plano técnico de la función Get Motion Controller Data](images/unreal-porting-img-15.png) |
| GetVersionString | ![Plano técnico de la función Get Version String](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![Plano técnico de la propiedad IsTrackingAvailable](images/unreal-porting-img-17.png) |
| IsButtonClicked, IsButtonDown, IsGrasped, IsSelectPressed | Use el sistema de acciones de entrada de Unreal. |
| SetFocusPointForFrame | Se quitó de la versión 4.26.  Anteriormente, se usaba para la reproyección al establecer una comunicación remota, pero ahora se admite la reproyección en profundidad. |