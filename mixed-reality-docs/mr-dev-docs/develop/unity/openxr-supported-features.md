---
title: Características admitidas del complemento OpenXR en Unity
description: Descubra las características que admite OpenXR para el desarrollo de realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: e6756df7f082e56b029b6e82e06d960ba39ed04a
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894005"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Mixed Reality compatibles con OpenXR en Unity

El Mixed Reality complemento **OpenXR** es una extensión del complemento **OpenXR** de Unity y admite un conjunto de características para HoloLens 2 y Windows Mixed Reality cascos. Antes de continuar, asegúrese de que el proyecto de Unity [está configurado para OpenXR.](openxr-getting-started.md)

## <a name="whats-supported"></a>Lo que se admite

Actualmente se admiten las siguientes características:

* Admite aplicaciones para UWP HoloLens 2 y optimización para HoloLens 2 modelo de aplicación.
* Admite aplicaciones win32 VR para Windows Mixed Reality cascos con perfiles de controlador más recientes y comunicación remota de aplicaciones holográficas.
* Seguimiento de escala mundial mediante delimitadores y espacio sin enlazar.
* [API de almacenamiento de delimitadores para conservar los](spatial-anchors-in-unity.md) delimitadores HoloLens 2 almacenamiento local.
* [Controlador de movimiento e interacciones de manos,](#motion-controller-and-hand-interactions)incluido el nuevo controlador HP Reverb G2.
* Seguimiento de manos articulado mediante 26 uniones y entradas de radio de la unión.
* Interacción de la mirada con los ojos HoloLens 2.
* Ubicación de la cámara de foto/vídeo (PV) en HoloLens 2.
* Captura de realidad mixta la representación de tercer ojo a través de la cámara PV.
* Admite ["Play" para HoloLens 2](#holographic-remoting-in-unity-editor-play-mode)con la aplicación holographic Remoting , lo que permite a los desarrolladores depurar scripts sin necesidad de compilar e implementar en el dispositivo.
* Compatible con MRTK Unity 2.5.3 y versiones posteriores a través de compatibilidad con el proveedor [de OpenXR de MRTK.](openxr-getting-started.md#using-mrtk-with-openxr-support)
* Compatible con UNITY [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior.
* (Se agregó en 0.1.3) Admite [la comunicación remota holográfica de](holographic-remoting-desktop.md) aplicaciones de escritorio desde una aplicación independiente de Windows integrada e implementada.
* (Se agregó en 0.1.4) Admite [el seguimiento de código QR](#qr-codes) en HoloLens2 a través de SpatialGraphNode
* (Se agregó en la versión 0.2.0) Admite **el anclaje** en la comunicación remota holográfica
* (Se agregó en la versión 0.2.0) Admite tanto las **uniones de mano como el seguimiento de mallas de mano.**
* (Se agregó en la versión 0.2.0) Admite **ARPlaneSubsystems para la** detección de plano y colocar hologramas mediante **ARRaycastManager.**
* (0.9.0) Admite **XRMeshSubsystem** y **ARMeshManager** para la asignación espacial.
* (Se agregó en la versión 0.9.0) Admite el complemento azure Spatial Anchors SDK para Windows. Para más información, consulte el proyecto [Mixed Reality ejemplo de azure Spatial Anchors OpenXR + OpenXR en GitHub.](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples/tree/main/AzureSpatialAnchorsSample)
* (Se agregó en la versión 0.9.1) Admite la comunicación remota holográfica de aplicaciones de escritorio desde una aplicación para UWP de Windows compilada e implementada.

## <a name="holographic-remoting-setup"></a>Configuración de Holographic Remoting

1. En primer lugar, debe [instalar la aplicación Holographic Remoting Player](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la Microsoft Store en el HoloLens 2
2. Ejecute la aplicación Holographic Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a los que conectarse.
    * Necesitará la versión 2.4 o posterior para trabajar con el complemento OpenXR.

    ![Captura de pantalla del reproductor de comunicación remota holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting in Unity Editor play mode (Comunicación remota holográfica en el modo de reproducción del Editor de Unity)

Compilar un proyecto de Unity para UWP en Visual Studio proyecto y, a continuación, empaquetar e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la característica de comunicación remota del editor holográfico, que le permite depurar el script de C# mediante el modo "Reproducir" directamente en un dispositivo HoloLens 2 a través de la red. Este escenario evita la sobrecarga de compilar e implementar un paquete de UWP en el dispositivo remoto.

1. Siga los pasos descritos en [Configuración de Holographic Remoting.](#holographic-remoting-setup)
2. Abra **Editar -> configuración** del proyecto, vaya a Administración del complemento **XR** y active la casilla **Windows Mixed Reality conjunto de características:**

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con la administración de complementos XR resaltada](images/openxr-features-img-02.png)

3. Expanda la **sección Características** en **OpenXR** y seleccione **Mostrar todo.**
4. Active la **casilla Holographic Editor Remoting (Comunicación** remota del editor holográfico) e introduzca la dirección IP que obtiene de la aplicación Holographic Remoting:

    ![Captura de pantalla del panel de configuración del proyecto abierto en el Editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "Play" (Reproducir) para reproducir la aplicación unity en la aplicación Holographic Remoting en HoloLens. También puede adjuntar [Visual Studio a Unity para](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0, el entorno de ejecución de comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica viene en futuras versiones.

## <a name="motion-controller-and-hand-interactions"></a>Interacciones de controlador de movimiento e mano

Para conocer los conceptos básicos sobre las interacciones de realidad mixta en Unity, visite el Manual de [Unity para la entrada XR de Unity.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html) En esta documentación de Unity se tratan las asignaciones de entradas específicas del controlador a entradas más **generalizablesFeatureUsage,** cómo se pueden identificar y clasificar las entradas XR disponibles, cómo leer datos de estas entradas y mucho más.

El Mixed Reality complemento OpenXR proporciona perfiles de interacción de entrada adicionales, asignados a **inputFeatureUsage** estándar, como se detalla a continuación:

| InputFeatureUsage | Controlador HP Reverb G2 (OpenXR) | HoloLens Hand (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Fuenquete: haga clic en | |
| desencadenador | Desencadenador  | |
| Agarre | Agarre | Pulsación o presión en el aire |
| primaryButton | [X/A] - Press | Pulsar en el aire |
| secondaryButton | [Y/B] - Press | |
| gripButton | Control: presione | |
| triggerButton | Desencadenador: presionar | |
| menuButton | Menú | |

### <a name="aim-and-grip-poses"></a>Poses de puntería y control

Tiene acceso a dos conjuntos de poses a través de interacciones de entrada de OpenXR:

* El control posa para representar objetos en la mano
* El objetivo es apuntar al mundo.

Puede encontrar más información sobre este diseño y las diferencias entre las dos posturas en [Especificación de OpenXR: subpaths de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Las poses proporcionadas por InputFeatureUsages **DevicePosition,** **DeviceRotation,** **DeviceVelocity** y **DeviceAngularVelocity** representan la posición de control de OpenXR.  InputFeatureUsages relacionados con las poses de control se definen en [CommonUsages de](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)Unity.

Las poses proporcionadas por InputFeatureUsages **PointerPosition**, **PointerRotation,** **PointerVelocity** y **PointerAngularVelocity** representan la posición de objetivo de OpenXR.  Estos inputFeatureUsages no se definen en los archivos de C# incluidos, por lo que deberá definir sus propios inputFeatureUsages como se muestra a continuación:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Haptics

Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el Manual de Unity para la entrada XR de [Unity: hápticos.](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)

## <a name="qr-codes"></a>Códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código. Puede encontrar más detalles en nuestra documentación [de seguimiento de código QR.](../platform-capabilities-and-apis/qr-code-tracking.md)  Cuando use el complemento OpenXR, tome el de [ `SpatialGraphNodeId` la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la API para buscar el código `Microsoft.MixedReality.OpenXR.SpatialGraphNode` QR.

Como referencia, tenemos un proyecto [de ejemplo de seguimiento QR en GitHub](https://github.com/yl-msft/QRTracking) con una explicación de uso más detallada para la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="whats-coming-soon"></a>Próximamente

Los siguientes problemas y características que faltan se conocen con Mixed Reality del complemento OpenXR **versión 0.9.2.** Estamos trabajando en ellas y lanzaremos correcciones y nuevas características en las próximas versiones.

* **ARM64 es** la única plataforma compatible con HoloLens 2 aplicaciones. La **plataforma ARM** está disponible en una versión futura.

## <a name="troubleshooting"></a>Solución de problemas

Cuando suspendes y reanudas una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista HoloLens.

* Establezca **Modo de envío de profundidad** en **Ninguno** en la configuración del proyecto de OpenXR como solución alternativa.
