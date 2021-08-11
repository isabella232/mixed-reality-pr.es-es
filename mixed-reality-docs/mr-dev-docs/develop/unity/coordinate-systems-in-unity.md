---
title: Sistemas de coordenadas de Unity
description: Obtenga información sobre cómo crear experiencias de realidad mixta de nivel general, de pie, de sala y de realidad mixta a escala mundial en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escala asentada, escala de pie, escala de sala, escala mundial, 360 grados, sentado, de pie, sala, mundo, escala, posición, orientación, Unity, delimitador espacial, delimitador espacial, world-locked, world-locking, body-locked, body-locking, tracking loss, locatability, bounds, recenter, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 3372b9bd259202145fd658e225a36d2125f4a86d01eb90bc765b65918540db8b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203587"
---
# <a name="coordinate-systems-in-unity"></a>Sistemas de coordenadas de Unity

Windows Mixed Reality aplicaciones en una amplia gama de escalas de experiencia, desde aplicaciones de solo orientación y de escalado asentado hasta aplicaciones de escala de sala. Por HoloLens, puede ir más allá y crear aplicaciones a escala mundial que permiten a los usuarios recorrer más de 5 metros, explorando toda una planta de un edificio y más allá.

El primer paso para crear una experiencia de [](../../design/coordinate-systems.md) realidad mixta en Unity es comprender los sistemas de coordenadas y elegir la escala de experiencia a la que se dirigirá la aplicación.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creación de una experiencia de solo orientación o de escala asentada

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para crear una **experiencia de solo orientación** o de escala asentada, debe establecer Unity en el tipo de espacio de seguimiento estacionado.  El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar un seguimiento del [marco de referencia estacionada.](../../design/coordinate-systems.md#spatial-coordinate-systems) En el modo de seguimiento estacionado, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el reenvío es -Z) aparecerá delante del usuario cuando se inicie la aplicación.

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

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creación de una experiencia de escala permanente o de escala de habitación

**Espacio de nombres:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para obtener **una experiencia de escala** permanente o de escala de **habitación,** deberá colocar contenido en relación con la planta. Debe razonar sobre la planta del usuario mediante la fase espacial **[,](../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa el origen de nivel de planta definido del usuario y el límite opcional de la sala, configurados durante la primera ejecución.

Para asegurarse de que Unity funciona con su sistema de coordenadas universal en el nivel de planta, puede establecer y probar que Unity usa el tipo de espacio de seguimiento RoomScale:

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
* Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universales para realizar el seguimiento del marco [de fase de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems).
* Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de fase de referencia, probablemente porque el usuario no ha configurado una planta en su entorno. Aunque un valor devuelto falso no es común, puede ocurrir si la fase se configura en una sala diferente y el dispositivo se mueve a la sala actual sin que el usuario configure una nueva fase.

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento RoomScale, el contenido colocado en el plano y=0 aparecerá en el suelo. El origen en 0, 0, 0 será el lugar específico en la planta donde el usuario se encuentra durante la configuración de la sala, con -Z que representa la dirección hacia delante a la que se enfrentaban durante la instalación.

**Espacio de nombres:** *UnityEngine.Experimental.XR*<br>
**Tipo:** *Límite*

En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine.Experimental.XR.Boundary para obtener un polígono de límite, especificando un tipo de límite trackedArea. Si el usuario definió un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de escalado de sala al usuario, donde puede recorrer la escena que cree. 

> [!NOTE]
> El sistema representará automáticamente el límite cuando el usuario se acerque a él. La aplicación no necesita usar este polígono para representar el propio límite. Sin embargo, puede optar por establecer los objetos de escena mediante este polígono de límites, para asegurarse de que el usuario puede llegar físicamente a esos objetos sin teleportar:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia a escala mundial

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Para experiencias **de** escala mundial verdaderas en HoloLens que permiten a los usuarios recorrer más de 5 metros, necesitará nuevas técnicas más allá de las usadas para las experiencias de escala de habitación. Una técnica clave que usará es [](../../design/coordinate-systems.md#spatial-anchors) crear un delimitador espacial para bloquear un clúster de hologramas exactamente en su lugar en el mundo físico, independientemente de la distancia que haya recorrer el usuario y, a continuación, encontrar esos [hologramas](../../design/coordinate-systems.md#spatial-anchor-persistence)de nuevo en sesiones posteriores.

En Unity, se crea un delimitador espacial mediante la adición **del componente WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Adición de un delimitador de mundo

Para agregar un delimitador de mundo, llame a AddComponent () en el objeto de juego con la <WorldAnchor> transformación que desea anclar en el mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Eso es todo. Este objeto de juego ahora se anclará a su ubicación actual en el mundo físico; es posible que vea que sus coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar esa alineación física. Use [la persistencia](persistence-in-unity.md) para encontrar esta ubicación delimitada de nuevo en una sesión de aplicación futura.

### <a name="removing-a-world-anchor"></a>Eliminación de un delimitador de mundo

Si ya no quiere que gameObject se bloquee en una ubicación del mundo físico y no pretende moverlo a este marco, puede llamar a Destroy en el componente World Anchor.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si quieres mover el Objeto GameObject a este marco, debes llamar a DestroyImmediate en su lugar.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Mover un GameObject world anchored

Los objetos GameObject no se pueden mover mientras un world anchor está en él. Si necesita mover el Objeto GameObject a este marco, debe:
1. DestroyImmediate the World Anchor component
2. Mover el objeto GameObject
3. Agregue un nuevo componente World Anchor al GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Control de los cambios de locatability

Es posible que un WorldAnchor no sea localizable en el mundo físico en un momento dado. Si esto ocurre, Unity no actualizará la transformación del objeto delimitado. Esto también puede cambiar mientras se ejecuta una aplicación. Si no se controla el cambio en la capacidad de locabilidad, el objeto no aparecerá en la ubicación física correcta del mundo.

Para recibir notificaciones sobre los cambios de locatability:
1. Suscripción al evento OnTrackingChanged
2. Control del evento

Se **llamará al evento OnTrackingChanged** cada vez que el delimitador espacial subyacente cambie entre un estado de localizable y no localizable.

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

A veces, los delimitadores se encuentran inmediatamente. En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva . Como resultado, no se desencadenará el evento OnTrackingChanged. Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Uso compartido de anclajes entre dispositivos

Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear un anclaje de nube duradero a partir de un WorldAnchor local, que la aplicación puede encontrar a continuación en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a>

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">y buscar anclajes en Unity.</a>

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, se encuentra a punto de explorar Mixed Reality bloques de creación principales. Desde aquí, puede continuar con el siguiente bloque de compilación:

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
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Azure Spatial Anchors para Unity</a>