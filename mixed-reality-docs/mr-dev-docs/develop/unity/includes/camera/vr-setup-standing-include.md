---
ms.openlocfilehash: 61fe8754192c1fbd0634fd9d1e1994327599321b
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748461"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use la [clase MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca la escala de destino **en** **Room** o **Standing**:

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:

![Espacio de reproducción de MRTK](../../images/mrtk-playspace.png)

1. En el panel **Hierarchy** (Jerarquía), expanda **MixedRealityPlayspace** GameObject y busque el **objeto secundario Main Camera (Cámara** principal).
2. En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen de seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Después de obtener el subsistema, llame [a TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

Y trabaje con [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)de Unity.

![Plataforma XR en la jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. Vaya a **la sección Otras configuraciones** de la Configuración **del Reproductor de la Tienda Windows.**
2. Elija **Windows Mixed Reality** como dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.
3. Seleccione **Virtual Reality Supported (Realidad virtual compatible)**

Dado que el objeto Cámara principal se etiqueta automáticamente como cámara, Unity potencia todo el movimiento y la traducción.

>[!NOTE]
>Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.
>
>De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Cámara, pero no tiene la configuración siguiente aplicada correctamente.

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para una **experiencia de escala** de pie o de escala de **habitación,** deberá colocar contenido relativo al suelo. Para razonar sobre la planta del usuario, se usa la fase espacial **[,](../../../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa el origen de nivel de planta definido del usuario y el límite opcional de la sala, que se configura durante la primera ejecución.

Para asegurarse de que Unity funciona con su sistema de coordenadas mundial en el nivel de planta, puede establecer y probar que Unity usa el tipo de espacio de seguimiento RoomScale:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

* Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del marco [de fase de referencia](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de fase de referencia, probablemente porque el usuario no ha configurado una planta en su entorno. Aunque un valor devuelto falso no es común, puede ocurrir si la fase se configura en otra sala y el dispositivo se mueve a la sala actual sin que el usuario configure una nueva fase.

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento RoomScale, el contenido situado en el plano y=0 aparecerá en el suelo. El origen en 0, 0, 0 será el lugar específico en la planta donde el usuario se encuentra durante la instalación de la sala, con -Z que representa la dirección hacia delante a la que se enfrentaban durante la instalación.