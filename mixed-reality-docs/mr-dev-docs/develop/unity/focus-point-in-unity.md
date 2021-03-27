---
title: Punto de enfoque en Unity
description: Obtenga información sobre cómo ajustar manualmente la estabilidad de los hologramas en Unity mediante el establecimiento del punto de enfoque para HoloLens y los auriculares con micrófonos de la realidad mixta de Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, punto de enfoque, plano de enfoque, plano de estabilización, punto de estabilización, Reproyección, LSR, búfer de profundidad, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 16f359e1742b86c5f12c0c5965ac9e818ea76aee
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636227"
---
# <a name="focus-point-in-unity"></a><span data-ttu-id="10f92-104">Punto de enfoque en Unity</span><span class="sxs-lookup"><span data-stu-id="10f92-104">Focus point in Unity</span></span>

<span data-ttu-id="10f92-105">**Espacio de nombres:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="10f92-105">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="10f92-106">**Tipo**: *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="10f92-106">**Type**: *HolographicSettings*</span></span>

<span data-ttu-id="10f92-107">Use el [punto de enfoque](../platform-capabilities-and-apis/hologram-stability.md#reprojection) para proporcionar a HoloLens una sugerencia sobre cómo estabilizar mejor los hologramas que se muestran actualmente.</span><span class="sxs-lookup"><span data-stu-id="10f92-107">Use the [focus point](../platform-capabilities-and-apis/hologram-stability.md#reprojection) to provide HoloLens with a hint about how to best stabilize the holograms currently being displayed.</span></span>

<span data-ttu-id="10f92-108">Si desea establecer el punto de enfoque en Unity, debe establecer cada fotograma mediante *HolographicSettings. SetFocusPointForFrame ()*.</span><span class="sxs-lookup"><span data-stu-id="10f92-108">If you want to set the Focus Point in Unity, it needs to be set every frame using *HolographicSettings.SetFocusPointForFrame()*.</span></span> <span data-ttu-id="10f92-109">Cuando no se establece el punto de enfoque para un marco, se utiliza el plano de estabilización predeterminado.</span><span class="sxs-lookup"><span data-stu-id="10f92-109">When the Focus Point isn't set for a frame, the default stabilization plane is used.</span></span>

> [!NOTE]
> <span data-ttu-id="10f92-110">De forma predeterminada, los nuevos proyectos de Unity tienen establecida la opción "habilitar el uso compartido del búfer de profundidad".</span><span class="sxs-lookup"><span data-stu-id="10f92-110">By default, new Unity projects have the "Enable Depth Buffer Sharing" option set.</span></span>  <span data-ttu-id="10f92-111">Con esta opción, una aplicación de Unity que se ejecute en un casco de escritorio envolvente o en una HoloLens que ejecute la actualización 2018 de abril de Windows 10 (RS4) o posterior enviará el búfer de profundidad a Windows para optimizar la estabilidad del holograma automáticamente, sin que la aplicación especifique un punto de enfoque:</span><span class="sxs-lookup"><span data-stu-id="10f92-111">With this option, a Unity app running on either an immersive desktop headset or a HoloLens running the Windows 10 April 2018 Update (RS4) or later will submit your depth buffer to Windows to optimize hologram stability automatically, without your app specifying a focus point:</span></span>
> * <span data-ttu-id="10f92-112">En un casco de escritorio envolvente, esto habilitará la Reproyección basada en profundidad por píxel.</span><span class="sxs-lookup"><span data-stu-id="10f92-112">On an immersive desktop headset, this will enable per-pixel depth-based reprojection.</span></span>
> * <span data-ttu-id="10f92-113">En una HoloLens que ejecute la actualización de abril de 2018 de Windows 10 o posterior, se analizará el búfer de profundidad para elegir un plano de estabilización óptimo automáticamente.</span><span class="sxs-lookup"><span data-stu-id="10f92-113">On a HoloLens running the Windows 10 April 2018 Update or later, this will analyze the depth buffer to pick an optimal stabilization plane automatically.</span></span>
>
> <span data-ttu-id="10f92-114">Cualquier enfoque debe proporcionar una calidad de imagen incluso mejor sin que la aplicación proporcione un trabajo explícito para seleccionar un punto de enfoque para cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="10f92-114">Either approach should provide even better image quality without explicit work by your app to select a focus point for each frame.</span></span>  <span data-ttu-id="10f92-115">Tenga en cuenta que si proporciona un punto de enfoque manualmente, se invalidará el comportamiento automático descrito anteriormente y se reducirá la estabilidad del holograma.</span><span class="sxs-lookup"><span data-stu-id="10f92-115">Note that if you do provide a focus point manually, that will override the automatic behavior described above, and will usually reduce hologram stability.</span></span>  <span data-ttu-id="10f92-116">Por lo general, solo debe especificar un punto de enfoque manual cuando la aplicación se ejecuta en una HoloLens que todavía no se ha actualizado a la actualización 2018 de abril de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="10f92-116">Generally, you should only specify a manual focus point when your app is running on a HoloLens that has not yet been updated to the Windows 10 April 2018 Update.</span></span>

### <a name="example"></a><span data-ttu-id="10f92-117">Ejemplo</span><span class="sxs-lookup"><span data-stu-id="10f92-117">Example</span></span>

<span data-ttu-id="10f92-118">Hay muchas maneras de establecer el punto de enfoque, como se sugiere por las sobrecargas disponibles en la función estática *SetFocusPointForFrame* .</span><span class="sxs-lookup"><span data-stu-id="10f92-118">There are many ways to set the Focus Point, as suggested by the overloads available on the *SetFocusPointForFrame* static function.</span></span> <span data-ttu-id="10f92-119">A continuación se muestra un ejemplo sencillo para establecer el plano de enfoque en el objeto proporcionado para cada fotograma:</span><span class="sxs-lookup"><span data-stu-id="10f92-119">Presented below is a simple example to set the focus plane to the provided object for each frame:</span></span>

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

> [!NOTE]
> <span data-ttu-id="10f92-120">El código más anterior puede reducir la estabilidad de los hologramas si el objeto que tiene el foco termina detrás del usuario.</span><span class="sxs-lookup"><span data-stu-id="10f92-120">The simple code above may reduce hologram stability if the focused object ends up behind the user.</span></span> <span data-ttu-id="10f92-121">Por lo general, se recomienda establecer **[Habilitar el uso compartido del búfer de profundidad](camera-in-unity.md#sharing-depth-buffers)** en lugar de especificar manualmente un punto de enfoque.</span><span class="sxs-lookup"><span data-stu-id="10f92-121">We generally recommend setting **[Enable Depth Buffer Sharing](camera-in-unity.md#sharing-depth-buffers)** instead of manually specifying a focus point.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="10f92-122">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="10f92-122">Next Development Checkpoint</span></span>

<span data-ttu-id="10f92-123">Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="10f92-123">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="10f92-124">Desde aquí, puede continuar con el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="10f92-124">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10f92-125">Pérdida de seguimiento</span><span class="sxs-lookup"><span data-stu-id="10f92-125">Tracking loss</span></span>](tracking-loss-in-unity.md)

<span data-ttu-id="10f92-126">O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="10f92-126">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="10f92-127">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="10f92-127">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="10f92-128">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="10f92-128">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

### <a name="see-also"></a><span data-ttu-id="10f92-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="10f92-129">See also</span></span>

* [<span data-ttu-id="10f92-130">Plano de estabilización</span><span class="sxs-lookup"><span data-stu-id="10f92-130">Stabilization plane</span></span>](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
