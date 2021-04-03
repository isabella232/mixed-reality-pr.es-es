---
title: Características compatibles con el complemento OpenXR en Unity
description: Descubra las características que OpenXR admite para el desarrollo de la realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: d45cc9ab0c0c922c1946f4c188202a99f049f4fc
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088494"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Características admitidas de OpenXR de realidad mixta en Unity

El paquete de **Complementos OpenXR de realidad mixta** es una extensión del **complemento OpenXR** de Unity y admite un conjunto de características para los auriculares HoloLens 2 y Windows Mixed Reality. Antes de continuar, asegúrese de que el proyecto [de Unity está configurado para OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Lo que se admite

Actualmente se admiten las siguientes características:

* Admite aplicaciones de UWP para HoloLens 2 y optimizar para el modelo de aplicación de HoloLens 2.
* Admite aplicaciones Win32 VR para auriculares con Windows Mixed Reality con los perfiles de controlador más recientes y la comunicación remota de la aplicación holográfica.
* Seguimiento de escala mundial con delimitadores y espacio sin enlazar.
* [Delimite la API de almacenamiento para conservar los delimitadores](spatial-anchors-in-unity.md) en el almacenamiento local de HoloLens 2.
* Control de [movimiento y interacciones de mano](#motion-controller-and-hand-interactions), incluido el nuevo controlador de HP reverberación G2.
* Seguimiento de mano articulado mediante 26 uniones y entradas de radio uniones.
* Interacción de ojo mirada en HoloLens 2.
* Buscar la cámara de foto/vídeo (PV) en HoloLens 2.
* Captura de realidad mixta mediante la representación de la tercera vista a través de la cámara PV.
* Admite ["Play" en HoloLens 2 con la aplicación de comunicación remota holográfica](#holographic-remoting-in-unity-editor-play-mode), lo que permite a los desarrolladores depurar scripts sin compilar e implementar en el dispositivo.
* Compatible con MRTK Unity 2.5.3 y versiones más recientes a través de la compatibilidad con el [proveedor de MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatible con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior.
* (Agregado en 0.1.3) Admite la [comunicación remota de la aplicación de escritorio holográfica](holographic-remoting-desktop.md) desde una aplicación independiente de Windows compilada e implementada.
* (Agregado en 0.1.4) Admite el [seguimiento del código QR](#qr-codes) en HoloLens2 a través de SpatialGraphNode
* (Agregado en 0.2.0) Admite **delimitador** en la comunicación remota holográfica
* (Agregado en 0.2.0) Admite las **uniones a mano y el seguimiento de mallas** .
* (Agregado en 0.2.0) Admite **ARPlaneSubsystems** para la detección de planos y colocar el holograma mediante **ARRaycastManager**.
* (0.9.0) admite **XRMeshSubsystem** y **ARMeshManager** para la asignación espacial.

## <a name="holographic-remoting-setup"></a>Configuración de Holographic Remoting

1. En primer lugar, debe [instalar la aplicación de reproductor de comunicación remota holográfica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde el Microsoft Store en HoloLens 2.
2. Ejecute la aplicación holográfica Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a la que se conectará.
    * Necesitará v 2.4 o posterior para trabajar con el complemento OpenXR

    ![Captura de pantalla del reproductor de acceso remoto holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting en el modo de reproducción del editor de Unity

Compilar un proyecto de Unity de UWP en un proyecto de Visual Studio y, luego, empaquetarlo e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la característica de comunicación remota del editor holográfica, que le permite depurar el script de C# mediante el modo "reproducir" directamente en un dispositivo HoloLens 2 a través de la red. En este escenario se evita la sobrecarga de crear e implementar un paquete de UWP en un dispositivo remoto.

1. Siga los pasos del [programa de instalación de Holographic Remoting](#holographic-remoting-setup)
2. Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** :

    ![Captura de pantalla del panel de configuración del proyecto abrir en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-features-img-02.png)

3. Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**
4. Active la casilla de **comunicación remota del editor holográfica** y escriba la dirección IP que obtiene de la aplicación de acceso remoto holográfica:

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "reproducir" para reproducir la aplicación de Unity en la aplicación de acceso remoto holográfica en HoloLens. También puede [adjuntar Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0, el tiempo de ejecución de la comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica está disponible en futuras versiones.

## <a name="motion-controller-and-hand-interactions"></a>Interacciones de controlador de movimiento y mano

Para conocer los aspectos básicos sobre las interacciones de la realidad mixta en Unity, visite el [manual de Unity para la entrada de Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentación de Unity cubre las asignaciones de entradas específicas del controlador a **InputFeatureUsage** s más generalizadas, cómo se pueden identificar y clasificar las entradas de XR disponibles, cómo leer datos de estas entradas, etc.

El complemento OpenXR de realidad mixta proporciona perfiles de interacción de entrada adicionales, asignados a **InputFeatureUsage** s estándar, como se detalla a continuación:

| InputFeatureUsage | Controlador de HP reverberación G2 (OpenXR) | Mano de HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick: haga clic | |
| desencadenador | Desencadenador  | |
| sujeta | Sujeta | Puntear o comprimir el aire |
| primaryButton | [X/A]-presionar | Pulsar en el aire |
| secondaryButton | [Y/B]-Presione | |
| gripButton | Agarre: presionar | |
| triggerButton | Desencadenador: Presione | |
| menuButton | Menú | |

### <a name="aim-and-grip-poses"></a>Objetivos y planteamiento

Tiene acceso a dos conjuntos de planteamientos a través de las interacciones de entrada de OpenXR:

* El control tiene que presentar los objetos a mano
* El objetivo plantea la señal del mundo.

Puede encontrar más información sobre este diseño y las diferencias entre las dos supuestos en la [especificación de OpenXR: subtrazados de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Las supuestos suministradas por InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** y **DeviceAngularVelocity** representan la representación del **control** OpenXR. Los InputFeatureUsages relacionados con los planteamientos de agarre se definen en [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)de Unity.

Las supuestos suministradas por InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** y **PointerAngularVelocity** representan la representación de **objetivo** OpenXR. Estos InputFeatureUsages no se definen en ningún archivo de C# incluido, por lo que deberá definir su propia InputFeatureUsages como se indica a continuación:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Hápticos

Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el [manual de Unity para entrada-hápticos de Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="qr-codes"></a>Códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código. Puede encontrar más detalles en nuestra documentación de [seguimiento de código QR](../platform-capabilities-and-apis/qr-code-tracking.md) .  Al usar el complemento OpenXR, tome el [ `SpatialGraphNodeId` de la API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) y use la `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para buscar el código QR.

Como referencia, tenemos un [proyecto de ejemplo de seguimiento de QR en github](https://github.com/yl-msft/QRTracking) con más información detallada sobre el uso de la [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).

## <a name="whats-coming-soon"></a>Novedades próximamente

Los siguientes problemas y las características que faltan se conocen con la **versión 0.9.0** del complemento OpenXR de realidad mixta. Estamos trabajando en ellos y publicará correcciones y nuevas características en las próximas versiones.

* La compatibilidad con los **anclajes espaciales de Azure** está disponible en una versión futura.
* **ARM64** es la única plataforma admitida para las aplicaciones de HoloLens 2. La plataforma **ARM** está próximamente en una versión futura.

## <a name="troubleshooting"></a>Solución de problemas

Al suspender y reanudar una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista de HoloLens.

* Establezca el **modo de envío de profundidad** en **ninguno** en la configuración del proyecto OpenXR como solución alternativa.
