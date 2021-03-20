---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719854"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity. Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento de Unity 2019/2020 + Windows XR](#tab/winxr)

El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity. Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia de escala mundial

**Espacio de nombres:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación. Una técnica clave que se va a usar es crear un [delimitador espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas precisamente en su lugar en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, [volver a buscar esos hologramas en sesiones posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).

En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.

### <a name="adding-a-world-anchor"></a>Agregar un delimitador mundial

Para agregar un delimitador mundial, llame a `AddComponent<WorldAnchor>()` en el objeto de juego con la transformación que quiere delimitar en el mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Eso es todo. Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física. Consulte [carga de un anclaje mundial](#loading-a-worldanchor) para volver a encontrar esta ubicación anclada en una sesión de aplicación futura.

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