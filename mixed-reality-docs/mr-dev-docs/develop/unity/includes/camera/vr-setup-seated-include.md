---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636376"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca la **escala de destino** en **encajada**:

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
```

Y trabaje con [XRRigs](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)de Unity.

![Plataforma de pruebas de XR en jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .
2. Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
3. Seleccionar **realidad virtual compatible**

Puesto que el objeto de cámara principal se etiqueta automáticamente como la cámara, Unity alimenta todo el movimiento y la traslación.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, cuando se crea una nueva escena en Unity, contiene una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero no tiene la configuración que se aplica correctamente.

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para compilar una experiencia de **solo orientación** o **de escalado original**, debe establecer Unity en el tipo de espacio de seguimiento de la estación. El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](../../../../design/coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento estacionario, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparecerá delante del usuario cuando se inicie la aplicación.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *InputTracking*

En el caso de una **experiencia pura de solo orientación** , como un visor de vídeo de 360 grados (donde las actualizaciones de los cabezales posicionales estropearían la ilusión), puede establecer [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:

```cs
InputTracking.disablePositionalTracking = true;
```

En el caso de una **experiencia de escalado** inactiva, para permitir que el usuario recentre posteriormente el origen de la caja, puede llamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :

```cs
InputTracking.Recenter();
```

Si va a crear una [experiencia de escalado original](../../../../design/coordinate-systems.md), puede volver a centrar el origen mundial de Unity en la posición principal del usuario mediante una llamada a **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .