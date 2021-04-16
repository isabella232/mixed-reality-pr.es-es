---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528795"
---
# <a name="world-locking-tools-recommended"></a>[World Locking Tools (recomendado)](#tab/wlt)

Se recomienda instalar World Locking Tools con la nueva Mixed Reality Feature Tool. Una vez que haya descargado Mixed Reality Feature Tool en el vínculo siguiente, seleccione la versión más reciente de **WLT Core** en la **sección World Locking Tools:**

![Mixed Reality ventana de selección de características de la herramienta de características con World Locking Tools seleccionado](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [Instalación de World Locking Tools con la herramienta de características de MR](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a>Configuración automatizada

Cuando el proyecto esté listo para comenzar, ejecute la utilidad de configuración de escena desde **Mixed Reality Toolkit > Utilities > World Locking Tools**:

![Editor de Unity con Mixed Reality Toolkit seleccionado](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> La utilidad Configurar escena se puede volver a ejecutar en cualquier momento. Por ejemplo, se debe volver a ejecutar si el destino de AR se ha cambiado de heredado a SDK de XR. Si la escena ya está configurada correctamente, la ejecución de la utilidad no tiene ningún efecto.

### <a name="visualizers"></a>Visualizadores

Durante el desarrollo temprano, agregar visualizadores puede ser útil para asegurarse de que WLT está configurado y funcionando correctamente. Se pueden quitar para el rendimiento de producción, o si por algún motivo ya no son necesarios, mediante la utilidad Quitar visualizadores. Puede encontrar más detalles sobre los visualizadores en la [documentación de Herramientas](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).

# <a name="aranchormanager"></a>[ARAnchorManager](#tab/anchorstore)

El Mixed Reality complemento OpenXR proporciona funcionalidad básica de anclaje a través de una implementación de **ARAnchorManager arFoundation** de Unity. Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el manual de [ARFoundation para AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). 

# <a name="worldanchor"></a>[WorldAnchor](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia a escala mundial

**Espacio de nombres:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Para las **verdaderas experiencias** a escala mundial en HoloLens que permiten a los usuarios recorrer más de 5 metros, necesitará nuevas técnicas más allá de las usadas para las experiencias de escala de habitación. Una técnica clave que usará es crear un delimitador espacial para bloquear un clúster de hologramas exactamente en su lugar en el mundo físico, independientemente de la distancia que haya pasado el usuario y, a continuación, vuelva [a](../../../../design/coordinate-systems.md#spatial-anchors) encontrar esos [hologramas](../../../../design/coordinate-systems.md#spatial-anchor-persistence)en sesiones posteriores.

En Unity, se crea un delimitador espacial agregando el **componente WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Adición de un delimitador de mundo

Para agregar un delimitador de mundo, llame `AddComponent<WorldAnchor>()` a en el objeto de juego con la transformación que desea delimitar en el mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Eso es todo. Este objeto de juego ahora se delimitará a su ubicación actual en el mundo físico; es posible que vea que sus coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar esa alineación física. Consulte carga de [un delimitador de mundo](#loading-a-worldanchor) para volver a encontrar esta ubicación anclada en una sesión de aplicación futura.

### <a name="removing-a-world-anchor"></a>Eliminación de un delimitador de mundo

Si ya no quiere que GameObject se bloquee en una ubicación física del mundo y no pretende moverlo a este marco, puede llamar a Destroy en el componente World Anchor.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si quiere mover el Objeto GameObject a este fotograma, debe llamar a DestroyImmediate en su lugar.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Mover un objeto GameObject world anchored

Los objetos GameObject no se pueden mover mientras un world anchor está en él. Si necesita mover el Objeto GameObject a este marco, debe hacer lo siguiente:

1. DestroyImmediate the World Anchor component (DestruirInmediate el componente World Anchor)
2. Mover el objeto GameObject
3. Agregue un nuevo componente World Anchor al Objeto GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Control de cambios de capacidad de uso

Un WorldAnchor puede no ser localizable en el mundo físico en un momento dado. Si esto ocurre, Unity no actualizará la transformación del objeto delimitado. Esto también puede cambiar mientras se ejecuta una aplicación. Si no se controla el cambio en la capacidad de locabilidad, el objeto no aparecerá en la ubicación física correcta del mundo.

Para recibir notificaciones sobre los cambios de locatability:

1. Suscripción al evento OnTrackingChanged
2. Control del evento

Se **llamará al evento OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado de localizable y no localizable.

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