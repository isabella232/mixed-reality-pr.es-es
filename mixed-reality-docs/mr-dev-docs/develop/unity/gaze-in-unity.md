---
title: Mirada en Unity
description: Obtenga información sobre cómo usar la entrada de mirada como una forma principal para que los usuarios puedan dirigirse a los hologramas que la aplicación crea en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: mirada con los ojos, mirada con la cabeza, unity, holograma, realidad mixta, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600154"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="fbdc9-104">Mirada con la cabeza en Unity</span><span class="sxs-lookup"><span data-stu-id="fbdc9-104">Head-gaze in Unity</span></span>

<span data-ttu-id="fbdc9-105">[La](../../design/gaze-and-commit.md) mirada es la manera principal para que los usuarios se [descumenten los hologramas](../../discover/hologram.md) que la [aplicación crea Mixed Reality](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="fbdc9-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="fbdc9-106">Implementación de la mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="fbdc9-106">Implementing head-gaze</span></span>

<span data-ttu-id="fbdc9-107">Conceptualmente, puede determinar la [mirada](../../design/gaze-and-commit.md) con la cabeza proyectando un rayo hacia delante desde el casco del usuario para ver lo que alcanza.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="fbdc9-108">En Unity, la posición y la dirección de la cabeza del usuario se exponen a través de [la cámara](camera-in-unity.md), específicamente [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) y [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="fbdc9-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="fbdc9-109">Llamar [a Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) proporciona un [Objeto RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) que contiene información sobre la colisión, incluido el punto de colisión 3D y el otro GameObject al que se ha alcanzado el rayo de mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="fbdc9-110">Ejemplo: Implementación de la mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="fbdc9-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="fbdc9-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="fbdc9-111">Best practices</span></span>

<span data-ttu-id="fbdc9-112">Aunque en el ejemplo anterior se muestra un único raycast desde el bucle de actualización para buscar el destino en el que se encuentran los puntos principales del usuario, se recomienda usar un solo objeto para administrar todos los procesos de mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="fbdc9-113">La combinación de la lógica de mirada con la cabeza ahorrará la potencia de procesamiento valiosa de la aplicación y limitará la difusión por rayos a uno por fotograma.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="fbdc9-114">Visualización de la mirada con la cabeza</span><span class="sxs-lookup"><span data-stu-id="fbdc9-114">Visualizing head-gaze</span></span>

<span data-ttu-id="fbdc9-115">Al igual que con un puntero del mouse en un equipo, debe implementar un [cursor](../../design/cursors.md) que represente la mirada con la cabeza del usuario.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="fbdc9-116">Saber qué contenido tiene como destino un usuario aumenta la confianza en lo que está a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="fbdc9-117">Mirada con la cabeza en el kit de herramientas Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="fbdc9-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="fbdc9-118">Puede acceder a la mirada con la cabeza desde [el Administrador de entrada](/windows/mixed-reality/mrtk-unity/features/input/overview) en MRTK.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="fbdc9-119">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="fbdc9-119">Next Development Checkpoint</span></span>

<span data-ttu-id="fbdc9-120">Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra en medio de la exploración de los bloques de creación principales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="fbdc9-121">Desde aquí, puede continuar con el siguiente bloque de compilación:</span><span class="sxs-lookup"><span data-stu-id="fbdc9-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbdc9-122">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="fbdc9-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="fbdc9-123">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="fbdc9-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fbdc9-124">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="fbdc9-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="fbdc9-125">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="fbdc9-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbdc9-126">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fbdc9-126">See also</span></span>
* [<span data-ttu-id="fbdc9-127">Cámara</span><span class="sxs-lookup"><span data-stu-id="fbdc9-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="fbdc9-128">Cursores</span><span class="sxs-lookup"><span data-stu-id="fbdc9-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="fbdc9-129">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="fbdc9-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)