---
title: Información general del sistema de límites
description: Página de aterrizaje del sistema de límites en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, sistema de límites,
ms.openlocfilehash: fd70479e5183e9a7557de5c5a532cc87161be017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177082"
---
# <a name="boundary-system-overview"></a>Información general del sistema de límites

El sistema de límites proporciona compatibilidad para visualizar componentes de límite de realidad virtual en aplicaciones de realidad mixta. Los límites definen el área en la que los usuarios pueden moverse de forma segura mientras llevan un casco de realidad virtual. Los límites son un componente importante de una experiencia de realidad mixta para ayudar a los usuarios a evitar obstáculos desconocidos al usar un casco de realidad virtual.

Muchas plataformas de realidad virtual proporcionan una pantalla automática, por ejemplo, un contorno blanco superpuesto en el mundo virtual cuando el usuario o su controlador se acerca al límite. El sistema de límites de Mixed Reality Toolkit amplía esta característica para habilitar la presentación de un contorno del área con seguimiento, un plano de la planta y otras características que se pueden usar para proporcionar información adicional a los usuarios.

## <a name="getting-started"></a>Introducción

La adición de compatibilidad con límites requiere dos componentes clave del Mixed Reality Toolkit: el sistema de límites y una plataforma de realidad virtual configurada con un límite.

1. [Habilitación](#enable-boundary-system) del sistema de límites
2. [Configuración de](#configure-boundary-visualization) la visualización de límites
3. [Compilación e implementación](#build-and-deploy) en una plataforma de realidad virtual con un límite configurado

## <a name="enable-boundary-system"></a>Habilitación del sistema de límites

El sistema de límites se administra mediante el objeto MixedRealityToolkit (u otro componente [registrador de](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) servicios).

En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit. Los pasos necesarios para otros registradores de servicios pueden ser diferentes.

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

1. Vaya al panel Inspector a la sección Sistema de límites y active Habilitar.

    ![Habilitar el sistema de límites](../images/boundary/MRTKConfig_Boundary.png)

1. Seleccione la implementación del sistema de límites. La implementación de clase predeterminada proporcionada por MRTK es la [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

    ![Selección de la implementación del sistema de límites](../images/boundary/BoundarySelectSystemType.png)

> [!NOTE]
> Toda la implementación del sistema de límites debe extender el [`IMixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.IMixedRealityBoundarySystem)

## <a name="configure-boundary-visualization"></a>Configuración de la visualización de límites

El [sistema de límites usa un perfil de configuración](configuring-boundary-visualization.md) para especificar qué componentes de límite se van a mostrar y para configurar su apariencia.

![Opciones de visualización de límites](../images/boundary/BoundaryVisualizationProfile.png)

> [!NOTE]
> Los usuarios del perfil predeterminado `DefaultMixedRealityBoundaryVisualizationProfile` (Assets/MRTK/SDK/Profiles) tendrán el sistema de límites preconfigurado para mostrar un plano de planta, el área de juego y el área de seguimiento.

## <a name="build-and-deploy"></a>Compilación e implementación

Una vez configurado el sistema de límites con las opciones de visualización deseadas, el proyecto se puede crear implementado en la plataforma de destino.

> [!NOTE]
> El modo de reproducción de Unity habilita la visualización en el editor del límite configurado. Esta característica permite un desarrollo y pruebas rápidos sin necesidad del paso de compilación e implementación. Asegúrese de realizar pruebas de aceptación finales mediante una versión integrada e implementada de la aplicación, que se ejecuta en el hardware y la plataforma de destino.

## <a name="accessing-boundary-system-via-code"></a>Acceso al sistema de límites mediante código

Si está habilitado y configurado, se puede acceder al sistema de límites a través de la clase auxiliar estática CoreServices. A continuación, la referencia se puede usar para cambiar dinámicamente los parámetros boundary y acceder a los GameObjects relacionados administrados por el sistema.

```c#
// Hide Boundary Walls at runtime
CoreServices.BoundarySystem.ShowBoundaryWalls = false;

// Get Unity GameObject for the floor visualization in scene
GameObject floorVisual = CoreServices.BoundarySystem.GetFloorVisualization();
```

## <a name="see-also"></a>Consulte también

- [Documentación de la API de límites](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [Configuración de la visualización de límites](configuring-boundary-visualization.md)
