---
title: Configuración del sistema de diagnóstico
description: Documentación para configurar diagnósticos en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 521ef71abd1ddf920863530a2a423c1080a135e5a404a26f1611fc14f92c2796
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198250"
---
# <a name="configuring-the-diagnostics-system"></a>Configuración del sistema de diagnóstico

## <a name="general-settings"></a>Configuración general

![Diagnósticos generales Configuración](../images/diagnostics/DiagnosticsGeneralSettings.png)

### <a name="enable-verbose-logging"></a>Habilitar el registro detallado

Indica si se habilitará o no el registro detallado de MRTK. El valor predeterminado es false, pero se puede desactivar para realizar seguimientos detallados que permitan al equipo de MRTK depurar o profundizar en los problemas. Por ejemplo, al presentar un problema, adjuntar los registros del reproductor de Unity (ya sea desde el editor o desde el reproductor) puede ayudar a reducir el origen de errores y problemas.

Tenga en cuenta que esta opción es independiente de si el sistema de diagnóstico está habilitado o no; esto se muestra en el sistema de diagnóstico porque es una opción de registro, pero en última instancia funciona en un nivel superior porque afecta al registro en todo el código base de MRTK.

### <a name="show-diagnostics"></a>Mostrar diagnósticos

Indica si el sistema de diagnóstico debe mostrar o no las opciones de diagnóstico configuradas.

Cuando se deshabilita, se ocultarán todas las opciones de diagnóstico configuradas.

## <a name="profiler-settings"></a>Configuración del profiler

![Diagnostics Profiler Configuración](../images/diagnostics/DiagnosticsProfilerSettings.png)

### <a name="show-profiler"></a>Mostrar el profiler

Indica si se va a mostrar o no Visual Profiler.

### <a name="frame-sample-rate"></a>Velocidad de muestreo de fotogramas

Cantidad de tiempo, en segundos, para recopilar fotogramas para el cálculo de la velocidad de fotogramas. El intervalo es de 0 a 5 segundos.

### <a name="window-anchor"></a>Delimitador de ventana

A qué parte del puerto de vista se debe delimitar la ventana del profiler. El valor predeterminado es Centro inferior.

### <a name="window-offset"></a>Desplazamiento de ventana

Desplazamiento, desde el centro del puerto de vista, para colocar Visual Profiler. El desplazamiento estará en la dirección de la propiedad *Delimitador de* ventana.

### <a name="window-scale"></a>Escala de ventanas

Multiplicador de tamaño aplicado a la ventana del profiler. Por ejemplo, si se establece el valor en 2, se duplicará el tamaño de la ventana.

### <a name="window-follow-speed"></a>Velocidad de seguimiento de ventana

Velocidad a la que se va a mover la ventana del profiler para mantener la visibilidad dentro del puerto de vista.

## <a name="programmatically-controlling-the-diagnostics-system"></a>Control del sistema de diagnóstico mediante programación

También es posible alternar la visibilidad del sistema de diagnóstico y del profiler en tiempo de ejecución. Por ejemplo, el código siguiente ocultará el sistema de diagnóstico y el profiler.

```c#
CoreServices.DiagnosticsSystem.ShowDiagnostics = false;

CoreServices.DiagnosticsSystem.ShowProfiler = false;
```

## <a name="see-also"></a>Consulte también

- [Sistema de diagnóstico](diagnostics-system-getting-started.md)
- [Uso de Visual Profiler](using-visual-profiler.md)
