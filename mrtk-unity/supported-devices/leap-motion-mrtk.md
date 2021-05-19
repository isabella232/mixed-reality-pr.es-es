---
title: MRTK de movimiento intercalar
description: Documentación que se debe configurar para Leap Motion
author: CDiaz-ms
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Leap Motion,
ms.openlocfilehash: 285328b1248f04504f30192f1294e9ae665b3fc9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145195"
---
# <a name="how-to-configure-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="fcd46-104">Configuración del seguimiento de manos de Leap Motion (by Ultraleap) en MRTK</span><span class="sxs-lookup"><span data-stu-id="fcd46-104">How to Configure Leap Motion (by Ultraleap) Hand Tracking in MRTK</span></span>

<span data-ttu-id="fcd46-105">Se [requiere un controlador leap motion](https://www.ultraleap.com/product/leap-motion-controller/) para usar este proveedor de datos.</span><span class="sxs-lookup"><span data-stu-id="fcd46-105">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

<span data-ttu-id="fcd46-106">El proveedor de datos Leap Motion permite el seguimiento de manos articulado para VR y podría ser útil para la creación rápida de prototipos en el editor.</span><span class="sxs-lookup"><span data-stu-id="fcd46-106">The Leap Motion Data Provider enables articulated hand tracking for VR and could be useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="fcd46-107">El proveedor de datos se puede configurar para usar el controlador leap motion montado en un casco o colocado en un escritorio cara arriba.</span><span class="sxs-lookup"><span data-stu-id="fcd46-107">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

![LeapMotionIntroGif](../images/cross-platform/leap-motion/LeapHandsGif3.gif)

<span data-ttu-id="fcd46-109">Este proveedor se puede usar en el editor y en el dispositivo en la plataforma independiente.</span><span class="sxs-lookup"><span data-stu-id="fcd46-109">This provider can be used in editor and on device while on the Standalone platform.</span></span>  <span data-ttu-id="fcd46-110">También se puede usar en el editor en la plataforma UWP, pero NO en una compilación de UWP.</span><span class="sxs-lookup"><span data-stu-id="fcd46-110">It can also be used in editor while on the UWP platform but NOT in a UWP build.</span></span>

|<span data-ttu-id="fcd46-111">Versiones admitidas de los módulos de Unity de Leap Motion</span><span class="sxs-lookup"><span data-stu-id="fcd46-111">Leap Motion Unity Modules Versions Supported</span></span>|
|---|
|<span data-ttu-id="fcd46-112">4.5.0</span><span class="sxs-lookup"><span data-stu-id="fcd46-112">4.5.0</span></span>|
|<span data-ttu-id="fcd46-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="fcd46-113">4.5.1</span></span>|

## <a name="using-leap-motion-by-ultraleap-hand-tracking-in-mrtk"></a><span data-ttu-id="fcd46-114">Uso del seguimiento manual de Leap Motion (by Ultraleap) en MRTK</span><span class="sxs-lookup"><span data-stu-id="fcd46-114">Using Leap Motion (by Ultraleap) hand tracking in MRTK</span></span>

1. <span data-ttu-id="fcd46-115">Importación de MRTK y los módulos leap motion de Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-115">Importing MRTK and the Leap Motion Unity Modules</span></span>
    - <span data-ttu-id="fcd46-116">Instale [el SDK de Leap Motion 4.0.0](https://developer.leapmotion.com/releases/?category=orion) si aún no está instalado</span><span class="sxs-lookup"><span data-stu-id="fcd46-116">Install the [Leap Motion SDK 4.0.0](https://developer.leapmotion.com/releases/?category=orion) if it is not already installed</span></span>
    - <span data-ttu-id="fcd46-117">Importe el **paquete Microsoft.MixedReality.Toolkit.Foundation** en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="fcd46-117">Import the **Microsoft.MixedReality.Toolkit.Foundation** package into the Unity project.</span></span>
    - <span data-ttu-id="fcd46-118">Descarga e importación de la versión más reciente de los módulos [de Unity leap motion](https://developer.leapmotion.com/unity) en el proyecto</span><span class="sxs-lookup"><span data-stu-id="fcd46-118">Download and import the latest version of the [Leap Motion Unity Modules](https://developer.leapmotion.com/unity) into the project</span></span>
        - <span data-ttu-id="fcd46-119">Importar solo el **paquete Principal** dentro de los módulos de Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-119">Only import the **Core** package within the Unity Modules</span></span>

1. <span data-ttu-id="fcd46-120">Integración de los módulos de Unity leap motion con MRTK</span><span class="sxs-lookup"><span data-stu-id="fcd46-120">Integrate the Leap Motion Unity Modules with MRTK</span></span>
    - <span data-ttu-id="fcd46-121">Una vez que los módulos de Unity estén en el proyecto, vaya a **Mixed Reality Toolkit**  >  **Leap Motion** Integrate Leap Motion Unity Modules (Integración de los módulos leap motion de  >  **Unity).**</span><span class="sxs-lookup"><span data-stu-id="fcd46-121">After the Unity Modules are in the project, navigate to **Mixed Reality Toolkit** > **Leap Motion** > **Integrate Leap Motion Unity Modules**</span></span>
    > [!NOTE]
    > <span data-ttu-id="fcd46-122">La integración de los módulos de Unity en MRTK agrega 10 definiciones de ensamblado al proyecto y agrega referencias a la definición del ensamblado **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.**</span><span class="sxs-lookup"><span data-stu-id="fcd46-122">Integrating the Unity Modules to MRTK adds 10 assembly definitions to the project and adds references to the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion** assembly definition.</span></span> <span data-ttu-id="fcd46-123">Asegúrese de que Visual Studio esté cerrado.</span><span class="sxs-lookup"><span data-stu-id="fcd46-123">Make sure Visual Studio is closed.</span></span>

     ![LeapMotionIntegration](../images/cross-platform/leap-motion/LeapMotionIntegrateMenu.png)

1. <span data-ttu-id="fcd46-125">Agregar el proveedor de datos Leap Motion</span><span class="sxs-lookup"><span data-stu-id="fcd46-125">Adding the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="fcd46-126">Creación de una escena de Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-126">Create a new Unity scene</span></span>
    - <span data-ttu-id="fcd46-127">Para agregar MRTK a la escena, vaya **a Mixed Reality Toolkit** Add to Scene and Configure (Agregar a la escena y  >  **configurar)**</span><span class="sxs-lookup"><span data-stu-id="fcd46-127">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>
    - <span data-ttu-id="fcd46-128">Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione **Copiar y** personalizar para clonar el perfil de realidad mixta predeterminado.</span><span class="sxs-lookup"><span data-stu-id="fcd46-128">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

    ![LeapMotionProfileClone](../images/cross-platform/CloneProfile.png)

    - <span data-ttu-id="fcd46-130">Selección del perfil **de configuración** de entrada</span><span class="sxs-lookup"><span data-stu-id="fcd46-130">Select the **Input** Configuration Profile</span></span>

    ![Perfil de configuración de entrada 1](../images/cross-platform/InputConfigurationProfile.png)

    - <span data-ttu-id="fcd46-132">Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.</span><span class="sxs-lookup"><span data-stu-id="fcd46-132">Select **Clone** in the input system profile to enable modification.</span></span>

    ![LeapMotionInputProfileClone](../images/cross-platform/CloneInputSystemProfile.png)

    - <span data-ttu-id="fcd46-134">Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.</span><span class="sxs-lookup"><span data-stu-id="fcd46-134">Open the **Input Data Providers** section, select **Add Data Provider** at the top, a new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="fcd46-135">Abra el nuevo proveedor de datos y establezca **el** tipo en **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager.**</span><span class="sxs-lookup"><span data-stu-id="fcd46-135">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.LeapMotion.Input > LeapMotionDeviceManager**</span></span>

    ![Leap Add Data Provider](../images/cross-platform/leap-motion/LeapAddDataProvider.png)

    - <span data-ttu-id="fcd46-137">Seleccione **Clonar** para cambiar la configuración predeterminada de Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-137">Select **Clone** to change the default Leap Motion settings.</span></span>

    ![LeapDataProviderPreClone](../images/cross-platform/leap-motion/LeapMotionDeviceManagerProfile.png)

    - <span data-ttu-id="fcd46-139">El proveedor de datos leap motion contiene `LeapControllerOrientation` la propiedad que es la ubicación del controlador de movimiento leap.</span><span class="sxs-lookup"><span data-stu-id="fcd46-139">The Leap Motion Data Provider contains the `LeapControllerOrientation` property which is the location of the Leap Motion Controller.</span></span> <span data-ttu-id="fcd46-140">`LeapControllerOrientation.Headset` indica que el controlador está montado en un casco.</span><span class="sxs-lookup"><span data-stu-id="fcd46-140">`LeapControllerOrientation.Headset` indicates the controller is mounted on a headset.</span></span> <span data-ttu-id="fcd46-141">`LeapControllerOrientation.Desk` indica que el controlador se coloca plano sobre el escritorio.</span><span class="sxs-lookup"><span data-stu-id="fcd46-141">`LeapControllerOrientation.Desk` indicates the controller is placed flat on desk.</span></span> <span data-ttu-id="fcd46-142">El valor predeterminado se establece en `LeapControllerOrientation.Headset` .</span><span class="sxs-lookup"><span data-stu-id="fcd46-142">The default value is set to `LeapControllerOrientation.Headset`.</span></span>
    - <span data-ttu-id="fcd46-143">Cada orientación del controlador contiene propiedades de desplazamiento:</span><span class="sxs-lookup"><span data-stu-id="fcd46-143">Each controller orientation contains offset properties:</span></span>
      - <span data-ttu-id="fcd46-144">Las **propiedades de desplazamiento** de orientación del casco reflejan las propiedades de desplazamiento en el componente LeapXRServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="fcd46-144">The **Headset** orientation offset properties mirror the offset properties in the LeapXRServiceProvider component.</span></span>  <span data-ttu-id="fcd46-145">tiene `LeapVRDeviceOffsetMode` tres opciones: Predeterminada, Desplazamiento manual de la cabeza y Transformación.</span><span class="sxs-lookup"><span data-stu-id="fcd46-145">The `LeapVRDeviceOffsetMode` has three options: Default, Manual Head Offset and Transform.</span></span>  <span data-ttu-id="fcd46-146">Si el modo de desplazamiento es Predeterminado, no se aplicará un desplazamiento al controlador leap motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-146">If the offset mode is Default, then an offset will not be applied to the Leap Motion Controller.</span></span>  <span data-ttu-id="fcd46-147">El modo desplazamiento manual de la cabeza permite la modificación de tres propiedades: `LeapVRDeviceOffsetY` y `LeapVRDeviceOffsetZ` `LeapVRDeviceTiltX` .</span><span class="sxs-lookup"><span data-stu-id="fcd46-147">The Manual Head Offset mode allows for the modification of three properties: `LeapVRDeviceOffsetY`, `LeapVRDeviceOffsetZ` and `LeapVRDeviceTiltX`.</span></span>  <span data-ttu-id="fcd46-148">A continuación, los valores de propiedad de desplazamiento del eje se aplican a la ubicación predeterminada del controlador.</span><span class="sxs-lookup"><span data-stu-id="fcd46-148">The axis offset property values are then applied to default controller placement.</span></span>  <span data-ttu-id="fcd46-149">El modo de desplazamiento Transformar contiene la `LeapVRDeviceOrigin` propiedad Transformar que especifica un nuevo origen para el controlador leap motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-149">The Transform offset mode contains the `LeapVRDeviceOrigin` Transform property which specifies a new origin for the Leap Motion Controller.</span></span>
      - <span data-ttu-id="fcd46-150">La **orientación desk** contiene la propiedad que define la posición `LeapControllerOffset` delimitadora de las manos bisiesta del escritorio.</span><span class="sxs-lookup"><span data-stu-id="fcd46-150">The **Desk** orientation contains the `LeapControllerOffset` property which defines the anchor position of the desk leap hands.</span></span>  <span data-ttu-id="fcd46-151">El desplazamiento se calcula en relación con la posición de la cámara principal y el valor predeterminado es (0,-0,2, 0,35) para asegurarse de que las manos aparecen delante y a la vista de la cámara.</span><span class="sxs-lookup"><span data-stu-id="fcd46-151">The offset is calculated relative to the main camera position and the default value is (0,-0.2, 0.35) to make sure the hands appear in front and in view of the camera.</span></span>

        > [!NOTE]
        > <span data-ttu-id="fcd46-152">Las propiedades de desplazamiento del perfil se aplican una vez cuando se inicia la aplicación.</span><span class="sxs-lookup"><span data-stu-id="fcd46-152">The offset properties in the profile are applied once when the application starts.</span></span>  <span data-ttu-id="fcd46-153">Para modificar los valores durante el tiempo de ejecución, obtenga el proveedor del servicio Leap Motion en la página Leap Motion Administrador de dispositivos:</span><span class="sxs-lookup"><span data-stu-id="fcd46-153">To modify the values during runtime, get the Leap Motion Service Provider from the Leap Motion Device Manager:</span></span>
        >```
        >LeapMotionDeviceManager leapMotionDeviceManager = CoreServices.GetInputSystemDataProvider<LeapMotionDeviceManager>();
        >LeapXRServiceProvider leapXRServiceProvider = leapMotionDeviceManager.LeapMotionServiceProvider as LeapXRServiceProvider; 
        >```

    - <span data-ttu-id="fcd46-154">`EnterPinchDistance` y `ExitPinchDistance` son los umbrales de distancia para la detección de gestos de pulsar en el aire o desenlazador.</span><span class="sxs-lookup"><span data-stu-id="fcd46-154">`EnterPinchDistance` and `ExitPinchDistance` are the distance thresholds for pinch/air tap gesture detection.</span></span>  <span data-ttu-id="fcd46-155">El gesto de acercar se calcula midiendo la distancia entre la punta del dedo índice y la punta del dedo.</span><span class="sxs-lookup"><span data-stu-id="fcd46-155">The pinch gesture is calculated by measuring the distance between the index finger tip and the thumb tip.</span></span>  <span data-ttu-id="fcd46-156">Para generar un evento de entrada hacia abajo, el valor `EnterPinchDistance` predeterminado se establece en 0,02.</span><span class="sxs-lookup"><span data-stu-id="fcd46-156">To raise an on input down event, the default `EnterPinchDistance` is set to 0.02.</span></span>  <span data-ttu-id="fcd46-157">Para generar un evento de entrada arriba (salir de la acción de acercar), la distancia predeterminada entre la punta del dedo índice y la punta del control es 0,05.</span><span class="sxs-lookup"><span data-stu-id="fcd46-157">To raise an on input up event (exiting the pinch), the default distance between the index finger tip and the thumb tip is 0.05.</span></span>

    <span data-ttu-id="fcd46-158">`LeapControllerOrientation`: casco (valor predeterminado)</span><span class="sxs-lookup"><span data-stu-id="fcd46-158">`LeapControllerOrientation`: Headset (Default)</span></span> |  <span data-ttu-id="fcd46-159">`LeapControllerOrientation`: Desk</span><span class="sxs-lookup"><span data-stu-id="fcd46-159">`LeapControllerOrientation`: Desk</span></span>
    :-------------------------:|:-------------------------:
    ![LeapHeadsetGif](../images/cross-platform/leap-motion/LeapHeadsetOrientationExampleMetacarpals.gif)  |  ![LeapDeskGif](../images/cross-platform/leap-motion/LeapDeskOrientationExampleMetacarpals.gif)
    ![LeapHeadsetInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerHeadset.png) |     ![LeapDeskInspector](../images/cross-platform/leap-motion/LeapMotionDeviceManagerDesk.png)

1. <span data-ttu-id="fcd46-164">Prueba del proveedor de datos Leap Motion</span><span class="sxs-lookup"><span data-stu-id="fcd46-164">Testing the Leap Motion Data Provider</span></span>
    - <span data-ttu-id="fcd46-165">Una vez agregado el proveedor de datos leap motion al perfil del sistema de entrada, presione play, mueva la mano delante del leap motion controller y debería ver la representación conjunta de la mano.</span><span class="sxs-lookup"><span data-stu-id="fcd46-165">After Leap Motion Data Provider has been added to the input system profile, press play, move your hand in front of the Leap Motion Controller and you should see the joint representation of the hand.</span></span>

1. <span data-ttu-id="fcd46-166">Creación del proyecto</span><span class="sxs-lookup"><span data-stu-id="fcd46-166">Building your project</span></span>
    - <span data-ttu-id="fcd46-167">Vaya a **File > Build Settings (Configuración > compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="fcd46-167">Navigate to **File > Build Settings**</span></span>
    - <span data-ttu-id="fcd46-168">Solo se admiten compilaciones independientes si se usa el proveedor de datos Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-168">Only Standalone builds are supported if using the Leap Motion Data Provider.</span></span>
    - <span data-ttu-id="fcd46-169">Para obtener instrucciones sobre cómo usar un casco Windows Mixed Reality para compilaciones independientes, consulte Compilación e implementación [de MRTK (independiente).](wmr-mrtk.md#building-and-deploying-mrtk-standalone)</span><span class="sxs-lookup"><span data-stu-id="fcd46-169">For instructions on how to use a Windows Mixed Reality headset for Standalone builds, see [Building and deploying MRTK (Standalone)](wmr-mrtk.md#building-and-deploying-mrtk-standalone).</span></span>

## <a name="getting-the-hand-joints"></a><span data-ttu-id="fcd46-170">Obtención de las uniones de mano</span><span class="sxs-lookup"><span data-stu-id="fcd46-170">Getting the hand joints</span></span>

<span data-ttu-id="fcd46-171">La obtención de uniones mediante el proveedor de datos Leap Motion es idéntica a la recuperación conjunta manual para una mano articulada de MRTK.</span><span class="sxs-lookup"><span data-stu-id="fcd46-171">Getting joints using the Leap Motion Data Provider is identical to hand joint retrieval for an MRTK Articulated Hand.</span></span>  <span data-ttu-id="fcd46-172">Para obtener más información, vea [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span><span class="sxs-lookup"><span data-stu-id="fcd46-172">For more information, see [Hand Tracking](../features/input/hand-tracking.md#polling-joint-pose-from-handjointutils).</span></span>

<span data-ttu-id="fcd46-173">Con MRTK en una escena de Unity y el proveedor de datos Leap Motion agregado como proveedor de datos de entrada en el perfil del sistema de entrada, cree un objeto de juego vacío y adjunte el siguiente script de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="fcd46-173">With MRTK in a unity scene and the Leap Motion Data Provider added as an Input Data Provider in the Input System profile, create an empty game object and attach the following example script.</span></span>

<span data-ttu-id="fcd46-174">Este script es un ejemplo sencillo de cómo recuperar la posición de la coyuntura de la mano de la mano de movimiento bisiesto.</span><span class="sxs-lookup"><span data-stu-id="fcd46-174">This script is a simple example of how to retrieve the pose of the palm joint in a Leap Motion Hand.</span></span>  <span data-ttu-id="fcd46-175">Una esfera sigue a la mano leap izquierda, mientras que un cubo sigue a la mano leap derecha.</span><span class="sxs-lookup"><span data-stu-id="fcd46-175">A sphere follows the left Leap hand while a cube follows the right Leap hand.</span></span>

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

## <a name="unity-editor-workflow-tip"></a><span data-ttu-id="fcd46-176">Sugerencia de flujo de trabajo del editor de Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-176">Unity editor workflow tip</span></span>

<span data-ttu-id="fcd46-177">El uso del proveedor de datos Leap Motion no requiere un casco de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="fcd46-177">Using the Leap Motion Data Provider does not require a VR headset.</span></span>  <span data-ttu-id="fcd46-178">Los cambios en una aplicación MRTK se pueden probar en el editor con las manos leap sin casco.</span><span class="sxs-lookup"><span data-stu-id="fcd46-178">Changes to an MRTK app can be tested in the editor with the Leap hands without a headset.</span></span>

<span data-ttu-id="fcd46-179">Las manos leap motion se mostrarán en el editor, sin un casco de realidad virtual conectado.</span><span class="sxs-lookup"><span data-stu-id="fcd46-179">The Leap Motion Hands will show up in the editor, without a VR headset plugged in.</span></span>  <span data-ttu-id="fcd46-180">Si está establecido en Casco, el controlador Leap Motion tendrá que mantener el control Leap Motion con una mano con la `LeapControllerOrientation` cámara orientada hacia delante. </span><span class="sxs-lookup"><span data-stu-id="fcd46-180">If the `LeapControllerOrientation` is set to **Headset**, then the Leap Motion controller will need to be held up by one hand with the camera facing forward.</span></span>

> [!NOTE]
> <span data-ttu-id="fcd46-181">Si la cámara se mueve mediante teclas WASD en el editor y es Casco , las manos `LeapControllerOrientation` no seguirán a la cámara. </span><span class="sxs-lookup"><span data-stu-id="fcd46-181">If the camera is moved using WASD keys in the editor and the `LeapControllerOrientation` is **Headset**, the hands will not follow the camera.</span></span> <span data-ttu-id="fcd46-182">Las manos solo seguirán el movimiento de la cámara si un casco vr está conectado mientras `LeapControllerOrientation` está establecido el **casco**.</span><span class="sxs-lookup"><span data-stu-id="fcd46-182">The hands will only follow camera movement if a VR headset is plugged in while the `LeapControllerOrientation` is set **Headset**.</span></span>  <span data-ttu-id="fcd46-183">Las manos bisiesta seguirán el movimiento de la cámara en el editor si `LeapControllerOrientation` está establecido en **Desk**.</span><span class="sxs-lookup"><span data-stu-id="fcd46-183">The Leap hands will follow the camera movement in the editor if the `LeapControllerOrientation` is set to **Desk**.</span></span>

## <a name="removing-leap-motion-from-the-project"></a><span data-ttu-id="fcd46-184">Quitar Leap Motion del proyecto</span><span class="sxs-lookup"><span data-stu-id="fcd46-184">Removing Leap Motion from the Project</span></span>

1. <span data-ttu-id="fcd46-185">Vaya a los **módulos de Unity leap** motion independientes  >  **Mixed Reality Toolkit Leap Motion**  >  </span><span class="sxs-lookup"><span data-stu-id="fcd46-185">Navigate to the **Mixed Reality Toolkit** > **Leap Motion** > **Separate Leap Motion Unity Modules**</span></span>
    - <span data-ttu-id="fcd46-186">Permitir que Unity se actualice como referencias en el **archivo Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** se modifica en este paso.</span><span class="sxs-lookup"><span data-stu-id="fcd46-186">Let Unity refresh as references in the **Microsoft.MixedReality.Toolkit.Providers.LeapMotion.asmdef** file are modified in this step</span></span>
1. <span data-ttu-id="fcd46-187">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-187">Close Unity</span></span>
1. <span data-ttu-id="fcd46-188">Cierre Visual Studio, si está abierto</span><span class="sxs-lookup"><span data-stu-id="fcd46-188">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="fcd46-189">Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.</span><span class="sxs-lookup"><span data-stu-id="fcd46-189">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
    - <span data-ttu-id="fcd46-190">Eliminación del **directorio UnityProjectName/Library**</span><span class="sxs-lookup"><span data-stu-id="fcd46-190">Delete the **UnityProjectName/Library** directory</span></span>
    - <span data-ttu-id="fcd46-191">Eliminación **del directorio UnityProjectName/Assets/Plugins/LeapMotion**</span><span class="sxs-lookup"><span data-stu-id="fcd46-191">Delete the **UnityProjectName/Assets/Plugins/LeapMotion** directory</span></span>
    - <span data-ttu-id="fcd46-192">Eliminación **del archivo UnityProjectName/Assets/Plugins/LeapMotion.meta**</span><span class="sxs-lookup"><span data-stu-id="fcd46-192">Delete the **UnityProjectName/Assets/Plugins/LeapMotion.meta** file</span></span>
1. <span data-ttu-id="fcd46-193">Volver a abrir Unity</span><span class="sxs-lookup"><span data-stu-id="fcd46-193">Reopen Unity</span></span>

<span data-ttu-id="fcd46-194">En Unity 2018.4, es posible que observe que los errores permanecen en la consola después de eliminar la biblioteca y los recursos principales de Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-194">In Unity 2018.4, you might notice that errors still remain in the console after deleting the Library and the Leap Motion Core Assets.</span></span>
<span data-ttu-id="fcd46-195">Si se registran errores después de volver a abrir, reinicie Unity de nuevo.</span><span class="sxs-lookup"><span data-stu-id="fcd46-195">If errors are logged after reopening, restart Unity again.</span></span>

## <a name="common-errors"></a><span data-ttu-id="fcd46-196">Errores comunes</span><span class="sxs-lookup"><span data-stu-id="fcd46-196">Common Errors</span></span>

### <a name="leap-motion-has-not-integrated-with-mrtk"></a><span data-ttu-id="fcd46-197">Leap Motion no se ha integrado con MRTK</span><span class="sxs-lookup"><span data-stu-id="fcd46-197">Leap Motion has not integrated with MRTK</span></span>

<span data-ttu-id="fcd46-198">Para probar si los módulos de Unity leap motion se han integrado con MRTK:</span><span class="sxs-lookup"><span data-stu-id="fcd46-198">To test if the Leap Motion Unity Modules have integrated with MRTK:</span></span>

- <span data-ttu-id="fcd46-199">Vaya a Mixed Reality **Toolkit > Utilities > Leap Motion > Estado de integración.**</span><span class="sxs-lookup"><span data-stu-id="fcd46-199">Navigate to **Mixed Reality Toolkit > Utilities > Leap Motion > Check Integration Status**</span></span>
  - <span data-ttu-id="fcd46-200">Se mostrará una ventana emergente con un mensaje sobre si los módulos de Unity leap motion se han integrado con MRTK o no.</span><span class="sxs-lookup"><span data-stu-id="fcd46-200">This will display a pop up window with a message about whether or not the Leap Motion Unity Modules have integrated with MRTK.</span></span>
- <span data-ttu-id="fcd46-201">Si el mensaje indica que los recursos no se han integrado:</span><span class="sxs-lookup"><span data-stu-id="fcd46-201">If the message says that the assets have not been integrated:</span></span>
  - <span data-ttu-id="fcd46-202">Asegúrese de que los módulos leap motion de Unity están en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="fcd46-202">Make sure the Leap Motion Unity Modules are in the project</span></span>
  - <span data-ttu-id="fcd46-203">Asegúrese de que se admite la versión agregada, consulte la tabla en la parte superior de la página para ver las versiones admitidas.</span><span class="sxs-lookup"><span data-stu-id="fcd46-203">Make sure that the version added is supported, see the table at the top of the page for versions supported.</span></span>
  - <span data-ttu-id="fcd46-204">Pruebe **Mixed Reality Toolkit > Utilities > Leap Motion > integrar módulos de Unity leap motion**</span><span class="sxs-lookup"><span data-stu-id="fcd46-204">Try **Mixed Reality Toolkit > Utilities > Leap Motion > Integrate Leap Motion Unity Modules**</span></span>

### <a name="copying-assembly-multiplayer-hlapi-failed"></a><span data-ttu-id="fcd46-205">Error al copiar HLAPI multijugador de ensamblado</span><span class="sxs-lookup"><span data-stu-id="fcd46-205">Copying assembly Multiplayer HLAPI failed</span></span>

<span data-ttu-id="fcd46-206">Al importar los recursos principales de Unity De Leap Motion, este error podría registrarse:</span><span class="sxs-lookup"><span data-stu-id="fcd46-206">On import of the Leap Motion Unity Core Assets this error might be logged:</span></span>

```
Copying assembly from 'Temp/com.unity.multiplayer-hlapi.Runtime.dll' to 'Library/ScriptAssemblies/com.unity.multiplayer-hlapi.Runtime.dll' failed
```

<span data-ttu-id="fcd46-207">**Solución**</span><span class="sxs-lookup"><span data-stu-id="fcd46-207">**Solution**</span></span>

- <span data-ttu-id="fcd46-208">Una solución a corto plazo es reiniciar Unity.</span><span class="sxs-lookup"><span data-stu-id="fcd46-208">A short term solution is to restart Unity.</span></span> <span data-ttu-id="fcd46-209">Consulte [el problema 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="fcd46-209">See [Issue 7761](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7761) for more information.</span></span>

## <a name="leap-motion-example-scene"></a><span data-ttu-id="fcd46-210">Escena de ejemplo de leap motion</span><span class="sxs-lookup"><span data-stu-id="fcd46-210">Leap Motion Example Scene</span></span>

<span data-ttu-id="fcd46-211">En la escena de ejemplo se usa el perfil DefaultLeapMotionConfiguration y se determina si el proyecto de Unity se ha configurado correctamente para usar el proveedor de datos Leap Motion.</span><span class="sxs-lookup"><span data-stu-id="fcd46-211">The example scene uses the DefaultLeapMotionConfiguration profile and determines if the Unity project has been configured correctly to use the Leap Motion Data Provider.</span></span>

<span data-ttu-id="fcd46-212">La escena de ejemplo se encuentra en el **paquete Microsoft.MixedReality.Toolkit.Examples** del **directorio MRTK/Examples/Demos/HandTracking/.**</span><span class="sxs-lookup"><span data-stu-id="fcd46-212">The example scene is contained in the **Microsoft.MixedReality.Toolkit.Examples** package in the **MRTK/Examples/Demos/HandTracking/** directory.</span></span>  

## <a name="see-also"></a><span data-ttu-id="fcd46-213">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fcd46-213">See also</span></span>

<span data-ttu-id="fcd46-214">-[Proveedores de entrada](../features/input/input-providers.md) 
- [Seguimiento de manos](../features/input/hand-tracking.md)</span><span class="sxs-lookup"><span data-stu-id="fcd46-214">-[Input Providers](../features/input/input-providers.md)
-[Hand Tracking](../features/input/hand-tracking.md)</span></span>
