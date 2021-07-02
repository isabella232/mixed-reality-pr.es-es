---
title: Implementación en Oculus Quest
description: Documentación que se debe configurar para Oculus Quest en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Oculus HoloLens 2
ms.openlocfilehash: d910f26374b21be26377bd40b9be0d45872e007a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177457"
---
# <a name="deploying-to-oculus-quest"></a><span data-ttu-id="697cf-104">Implementación en Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="697cf-104">Deploying to Oculus Quest</span></span>

<span data-ttu-id="697cf-105">Se [requiere una misión de Oculus.](https://www.oculus.com/quest/)</span><span class="sxs-lookup"><span data-stu-id="697cf-105">An [Oculus Quest](https://www.oculus.com/quest/) is required.</span></span>

<span data-ttu-id="697cf-106">La compatibilidad de MRTK con Oculus Unity se realiza a través de dos orígenes diferentes, la canalización del SDK de XR de Unity y el paquete de Unity de integración de Oculus.</span><span class="sxs-lookup"><span data-stu-id="697cf-106">MRTK's support for the Oculus Quest comes via two different sources, Unity's XR SDK pipeline and the Oculus Integration Unity package.</span></span> <span data-ttu-id="697cf-107">El **proveedor de datos XRSDK de Oculus** permite el uso de ambos orígenes y debe usarse para implementar MRTK en Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="697cf-107">The **Oculus XRSDK Data Provider** enables the use of both sources and must be used to deploy MRTK on the Oculus Quest.</span></span>

<span data-ttu-id="697cf-108">La [canalización del SDK de XR](https://docs.unity3d.com/Manual/XR.html) de Unity permite el uso de controladores táctiles de Oculus y el seguimiento de la cabeza con Oculus Tracking.</span><span class="sxs-lookup"><span data-stu-id="697cf-108">The [Unity XR SDK Pipeline](https://docs.unity3d.com/Manual/XR.html) enables the use of Oculus Touch controllers and head tracking with the Oculus Quest.</span></span>
<span data-ttu-id="697cf-109">Esta canalización es el estándar para desarrollar aplicaciones XR en Unity 2019.3 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="697cf-109">This pipeline is the standard for developing XR applications in Unity 2019.3 and beyond.</span></span> <span data-ttu-id="697cf-110">Para usar esta canalización, asegúrese de usar **Unity 2019.3 o una versión más reciente.**</span><span class="sxs-lookup"><span data-stu-id="697cf-110">To use this pipeline, make sure that you using **Unity 2019.3 or newer**.</span></span> <span data-ttu-id="697cf-111">Esto es **necesario para** implementar aplicaciones MRTK en Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="697cf-111">This is **required** to deploy MRTK applications to the Oculus Quest.</span></span>

<span data-ttu-id="697cf-112">El [paquete de Unity de integración de Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite el uso del seguimiento **manual** con Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="697cf-112">The [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) allows for the use of **hand tracking** with the Oculus Quest.</span></span> <span data-ttu-id="697cf-113">Este proveedor de datos **NO usa** la canalización del SDK **de XR** de Unity ni **la canalización de XR heredada.**</span><span class="sxs-lookup"><span data-stu-id="697cf-113">This data provider does **NOT** use Unity's **XR SDK Pipeline** or **Legacy XR Pipeline**.</span></span>

## <a name="setting-up-project-for-the-oculus-quest"></a><span data-ttu-id="697cf-114">Configuración del proyecto para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="697cf-114">Setting up project for the Oculus Quest</span></span>

1. <span data-ttu-id="697cf-115">Siga [estos pasos](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para asegurarse de que el proyecto está listo para implementarse en Oculus Quest.</span><span class="sxs-lookup"><span data-stu-id="697cf-115">Follow [these steps](https://developer.oculus.com/documentation/unity/book-unity-gsg/) to ensure that your project is ready to deploy on Oculus Quest.</span></span>

1. <span data-ttu-id="697cf-116">Asegúrese de [que el modo de](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) desarrollador está habilitado en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="697cf-116">Ensure that [developer mode](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) is enabled on your device.</span></span> <span data-ttu-id="697cf-117">La instalación de los controladores de ADB de Oculus es opcional.</span><span class="sxs-lookup"><span data-stu-id="697cf-117">Installing the Oculus ADB Drivers is optional.</span></span>

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a><span data-ttu-id="697cf-118">Configuración de la canalización del SDK de XR para Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="697cf-118">Setting up the XR SDK Pipeline for Oculus Quest</span></span>

1. <span data-ttu-id="697cf-119">Asegúrese de que **el complemento Oculus XR** está instalado en **Window --> Administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="697cf-119">Ensure that the **Oculus XR Plugin** is installed under **Window --> Package Manager**</span></span>

    ![Paquete del complemento XR de Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. <span data-ttu-id="697cf-121">Asegúrese de que el proveedor de complementos de Oculus está incluido en el proyecto; para ello, vaya **a Edit --> Project Configuración --> XR Plug-in Management --> Plug-in Providers (Editar --> Project Configuración --> XR Plug-in Management --> Plug-in Providers [Editar --> Project Configuración --> XR Plug-in Management --> Plug-in Providers].**</span><span class="sxs-lookup"><span data-stu-id="697cf-121">Make sure that the Oculus Plug-in Provider is included in your project by going to **Edit --> Project Settings --> XR Plug-in Management --> Plug-in Providers**</span></span>

    ![Proveedor de complementos de Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a><span data-ttu-id="697cf-123">Configuración del paquete de Unity de integración de Oculus para habilitar el seguimiento a mano</span><span class="sxs-lookup"><span data-stu-id="697cf-123">Setting up the Oculus Integration Unity package to enable handtracking</span></span>

1. <span data-ttu-id="697cf-124">Descargue e importe [Oculus Integration desde](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) el almacén de recursos de Unity.</span><span class="sxs-lookup"><span data-stu-id="697cf-124">Download and import [Oculus Integration](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) from the Unity Asset Store.</span></span> <span data-ttu-id="697cf-125">La versión más reciente probada para funcionar es 20.0.0.</span><span class="sxs-lookup"><span data-stu-id="697cf-125">The latest version tested to work is 20.0.0.</span></span> <span data-ttu-id="697cf-126">Las versiones anteriores se pueden encontrar en este [archivo](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span><span class="sxs-lookup"><span data-stu-id="697cf-126">Older versions can be found from this [archive](https://developer.oculus.com/downloads/package/unity-integration-archive/).</span></span>

1. <span data-ttu-id="697cf-127">Vaya a Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules (Integrar módulos de Unity de integración de Oculus).</span><span class="sxs-lookup"><span data-stu-id="697cf-127">Navigate to Mixed Reality Toolkit > Utilities > Oculus > Integrate Oculus Integration Unity Modules.</span></span> <span data-ttu-id="697cf-128">Al hacerlo, se actualizarán las definiciones de asmdefs con las definiciones y las referencias necesarias para que el código de Oculus Quest pertinente funcione.</span><span class="sxs-lookup"><span data-stu-id="697cf-128">Doing this will update the asmdefs with definitions and references needed for the relevant Oculus Quest code to function.</span></span> <span data-ttu-id="697cf-129">También actualizará el archivo csc para filtrar las advertencias obsoletas producidas por los recursos de integración de Oculus.</span><span class="sxs-lookup"><span data-stu-id="697cf-129">It will also update the csc file to filter out the obsolete warnings produced by the Oculus Integration assets.</span></span> <span data-ttu-id="697cf-130">El repositorio de MRTK contiene un archivo csc que convierte las advertencias en errores. Esta conversión detiene el proceso de MRTK-Quest configuración.</span><span class="sxs-lookup"><span data-stu-id="697cf-130">The MRTK repo contains a csc file that converts warnings to errors, this conversion halts the MRTK-Quest configuration process.</span></span>

    ![Asmdef de integración de Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. <span data-ttu-id="697cf-132">En la carpeta Oculus importada (debe encontrarse en Assets/Oculus), hay un objeto que puede incluir scripts denominado OculusProjectConfig.</span><span class="sxs-lookup"><span data-stu-id="697cf-132">In the imported Oculus folder (It should be found at Assets/Oculus), there is a scriptable object called OculusProjectConfig.</span></span> <span data-ttu-id="697cf-133">En ese archivo de configuración, debe establecer HandTrackingSupport en "Controladores y manos".</span><span class="sxs-lookup"><span data-stu-id="697cf-133">In that config file, you need to set HandTrackingSupport to "Controllers and Hands".</span></span>

    ![Controlador de integración de Oculus y manos](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a><span data-ttu-id="697cf-135">Configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="697cf-135">Setting up the scene</span></span>

1. <span data-ttu-id="697cf-136">Cree una nueva escena de Unity o abra una escena preexistida como HandInteractionExamples.</span><span class="sxs-lookup"><span data-stu-id="697cf-136">Create a new Unity scene or open a pre-existing scene like HandInteractionExamples.</span></span>
1. <span data-ttu-id="697cf-137">Agregue MRTK a la escena; para Mixed Reality Toolkit agregar a la escena   >  **y configurar**.</span><span class="sxs-lookup"><span data-stu-id="697cf-137">Add MRTK to the scene by navigating to **Mixed Reality Toolkit** > **Add to Scene and Configure**.</span></span>

## <a name="using-the-oculus-xr-sdk-data-provider"></a><span data-ttu-id="697cf-138">Uso del proveedor de datos del SDK de Oculus XR</span><span class="sxs-lookup"><span data-stu-id="697cf-138">Using the Oculus XR SDK Data Provider</span></span>

::: moniker range=">= mrtkunity-2021-05"

1. <span data-ttu-id="697cf-139">Configuración del perfil para usar el proveedor de datos del **SDK de Oculus XR**</span><span class="sxs-lookup"><span data-stu-id="697cf-139">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="697cf-140">Si no pretende modificar los perfiles de configuración</span><span class="sxs-lookup"><span data-stu-id="697cf-140">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="697cf-141">Use cualquiera de los perfiles de MRTK predeterminados, que están configurados en las canalizaciones XR de Unity.</span><span class="sxs-lookup"><span data-stu-id="697cf-141">Use any of the default MRTK profiles, which are all configured across Unity's XR pipelines.</span></span> <span data-ttu-id="697cf-142">El elemento DefaultXRSDKConfigurationProfile anterior ahora está etiquetado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="697cf-142">The previous DefaultXRSDKConfigurationProfile is now labeled obsolete.</span></span>
        - <span data-ttu-id="697cf-143">Vaya a [Compilación e implementación del proyecto en Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="697cf-143">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="697cf-144">De lo contrario, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="697cf-144">Otherwise follow the following:</span></span>
        - <span data-ttu-id="697cf-145">Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione **Copiar y** personalizar para clonar el perfil de realidad mixta predeterminado.</span><span class="sxs-lookup"><span data-stu-id="697cf-145">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="697cf-147">Seleccione el perfil **de configuración** de entrada.</span><span class="sxs-lookup"><span data-stu-id="697cf-147">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuración de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="697cf-149">Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.</span><span class="sxs-lookup"><span data-stu-id="697cf-149">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil del sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="697cf-151">Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.</span><span class="sxs-lookup"><span data-stu-id="697cf-151">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="697cf-152">Abra el nuevo proveedor de datos y establezca **El tipo** en **Microsoft.MixedReality.Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="697cf-152">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Agregar proveedor de datos XRSDK de Oculus](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end
::: moniker range="< mrtkunity-2021-05"

1. <span data-ttu-id="697cf-154">Configuración del perfil para usar el proveedor de datos del **SDK de Oculus XR**</span><span class="sxs-lookup"><span data-stu-id="697cf-154">Configure your profile to use the **Oculus XR SDK Data Provider**</span></span>
    - <span data-ttu-id="697cf-155">Si no pretende modificar los perfiles de configuración</span><span class="sxs-lookup"><span data-stu-id="697cf-155">If not intending to modify the configuration profiles</span></span>
        - <span data-ttu-id="697cf-156">Cambie el perfil a DefaultXRSDKConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="697cf-156">Change your profile to DefaultXRSDKConfigurationProfile.</span></span>
        - <span data-ttu-id="697cf-157">Vaya a [Compilación e implementación del proyecto en Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)</span><span class="sxs-lookup"><span data-stu-id="697cf-157">Go to [Build and deploy your project to Oculus Quest](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest).</span></span>
    - <span data-ttu-id="697cf-158">De lo contrario, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="697cf-158">Otherwise follow the following:</span></span>
        - <span data-ttu-id="697cf-159">Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione **Copiar y** personalizar para clonar el perfil de realidad mixta predeterminado.</span><span class="sxs-lookup"><span data-stu-id="697cf-159">Select the MixedRealityToolkit game object in the hierarchy and select **Copy and Customize** to clone the default mixed reality profile.</span></span>

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - <span data-ttu-id="697cf-161">Seleccione el perfil **de configuración** de entrada.</span><span class="sxs-lookup"><span data-stu-id="697cf-161">Select the **Input** Configuration Profile.</span></span>

        ![Perfil de configuración de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - <span data-ttu-id="697cf-163">Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.</span><span class="sxs-lookup"><span data-stu-id="697cf-163">Select **Clone** in the input system profile to enable modification.</span></span>

        ![Clonar perfil del sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - <span data-ttu-id="697cf-165">Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.</span><span class="sxs-lookup"><span data-stu-id="697cf-165">Open the **Input Data Providers** section, select **Add Data Provider** at the top, and new data provider will be added at the end of the list.</span></span>  <span data-ttu-id="697cf-166">Abra el nuevo proveedor de datos y establezca **El tipo** en **Microsoft.MixedReality.Toolkit. XRSDK. Oculus > OculusXRSDKDeviceManager**.</span><span class="sxs-lookup"><span data-stu-id="697cf-166">Open the new data provider and set the **Type** to **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**.</span></span>

        ![Agregar proveedor de datos XRSDK de Oculus](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)
::: moniker-end

1. <span data-ttu-id="697cf-168">El proveedor de datos del SDK de Oculus XR incluye un prefab de cámara OVR que configura automáticamente el proyecto con un equipo de cámara OVR y las manos de OVR para enrutar correctamente la entrada.</span><span class="sxs-lookup"><span data-stu-id="697cf-168">The Oculus XR SDK Data Provider includes an OVR Camera Rig Prefab which automatically configures the project with an OVR Camera Rig and OVR Hands to properly route input.</span></span> <span data-ttu-id="697cf-169">La adición manual de un dispositivo de cámara OVR a la escena requerirá la configuración manual de la configuración y la entrada.</span><span class="sxs-lookup"><span data-stu-id="697cf-169">Manually adding an OVR Camera Rig to the scene will require manual configuration of settings and input.</span></span>

## <a name="build-and-deploy-your-project-to-oculus-quest"></a><span data-ttu-id="697cf-170">Compilación e implementación del proyecto en Oculus Quest</span><span class="sxs-lookup"><span data-stu-id="697cf-170">Build and deploy your project to Oculus Quest</span></span>

1. <span data-ttu-id="697cf-171">Conexión de Oculus Quest a través de un cable USB 3.0 -> USB C</span><span class="sxs-lookup"><span data-stu-id="697cf-171">Plug in your Oculus Quest via a USB 3.0 -> USB C cable</span></span>
1. <span data-ttu-id="697cf-172">Vaya a **File > Build Configuración**</span><span class="sxs-lookup"><span data-stu-id="697cf-172">Navigate to **File > Build Settings**</span></span>
1. <span data-ttu-id="697cf-173">Cambio de la implementación a **Android**</span><span class="sxs-lookup"><span data-stu-id="697cf-173">Change the deployment to **Android**</span></span>
1. <span data-ttu-id="697cf-174">Asegúrese de que Oculus Quest está seleccionado como el dispositivo de ejecución aplicable.</span><span class="sxs-lookup"><span data-stu-id="697cf-174">Ensure that the Oculus Quest is selected as the applicable run device</span></span>

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. <span data-ttu-id="697cf-176">Seleccione Compilar y ejecutar.</span><span class="sxs-lookup"><span data-stu-id="697cf-176">Select Build and Run</span></span>
    - <span data-ttu-id="697cf-177">Es probable que se encuentre con el siguiente conjunto de errores de compilación al seleccionar *Compilar y ejecutar* la primera vez.</span><span class="sxs-lookup"><span data-stu-id="697cf-177">You will likely encounter the following set of build errors when you select *Build and Run* the first time.</span></span> <span data-ttu-id="697cf-178">Debería poder realizar la implementación correctamente al seleccionar Compilar *y ejecutar de* nuevo.</span><span class="sxs-lookup"><span data-stu-id="697cf-178">You should be able to successfully deploy upon selecting *Build and Run* again.</span></span>

    ![Errores de compilación esperados de Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. <span data-ttu-id="697cf-180">Acepte el _símbolo del sistema Permitir depuración USB_ desde dentro de la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="697cf-180">Accept the _Allow USB Debugging_ prompt from inside the quest</span></span>
1. <span data-ttu-id="697cf-181">Ver la escena dentro de la misión de Oculus</span><span class="sxs-lookup"><span data-stu-id="697cf-181">See your scene inside the Oculus Quest</span></span>

## <a name="removing-oculus-integration-from-the-project"></a><span data-ttu-id="697cf-182">Quitar la integración de Oculus del Project</span><span class="sxs-lookup"><span data-stu-id="697cf-182">Removing Oculus Integration from the Project</span></span>

1. <span data-ttu-id="697cf-183">Vaya a la Mixed Reality Toolkit > Oculus > Módulos de Unity de integración de Oculus independientes ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span><span class="sxs-lookup"><span data-stu-id="697cf-183">Navigate to the Mixed Reality Toolkit > Oculus > Separate Oculus Integration Unity Modules  ![Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)</span></span>
1. <span data-ttu-id="697cf-184">Deje que Unity se actualice como referencias en Microsoft.MixedReality. Toolkit. Providers.Oculus.asmdef y otros archivos se modifican en este paso</span><span class="sxs-lookup"><span data-stu-id="697cf-184">Let Unity refresh as references in the Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef and other files are modified in this step</span></span>
1. <span data-ttu-id="697cf-185">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="697cf-185">Close Unity</span></span>
1. <span data-ttu-id="697cf-186">Cierre Visual Studio, si está abierto.</span><span class="sxs-lookup"><span data-stu-id="697cf-186">Close Visual Studio, if it's open</span></span>
1. <span data-ttu-id="697cf-187">Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.</span><span class="sxs-lookup"><span data-stu-id="697cf-187">Open File Explorer and navigate to the root of the MRTK Unity project</span></span>
1. <span data-ttu-id="697cf-188">Eliminación del directorio UnityProjectName/Library</span><span class="sxs-lookup"><span data-stu-id="697cf-188">Delete the UnityProjectName/Library directory</span></span>
1. <span data-ttu-id="697cf-189">Eliminación del directorio UnityProjectName/Assets/Oculus</span><span class="sxs-lookup"><span data-stu-id="697cf-189">Delete the UnityProjectName/Assets/Oculus directory</span></span>
1. <span data-ttu-id="697cf-190">Eliminación del archivo UnityProjectName/Assets/Oculus.meta</span><span class="sxs-lookup"><span data-stu-id="697cf-190">Delete the UnityProjectName/Assets/Oculus.meta file</span></span>
1. <span data-ttu-id="697cf-191">Volver a abrir Unity</span><span class="sxs-lookup"><span data-stu-id="697cf-191">Reopen Unity</span></span>

## <a name="common-errors"></a><span data-ttu-id="697cf-192">Errores comunes</span><span class="sxs-lookup"><span data-stu-id="697cf-192">Common errors</span></span>

### <a name="quest-not-recognized-by-unity"></a><span data-ttu-id="697cf-193">Misión no reconocida por Unity</span><span class="sxs-lookup"><span data-stu-id="697cf-193">Quest not recognized by Unity</span></span>

<span data-ttu-id="697cf-194">Asegúrese de que las rutas de acceso de Android están configuradas correctamente.</span><span class="sxs-lookup"><span data-stu-id="697cf-194">Make sure your Android paths are properly configured.</span></span> <span data-ttu-id="697cf-195">Si sigue teniendo problemas, siga esta [guía.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span><span class="sxs-lookup"><span data-stu-id="697cf-195">If you continue to encounter problems, follow this [guide](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)</span></span>

<span data-ttu-id="697cf-196">**Editar > preferencias > herramientas externas > Android**</span><span class="sxs-lookup"><span data-stu-id="697cf-196">**Edit > Preferences > External Tools > Android**</span></span>

![Configuración de herramientas de Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
