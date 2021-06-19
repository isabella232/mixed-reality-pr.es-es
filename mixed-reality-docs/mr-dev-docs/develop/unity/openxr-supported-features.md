---
title: Características admitidas del complemento OpenXR en Unity
description: Descubra las características que admite OpenXR para el desarrollo de realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: 371815d6410a7add8ee9c62f72d746d74ad397b0
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392673"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Mixed Reality compatibles con OpenXR en Unity

El Mixed Reality complemento **OpenXR** es una extensión del complemento **OpenXR** de Unity y admite un conjunto de características para HoloLens 2 y Windows Mixed Reality cascos. Antes de continuar, asegúrese de que el proyecto de Unity [está configurado para OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>Lo que se admite

Actualmente se admiten las siguientes características:

* Admite aplicaciones para UWP HoloLens 2 y optimización para HoloLens 2 modelo de aplicación.
* Admite aplicaciones win32 VR para Windows Mixed Reality cascos con perfiles de controlador más recientes y comunicación remota de aplicaciones holográficas.
* Seguimiento de escala mundial mediante delimitadores y espacio sin enlazar.
* [API de almacenamiento de delimitadores para conservar los](spatial-anchors-in-unity.md) delimitadores HoloLens 2 almacenamiento local.
* [Controlador de movimiento e interacciones con las manos,](#motion-controller-and-hand-interactions)incluido el nuevo controlador HP Reverb G2.
* Seguimiento de manos articulado mediante 26 uniones y entradas de radio de la unión.
* Interacción de la mirada con los ojos HoloLens 2.
* Ubicación de la cámara de foto/vídeo (PV) en HoloLens 2.
* Captura de realidad mixta la representación de tercer ojo a través de la cámara PV.
* Admite "Play" para HoloLens 2 con la aplicación [holographic Remoting,](unity-play-mode.md#unity-play-mode-with-holographic-remoting)lo que permite a los desarrolladores depurar scripts sin necesidad de compilar e implementar en el dispositivo.
* Compatible con MRTK Unity 2.5.3 y versiones más recientes a través de la compatibilidad con el proveedor [de OpenXR de MRTK.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Compatible con UNITY [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior.
* (Se agregó en 0.1.3) Admite [la comunicación remota holográfica de](holographic-remoting-desktop.md) aplicaciones de escritorio desde una aplicación independiente de Windows integrada e implementada.
* (Se agregó en 0.1.4) Admite [el seguimiento de código QR](#qr-codes) en HoloLens2 a través de SpatialGraphNode
* (Se agregó en 0.2.0) Admite **Anchor** in Holographic Remoting (Anclaje en comunicación remota holográfica)
* (Se agregó en 0.2.0) Admite tanto las **uniones de mano como el seguimiento de mallas de mano.**
* (Se agregó en 0.2.0) Admite **ARPlaneSubsystems para la** detección de plano y colocar hologramas mediante **ARRaycastManager**.
* (0.9.0) Admite **XRMeshSubsystem** y **ARMeshManager** para la asignación espacial.
* (Se agregó en 0.9.0) Admite el complemento azure Spatial Anchors SDK para Windows. Para más información, consulte el proyecto [de ejemplo Mixed Reality y OpenXR Azure Spatial Anchors en GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Se agregó en 0.9.1) Admite la comunicación remota holográfica de aplicaciones de escritorio desde una aplicación de Windows para UWP compilada e implementada.
* (Se agregó en 0.9.4) Admite la plataforma ARM además de ARM64 para HoloLens 2 aplicación.

## <a name="motion-controller-and-hand-interactions"></a>Interacciones de controlador de movimiento e mano

Para conocer los conceptos básicos sobre las interacciones de realidad mixta en Unity, visite el Manual de [Unity para la entrada XR de Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) En esta documentación de Unity se tratan las asignaciones de entradas específicas del controlador a entradas **más generalizablesFeatureUsage,** cómo se pueden identificar y clasificar las entradas XR disponibles, cómo leer datos de estas entradas y mucho más.

El Mixed Reality complemento OpenXR proporciona perfiles de interacción de entrada adicionales, asignados a **inputFeatureUsage** estándar, como se detalla a continuación:

| InputFeatureUsage | Controlador HP Reverb G2 (OpenXR) | HoloLens Hand (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Interruptor: haga clic en | |
| desencadenador | Desencadenador  | |
| Agarre | Agarre | Pulsación o presión en el aire |
| primaryButton | [X/A]: presionar | Pulsar en el aire |
| secondaryButton | [Y/B]: presionar | |
| gripButton | Control : presione | |
| triggerButton | Desencadenador: presione | |
| menuButton | Menú | |

### <a name="aim-and-grip-poses"></a>Poses de puntería y control

Tiene acceso a dos conjuntos de poses a través de interacciones de entrada de OpenXR:

* Las poses de control para representar objetos en la mano
* El objetivo es apuntar al mundo.

Puede encontrar más información sobre este diseño y las diferencias entre las dos posturas en [especificación de OpenXR: subpaths de entrada.](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)

Las poses proporcionadas por InputFeatureUsages **DevicePosition**, **DeviceRotation,** **DeviceVelocity** y **DeviceAngularVelocity** representan la posición de control de OpenXR.  InputFeatureUsages relacionados con las poses de control se definen en [CommonUsages de](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Las poses proporcionadas por InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** y **PointerAngularVelocity** representan la posición de objetivo de OpenXR.  Estos InputFeatureUsages no se definen en los archivos de C# incluidos, por lo que deberá definir sus propios inputFeatureUsages de la siguiente manera:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el Manual de Unity para la entrada XR de [Unity: hápticos.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="qr-codes"></a>Códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código. Puede encontrar más detalles en nuestra documentación [de seguimiento de código QR.](../platform-capabilities-and-apis/qr-code-tracking.md)  Cuando use el complemento OpenXR, tome el de [ `SpatialGraphNodeId` la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la API para buscar el código `Microsoft.MixedReality.OpenXR.SpatialGraphNode` QR.

Como referencia, tenemos un proyecto [de ejemplo de seguimiento QR en GitHub](https://github.com/yl-msft/QRTracking) con una explicación más detallada del uso de la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="troubleshooting"></a>Solución de problemas

Cuando suspendes y reanudas una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista HoloLens.

* Establezca **Modo de envío de profundidad** en **Ninguno** en la configuración del proyecto de OpenXR como solución alternativa.
