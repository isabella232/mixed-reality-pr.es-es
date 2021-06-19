---
title: Elección de la canalización para desarrolladores
description: Manténgase al día de las recomendaciones de canalización de desarrollo de Unity más recientes para el desarrollo de aplicaciones de HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394559"
---
# <a name="choosing-your-developer-pipeline"></a><span data-ttu-id="e9834-104">Elección de la canalización para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="e9834-104">Choosing your developer pipeline</span></span>

![Banner del logotipo de Unity](../images/unity_logo_banner.png)<br>

<span data-ttu-id="e9834-106">Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.</span><span class="sxs-lookup"><span data-stu-id="e9834-106">While we currently **recommend installing Unity 2019.4 LTS and using Legacy Built-in XR** for Mixed Reality development, you can build apps with other Unity configurations as well.</span></span>

## <a name="mixed-reality-toolkit-recommended"></a><span data-ttu-id="e9834-107">Mixed Reality Toolkit (recomendado)</span><span class="sxs-lookup"><span data-stu-id="e9834-107">Mixed Reality Toolkit (Recommended)</span></span>

<span data-ttu-id="e9834-108">La configuración de Unity recomendada actualmente de Microsoft para HoloLens 2 es Mixed Reality Toolkit...</span><span class="sxs-lookup"><span data-stu-id="e9834-108">Microsoft’s current recommended Unity configuration for HoloLens 2 is the Mixed Reality Toolkit...</span></span>

### <a name="install-the-mixed-reality-feature-tool"></a><span data-ttu-id="e9834-109">Instalación de la herramienta Mixed Reality características</span><span class="sxs-lookup"><span data-stu-id="e9834-109">Install the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="e9834-110">La [herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md) es una nueva manera de que los desarrolladores detecten y agreguen paquetes de características de Mixed Reality en proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="e9834-110">The [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) is a new way for developers to discover and add Mixed Reality feature packages into Unity projects.</span></span> 

<span data-ttu-id="e9834-111">Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="e9834-111">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="e9834-112">Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto que elija.</span><span class="sxs-lookup"><span data-stu-id="e9834-112">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e9834-113">Importación de Mixed Reality Toolkit para Unity</span><span class="sxs-lookup"><span data-stu-id="e9834-113">Importing the Mixed Reality Toolkit for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="e9834-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="e9834-115">[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> 

* <span data-ttu-id="e9834-116">Instale el paquete de Mixed Reality Toolkit según las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md#system-requirements) y seleccione el paquete **Mixed Reality Toolkit Foundation**.</span><span class="sxs-lookup"><span data-stu-id="e9834-116">Install the Mixed Reality Toolkit package by following the [installation and usage instructions](welcome-to-mr-feature-tool.md#system-requirements) and selecting the **Mixed Reality Toolkit Foundation** package.</span></span>

<span data-ttu-id="e9834-117">Se recomienda que complete la sección Introducción de nuestros recorridos de desarrollo de [HoloLens](unity-development-overview.md#1-getting-started) o [VR](unity-development-wmr-overview.md#1-getting-started) seleccionados.</span><span class="sxs-lookup"><span data-stu-id="e9834-117">We recommend completing the getting started section in our curated [HoloLens](unity-development-overview.md#1-getting-started) or [VR](unity-development-wmr-overview.md#1-getting-started) development journeys.</span></span> <span data-ttu-id="e9834-118">Si ya sigue el recorrido de desarrollo de Unity para HoloLens, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](tutorials/mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="e9834-118">If you're already following the Unity development for HoloLens journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/mr-learning-base-01.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9834-119">Tenga en cuenta que las instrucciones de instalación están destinadas a la combinación estable más reciente de las versiones de MRTK y Unity, que son **MRTK 2.6.1** y **Unity 2019.4 LTS**.</span><span class="sxs-lookup"><span data-stu-id="e9834-119">Note that installation instructions are targeted for the latest stable combination of MRTK and Unity releases, which are **MRTK 2.6.1** and **Unity 2019.4 LTS**.</span></span>

> [!NOTE]
> <span data-ttu-id="e9834-120">Si no quiere usar MRTK para Unity, tendrá que [crear scripts para todas las interacciones y comportamientos](configure-unity-project.md).</span><span class="sxs-lookup"><span data-stu-id="e9834-120">If you don't want to use MRTK for Unity, you'll need to [script all interactions and behaviors yourself](configure-unity-project.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="e9834-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner de Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="e9834-121"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity banner](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="e9834-122">**Mixed Reality Toolkit - Unity (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="e9834-122">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a><span data-ttu-id="e9834-123">Manual</span><span class="sxs-lookup"><span data-stu-id="e9834-123">Manual</span></span> 

<span data-ttu-id="e9834-124">Tbd...</span><span class="sxs-lookup"><span data-stu-id="e9834-124">TBD...</span></span>