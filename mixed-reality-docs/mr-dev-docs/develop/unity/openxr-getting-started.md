---
title: Uso del Mixed Reality de OpenXR para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: 97169507e2b61110d2d16580ba957feff3755258
ms.sourcegitcommit: aca5fddb98fbbd9aa22bdf8174d7fdcdb9d4c08a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2021
ms.locfileid: "107894033"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="ae749-104">Uso del Mixed Reality de OpenXR para Unity</span><span class="sxs-lookup"><span data-stu-id="ae749-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="ae749-105">A partir de la versión 2020.2 de Unity, el paquete del complemento Mixed Reality OpenXR de Microsoft está disponible mediante el Administrador de paquetes Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="ae749-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae749-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="ae749-106">Prerequisites</span></span>

* <span data-ttu-id="ae749-107">Unity 2020.3 LTS o posterior</span><span class="sxs-lookup"><span data-stu-id="ae749-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="ae749-108">Complemento OpenXR de Unity 1.1.1 o posterior</span><span class="sxs-lookup"><span data-stu-id="ae749-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="ae749-109">Visual Studio 2019 o posterior</span><span class="sxs-lookup"><span data-stu-id="ae749-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="ae749-110">Instalación de la compatibilidad con la plataforma **UWP** en Unity para HoloLens 2 aplicaciones</span><span class="sxs-lookup"><span data-stu-id="ae749-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="ae749-111">Si va a compilar aplicaciones de REALIDAD virtual en equipos Windows, Mixed Reality complemento OpenXR no es necesario necesariamente.</span><span class="sxs-lookup"><span data-stu-id="ae749-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ae749-112">Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o si va a compilar aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="ae749-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="ae749-113">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="ae749-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="ae749-114">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="ae749-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ae749-115">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ae749-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="ae749-116">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="ae749-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae749-117">Configuración del proyecto mediante MRTK</span><span class="sxs-lookup"><span data-stu-id="ae749-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="ae749-118">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="ae749-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="ae749-119">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="ae749-119">Manual setup without MRTK</span></span>

<span data-ttu-id="ae749-120">Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ae749-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="ae749-121">Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="ae749-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="ae749-123">Establecimiento del destino de compilación</span><span class="sxs-lookup"><span data-stu-id="ae749-123">Setting your build target</span></span>

<span data-ttu-id="ae749-124">Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="ae749-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](images/wmr-config-img-3.png)

<span data-ttu-id="ae749-126">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="ae749-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="ae749-127">Seleccione File > Build Settings... (Configuración **> compilación de archivos...**</span><span class="sxs-lookup"><span data-stu-id="ae749-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="ae749-128">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="ae749-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="ae749-129">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="ae749-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="ae749-130">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="ae749-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="ae749-131">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="ae749-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="ae749-132">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="ae749-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="ae749-133">Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).</span><span class="sxs-lookup"><span data-stu-id="ae749-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

<span data-ttu-id="ae749-135">Después de configurar la plataforma, debe hacer [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.</span><span class="sxs-lookup"><span data-stu-id="ae749-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ae749-136">Configuración de la administración de complementos XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="ae749-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ae749-137">Para establecer OpenXR como runtime en Unity:</span><span class="sxs-lookup"><span data-stu-id="ae749-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ae749-138">En el Editor de Unity, vaya **a Editar > configuración del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="ae749-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ae749-139">En la lista de Configuración, seleccione **Administración de complementos XR.**</span><span class="sxs-lookup"><span data-stu-id="ae749-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ae749-140">Active los **cuadros Inicializar XR al inicio** y **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="ae749-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="ae749-141">Si el destino HoloLens 2, asegúrese de que está en la plataforma UWP y **seleccione Microsoft HoloLens conjunto de características.**</span><span class="sxs-lookup"><span data-stu-id="ae749-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración del complemento XR resaltada](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="ae749-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="ae749-143">Optimization</span></span>

<span data-ttu-id="ae749-144">Si está desarrollando para HoloLens 2, vaya **a Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicación de la configuración de proyecto recomendada para HoloLens 2 para obtener un mejor rendimiento de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="ae749-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="ae749-146">Si ve un icono de advertencia rojo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ae749-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ae749-147">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="ae749-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="ae749-149">Ya está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="ae749-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ae749-150">Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ae749-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="ae749-151">Prueba de las escenas de ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="ae749-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="ae749-152">HoloLens 2 ejemplos</span><span class="sxs-lookup"><span data-stu-id="ae749-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="ae749-153">En el Editor de Unity, vaya a **Ventana > Administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="ae749-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="ae749-154">En la lista de paquetes, seleccione **Mixed Reality complemento OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="ae749-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="ae749-155">Busque el ejemplo en la **lista Ejemplos** y seleccione **Importar.**</span><span class="sxs-lookup"><span data-stu-id="ae749-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de pantalla de unity Administrador de paquetes en el editor de Unity con Mixed Reality complemento OpenXR seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="ae749-157">Cuando se actualiza un paquete, Unity proporciona la opción de actualizar ejemplos importados.</span><span class="sxs-lookup"><span data-stu-id="ae749-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="ae749-158">La actualización de un ejemplo importado sobrescribirá los cambios realizados en el ejemplo y los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="ae749-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ae749-159">Uso de MRTK con compatibilidad con OpenXR</span><span class="sxs-lookup"><span data-stu-id="ae749-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ae749-160">MRTK-Unity admite el Mixed Reality complemento OpenXR a partir de la versión 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="ae749-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="ae749-161">Vuelva a [abrir Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="ae749-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="ae749-162">La compatibilidad con OpenXR está en el **paquete Foundation.**</span><span class="sxs-lookup"><span data-stu-id="ae749-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="ae749-163">Vaya al script del componente MixedReality Toolkit en el inspector y cambie al **perfil DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="ae749-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Captura de pantalla de cambio de la configuración de MRTK en el componente Mixed Reality Toolkit del inspector](images/openxr-img-11.png)

    1. <span data-ttu-id="ae749-165">Consulte la documentación de MRTK para obtener información más [detallada sobre la migración a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="ae749-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="ae749-166">Al actualizar desde una versión anterior de MRTK, asegúrese de que la línea siguiente se encuentra en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="ae749-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ae749-167">Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.</span><span class="sxs-lookup"><span data-stu-id="ae749-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae749-168">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="ae749-168">Next steps</span></span>

<span data-ttu-id="ae749-169">Ahora que tiene el proyecto configurado para OpenXR y [](openxr-supported-features.md) tiene acceso a ejemplos, consulte las características que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ae749-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ae749-170">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="ae749-170">Have Feedback?</span></span>

<span data-ttu-id="ae749-171">OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que pueda enviarnos para mejorarlo.</span><span class="sxs-lookup"><span data-stu-id="ae749-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ae749-172">Para encontrarnos en los foros de [Unity,](https://aka.ms/unityforums) debe etiquetar la publicación del foro con **Microsoft**  +  **OpenXR** y HoloLens 2 **o Windows Mixed Reality**. </span><span class="sxs-lookup"><span data-stu-id="ae749-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae749-173">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ae749-173">See also</span></span>

* [<span data-ttu-id="ae749-174">Configuración de un proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="ae749-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ae749-175">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="ae749-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ae749-176">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="ae749-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
