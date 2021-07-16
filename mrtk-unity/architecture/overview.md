---
title: Información general sobre la arquitectura
description: Información general sobre la arquitectura de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, arquitectura de MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281912"
---
# <a name="architecture-overview"></a><span data-ttu-id="a3bbf-104">Información general sobre la arquitectura</span><span class="sxs-lookup"><span data-stu-id="a3bbf-104">Architecture overview</span></span>

<span data-ttu-id="a3bbf-105">Para obtener una introducción general al contenido de MRTK, la información de arquitectura contenida en este documento le ayudará a comprender lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a3bbf-105">For an overall introduction to the contents of MRTK, the architecture information contained in this document will help you understand the following:</span></span>

- <span data-ttu-id="a3bbf-106">Fragmentos grandes de MRTK y cómo se conectan</span><span class="sxs-lookup"><span data-stu-id="a3bbf-106">Large pieces of MRTK and how they connect</span></span>
- <span data-ttu-id="a3bbf-107">Conceptos que MRTK introduce y que pueden no existir en Unity de la vaina</span><span class="sxs-lookup"><span data-stu-id="a3bbf-107">Concepts that MRTK introduces which may not exist in vanilla Unity</span></span>
- <span data-ttu-id="a3bbf-108">Cómo funcionan algunos de los sistemas más grandes (como entrada)</span><span class="sxs-lookup"><span data-stu-id="a3bbf-108">How some of the larger systems (such as Input) work</span></span>

<span data-ttu-id="a3bbf-109">Esta sección no está pensada para enseñar a realizar tareas, sino a estructurar estas tareas y por qué.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-109">This section isn't intended to teach you how to do tasks, but rather how such tasks are structured and why.</span></span>

## <a name="many-audiences-one-toolkit"></a><span data-ttu-id="a3bbf-110">Muchas audiencias, un kit de herramientas</span><span class="sxs-lookup"><span data-stu-id="a3bbf-110">Many audiences, one toolkit</span></span>

<span data-ttu-id="a3bbf-111">MRTK no tiene una sola audiencia uniforme.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-111">MRTK doesn't have a single, uniform audience.</span></span> <span data-ttu-id="a3bbf-112">Se ha escrito para admitir casos de uso que van desde hackathons por primera vez hasta personas que construyen experiencias complejas y compartidas para empresas.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-112">It's been written to support use cases ranging from first time hackathons, to individuals building complex, shared experiences for enterprise.</span></span> <span data-ttu-id="a3bbf-113">Es posible que se hayan escrito código y API optimizados para uno más que el otro (es decir, algunas partes de MRTK parecen más optimizadas para la "configuración de un solo clic"), pero es importante tener en cuenta que algunas de ellas son más por motivos históricos y de recursos.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-113">Some code and APIs may have been written that are optimized for one more than the other (i.e. some parts of the MRTK seem more optimized for "one click configure"), but it's important to note that some of those are more for historical and resourcing reasons.</span></span> <span data-ttu-id="a3bbf-114">A medida que MRTK evoluciona, las características que se van construyendo deben diseñarse para escalarse para admitir la gama de casos de uso.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-114">As MRTK evolves, the features that get built should be designed to scale to support the range of use cases.</span></span>

<span data-ttu-id="a3bbf-115">MRTK también tiene requisitos para escalar correctamente entre las experiencias de REALIDAD virtual y AR.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-115">MRTK also has requirements to gracefully scale across VR and AR experiences.</span></span> <span data-ttu-id="a3bbf-116">Debe ser fácil compilar aplicaciones que se retrasen correctamente en el comportamiento cuando se implementan en un HoloLens 2 O un HoloLens 1, y debería ser fácil compilar aplicaciones destinadas a OpenVR y WMR (y otras plataformas).</span><span class="sxs-lookup"><span data-stu-id="a3bbf-116">It should be easy to build applications that gracefully fallback in behavior when deployed on a HoloLens 2 OR a HoloLens 1, and it should be simple to build applications that target OpenVR and WMR (and other platforms).</span></span> <span data-ttu-id="a3bbf-117">Aunque en ocasiones el equipo puede centrar una iteración determinada en un sistema o plataforma específicos, el objetivo a largo plazo es crear una amplia gama de soporte técnico para cualquier lugar donde los usuarios estén creando experiencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-117">While at times the team may focus a particular iteration on a specific system or platform, the long term goal is to build a wide range of support for wherever people are building mixed reality experiences.</span></span>

## <a name="high-level-breakdown"></a><span data-ttu-id="a3bbf-118">Desglose de alto nivel</span><span class="sxs-lookup"><span data-stu-id="a3bbf-118">High level breakdown</span></span>

<span data-ttu-id="a3bbf-119">MRTK es una colección de herramientas para obtener rápidamente experiencias de realidad mixta (MR) y también un marco de trabajo de aplicación con opiniones sobre su propio entorno de ejecución, cómo se debe extender y cómo se debe configurar.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-119">The MRTK is both a collection of tools for getting mixed reality (MR) experiences off the ground quickly, and also an application framework with opinions on its own runtime, how it should be extended, and how it should be configured.</span></span>

<span data-ttu-id="a3bbf-120">En un nivel alto, mrtk se puede desglosar de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="a3bbf-120">At a high level, the MRTK can be broken down in the following ways:</span></span>

![Diagrama de información general de la arquitectura](../features/images/architecture/MRTK_Architecture.png)

<span data-ttu-id="a3bbf-122">MrTK también contiene otro conjunto de utilidades de bolsa de mano que tienen poca o ninguna dependencia en el resto de MRTK (para enumerar algunas: herramientas de compilación, solucionadores, influenciadores de audio, utilidades de suavizado y representadores de línea).</span><span class="sxs-lookup"><span data-stu-id="a3bbf-122">The MRTK also contains another set of grab-bag utilities that have little to no dependencies on the rest of the MRTK (to list a few: build tools, solvers, audio influencers, smoothing utilities, and line renderers)</span></span>

<span data-ttu-id="a3bbf-123">El resto de la documentación de la arquitectura se compilará de abajo hacia arriba, empezando por el marco y el entorno de ejecución, y avanzará a sistemas más interesantes y complejos, como la entrada.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-123">The remainder of the architecture documentation will build bottom up, starting from the framework and runtime, progressing to more interesting and complex systems, such as input.</span></span> <span data-ttu-id="a3bbf-124">Consulte la tabla de contenido para continuar con la introducción a la arquitectura.</span><span class="sxs-lookup"><span data-stu-id="a3bbf-124">Please see the table of contents to continue with the architectural overview.</span></span>
