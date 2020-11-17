---
title: Superficies
description: Surfaces es una aplicación de ejemplo de código abierto de laboratorios de diseño de la realidad mixta de Microsoft. Explora cómo podemos crear un repentino de uso táctil con visual, audio y seguimiento de mano totalmente articulado.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, diseño, aplicación de ejemplo, controles, MRTK, kit de herramientas de realidad mixta, Unity, aplicaciones de ejemplo, aplicaciones de ejemplo, código abierto, Microsoft Store, HoloLens, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: c20ea17b20c867d9bf1da0d5f6244e36f2abbf27
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678524"
---
# <a name="surfaces"></a><span data-ttu-id="f4761-105">Superficies</span><span class="sxs-lookup"><span data-stu-id="f4761-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="f4761-106">En este artículo se describe un ejemplo de exploración que hemos creado en los [laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDesignLabs_Unity), un lugar donde compartimos nuestros aprendizajes sobre y sugerencias para el desarrollo de aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f4761-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="f4761-107">Los artículos y el código relacionados con el diseño evolucionarán a medida que se realizan nuevas detecciones.</span><span class="sxs-lookup"><span data-stu-id="f4761-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="f4761-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  es una aplicación de ejemplo de código abierto de laboratorios de diseño de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f4761-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="f4761-109">Explora cómo podemos crear un repentino de uso táctil con visual, audio y seguimiento de mano totalmente articulado.</span><span class="sxs-lookup"><span data-stu-id="f4761-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Superficies](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="f4761-111">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="f4761-111">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="f4761-112">Grabado con HoloLens 2 mediante la captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f4761-112">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="f4761-113">Acerca de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f4761-113">About the app</span></span>
<span data-ttu-id="f4761-114">Surfaces muestra cómo usar el sistema de entrada y los bloques de creación de un kit de herramientas de realidad mixta (MRTK) para crear una experiencia de aplicación para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f4761-114">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="f4761-115">En este proyecto, puede encontrar los ejemplos de:</span><span class="sxs-lookup"><span data-stu-id="f4761-115">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="f4761-116">Use el [sistema de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)de MRTK, un seguimiento manual o conjunto.</span><span class="sxs-lookup"><span data-stu-id="f4761-116">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="f4761-117">Use el [sombreador estándar](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) de MRTK para los gráficos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f4761-117">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="f4761-118">Puede usar los componentes de este proyecto para crear sus propias experiencias de aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="f4761-118">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="f4761-119">MR dev Days 2020-Lears from the MR Surfaces App</span><span class="sxs-lookup"><span data-stu-id="f4761-119">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="f4761-120">Información de la aplicación de superficies MR</span><span class="sxs-lookup"><span data-stu-id="f4761-120">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="f4761-121">Lars Simkins, Senior Designer, detrás de la aplicación Surfaces Surfaces, habla sobre el caso de diseño de la aplicación y los aspectos técnicos.</span><span class="sxs-lookup"><span data-stu-id="f4761-121">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="f4761-122">Repositorio del proyecto en GitHub</span><span class="sxs-lookup"><span data-stu-id="f4761-122">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="f4761-123">Descarga de la aplicación desde Microsoft Store en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="f4761-123">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="f4761-124">(La aplicación solo está disponible en HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="f4761-124">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f4761-125">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="f4761-125">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f4761-126"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f4761-126"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f4761-127">Diseñador de experiencias de usuario @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f4761-127">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f4761-128">Consulte también</span><span class="sxs-lookup"><span data-stu-id="f4761-128">See also</span></span>

* <span data-ttu-id="f4761-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="f4761-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="f4761-130">[Surfaces](sampleapp-surfaces.md) - [(descarga desde Microsoft Store en HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="f4761-130">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="f4761-131">Tabla periódica de los elementos 2.0</span><span class="sxs-lookup"><span data-stu-id="f4761-131">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="f4761-132">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="f4761-132">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
