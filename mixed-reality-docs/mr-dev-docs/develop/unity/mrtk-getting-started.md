---
title: Introducción a MRTK para Unity
description: Descubra todo lo que Mixed Reality Toolkit multiplataforma puede ofrecer a los nuevos desarrolladores de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, tools, SDK, HoloLens, HoloLens 2, mixed reality headset, windows mixed reality headset, virtual reality headset, cross-platform
ms.openlocfilehash: 54ad49bbf4da577a398a0bfb12fbdc84cdff34d9
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238119"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="17276-104">Introducción a MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="17276-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="17276-106">¿Qué es Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="17276-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="17276-107">MRTK es un increíble kit de herramientas de código abierto que ha estado presente desde la primera vez que se lanzó HoloLens.</span><span class="sxs-lookup"><span data-stu-id="17276-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="17276-108">El kit de herramientas no sería de la forma que es actualmente sin el trabajo que aporta nuestra comunidad de desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="17276-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="17276-109">Durante los últimos tres años, hemos tenido en cuenta los comentarios de nuestra comunidad de desarrolladores y hemos creado MRTK v2 para dar respuesta a las preocupaciones más importantes.</span><span class="sxs-lookup"><span data-stu-id="17276-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="17276-110">MRTK para Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="17276-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="17276-111">La manera más fácil de instalar el kit de herramientas es con la nueva herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="17276-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="17276-112">Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el paquete **Mixed Reality Toolkit Foundation** en la categoría Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="17276-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span> 

<span data-ttu-id="17276-113">MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales.</span><span class="sxs-lookup"><span data-stu-id="17276-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="17276-114">La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="17276-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="17276-115">El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.</span><span class="sxs-lookup"><span data-stu-id="17276-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="17276-116">Eche un vistazo a la [documentación de MRTK en GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más detalles sobre las características.</span><span class="sxs-lookup"><span data-stu-id="17276-116">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="17276-117">Novedades en MRTK v2</span><span class="sxs-lookup"><span data-stu-id="17276-117">New with MRTK v2</span></span>

<span data-ttu-id="17276-118">Queremos remarcar nuestro compromiso con estas herramientas de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="17276-118">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="17276-119">De hecho, hemos usado MRTK, versión 2, para desarrollar nuestras experiencias de bandeja de entrada, como configuración rápida (OOBE) y nuestra aplicación de sugerencias de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="17276-119">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="17276-120">Además, verás nuevas funcionalidades de HoloLens 2 expuestas por primera vez a través de MRTK porque creemos que es la mejor manera de llevar a cabo el desarrollo en nuestra plataforma.</span><span class="sxs-lookup"><span data-stu-id="17276-120">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="17276-121">Modular</span><span class="sxs-lookup"><span data-stu-id="17276-121">Modular</span></span>

<span data-ttu-id="17276-122">Lo hemos diseñado de una manera modular, por lo que no es necesario incluir cada una de las partes del kit de herramientas en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="17276-122">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="17276-123">De hecho, esto supone varias ventajas.</span><span class="sxs-lookup"><span data-stu-id="17276-123">There are actually a few benefits to this.</span></span>  <span data-ttu-id="17276-124">Mantiene el tamaño del proyecto más pequeño y facilita su administración.</span><span class="sxs-lookup"><span data-stu-id="17276-124">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="17276-125">Además, dado que se ha creado con objetos que admiten scripts y está basado en una interfaz, también puedes reemplazar los componentes incluidos por los tuyos propios, a fin de agregar compatibilidad con otros servicios, sistemas y plataformas.</span><span class="sxs-lookup"><span data-stu-id="17276-125">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="17276-126">Multiplataforma</span><span class="sxs-lookup"><span data-stu-id="17276-126">Cross-platform</span></span>

<span data-ttu-id="17276-127">Hablando de otras plataformas, también ofrece compatibilidad multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="17276-127">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="17276-128">Aunque esto no significa que todas las plataformas sean compatibles, nos hemos asegurado de que ninguna parte del código del kit de herramientas deje de funcionar al cambiar el destino de compilación a otras plataformas.</span><span class="sxs-lookup"><span data-stu-id="17276-128">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="17276-129">La solidez y la extensibilidad del diseño modular establecen las aplicaciones a fin de poder admitir varias plataformas, como ARCore, ARKit y OpenVR.</span><span class="sxs-lookup"><span data-stu-id="17276-129">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="17276-130">Buen rendimiento</span><span class="sxs-lookup"><span data-stu-id="17276-130">Performant</span></span>

<span data-ttu-id="17276-131">Dado que trabamos con plataformas móviles, lo hemos diseñado pensando en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="17276-131">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="17276-132">Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan en tu contra.</span><span class="sxs-lookup"><span data-stu-id="17276-132">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="17276-133">Consulta también</span><span class="sxs-lookup"><span data-stu-id="17276-133">See also</span></span>

* [<span data-ttu-id="17276-134">Instalación de las herramientas</span><span class="sxs-lookup"><span data-stu-id="17276-134">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="17276-135">Herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="17276-135">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="17276-136">Desarrollo con MRTK para Unity</span><span class="sxs-lookup"><span data-stu-id="17276-136">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="17276-137">MRTK: Página principal de documentación (GitHub)</span><span class="sxs-lookup"><span data-stu-id="17276-137">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="17276-138">Migración de HoloToolkit/MRTK a MRTK, versión 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="17276-138">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
