---
title: Superficies
description: Aprenda a crear sensationss táctiles con visual, audio y seguimiento de mano articulados en la aplicación de ejemplo Surfaces.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, kit de herramientas de realidad mixta, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: bfb93574212dc9e6624d8baac636caf5c8df428a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009315"
---
# <a name="surfaces"></a><span data-ttu-id="f0123-104">Superficies</span><span class="sxs-lookup"><span data-stu-id="f0123-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="f0123-105">En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f0123-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="f0123-106">Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.</span><span class="sxs-lookup"><span data-stu-id="f0123-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="f0123-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  es una aplicación de ejemplo de código abierto de laboratorios de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f0123-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="f0123-108">Explora cómo podemos crear un repentino de uso táctil con visual, audio y seguimiento de mano totalmente articulado.</span><span class="sxs-lookup"><span data-stu-id="f0123-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Superficies](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="f0123-110">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="f0123-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="f0123-111">Grabado con HoloLens 2 mediante la captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f0123-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="f0123-112">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f0123-112">About the app</span></span>

<span data-ttu-id="f0123-113">Surfaces muestra cómo usar el sistema de entrada y los bloques de creación de un kit de herramientas de realidad mixta (MRTK) para crear una experiencia de aplicación para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f0123-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="f0123-114">En este proyecto, puede encontrar los ejemplos de:</span><span class="sxs-lookup"><span data-stu-id="f0123-114">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="f0123-115">Use el [sistema de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)de MRTK, un seguimiento manual o conjunto.</span><span class="sxs-lookup"><span data-stu-id="f0123-115">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="f0123-116">Use el [sombreador estándar](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) de MRTK para los gráficos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f0123-116">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="f0123-117">Puede usar los componentes de este proyecto para crear sus propias experiencias de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f0123-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="f0123-118">MR dev Days 2020-Lears from the MR Surfaces App</span><span class="sxs-lookup"><span data-stu-id="f0123-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="f0123-119">Información de la aplicación de superficies MR</span><span class="sxs-lookup"><span data-stu-id="f0123-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="f0123-120">Lars Simkins, Senior Designer, detrás de la aplicación Surfaces Surfaces, habla sobre el caso de diseño de la aplicación y los aspectos técnicos.</span><span class="sxs-lookup"><span data-stu-id="f0123-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="f0123-121">Repositorio del proyecto en GitHub</span><span class="sxs-lookup"><span data-stu-id="f0123-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="f0123-122">Descarga de la aplicación desde Microsoft Store en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f0123-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="f0123-123">(La aplicación solo está disponible en HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f0123-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f0123-124">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="f0123-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f0123-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f0123-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f0123-126">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f0123-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f0123-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f0123-127">See also</span></span>

* <span data-ttu-id="f0123-128">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="f0123-128">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="f0123-129">[Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="f0123-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="f0123-130">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="f0123-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="f0123-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="f0123-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
