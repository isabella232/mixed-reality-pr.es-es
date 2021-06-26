---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día de las recomendaciones más recientes del complemento Unity y XR para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: 646a0ec3b3b332b038509cba39caa085c1590c1a
ms.sourcegitcommit: 593e8f80297ac0b5eccb2488d3f333885eab9adf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112921433"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="405ba-104">Elección de una versión de Unity y un complemento XR</span><span class="sxs-lookup"><span data-stu-id="405ba-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="405ba-105">Aunque actualmente se recomienda instalar **Unity 2020.3 LTS** con el complemento openXR de Mixed Reality más reciente para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="405ba-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="405ba-106">Unity 2020.3 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="405ba-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="405ba-107">La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2020.3 LTS** con la versión más reciente Mixed Reality complemento OpenXR.</span><span class="sxs-lookup"><span data-stu-id="405ba-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="405ba-108">DEBE usar la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de la versión 2020.3.</span><span class="sxs-lookup"><span data-stu-id="405ba-108">You MUST use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="405ba-109">Unity 2020 no admite el destino HoloLens (1ª generación).</span><span class="sxs-lookup"><span data-stu-id="405ba-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="405ba-110">Estos cascos siguen siendo compatibles con **[Unity 2019 LTS](#unity-20194-lts)** con XR integrado heredado durante el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="405ba-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>
>
> [!NOTE]
> <span data-ttu-id="405ba-111">Algunos paquetes aún no son compatibles con proyectos de realidad mixta en Unity 2020 LTS:</span><span class="sxs-lookup"><span data-stu-id="405ba-111">Some packages are not yet compatible with mixed reality projects in Unity 2020 LTS:</span></span>
> 
> * <span data-ttu-id="405ba-112">La canalización de representación universal (URP) 10.5.0 o anterior tiene un problema de rendimiento conocido en HoloLens 2 dispositivos.</span><span class="sxs-lookup"><span data-stu-id="405ba-112">The Universal Rendering Pipeline (URP) 10.5.0 or older has a known performance issue on HoloLens 2 devices.</span></span> <span data-ttu-id="405ba-113">_(corregido en la próxima versión de URP)_</span><span class="sxs-lookup"><span data-stu-id="405ba-113">_(fixed in the next URP release)_</span></span>
> * <span data-ttu-id="405ba-114">Azure Remote Rendering ha enviado aún una versión actualizada compatible con Unity 2020.</span><span class="sxs-lookup"><span data-stu-id="405ba-114">Azure Remote Rendering has not yet shipped an updated release supporting Unity 2020.</span></span>
>
> <span data-ttu-id="405ba-115">Si el proyecto de Unity usa la canalización de representación universal o Azure Remote Rendering, se recomienda no actualizar el proyecto a Unity 2020 hasta que haya paquetes actualizados disponibles.</span><span class="sxs-lookup"><span data-stu-id="405ba-115">If your Unity project uses the Universal Rendering Pipeline or Azure Remote Rendering, we recommend holding off on upgrading your project to Unity 2020 until updated packages are available.</span></span>

<span data-ttu-id="405ba-116">La mejor manera de instalar y administrar Unity es mediante <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span><span class="sxs-lookup"><span data-stu-id="405ba-116">The best way to install and manage Unity is through the <a href="https://unity3d.com/get-unity/download" target="_blank">Unity Hub</a>.</span></span> <span data-ttu-id="405ba-117">Cuando esté instalado, abra Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="405ba-117">When it's installed, open Unity Hub:</span></span>

1. <span data-ttu-id="405ba-118">Seleccione la **pestaña Installs (Instala)** y elija **ADD (AGREGAR).**</span><span class="sxs-lookup"><span data-stu-id="405ba-118">Select the **Installs** tab and choose **ADD**</span></span>
2. <span data-ttu-id="405ba-119">Seleccione Unity 2020.3 LTS y haga clic en **Siguiente.**</span><span class="sxs-lookup"><span data-stu-id="405ba-119">Select Unity 2020.3 LTS and click **Next**</span></span>

![Nueva versión de la nueva versión de la instancia de Unity Hub](images/unity-hub-img-01.png)

3. <span data-ttu-id="405ba-121">Compruebe los siguientes componentes en **"Plataformas".**</span><span class="sxs-lookup"><span data-stu-id="405ba-121">Check following components under **'Platforms'**</span></span>
    * <span data-ttu-id="405ba-122">**Compatibilidad con la compilación de la Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="405ba-122">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="405ba-123">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="405ba-123">**Windows Build Support (IL2CPP)**</span></span>

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

4. <span data-ttu-id="405ba-125">Si ha instalado Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="405ba-125">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="405ba-127">Uso del complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="405ba-127">Using the OpenXR plugin</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="405ba-128">Aunque se recomienda usar OpenXR para todos los proyectos nuevos, Unity 2020.3 LTS también admite el complemento [XR de Windows.](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="405ba-128">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=windowsxr).</span></span> <span data-ttu-id="405ba-129">Este complemento es totalmente compatible, aunque no recibirá nuevas características como la compatibilidad con AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="405ba-129">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="405ba-130">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="405ba-130">Unity 2019.4 LTS</span></span>

<span data-ttu-id="405ba-131">Si necesita usar Unity 2019, puede usar **Unity 2019 LTS con XR integrado heredado.**</span><span class="sxs-lookup"><span data-stu-id="405ba-131">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="405ba-132">Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:</span><span class="sxs-lookup"><span data-stu-id="405ba-132">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="405ba-133">Configuración de XR integrado heredado</span><span class="sxs-lookup"><span data-stu-id="405ba-133">Set up Legacy Built-in XR</span></span>](/windows/mixed-reality/develop/unity/xr-project-setup?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="405ba-134">Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="405ba-134">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="405ba-135">Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="405ba-135">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="405ba-136">En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.</span><span class="sxs-lookup"><span data-stu-id="405ba-136">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="405ba-137">Si va a desarrollar aplicaciones para HoloLens (1ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="405ba-137">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20211"></a><span data-ttu-id="405ba-138">Unity 2021.1</span><span class="sxs-lookup"><span data-stu-id="405ba-138">Unity 2021.1</span></span>

<span data-ttu-id="405ba-139">Si está probando las primeras compilaciones de **Unity 2021.1,** debe pasar al complemento **OpenXR,** ya que el complemento XR de Windows está en desuso.</span><span class="sxs-lookup"><span data-stu-id="405ba-139">If you are trying out early **Unity 2021.1** builds, you should move forward to the **OpenXR plugin**, as the Windows XR plugin is deprecated there.</span></span>  <span data-ttu-id="405ba-140">A partir de Unity 2021.2, el complemento OpenXR será la única ruta de acceso para el desarrollo de Mixed Reality, ya que ya no se admite el complemento XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="405ba-140">Starting in Unity 2021.2, the OpenXR plugin will be the only path for Mixed Reality development, as the Windows XR plugin will no longer be supported.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="405ba-141">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="405ba-141">Unity 2018.4 LTS</span></span>

<span data-ttu-id="405ba-142">Si ya tiene un proyecto con Unity 2018.4 LTS, el motor de Unity seguirá siendo compatible durante 2 años después de su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="405ba-142">If you already have a project using Unity 2018.4 LTS, your Unity engine continues to be supported for 2 years after its release.</span></span>  <span data-ttu-id="405ba-143">Unity 2018 LTS llegará al final del servicio en la primavera de 2021.</span><span class="sxs-lookup"><span data-stu-id="405ba-143">Unity 2018 LTS will reach end of service in the spring of 2021.</span></span>
