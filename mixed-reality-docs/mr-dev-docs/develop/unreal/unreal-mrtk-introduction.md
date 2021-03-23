---
title: Introducción de MRTK para Unreal
description: Descubra todo lo que Mixed Reality Toolkit for Unreal puede ofrecer a los nuevos desarrolladores de realidad mixta.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, tools, SDK, HoloLens, HoloLens 2, mixed reality headset, windows mixed reality headset, virtual reality headset, cross-platform
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98584834"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="a02dc-104">Introducción de MRTK para Unreal</span><span class="sxs-lookup"><span data-stu-id="a02dc-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="a02dc-106">¿Qué es Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="a02dc-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="a02dc-107">MRTK es un increíble kit de herramientas de código abierto que ha estado presente desde la primera vez que se lanzó HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a02dc-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="a02dc-108">El kit de herramientas no sería de la forma que es actualmente sin el trabajo que aporta nuestra comunidad de desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="a02dc-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="a02dc-109">Mixed Reality Toolkit para Unreal (MRTK-Unreal) es un conjunto de componentes, en forma de complementos, muestras y documentación, diseñado para facilitar el desarrollo de aplicaciones de realidad mixta con Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="a02dc-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="a02dc-110">Actualmente, el kit de herramientas consta de:</span><span class="sxs-lookup"><span data-stu-id="a02dc-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="a02dc-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), que proporciona código, planos técnicos y ejemplos para implementar características de experiencia de usuario para aplicaciones de Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="a02dc-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="a02dc-112">[Graphic Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), que ayuda a mejorar la fidelidad visual de las aplicaciones de realidad mixta sin salirse de los presupuestos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a02dc-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="a02dc-113">Eche un vistazo a la [documentación de MRTK en GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) y empiece a trabajar con las guías de instalación de [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) o [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).</span><span class="sxs-lookup"><span data-stu-id="a02dc-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="a02dc-114">Modular</span><span class="sxs-lookup"><span data-stu-id="a02dc-114">Modular</span></span>

<span data-ttu-id="a02dc-115">Hemos compilado MRTK Unreal de una manera modular, por lo que no es necesario incluir cada una de las partes del kit de herramientas en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="a02dc-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="a02dc-116">Puede elegir los complementos que necesite y agregarlos o quitarlos cuando lo considere oportuno.</span><span class="sxs-lookup"><span data-stu-id="a02dc-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="a02dc-117">Este enfoque reduce el tamaño del proyecto y facilita su administración.</span><span class="sxs-lookup"><span data-stu-id="a02dc-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="a02dc-118">Buen rendimiento</span><span class="sxs-lookup"><span data-stu-id="a02dc-118">Performant</span></span>

<span data-ttu-id="a02dc-119">Dado que trabamos con plataformas móviles, hemos diseñado MRTK Unreal pensando en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="a02dc-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="a02dc-120">Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan en su contra.</span><span class="sxs-lookup"><span data-stu-id="a02dc-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="a02dc-121">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a02dc-121">See also</span></span>

* [<span data-ttu-id="a02dc-122">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="a02dc-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="a02dc-123">Desarrollo con MRTK para Unreal</span><span class="sxs-lookup"><span data-stu-id="a02dc-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="a02dc-124">UX Tools: guía de instalación (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a02dc-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="a02dc-125">UX Tools: página principal de documentación (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a02dc-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="a02dc-126">Graphics Tools: guía de instalación (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a02dc-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="a02dc-127">Graphics Tools: página principal de documentación (GitHub)</span><span class="sxs-lookup"><span data-stu-id="a02dc-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)