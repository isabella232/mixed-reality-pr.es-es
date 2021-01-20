---
title: Sistemas de coordenadas de Unity
description: Aprenda a crear experiencias colocadas, permanentes, de escala de sala y de realidad mixta de gran escala en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escalado colocado, escalado permanente, escalado de sala, de escala mundial, 360 Degree, sentada, permanente, habitación, mundo, escala, posición, orientación, Unity, delimitador, anclaje espacial, delimitador mundial, límite mundial, bloqueo mundial, bloqueo de la realidad mixta, bloqueo del cuerpo de la realidad, pérdida de seguimiento, uso de la realidad
ms.openlocfilehash: aa68ae44e09dfe579f8ab8924d1b300506a1f00e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581060"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="b3671-104">Sistemas de coordenadas de Unity</span><span class="sxs-lookup"><span data-stu-id="b3671-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="b3671-105">Windows Mixed Reality es compatible con aplicaciones a través de una amplia gama de [escalas](../../design/coordinate-systems.md), desde aplicaciones de solo orientación y de escalado sentado hasta las aplicaciones a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="b3671-105">Windows Mixed Reality supports apps across a wide range of [experience scales](../../design/coordinate-systems.md), from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="b3671-106">En HoloLens, puede ir más allá y compilar aplicaciones a gran escala que permitan a los usuarios recorrer más de 5 metros, explorando todo el piso de un edificio y más allá.</span><span class="sxs-lookup"><span data-stu-id="b3671-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="b3671-107">El primer paso para crear una experiencia de realidad mixta en Unity es determinar la [escala de experiencia](../../design/coordinate-systems.md) de destino de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b3671-107">Your first step in building a mixed reality experience in Unity is to determine which [experience scale](../../design/coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="b3671-108">Creación de una experiencia de solo orientación o de escalado</span><span class="sxs-lookup"><span data-stu-id="b3671-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="b3671-109">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b3671-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b3671-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b3671-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b3671-111">Para compilar una experiencia de **solo orientación** o **de escalado original**, debe establecer Unity en el tipo de espacio de seguimiento de la estación.</span><span class="sxs-lookup"><span data-stu-id="b3671-111">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="b3671-112">El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="b3671-112">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="b3671-113">En el modo de seguimiento estacionario, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparecerá delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b3671-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="b3671-114">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b3671-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b3671-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="b3671-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="b3671-116">En el caso de una **experiencia pura de solo orientación** , como un visor de vídeo de 360 grados (donde las actualizaciones de los cabezales posicionales estropearían la ilusión), puede establecer [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="b3671-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="b3671-117">En el caso de una **experiencia de escalado** inactiva, para permitir que el usuario recentre posteriormente el origen de la caja, puede llamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="b3671-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="b3671-118">Creación de una experiencia de escalado permanente o a escala de habitación</span><span class="sxs-lookup"><span data-stu-id="b3671-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="b3671-119">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="b3671-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="b3671-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="b3671-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="b3671-121">En el caso de una experiencia de escalado **permanente** o de **escalado de habitación**, deberá colocar contenido en relación con el piso.</span><span class="sxs-lookup"><span data-stu-id="b3671-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="b3671-122">Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="b3671-122">You reason about the user's floor using the **[spatial stage](../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="b3671-123">Para asegurarse de que Unity funcione con su sistema de coordenadas universal en el nivel inferior, puede establecer y probar que Unity usa el tipo de espacio de seguimiento de RoomScale:</span><span class="sxs-lookup"><span data-stu-id="b3671-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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
* <span data-ttu-id="b3671-124">Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del [marco de fase de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="b3671-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="b3671-125">Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de la fase de referencia, probablemente porque el usuario no ha configurado un piso en su entorno.</span><span class="sxs-lookup"><span data-stu-id="b3671-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="b3671-126">Aunque un valor devuelto falso no es habitual, puede suceder si la fase se configura en otro salón y el dispositivo se mueve a la habitación actual sin que el usuario configure una nueva fase.</span><span class="sxs-lookup"><span data-stu-id="b3671-126">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="b3671-127">Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo.</span><span class="sxs-lookup"><span data-stu-id="b3671-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="b3671-128">El origen en 0, 0, 0 será el lugar específico del piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección hacia delante hacia delante durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="b3671-128">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="b3671-129">**Espacio de nombres:** *UnityEngine. experimental. XR*</span><span class="sxs-lookup"><span data-stu-id="b3671-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="b3671-130">**Tipo:** *límite*</span><span class="sxs-lookup"><span data-stu-id="b3671-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="b3671-131">En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine. experimental. XR. Boundary para obtener un polígono de límite, especificando un tipo de límite de TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="b3671-131">In script code, you can then call the TryGetGeometry method on the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="b3671-132">Si el usuario definía un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de **escalado** a la habitación al usuario, donde puede recorrer la escena que cree.</span><span class="sxs-lookup"><span data-stu-id="b3671-132">If the user defined a boundary (you get back a list of vertices), it's safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

> [!NOTE]
> <span data-ttu-id="b3671-133">El sistema representará automáticamente el límite cuando el usuario lo aproxime.</span><span class="sxs-lookup"><span data-stu-id="b3671-133">The system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="b3671-134">No es necesario que la aplicación use este polígono para representar el límite.</span><span class="sxs-lookup"><span data-stu-id="b3671-134">Your app doesn't need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="b3671-135">Sin embargo, puede elegir diseñar los objetos de la escena con este polígono de límite para asegurarse de que el usuario pueda llegar físicamente a esos objetos sin teletransportar:</span><span class="sxs-lookup"><span data-stu-id="b3671-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="b3671-136">Creación de una experiencia de escala mundial</span><span class="sxs-lookup"><span data-stu-id="b3671-136">Building a world-scale experience</span></span>

<span data-ttu-id="b3671-137">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="b3671-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="b3671-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="b3671-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="b3671-139">En el caso de **experiencias** reales en HoloLens que permitan a los usuarios ir más allá de 5 metros, necesitará nuevas técnicas más allá de las que se usan para experiencias a escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="b3671-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="b3671-140">Una técnica clave que se va a usar es crear un [delimitador espacial](../../design/coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas precisamente en su lugar en el mundo físico, con independencia de cuánto se haya desplazado el usuario y, a continuación, [volver a buscar esos hologramas en sesiones posteriores](../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="b3671-140">One key technique you'll use is to create a [spatial anchor](../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="b3671-141">En Unity, puede crear un delimitador espacial agregando el componente Unity de **WorldAnchor** a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="b3671-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="b3671-142">Agregar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="b3671-142">Adding a World Anchor</span></span>

<span data-ttu-id="b3671-143">Para agregar un delimitador mundial, llame a AddComponent <WorldAnchor> () en el objeto de juego con la transformación que quiere delimitar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="b3671-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="b3671-144">Ya está.</span><span class="sxs-lookup"><span data-stu-id="b3671-144">That's it!</span></span> <span data-ttu-id="b3671-145">Este objeto de juego se anclará ahora a su ubicación actual en el mundo físico; puede ver que las coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar la alineación física.</span><span class="sxs-lookup"><span data-stu-id="b3671-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="b3671-146">Use la [persistencia](persistence-in-unity.md) para volver a buscar esta ubicación anclada en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="b3671-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="b3671-147">Quitar un delimitador mundial</span><span class="sxs-lookup"><span data-stu-id="b3671-147">Removing a World Anchor</span></span>

<span data-ttu-id="b3671-148">Si ya no desea que el GameObject esté bloqueado en una ubicación física del mundo y no tiene intención de moverlo a este fotograma, puede llamar simplemente a Destroy en el componente del mundo de delimitador.</span><span class="sxs-lookup"><span data-stu-id="b3671-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="b3671-149">Si desea trasladar GameObject este fotograma, debe llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="b3671-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="b3671-150">Mover un GameObject anclado mundial</span><span class="sxs-lookup"><span data-stu-id="b3671-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="b3671-151">No se puede cambiar GameObject mientras un delimitador internacional está en él.</span><span class="sxs-lookup"><span data-stu-id="b3671-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="b3671-152">Si necesita trasladar el GameObject de este marco, debe:</span><span class="sxs-lookup"><span data-stu-id="b3671-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="b3671-153">DestroyImmediate el componente de anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="b3671-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="b3671-154">Movimiento del GameObject</span><span class="sxs-lookup"><span data-stu-id="b3671-154">Move the GameObject</span></span>
3. <span data-ttu-id="b3671-155">Agregue un nuevo componente de anclaje mundial a GameObject.</span><span class="sxs-lookup"><span data-stu-id="b3671-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="b3671-156">Control de los cambios de ubicación</span><span class="sxs-lookup"><span data-stu-id="b3671-156">Handling Locatability Changes</span></span>

<span data-ttu-id="b3671-157">Es posible que WorldAnchor no se pueda localizar en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="b3671-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="b3671-158">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="b3671-158">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="b3671-159">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="b3671-159">This also can change while an app is running.</span></span> <span data-ttu-id="b3671-160">Si no se controla el cambio en la localización, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="b3671-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="b3671-161">Para recibir notificaciones sobre los cambios de Ubicación:</span><span class="sxs-lookup"><span data-stu-id="b3671-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="b3671-162">Suscribirse al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="b3671-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="b3671-163">Controlar el evento</span><span class="sxs-lookup"><span data-stu-id="b3671-163">Handle the event</span></span>

<span data-ttu-id="b3671-164">Se llamará al evento **OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado que se pueda localizar y que no se pueda localizar.</span><span class="sxs-lookup"><span data-stu-id="b3671-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="b3671-165">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="b3671-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="b3671-166">A veces, los delimitadores se colocan inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="b3671-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="b3671-167">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando AddComponent <WorldAnchor> () devuelva.</span><span class="sxs-lookup"><span data-stu-id="b3671-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="b3671-168">Como resultado, el evento OnTrackingChanged no se desencadenará.</span><span class="sxs-lookup"><span data-stu-id="b3671-168">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="b3671-169">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="b3671-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="b3671-170">Compartir delimitadores entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="b3671-170">Sharing anchors across devices</span></span>

<span data-ttu-id="b3671-171">Use los <a href="/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede encontrar en varios dispositivos de HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="b3671-171">Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="b3671-172">Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="b3671-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="b3671-173">Esto permite compartir experiencias en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="b3671-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="b3671-174">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="b3671-174">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="b3671-175">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="b3671-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b3671-176">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="b3671-176">Next Development Checkpoint</span></span>

<span data-ttu-id="b3671-177">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b3671-177">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="b3671-178">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="b3671-178">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3671-179">Gaze</span><span class="sxs-lookup"><span data-stu-id="b3671-179">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="b3671-180">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="b3671-180">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b3671-181">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="b3671-181">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b3671-182">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="b3671-182">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3671-183">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b3671-183">See Also</span></span>
* [<span data-ttu-id="b3671-184">Escalas de experiencia</span><span class="sxs-lookup"><span data-stu-id="b3671-184">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="b3671-185">Fase espacial</span><span class="sxs-lookup"><span data-stu-id="b3671-185">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="b3671-186">Pérdida de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="b3671-186">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="b3671-187">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="b3671-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="b3671-188">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="b3671-188">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="b3671-189">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="b3671-189">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="b3671-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="b3671-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="b3671-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="b3671-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>