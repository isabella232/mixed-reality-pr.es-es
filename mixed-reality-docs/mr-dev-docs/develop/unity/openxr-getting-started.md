---
title: Uso del complemento OpenXR de Mixed Reality
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547040"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="a0f78-104">Uso del complemento OpenXR de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="a0f78-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="a0f78-105">Para los desarrolladores que usan Unity 2020 para compilar aplicaciones HoloLens 2 o Mixed Reality, se puede usar el complemento OpenXR en lugar del complemento WindowsXR para mejorar las compatibilidades multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="a0f78-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="a0f78-106">El Mixed Reality complemento OpenXR también funciona bien con la versión [más reciente Mixed Reality Toolkit 2.7.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="a0f78-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0f78-107">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a0f78-107">Prerequisites</span></span>

* <span data-ttu-id="a0f78-108">Versión más reciente de Unity 2020.3 LTS(se recomienda 2020.3.8f1 o superior)</span><span class="sxs-lookup"><span data-stu-id="a0f78-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="a0f78-109">Complemento OpenXR de Unity más reciente (se recomienda la versión 1.2 o posterior)</span><span class="sxs-lookup"><span data-stu-id="a0f78-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="a0f78-110">Herramientas [más recientes para HoloLens 2 desarrollo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="a0f78-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="a0f78-111">MrTK más reciente (opcional), (se recomienda la versión 2.7 o posterior)</span><span class="sxs-lookup"><span data-stu-id="a0f78-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="a0f78-112">Versión Mixed Reality complemento OpenXR(se recomienda la versión 1.0.0-preview.1 o posterior)</span><span class="sxs-lookup"><span data-stu-id="a0f78-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![Captura de pantalla del ejemplo básico de xr Unity abierto que se ejecuta en HoloLens](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="a0f78-114">Si va a compilar aplicaciones de realidad virtual en pc Windows, Mixed Reality complemento OpenXR no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="a0f78-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="a0f78-115">Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.</span><span class="sxs-lookup"><span data-stu-id="a0f78-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="a0f78-116">Configuración del proyecto con MRTK</span><span class="sxs-lookup"><span data-stu-id="a0f78-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="a0f78-117">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="a0f78-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="a0f78-118">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a0f78-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="a0f78-119">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="a0f78-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a0f78-120">Configuración del proyecto mediante MRTK</span><span class="sxs-lookup"><span data-stu-id="a0f78-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="a0f78-121">Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="a0f78-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="a0f78-122">Configuración manual sin MRTK</span><span class="sxs-lookup"><span data-stu-id="a0f78-122">Manual setup without MRTK</span></span>

<span data-ttu-id="a0f78-123">Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="a0f78-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="a0f78-124">Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="a0f78-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="a0f78-126">Establecimiento del destino de compilación</span><span class="sxs-lookup"><span data-stu-id="a0f78-126">Setting your build target</span></span>

<span data-ttu-id="a0f78-127">Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="a0f78-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & independiente resaltado](images/wmr-config-img-3.png)

<span data-ttu-id="a0f78-129">Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="a0f78-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="a0f78-130">Seleccione File > Build Settings... (Configuración **> compilación de archivos...**</span><span class="sxs-lookup"><span data-stu-id="a0f78-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="a0f78-131">Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**</span><span class="sxs-lookup"><span data-stu-id="a0f78-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="a0f78-132">Establezca la **arquitectura** en **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="a0f78-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="a0f78-133">Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.</span><span class="sxs-lookup"><span data-stu-id="a0f78-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="a0f78-134">Establezca **Build Type** (Tipo de compilación) en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="a0f78-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="a0f78-135">Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)</span><span class="sxs-lookup"><span data-stu-id="a0f78-135">Set **UWP SDK** to **Latest installed**</span></span>

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="a0f78-137">Configuración de la administración de complementos XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0f78-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="a0f78-138">Para establecer OpenXR como runtime en Unity:</span><span class="sxs-lookup"><span data-stu-id="a0f78-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="a0f78-139">En el Editor de Unity, vaya **a Editar > configuración del proyecto.**</span><span class="sxs-lookup"><span data-stu-id="a0f78-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="a0f78-140">En la lista de Configuración, seleccione **Administración de complementos XR.**</span><span class="sxs-lookup"><span data-stu-id="a0f78-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="a0f78-141">Active los **cuadros Initialize XR on Startup (Inicializar XR) en Startup** (Inicio) y **OpenXR (OpenXR).**</span><span class="sxs-lookup"><span data-stu-id="a0f78-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="a0f78-142">Si el destino HoloLens 2, asegúrese de que está en la plataforma UWP y **seleccione Microsoft HoloLens conjunto de características.**</span><span class="sxs-lookup"><span data-stu-id="a0f78-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración del complemento XR resaltada](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="a0f78-144">Optimization</span><span class="sxs-lookup"><span data-stu-id="a0f78-144">Optimization</span></span>

<span data-ttu-id="a0f78-145">Si está desarrollando para HoloLens 2, vaya **a Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicación de la configuración de proyecto recomendada para HoloLens 2 para obtener un mejor rendimiento de la aplicación).</span><span class="sxs-lookup"><span data-stu-id="a0f78-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="a0f78-147">Si ve un icono de advertencia rojo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a0f78-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="a0f78-148">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="a0f78-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="a0f78-150">Ya está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="a0f78-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="a0f78-151">Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a0f78-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="a0f78-152">Proyectos de ejemplo de Unity para OpenXR y HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a0f78-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="a0f78-153">Consulte el repositorio de ejemplos de [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) para ver proyectos de Unity de ejemplo que muestran cómo compilar aplicaciones de Unity para cascos HoloLens 2 o Mixed Reality mediante el complemento Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a0f78-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="a0f78-154">Uso de MRTK con compatibilidad con OpenXR</span><span class="sxs-lookup"><span data-stu-id="a0f78-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="a0f78-155">MRTK para Unity versión 2.7 ahora admite oficialmente Mixed Reality complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a0f78-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="a0f78-156">Abra de [nuevo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho.</span><span class="sxs-lookup"><span data-stu-id="a0f78-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="a0f78-157">La compatibilidad con OpenXR está en el **paquete de Foundation.**</span><span class="sxs-lookup"><span data-stu-id="a0f78-157">OpenXR support is in the **Foundation** package.</span></span>

![Ventana detectar características de la herramienta de características de realidad mixta con recursos estándar resaltados](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="a0f78-159">Al actualizar desde una versión anterior de MRTK, asegúrese de que la siguiente línea se encuentra en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="a0f78-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="a0f78-160">Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.</span><span class="sxs-lookup"><span data-stu-id="a0f78-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0f78-161">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="a0f78-161">Next steps</span></span>

<span data-ttu-id="a0f78-162">Ahora que tiene el proyecto configurado para OpenXR y [](openxr-supported-features.md) tiene acceso a ejemplos, consulte las características que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a0f78-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="a0f78-163">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="a0f78-163">Have Feedback?</span></span>

<span data-ttu-id="a0f78-164">OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que pueda proporcionarnos para mejorarlo.</span><span class="sxs-lookup"><span data-stu-id="a0f78-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="a0f78-165">Para encontrarnos en los foros de [Unity,](https://aka.ms/unityforums) debe etiquetar la publicación del foro con **Microsoft**  +  **OpenXR** y HoloLens 2 **o Windows Mixed Reality**. </span><span class="sxs-lookup"><span data-stu-id="a0f78-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0f78-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="a0f78-166">See also</span></span>

* [<span data-ttu-id="a0f78-167">Configuración de un proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="a0f78-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="a0f78-168">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="a0f78-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="a0f78-169">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="a0f78-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
