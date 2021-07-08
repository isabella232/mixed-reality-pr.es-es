---
title: Configuración del proyecto con Unreal
description: Obtenga información sobre cómo configurar el proyecto con la versión más reciente de Unreal Engine y Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realidad mixta, desarrollo, características, nuevo proyecto, emulador, documentación, guías, hologramas, desarrollo de juegos, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394617"
---
# <a name="setting-up-your-unreal-project"></a><span data-ttu-id="14ab9-104">Configuración del proyecto con Unreal</span><span class="sxs-lookup"><span data-stu-id="14ab9-104">Setting up your Unreal project</span></span>

<span data-ttu-id="14ab9-105">Se recomienda instalar [Unreal Engine, versión 4.25 ](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o posterior, para aprovechar al máximo la compatibilidad integrada de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="14ab9-105">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

<span data-ttu-id="14ab9-106">Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**.</span><span class="sxs-lookup"><span data-stu-id="14ab9-106">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** and click **Options**.</span></span> <span data-ttu-id="14ab9-107">En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="14ab9-107">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
<span data-ttu-id="14ab9-108">![Opción de instalación no real de HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span><span class="sxs-lookup"><span data-stu-id="14ab9-108">![Unreal Install Option HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)</span></span>

## <a name="import-mixed-reality-toolkit-for-unreal"></a><span data-ttu-id="14ab9-109">Importación de Mixed Reality Toolkit para Unreal</span><span class="sxs-lookup"><span data-stu-id="14ab9-109">Import Mixed Reality Toolkit for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

<span data-ttu-id="14ab9-111">Mixed Reality Toolkit (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="14ab9-111">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="14ab9-112">MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="14ab9-112">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="14ab9-113">El kit de herramientas está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="14ab9-113">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

<span data-ttu-id="14ab9-114">Para la instalación, le recomendamos que complete la [sección Introducción](unreal-development-overview.md#1-getting-started) de nuestro [recorrido de desarrollo de Unreal](unreal-development-overview.md) seleccionado.</span><span class="sxs-lookup"><span data-stu-id="14ab9-114">For installation, we recommend completing the [Getting Started section](unreal-development-overview.md#1-getting-started) of our curated [Unreal development journey](unreal-development-overview.md).</span></span> <span data-ttu-id="14ab9-115">Si ya sigue el recorrido de desarrollo de Unreal, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](tutorials/unreal-uxt-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="14ab9-115">If you're already following the Unreal development journey, finish up the rest of the setup steps listed below and continue on to the [HoloLens 2 Getting Started tutorials](tutorials/unreal-uxt-ch1.md).</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="14ab9-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagen del logotipo de Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="14ab9-116"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity logo image](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="14ab9-117">**Mixed Reality Toolkit - Unreal (GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="14ab9-117">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="14ab9-118">Si no desea usar MRTK para Unreal, tendrá que crear scripts para todas las interacciones y comportamientos.</span><span class="sxs-lookup"><span data-stu-id="14ab9-118">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>