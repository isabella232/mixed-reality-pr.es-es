---
title: Sistemas de coordenadas de Unity
description: Aprenda a crear experiencias colocadas, permanentes, de escala de sala y de realidad mixta de gran escala en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escalado colocado, escalado permanente, escalado de sala, de escala mundial, 360 Degree, sentada, permanente, habitación, mundo, escala, posición, orientación, Unity, delimitador, anclaje espacial, delimitador mundial, límite mundial, bloqueo mundial, bloqueo de la realidad mixta, bloqueo del cuerpo de la realidad, pérdida de seguimiento, uso de la realidad
ms.openlocfilehash: 900c393bf9ab09f1ac49e3108488d081f8025c19
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010286"
---
# <a name="coordinate-systems-in-unity"></a>Sistemas de coordenadas de Unity

Windows Mixed Reality es compatible con aplicaciones a través de una amplia gama de [escalas](../../design/coordinate-systems.md), desde aplicaciones de solo orientación y de escalado sentado hasta las aplicaciones a escala de habitación. En HoloLens, puede ir más allá y compilar aplicaciones a gran escala que permitan a los usuarios recorrer más de 5 metros, explorando todo el piso de un edificio y más allá.

El primer paso para crear una experiencia de realidad mixta en Unity es determinar la [escala de experiencia](../../design/coordinate-systems.md) de destino de la aplicación.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creación de una experiencia de solo orientación o de escalado

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Para compilar una experiencia de **solo orientación** o **de escalado original**, debe establecer Unity en el tipo de espacio de seguimiento de la estación. El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento estacionario, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparecerá delante del usuario cuando se inicie la aplicación.

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

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creación de una experiencia de escalado permanente o a escala de habitación

**Espacio de nombres:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

En el caso de una experiencia de escalado **permanente** o de **escalado de habitación**, deberá colocar contenido en relación con el piso. Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución.

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
* Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del [marco de fase de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de la fase de referencia, probablemente porque el usuario no ha configurado un piso en su entorno. Aunque un valor devuelto falso no es habitual, puede suceder si la fase se configura en otro salón y el dispositivo se mueve a la habitación actual sin que el usuario configure una nueva fase.

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo. El origen en 0, 0, 0 será el lugar específico del piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección hacia delante hacia delante durante la instalación.

**Espacio de nombres:** *UnityEngine. experimental. XR*<br>
**Tipo:** *límite*

En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine. experimental. XR. Boundary para obtener un polígono de límite, especificando un tipo de límite de TrackedArea. Si el usuario definía un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de **escalado** a la habitación al usuario, donde puede recorrer la escena que cree.

> [!NOTE]
> El sistema representará automáticamente el límite cuando el usuario lo aproxime. No es necesario que la aplicación use este polígono para representar el límite. Sin embargo, puede elegir diseñar los objetos de la escena con este polígono de límite para asegurarse de que el usuario pueda llegar físicamente a esos objetos sin teletransportar:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia de escala mundial

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación. Una técnica clave que se va a usar es crear un [delimitador espacial](../../design/coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas precisamente en su lugar en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, [volver a buscar esos hologramas en sesiones posteriores](../../design/coordinate-systems.md#spatial-anchor-persistence).

En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.

### <a name="adding-a-world-anchor"></a>Agregar un delimitador mundial

Para agregar un delimitador mundial, llame a AddComponent <WorldAnchor> () en el objeto de juego con la transformación que quiere delimitar en el mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Eso es todo. Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física. Use la [persistencia](persistence-in-unity.md) para volver a buscar esta ubicación anclada en una sesión de aplicación futura.

### <a name="removing-a-world-anchor"></a>Quitar un delimitador mundial

Si ya no desea que el GameObject esté bloqueado en una ubicación física del mundo y no tiene intención de moverlo a este fotograma, puede llamar simplemente a Destroy en el componente del mundo de delimitador.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si desea trasladar GameObject este fotograma, debe llamar a DestroyImmediate en su lugar.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Mover un GameObject anclado mundial

No se puede cambiar GameObject mientras un delimitador internacional está en él. Si necesita trasladar el GameObject de este marco, debe:
1. DestroyImmediate el componente de anclaje mundial
2. Movimiento del GameObject
3. Agregue un nuevo componente de anclaje mundial a GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Control de los cambios de ubicación

Es posible que WorldAnchor no se pueda localizar en el mundo físico en un momento dado. Si esto ocurre, Unity no actualizará la transformación del objeto delimitado. Esto también puede cambiar mientras se ejecuta una aplicación. Si no se controla el cambio en la localización, el objeto no aparecerá en la ubicación física correcta del mundo.

Para recibir notificaciones sobre los cambios de Ubicación:
1. Suscribirse al evento OnTrackingChanged
2. Controlar el evento

Se llamará al evento **OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado que se pueda localizar y que no se pueda localizar.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

A continuación, controle el evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

A veces, los delimitadores se colocan inmediatamente. En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva. Como resultado, el evento OnTrackingChanged no se desencadenará. Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Compartir delimitadores entre dispositivos

Use los <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede encontrar en varios dispositivos de HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta. Desde aquí, puede continuar con el siguiente bloque de creación:

> [!div class="nextstepaction"]
> [Gaze](gaze-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Escalas de experiencia](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [Fase espacial](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Pérdida de seguimiento en Unity](tracking-loss-in-unity.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Persistencia en Unity](persistence-in-unity.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a>
