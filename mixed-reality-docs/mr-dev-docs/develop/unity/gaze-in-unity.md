---
title: Mirada en Unity
description: Fijamente es una forma principal de que los usuarios tengan como destino los hologramas que crea la aplicación en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: miras hacia abajo, a la punta, por la cabeza, el holograma, la realidad mixta, el casco de realidad mixta, el casco de realidad mixta de Windows, el casco de realidad virtual, MRTK, el kit de herramientas de realidad mixta
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010366"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="18baf-104">Encabezado de la mirada en Unity</span><span class="sxs-lookup"><span data-stu-id="18baf-104">Head-gaze in Unity</span></span>

<span data-ttu-id="18baf-105">[Miramos](../../design/gaze-and-commit.md) el método principal para que los usuarios tengan como destino los [hologramas](../../discover/hologram.md) que crea la aplicación en [realidad mixta](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="18baf-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="18baf-106">Implementación del encabezado de mira</span><span class="sxs-lookup"><span data-stu-id="18baf-106">Implementing head-gaze</span></span>

<span data-ttu-id="18baf-107">Conceptualmente, para determinar el [encabezado](../../design/gaze-and-commit.md) , puede proyectar un rayo hacia delante desde los auriculares del usuario para ver lo que llega.</span><span class="sxs-lookup"><span data-stu-id="18baf-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="18baf-108">En Unity, la posición y la dirección principales del usuario se exponen a través de la [cámara](camera-in-unity.md), concretamente [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine. Camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="18baf-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="18baf-109">La llamada a [física. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) le proporciona un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto de colisión 3D y el otro GameObject el toque del rayo de la punta.</span><span class="sxs-lookup"><span data-stu-id="18baf-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="18baf-110">Ejemplo: implementación de la cabeza de mira</span><span class="sxs-lookup"><span data-stu-id="18baf-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="18baf-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="18baf-111">Best practices</span></span>

<span data-ttu-id="18baf-112">Aunque en el ejemplo anterior se activa un solo Raycast desde el bucle de actualización para buscar el destino al que apunta el encabezado del usuario, se recomienda usar un solo objeto para administrar todos los procesos de mirados.</span><span class="sxs-lookup"><span data-stu-id="18baf-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="18baf-113">La combinación de la lógica de mirada le ahorrará la potencia de procesamiento de la aplicación y limitará la raycasting a una por fotograma.</span><span class="sxs-lookup"><span data-stu-id="18baf-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="18baf-114">Visualización del encabezado</span><span class="sxs-lookup"><span data-stu-id="18baf-114">Visualizing head-gaze</span></span>

<span data-ttu-id="18baf-115">Al igual que con un puntero del mouse en un equipo, debe implementar un [cursor](../../design/cursors.md) que represente el encabezado del usuario.</span><span class="sxs-lookup"><span data-stu-id="18baf-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="18baf-116">Conocer el contenido de destino de un usuario aumenta la confianza con respecto a la forma en que va a interactuar.</span><span class="sxs-lookup"><span data-stu-id="18baf-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="18baf-117">Mira al principio en el kit de herramientas de la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="18baf-117">Head-gaze in the Mixed Reality Toolkit</span></span> 
<span data-ttu-id="18baf-118">Puede acceder al encabezado de la mirada desde el [Administrador de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) en MRTK.</span><span class="sxs-lookup"><span data-stu-id="18baf-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="18baf-119">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="18baf-119">Next Development Checkpoint</span></span>

<span data-ttu-id="18baf-120">Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="18baf-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="18baf-121">Desde aquí, puede continuar con el siguiente bloque de creación:</span><span class="sxs-lookup"><span data-stu-id="18baf-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="18baf-122">Gestos y controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="18baf-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="18baf-123">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="18baf-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="18baf-124">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="18baf-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="18baf-125">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="18baf-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="18baf-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="18baf-126">See also</span></span>
* [<span data-ttu-id="18baf-127">Cámara</span><span class="sxs-lookup"><span data-stu-id="18baf-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="18baf-128">Cursores</span><span class="sxs-lookup"><span data-stu-id="18baf-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="18baf-129">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="18baf-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
