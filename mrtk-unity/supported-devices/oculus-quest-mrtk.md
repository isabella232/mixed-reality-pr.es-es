---
title: Oculus Quest MRTK
description: Documentación que se debe configurar para Oculus Quest en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Oculus Unity,
ms.openlocfilehash: c0eccd0b366d39529eafc51d23031fc30144b1ae
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143967"
---
# <a name="how-to-configure-oculus-quest-in-mrtk-using-the-xr-sdk-pipeline"></a><span data-ttu-id="73aa0-104">Configuración de Oculus Quest en MRTK mediante la canalización del SDK de XR</span><span class="sxs-lookup"><span data-stu-id="73aa0-104">How to configure Oculus Quest in MRTK using the XR SDK pipeline</span></span>

<span data-ttu-id="73aa0-105">Se [requiere una misión de Oculus.](https://www.oculus.com/quest/)</span><span class="sxs-lookup"><span data-stu-id="73aa0-105">A [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="73aa0-106">La compatibilidad de MRTK con Oculus Unity se realiza a través de dos orígenes diferentes, la canalización XR de Unity y el paquete de Unity de integración de Oculus.</span><span class="sxs-lookup"><span data-stu-id="73aa0-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="73aa0-107">El **proveedor de datos Oculus XRSDK** permite el uso de ambos orígenes y debe usarse para usar MRTK en Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="73aa0-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to use MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="73aa0-108">La [canalización XR de Unity permite](https://docs.unity3d.com/Manual/XR.html) el uso de controladores Oculus Touch y el seguimiento de la cabeza con Oculus Raid.</span><span class="sxs-lookup"><span data-stu-id="73aa0-108">The [Unity's XR Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="73aa0-109">Esta canalización es el estándar para desarrollar aplicaciones XR en Unity 2019.3 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="73aa0-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="73aa0-110">Para usar esta canalización, asegúrese de usar **Unity 2019.3 o una versión más reciente.**</span><span class="sxs-lookup"><span data-stu-id="73aa0-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span>

<span data-ttu-id="73aa0-111">El paquete de Unity de integración [de Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite el uso del seguimiento **manual** con Oculus Unity.</span><span class="sxs-lookup"><span data-stu-id="73aa0-111">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span>
<span data-ttu-id="73aa0-112">Este proveedor  de datos NO usa la canalización **XR** de Unity ni la canalización **XR** heredada, pero dado que los controladores y el seguimiento hacia la cabeza se controlan mediante la canalización XR de Unity, se deben seguir los pasos descritos en Configuración del proyecto para la canalización de **Oculus para** asegurarse de que usa la canalización de **XR** y no la canalización **XR** heredada que se va a dejar en desuso.</span><span class="sxs-lookup"><span data-stu-id="73aa0-112">This data provider does **NOT** use Unity's **XR Pipeline** or **Legacy XR Pipeline**, but because controllers and headtracking are handled by the Unity's XR Pipeline, the steps in **Setting up project for the Oculus Quest** must be followed to ensure that you are using the **XR Pipeline** and not the to-be-deprecated **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="73aa0-113">Configuración del proyecto para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="73aa0-113">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="73aa0-114">Siga [estos pasos](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para asegurarse de que el proyecto está listo para implementarse en Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="73aa0-114">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="73aa0-115">Asegúrese de [que el modo de](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) desarrollador está habilitado en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="73aa0-115">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="73aa0-116">La instalación de los controladores de ADB de Oculus es opcional.</span><span class="sxs-lookup"><span data-stu-id="73aa0-116">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-pipeline-for-oculus-quest"></a><span data-ttu-id="73aa0-117">Configuración de la canalización de XR para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="73aa0-117">Setting up the XR Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="73aa0-118">Asegúrese de que **el complemento Oculus XR** está instalado en **La ventana --> Administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="73aa0-118">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Paquete del complemento XR de Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="73aa0-120">Asegúrese de que el proveedor de complementos de Oculus está incluido en el proyecto; para ello, vaya a Editar la configuración del proyecto **--> --> Administración** de complementos XR --> Proveedores de complementos.</span><span class="sxs-lookup"><span data-stu-id="73aa0-120">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Proveedor de complementos de Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="73aa0-122">Configuración del paquete de Unity de integración de Oculus para habilitar el seguimiento a mano</span><span class="sxs-lookup"><span data-stu-id="73aa0-122">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="73aa0-123">Descargue e importe [Oculus Integration desde](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) el Almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="73aa0-123">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="73aa0-124">La versión más reciente probada para funcionar es la 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="73aa0-124">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="73aa0-125">Las versiones anteriores se pueden encontrar en este [archivo](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span><span class="sxs-lookup"><span data-stu-id="73aa0-125">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/)</span></span>

1. <span data-ttu-id="73aa0-126">Vaya a Mixed Reality Toolkit > Utilities > Oculus > integrate Oculus Integration Unity Modules (Integrar módulos de Unity de integración de Oculus).</span><span class="sxs-lookup"><span data-stu-id="73aa0-126">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="73aa0-127">Al hacerlo, se actualizarán las definiciones de asmdefs con las definiciones y las referencias necesarias para que el código de Oculus Quest pertinente funcione.</span><span class="sxs-lookup"><span data-stu-id="73aa0-127">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="73aa0-128">También actualizará el archivo csc para filtrar las advertencias obsoletas producidas por los recursos de integración de Oculus.</span><span class="sxs-lookup"><span data-stu-id="73aa0-128">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="73aa0-129">El repositorio MRTK contiene un archivo csc que convierte advertencias en errores, esta conversión detiene el proceso de MRTK-Quest configuración.</span><span class="sxs-lookup"><span data-stu-id="73aa0-129">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Asmdef de integración de Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="73aa0-131">En la carpeta Oculus importada (debe encontrarse en Assets/Oculus), hay un objeto que puede incluir scripts denominado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="73aa0-131">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="73aa0-132">En ese archivo de configuración, debe establecer HandTrackingSupport en "Controladores y manos".</span><span class="sxs-lookup"><span data-stu-id="73aa0-132">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integración de Oculus y manos](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="73aa0-134">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="73aa0-134">Setting up the scene</span></span>

1. <span data-ttu-id="73aa0-135">Cree una nueva escena de Unity o abra una escena preexistida como HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="73aa0-135">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples</span></span>
1. <span data-ttu-id="73aa0-136">Para agregar MRTK a la escena, vaya a **Mixed Reality Toolkit** Add to Scene and Configure (Agregar a la escena y  >  **configurar)**</span><span class="sxs-lookup"><span data-stu-id="73aa0-136">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="73aa0-137">Uso del proveedor de datos del SDK de Oculus XR</span><span class="sxs-lookup"><span data-stu-id="73aa0-137">Using the Oculus XR SDK Data Provider</span></span>

1. <span data-ttu-id="73aa0-138">Configuración del perfil para usar el proveedor de datos del **SDK de Oculus XR**</span><span class="sxs-lookup"><span data-stu-id="73aa0-138">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="73aa0-139">Si no pretende modificar los perfiles de configuración</span><span class="sxs-lookup"><span data-stu-id="73aa0-139">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="73aa0-140">Cambie el perfil a DefaultXRSDKConfigurationProfile y vaya a [Compilación e implementación del proyecto en Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="73aa0-140">Change your profile to DefaultXRSDKConfigurationProfile and go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span></span>

    - <span data-ttu-id="73aa0-141">De lo contrario, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="73aa0-141">Otherwise follow the following:</span></span>
        - <span data-ttu-id="73aa0-142">Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione **Copiar y** personalizar para clonar el perfil de realidad mixta predeterminado.</span><span class="sxs-lookup"><span data-stu-id="73aa0-142">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="73aa0-144">Selección del perfil **de configuración** de entrada</span><span class="sxs-lookup"><span data-stu-id="73aa0-144">Select the **Input** Configuration Profile</span></span>

        ![Perfil de configuración de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="73aa0-146">Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.</span><span class="sxs-lookup"><span data-stu-id="73aa0-146">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil del sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="73aa0-148">Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.</span><span class="sxs-lookup"><span data-stu-id="73aa0-148">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="73aa0-149">Abra el nuevo proveedor de datos y establezca **El** tipo en **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="73aa0-149">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**</span></span>

        ![Agregar proveedor de datos XRSDK de Oculus](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. <span data-ttu-id="73aa0-151">El proveedor de datos del SDK de Oculus XR incluye un prefab de cámara OVR que configura automáticamente el proyecto con un equipo de cámara OVR y las manos de OVR para enrutar correctamente la entrada.</span><span class="sxs-lookup"><span data-stu-id="73aa0-151">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="73aa0-152">La adición manual de un dispositivo de cámara OVR a la escena requerirá la configuración manual de la configuración y la entrada.</span><span class="sxs-lookup"><span data-stu-id="73aa0-152">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="73aa0-153">Compilación e implementación del proyecto en Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="73aa0-153">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="73aa0-154">Conecte su Oculus Quest a través de un cable USB 3.0 -> USB C</span><span class="sxs-lookup"><span data-stu-id="73aa0-154">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="73aa0-155">Vaya a **File > Build Settings (Configuración > compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="73aa0-155">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="73aa0-156">Cambio de la implementación a **Android**</span><span class="sxs-lookup"><span data-stu-id="73aa0-156">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="73aa0-157">Asegúrese de que Oculus Quest está seleccionado como el dispositivo de ejecución aplicable.</span><span class="sxs-lookup"><span data-stu-id="73aa0-157">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="73aa0-159">Seleccione Compilar y ejecutar.</span><span class="sxs-lookup"><span data-stu-id="73aa0-159">Select Build and Run</span></span>
    - <span data-ttu-id="73aa0-160">Es probable que se encuentre con el siguiente conjunto de errores de compilación al seleccionar *Compilar y ejecutar* la primera vez.</span><span class="sxs-lookup"><span data-stu-id="73aa0-160">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="73aa0-161">Debería poder realizar la implementación correctamente al seleccionar Compilar *y ejecutar de* nuevo.</span><span class="sxs-lookup"><span data-stu-id="73aa0-161">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Errores de compilación esperados de Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="73aa0-163">Acepte el _símbolo del sistema Permitir depuración USB_ desde dentro de la misión.</span><span class="sxs-lookup"><span data-stu-id="73aa0-163">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="73aa0-164">Ver la escena dentro de Oculus Scene</span><span class="sxs-lookup"><span data-stu-id="73aa0-164">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="73aa0-165">Quitar la integración de Oculus del proyecto</span><span class="sxs-lookup"><span data-stu-id="73aa0-165">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="73aa0-166">Vaya a Mixed Reality Toolkit > Oculus > Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="73aa0-166">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="73aa0-167">Deje que Unity se actualice como referencias en Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef y se modifican otros archivos en este paso.</span><span class="sxs-lookup"><span data-stu-id="73aa0-167">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="73aa0-168">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="73aa0-168">Close Unity</span></span>
1. <span data-ttu-id="73aa0-169">Cierre Visual Studio, si está abierto</span><span class="sxs-lookup"><span data-stu-id="73aa0-169">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="73aa0-170">Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.</span><span class="sxs-lookup"><span data-stu-id="73aa0-170">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="73aa0-171">Eliminación del directorio UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="73aa0-171">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="73aa0-172">Eliminación del directorio UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="73aa0-172">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="73aa0-173">Eliminación del archivo UnityProjectName/Assets/Oculus.meta</span><span class="sxs-lookup"><span data-stu-id="73aa0-173">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="73aa0-174">Volver a abrir Unity</span><span class="sxs-lookup"><span data-stu-id="73aa0-174">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="73aa0-175">Errores comunes</span><span class="sxs-lookup"><span data-stu-id="73aa0-175">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="73aa0-176">Misión no reconocida por Unity</span><span class="sxs-lookup"><span data-stu-id="73aa0-176">Quest not recognized by Unity</span></span>

<span data-ttu-id="73aa0-177">Asegúrese de que las rutas de acceso de Android están configuradas correctamente.</span><span class="sxs-lookup"><span data-stu-id="73aa0-177">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="73aa0-178">Si sigue teniendo problemas, siga esta [guía.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="73aa0-178">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="73aa0-179">**Editar > preferencias > herramientas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="73aa0-179">**Edit > Preferences > External Tools > Android**</span></span>

![Configuración de herramientas de Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
