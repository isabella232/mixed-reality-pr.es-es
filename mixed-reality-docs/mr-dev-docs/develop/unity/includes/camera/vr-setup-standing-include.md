---
ms.openlocfilehash: 5f990569ae4052377cba717b5526bb8ba51b8016
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636387"
---
# <a name="mrtk"></a>[<span data-ttu-id="820f0-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="820f0-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="820f0-102">Use la clase [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) de MRTK para Unity y establezca la **escala de destino** en cualquier **habitación** o **posición**:</span><span class="sxs-lookup"><span data-stu-id="820f0-102">Use the [MixedRealityPlayspace](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.mixedrealityplayspace) class from MRTK for Unity and set the **Target Scale** to either **Room** or **Standing**:</span></span>

![Ventana de configuración de MRTK](../../images/mrtk-target-scale.png)

<span data-ttu-id="820f0-104">MRTK debe controlar la posición de los Playspace y de la cámara automáticamente, pero es conveniente realizar una doble comprobación:</span><span class="sxs-lookup"><span data-stu-id="820f0-104">MRTK should handle the position of the playspace and camera automatically, but it's good to double check:</span></span>

![MRTK playspace](../../images/mrtk-playspace.png)

1. <span data-ttu-id="820f0-106">En el panel **jerarquía** , expanda **MixedRealityPlayspace** GameObject y busque el objeto secundario **Camera principal** .</span><span class="sxs-lookup"><span data-stu-id="820f0-106">From the **Hierarchy** panel, expand the **MixedRealityPlayspace** GameObject and find the **Main Camera** child object</span></span>
2. <span data-ttu-id="820f0-107">En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** a **(X: 0, y: 0, Z: 0)**</span><span class="sxs-lookup"><span data-stu-id="820f0-107">In the **Inspector** panel, find the **Transform** component and change the **Position** to **(X: 0, Y: 0, Z: 0)**</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="820f0-108">SDK DE XR</span><span class="sxs-lookup"><span data-stu-id="820f0-108">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="820f0-109">Establezca el modo de origen del seguimiento en [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span><span class="sxs-lookup"><span data-stu-id="820f0-109">Set your tracking origin mode on the [XRInputSubsystem](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.html).</span></span> <span data-ttu-id="820f0-110">Después de obtener el subsistema, llame a [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span><span class="sxs-lookup"><span data-stu-id="820f0-110">After obtaining the subsystem, call [TrySetTrackingOriginMode](https://docs.unity3d.com/Documentation/ScriptReference/XR.XRInputSubsystem.TrySetTrackingOriginMode.html):</span></span>

```cs
xrInputSubsystem.TrySetTrackingOriginMode(TrackingOriginModeFlags.Floor);
```

<span data-ttu-id="820f0-111">Y trabaje con [XRRigs](https://docs.unity3d.com/Manual/configuring-project-for-xr.html)de Unity.</span><span class="sxs-lookup"><span data-stu-id="820f0-111">And work with Unity's [XRRig](https://docs.unity3d.com/Manual/configuring-project-for-xr.html).</span></span>

![Plataforma de pruebas de XR en jerarquía](../../images/xrsdk-xrrig.png)

# <a name="legacy-wsa"></a>[<span data-ttu-id="820f0-113">WSA heredado</span><span class="sxs-lookup"><span data-stu-id="820f0-113">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

1. <span data-ttu-id="820f0-114">Vaya a la sección **otras opciones** de **configuración del reproductor de la tienda Windows** .</span><span class="sxs-lookup"><span data-stu-id="820f0-114">Go to **Other Settings** section of the **Windows Store Player Settings**</span></span>
2. <span data-ttu-id="820f0-115">Elija **Windows Mixed Reality** como el dispositivo, que puede aparecer como **Windows Holographic** en versiones anteriores de Unity.</span><span class="sxs-lookup"><span data-stu-id="820f0-115">Choose **Windows Mixed Reality** as the device, which may be listed as **Windows Holographic** in older versions of Unity</span></span>
3. <span data-ttu-id="820f0-116">Seleccionar **realidad virtual compatible**</span><span class="sxs-lookup"><span data-stu-id="820f0-116">Select **Virtual Reality Supported**</span></span>

<span data-ttu-id="820f0-117">Puesto que el objeto de cámara principal se etiqueta automáticamente como la cámara, Unity alimenta todo el movimiento y la traslación.</span><span class="sxs-lookup"><span data-stu-id="820f0-117">Since the Main Camera object is automatically tagged as the camera, Unity powers all movement and translation.</span></span>

>[!NOTE]
><span data-ttu-id="820f0-118">Esta configuración debe aplicarse a la cámara en cada escena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="820f0-118">These settings need to be applied to the Camera in each scene of your app.</span></span>
>
><span data-ttu-id="820f0-119">De forma predeterminada, cuando se crea una nueva escena en Unity, contiene una cámara principal GameObject en la jerarquía que incluye el componente de cámara, pero no tiene la configuración que se aplica correctamente.</span><span class="sxs-lookup"><span data-stu-id="820f0-119">By default, when you create a new scene in Unity, it will contain a Main Camera GameObject in the Hierarchy which includes the Camera component, but does not have the settings below properly applied.</span></span>

<span data-ttu-id="820f0-120">**Espacio de nombres:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="820f0-120">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="820f0-121">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="820f0-121">**Type:** *XRDevice*</span></span>

<span data-ttu-id="820f0-122">En el caso de una experiencia de escalado **permanente** o de **escalado de habitación**, deberá colocar contenido en relación con el piso.</span><span class="sxs-lookup"><span data-stu-id="820f0-122">For a **standing-scale** or **room-scale experience**, you'll need to place content relative to the floor.</span></span> <span data-ttu-id="820f0-123">Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución.</span><span class="sxs-lookup"><span data-stu-id="820f0-123">You reason about the user's floor using the **[spatial stage](../../../../design/coordinate-systems.md#spatial-coordinate-systems)**, which represents the user's defined floor-level origin and optional room boundary, set up during first run.</span></span>

<span data-ttu-id="820f0-124">Para asegurarse de que Unity funcione con su sistema de coordenadas universal en el nivel inferior, puede establecer y probar que Unity usa el tipo de espacio de seguimiento de RoomScale:</span><span class="sxs-lookup"><span data-stu-id="820f0-124">To ensure that Unity is operating with its world coordinate system at floor-level, you can set and test that Unity is using the RoomScale tracking space type:</span></span>

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

* <span data-ttu-id="820f0-125">Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universal para realizar el seguimiento del [marco de fase de referencia](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span><span class="sxs-lookup"><span data-stu-id="820f0-125">If SetTrackingSpaceType returns true, Unity has successfully switched its world coordinate system to track the [stage frame of reference](../../../../design/coordinate-systems.md#spatial-coordinate-systems).</span></span>
* <span data-ttu-id="820f0-126">Si SetTrackingSpaceType devuelve false, Unity no pudo cambiar al marco de la fase de referencia, probablemente porque el usuario no ha configurado un piso en su entorno.</span><span class="sxs-lookup"><span data-stu-id="820f0-126">If SetTrackingSpaceType returns false, Unity was unable to switch to the stage frame of reference, likely because the user has not set up a floor in their environment.</span></span> <span data-ttu-id="820f0-127">Aunque un valor devuelto falso no es habitual, puede suceder si la fase se configura en otro salón y el dispositivo se mueve a la habitación actual sin que el usuario configure una nueva fase.</span><span class="sxs-lookup"><span data-stu-id="820f0-127">While a false return value isn't common, it can happen if the stage is set up in a different room and the device is moved to the current room without the user setting up a new stage.</span></span>

<span data-ttu-id="820f0-128">Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo.</span><span class="sxs-lookup"><span data-stu-id="820f0-128">Once your app successfully sets the RoomScale tracking space type, content placed on the y=0 plane will appear on the floor.</span></span> <span data-ttu-id="820f0-129">El origen en 0, 0, 0 será el lugar específico del piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección hacia delante hacia delante durante la instalación.</span><span class="sxs-lookup"><span data-stu-id="820f0-129">The origin at 0, 0, 0 will be the specific place on the floor where the user stood during room setup, with -Z representing the forward direction they were facing during setup.</span></span>