---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636387"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Use la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca la **escala de destino** en cualquier **habitación** o **posición**:

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

MRTK debe controlar la posición de los Playspace y de la cámara automáticamente, pero es conveniente realizar una doble comprobación:

![MRTK playspace](../../images/mrtk-playspace.png)

1. En el panel **jerarquía** , expanda **MixedRealityPlayspace** GameObject y busque el objeto secundario **Camera principal** .
2. En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Establezca el modo de origen del seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html). Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
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

En el caso de una experiencia de escalado **permanente** o de **escalado de habitación**, deberá colocar contenido en relación con el piso. Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución.

Para asegurarse de que Unity funcione con su sistema de coordenadas universal en el nivel inferior, puede establecer y probar que Unity usa el tipo de espacio de seguimiento de RoomScale:

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

* Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del [marco de fase de referencia](../../../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de la fase de referencia, probablemente porque el usuario no ha configurado un piso en su entorno. Aunque un valor devuelto falso no es habitual, puede suceder si la fase se configura en otro salón y el dispositivo se mueve a la habitación actual sin que el usuario configure una nueva fase.

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo. El origen en 0, 0, 0 será el lugar específico del piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección hacia delante hacia delante durante la instalación.