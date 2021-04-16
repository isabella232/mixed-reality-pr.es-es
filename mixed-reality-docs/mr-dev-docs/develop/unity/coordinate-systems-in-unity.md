---
title: Sistemas de coordenadas de Unity
description: Obtenga información sobre cómo crear experiencias de realidad mixta de nivel general, de pie, de sala y de realidad mixta a escala mundial en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escala asentada, escala de pie, escala de sala, escala mundial, 360 grados, sentado, de pie, sala, mundo, escala, posición, orientación, Unity, delimitador espacial, delimitador espacial, world-locked, world-locking, body-locked, body-locking, tracking loss, locatability, bounds, recenter, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 91b1adf6dcf1c54d0d29a02bfb97ac4674a87c88
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528746"
---
# <a name="coordinate-systems-in-unity"></a><span data-ttu-id="3b973-104">Sistemas de coordenadas de Unity</span><span class="sxs-lookup"><span data-stu-id="3b973-104">Coordinate systems in Unity</span></span>

<span data-ttu-id="3b973-105">Windows Mixed Reality aplicaciones en una amplia gama de escalas de experiencia, desde aplicaciones de solo orientación y de escalado asentado hasta aplicaciones de escala de sala.</span><span class="sxs-lookup"><span data-stu-id="3b973-105">Windows Mixed Reality supports apps across a wide range of experience scales, from orientation-only and seated-scale apps up through room-scale apps.</span></span> <span data-ttu-id="3b973-106">En HoloLens, puede ir más allá y crear aplicaciones a escala mundial que permiten a los usuarios recorrer más de 5 metros, explorando toda una planta de un edificio y más allá.</span><span class="sxs-lookup"><span data-stu-id="3b973-106">On HoloLens, you can go further and build world-scale apps that let users walk beyond 5 meters, exploring an entire floor of a building and beyond.</span></span>

<span data-ttu-id="3b973-107">El primer paso para crear una experiencia de [](../../design/coordinate-systems.md) realidad mixta en Unity es comprender los sistemas de coordenadas y elegir la escala de experiencia a la que se dirigirá la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b973-107">Your first step in building a mixed reality experience in Unity is to understand [coordinate systems and choose the experience scale](../../design/coordinate-systems.md) your app will target.</span></span>

## <a name="building-an-orientation-only-or-seated-scale-experience"></a><span data-ttu-id="3b973-108">Creación de una experiencia de solo orientación o de escala asentada</span><span class="sxs-lookup"><span data-stu-id="3b973-108">Building an orientation-only or seated-scale experience</span></span>

<span data-ttu-id="3b973-109">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="3b973-109">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3b973-110">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="3b973-110">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3b973-111">Para crear una **experiencia de solo orientación** o de escala asentada, debe establecer Unity en el tipo de espacio de seguimiento estacionado. </span><span class="sxs-lookup"><span data-stu-id="3b973-111">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="3b973-112">El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar el seguimiento [del marco de referencia estacionada.](../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="3b973-112">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="3b973-113">En el modo de seguimiento estacionado, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el reenvío es -Z) aparecerá delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b973-113">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="3b973-114">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="3b973-114">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3b973-115">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="3b973-115">**Type:** *InputTracking*</span></span>

<span data-ttu-id="3b973-116">Para una **experiencia** pura de solo orientación, como un visor de vídeo de 360 grados (donde las actualizaciones de la cabeza posicional harían perder la esperanza), puede establecer [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="3b973-116">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="3b973-117">Para una **experiencia de escalado asentado**, para permitir que el usuario más adelante haga más reciente el origen asentado, puede llamar al [XR. Método InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)</span><span class="sxs-lookup"><span data-stu-id="3b973-117">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a><span data-ttu-id="3b973-118">Creación de una experiencia de escala permanente o de escala de habitación</span><span class="sxs-lookup"><span data-stu-id="3b973-118">Building a standing-scale or room-scale experience</span></span>

<span data-ttu-id="3b973-119">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="3b973-119">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="3b973-120">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="3b973-120">**Type:** *XRDevice*</span></span>

<span data-ttu-id="3b973-121">Para una **experiencia de escala** de pie o de escala de **habitación,** deberá colocar contenido relativo a la planta.</span><span class="sxs-lookup"><span data-stu-id="3b973-121">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="3b973-122">Para razonar sobre la planta del usuario, se usa la fase espacial **[,](../../design/coordinate-systems.md#spatial-coordinate-systems)** que representa el origen de nivel de planta definido del usuario y el límite opcional de la sala, que se configura durante la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="3b973-122">You reason about the user's floor using the **[spatial stage](../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="3b973-123">Para asegurarse de que Unity funciona con su sistema de coordenadas del mundo en el nivel de planta, puede establecer y probar que Unity usa el tipo de espacio de seguimiento RoomScale:</span><span class="sxs-lookup"><span data-stu-id="3b973-123">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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
* <span data-ttu-id="3b973-124">Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del marco [de fase de referencia](../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="3b973-124">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="3b973-125">Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de fase de referencia, probablemente porque el usuario no ha configurado una planta en su entorno.</span><span class="sxs-lookup"><span data-stu-id="3b973-125">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="3b973-126">Aunque un valor devuelto falso no es común, puede ocurrir si la fase se configura en otra sala y el dispositivo se mueve a la sala actual sin que el usuario configure una nueva fase.</span><span class="sxs-lookup"><span data-stu-id="3b973-126">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="3b973-127">Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento RoomScale, el contenido situado en el plano y=0 aparecerá en el suelo.</span><span class="sxs-lookup"><span data-stu-id="3b973-127">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="3b973-128">El origen en 0, 0, 0 será el lugar específico en la planta donde el usuario se encuentra durante la instalación de la sala, con -Z que representa la dirección hacia delante a la que se enfrentaban durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="3b973-128">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>

<span data-ttu-id="3b973-129">**Espacio de nombres:** *UnityEngine.Experimental.XR*</span><span class="sxs-lookup"><span data-stu-id="3b973-129">**Namespace:** *UnityEngine.Experimental.XR*</span></span><br>
<span data-ttu-id="3b973-130">**Tipo:** *Límite*</span><span class="sxs-lookup"><span data-stu-id="3b973-130">**Type:** *Boundary*</span></span>

<span data-ttu-id="3b973-131">En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine.Experimental.XR.Boundary para obtener un polígono de límites, especificando un tipo de límite TrackedArea.</span><span class="sxs-lookup"><span data-stu-id="3b973-131">In script code, you can then call the TryGetGeometry method on the UnityEngine.Experimental.XR.Boundary type to get a boundary polygon, specifying a boundary type of TrackedArea.</span></span> <span data-ttu-id="3b973-132">Si el usuario definió un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de escala de habitación al usuario, donde puede recorrer la escena que cree. </span><span class="sxs-lookup"><span data-stu-id="3b973-132">If the user defined a boundary (you get back a list of vertices), it's safe to deliver a **room-scale experience** to the user, where they can walk around the scene you create.</span></span>

> [!NOTE]
> <span data-ttu-id="3b973-133">El sistema representará automáticamente el límite cuando el usuario se acerque a él.</span><span class="sxs-lookup"><span data-stu-id="3b973-133">The system will automatically render the boundary when the user approaches it.</span></span> <span data-ttu-id="3b973-134">La aplicación no necesita usar este polígono para representar el propio límite.</span><span class="sxs-lookup"><span data-stu-id="3b973-134">Your app doesn't need to use this polygon to render the boundary itself.</span></span> <span data-ttu-id="3b973-135">Sin embargo, puede optar por establecer los objetos de escena mediante este polígono de límites, para asegurarse de que el usuario puede llegar físicamente a esos objetos sin teleportar:</span><span class="sxs-lookup"><span data-stu-id="3b973-135">However, you may choose to lay out your scene objects using this boundary polygon, to ensure the user can physically reach those objects without teleporting:</span></span>

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="3b973-136">Creación de una experiencia a escala mundial</span><span class="sxs-lookup"><span data-stu-id="3b973-136">Building a world-scale experience</span></span>

<span data-ttu-id="3b973-137">**Espacio de nombres:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="3b973-137">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="3b973-138">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="3b973-138">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="3b973-139">Para obtener **experiencias** verdaderas a escala mundial en HoloLens que permiten a los usuarios recorrer más de 5 metros, necesitará nuevas técnicas más allá de las usadas para las experiencias de escala de habitación.</span><span class="sxs-lookup"><span data-stu-id="3b973-139">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="3b973-140">Una técnica clave que usará es [](../../design/coordinate-systems.md#spatial-anchors) crear un delimitador espacial para bloquear un clúster de hologramas exactamente en su lugar en el mundo físico, independientemente de la distancia que haya recorrendo el usuario y, a continuación, encontrar esos [hologramas](../../design/coordinate-systems.md#spatial-anchor-persistence)de nuevo en sesiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="3b973-140">One key technique you'll use is to create a [spatial anchor](../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="3b973-141">En Unity, se crea un delimitador espacial mediante la adición **del componente WorldAnchor** Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="3b973-141">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="3b973-142">Adición de un delimitador de mundo</span><span class="sxs-lookup"><span data-stu-id="3b973-142">Adding a World Anchor</span></span>

<span data-ttu-id="3b973-143">Para agregar un delimitador de mundo, llame a AddComponent () en el objeto de juego con la <WorldAnchor> transformación que desea anclar en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="3b973-143">To add a world anchor, call AddComponent<WorldAnchor>() on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="3b973-144">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="3b973-144">That's it!</span></span> <span data-ttu-id="3b973-145">Este objeto de juego ahora se anclará a su ubicación actual en el mundo físico; es posible que vea que sus coordenadas del mundo de Unity se ajustan ligeramente con el tiempo para garantizar esa alineación física.</span><span class="sxs-lookup"><span data-stu-id="3b973-145">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="3b973-146">Use [la persistencia para](persistence-in-unity.md) encontrar esta ubicación delimitada de nuevo en una sesión de aplicación futura.</span><span class="sxs-lookup"><span data-stu-id="3b973-146">Use [persistence](persistence-in-unity.md) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="3b973-147">Eliminación de un delimitador de mundo</span><span class="sxs-lookup"><span data-stu-id="3b973-147">Removing a World Anchor</span></span>

<span data-ttu-id="3b973-148">Si ya no quieres que gameObject esté bloqueado en una ubicación física del mundo y no quieres moverlo a este marco, puedes llamar a Destroy en el componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="3b973-148">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="3b973-149">Si quieres mover el Objeto GameObject a este marco, debes llamar a DestroyImmediate en su lugar.</span><span class="sxs-lookup"><span data-stu-id="3b973-149">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="3b973-150">Mover un GameObject world anchored</span><span class="sxs-lookup"><span data-stu-id="3b973-150">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="3b973-151">Los objetos GameObject no se pueden mover mientras un world anchor está en él.</span><span class="sxs-lookup"><span data-stu-id="3b973-151">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="3b973-152">Si necesita mover el Objeto GameObject a este marco, debe:</span><span class="sxs-lookup"><span data-stu-id="3b973-152">If you need to move the GameObject this frame, you need to:</span></span>
1. <span data-ttu-id="3b973-153">DestroyImmediate the World Anchor component</span><span class="sxs-lookup"><span data-stu-id="3b973-153">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="3b973-154">Mover el objeto GameObject</span><span class="sxs-lookup"><span data-stu-id="3b973-154">Move the GameObject</span></span>
3. <span data-ttu-id="3b973-155">Agregue un nuevo componente World Anchor al GameObject.</span><span class="sxs-lookup"><span data-stu-id="3b973-155">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="3b973-156">Control de cambios de capacidad de uso</span><span class="sxs-lookup"><span data-stu-id="3b973-156">Handling Locatability Changes</span></span>

<span data-ttu-id="3b973-157">Un WorldAnchor puede no ser localizable en el mundo físico en un momento dado.</span><span class="sxs-lookup"><span data-stu-id="3b973-157">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="3b973-158">Si esto ocurre, Unity no actualizará la transformación del objeto delimitado.</span><span class="sxs-lookup"><span data-stu-id="3b973-158">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="3b973-159">Esto también puede cambiar mientras se ejecuta una aplicación.</span><span class="sxs-lookup"><span data-stu-id="3b973-159">This also can change while an app is running.</span></span> <span data-ttu-id="3b973-160">Si no se controla el cambio en la capacidad de proceso, el objeto no aparecerá en la ubicación física correcta del mundo.</span><span class="sxs-lookup"><span data-stu-id="3b973-160">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="3b973-161">Para recibir notificaciones sobre los cambios de locatability:</span><span class="sxs-lookup"><span data-stu-id="3b973-161">To be notified about locatability changes:</span></span>
1. <span data-ttu-id="3b973-162">Suscripción al evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="3b973-162">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="3b973-163">Control del evento</span><span class="sxs-lookup"><span data-stu-id="3b973-163">Handle the event</span></span>

<span data-ttu-id="3b973-164">Se **llamará al evento OnTrackingChanged** siempre que el delimitador espacial subyacente cambie entre un estado de localizable y no localizable.</span><span class="sxs-lookup"><span data-stu-id="3b973-164">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="3b973-165">A continuación, controle el evento:</span><span class="sxs-lookup"><span data-stu-id="3b973-165">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="3b973-166">A veces, los delimitadores se encuentran inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="3b973-166">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="3b973-167">En este caso, esta propiedad isLocated del delimitador se establecerá en true cuando addComponent <WorldAnchor> () devuelva .</span><span class="sxs-lookup"><span data-stu-id="3b973-167">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="3b973-168">Como resultado, no se desencadenará el evento OnTrackingChanged.</span><span class="sxs-lookup"><span data-stu-id="3b973-168">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="3b973-169">Un patrón limpio sería llamar al controlador OnTrackingChanged con el estado IsLocated inicial después de adjuntar un delimitador.</span><span class="sxs-lookup"><span data-stu-id="3b973-169">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a><span data-ttu-id="3b973-170">Uso compartido de delimitadores entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="3b973-170">Sharing anchors across devices</span></span>

<span data-ttu-id="3b973-171">Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear un anclaje de nube duradero a partir de un WorldAnchor local, que la aplicación puede localizar a continuación en varios dispositivos HoloLens, iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="3b973-171">Use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="3b973-172">Al compartir un delimitador espacial común entre varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="3b973-172">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="3b973-173">Esto permite compartir experiencias en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="3b973-173">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="3b973-174">Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a></span><span class="sxs-lookup"><span data-stu-id="3b973-174">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="3b973-175">Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear y buscar <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">delimitadores en Unity.</a></span><span class="sxs-lookup"><span data-stu-id="3b973-175">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3b973-176">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="3b973-176">Next Development Checkpoint</span></span>

<span data-ttu-id="3b973-177">Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, está en medio de la exploración de los Mixed Reality de creación principales.</span><span class="sxs-lookup"><span data-stu-id="3b973-177">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="3b973-178">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="3b973-178">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b973-179">Gaze</span><span class="sxs-lookup"><span data-stu-id="3b973-179">Gaze</span></span>](gaze-in-unity.md)

<span data-ttu-id="3b973-180">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="3b973-180">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b973-181">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="3b973-181">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="3b973-182">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="3b973-182">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b973-183">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3b973-183">See Also</span></span>
* [<span data-ttu-id="3b973-184">Escalas de experiencia</span><span class="sxs-lookup"><span data-stu-id="3b973-184">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="3b973-185">Fase espacial</span><span class="sxs-lookup"><span data-stu-id="3b973-185">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="3b973-186">Pérdida de seguimiento en Unity</span><span class="sxs-lookup"><span data-stu-id="3b973-186">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="3b973-187">Delimitadores espaciales</span><span class="sxs-lookup"><span data-stu-id="3b973-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="3b973-188">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="3b973-188">Persistence in Unity</span></span>](persistence-in-unity.md)
* [<span data-ttu-id="3b973-189">Experiencias compartidas en Unity</span><span class="sxs-lookup"><span data-stu-id="3b973-189">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
* <span data-ttu-id="3b973-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="3b973-190"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="3b973-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Azure Spatial Anchors para Unity</a></span><span class="sxs-lookup"><span data-stu-id="3b973-191"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>