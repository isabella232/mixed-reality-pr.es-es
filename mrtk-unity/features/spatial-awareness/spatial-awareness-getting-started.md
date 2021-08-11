---
title: Introducción al reconocimiento espacial
description: describe el reconocimiento espacial en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: bbe5b923ea7da965424e7fac98adca180c6f91d0c9b4c4ca7a0477e301c362f9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204333"
---
# <a name="spatial-awareness-getting-started"></a>Introducción al reconocimiento espacial

![Reconocimiento espacial](../images/spatial-awareness/MRTK_SpatialAwareness_Main.png)

El sistema de reconocimiento espacial proporciona reconocimiento ambiental del mundo real en aplicaciones de realidad mixta. Cuando se introdujo en Microsoft HoloLens, Spatial Awareness proporcionó una colección de mallas, que representan la geometría del entorno, lo que permitía interacciones atractivas entre hologramas y el mundo real.

> [!NOTE]
> En este momento, el Mixed Reality Toolkit no se incluye con algoritmos de Spatial Understanding como se empaquetaron originalmente en HoloToolkit. La comprensión espacial suele implicar la transformación de los datos de la malla espacial para crear datos de malla simplificados o agrupados, como planos, paredes, plantas, plantas, plantas, etc.

## <a name="getting-started"></a>Introducción

La adición de compatibilidad con el reconocimiento espacial requiere dos componentes clave de la Mixed Reality Toolkit: el sistema de reconocimiento espacial y un proveedor de plataforma compatible.

1. [Habilitación](#enable-the-spatial-awareness-system) del sistema de reconocimiento espacial
2. [Registro](#register-observers) y [configuración de](configuring-spatial-awareness-mesh-observer.md) uno o varios observadores espaciales para proporcionar datos de malla
3. [Compilación e implementación](#build-and-deploy) en una plataforma que admita el reconocimiento espacial

### <a name="enable-the-spatial-awareness-system"></a>Habilitación del sistema de reconocimiento espacial

El sistema de reconocimiento espacial se administra mediante el objeto MixedRealityToolkit (u otro componente [del registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios). Siga estos pasos para habilitar o deshabilitar el sistema *de reconocimiento espacial* en el perfil de *MixedRealityToolkit.*

El Mixed Reality Toolkit incluye algunos perfiles preconfigurados predeterminados. Algunas de ellas tienen el sistema de reconocimiento espacial habilitado o deshabilitado de forma predeterminada. La intención de esta configuración previa, especialmente para cuando está deshabilitada, es evitar la sobrecarga visual de calcular y representar las mallas.

| Perfil | Sistema habilitado de forma predeterminada |
| --- | --- |
| `DefaultHoloLens1ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens1) | False |
| `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2) | False |
| `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles) | True |

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena para abrirlo en el panel inspector.

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Vaya a la sección *Spatial Awareness System (Sistema de reconocimiento espacial)* y active *Enable Spatial Awareness System (Habilitar el sistema de reconocimiento espacial).*

    ![Habilitación del reconocimiento espacial](../images/spatial-awareness/MRTKConfig_SpatialAwareness.png)

1. Seleccione el tipo de implementación del sistema de reconocimiento espacial deseado. es [`MixedRealitySpatialAwarenessSystem`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessSystem) el valor predeterminado proporcionado.

    ![Selección de la implementación del sistema de reconocimiento espacial](../images/spatial-awareness/SpatialAwarenessSelectSystemType.png)

### <a name="register-observers"></a>Registro de observadores

Los servicios de la Mixed Reality Toolkit pueden tener [servicios de](../../architecture/systems-extensions-providers.md) proveedor de datos que complementan el servicio principal con controles de implementación y datos específicos de la plataforma. Un ejemplo de esto es el sistema [](../input/input-providers.md) de entrada Mixed Reality que tiene varios proveedores de datos para obtener información de controlador y otra información de entrada relacionada de varias API específicas de la plataforma.

El sistema de reconocimiento espacial es similar en que los proveedores de datos suministran al sistema datos de malla sobre el mundo real. El perfil de reconocimiento espacial debe tener al menos un observador espacial registrado. Los observadores espaciales suelen ser componentes específicos de la plataforma que actúan como proveedor para mostrar varios tipos de datos de malla desde un punto de conexión específico de la plataforma (es decir, HoloLens).

1. Abrir o expandir el perfil *del sistema de reconocimiento espacial*

    ![Perfil del sistema de reconocimiento espacial](../images/spatial-awareness/SpatialAwarenessProfile.png)

1. Haga clic en *el botón "Agregar observador espacial".*
1. Selección del tipo de *implementación de Observador espacial deseado*

    ![Selección de la implementación del observador espacial](../images/spatial-awareness/SpatialAwarenessSelectObserver.png)

1. [Modificar las propiedades de configuración en el observador según](configuring-spatial-awareness-mesh-observer.md) sea necesario

> [!NOTE]
> Los usuarios `DefaultMixedRealityToolkitConfigurationProfile` de (Assets/MRTK/SDK/Profiles) tendrán preconfigurado el sistema de reconocimiento espacial para la plataforma Windows Mixed Reality que usa la [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) clase .

### <a name="build-and-deploy"></a>Compilación e implementación

Una vez configurado el sistema de reconocimiento espacial con los observadores deseados, el proyecto se puede crear e implementar en la plataforma de destino.

> [!IMPORTANT]
> Si el destino es Windows Mixed Reality plataforma (por ejemplo, HoloLens), es [](/windows/mixed-reality/spatial-mapping-in-unity) importante asegurarse de que la funcionalidad percepción espacial está habilitada para usar el sistema de reconocimiento espacial en el dispositivo.

> [!WARNING]
> Algunas plataformas, Microsoft HoloLens, proporcionan compatibilidad para la ejecución remota desde Unity. Esta característica permite un desarrollo y pruebas rápidos sin necesidad del paso de compilación e implementación. Asegúrese de realizar pruebas de aceptación finales mediante una versión integrada e implementada de la aplicación, que se ejecuta en el hardware y la plataforma de destino.

## <a name="next-steps"></a>Pasos siguientes

Después de seguir los procedimientos anteriores para habilitar el sistema de reconocimiento espacial, el sistema se puede configurar y controlar con más detalle.

Información para configurar observadores en inspector:

- [Configuración de observadores para en el uso de dispositivos](configuring-spatial-awareness-mesh-observer.md)
- [Configuración de observadores para el uso en el editor](spatial-object-mesh-observer.md)

Información para controlar y extender observadores a través del código:

- [Configuración de observadores mediante código](usage-guide.md)
- [Creación de un observador personalizado](create-data-provider.md)

## <a name="see-also"></a>Consulte también

- [Documentación de Spatial Awareness API](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)
- [Información general sobre la asignación espacial WMR](/windows/mixed-reality/spatial-mapping)
- [Asignación espacial en WMR de Unity](/windows/mixed-reality/spatial-mapping-in-unity)
