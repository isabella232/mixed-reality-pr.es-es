---
title: Modularización MRTK
description: Describe la componenteización en MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 04b2e6155e591a918b95aed20961a0450afe5f43
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144421"
---
# <a name="mixed-reality-toolkit-componentization"></a>componentes Mixed Reality Toolkit

Una de las excelentes características nuevas de Mixed Reality Toolkit v2 es la mejora de la componenteización. Siempre que sea posible, los componentes individuales están aislados de todos los componentes, menos de la capa principal de la base.

## <a name="minimized-dependencies"></a>Dependencias minimizadas

MRTK v2 se desarrolló intencionadamente para ser modular y minimizar las dependencias entre los servicios del sistema (por ejemplo, el reconocimiento espacial).

Debido a la naturaleza de algunos servicios del sistema (por ejemplo, entrada y teleportación), existe un pequeño número de dependencias.

Aunque se espera que los servicios necesiten uno o varios componentes del proveedor de datos, no hay vínculos directos entre ellos. Lo mismo sucede con las características del SDK (por ejemplo, Interfaz de usuario componentes).

## <a name="component-communication"></a>Comunicación de componentes

Para asegurarse de que no hay vínculos directos entre componentes, MRTK v2 usa interfaces para comunicarse entre servicios, proveedores de datos y código de aplicación. Estas interfaces se definen en y toda la comunicación se enruta a través del componente principal Mixed Reality Toolkit.

![Uso del sistema de reconocimiento espacial a través de interfaces](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a>Minimizar la superficie de importación de MRTK

En este momento, mrtk se importa como un único paquete básico (omitiendo por un momento la existencia del paquete de ejemplos, que es un paquete completamente opcional). Es posible reducir esta superficie si se recortan manualmente los archivos importados, aunque se trata de un proceso muy manual que no tiene una guía bien definida.

Es posible desactivar los elementos arbitrarios durante la importación del paquete de Foundation. Sin embargo, no se recomienda hacerlo en una fase temprana del desarrollo, ya que podría interrumpir la funcionalidad. Después de haber descubierto el conjunto de características final de una aplicación, los proveedores y servicios innecesarios se pueden realizar en las carpetas siguientes:

- MRTK/Services
- MRTK/Providers
- MRTK/SDK/Features

> [!NOTE]
> MRTK v2.x **_requiere el_** contenido de la carpeta Assets/MRTK/Core.

## <a name="upcoming-features"></a>Próximas características

### <a name="application-architecture"></a>Arquitectura de la aplicación

MrTK tendrá compatibilidad para permitir que las aplicaciones se puedan crear con una variedad de arquitecturas, entre las que se incluyen:

- [Localizador de servicios MixedRealityToolkit](#mixedrealitytoolkit-service-locator)
- [Servicios individuales](#individual-service-components)
- [Localizador de servicios personalizados](#custom-service-locator)
- [Arquitectura híbrida](#hybrid-architecture)

Al seleccionar una arquitectura de aplicación, es importante tener en cuenta la flexibilidad de diseño y el rendimiento de la aplicación. No se espera que las arquitecturas descritas aquí sean adecuadas para todas las aplicaciones.

#### <a name="mixedrealitytoolkit-service-locator"></a>Localizador de servicios MixedRealityToolkit

MrTK permite (y configura automáticamente) las escenas de aplicación para usar el componente de [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizador de servicios predeterminado. Este componente incluye compatibilidad para configurar sistemas MRTK y proveedores de datos a través de inspectores de configuración y administra la duración de los componentes y los comportamientos principales (por ejemplo, cuándo actualizar).

Todos los sistemas se representan en el inspector de configuración principal, independientemente de si están presentes o no en el proyecto. Consulte la Guía [Mixed Reality configuración de datos](../configuration/mixed-reality-configuration-guide.md) para obtener más información.

#### <a name="individual-service-components"></a>Componentes de servicio individuales

Algunos desarrolladores han expresado su deseo de incluir componentes de servicio individuales en la jerarquía de la escena de la aplicación. Para habilitar este uso, los servicios tendrán que encapsularse en un registrador personalizado o se registrarán por sí solos o se administrarán por sí solos.

Un servicio de registro propio implementaría y se registraría a sí mismo para que el código de la aplicación pudiera detectar la instancia [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) de servicio a través de un registro.

Un servicio de auto-administración podría implementarse como un objeto singleton en la jerarquía de escena. Este objeto proporcionaría y la propiedad de instancia que el código de aplicación podría usar para acceder directamente a la funcionalidad del servicio.

#### <a name="custom-service-locator"></a>Localizador de servicios personalizados

Algunos desarrolladores han solicitado la capacidad de crear un componente de localizador de servicios personalizado. Los localizadores de servicios personalizados implementarían la interfaz y administrarían el ciclo de vida [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) y los comportamientos principales de los servicios activos.

#### <a name="hybrid-architecture"></a>Arquitectura híbrida

MRTK admitirá una arquitectura híbrida en la que los desarrolladores pueden combinar los enfoques anteriores según sea necesario o deseado. Por ejemplo, un desarrollador podría empezar con el localizador [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) de servicios y agregar un servicio de registro propio.

> [!NOTE]
> Al optar por una arquitectura híbrida, es importante tener en cuenta cualquier duplicación de trabajo (por ejemplo, adquirir datos de controlador de varios componentes).
