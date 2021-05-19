---
title: Configuración de diagnósticos
description: documentación para configurar diagnósticos en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 2ff761baa728017eb011cb9105cf203e6e3a72e4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144174"
---
# <a name="configuring-the-diagnostics-system"></a><span data-ttu-id="1d3b3-104">Configuración del sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1d3b3-104">Configuring the diagnostics system</span></span>

## <a name="general-settings"></a><span data-ttu-id="1d3b3-105">Configuración general</span><span class="sxs-lookup"><span data-stu-id="1d3b3-105">General settings</span></span>

![Configuración general de diagnósticos](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a><span data-ttu-id="1d3b3-107">Habilitar el registro detallado</span><span class="sxs-lookup"><span data-stu-id="1d3b3-107">Enable verbose logging</span></span>

<span data-ttu-id="1d3b3-108">Indica si se habilitará o no el registro detallado de MRTK.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-108">Indicates whether or not verbose MRTK logging will be enabled.</span></span> <span data-ttu-id="1d3b3-109">El valor predeterminado es false, pero se puede desactivar para realizar seguimientos detallados que permitan al equipo de MRTK depurar o profundizar en los problemas.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-109">This defaults to false, but can be turned on to take detailed traces that allow the MRTK team to debug/dig into issues.</span></span> <span data-ttu-id="1d3b3-110">Por ejemplo, al presentar un problema, adjuntar los registros del reproductor de Unity (ya sea desde el editor o desde el reproductor) puede ayudar a reducir el origen de errores y problemas.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-110">For example, when filing an issue, attaching the Unity player logs (either from the editor or from the player) can help narrow down the source of bugs and issues.</span></span>

<span data-ttu-id="1d3b3-111">Tenga en cuenta que esta opción es independiente de si el sistema de diagnóstico está habilitado o no; esto se muestra en el sistema de diagnóstico porque es una opción de registro, pero en última instancia funciona en un nivel superior porque afecta al registro en todo el código base de MRTK.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-111">Note that this option is independent of whether or not diagnostics system is enabled - this shows up under the diagnostics system because it's a logging option, but ultimately operates at a higher level because it affects logging across the entire MRTK codebase.</span></span>

### <a name="show-diagnostics"></a><span data-ttu-id="1d3b3-112">Mostrar diagnósticos</span><span class="sxs-lookup"><span data-stu-id="1d3b3-112">Show diagnostics</span></span>

<span data-ttu-id="1d3b3-113">Indica si el sistema de diagnóstico debe mostrar o no las opciones de diagnóstico configuradas.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-113">Indicates whether or not the diagnostics system is to display the configured diagnostic options.</span></span>

<span data-ttu-id="1d3b3-114">Cuando se deshabilita, se ocultarán todas las opciones de diagnóstico configuradas.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-114">When disabled, all configured diagnostic options will be hidden.</span></span>

## <a name="profiler-settings"></a><span data-ttu-id="1d3b3-115">Configuración del profiler</span><span class="sxs-lookup"><span data-stu-id="1d3b3-115">Profiler settings</span></span>

![Configuración del profiler de diagnósticos](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a><span data-ttu-id="1d3b3-117">Mostrar el profiler</span><span class="sxs-lookup"><span data-stu-id="1d3b3-117">Show profiler</span></span>

<span data-ttu-id="1d3b3-118">Indica si se va a mostrar o no Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-118">Indicates whether or not the Visual Profiler is to be displayed.</span></span>

### <a name="frame-sample-rate"></a><span data-ttu-id="1d3b3-119">Velocidad de muestreo de fotogramas</span><span class="sxs-lookup"><span data-stu-id="1d3b3-119">Frame sample rate</span></span>

<span data-ttu-id="1d3b3-120">Cantidad de tiempo, en segundos, para recopilar fotogramas para el cálculo de la velocidad de fotogramas.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-120">The amount of time, in seconds to collect frames for frame rate calculation.</span></span> <span data-ttu-id="1d3b3-121">El intervalo es de 0 a 5 segundos.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-121">The range is 0 to 5 seconds.</span></span>

### <a name="window-anchor"></a><span data-ttu-id="1d3b3-122">Delimitador de ventana</span><span class="sxs-lookup"><span data-stu-id="1d3b3-122">Window anchor</span></span>

<span data-ttu-id="1d3b3-123">A qué parte del puerto de vista se debe delimitar la ventana del profiler.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-123">To what portion of the view port should the profiler window be anchored.</span></span> <span data-ttu-id="1d3b3-124">El valor predeterminado es Centro inferior.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-124">The default value is Lower Center.</span></span>

### <a name="window-offset"></a><span data-ttu-id="1d3b3-125">Desplazamiento de ventana</span><span class="sxs-lookup"><span data-stu-id="1d3b3-125">Window offset</span></span>

<span data-ttu-id="1d3b3-126">Desplazamiento, desde el centro del puerto de vista, para colocar Visual Profiler.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-126">The offset, from the center of the view port, to place the Visual Profiler.</span></span> <span data-ttu-id="1d3b3-127">El desplazamiento estará en la dirección de la propiedad *Delimitador de* ventana.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-127">The offset will be in the direction of the *Window Anchor* property.</span></span>

### <a name="window-scale"></a><span data-ttu-id="1d3b3-128">Escala de ventanas</span><span class="sxs-lookup"><span data-stu-id="1d3b3-128">Window scale</span></span>

<span data-ttu-id="1d3b3-129">Multiplicador de tamaño aplicado a la ventana del profiler.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-129">Size multiplier applied to the profiler window.</span></span> <span data-ttu-id="1d3b3-130">Por ejemplo, si se establece el valor en 2, se duplicará el tamaño de la ventana.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-130">For example, setting the value to 2 will double the window size.</span></span>

### <a name="window-follow-speed"></a><span data-ttu-id="1d3b3-131">Velocidad de seguimiento de ventana</span><span class="sxs-lookup"><span data-stu-id="1d3b3-131">Window follow speed</span></span>

<span data-ttu-id="1d3b3-132">Velocidad a la que se va a mover la ventana del profiler para mantener la visibilidad dentro del puerto de vista.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-132">The speed at which to move the profiler window to maintain visibility within the view port.</span></span>

## <a name="programmatically-controlling-the-diagnostics-system"></a><span data-ttu-id="1d3b3-133">Control mediante programación del sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1d3b3-133">Programmatically controlling the diagnostics system</span></span>

<span data-ttu-id="1d3b3-134">También es posible alternar la visibilidad del sistema de diagnóstico y del profiler en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-134">It's also possible to toggle the visibility of the diagnostics system and the profiler at runtime.</span></span> <span data-ttu-id="1d3b3-135">Por ejemplo, el código siguiente ocultará el sistema de diagnóstico y el profiler.</span><span class="sxs-lookup"><span data-stu-id="1d3b3-135">For example, the code below will hide the diagnostics system and profiler.</span></span>

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a><span data-ttu-id="1d3b3-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1d3b3-136">See also</span></span>

- [<span data-ttu-id="1d3b3-137">Sistema de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="1d3b3-137">Diagnostics System</span></span>](diagnostics-system-getting-started.md)
- [<span data-ttu-id="1d3b3-138">Uso de Visual Profiler</span><span class="sxs-lookup"><span data-stu-id="1d3b3-138">Using the Visual Profiler</span></span>](using-visual-profiler.md)
