---
title: Uso del profiler visual
description: documentación para usar Visual Profiler en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 018d6bf2087b73697a1e1f43e206c96ae25e1f21
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177221"
---
# <a name="using-the-visual-profiler"></a><span data-ttu-id="9e78a-104">Uso del profiler visual</span><span class="sxs-lookup"><span data-stu-id="9e78a-104">Using the visual profiler</span></span>

<span data-ttu-id="9e78a-105">VisualProfiler proporciona una vista en la aplicación fácil de usar del rendimiento de una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="9e78a-105">The VisualProfiler provides an easy to use, in-application view of a mixed reality application's performance.</span></span> <span data-ttu-id="9e78a-106">El profiler se admite en todas las Mixed Reality Toolkit plataformas, incluidas:</span><span class="sxs-lookup"><span data-stu-id="9e78a-106">The profiler is supported on all Mixed Reality Toolkit platforms, including:</span></span>

- <span data-ttu-id="9e78a-107">Microsoft HoloLens (1.ª generación)</span><span class="sxs-lookup"><span data-stu-id="9e78a-107">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="9e78a-108">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="9e78a-108">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="9e78a-109">Cascos envolventes de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="9e78a-109">Windows Mixed Reality immersive headsets</span></span>
- <span data-ttu-id="9e78a-110">OpenVR</span><span class="sxs-lookup"><span data-stu-id="9e78a-110">OpenVR</span></span>

<span data-ttu-id="9e78a-111">Al desarrollar una aplicación, céntrate en varias partes de la escena, ya que Visual Profiler muestra datos relativos a la vista actual.</span><span class="sxs-lookup"><span data-stu-id="9e78a-111">While developing an application, focus on multiple parts of the scene as the Visual Profiler displays data relative to the current view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e78a-112">Centre la atención en partes de la escena con objetos complejos, efectos de partícula o actividad.</span><span class="sxs-lookup"><span data-stu-id="9e78a-112">Focus attention on portions of the scene with complex objects, particle effects or activity.</span></span> <span data-ttu-id="9e78a-113">Estos y otros factores a menudo contribuyen a la reducción del rendimiento de la aplicación y a una experiencia de usuario menos que ideal.</span><span class="sxs-lookup"><span data-stu-id="9e78a-113">These and other factors often contribute to reduction in application performance and a less than ideal user experience.</span></span>

## <a name="visual-profiler-interface"></a><span data-ttu-id="9e78a-114">Interfaz del profiler visual</span><span class="sxs-lookup"><span data-stu-id="9e78a-114">Visual profiler interface</span></span>

![Interfaz de Visual Profiler](../images/diagnostics/VisualProfiler.png)

<span data-ttu-id="9e78a-116">La interfaz de Visual Profiler incluye los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="9e78a-116">The Visual Profiler interface includes the following components:</span></span>

- [<span data-ttu-id="9e78a-117">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="9e78a-117">Frame Rate</span></span>](#frame-rate)
- [<span data-ttu-id="9e78a-118">Tiempo de fotogramas</span><span class="sxs-lookup"><span data-stu-id="9e78a-118">Frame Time</span></span>](#frame-time)
- [<span data-ttu-id="9e78a-119">Marco Graph</span><span class="sxs-lookup"><span data-stu-id="9e78a-119">Frame Graph</span></span>](#frame-graph)
- [<span data-ttu-id="9e78a-120">Uso de memoria</span><span class="sxs-lookup"><span data-stu-id="9e78a-120">Memory Utilization</span></span>](#memory-utilization)

### <a name="frame-rate"></a><span data-ttu-id="9e78a-121">Velocidad de fotogramas</span><span class="sxs-lookup"><span data-stu-id="9e78a-121">Frame rate</span></span>

<span data-ttu-id="9e78a-122">En la esquina superior izquierda de la interfaz se encuentra la velocidad de fotogramas, medida en fotogramas por segundo.</span><span class="sxs-lookup"><span data-stu-id="9e78a-122">In the upper-left corner of the interface is the frame rate, measured in frames per second.</span></span> <span data-ttu-id="9e78a-123">Para obtener la mejor experiencia y comodidad del usuario, este valor debe ser lo más alto posible.</span><span class="sxs-lookup"><span data-stu-id="9e78a-123">For the best user experience and comfort, this value should be as high as possible.</span></span>

<span data-ttu-id="9e78a-124">La configuración específica de la plataforma y el hardware desempeñará un papel importante en la velocidad máxima de fotogramas factible.</span><span class="sxs-lookup"><span data-stu-id="9e78a-124">The specific platform and hardware configuration will play a significant role in the maximum achievable frame rate.</span></span> <span data-ttu-id="9e78a-125">Algunos valores de destino comunes incluyen:</span><span class="sxs-lookup"><span data-stu-id="9e78a-125">Some common target values include:</span></span>

- <span data-ttu-id="9e78a-126">Microsoft HoloLens: 60</span><span class="sxs-lookup"><span data-stu-id="9e78a-126">Microsoft HoloLens: 60</span></span>
- <span data-ttu-id="9e78a-127">Windows Mixed Reality Ultra: 90</span><span class="sxs-lookup"><span data-stu-id="9e78a-127">Windows Mixed Reality Ultra: 90</span></span>

> [!NOTE]
> <span data-ttu-id="9e78a-128">Debido a [la limitación](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens)de velocidad de fotogramas en HoloLens cuando mrc predeterminado está activo, el profiler visual se oculta mientras se capturan vídeos y fotos.</span><span class="sxs-lookup"><span data-stu-id="9e78a-128">Due to [frame rate throttling on HoloLens when default MRC is active](/windows/mixed-reality/mixed-reality-capture-for-developers#what-to-expect-when-mrc-is-enabled-on-hololens), the visual profiler hides itself while videos and photos are captured.</span></span> <span data-ttu-id="9e78a-129">Esta configuración se puede invalidar en el perfil del sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9e78a-129">This setting can be overridden in the diagnostics system profile.</span></span>

### <a name="frame-time"></a><span data-ttu-id="9e78a-130">Tiempo entre fotogramas</span><span class="sxs-lookup"><span data-stu-id="9e78a-130">Frame time</span></span>

<span data-ttu-id="9e78a-131">A la derecha de la velocidad de fotogramas se encuentra el tiempo de fotograma, en milisegundos, empleado en la CPU.</span><span class="sxs-lookup"><span data-stu-id="9e78a-131">To the right of the frame rate is the frame time, in milliseconds, spent on the CPU.</span></span> <span data-ttu-id="9e78a-132">Para lograr las tasas de fotogramas de destino mencionadas anteriormente, una aplicación puede dedicar la siguiente cantidad de tiempo por fotograma:</span><span class="sxs-lookup"><span data-stu-id="9e78a-132">To achieve the target frame rates mentioned previously, an application can spend the following amount of time per frame:</span></span>

- <span data-ttu-id="9e78a-133">60 fps: 16,6 ms</span><span class="sxs-lookup"><span data-stu-id="9e78a-133">60 fps: 16.6 ms</span></span>
- <span data-ttu-id="9e78a-134">90 fps: 11,1 ms</span><span class="sxs-lookup"><span data-stu-id="9e78a-134">90 fps: 11.1 ms</span></span>

<span data-ttu-id="9e78a-135">Está previsto que el tiempo de GPU se agregó en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="9e78a-135">GPU time is planned to be added in a future release.</span></span>

### <a name="frame-graph"></a><span data-ttu-id="9e78a-136">Gráfico de fotogramas</span><span class="sxs-lookup"><span data-stu-id="9e78a-136">Frame graph</span></span>

<span data-ttu-id="9e78a-137">El gráfico de fotogramas proporciona una presentación gráfica del historial de velocidad de fotogramas de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9e78a-137">The frame graph provides a graphical display of the application frame rate history.</span></span>

![Visual Profiler Missed Frame Graph](../images/diagnostics/VisualProfilerMissedFrames.png)

<span data-ttu-id="9e78a-139">Al usar la aplicación, busque fotogramas perdidos que indiquen que la aplicación no está alcanzando su velocidad de fotogramas objetivo y puede que necesite trabajo de optimización.</span><span class="sxs-lookup"><span data-stu-id="9e78a-139">When using the application, look for missed frames which indicate that the application is not hitting its target frame rate and may need optimization work.</span></span>

### <a name="memory-utilization"></a><span data-ttu-id="9e78a-140">Uso de memoria</span><span class="sxs-lookup"><span data-stu-id="9e78a-140">Memory utilization</span></span>

<span data-ttu-id="9e78a-141">La presentación de uso de memoria permite comprender fácilmente cómo afecta la vista actual al consumo de memoria de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="9e78a-141">The memory utilization display allows for easy understanding of how the current view is impacting an application's memory consumption.</span></span>

![Memoria de Visual Profiler Graph](../images/diagnostics/VisualProfilerMemory.png)

<span data-ttu-id="9e78a-143">Al usar la aplicación, busque el uso total de memoria.</span><span class="sxs-lookup"><span data-stu-id="9e78a-143">When using the application, look for total memory usage.</span></span> <span data-ttu-id="9e78a-144">Entre los indicadores clave se incluyen la proximidad del límite de memoria y los cambios rápidos en el uso.</span><span class="sxs-lookup"><span data-stu-id="9e78a-144">Key indicators include nearing the memory limit and rapid changes in usage.</span></span>

## <a name="customizing-the-visual-profiler"></a><span data-ttu-id="9e78a-145">Personalización del profiler visual</span><span class="sxs-lookup"><span data-stu-id="9e78a-145">Customizing the visual profiler</span></span>

<span data-ttu-id="9e78a-146">La apariencia y el comportamiento de Visual Profiler se pueden personalizar a través del perfil del sistema de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="9e78a-146">The Visual Profiler's appearance and behavior are customizable via the diagnostics system profile.</span></span> <span data-ttu-id="9e78a-147">Consulte [Configuración del sistema de diagnóstico para](configuring-diagnostics.md) obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9e78a-147">Please see [Configuring the Diagnostics System](configuring-diagnostics.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e78a-148">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9e78a-148">See also</span></span>

- [<span data-ttu-id="9e78a-149">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9e78a-149">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="9e78a-150">Configuración del sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9e78a-150">Configuring the Diagnostics System</span></span>](configuring-diagnostics.md)
