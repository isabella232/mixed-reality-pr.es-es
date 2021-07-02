---
title: Introducción al sistema de diagnósticos
description: Documentación para habilitar y deshabilitar diagnósticos en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a31b88f661c141941cae2d0b01668b26c0bed7d7
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177243"
---
# <a name="diagnostics-system-overview"></a>Introducción al sistema de diagnósticos

El Mixed Reality Toolkit diagnostics proporciona herramientas de diagnóstico que se ejecutan dentro de la aplicación para habilitar el análisis de problemas de la aplicación.

La primera versión del sistema de diagnóstico contiene [Visual Profiler](using-visual-profiler.md) para permitir el análisis de problemas de rendimiento mientras se usa la aplicación.

## <a name="getting-started"></a>Introducción

> [!IMPORTANT]
> Se recomienda **_encarecidamente_** habilitar el sistema de diagnóstico durante todo el ciclo de desarrollo del producto y deshabilitarlo como último cambio antes de compilar y publicar la versión final.

Hay dos pasos clave para empezar a usar el sistema de diagnóstico.

1. [Habilitar](#enable-diagnostics) el sistema de diagnóstico
2. [Configuración de](#configure-diagnostic-options) opciones de diagnóstico

### <a name="enable-diagnostics"></a>Habilitación de diagnósticos

El sistema de diagnóstico se administra mediante el objeto MixedRealityToolkit (u otro componente [de registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios).

En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit. Los pasos necesarios para otros registradores de servicios pueden ser diferentes.

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Vaya al panel Inspector a la sección Sistema de diagnóstico y active Habilitar.
1. Selección de la implementación del sistema de diagnóstico

    ![Selección de la implementación del sistema de diagnósticos](../images/diagnostics/DiagnosticsSelectSystemType.png)

> [!NOTE]
> Los usuarios del perfil predeterminado `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) tendrán el sistema de diagnóstico preconfigurado para usar el [`MixedRealityDiagnosticsSystem`](xref:Microsoft.MixedReality.Toolkit.Diagnostics.MixedRealityDiagnosticsSystem) objeto .

### <a name="configure-diagnostic-options"></a>Configuración de opciones de diagnóstico

El sistema de diagnóstico usa un perfil de configuración para especificar qué componentes se van a mostrar y para configurar sus valores. Consulte [Configuring the Diagnostics System (Configuración](configuring-diagnostics.md) del sistema de diagnóstico) para obtener más información relacionada con la configuración de componentes disponible.

> [!IMPORTANT]
> Aunque es posible usar el modo de reproducción de Unity al desarrollar aplicaciones sin necesidad de los pasos de compilación e implementación, es importante evaluar los resultados del sistema de diagnóstico mediante una aplicación compilada que se ejecuta en el hardware y la plataforma de destino.
>
> Es posible que los diagnósticos de rendimiento, como [Visual Profiler,](using-visual-profiler.md)no reflejen con precisión el rendimiento real de la aplicación cuando se ejecutan desde el editor.

## <a name="see-also"></a>Consulte también

- [Documentación de la API de diagnóstico](xref:Microsoft.MixedReality.Toolkit.Diagnostics)
- [Configuración del sistema de diagnóstico](configuring-diagnostics.md)
- [Uso de Visual Profiler](using-visual-profiler.md)
