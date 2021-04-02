---
title: Elección de una versión de Unity y el complemento XR
description: Manténgase al día sobre las últimas recomendaciones del complemento Unity y XR para el desarrollo de aplicaciones de HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-Unity, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, Unity
ms.openlocfilehash: b8f5f0131da811393ee053541e0c2fa0c735472e
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938157"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="a6540-104">Elección de una versión de Unity y el complemento XR</span><span class="sxs-lookup"><span data-stu-id="a6540-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="a6540-105">Aunque actualmente se **recomienda instalar Unity 2019,4 lts y el uso de la versión de XR integrada heredada** para el desarrollo de realidad mixta, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6540-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="a6540-106">Unity 2019,4 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="a6540-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="a6540-107">La configuración de Unity recomendada actual de Microsoft para el desarrollo de la realidad de HoloLens 2 y Windows Mixed Reality es **Unity 2019,4 lts con compatibilidad integrada de XR heredada** .</span><span class="sxs-lookup"><span data-stu-id="a6540-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="a6540-108">La mejor manera de instalar y administrar Unity es a través del <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span><span class="sxs-lookup"><span data-stu-id="a6540-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="a6540-109">Cuando esté instalado, abra Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="a6540-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="a6540-110">Seleccione la pestaña **instalaciones** y elija **Agregar** .</span><span class="sxs-lookup"><span data-stu-id="a6540-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="a6540-111">Seleccione Unity 2019,4 LTS y haga clic en **siguiente** .</span><span class="sxs-lookup"><span data-stu-id="a6540-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Instalar la nueva versión de Unity Hub](images/unity-hub-img-01.png)

3. <span data-ttu-id="a6540-113">Comprobar los siguientes componentes en **' Plataformas '**</span><span class="sxs-lookup"><span data-stu-id="a6540-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="a6540-114">**Compatibilidad con la compilación de Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="a6540-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="a6540-115">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="a6540-115">**Windows Build Support (IL2CPP)**</span></span>

![Opción de compatibilidad con la compilación de Unity Plataforma universal de Windows](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="a6540-117">Si instaló Unity sin estas opciones, puede agregarlos a través del menú **' agregar módulos '** en Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="a6540-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opción de compatibilidad con la compilación de Windows de Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="a6540-119">Para empezar a trabajar con las versiones anteriores de XR integradas en Unity 2019,4 LTS, haga clic aquí:</span><span class="sxs-lookup"><span data-stu-id="a6540-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6540-120">Configurar XR integrado</span><span class="sxs-lookup"><span data-stu-id="a6540-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="a6540-121">Unity ha dejado de usar su compatibilidad integrada de XR heredada a partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="a6540-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="a6540-122">Aunque Unity 2019 ofrece un nuevo marco de trabajo de complemento de XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de los delimitadores espaciales de Azure con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="a6540-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="a6540-123">En Unity 2020, se admiten los delimitadores espaciales de Azure en el marco de trabajo del complemento XR.</span><span class="sxs-lookup"><span data-stu-id="a6540-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="a6540-124">Si va a desarrollar aplicaciones para HoloLens (1ª generación), estos auriculares siguen siendo compatibles con Unity 2019 LTS con XR integrado integrado para el ciclo de vida completo de Unity 2019 LTS a mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="a6540-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="a6540-125">Unity 2020,3 LTS</span><span class="sxs-lookup"><span data-stu-id="a6540-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="a6540-126">Si usa **Unity 2020,3 LTS**, puede usar el **complemento de Windows XR** para desarrollar aplicaciones de la realidad de HoloLens 2 y Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="a6540-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="a6540-127">Sin embargo, hay problemas conocidos que afectan a la estabilidad del holograma y otras características de HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="a6540-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="a6540-128">El envío de búfer de profundidad se ha revertido en las compilaciones de Unity 2020 recientes, lo que produce una inestabilidad grave de hologramas.</span><span class="sxs-lookup"><span data-stu-id="a6540-128">Depth buffer submission has regressed in recent Unity 2020 builds, which results in severe hologram instability.</span></span>
* <span data-ttu-id="a6540-129">Las aplicaciones de comunicación remota de aplicaciones holográficas que usan el destino de compilación Plataforma universal de Windows no funcionan.</span><span class="sxs-lookup"><span data-stu-id="a6540-129">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="a6540-130">El sistema de trabajos de gráficos de Unity está predeterminado en, aunque no es compatible con los proyectos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a6540-130">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="a6540-131">Si decide iniciar un nuevo proyecto en Unity 2020 hoy, asegúrese de seguir los próximos meses para las compilaciones de Unity actualizadas y las compilaciones del complemento de Windows XR antes de enviar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6540-131">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming months for updated Unity builds and Windows XR plugin builds before shipping your app.</span></span>  <span data-ttu-id="a6540-132">Esto garantizará que los usuarios experimenten una estabilidad de holograma adecuada.</span><span class="sxs-lookup"><span data-stu-id="a6540-132">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6540-133">Usar el complemento de Windows XR</span><span class="sxs-lookup"><span data-stu-id="a6540-133">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="a6540-134">Usar OpenXR</span><span class="sxs-lookup"><span data-stu-id="a6540-134">Using OpenXR</span></span>

<span data-ttu-id="a6540-135">Unity 2020,3 LTS también admite una versión preliminar pública del complemento **OpenXR de realidad mixta** .</span><span class="sxs-lookup"><span data-stu-id="a6540-135">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="a6540-136">El complemento OpenXR de realidad mixta es totalmente compatible con AR Foundation 4,0 y proporciona implementaciones ARPlaneManager y ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="a6540-136">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="a6540-137">Esto le permite escribir código de prueba de posicionamiento una vez que abarque los teléfonos y tabletas de HoloLens 2 y ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="a6540-137">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="a6540-138">Más adelante este año, **unity 2020,3 LTS con el complemento OpenXR** se convertirá en la configuración de Unity recomendada y las futuras características de HoloLens 2 en Unity solo se expondrán a través de este complemento.</span><span class="sxs-lookup"><span data-stu-id="a6540-138">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>  <span data-ttu-id="a6540-139">Aquí puede iniciar el proyecto aquí; sin embargo, si el proyecto tiene como destino HoloLens 2, actualmente se encontrará la estabilidad de los hologramas de Unity 2020 y otros problemas mencionados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a6540-139">You can start your project here for now - however, if your project targets HoloLens 2, you will currently encounter the Unity 2020 hologram stability and other issues listed above.</span></span>  <span data-ttu-id="a6540-140">Asegúrese de volver a consultar los próximos meses para obtener las compilaciones de Unity actualizadas y las compilaciones de complementos de OpenXR antes de enviar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6540-140">Be sure to check back in the coming months for updated Unity builds and OpenXR plugin builds before shipping your app.</span></span>  <span data-ttu-id="a6540-141">Esto garantizará que los usuarios experimenten una estabilidad de holograma adecuada.</span><span class="sxs-lookup"><span data-stu-id="a6540-141">This will ensure that your users experience proper hologram stability.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="a6540-142">Uso del complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="a6540-142">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="a6540-143">Unity 2021,1</span><span class="sxs-lookup"><span data-stu-id="a6540-143">Unity 2021.1</span></span>

<span data-ttu-id="a6540-144">Si está probando versiones anteriores de **Unity 2021,1** , debe avanzar al **complemento OpenXR**, ya que el complemento de Windows XR está en desuso.</span><span class="sxs-lookup"><span data-stu-id="a6540-144">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="a6540-145">A partir de Unity 2021,2, el complemento OpenXR será la única ruta de acceso para el desarrollo de realidad mixta, ya que el complemento de Windows XR ya no se admitirá.</span><span class="sxs-lookup"><span data-stu-id="a6540-145">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="a6540-146">Unity 2018,4 LTS</span><span class="sxs-lookup"><span data-stu-id="a6540-146">Unity 2018.4 LTS</span></span>

<span data-ttu-id="a6540-147">Si ya tiene un proyecto que usa Unity 2018,4 LTS, el motor de Unity seguirá siendo compatible durante 2 años después de su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="a6540-147">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="a6540-148">Unity 2018 LTS alcanzará el final del servicio en el muelle de 2021.</span><span class="sxs-lookup"><span data-stu-id="a6540-148">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
