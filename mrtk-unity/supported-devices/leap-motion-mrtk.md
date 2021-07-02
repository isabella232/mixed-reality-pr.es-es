---
title: Uso de Leap Motion
description: Documentación que se debe configurar para Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Leap Motion,
ms.openlocfilehash: 3ddf039f8409022d8aa2e425c46cd4d47ede16a0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176512"
---
# <a name="using-leap-motion"></a><span data-ttu-id="d248a-104">Uso de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="d248a-104">Using Leap Motion</span></span>

<span data-ttu-id="d248a-105">Se [requiere un controlador leap motion](https://www.ultraleap.com/product/leap-motion-controller/) para usar este proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="d248a-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="d248a-106">El proveedor de datos Leap Motion permite el seguimiento de manos articulado para VR y podría ser útil para la creación rápida de prototipos en el editor.</span><span class="sxs-lookup"><span data-stu-id="d248a-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="d248a-107">El proveedor de datos se puede configurar para usar el controlador leap motion montado en un casco o colocado en un escritorio cara arriba.</span><span class="sxs-lookup"><span data-stu-id="d248a-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="d248a-109">Este proveedor se puede usar en el editor y en el dispositivo en la plataforma independiente.</span><span class="sxs-lookup"><span data-stu-id="d248a-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="d248a-110">También se puede usar en el editor mientras está en la plataforma UWP, pero NO en una compilación de UWP.</span><span class="sxs-lookup"><span data-stu-id="d248a-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

| <span data-ttu-id="d248a-111">Versión de MRTK</span><span class="sxs-lookup"><span data-stu-id="d248a-111">MRTK Version</span></span> | <span data-ttu-id="d248a-112">Versiones admitidas de los módulos de Unity de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="d248a-112">Leap Motion Unity Modules Versions Supported</span></span> |
| --- | --- |
|<span data-ttu-id="d248a-113">2.6.x</span><span class="sxs-lookup"><span data-stu-id="d248a-113">2.6.x</span></span> | <span data-ttu-id="d248a-114">4.5.0, 4.5.1</span><span class="sxs-lookup"><span data-stu-id="d248a-114">4.5.0, 4.5.1</span></span>|
|<span data-ttu-id="d248a-115">2.7.x</span><span class="sxs-lookup"><span data-stu-id="d248a-115">2.7.x</span></span>| <span data-ttu-id="d248a-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span><span class="sxs-lookup"><span data-stu-id="d248a-116">4.5.0, 4.5.1, 4.6.0, 4.7.0, 4.7.1, 4.8.0</span></span>|


## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="d248a-117">Uso del seguimiento manual de Leap Motion (by Ultraleap) en MRTK</span><span class="sxs-lookup"><span data-stu-id="d248a-117">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="d248a-118">Importación de MRTK y los módulos leap motion de Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-118">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="d248a-119">Instale el [SDK de Leap Motion](https://developer.leapmotion.com/releases/?category=orion) más reciente si aún no está instalado</span><span class="sxs-lookup"><span data-stu-id="d248a-119">Install the latest [Leap Motion SDK](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="d248a-120">Importe **Microsoft.MixedReality.Toolkit. Paquete** básico en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="d248a-120">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="d248a-121">Descarga e importación de la versión más reciente de los módulos [de Unity leap motion](https://developer.leapmotion.com/unity) en el proyecto</span><span class="sxs-lookup"><span data-stu-id="d248a-121">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="d248a-122">Importar solo el **paquete Principal** dentro de los módulos de Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-122">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="d248a-123">Integración de los módulos de Unity leap motion con MRTK</span><span class="sxs-lookup"><span data-stu-id="d248a-123">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="d248a-124">Una vez que los módulos de Unity estén en el proyecto, vaya a **Mixed Reality Toolkit**  >  Leap Motion Integrate Leap Motion Unity Modules **(Integración** de  >  **Leap Motion Unity Modules).**</span><span class="sxs-lookup"><span data-stu-id="d248a-124">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="d248a-125">La integración de los módulos de Unity en MRTK agrega 10 definiciones de ensamblado al proyecto y agrega referencias a **Microsoft.MixedReality.Toolkit. Definición del ensamblado Providers.LeapMotion.**</span><span class="sxs-lookup"><span data-stu-id="d248a-125">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="d248a-126">Asegúrese de que Visual Studio esté cerrado.</span><span class="sxs-lookup"><span data-stu-id="d248a-126">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="d248a-128">Adición del proveedor de datos Leap Motion</span><span class="sxs-lookup"><span data-stu-id="d248a-128">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="d248a-129">Creación de una nueva escena de Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-129">Create a new Unity scene</span></span>
    - <span data-ttu-id="d248a-130">Para agregar MRTK a la escena, vaya a **Mixed Reality Toolkit**  >  **Agregar a la escena y configurar**</span><span class="sxs-lookup"><span data-stu-id="d248a-130">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="d248a-131">Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione Copiar y **personalizar** para clonar el perfil de realidad mixta predeterminado.</span><span class="sxs-lookup"><span data-stu-id="d248a-131">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="d248a-133">Selección del perfil **de configuración** de entrada</span><span class="sxs-lookup"><span data-stu-id="d248a-133">Select the **Input** Configuration Profile</span></span>

    ![Perfil de configuración de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="d248a-135">Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.</span><span class="sxs-lookup"><span data-stu-id="d248a-135">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="d248a-137">Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.</span><span class="sxs-lookup"><span data-stu-id="d248a-137">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="d248a-138">Abra el nuevo proveedor de datos y establezca **El tipo** en **Microsoft.MixedReality.Toolkit. LeapMotion.Input > LeapMotionDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="d248a-138">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="d248a-140">Seleccione **Clonar** para cambiar la configuración predeterminada de Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-140">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="d248a-142">El proveedor de datos Leap Motion contiene `LeapControllerOrientation` la propiedad que es la ubicación del controlador leap motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-142">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="d248a-143">`LeapControllerOrientation.Headset` indica que el controlador está montado en un casco.</span><span class="sxs-lookup"><span data-stu-id="d248a-143">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="d248a-144">`LeapControllerOrientation.Desk` indica que el controlador se coloca plano sobre el escritorio.</span><span class="sxs-lookup"><span data-stu-id="d248a-144">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="d248a-145">El valor predeterminado se establece en `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="d248a-145">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="d248a-146">Cada orientación del controlador contiene propiedades de desplazamiento:</span><span class="sxs-lookup"><span data-stu-id="d248a-146">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="d248a-147">Las **propiedades de desplazamiento** de orientación del casco reflejan las propiedades de desplazamiento en el componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="d248a-147">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="d248a-148">tiene `LeapVRDeviceOffsetMode` tres opciones: Predeterminada, Desplazamiento manual de la cabeza y Transformación.</span><span class="sxs-lookup"><span data-stu-id="d248a-148">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="d248a-149">Si el modo de desplazamiento es Predeterminado, no se aplicará un desplazamiento al controlador leap motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-149">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="d248a-150">El modo desplazamiento manual de la cabeza permite la modificación de tres propiedades: `LeapVRDeviceOffsetY` y `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="d248a-150">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="d248a-151">A continuación, los valores de propiedad de desplazamiento del eje se aplican a la ubicación predeterminada del controlador.</span><span class="sxs-lookup"><span data-stu-id="d248a-151">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="d248a-152">El modo de desplazamiento Transformar contiene la `LeapVRDeviceOrigin` propiedad Transformar que especifica un nuevo origen para el controlador leap motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-152">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="d248a-153">La **orientación desk** contiene la propiedad que define la posición `LeapControllerOffset` delimitadora de las manos bisiesta del escritorio.</span><span class="sxs-lookup"><span data-stu-id="d248a-153">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="d248a-154">El desplazamiento se calcula en relación con la posición de la cámara principal y el valor predeterminado es (0,-0,2, 0,35) para asegurarse de que las manos aparecen delante y a la vista de la cámara.</span><span class="sxs-lookup"><span data-stu-id="d248a-154">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="d248a-155">Las propiedades de desplazamiento del perfil se aplican una vez cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d248a-155">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="d248a-156">Para modificar los valores durante el tiempo de ejecución, obtenga el proveedor del servicio Leap Motion desde la página Leap Motion Administrador de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="d248a-156">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="d248a-157">`EnterPinchDistance` y `ExitPinchDistance` son los umbrales de distancia para la detección de gestos de pulsar en el aire o desenlazador.</span><span class="sxs-lookup"><span data-stu-id="d248a-157">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="d248a-158">El gesto de acercar se calcula midiendo la distancia entre la punta del dedo índice y la punta del dedo.</span><span class="sxs-lookup"><span data-stu-id="d248a-158">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="d248a-159">Para generar un evento de entrada hacia abajo, el valor `EnterPinchDistance` predeterminado se establece en 0,02.</span><span class="sxs-lookup"><span data-stu-id="d248a-159">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="d248a-160">Para generar un evento de entrada arriba (salir de la acción de acercar), la distancia predeterminada entre la punta del dedo índice y la punta del dedo es 0,05.</span><span class="sxs-lookup"><span data-stu-id="d248a-160">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="d248a-161">`LeapControllerOrientation`: casco (valor predeterminado)</span><span class="sxs-lookup"><span data-stu-id="d248a-161">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="d248a-162">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="d248a-162">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="d248a-167">Prueba del proveedor de datos Leap Motion</span><span class="sxs-lookup"><span data-stu-id="d248a-167">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="d248a-168">Después de agregar el proveedor de datos leap motion al perfil del sistema de entrada, presione reproducir, mueva la mano delante del controlador leap motion y debería ver la representación conjunta de la mano.</span><span class="sxs-lookup"><span data-stu-id="d248a-168">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="d248a-169">Creación del proyecto</span><span class="sxs-lookup"><span data-stu-id="d248a-169">Building your project</span></span>
    - <span data-ttu-id="d248a-170">Vaya a **File > Build Configuración**</span><span class="sxs-lookup"><span data-stu-id="d248a-170">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="d248a-171">Solo se admiten compilaciones independientes si se usa el proveedor de datos Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-171">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="d248a-172">Para obtener instrucciones sobre cómo usar un casco Windows Mixed Reality para compilaciones independientes, consulte Building [and deploying MRTK to WMR Headsets (Standalone) (Compilación e implementación de MRTK en cascos WMR [independiente]).](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone)</span><span class="sxs-lookup"><span data-stu-id="d248a-172">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK to WMR Headsets (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-to-wmr-headsets-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="d248a-173">Obtención de las uniones de las manos</span><span class="sxs-lookup"><span data-stu-id="d248a-173">Getting the hand joints</span></span>

<span data-ttu-id="d248a-174">La obtención de uniones mediante el proveedor de datos Leap Motion es idéntica a la recuperación de la mano de una mano articulada de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d248a-174">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="d248a-175">Para obtener más información, vea [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="d248a-175">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="d248a-176">Con MRTK en una escena de Unity y el proveedor de datos Leap Motion agregado como proveedor de datos de entrada en el perfil del sistema de entrada, cree un objeto de juego vacío y adjunte el siguiente script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="d248a-176">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="d248a-177">Este script es un ejemplo sencillo de cómo recuperar la posición de la coyuntura de la mano de la mano de movimiento bisiesto.</span><span class="sxs-lookup"><span data-stu-id="d248a-177">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="d248a-178">Una esfera sigue a la mano leap izquierda, mientras que un cubo sigue a la mano leap derecha.</span><span class="sxs-lookup"><span data-stu-id="d248a-178">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

```c#
using Microsoft.MixedReality.Toolkit;
using Microsoft.MixedReality.Toolkit.Input;
using Microsoft.MixedReality.Toolkit.Utilities;
using System.Collections.Generic;
using UnityEngine;

public class LeapHandJoints : MonoBehaviour, IMixedRealityHandJointHandler
{
    private GameObject leftHandSphere;
    private GameObject rightHandCube;

    private void Start()
    {
        // Register the HandJointHandler as a global listener
        CoreServices.InputSystem.RegisterHandler<IMixedRealityHandJointHandler>(this);

        // Create a sphere to follow the left hand palm position
        leftHandSphere = GameObject.CreatePrimitive(PrimitiveType.Sphere);
        leftHandSphere.transform.localScale = Vector3.one * 0.03f;

        // Create a cube to follow the right hand palm position
        rightHandCube = GameObject.CreatePrimitive(PrimitiveType.Cube);
        rightHandCube.transform.localScale = Vector3.one * 0.03f;
    }

    public void OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == Handedness.Left)
        {
            Vector3 leftHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            leftHandSphere.transform.position = leftHandPalmPosition;
        }

        if (eventData.Handedness == Handedness.Right)
        {
            Vector3 rightHandPalmPosition = eventData.InputData[TrackedHandJoint.Palm].Position;
            rightHandCube.transform.position = rightHandPalmPosition;
        }
    }
```

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="d248a-179">Sugerencia de flujo de trabajo del editor de Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-179">Unity editor workflow tip</span></span>

<span data-ttu-id="d248a-180">El uso del proveedor de datos Leap Motion no requiere un casco de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="d248a-180">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="d248a-181">Los cambios en una aplicación MRTK se pueden probar en el editor con las manos Leap sin casco.</span><span class="sxs-lookup"><span data-stu-id="d248a-181">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="d248a-182">Las manos leap motion se mostrarán en el editor, sin un casco de realidad virtual conectado.</span><span class="sxs-lookup"><span data-stu-id="d248a-182">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="d248a-183">Si se establece en Casco, el controlador Leap Motion tendrá que mantener el control Leap Motion con una mano con la `LeapControllerOrientation` cámara orientada hacia delante. </span><span class="sxs-lookup"><span data-stu-id="d248a-183">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="d248a-184">Si la cámara se mueve mediante teclas WASD en el editor y es Casco, las manos `LeapControllerOrientation` no seguirán la cámara. </span><span class="sxs-lookup"><span data-stu-id="d248a-184">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="d248a-185">Las manos solo seguirán el movimiento de la cámara si un casco de realidad virtual está conectado mientras `LeapControllerOrientation` está establecido el **casco**.</span><span class="sxs-lookup"><span data-stu-id="d248a-185">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="d248a-186">Las manos bisiesta seguirán el movimiento de la cámara en el editor si `LeapControllerOrientation` está establecido en **Desk**.</span><span class="sxs-lookup"><span data-stu-id="d248a-186">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="d248a-187">Quitar Leap Motion del Project</span><span class="sxs-lookup"><span data-stu-id="d248a-187">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="d248a-188">Vaya a la página **Mixed Reality Toolkit** Leap Motion Separate Leap Motion Unity Modules  >  **(Módulos de** Unity de Leap Motion independientes de Leap  >  **Motion).**</span><span class="sxs-lookup"><span data-stu-id="d248a-188">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="d248a-189">Deje que Unity se actualice como referencias **en Microsoft.MixedReality.Toolkit. El archivo Providers.LeapMotion.asmdef** se modifica en este paso</span><span class="sxs-lookup"><span data-stu-id="d248a-189">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="d248a-190">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-190">Close Unity</span></span>
1. <span data-ttu-id="d248a-191">Cierre Visual Studio, si está abierto</span><span class="sxs-lookup"><span data-stu-id="d248a-191">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="d248a-192">Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.</span><span class="sxs-lookup"><span data-stu-id="d248a-192">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="d248a-193">Eliminación del **directorio UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="d248a-193">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="d248a-194">Eliminación **del directorio UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="d248a-194">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="d248a-195">Eliminación **del archivo UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="d248a-195">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="d248a-196">Volver a abrir Unity</span><span class="sxs-lookup"><span data-stu-id="d248a-196">Reopen Unity</span></span>

<span data-ttu-id="d248a-197">En Unity 2018.4, es posible que observe que los errores permanecen en la consola después de eliminar la biblioteca y los recursos principales de Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-197">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="d248a-198">Si se registran errores después de volver a abrir, reinicie Unity de nuevo.</span><span class="sxs-lookup"><span data-stu-id="d248a-198">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="d248a-199">Errores comunes</span><span class="sxs-lookup"><span data-stu-id="d248a-199">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="d248a-200">Leap Motion no se ha integrado con MRTK</span><span class="sxs-lookup"><span data-stu-id="d248a-200">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="d248a-201">Para probar si los módulos leap motion de Unity se han integrado con MRTK:</span><span class="sxs-lookup"><span data-stu-id="d248a-201">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="d248a-202">Vaya a Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status (Estado de **integración).**</span><span class="sxs-lookup"><span data-stu-id="d248a-202">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="d248a-203">Se mostrará una ventana emergente con un mensaje sobre si los módulos leap motion de Unity se han integrado o no con MRTK.</span><span class="sxs-lookup"><span data-stu-id="d248a-203">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="d248a-204">Si el mensaje indica que los recursos no se han integrado:</span><span class="sxs-lookup"><span data-stu-id="d248a-204">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="d248a-205">Asegúrese de que los módulos leap motion de Unity están en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d248a-205">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="d248a-206">Asegúrese de que se admite la versión agregada, consulte la tabla en la parte superior de la página para ver las versiones admitidas.</span><span class="sxs-lookup"><span data-stu-id="d248a-206">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="d248a-207">Pruebe **Mixed Reality Toolkit > Utilities > Leap Motion > integración de módulos leap motion de Unity**</span><span class="sxs-lookup"><span data-stu-id="d248a-207">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="d248a-208">Error al copiar el ensamblado HLAPI multijugador</span><span class="sxs-lookup"><span data-stu-id="d248a-208">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="d248a-209">Al importar los recursos principales de Unity De Leap Motion, este error podría registrarse:</span><span class="sxs-lookup"><span data-stu-id="d248a-209">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="d248a-210">**Solución**</span><span class="sxs-lookup"><span data-stu-id="d248a-210">**Solution**</span></span>

- <span data-ttu-id="d248a-211">Una solución a corto plazo es reiniciar Unity.</span><span class="sxs-lookup"><span data-stu-id="d248a-211">A short term solution is to restart Unity.</span></span> <span data-ttu-id="d248a-212">Consulte [el problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="d248a-212">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="d248a-213">Escena de ejemplo de leap motion</span><span class="sxs-lookup"><span data-stu-id="d248a-213">Leap Motion Example Scene</span></span>

<span data-ttu-id="d248a-214">En la escena de ejemplo se usa el perfil DefaultLeapMotionConfiguration y se determina si el proyecto de Unity se ha configurado correctamente para usar el proveedor de datos Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="d248a-214">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="d248a-215">La escena de ejemplo se encuentra en **Microsoft.MixedReality.Toolkit. Paquete** de ejemplos en **el directorio MRTK/Examples/Demos/HandTracking/.**</span><span class="sxs-lookup"><span data-stu-id="d248a-215">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d248a-216">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d248a-216">See also</span></span>

- [<span data-ttu-id="d248a-217">Proveedores de entrada</span><span class="sxs-lookup"><span data-stu-id="d248a-217">Input Providers</span></span>](../features/input/input-providers.md)
- [<span data-ttu-id="d248a-218">Seguimiento de manos</span><span class="sxs-lookup"><span data-stu-id="d248a-218">Hand Tracking</span></span>](../features/input/hand-tracking.md)
