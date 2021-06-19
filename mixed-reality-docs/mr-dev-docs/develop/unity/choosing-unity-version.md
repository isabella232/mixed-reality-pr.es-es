---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día con las recomendaciones más recientes de los complementos de Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, unity
ms.openlocfilehash: 452692b1be98459cc242833149b1cfd91f0f4d4a
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394425"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="f3ab6-104">Elección de una versión de Unity y un complemento XR</span><span class="sxs-lookup"><span data-stu-id="f3ab6-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="f3ab6-105">Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="f3ab6-106">Unity 2019.4 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="f3ab6-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="f3ab6-107">La configuración de Unity recomendada actualmente de Microsoft para el desarrollo HoloLens 2 y Windows Mixed Reality es **Unity 2019.4 LTS** con compatibilidad con XR integrada heredada.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="f3ab6-108">La mejor manera de instalar y administrar Unity es a través de <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub].</a></span><span class="sxs-lookup"><span data-stu-id="f3ab6-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="f3ab6-109">Cuando esté instalado, abra Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="f3ab6-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="f3ab6-110">Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="f3ab6-111">Seleccione Unity 2019.4 LTS y haga clic en **Siguiente.**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nueva versión de la instancia de Unity Hub](images/unity-hub-img-2019.png)

3. <span data-ttu-id="f3ab6-113">Compruebe los siguientes componentes en **"Plataformas".**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="f3ab6-114">**Compatibilidad con la compilación de la Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="f3ab6-115">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-115">**Windows Build Support (IL2CPP)**</span></span>

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](images/Unity_Install_Option_UWP_2019.png)

4. <span data-ttu-id="f3ab6-117">Si instaló Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="f3ab6-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opción de compatibilidad con la compilación de Windows para Unity](images/Unity_Install_Option_UWP2_2019.png)

<span data-ttu-id="f3ab6-119">Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:</span><span class="sxs-lookup"><span data-stu-id="f3ab6-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3ab6-120">Configuración de XR integrado heredado</span><span class="sxs-lookup"><span data-stu-id="f3ab6-120">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="f3ab6-121">Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="f3ab6-122">Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="f3ab6-123">En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="f3ab6-124">Si va a desarrollar aplicaciones para HoloLens (1.ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="f3ab6-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="f3ab6-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="f3ab6-126">Si usa **Unity 2020.3 LTS,** la recomendación actual de Microsoft es la Mixed Reality **complemento OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="f3ab6-126">If you’re using **Unity 2020.3 LTS**, Microsoft’s current recommendation is the latest **Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="f3ab6-127">DEBE usar la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de 2020.3.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-127">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

<span data-ttu-id="f3ab6-128">El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-128">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="f3ab6-129">Esto le permite escribir código de prueba de acceso una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-129">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span>

<span data-ttu-id="f3ab6-130">Sin embargo, hay problemas conocidos que afectan a los proyectos de Unity 2020 LTS:</span><span class="sxs-lookup"><span data-stu-id="f3ab6-130">However, there are known issues that affect Unity 2020 LTS projects:</span></span>

* <span data-ttu-id="f3ab6-131">La canalización de representación universal (URP) 10.5.0 o anterior tiene penalizaciones de rendimiento en HoloLens 2 dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-131">The Universal Rendering Pipeline (URP) 10.5.0 or older has performance penalties on HoloLens 2 devices.</span></span>

<span data-ttu-id="f3ab6-132">Si decide iniciar un nuevo proyecto en Unity 2020 hoy mismo, asegúrese de realizar un seguimiento en las próximas semanas de las compilaciones de Unity y los paquetes URP actualizados antes de enviar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-132">If you choose to start a new project in Unity 2020 today, be sure to follow up over the coming weeks for updated Unity builds and URP packages before shipping your app.</span></span>  <span data-ttu-id="f3ab6-133">Esto garantizará que los usuarios experimente la estabilidad adecuada del holograma.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-133">This will ensure that your users experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3ab6-134">Uso del complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="f3ab6-134">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

## <a name="unity-20211"></a><span data-ttu-id="f3ab6-135">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="f3ab6-135">Unity 2021.1</span></span>

<span data-ttu-id="f3ab6-136">Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso allí.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-136">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="f3ab6-137">A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-137">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="f3ab6-138">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="f3ab6-138">Unity 2018.4 LTS</span></span>

<span data-ttu-id="f3ab6-139">Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante dos años después de su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-139">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="f3ab6-140">Unity 2018 LTS llegará al final del servicio en la primavera de 2021.</span><span class="sxs-lookup"><span data-stu-id="f3ab6-140">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>