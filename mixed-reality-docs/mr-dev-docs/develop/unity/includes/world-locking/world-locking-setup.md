---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528795"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="0da83-101">World Locking Tools (recomendado)</span><span class="sxs-lookup"><span data-stu-id="0da83-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="0da83-102">Se recomienda instalar World Locking Tools con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="0da83-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="0da83-103">Una vez que haya descargado Mixed Reality Feature Tool en el vínculo siguiente, seleccione la versión más reciente de **WLT Core** en la **sección World Locking Tools:**</span><span class="sxs-lookup"><span data-stu-id="0da83-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Mixed Reality ventana de selección de características de la herramienta de características con World Locking Tools seleccionado](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="0da83-105">Instalación de World Locking Tools con la herramienta de características de MR</span><span class="sxs-lookup"><span data-stu-id="0da83-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="0da83-106">Configuración automatizada</span><span class="sxs-lookup"><span data-stu-id="0da83-106">Automated setup</span></span>

<span data-ttu-id="0da83-107">Cuando el proyecto esté listo para comenzar, ejecute la utilidad de configuración de escena desde **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span><span class="sxs-lookup"><span data-stu-id="0da83-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Editor de Unity con Mixed Reality Toolkit seleccionado](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="0da83-109">La utilidad Configurar escena se puede volver a ejecutar en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="0da83-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="0da83-110">Por ejemplo, se debe volver a ejecutar si el destino de AR se ha cambiado de heredado a SDK de XR.</span><span class="sxs-lookup"><span data-stu-id="0da83-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="0da83-111">Si la escena ya está configurada correctamente, la ejecución de la utilidad no tiene ningún efecto.</span><span class="sxs-lookup"><span data-stu-id="0da83-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="0da83-112">Visualizadores</span><span class="sxs-lookup"><span data-stu-id="0da83-112">Visualizers</span></span>

<span data-ttu-id="0da83-113">Durante el desarrollo temprano, agregar visualizadores puede ser útil para asegurarse de que WLT está configurado y funcionando correctamente.</span><span class="sxs-lookup"><span data-stu-id="0da83-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="0da83-114">Se pueden quitar para el rendimiento de producción, o si por algún motivo ya no son necesarios, mediante la utilidad Quitar visualizadores.</span><span class="sxs-lookup"><span data-stu-id="0da83-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="0da83-115">Puede encontrar más detalles sobre los visualizadores en la [documentación de Herramientas](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span><span class="sxs-lookup"><span data-stu-id="0da83-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="0da83-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="0da83-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="0da83-117">El Mixed Reality complemento OpenXR proporciona funcionalidad básica de anclaje a través de una implementación de **ARAnchorManager arFoundation** de Unity.</span><span class="sxs-lookup"><span data-stu-id="0da83-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="0da83-118">Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el manual de [ARFoundation para AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="0da83-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="0da83-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="0da83-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="0da83-120">Creación de una experiencia a escala mundial</span><span class="sxs-lookup"><span data-stu-id="0da83-120">Building a world-scale experience</span></span>

<span data-ttu-id="0da83-121">**Espacio de nombres:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="0da83-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="0da83-122">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="0da83-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="0da83-123">Para las **verdaderas experiencias** a escala mundial en HoloLens que permiten a los usuarios recorrer más de 5 metros, necesitará nuevas técnicas más allá de las usadas para las experiencias de escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="0da83-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="0da83-124">Una técnica clave que usará es crear un delimitador espacial para bloquear un clúster de hologramas exactamente en su lugar en el mundo físico, independientemente de la distancia que haya pasado el usuario y, a continuación, vuelva [a](../../../../design/coordinate-systems.md#spatial-anchors) encontrar esos [hologramas](../../../../design/coordinate-systems.md#spatial-anchor-persistence)en sesiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="0da83-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="0da83-125">En Unity, se crea un delimitador espacial agregando el **componente WorldAnchor** Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="0da83-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="0da83-126">Adición de un delimitador de mundo</span><span class="sxs-lookup"><span data-stu-id="0da83-126">Adding a World Anchor</span></span>

<span data-ttu-id="0da83-127">Para agregar un delimitador de mundo, llame `AddComponent<WorldAnchor>()` a en el objeto de juego con la transformación que desea delimitar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="0da83-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="0da83-128">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="0da83-128">That's it!</span></span> <span data-ttu-id="0da83-129">Este objeto de juego ahora se delimitará a su ubicación actual en el mundo físico; es posible que vea que sus coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar esa alineación física.</span><span class="sxs-lookup"><span data-stu-id="0da83-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="0da83-130">Consulte carga de [un delimitador de mundo](#loading-a-worldanchor) para volver a encontrar esta ubicación anclada en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="0da83-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="0da83-131">Eliminación de un delimitador de mundo</span><span class="sxs-lookup"><span data-stu-id="0da83-131">Removing a World Anchor</span></span>

<span data-ttu-id="0da83-132">Si ya no quiere que GameObject se bloquee en una ubicación física del mundo y no pretende moverlo a este marco, puede llamar a Destroy en el componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="0da83-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="0da83-133">Si quiere mover el Objeto GameObject a este fotograma, debe llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="0da83-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="0da83-134">Mover un objeto GameObject world anchored</span><span class="sxs-lookup"><span data-stu-id="0da83-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="0da83-135">Los objetos GameObject no se pueden mover mientras un world anchor está en él.</span><span class="sxs-lookup"><span data-stu-id="0da83-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="0da83-136">Si necesita mover el Objeto GameObject a este marco, debe hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0da83-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="0da83-137">DestroyImmediate the World Anchor component (DestruirInmediate el componente World Anchor)</span><span class="sxs-lookup"><span data-stu-id="0da83-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="0da83-138">Mover el objeto GameObject</span><span class="sxs-lookup"><span data-stu-id="0da83-138">Move the GameObject</span></span>
3. <span data-ttu-id="0da83-139">Agregue un nuevo componente World Anchor al Objeto GameObject.</span><span class="sxs-lookup"><span data-stu-id="0da83-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="0da83-140">Control de cambios de capacidad de uso</span><span class="sxs-lookup"><span data-stu-id="0da83-140">Handling Locatability Changes</span></span>

<span data-ttu-id="0da83-141">Un WorldAnchor puede no ser localizable en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="0da83-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="0da83-142">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="0da83-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="0da83-143">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="0da83-143">This also can change while an app is running.</span></span> <span data-ttu-id="0da83-144">Si no se controla el cambio en la capacidad de locabilidad, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="0da83-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="0da83-145">Para recibir notificaciones sobre los cambios de locatability:</span><span class="sxs-lookup"><span data-stu-id="0da83-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="0da83-146">Suscripción al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="0da83-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="0da83-147">Control del evento</span><span class="sxs-lookup"><span data-stu-id="0da83-147">Handle the event</span></span>

<span data-ttu-id="0da83-148">Se **llamará al evento OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado de localizable y no localizable.</span><span class="sxs-lookup"><span data-stu-id="0da83-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="0da83-149">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="0da83-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="0da83-150">A veces, los delimitadores se encuentran inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="0da83-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="0da83-151">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva .</span><span class="sxs-lookup"><span data-stu-id="0da83-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="0da83-152">Como resultado, no se desencadenará el evento OnTrackingChanged.</span><span class="sxs-lookup"><span data-stu-id="0da83-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="0da83-153">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="0da83-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```