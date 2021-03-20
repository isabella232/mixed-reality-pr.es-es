---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719854"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="71fc6-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="71fc6-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="71fc6-102">El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity.</span><span class="sxs-lookup"><span data-stu-id="71fc6-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="71fc6-103">Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="71fc6-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="71fc6-104">Complemento de Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="71fc6-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="71fc6-105">El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity.</span><span class="sxs-lookup"><span data-stu-id="71fc6-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="71fc6-106">Para obtener información sobre los conceptos básicos de ARAnchors en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="71fc6-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="71fc6-107">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="71fc6-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="71fc6-108">Creación de una experiencia de escala mundial</span><span class="sxs-lookup"><span data-stu-id="71fc6-108">Building a world-scale experience</span></span>

<span data-ttu-id="71fc6-109">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="71fc6-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="71fc6-110">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="71fc6-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="71fc6-111">En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="71fc6-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="71fc6-112">Una técnica clave que se va a usar es crear un [delimitador espacial](../../../design/coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas precisamente en su lugar en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, [volver a buscar esos hologramas en sesiones posteriores](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="71fc6-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="71fc6-113">En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="71fc6-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="71fc6-114">Agregar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="71fc6-114">Adding a World Anchor</span></span>

<span data-ttu-id="71fc6-115">Para agregar un delimitador mundial, llame a `AddComponent<WorldAnchor>()` en el objeto de juego con la transformación que quiere delimitar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="71fc6-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="71fc6-116">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="71fc6-116">That's it!</span></span> <span data-ttu-id="71fc6-117">Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física.</span><span class="sxs-lookup"><span data-stu-id="71fc6-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="71fc6-118">Consulte [carga de un anclaje mundial](#loading-a-worldanchor) para volver a encontrar esta ubicación anclada en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="71fc6-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="71fc6-119">Quitar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="71fc6-119">Removing a World Anchor</span></span>

<span data-ttu-id="71fc6-120">Si ya no desea que el GameObject esté bloqueado en una ubicación física del mundo y no tiene intención de moverlo a este fotograma, puede llamar simplemente a Destroy en el componente del mundo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="71fc6-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="71fc6-121">Si desea trasladar GameObject este fotograma, debe llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="71fc6-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="71fc6-122">Mover un GameObject anclado mundial</span><span class="sxs-lookup"><span data-stu-id="71fc6-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="71fc6-123">No se puede cambiar GameObject mientras un delimitador internacional está en él.</span><span class="sxs-lookup"><span data-stu-id="71fc6-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="71fc6-124">Si necesita trasladar el GameObject de este marco, debe:</span><span class="sxs-lookup"><span data-stu-id="71fc6-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="71fc6-125">DestroyImmediate el componente de anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="71fc6-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="71fc6-126">Movimiento del GameObject</span><span class="sxs-lookup"><span data-stu-id="71fc6-126">Move the GameObject</span></span>
3. <span data-ttu-id="71fc6-127">Agregue un nuevo componente de anclaje mundial a GameObject.</span><span class="sxs-lookup"><span data-stu-id="71fc6-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="71fc6-128">Control de los cambios de ubicación</span><span class="sxs-lookup"><span data-stu-id="71fc6-128">Handling Locatability Changes</span></span>

<span data-ttu-id="71fc6-129">Es posible que WorldAnchor no se pueda localizar en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="71fc6-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="71fc6-130">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="71fc6-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="71fc6-131">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="71fc6-131">This also can change while an app is running.</span></span> <span data-ttu-id="71fc6-132">Si no se controla el cambio en la localización, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="71fc6-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="71fc6-133">Para recibir notificaciones sobre los cambios de Ubicación:</span><span class="sxs-lookup"><span data-stu-id="71fc6-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="71fc6-134">Suscribirse al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="71fc6-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="71fc6-135">Controlar el evento</span><span class="sxs-lookup"><span data-stu-id="71fc6-135">Handle the event</span></span>

<span data-ttu-id="71fc6-136">Se llamará al evento **OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado que se pueda localizar y que no se pueda localizar.</span><span class="sxs-lookup"><span data-stu-id="71fc6-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="71fc6-137">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="71fc6-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="71fc6-138">A veces, los delimitadores se colocan inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="71fc6-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="71fc6-139">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva.</span><span class="sxs-lookup"><span data-stu-id="71fc6-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="71fc6-140">Como resultado, el evento OnTrackingChanged no se desencadenará.</span><span class="sxs-lookup"><span data-stu-id="71fc6-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="71fc6-141">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="71fc6-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```