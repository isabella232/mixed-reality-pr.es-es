---
ms.openlocfilehash: 7470690a96380184ead7319d4461005042c6db82
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636319"
---
# <a name="mrtk"></a>[<span data-ttu-id="257a9-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="257a9-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="257a9-102">Siga este [Tutorial paso a paso](../../tutorials/mr-learning-base-01.md) para agregar y configurar automáticamente el kit de herramientas de realidad mixta en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="257a9-102">Follow this [step-by-step tutorial](../../tutorials/mr-learning-base-01.md) to add and automatically configure Mixed Reality Toolkit in your Unity project.</span></span> <span data-ttu-id="257a9-103">También es posible trabajar directamente con la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establecer la escala de **destino** en **mundo**:</span><span class="sxs-lookup"><span data-stu-id="257a9-103">It's also possible to work directly with the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **World**:</span></span>

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="257a9-105">MRTK debe controlar la posición de los Playspace y de la cámara automáticamente, pero es conveniente realizar una doble comprobación:</span><span class="sxs-lookup"><span data-stu-id="257a9-105">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="257a9-107">En el panel **jerarquía** , expanda **MixedRealityPlayspace** GameObject y busque el objeto secundario **Camera principal** .</span><span class="sxs-lookup"><span data-stu-id="257a9-107">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="257a9-108">En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="257a9-108">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="257a9-109">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="257a9-109">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="257a9-110">Establezca el modo de origen del seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="257a9-110">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="257a9-111">Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="257a9-111">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Unbounded); // Recommendation for OpenXR
```

<span data-ttu-id="257a9-112">Puede usar [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) para las aplicaciones de HoloLens, que funciona mejor con los delimitadores y ARKit/ARCore.</span><span class="sxs-lookup"><span data-stu-id="257a9-112">You can use [ARSession](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.1/manual/index.html#installing-ar-foundation) for HoloLens applications, which works better with anchors and ARKit/ARCore.</span></span>

![Sesión de AR en jerarquía](../../images/xrsdk-arsession.png)

> [!IMPORTANT]
> <span data-ttu-id="257a9-114">La sesión AR y las características relacionadas necesitan AR Foundation instalado.</span><span class="sxs-lookup"><span data-stu-id="257a9-114">AR Session and related features need AR Foundation installed.</span></span>

<span data-ttu-id="257a9-115">También es posible aplicar los cambios de la cámara manualmente sin usar ARSession:</span><span class="sxs-lookup"><span data-stu-id="257a9-115">It's also possible to apply the camera changes manually without using ARSession:</span></span>

1. <span data-ttu-id="257a9-116">Seleccionar **cámara principal** en el panel **jerarquía**</span><span class="sxs-lookup"><span data-stu-id="257a9-116">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="257a9-117">En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="257a9-117">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="257a9-118">![Cámara en el panel del inspector en Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="257a9-118">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="257a9-119">*Cámara en el panel del inspector en Unity*</span><span class="sxs-lookup"><span data-stu-id="257a9-119">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="257a9-120">Agregar un **TrackedPoseDriver** a la **cámara principal**</span><span class="sxs-lookup"><span data-stu-id="257a9-120">Add a **TrackedPoseDriver** to the **Main Camera**</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="257a9-121">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="257a9-121">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="257a9-122">Seleccionar **cámara principal** en el panel **jerarquía**</span><span class="sxs-lookup"><span data-stu-id="257a9-122">Select **Main Camera** in the **Hierarchy** panel</span></span>
1. <span data-ttu-id="257a9-123">En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="257a9-123">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

   <span data-ttu-id="257a9-124">![Cámara en el panel del inspector en Unity](../../images/maincamera-350px.png)</span><span class="sxs-lookup"><span data-stu-id="257a9-124">![Camera in the Inspector pane in Unity](../../images/maincamera-350px.png)</span></span>  
   <span data-ttu-id="257a9-125">*Cámara en el panel del inspector en Unity*</span><span class="sxs-lookup"><span data-stu-id="257a9-125">*Camera in the Inspector pane in Unity*</span></span>

1. <span data-ttu-id="257a9-126">Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="257a9-126">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
1. <span data-ttu-id="257a9-127">Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.</span><span class="sxs-lookup"><span data-stu-id="257a9-127">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
1. <span data-ttu-id="257a9-128">Seleccionar **realidad virtual compatible**</span><span class="sxs-lookup"><span data-stu-id="257a9-128">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="257a9-129">Puesto que el objeto de cámara principal se etiqueta automáticamente como la cámara, Unity alimenta todo el movimiento y la traslación.</span><span class="sxs-lookup"><span data-stu-id="257a9-129">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="257a9-130">Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="257a9-130">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="257a9-131">De forma predeterminada, al crear una nueva escena en Unity, contendrá una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero es posible que no tenga la configuración aplicada correctamente.</span><span class="sxs-lookup"><span data-stu-id="257a9-131">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but may not have the settings properly applied.</span></span>