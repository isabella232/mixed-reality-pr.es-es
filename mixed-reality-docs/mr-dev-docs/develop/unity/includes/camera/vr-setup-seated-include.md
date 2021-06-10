---
ms.openlocfilehash: 3bffb5db8f4a36d04c2b408c939cbd2010a7def7
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748510"
---
# <a name="mrtk"></a>[<span data-ttu-id="5d885-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="5d885-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5d885-102">Use la [clase MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca **La** escala de destino **en Asentado:**</span><span class="sxs-lookup"><span data-stu-id="5d885-102">Use the [MixedRealityPlayspace](/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to **Seated**:</span></span>

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="5d885-104">MRTK debe controlar la posición del espacio de juego y la cámara automáticamente, pero es bueno comprobarlo de nuevo:</span><span class="sxs-lookup"><span data-stu-id="5d885-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![Espacio de juego de MRTK](../../images/mrtk-playspace.png)

1. <span data-ttu-id="5d885-106">En el panel **Jerarquía,** expanda **el objeto GameObject MixedRealityPlayspace** y busque el objeto secundario **Cámara** principal.</span><span class="sxs-lookup"><span data-stu-id="5d885-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="5d885-107">En el **panel Inspector,** busque el **componente Transformar** y cambie **la posición** a **(X: 0, Y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="5d885-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="5d885-108">XR SDK</span><span class="sxs-lookup"><span data-stu-id="5d885-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="5d885-109">Establezca el modo de origen de seguimiento [en XRInputSubsystem.](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html)</span><span class="sxs-lookup"><span data-stu-id="5d885-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="5d885-110">Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="5d885-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Device);
```

<span data-ttu-id="5d885-111">Y trabaje con [XRRig de](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)Unity.</span><span class="sxs-lookup"><span data-stu-id="5d885-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![XR en jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="5d885-113">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="5d885-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="5d885-114">Vaya a **la sección Otras configuraciones** de la Configuración **del Reproductor de la Tienda Windows.**</span><span class="sxs-lookup"><span data-stu-id="5d885-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="5d885-115">Elija **Windows Mixed Reality** dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.</span><span class="sxs-lookup"><span data-stu-id="5d885-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="5d885-116">Seleccione **Virtual Reality Supported (Realidad virtual admitida)**</span><span class="sxs-lookup"><span data-stu-id="5d885-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="5d885-117">Dado que el objeto Cámara principal se etiqueta automáticamente como la cámara, Unity impulsa todo el movimiento y la traducción.</span><span class="sxs-lookup"><span data-stu-id="5d885-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="5d885-118">Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5d885-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="5d885-119">De forma predeterminada, al crear una nueva escena en Unity, contendrá un GameObject de cámara principal en la jerarquía que incluye el componente Camera, pero no tiene la configuración siguiente aplicada correctamente.</span><span class="sxs-lookup"><span data-stu-id="5d885-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="5d885-120">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5d885-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5d885-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="5d885-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="5d885-122">Para crear una **experiencia de solo orientación** o de escala asentada, debe establecer Unity en el tipo de espacio de seguimiento estacionado. </span><span class="sxs-lookup"><span data-stu-id="5d885-122">To build an **orientation-only** or **seated-scale experience**, you need to set Unity to the Stationary tracking space type.</span></span> <span data-ttu-id="5d885-123">El espacio de seguimiento estacionario establece el sistema de coordenadas universal de Unity para realizar un seguimiento del [marco de referencia estacionada.](../../../../design/coordinate-systems.md#spatial-coordinate-systems)</span><span class="sxs-lookup"><span data-stu-id="5d885-123">Stationary tracking space sets Unity's world coordinate system to track the [stationary frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span> <span data-ttu-id="5d885-124">En el modo de seguimiento estacionado, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el reenvío es -Z) aparecerá delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5d885-124">In the Stationary tracking mode, content placed in the editor just in front of the camera's default location (forward is -Z) will appear in front of the user when the app launches.</span></span>

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

<span data-ttu-id="5d885-125">**Espacio de nombres:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="5d885-125">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5d885-126">**Tipo:** *InputTracking*</span><span class="sxs-lookup"><span data-stu-id="5d885-126">**Type:** *InputTracking*</span></span>

<span data-ttu-id="5d885-127">Para una **experiencia** pura de solo orientación, como un visor de vídeo de 360 grados (donde las actualizaciones de la cabeza posicional harían perder la esperanza), puede establecer [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:</span><span class="sxs-lookup"><span data-stu-id="5d885-127">For a pure **orientation-only experience** such as a 360-degree video viewer (where positional head updates would ruin the illusion), you can then set [XR.InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) to true:</span></span>

```cs
InputTracking.disablePositionalTracking = true;
```

<span data-ttu-id="5d885-128">Para una **experiencia de escalado asentado**, para permitir que el usuario más adelante haga más reciente el origen asentado, puede llamar al [XR. Método InputTracking.Recenter:](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)</span><span class="sxs-lookup"><span data-stu-id="5d885-128">For a **seated-scale experience**, to let the user later recenter the seated origin, you can call the [XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) method:</span></span>

```cs
InputTracking.Recenter();
```

<span data-ttu-id="5d885-129">Si va [a](../../../../design/coordinate-systems.md)crear una experiencia de escalado asentado, puede hacer más reciente el origen mundial de Unity en la posición de la cabeza actual del usuario mediante una llamada a **[la XR. Método InputTracking.Recenter.](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)**</span><span class="sxs-lookup"><span data-stu-id="5d885-129">If you're building a [seated-scale experience](../../../../design/coordinate-systems.md), you can recenter Unity's world origin at the user's current head position by calling the **[XR.InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** method.</span></span>