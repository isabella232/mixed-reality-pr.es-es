---
title: Uso del complemento OpenXR de Mixed Reality
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: 733bbbd75dd170241e8781e24989d23902781fb9
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333447"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="29118-104">Uso del complemento OpenXR de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="29118-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="29118-105">Para los desarrolladores que usan Unity 2020 para compilar aplicaciones HoloLens 2 o Mixed Reality, se puede usar el complemento OpenXR en lugar del complemento WindowsXR para mejorar las compatibilidades multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="29118-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="29118-106">El Mixed Reality complemento OpenXR también funciona bien con la herramienta de [características Mixed Reality más reciente.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="29118-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29118-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="29118-107">Prerequisites</span></span>

* <span data-ttu-id="29118-108">La versión más reciente de Unity 2020.3 LTS, se recomienda 2020.3.6f1 o superior.</span><span class="sxs-lookup"><span data-stu-id="29118-108">Latest Unity 2020.3 LTS, recommend 2020.3.6f1 or above.</span></span>
* <span data-ttu-id="29118-109">El complemento OpenXR de Unity más reciente, recomendado 1.2 o posterior</span><span class="sxs-lookup"><span data-stu-id="29118-109">Latest Unity OpenXR plugin, recommend 1.2 or later</span></span>
* <span data-ttu-id="29118-110">Herramientas [más recientes para HoloLens 2 desarrollo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="29118-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="29118-111">Versión más reciente de MRTK (opcional), se recomienda la versión 2.6 o posterior.</span><span class="sxs-lookup"><span data-stu-id="29118-111">Latest MRTK (optional), recommend version 2.6 or later</span></span>
* <span data-ttu-id="29118-112">Versión Mixed Reality complemento OpenXR, se recomienda la versión 0.9.5 o posterior.</span><span class="sxs-lookup"><span data-stu-id="29118-112">Latest Mixed Reality OpenXR Plugin, recommend version 0.9.5 or later</span></span>

> [!NOTE]
> <span data-ttu-id="29118-113">Si va a compilar aplicaciones de realidad virtual en equipos Windows, Mixed Reality complemento OpenXR no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="29118-113">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="29118-114">Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="29118-114">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="29118-115">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="29118-115">Setting up your project with MRTK</span></span>

<span data-ttu-id="29118-116">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="29118-116">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="29118-117">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="29118-117">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="29118-118">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="29118-118">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29118-119">Configuración del proyecto mediante MRTK</span><span class="sxs-lookup"><span data-stu-id="29118-119">Set up your project using MRTK</span></span>](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="29118-120">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="29118-120">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="29118-121">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="29118-121">Manual setup without MRTK</span></span>

<span data-ttu-id="29118-122">Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="29118-122">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="29118-123">Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="29118-123">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="29118-125">Establecimiento del destino de compilación</span><span class="sxs-lookup"><span data-stu-id="29118-125">Setting your build target</span></span>

<span data-ttu-id="29118-126">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="29118-126">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & independiente resaltado](images/wmr-config-img-3.png)

<span data-ttu-id="29118-128">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="29118-128">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="29118-129">Seleccione File > Build Settings... (Configuración **de compilación de archivos).**</span><span class="sxs-lookup"><span data-stu-id="29118-129">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="29118-130">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="29118-130">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="29118-131">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="29118-131">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="29118-132">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="29118-132">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="29118-133">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="29118-133">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="29118-134">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="29118-134">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="29118-136">Configuración de la administración de complementos XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="29118-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="29118-137">Para establecer OpenXR como runtime en Unity:</span><span class="sxs-lookup"><span data-stu-id="29118-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="29118-138">En el Editor de Unity, vaya **a Editar > configuración del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="29118-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="29118-139">En la lista de configuración, seleccione **Administración de complementos XR.**</span><span class="sxs-lookup"><span data-stu-id="29118-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="29118-140">Active los **cuadros Inicializar XR al inicio** y **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="29118-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="29118-141">Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y **seleccione Microsoft HoloLens conjunto de características.**</span><span class="sxs-lookup"><span data-stu-id="29118-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="29118-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="29118-143">Optimization</span></span>

<span data-ttu-id="29118-144">Si va a desarrollar para HoloLens 2, vaya a Mixed Reality> **OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicar la configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="29118-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="29118-146">Si ve un icono de advertencia rojo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="29118-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="29118-147">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="29118-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](images/openxr-img-06.png)

<span data-ttu-id="29118-149">Ya está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="29118-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="29118-150">Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="29118-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="29118-151">Proyectos de ejemplo de Unity para OpenXR y HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="29118-151">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="29118-152">Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="29118-152">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="29118-153">Uso de MRTK con compatibilidad con OpenXR</span><span class="sxs-lookup"><span data-stu-id="29118-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="29118-154">MRTK-Unity admite el Mixed Reality complemento OpenXR a partir de la versión 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="29118-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="29118-155">Abra de [nuevo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="29118-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="29118-156">La compatibilidad con OpenXR está en el **paquete de Foundation.**</span><span class="sxs-lookup"><span data-stu-id="29118-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="29118-157">Vaya al script del componente MixedReality Toolkit en el inspector y cambie al perfil **DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="29118-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Captura de pantalla de la conmutación de la configuración de MRTK en el componente Mixed Reality Toolkit del inspector](images/openxr-img-11.png)

    1. <span data-ttu-id="29118-159">Consulte la documentación de MRTK para obtener información más [detallada sobre la migración a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)</span><span class="sxs-lookup"><span data-stu-id="29118-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="29118-160">Al actualizar desde una versión anterior de MRTK, asegúrese de que la siguiente línea se encuentra en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="29118-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="29118-161">Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.</span><span class="sxs-lookup"><span data-stu-id="29118-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="29118-162">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="29118-162">Next steps</span></span>

<span data-ttu-id="29118-163">Ahora que tiene el proyecto configurado para OpenXR y [](openxr-supported-features.md) tiene acceso a ejemplos, consulte las características que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="29118-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="29118-164">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="29118-164">Have Feedback?</span></span>

<span data-ttu-id="29118-165">OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que pueda proporcionarnos para mejorarlo.</span><span class="sxs-lookup"><span data-stu-id="29118-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="29118-166">Para encontrarnos en los foros de [Unity,](https://aka.ms/unityforums) debe etiquetar la publicación del foro con **Microsoft**  +  **OpenXR** y HoloLens 2 **o Windows Mixed Reality**. </span><span class="sxs-lookup"><span data-stu-id="29118-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="29118-167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="29118-167">See also</span></span>

* [<span data-ttu-id="29118-168">Configuración de un proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="29118-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="29118-169">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="29118-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="29118-170">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="29118-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
