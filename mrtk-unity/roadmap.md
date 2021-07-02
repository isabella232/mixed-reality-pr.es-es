---
title: Plan de desarrollo
description: documentación para delinear la hoja de ruta de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 7385d516e986c1602ad59e2825aa6d1262504727
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175581"
---
# <a name="roadmap"></a><span data-ttu-id="5dea2-104">Plan de desarrollo</span><span class="sxs-lookup"><span data-stu-id="5dea2-104">Roadmap</span></span>

<span data-ttu-id="5dea2-105">En este documento se describe la hoja de ruta de la Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="5dea2-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="5dea2-106">Tenga en cuenta que lo siguiente refleja el trabajo que está en desarrollo y las fechas de destino reflejan las estimaciones.</span><span class="sxs-lookup"><span data-stu-id="5dea2-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="5dea2-107">Versión actual</span><span class="sxs-lookup"><span data-stu-id="5dea2-107">Current release</span></span>

<span data-ttu-id="5dea2-108">Microsoft Mixed Reality Toolkit v2.6</span><span class="sxs-lookup"><span data-stu-id="5dea2-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="5dea2-109">Próximas versiones</span><span class="sxs-lookup"><span data-stu-id="5dea2-109">Upcoming releases</span></span>

| <span data-ttu-id="5dea2-110">Producto</span><span class="sxs-lookup"><span data-stu-id="5dea2-110">Product</span></span> | <span data-ttu-id="5dea2-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="5dea2-111">Description</span></span> | <span data-ttu-id="5dea2-112">Escala de tiempo</span><span class="sxs-lookup"><span data-stu-id="5dea2-112">Timeline</span></span> | <span data-ttu-id="5dea2-113">Project placa</span><span class="sxs-lookup"><span data-stu-id="5dea2-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="5dea2-114">MRTK V2.7</span><span class="sxs-lookup"><span data-stu-id="5dea2-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="5dea2-115">Siguiente iteración de MRTK</span><span class="sxs-lookup"><span data-stu-id="5dea2-115">Next iteration of MRTK</span></span> | <span data-ttu-id="5dea2-116">Mayo de 2021</span><span class="sxs-lookup"><span data-stu-id="5dea2-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="5dea2-117">Las versiones se centra en temas (por ejemplo, áreas de características grandes) y están programadas para producirse aproximadamente cada 8-12 semanas.</span><span class="sxs-lookup"><span data-stu-id="5dea2-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="5dea2-118">Los detalles de la versión, incluidos los elementos de trabajo pendiente, se pueden encontrar en las [GitHub de hitos](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span><span class="sxs-lookup"><span data-stu-id="5dea2-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="5dea2-119">El conjunto completo de problemas abiertos también se puede encontrar [en GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="5dea2-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="5dea2-120">mapa Mixed Reality Toolkit de desarrollo de Mixed Reality Toolkit (MRTK)</span><span class="sxs-lookup"><span data-stu-id="5dea2-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="5dea2-121">El Mixed Reality Toolkit está diseñado para ser multiplataforma MR/AR/VR/XR por diseño.</span><span class="sxs-lookup"><span data-stu-id="5dea2-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="5dea2-122">El kit de herramientas admite actualmente Unity 2019.4.x y Unity 2018.4.x.</span><span class="sxs-lookup"><span data-stu-id="5dea2-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="5dea2-123">Cuando Unity publica un producto LTS (compatibilidad a largo plazo), el Mixed Reality Toolkit actualizará a la versión LTS.</span><span class="sxs-lookup"><span data-stu-id="5dea2-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="5dea2-124">Aunque el Mixed Reality Toolkit se ejecuta en la versión más reciente de la rama técnica no beta (por ejemplo, 2020.1) de Unity, no se admite oficialmente.</span><span class="sxs-lookup"><span data-stu-id="5dea2-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="5dea2-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="5dea2-125">2.7.0</span></span>

<span data-ttu-id="5dea2-126">Actualmente estamos planeando la versión 2.7.0 y pronto tendrá más actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="5dea2-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="5dea2-127">Para conocer el estado más reciente de la versión, visite la página [del hito](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span><span class="sxs-lookup"><span data-stu-id="5dea2-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="5dea2-128">Estado: Planeamiento</span><span class="sxs-lookup"><span data-stu-id="5dea2-128">Status: Planning</span></span>

<span data-ttu-id="5dea2-129">Escala de tiempo de destino: mayo de 2021</span><span class="sxs-lookup"><span data-stu-id="5dea2-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="5dea2-130">Temas:</span><span class="sxs-lookup"><span data-stu-id="5dea2-130">Themes:</span></span>

- <span data-ttu-id="5dea2-131">Stability</span><span class="sxs-lookup"><span data-stu-id="5dea2-131">Stability</span></span> 
- <span data-ttu-id="5dea2-132">Expansión de la plataforma: OpenXR</span><span class="sxs-lookup"><span data-stu-id="5dea2-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="5dea2-133">Experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="5dea2-133">User Experience</span></span>
- <span data-ttu-id="5dea2-134">Educación para desarrolladores</span><span class="sxs-lookup"><span data-stu-id="5dea2-134">Developer Education</span></span>
- <span data-ttu-id="5dea2-135">Packaging</span><span class="sxs-lookup"><span data-stu-id="5dea2-135">Packaging</span></span>

<span data-ttu-id="5dea2-136">**Estabilidad**</span><span class="sxs-lookup"><span data-stu-id="5dea2-136">**Stability**</span></span>

<span data-ttu-id="5dea2-137">La calidad y la estabilidad son la prioridad principal para esta y todas las versiones Mixed Reality Toolkit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5dea2-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="5dea2-138">Seguiremos priorizando los problemas de clientes y asociados que afectan a la estabilidad de los componentes de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5dea2-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="5dea2-139">**Expansión de la plataforma: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="5dea2-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="5dea2-140">El equipo de MRTK admite el futuro abierto de la realidad mixta a través [de OpenXR.](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)</span><span class="sxs-lookup"><span data-stu-id="5dea2-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="5dea2-141">La compatibilidad con OpenXR está actualmente en desarrollo, con compatibilidad con la versión preliminar inicial publicada en MRTK 2.5.2.</span><span class="sxs-lookup"><span data-stu-id="5dea2-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="5dea2-142">**Experiencia del usuario**</span><span class="sxs-lookup"><span data-stu-id="5dea2-142">**User Experience**</span></span>

<span data-ttu-id="5dea2-143">Estamos escuchando sus comentarios sobre MRTK y tenemos planes continuos para:</span><span class="sxs-lookup"><span data-stu-id="5dea2-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="5dea2-144">Corrección de errores</span><span class="sxs-lookup"><span data-stu-id="5dea2-144">Bug fixes</span></span>
- <span data-ttu-id="5dea2-145">Facilitar la lectura de los controles de experiencia de usuario de MRTK</span><span class="sxs-lookup"><span data-stu-id="5dea2-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="5dea2-146">HoloLens Paridad del shell</span><span class="sxs-lookup"><span data-stu-id="5dea2-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="5dea2-147">Pruebas para asegurarse de que las características no se revierte</span><span class="sxs-lookup"><span data-stu-id="5dea2-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="5dea2-148">**Educación para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="5dea2-148">**Developer Education**</span></span>

<span data-ttu-id="5dea2-149">Hemos migrado nuestra documentación para desarrolladores de GitHub a una nueva plataforma de documentos.</span><span class="sxs-lookup"><span data-stu-id="5dea2-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="5dea2-150">Queremos escuchar sus comentarios para poder seguir mejorando nuestra experiencia de documentación para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="5dea2-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="5dea2-151">Actualmente tenemos [tutoriales de MRTK](/windows/mixed-reality/develop/unity/tutorials) que se encuentran en una sección diferente de Mixed Reality documentos. Vamos a migrar estos tutoriales para que se realicen con el resto de la documentación de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5dea2-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="5dea2-152">**Packaging**</span><span class="sxs-lookup"><span data-stu-id="5dea2-152">**Packaging**</span></span>

<span data-ttu-id="5dea2-153">La [Mixed Reality de características es](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) una nueva manera para que los desarrolladores detecten, actualicen y agreguen Mixed Reality paquetes de características en proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="5dea2-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="5dea2-154">Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="5dea2-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="5dea2-155">Tenemos previsto realizar actualizaciones en la herramienta de características Mixed Reality a medida que respondemos a solicitudes y errores de características.</span><span class="sxs-lookup"><span data-stu-id="5dea2-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="5dea2-156">Trabajo pendiente</span><span class="sxs-lookup"><span data-stu-id="5dea2-156">Backlog</span></span>

<span data-ttu-id="5dea2-157">En la lista siguiente se resaltan algunas de las inversiones clave que el equipo de MRTK pretende llevar a cabo.</span><span class="sxs-lookup"><span data-stu-id="5dea2-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="5dea2-158">Expansión de la plataforma</span><span class="sxs-lookup"><span data-stu-id="5dea2-158">Platform expansion</span></span>
- <span data-ttu-id="5dea2-159">Extensibilidad</span><span class="sxs-lookup"><span data-stu-id="5dea2-159">Extensibility</span></span>
- <span data-ttu-id="5dea2-160">Modularidad</span><span class="sxs-lookup"><span data-stu-id="5dea2-160">Modularity</span></span>
- <span data-ttu-id="5dea2-161">Características de accesibilidad</span><span class="sxs-lookup"><span data-stu-id="5dea2-161">Accessibility features</span></span>
- <span data-ttu-id="5dea2-162">Mejoras de globalización</span><span class="sxs-lookup"><span data-stu-id="5dea2-162">Globalization enhancements</span></span>
- <span data-ttu-id="5dea2-163">Compatibilidad con servicios en la nube</span><span class="sxs-lookup"><span data-stu-id="5dea2-163">Cloud service support</span></span>
- <span data-ttu-id="5dea2-164">Herramientas</span><span class="sxs-lookup"><span data-stu-id="5dea2-164">Tools</span></span>
