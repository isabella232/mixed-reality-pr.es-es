---
title: Elección de una versión de Unity y un complemento XR
description: Manténgase al día con las recomendaciones más recientes de los complementos de Unity y XR para HoloLens desarrollo de aplicaciones.
author: hferrone
ms.author: v-hferrone
ms.date: 06/24/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: c69576e991f3fe32ae69fce10069ecdae65b3f9a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603686"
---
# <a name="choosing-a-unity-version-and-xr-plugin"></a><span data-ttu-id="71aa8-104">Elección de una versión de Unity y un complemento XR</span><span class="sxs-lookup"><span data-stu-id="71aa8-104">Choosing a Unity version and XR plugin</span></span>

<span data-ttu-id="71aa8-105">Aunque actualmente se recomienda instalar **Unity 2020.3 LTS** con el complemento openXR de Mixed Reality más reciente para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="71aa8-105">While we currently **recommend installing Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="unity-20203-lts-recommended"></a><span data-ttu-id="71aa8-106">Unity 2020.3 LTS (recomendado)</span><span class="sxs-lookup"><span data-stu-id="71aa8-106">Unity 2020.3 LTS (Recommended)</span></span>

<span data-ttu-id="71aa8-107">La configuración de Unity recomendada actualmente de Microsoft para el desarrollo de HoloLens 2 y Windows Mixed Reality es **Unity 2020.3 LTS** con la versión Mixed Reality complemento OpenXR más reciente.</span><span class="sxs-lookup"><span data-stu-id="71aa8-107">Microsoft’s current recommended Unity configuration for HoloLens 2 and Windows Mixed Reality development is **Unity 2020.3 LTS with the latest Mixed Reality OpenXR plugin**.</span></span> <span data-ttu-id="71aa8-108">Debe **usar** la versión de revisión de Unity 2020.3.8f1 o posterior para evitar problemas de rendimiento conocidos con compilaciones anteriores de 2020.3.</span><span class="sxs-lookup"><span data-stu-id="71aa8-108">You **must** use Unity patch release 2020.3.8f1 or later to avoid known performance issues with earlier 2020.3 builds.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71aa8-109">Unity 2020 no admite el destino HoloLens (1.ª generación).</span><span class="sxs-lookup"><span data-stu-id="71aa8-109">Unity 2020 does not support targeting HoloLens (1st gen).</span></span> <span data-ttu-id="71aa8-110">Estos cascos siguen siendo compatibles con **[Unity 2019 LTS](#unity-20194-lts)** con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="71aa8-110">These headsets remain supported in **[Unity 2019 LTS](#unity-20194-lts)** with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

<span data-ttu-id="71aa8-111">La mejor manera de instalar y administrar Unity es a través de **Unity Hub:**</span><span class="sxs-lookup"><span data-stu-id="71aa8-111">The best way to install and manage Unity is through the **Unity Hub**:</span></span>

1. <span data-ttu-id="71aa8-112">Instale <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub.**</a></span><span class="sxs-lookup"><span data-stu-id="71aa8-112">Install <a href="https://unity3d.com/get-unity/download" target="_blank">**Unity Hub**</a>.</span></span>
2. <span data-ttu-id="71aa8-113">Seleccione la **pestaña Installs (Instala)** y elija **Add (Agregar).**</span><span class="sxs-lookup"><span data-stu-id="71aa8-113">Select the **Installs** tab and choose **Add**.</span></span>
3. <span data-ttu-id="71aa8-114">Seleccione **Unity 2020.3 LTS** y haga clic **en Siguiente.**</span><span class="sxs-lookup"><span data-stu-id="71aa8-114">Select **Unity 2020.3 LTS** and click **Next**.</span></span>

![Instalación de la nueva versión de Unity Hub](images/unity-hub-img-01.png)

4. <span data-ttu-id="71aa8-116">Compruebe los siguientes componentes en **"Plataformas":**</span><span class="sxs-lookup"><span data-stu-id="71aa8-116">Check the following components under **'Platforms'**:</span></span>
    * <span data-ttu-id="71aa8-117">**Compatibilidad con la compilación de la Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="71aa8-117">**Universal Windows Platform Build Support**</span></span>
    * <span data-ttu-id="71aa8-118">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="71aa8-118">**Windows Build Support (IL2CPP)**</span></span>

![Opción de compatibilidad con la compilación de la Plataforma universal de Windows para Unity](../images/Unity_Install_Option_UWP.png)

5. <span data-ttu-id="71aa8-120">Si anteriormente instaló Unity sin estas opciones, puede agregarlas a través del menú **"Agregar módulos"** en Unity Hub:</span><span class="sxs-lookup"><span data-stu-id="71aa8-120">If you previously installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub:</span></span>

![Opción de compatibilidad con la compilación de Windows para Unity](../images/Unity_Install_Option_UWP2.png)

<span data-ttu-id="71aa8-122">Una vez que tenga Unity 2020.3 instalado, empezar a crear un proyecto o actualizar uno existente mediante el complemento Mixed Reality OpenXR:</span><span class="sxs-lookup"><span data-stu-id="71aa8-122">Once you have Unity 2020.3 installed, get started creating a project or upgrading an existing project using the Mixed Reality OpenXR plugin:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71aa8-123">Configuración del proyecto con el complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="71aa8-123">Set up your project with the OpenXR plugin</span></span>](xr-project-setup.md?tabs=openxr)

> [!NOTE]
> <span data-ttu-id="71aa8-124">Aunque se recomienda usar OpenXR para todos los proyectos nuevos, Unity 2020.3 LTS también admite Windows [complemento XR.](xr-project-setup.md?tabs=windowsxr)</span><span class="sxs-lookup"><span data-stu-id="71aa8-124">While we recommend using OpenXR for all new projects, Unity 2020.3 LTS also supports the [Windows XR plugin](xr-project-setup.md?tabs=windowsxr).</span></span> <span data-ttu-id="71aa8-125">Este complemento es totalmente compatible, aunque no recibirá nuevas características como la compatibilidad con AR Foundation 4.0.</span><span class="sxs-lookup"><span data-stu-id="71aa8-125">This plugin is fully supported, although it won't receive new features such as AR Foundation 4.0 support.</span></span>

## <a name="unity-20194-lts"></a><span data-ttu-id="71aa8-126">Unity 2019.4 LTS</span><span class="sxs-lookup"><span data-stu-id="71aa8-126">Unity 2019.4 LTS</span></span>

<span data-ttu-id="71aa8-127">Si necesita usar Unity 2019, puede usar **Unity 2019 LTS con XR integrado heredado.**</span><span class="sxs-lookup"><span data-stu-id="71aa8-127">If you need to use Unity 2019, you can use **Unity 2019 LTS with Legacy Built-in XR**.</span></span> <span data-ttu-id="71aa8-128">Para empezar a trabajar con XR integrado heredado en Unity 2019.4 LTS, haga clic aquí:</span><span class="sxs-lookup"><span data-stu-id="71aa8-128">To get started with Legacy Built-in XR in Unity 2019.4 LTS, click here:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71aa8-129">Configuración del proyecto con XR integrado heredado</span><span class="sxs-lookup"><span data-stu-id="71aa8-129">Set up your project with Legacy Built-in XR</span></span>](xr-project-setup.md?tabs=legacy)

> [!NOTE]
> <span data-ttu-id="71aa8-130">Unity ha dejado de ser compatible con XR integrado heredado a partir de Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="71aa8-130">Unity has deprecated its Legacy Built-in XR support as of Unity 2019.</span></span>  <span data-ttu-id="71aa8-131">Aunque Unity 2019 ofrece un nuevo marco de complementos XR, Microsoft no recomienda actualmente esa ruta de acceso en Unity 2019 debido a las incompatibilidades de Azure Spatial Anchors con AR Foundation 2.</span><span class="sxs-lookup"><span data-stu-id="71aa8-131">While Unity 2019 does offer a new XR Plug-in framework, Microsoft is not currently recommending that path in Unity 2019 due to Azure Spatial Anchors incompatibilities with AR Foundation 2.</span></span>  <span data-ttu-id="71aa8-132">En Unity 2020, Azure Spatial Anchors se admite en el marco del complemento XR.</span><span class="sxs-lookup"><span data-stu-id="71aa8-132">In Unity 2020, Azure Spatial Anchors is supported within the XR Plug-in framework.</span></span>

<span data-ttu-id="71aa8-133">Si está desarrollando aplicaciones para HoloLens (1.ª generación), estos cascos seguirán siendo compatibles con Unity 2019 LTS con XR integrado heredado para el ciclo de vida completo de Unity 2019 LTS hasta mediados de 2022.</span><span class="sxs-lookup"><span data-stu-id="71aa8-133">If you are developing apps for HoloLens (1st gen), these headsets remain supported in Unity 2019 LTS with Legacy Built-in XR for the full lifecycle of Unity 2019 LTS through mid-2022.</span></span>

## <a name="unity-20212"></a><span data-ttu-id="71aa8-134">Unity 2021.2</span><span class="sxs-lookup"><span data-stu-id="71aa8-134">Unity 2021.2</span></span>

<span data-ttu-id="71aa8-135">Si está probando las primeras compilaciones de **Unity 2021.2,** introducción al Mixed Reality [**de OpenXR.**](xr-project-setup.md?tabs=openxr)</span><span class="sxs-lookup"><span data-stu-id="71aa8-135">If you are trying out early **Unity 2021.2** builds, get started with the [**Mixed Reality OpenXR plugin**](xr-project-setup.md?tabs=openxr).</span></span> <span data-ttu-id="71aa8-136">El complemento OpenXR es la única ruta de acceso para el desarrollo de realidad mixta en Unity 2021.2 y versiones posteriores, ya que la versión final de Unity para admitir el complemento XR de Windows era Unity 2021.1.</span><span class="sxs-lookup"><span data-stu-id="71aa8-136">The OpenXR plugin is the only path for mixed reality development in Unity 2021.2 and later, as the final Unity version to support the Windows XR plugin was Unity 2021.1.</span></span>

## <a name="unity-20184-lts"></a><span data-ttu-id="71aa8-137">Unity 2018.4 LTS</span><span class="sxs-lookup"><span data-stu-id="71aa8-137">Unity 2018.4 LTS</span></span>

<span data-ttu-id="71aa8-138">Unity 2018.4 LTS ha llegado al final de la ventana de soporte técnico de Long-Term de dos años de Unity y ya no recibe actualizaciones de Unity, aunque los proyectos seguirán en ejecución.</span><span class="sxs-lookup"><span data-stu-id="71aa8-138">Unity 2018.4 LTS has reached the end of Unity's two-year Long-Term Support window and is no longer receiving updates from Unity, although your projects will continue to run.</span></span>

<span data-ttu-id="71aa8-139">Si tiene un proyecto de Unity 2018, debe considerar la posibilidad de planear una migración hacia Unity 2020.3 LTS y el complemento OpenXR Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="71aa8-139">If you have a Unity 2018 project, you should consider planning for a migration forward to Unity 2020.3 LTS and the Mixed Reality OpenXR plugin.</span></span>