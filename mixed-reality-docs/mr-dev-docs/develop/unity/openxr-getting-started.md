---
title: Uso del complemento OpenXR de realidad mixta para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: cae588acbcddeefae45a555f335f1c74389f1824
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496173"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="b544e-104">Uso del complemento OpenXR de realidad mixta para Unity</span><span class="sxs-lookup"><span data-stu-id="b544e-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="b544e-105">A partir de la versión 2020,2 de Unity, el paquete de complementos de OpenXR mixed reality de Microsoft está disponible mediante el administrador de paquetes de Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="b544e-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b544e-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b544e-106">Prerequisites</span></span>

* <span data-ttu-id="b544e-107">Unity 2020,2 o posterior</span><span class="sxs-lookup"><span data-stu-id="b544e-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="b544e-108">Complemento de Unity OpenXR 0.1.3 o posterior</span><span class="sxs-lookup"><span data-stu-id="b544e-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="b544e-109">Visual Studio 2019 o posterior</span><span class="sxs-lookup"><span data-stu-id="b544e-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="b544e-110">Instalación de la compatibilidad con la plataforma **UWP** en Unity para aplicaciones de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b544e-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="b544e-111">Si va a compilar aplicaciones de VR en el equipo con Windows, el complemento OpenXR de realidad mixta no es necesariamente necesario.</span><span class="sxs-lookup"><span data-stu-id="b544e-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="b544e-112">Sin embargo, querrá instalar el complemento si está personalizando la asignación de controladores para los controladores de HP reverberación G2 o la creación de aplicaciones que funcionan en los auriculares de HoloLens 2 y VR.</span><span class="sxs-lookup"><span data-stu-id="b544e-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="b544e-113">Instalación de OpenXR con la herramienta de característica de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b544e-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="b544e-114">Instale el complemento OpenXR con la nueva aplicación de herramienta de características de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b544e-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="b544e-115">Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el paquete de **Complementos Mixed Reality OpenXR** en la categoría del kit de herramientas de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="b544e-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Ventana paquetes de herramientas de característica de realidad mixta con el complemento Open XR resaltado](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="b544e-117">Configuración de administración de complementos de XR para OpenXR</span><span class="sxs-lookup"><span data-stu-id="b544e-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="b544e-118">Para establecer OpenXR como el tiempo de ejecución en Unity:</span><span class="sxs-lookup"><span data-stu-id="b544e-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="b544e-119">En el editor de Unity, vaya a **editar > configuración del proyecto** .</span><span class="sxs-lookup"><span data-stu-id="b544e-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="b544e-120">En la lista de opciones, seleccione **Administración de complementos de XR**</span><span class="sxs-lookup"><span data-stu-id="b544e-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="b544e-121">Active las casillas **inicializar XR en el inicio** y **OpenXR (versión preliminar)**</span><span class="sxs-lookup"><span data-stu-id="b544e-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="b544e-122">Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione **conjunto de características de Microsoft HoloLens** .</span><span class="sxs-lookup"><span data-stu-id="b544e-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="b544e-124">Si ve un icono de advertencia rojo junto al **complemento OpenXR (versión preliminar)**, haga clic en el icono y seleccione **corregir todo** antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b544e-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="b544e-125">Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="b544e-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="b544e-127">Ahora está listo para empezar a desarrollar con OpenXR en Unity.</span><span class="sxs-lookup"><span data-stu-id="b544e-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="b544e-128">Continúe con la siguiente sección para aprender a usar los ejemplos de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="b544e-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="b544e-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="b544e-129">Optimization</span></span>

<span data-ttu-id="b544e-130">Si está desarrollando para HoloLens 2, vaya a **Mixed Reality> OpenXR > aplicar la configuración de proyecto recomendada para hololens 2** para obtener un mejor rendimiento de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b544e-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Captura de pantalla del elemento de menú de realidad mixta abrir con OpenXR seleccionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="b544e-132">Pruebe las escenas de ejemplo de Unity</span><span class="sxs-lookup"><span data-stu-id="b544e-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="b544e-133">Para el uso de uno o varios de los ejemplos, instale [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) desde el **Administrador de paquetes**:</span><span class="sxs-lookup"><span data-stu-id="b544e-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con AR Foundation resaltado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="b544e-135">Ejemplos de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b544e-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="b544e-136">En el editor de Unity, navegue a la **ventana > administrador de paquetes**</span><span class="sxs-lookup"><span data-stu-id="b544e-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="b544e-137">En la lista de paquetes, seleccione **Mixed Reality OpenXR plugin** .</span><span class="sxs-lookup"><span data-stu-id="b544e-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="b544e-138">Busque el ejemplo en la lista de **ejemplos** y seleccione **importar** .</span><span class="sxs-lookup"><span data-stu-id="b544e-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="b544e-140">Cuando se actualiza un paquete, Unity ofrece la opción de actualizar los ejemplos importados.</span><span class="sxs-lookup"><span data-stu-id="b544e-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="b544e-141">Al actualizar un ejemplo importado se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="b544e-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="b544e-142">Uso de MRTK con compatibilidad con OpenXR</span><span class="sxs-lookup"><span data-stu-id="b544e-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="b544e-143">MRTK Unity es compatible con el complemento de OpenXR de realidad mixta a partir de la versión 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="b544e-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="b544e-144">Vuelva a abrir la [herramienta de característica de realidad mixta](welcome-to-mr-feature-tool.md) y seleccione el paquete de **complemento de realidad mixta OpenXR** en la categoría compatibilidad con plataformas.</span><span class="sxs-lookup"><span data-stu-id="b544e-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>
2. <span data-ttu-id="b544e-145">Vaya al script del componente MixedReality Toolkit en el inspector y cambie al perfil **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="b544e-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![Captura de pantalla de cambio de la configuración de MRTK en el componente del kit de herramientas de realidad mixta en el inspector](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="b544e-147">Problemas conocidos</span><span class="sxs-lookup"><span data-stu-id="b544e-147">Known issues</span></span> 

<span data-ttu-id="b544e-148">Cuando use la característica de seguimiento de la mano, agregue la siguiente línea en el archivo **assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="b544e-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="b544e-149">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="b544e-149">Next steps</span></span>

<span data-ttu-id="b544e-150">Ahora que ha configurado el proyecto para OpenXR y tiene acceso a los ejemplos, consulte [las características](openxr-supported-features.md) que se admiten actualmente en nuestro complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="b544e-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="b544e-151">¿Tiene comentarios?</span><span class="sxs-lookup"><span data-stu-id="b544e-151">Have Feedback?</span></span>

<span data-ttu-id="b544e-152">OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que nos proporcione para ayudarlo a mejorar.</span><span class="sxs-lookup"><span data-stu-id="b544e-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="b544e-153">Nos encontrarás en los [foros de Unity](https://aka.ms/unityforums) mediante el etiquetado de tu entrada de foro con **Microsoft**  +  **OpenXRs** y **HoloLens 2** o **Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="b544e-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b544e-154">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b544e-154">See also</span></span>

* [<span data-ttu-id="b544e-155">Configuración de un proyecto sin MRTK</span><span class="sxs-lookup"><span data-stu-id="b544e-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="b544e-156">Configuración recomendada para Unity</span><span class="sxs-lookup"><span data-stu-id="b544e-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="b544e-157">Recomendaciones de rendimiento para Unity</span><span class="sxs-lookup"><span data-stu-id="b544e-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)
