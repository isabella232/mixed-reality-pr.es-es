---
ms.openlocfilehash: 6e751f5376110ddc6ae92c75b4182fba8240a356
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748511"
---
# <a name="mrtk"></a>[<span data-ttu-id="e5645-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="e5645-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="e5645-102">Siga este [tutorial paso a paso](../../tutorials/mr-learning-base-01.md) para agregar y configurar automáticamente Mixed Reality Toolkit en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="e5645-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="e5645-103">También es posible trabajar directamente con la clase [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establecer la escala de destino **en** **Mundo:**</span><span class="sxs-lookup"><span data-stu-id="e5645-103">It's also possible to work directly with the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="e5645-105">MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:</span><span class="sxs-lookup"><span data-stu-id="e5645-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Espacio de reproducción de MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="e5645-107">En el panel **Hierarchy** (Jerarquía), expanda **MixedRealityPlayspace** GameObject y busque el **objeto secundario Main Camera (Cámara** principal).</span><span class="sxs-lookup"><span data-stu-id="e5645-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="e5645-108">En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="e5645-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="e5645-109">XR SDK</span><span class="sxs-lookup"><span data-stu-id="e5645-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="e5645-110">Establezca el modo de origen de seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="e5645-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="e5645-111">Después de obtener el subsistema, llame [a TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="e5645-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="e5645-112">Puede usar [ARSession para](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) aplicaciones HoloLens, que funciona mejor con delimitadores y ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="e5645-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sesión de AR en la jerarquía](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="e5645-114">La sesión de AR y las características relacionadas necesitan que AR Foundation esté instalado.</span><span class="sxs-lookup"><span data-stu-id="e5645-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="e5645-115">También es posible aplicar los cambios de cámara manualmente sin usar ARSession:</span><span class="sxs-lookup"><span data-stu-id="e5645-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="e5645-116">Seleccione **Cámara principal en** el panel **Jerarquía.**</span><span class="sxs-lookup"><span data-stu-id="e5645-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="e5645-117">En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="e5645-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="e5645-118">![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="e5645-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="e5645-119">*Cámara en el panel Inspector de Unity*</span><span class="sxs-lookup"><span data-stu-id="e5645-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="e5645-120">Agregar **trackedPoseDriver** a la **cámara principal**</span><span class="sxs-lookup"><span data-stu-id="e5645-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="e5645-121">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="e5645-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="e5645-122">Seleccione **Cámara principal en** el panel **Jerarquía.**</span><span class="sxs-lookup"><span data-stu-id="e5645-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="e5645-123">En el **panel Inspector,** busque el componente **Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="e5645-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="e5645-124">![Cámara en el panel Inspector de Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="e5645-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="e5645-125">*Cámara en el panel Inspector de Unity*</span><span class="sxs-lookup"><span data-stu-id="e5645-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="e5645-126">Vaya a **la sección Otras configuraciones** de la Configuración **del Reproductor de la Tienda Windows.**</span><span class="sxs-lookup"><span data-stu-id="e5645-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="e5645-127">Elija **Windows Mixed Reality** como dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.</span><span class="sxs-lookup"><span data-stu-id="e5645-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="e5645-128">Seleccione **Virtual Reality Supported (Realidad virtual compatible)**</span><span class="sxs-lookup"><span data-stu-id="e5645-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="e5645-129">Dado que el objeto Cámara principal se etiqueta automáticamente como cámara, Unity potencia todo el movimiento y la traducción.</span><span class="sxs-lookup"><span data-stu-id="e5645-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="e5645-130">Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e5645-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="e5645-131">De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Camera, pero es posible que no tenga la configuración aplicada correctamente.</span><span class="sxs-lookup"><span data-stu-id="e5645-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>