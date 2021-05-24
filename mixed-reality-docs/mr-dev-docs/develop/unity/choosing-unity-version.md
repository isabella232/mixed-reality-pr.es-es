---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día de las recomendaciones más recientes del complemento Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 03/26/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: febeb46972935a02d9c945e2a0cafabebedd0715
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333387"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="b860a-104">Elección de una versión de Unity y un complemento XR</span><span class="sxs-lookup"><span data-stu-id="b860a-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="b860a-105">Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="b860a-105">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20194-lts-recommended"></a><span data-ttu-id="b860a-106">Unity 2019.4 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="b860a-106">Unity 2019.4 LTS (Recommended)</span></span>

<span data-ttu-id="b860a-107">La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2019.4 LTS** con compatibilidad con XR integrada heredada.</span><span class="sxs-lookup"><span data-stu-id="b860a-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2019.4 LTS using Legacy Built-in XR** support.</span></span>

<span data-ttu-id="b860a-108">La mejor manera de instalar y administrar Unity es a través de <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub].</a></span><span class="sxs-lookup"><span data-stu-id="b860a-108">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">[Unity Hub]</a>.</span></span> <span data-ttu-id="b860a-109">Cuando esté instalado, abra Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="b860a-109">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="b860a-110">Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**</span><span class="sxs-lookup"><span data-stu-id="b860a-110">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="b860a-111">Seleccione Unity 2019.4 LTS y haga clic en **Siguiente.**</span><span class="sxs-lookup"><span data-stu-id="b860a-111">Select Unity 2019.4 LTS and click **Next**</span></span>

![Nueva versión de la nueva versión de la instancia de Unity Hub](images/unity-hub-img-01.png)

3. <span data-ttu-id="b860a-113">Compruebe los siguientes componentes en **"Plataformas".**</span><span class="sxs-lookup"><span data-stu-id="b860a-113">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="b860a-114">**Compatibilidad con la compilación de la Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="b860a-114">**Universal Windows Platform Build Support**</span></span> 
    * <span data-ttu-id="b860a-115">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="b860a-115">**Windows Build Support (IL2CPP)**</span></span>

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="b860a-117">Si ha instalado Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="b860a-117">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="b860a-119">Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:</span><span class="sxs-lookup"><span data-stu-id="b860a-119">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b860a-120">Configuración de XR integrado heredado</span><span class="sxs-lookup"><span data-stu-id="b860a-120">Set up Legacy Built-in XR</span></span>](legacy-xr-support.md)

> [!NOTE]
> <span data-ttu-id="b860a-121">Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="b860a-121">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="b860a-122">Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="b860a-122">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="b860a-123">En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.</span><span class="sxs-lookup"><span data-stu-id="b860a-123">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="b860a-124">Si va a desarrollar aplicaciones para HoloLens (1ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="b860a-124">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20203-lts"></a><span data-ttu-id="b860a-125">Unity 2020.3 LTS</span><span class="sxs-lookup"><span data-stu-id="b860a-125">Unity 2020.3 LTS</span></span> 

<span data-ttu-id="b860a-126">Si usa **Unity 2020.3 LTS,** puede usar el complemento **XR** de Windows para desarrollar HoloLens 2 y Windows Mixed Reality aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b860a-126">If you’re using **Unity 2020.3 LTS**, you can use the **Windows XR plugin** to develop HoloLens 2 and Windows Mixed Reality applications.</span></span>

<span data-ttu-id="b860a-127">Sin embargo, hay problemas conocidos que afectan a la estabilidad del holograma y otras características en HoloLens 2:</span><span class="sxs-lookup"><span data-stu-id="b860a-127">However, there are known issues that affect hologram stability and other features on HoloLens 2:</span></span> 

* <span data-ttu-id="b860a-128">Las aplicaciones de comunicación remota de aplicaciones holográficas que usan Plataforma universal de Windows destino de compilación no funcionan.</span><span class="sxs-lookup"><span data-stu-id="b860a-128">Holographic app remoting applications using the Universal Windows Platform build target are not working.</span></span>
* <span data-ttu-id="b860a-129">El sistema de trabajos gráficos de Unity está predeterminado, aunque no sea compatible con los proyectos de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b860a-129">The Unity graphics jobs system is defaulted on, even though it is not compatible with HoloLens projects.</span></span>

<span data-ttu-id="b860a-130">Si decide usar Unity 2020, asegúrese de actualizar a Unity 2020.3.6f1 o versiones posteriores para garantizar que el usuario experimente una estabilidad adecuada del holograma.</span><span class="sxs-lookup"><span data-stu-id="b860a-130">If you choose to use Unity 2020, be sure to upgrade to Unity 2020.3.6f1 or later versions to ensure your user experience proper hologram stability.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b860a-131">Uso del complemento XR de Windows</span><span class="sxs-lookup"><span data-stu-id="b860a-131">Using the Windows XR plugin</span></span>](windows-xr-plugin.md)

### <a name="using-openxr"></a><span data-ttu-id="b860a-132">Uso de OpenXR</span><span class="sxs-lookup"><span data-stu-id="b860a-132">Using OpenXR</span></span>

<span data-ttu-id="b860a-133">Unity 2020.3 LTS también admite una versión preliminar pública del Mixed Reality **complemento OpenXR.**</span><span class="sxs-lookup"><span data-stu-id="b860a-133">Unity 2020.3 LTS also supports a public preview of the **Mixed Reality OpenXR** plugin.</span></span>

<span data-ttu-id="b860a-134">El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager.</span><span class="sxs-lookup"><span data-stu-id="b860a-134">The Mixed Reality OpenXR plugin fully supports AR Foundation 4.0, providing ARPlaneManager and ARRaycastManager implementations.</span></span> <span data-ttu-id="b860a-135">Esto le permite escribir código de prueba de acceso una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.</span><span class="sxs-lookup"><span data-stu-id="b860a-135">This enables you to write hit-testing code once that then spans HoloLens 2 and ARCore/ARKit phones and tablets.</span></span> 

<span data-ttu-id="b860a-136">Más adelante este año, **Unity 2020.3 LTS** con el complemento OpenXR se convertirá en la configuración recomendada de Unity y las futuras características de HoloLens 2 en Unity solo se mostrarán a través de este complemento.</span><span class="sxs-lookup"><span data-stu-id="b860a-136">Later this year, **Unity 2020.3 LTS with the OpenXR plugin** will become the recommended Unity configuration, and future HoloLens 2 features in Unity will be exposed only through this plugin.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b860a-137">Uso del complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="b860a-137">Using the OpenXR plugin</span></span>](openxr-getting-started.md)

## <a name="unity-20211"></a><span data-ttu-id="b860a-138">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="b860a-138">Unity 2021.1</span></span>

<span data-ttu-id="b860a-139">Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso allí.</span><span class="sxs-lookup"><span data-stu-id="b860a-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="b860a-140">A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="b860a-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="b860a-141">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="b860a-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="b860a-142">Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante dos años después de su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="b860a-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="b860a-143">Unity 2018 LTS llegará al final del servicio en la primavera de 2021.</span><span class="sxs-lookup"><span data-stu-id="b860a-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
