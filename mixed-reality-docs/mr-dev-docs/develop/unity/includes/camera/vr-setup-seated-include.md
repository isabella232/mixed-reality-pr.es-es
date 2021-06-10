---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748510"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use la [clase MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca **La** escala de destino **en Asentado:**

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:

![Espacio de juego de MRTK](../../images/mrtk-playspace.png)

1. En el panel **Jerarquía,** expanda **el objeto GameObject MixedRealityPlayspace** y busque el objeto secundario **Cámara** principal.
2. En el **panel Inspector,** busque el **componente Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen de seguimiento [en XRInputSubsystem.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html) Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

Y trabaje con [XRRig de](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.

![XR en jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Vaya a **la sección Otras configuraciones** de la Configuración **del Reproductor de la Tienda Windows.**
2. Elija **Windows Mixed Reality** dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
3. Seleccione **Virtual Reality Supported (Realidad virtual admitida)**

Dado que el objeto Cámara principal se etiqueta automáticamente como la cámara, Unity impulsa todo el movimiento y la traducción.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Camera, pero no tiene la configuración siguiente aplicada correctamente.

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para crear una **experiencia de solo orientación** o de escala asentada, debe establecer Unity en el tipo de espacio de seguimiento estacionado.  El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar un seguimiento del [marco de referencia estacionada.](../../../../design/coordinate-systems.md#spatial-coordinate-systems) En el modo de seguimiento estacionado, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el reenvío es -Z) aparecerá delante del usuario cuando se inicie la aplicación.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Para una **experiencia** pura de solo orientación, como un visor de vídeo de 360 grados (donde las actualizaciones de la cabeza posicional harían perder la esperanza), puede establecer [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:

```cs
InputTracking.disablePositionalTracking = true;
```

Para una **experiencia de escalado asentado**, para permitir que el usuario más adelante haga más reciente el origen asentado, puede llamar al [XR. Método InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)

```cs
InputTracking.Recenter();
```

Si va [a](../../../../design/coordinate-systems.md)crear una experiencia de escalado asentado, puede hacer más reciente el origen mundial de Unity en la posición de la cabeza actual del usuario mediante una llamada a **[la XR. Método InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**