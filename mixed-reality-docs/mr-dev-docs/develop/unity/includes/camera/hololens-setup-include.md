---
ms.openlocfilehash: 78596197af6c2e7c329e7a7c99281f8debee13b973a212709f5be1ec34e04eea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212334"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Siga este [tutorial paso a paso para](../../tutorials/mr-learning-base-01.md) agregar y configurar automáticamente Mixed Reality Toolkit en el proyecto de Unity. También es posible trabajar directamente con la clase [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establecer la escala de destino **en** **Mundo:**

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:

![Espacio de juego de MRTK](../../images/mrtk-playspace.png)

1. En el panel **Jerarquía,** expanda **el objeto GameObject MixedRealityPlayspace** y busque el objeto secundario **Cámara** principal.
2. En el **panel Inspector,** busque el **componente Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen de seguimiento [en XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Puede usar [ARSession para](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) HoloLens aplicaciones, lo que funciona mejor con delimitadores y ARKit/ARCore.

![Sesión de AR en la jerarquía](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> La sesión de AR y las características relacionadas necesitan la instalación de AR Foundation.

También es posible aplicar los cambios de cámara manualmente sin usar ARSession:

1. Seleccione **Cámara principal** en el panel **Jerarquía.**
1. En el **panel Inspector,** busque el **componente Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

   ![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel Inspector de Unity*

1. Adición **de trackedPoseDriver** a la **cámara principal**

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Seleccione **Cámara principal** en el panel **Jerarquía.**
1. En el **panel Inspector,** busque el **componente Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

   ![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel Inspector de Unity*

1. Vaya a **la sección Otros Configuración** del reproductor de Windows Store **Configuración**
1. Elija **Windows Mixed Reality** dispositivo, que puede aparecer como Windows **Holographic** en versiones anteriores de Unity.
1. Seleccione **Virtual Reality Supported (Realidad virtual admitida)**

Dado que el objeto Cámara principal se etiqueta automáticamente como la cámara, Unity impulsa todo el movimiento y la traducción.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Camera, pero es posible que no se aplique correctamente la configuración.