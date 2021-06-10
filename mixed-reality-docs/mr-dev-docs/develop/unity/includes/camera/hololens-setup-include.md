---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748511"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Siga este [tutorial paso a paso](../../tutorials/mr-learning-base-01.md) para agregar y configurar automáticamente Mixed Reality Toolkit en el proyecto de Unity. También es posible trabajar directamente con la clase [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establecer la escala de destino **en** **Mundo:**

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:

![Espacio de reproducción de MRTK](../../images/mrtk-playspace.png)

1. En el panel **Hierarchy** (Jerarquía), expanda **MixedRealityPlayspace** GameObject y busque el **objeto secundario Main Camera (Cámara** principal).
2. En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen de seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Después de obtener el subsistema, llame [a TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Puede usar [ARSession para](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) aplicaciones HoloLens, que funciona mejor con delimitadores y ARKit/ARCore.

![Sesión de AR en la jerarquía](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> La sesión de AR y las características relacionadas necesitan que AR Foundation esté instalado.

También es posible aplicar los cambios de cámara manualmente sin usar ARSession:

1. Seleccione **Cámara principal en** el panel **Jerarquía.**
1. En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

   ![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel Inspector de Unity*

1. Agregar **trackedPoseDriver** a la **cámara principal**

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Seleccione **Cámara principal en** el panel **Jerarquía.**
1. En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

   ![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel Inspector de Unity*

1. Vaya a **la sección Otras configuraciones** de la Configuración **del Reproductor de la Tienda Windows.**
1. Elija **Windows Mixed Reality** como dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
1. Seleccione **Virtual Reality Supported (Realidad virtual compatible)**

Dado que el objeto Cámara principal se etiqueta automáticamente como cámara, Unity potencia todo el movimiento y la traducción.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Camera, pero es posible que no tenga la configuración aplicada correctamente.