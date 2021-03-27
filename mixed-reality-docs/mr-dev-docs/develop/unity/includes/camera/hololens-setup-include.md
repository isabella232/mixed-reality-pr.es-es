---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636319"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Siga este [Tutorial paso a paso](../../tutorials/mr-learning-base-01.md) para agregar y configurar automáticamente el kit de herramientas de realidad mixta en el proyecto de Unity. También es posible trabajar directamente con la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establecer la escala de **destino** en **mundo**:

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición de los Playspace y de la cámara automáticamente, pero es conveniente realizar una doble comprobación:

![MRTK playspace](../../images/mrtk-playspace.png)

1. En el panel **jerarquía** , expanda **MixedRealityPlayspace** GameObject y busque el objeto secundario **Camera principal** .
2. En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen del seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

Puede usar [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) para las aplicaciones de HoloLens, que funciona mejor con los delimitadores y ARKit/ARCore.

![Sesión de AR en jerarquía](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> La sesión AR y las características relacionadas necesitan AR Foundation instalado.

También es posible aplicar los cambios de la cámara manualmente sin usar ARSession:

1. Seleccionar **cámara principal** en el panel **jerarquía**
1. En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**

   ![Cámara en el panel del inspector en Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel del inspector en Unity*

1. Agregar un **TrackedPoseDriver** a la **cámara principal**

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Seleccionar **cámara principal** en el panel **jerarquía**
1. En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**

   ![Cámara en el panel del inspector en Unity](../../images/maincamera-350px.png)  
   *Cámara en el panel del inspector en Unity*

1. Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .
1. Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
1. Seleccionar **realidad virtual compatible**

Puesto que el objeto de cámara principal se etiqueta automáticamente como la cámara, Unity alimenta todo el movimiento y la traslación.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, al crear una nueva escena en Unity, contendrá una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero es posible que no tenga la configuración aplicada correctamente.