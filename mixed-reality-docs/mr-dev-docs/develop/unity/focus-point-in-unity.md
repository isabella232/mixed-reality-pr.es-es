---
title: Punto de enfoque en Unity
description: Ajuste manual de la estabilidad de holograma en Unity estableciendo el punto de enfoque
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, plano de enfoque, plano de estabilización, punto de estabilización, Reproyección, LSR, búfer de profundidad
ms.openlocfilehash: 4d8c8a232d12a8d6f0a7694fbc0ed8f66395163a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691244"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="cf4a1-104">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="cf4a1-104">Focus point in Unity</span></span>

<span data-ttu-id="cf4a1-105">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="cf4a1-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="cf4a1-106">**Tipo** : *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="cf4a1-106">**Type** : *HolographicSettings*</span></span>

<span data-ttu-id="cf4a1-107">Se puede establecer el [punto de enfoque](../platform-capabilities-and-apis/hologram-stability.md#reprojection) para proporcionar a HoloLens una sugerencia sobre cómo realizar mejor la estabilización en los hologramas que se muestran actualmente.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-107">The [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) can be set to provide HoloLens a hint about how to best perform stabilization on the holograms currently being displayed.</span></span>

<span data-ttu-id="cf4a1-108">Si desea establecer el punto de enfoque en Unity, debe establecer cada fotograma mediante *HolographicSettings. SetFocusPointForFrame ()* .</span><span class="sxs-lookup"><span data-stu-id="cf4a1-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()* .</span></span> <span data-ttu-id="cf4a1-109">Si no se establece el punto de enfoque para un marco, se usará el plano de estabilización predeterminado.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-109">If the Focus Point is not set for a frame, the default stabilization plane will be used.</span></span>

> [!NOTE]
> <span data-ttu-id="cf4a1-110">De forma predeterminada, los nuevos proyectos de Unity tienen establecida la opción "habilitar el uso compartido del búfer de profundidad".</span><span class="sxs-lookup"><span data-stu-id="cf4a1-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="cf4a1-111">Con esta opción, una aplicación de Unity que se ejecute en un casco de escritorio envolvente o en una HoloLens que ejecute la actualización 2018 de abril de Windows 10 (RS4) o posterior enviará el búfer de profundidad a Windows para optimizar la estabilidad del holograma automáticamente, sin que la aplicación especifique un punto de enfoque:</span><span class="sxs-lookup"><span data-stu-id="cf4a1-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="cf4a1-112">En un casco de escritorio envolvente, esto habilitará la Reproyección basada en profundidad por píxel.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="cf4a1-113">En una HoloLens que ejecute la actualización de abril de 2018 de Windows 10 o posterior, se analizará el búfer de profundidad para elegir un plano de estabilización óptimo automáticamente.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="cf4a1-114">Cualquier enfoque debe proporcionar una calidad de imagen incluso mejor sin que la aplicación proporcione un trabajo explícito para seleccionar un punto de enfoque para cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="cf4a1-115">Tenga en cuenta que si proporciona un punto de enfoque manualmente, se invalidará el comportamiento automático descrito anteriormente y se reducirá la estabilidad del holograma.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="cf4a1-116">Por lo general, solo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en una HoloLens que todavía no se ha actualizado a la actualización 2018 de abril de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="cf4a1-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="cf4a1-117">Example</span></span>

<span data-ttu-id="cf4a1-118">Hay muchas maneras de establecer el punto de enfoque, como se sugiere por las sobrecargas disponibles en la función estática *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="cf4a1-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="cf4a1-119">A continuación se muestra un ejemplo sencillo para establecer el plano de enfoque en el objeto proporcionado para cada fotograma:</span><span class="sxs-lookup"><span data-stu-id="cf4a1-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

<span data-ttu-id="cf4a1-120">Tenga en cuenta que el código anterior puede acabar reduciendo la estabilidad del holograma si el objeto que tiene el foco termina detrás del usuario.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-120">Note that the simple code above may end up reducing hologram stability if the focused object ends up behind the user.</span></span>  <span data-ttu-id="cf4a1-121">Este es el motivo por el que normalmente debería establecer "habilitar el uso compartido del búfer de profundidad" en lugar de especificar manualmente un punto de enfoque.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-121">This is why you should generally set "Enable Depth Buffer Sharing" instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cf4a1-122">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="cf4a1-122">Next Development Checkpoint</span></span>

<span data-ttu-id="cf4a1-123">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-123">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="cf4a1-124">Desde aquí, puede continuar con el tema siguiente:</span><span class="sxs-lookup"><span data-stu-id="cf4a1-124">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf4a1-125">Pérdida de seguimiento</span><span class="sxs-lookup"><span data-stu-id="cf4a1-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="cf4a1-126">O ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="cf4a1-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf4a1-127">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="cf4a1-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="cf4a1-128">Siempre puede volver a los puntos de [control de desarrollo de Unity](unity-development-overview.md#3-platform-capabilities-and-apis) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="cf4a1-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="cf4a1-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="cf4a1-129">See also</span></span>
* [<span data-ttu-id="cf4a1-130">Plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="cf4a1-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
