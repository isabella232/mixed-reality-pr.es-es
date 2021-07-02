---
title: Adición de interactividad cercana
description: Documentación sobre la interacción próxima en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, interacción cercana,
ms.openlocfilehash: 241425f0c158d684cad6dad8c88c8d692cbec42f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176868"
---
# <a name="how-to-add-near-interactivity"></a><span data-ttu-id="e4eb2-104">Adición de interactividad cercana</span><span class="sxs-lookup"><span data-stu-id="e4eb2-104">How to add near interactivity</span></span>

<span data-ttu-id="e4eb2-105">Las interacciones cercanas tienen la forma de toques y agarrar.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="e4eb2-106">Los eventos de entrada táctil y de captura se elevan como eventos de puntero mediante los objetos [Detepointer](pointers.md#pokepointer) [y SpherePointer,](pointers.md#spherepointer)respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="e4eb2-107">Se requieren tres pasos clave para escuchar eventos de entrada táctiles o de entrada en un GameObject determinado.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="e4eb2-108">Asegúrese de que el puntero correspondiente está registrado en el perfil [de configuración de MRTK principal.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="e4eb2-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="e4eb2-109">Asegúrese de que el Elemento GameObject deseado tiene el componente de script [táctil](#add-grab-interactions) [o](#add-touch-interactions) de toma adecuado y [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="e4eb2-110">Implemente una interfaz de controlador de entrada en un script adjunto al GameObject deseado para escuchar los [eventos de entrada](#grab-code-example) [táctil.](#touch-code-example)</span><span class="sxs-lookup"><span data-stu-id="e4eb2-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="e4eb2-111">Adición de interacciones de captura</span><span class="sxs-lookup"><span data-stu-id="e4eb2-111">Add grab interactions</span></span>

1. <span data-ttu-id="e4eb2-112">Asegúrese de [que spherepointer](pointers.md#spherepointer) está registrado en el perfil de *puntero MRTK*.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="e4eb2-113">El perfil de MRTK predeterminado y el HoloLens 2 predeterminado ya contienen *un spherepointer*.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="e4eb2-114">Para confirmar que se creará spherepointer, seleccione el perfil de configuración de MRTK y vaya a **Input**  >  **Pointers** Pointer Options (Opciones de puntero de puntero de  >  **entrada).**</span><span class="sxs-lookup"><span data-stu-id="e4eb2-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="e4eb2-115">El `GrabPointer` objeto prefab predeterminado (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  debe aparecer con un tipo de controlador *de mano articulada.*</span><span class="sxs-lookup"><span data-stu-id="e4eb2-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="e4eb2-116">Un objeto prefab personalizado se puede usar siempre que implemente la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) clase .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Ejemplo de perfil de puntero de captura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="e4eb2-118">El puntero de toma predeterminado consulta objetos cercanos en un cono alrededor del punto de toma para que coincida con la interfaz predeterminada de Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Puntero de toma cónica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="e4eb2-120">En el Elemento GameObject que se debe poder agarrar, agregue [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) un elemento , así como un colisionador.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="e4eb2-121">Asegúrese de que la capa de GameObject está en una capa que se puede agarrar.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="e4eb2-122">De forma predeterminada, se pueden capturar todas las *capas excepto Reconocimiento* espacial e Ignorar *raycasts.*</span><span class="sxs-lookup"><span data-stu-id="e4eb2-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="e4eb2-123">Vea qué capas se pueden agarrar inspeccionando las *máscaras* de capa de captura en el prefab *de GrabPointer.*</span><span class="sxs-lookup"><span data-stu-id="e4eb2-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="e4eb2-124">En GameObject o en uno de sus antecesores, agregue un componente de script que implemente la [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaz .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="e4eb2-125">Cualquier antecesor del objeto con [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) también podrá recibir eventos de puntero.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="e4eb2-126">Ejemplo de código de captura</span><span class="sxs-lookup"><span data-stu-id="e4eb2-126">Grab code example</span></span>

<span data-ttu-id="e4eb2-127">A continuación se muestra un script que se imprimirá si un evento es un toque o una toma.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="e4eb2-128">En la función de *interfaz IMixedRealityPointerHandler* pertinente, se puede ver el tipo de puntero que desencadena ese evento a través de [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="e4eb2-129">Si el puntero es *spherepointer,* la interacción es una toma.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a><span data-ttu-id="e4eb2-130">Adición de interacciones táctiles</span><span class="sxs-lookup"><span data-stu-id="e4eb2-130">Add touch interactions</span></span>

<span data-ttu-id="e4eb2-131">El proceso para agregar interacciones táctiles en elementos UnityUI es diferente al de gameObjects 3D de la vaina.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="e4eb2-132">Puede ir directamente a la sección siguiente, Interfaz de usuario *de Unity,* para habilitar los componentes de la interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="e4eb2-133">Sin **embargo,** para ambos tipos de elementos de la experiencia del usuario, asegúrese de que Se ha registrado [Un elemento Detener](pointers.md#pokepointer) en el perfil de puntero de *MRTK*.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="e4eb2-134">El perfil de MRTK predeterminado y el HoloLens 2 predeterminado ya contienen *un valor de Tipo Depointer*.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="e4eb2-135">Se puede confirmar que se creará un elemento PointerePointer seleccionando el perfil de configuración de MRTK y navegando a Input  >  **Pointers** Pointer Options (Opciones de puntero de puntero de  >  **entrada).**</span><span class="sxs-lookup"><span data-stu-id="e4eb2-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="e4eb2-136">El `PokePointer` objeto prefab predeterminado (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers)  debe aparecer con un tipo de controlador *de mano articulada.*</span><span class="sxs-lookup"><span data-stu-id="e4eb2-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="e4eb2-137">Un objeto prefab personalizado se puede usar siempre que implemente la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) clase .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Ejemplo de perfil de puntero de puntero de puntero de puntero de puntero](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="e4eb2-139">GameObjects 3D</span><span class="sxs-lookup"><span data-stu-id="e4eb2-139">3D GameObjects</span></span>

<span data-ttu-id="e4eb2-140">Hay dos maneras diferentes de agregar interacciones táctiles a objetos GameObject 3D, en función de si el objeto 3d solo debe tener un solo plano táctil, o de si debe ser táctil en función de todo su colisionador.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="e4eb2-141">La primera forma suele ser en objetos con BoxColliders, donde solo se desea que una sola cara del colisionador reaccione a eventos táctiles.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="e4eb2-142">El otro es para objetos que deben ser táctiles desde cualquier dirección en función de su colisionador.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="e4eb2-143">Toque facial único</span><span class="sxs-lookup"><span data-stu-id="e4eb2-143">Single face touch</span></span>

<span data-ttu-id="e4eb2-144">Esto es útil para habilitar situaciones en las que solo es necesario tocar una sola cara.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="e4eb2-145">Esta opción supone que el objeto de juego tiene boxcollider.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="e4eb2-146">es posible usar esto con objetos que no son BoxCollider, en cuyo caso las propiedades "Bounds" y "Local Center" se establecen de forma manual para configurar el plano táctil (es decir, los límites deben establecerse en un valor distinto de cero-cero).</span><span class="sxs-lookup"><span data-stu-id="e4eb2-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="e4eb2-147">En el Elemento GameObject que debe ser táctil, agregue boxcollider y [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="e4eb2-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="e4eb2-148">Establezca **Eventos en Recibir** en *Táctil* si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaz Input.IMixedRealityTouchHandler) en el siguiente script de componente.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="e4eb2-149">Haga clic **en Fix bounds (Corregir límites)** **y fix center (Centro de corrección).**</span><span class="sxs-lookup"><span data-stu-id="e4eb2-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Instalación de NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="e4eb2-151">En ese objeto o uno de sus antecesores, agregue un componente de script que implemente el [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="e4eb2-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="e4eb2-152">Interfaz.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-152">interface.</span></span> <span data-ttu-id="e4eb2-153">Cualquier antecesor del objeto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) también podrá recibir eventos de puntero.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="e4eb2-154">En la vista de escena del editor con *el elemento GameObject NearInteractionTouchable* seleccionado, observe un cuadrado de contorno blanco y una flecha.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="e4eb2-155">La flecha apunta a la "parte delantera" del control táctil.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="e4eb2-156">El colisionable solo será táctil desde esa dirección.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="e4eb2-157">Para que un colisionador sea táctil desde todas las direcciones, consulte la sección sobre la función táctil [de colisionador arbitrario](#arbitrary-collider-touch).</span><span class="sxs-lookup"><span data-stu-id="e4eb2-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="e4eb2-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="e4eb2-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="e4eb2-159">Toque de colisionador arbitrario</span><span class="sxs-lookup"><span data-stu-id="e4eb2-159">Arbitrary collider touch</span></span>

<span data-ttu-id="e4eb2-160">Esto es útil para habilitar situaciones en las que el objeto de juego debe ser táctil a lo largo de toda la cara del colisionador.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="e4eb2-161">Por ejemplo, esto se puede usar para habilitar interacciones táctiles para un objeto con spherecollider, donde todo el colisionador debe ser táctil.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="e4eb2-162">En el Elemento GameObject que debe ser táctil, agregue un colisionador y un [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="e4eb2-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="e4eb2-163">Establezca **Eventos en Recibir** en *Táctil* si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaz Input.IMixedRealityTouchHandler) en el siguiente script de componente.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="e4eb2-164">En ese objeto o uno de sus antecesores, agregue un componente de script que implemente el [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="e4eb2-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="e4eb2-165">Interfaz.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-165">interface.</span></span> <span data-ttu-id="e4eb2-166">Cualquier antecesor del objeto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) también podrá recibir eventos de puntero.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="e4eb2-167">Interfaz de usuario de Unity</span><span class="sxs-lookup"><span data-stu-id="e4eb2-167">Unity UI</span></span>

1. <span data-ttu-id="e4eb2-168">Agregue o asegúrese de que hay un [lienzo de UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) en la escena.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="e4eb2-169">En el Elemento GameObject que debe ser táctil, agregue un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="e4eb2-170">Establezca **Eventos en Recibir en** *Táctil* si usa la interfaz en el siguiente script [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) de componente.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="e4eb2-171">En ese objeto o uno de sus antecesores, agregue un componente de script que implemente la [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaz .</span><span class="sxs-lookup"><span data-stu-id="e4eb2-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="e4eb2-172">Cualquier antecesor del objeto con [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) también podrá recibir eventos de puntero.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4eb2-173">Es posible que los objetos no se comporten según lo previsto si se encuentran en objetos de lienzo superpuestos.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="e4eb2-174">Para garantizar un comportamiento coherente, nunca superponga los objetos de lienzo en la escena.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4eb2-175">En el `NearInteractionTouchable` componente de script, para la propiedad *Eventos que se van a recibir* hay dos opciones: *Puntero* y *Toque*.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="e4eb2-176">Establezca *Events (Eventos)* en Receive (Recibir) en *Pointer* (Puntero) si usa la interfaz y establezca en Touch si usa la interfaz del script de componente que [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) responde o controla los eventos de  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) entrada.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="e4eb2-177">Ejemplo de código táctil</span><span class="sxs-lookup"><span data-stu-id="e4eb2-177">Touch code example</span></span>

<span data-ttu-id="e4eb2-178">El código siguiente muestra un MonoBehaviour que se puede adjuntar a un Elemento GameObject con un componente variant y responder a eventos [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) de entrada táctiles.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a><span data-ttu-id="e4eb2-179">Ejemplos de scripts de interacción cercanos</span><span class="sxs-lookup"><span data-stu-id="e4eb2-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="e4eb2-180">Eventos de función táctil</span><span class="sxs-lookup"><span data-stu-id="e4eb2-180">Touch events</span></span>

<span data-ttu-id="e4eb2-181">En este ejemplo se crea un cubo, se puede tocar y se cambia el color al tocar.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a><span data-ttu-id="e4eb2-182">Eventos de captura</span><span class="sxs-lookup"><span data-stu-id="e4eb2-182">Grab events</span></span>

<span data-ttu-id="e4eb2-183">En el ejemplo siguiente se muestra cómo hacer que un Elemento GameObject se puede arrastrar.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="e4eb2-184">Supone que el objeto de juego tiene un colisionador.</span><span class="sxs-lookup"><span data-stu-id="e4eb2-184">Assumes that the game object has a collider on it.</span></span>

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a><span data-ttu-id="e4eb2-185">API útiles</span><span class="sxs-lookup"><span data-stu-id="e4eb2-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="e4eb2-186">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e4eb2-186">See also</span></span>

* [<span data-ttu-id="e4eb2-187">Información general sobre acciones del usuario</span><span class="sxs-lookup"><span data-stu-id="e4eb2-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="e4eb2-188">Punteros</span><span class="sxs-lookup"><span data-stu-id="e4eb2-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="e4eb2-189">Eventos de entrada</span><span class="sxs-lookup"><span data-stu-id="e4eb2-189">Input Events</span></span>](input-events.md)
