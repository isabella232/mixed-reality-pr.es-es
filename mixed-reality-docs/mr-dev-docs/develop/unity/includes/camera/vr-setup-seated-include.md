---
ms.openlocfilehash: c7e5be36420ef14fe5aaeaafb49c0a990942339f
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636376"
---
# <a name="mrtk"></a>[<span data-ttu-id="19059-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="19059-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="19059-102">Use la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca la **escala de destino** en **encajada**:</span><span class="sxs-lookup"><span data-stu-id="19059-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="19059-104">MRTK debe controlar la posición de los Playspace y de la cámara automáticamente, pero es conveniente realizar una doble comprobación:</span><span class="sxs-lookup"><span data-stu-id="19059-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="19059-106">En el panel **jerarquía** , expanda **MixedRealityPlayspace** GameObject y busque el objeto secundario **Camera principal** .</span><span class="sxs-lookup"><span data-stu-id="19059-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="19059-107">En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="19059-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="19059-108">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="19059-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="19059-109">Establezca el modo de origen del seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="19059-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="19059-110">Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="19059-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="19059-111">Y trabaje con [XRRigs](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)de Unity.</span><span class="sxs-lookup"><span data-stu-id="19059-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Plataforma de pruebas de XR en jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="19059-113">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="19059-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="19059-114">Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="19059-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="19059-115">Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.</span><span class="sxs-lookup"><span data-stu-id="19059-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="19059-116">Seleccionar **realidad virtual compatible**</span><span class="sxs-lookup"><span data-stu-id="19059-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="19059-117">Puesto que el objeto de cámara principal se etiqueta automáticamente como la cámara, Unity alimenta todo el movimiento y la traslación.</span><span class="sxs-lookup"><span data-stu-id="19059-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="19059-118">Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="19059-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="19059-119">De forma predeterminada, cuando se crea una nueva escena en Unity, contiene una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero no tiene la configuración que se aplica correctamente.</span><span class="sxs-lookup"><span data-stu-id="19059-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="19059-120">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="19059-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="19059-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="19059-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="19059-122">Para compilar una experiencia de **solo orientación** o **de escalado original**, debe establecer Unity en el tipo de espacio de seguimiento de la estación.</span><span class="sxs-lookup"><span data-stu-id="19059-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="19059-123">El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="19059-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="19059-124">En el modo de seguimiento estacionario, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparecerá delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="19059-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="19059-125">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="19059-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="19059-126">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="19059-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="19059-127">En el caso de una **experiencia pura de solo orientación** , como un visor de vídeo de 360 grados (donde las actualizaciones de los cabezales posicionales estropearían la ilusión), puede establecer [XR. InputTracking. disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="19059-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="19059-128">En el caso de una **experiencia de escalado** inactiva, para permitir que el usuario recentre posteriormente el origen de la caja, puede llamar a [XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) :</span><span class="sxs-lookup"><span data-stu-id="19059-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="19059-129">Si va a crear una [experiencia de escalado original](../../../../design/coordinate-systems.md), puede volver a centrar el origen mundial de Unity en la posición principal del usuario mediante una llamada a **[XR. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** .</span><span class="sxs-lookup"><span data-stu-id="19059-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>