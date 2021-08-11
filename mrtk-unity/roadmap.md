---
title: Plan de desarrollo
description: documentación para la delineación de la hoja de ruta de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: b591d3ed7bd3c470bdf5b9598864f35963fb99a9957c5ceefdd1417372a3b97e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203237"
---
# <a name="roadmap"></a>Plan de desarrollo

En este documento se describe el mapa de ruta de la Mixed Reality Toolkit. Tenga en cuenta que lo siguiente refleja el trabajo que está en desarrollo y las fechas de destino reflejan las estimaciones.

## <a name="current-release"></a>Versión actual

Microsoft Mixed Reality Toolkit v2.6

## <a name="upcoming-releases"></a>Próximas versiones

| Producto | Descripción | Escala de tiempo | Project placa |
| --- | --- | --- | --- |
| [MRTK V2.7](#270) | Siguiente iteración de MRTK | Mayo de 2021 | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

Las versiones se centra en temas (por ejemplo, áreas de características grandes) y están programadas para producirse aproximadamente cada 8-12 semanas.

Los detalles de la versión, incluidos los elementos de trabajo pendiente, se pueden encontrar en las [GitHub de hitos](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones). El conjunto completo de problemas abiertos también se puede encontrar en [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a>Mixed Reality Toolkit mapa de ruta de Mixed Reality Toolkit (MRTK)

El Mixed Reality Toolkit está diseñado para ser multiplataforma MR/AR/VR/XR por diseño. El kit de herramientas admite actualmente Unity 2019.4.x y Unity 2018.4.x.

> Cuando Unity publica un producto LTS (soporte técnico a largo plazo), el Mixed Reality Toolkit actualizará a la versión LTS. Aunque el Mixed Reality Toolkit se ejecuta en la versión más reciente de la rama tecnológica no beta (por ejemplo, 2020.1) de Unity, no se admite oficialmente.

### <a name="270"></a>2.7.0

Actualmente estamos planeando la versión 2.7.0 y pronto tendrá más actualizaciones.
Para obtener el estado más reciente de la versión, visite la página [del hito](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).

Estado: Planeamiento

Escala de tiempo de destino: mayo de 2021

Temas:

- Stability 
- Expansión de plataforma: OpenXR
- Experiencia del usuario
- Educación para desarrolladores
- Packaging

**Estabilidad**

La calidad y la estabilidad son la prioridad principal para esta y todas las versiones Mixed Reality Toolkit Microsoft. Seguiremos priorizando los problemas de clientes y asociados que afectan a la estabilidad de los componentes de MRTK.

**Expansión de plataforma: OpenXR**

El equipo de MRTK admite el futuro abierto de la realidad mixta a través [de OpenXR.](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672) La compatibilidad con OpenXR está actualmente en desarrollo, con compatibilidad con la versión preliminar inicial publicada en MRTK 2.5.2.

**Experiencia del usuario**

Estamos escuchando sus comentarios sobre MRTK y tenemos planes continuos para:

- Corrección de errores
- Hacer que los controles de la experiencia de usuario de MRTK sean más fáciles de entender
- HoloLens Paridad del shell
- Pruebas para asegurarse de que las características no se revierte

**Educación para desarrolladores**

Hemos migrado nuestra documentación para desarrolladores de GitHub a una nueva plataforma de documentos. Queremos escuchar sus comentarios para que podamos seguir mejorando nuestra experiencia de documentación para desarrolladores.
Actualmente tenemos [tutoriales de MRTK](/windows/mixed-reality/develop/unity/tutorials) que se encuentran en una sección diferente de Mixed Reality documentos. Migraremos estos tutoriales para que se realicen con el resto de la documentación de MRTK. 

**Packaging**

La [herramienta Mixed Reality características es](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) una nueva manera para que los desarrolladores detecten, actualicen y agreguen paquetes Mixed Reality características en proyectos de Unity. Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación. Tenemos previsto realizar actualizaciones en la herramienta de características Mixed Reality a medida que respondamos a solicitudes y errores de características.

## <a name="backlog"></a>Trabajo pendiente

En la lista siguiente se resaltan algunas de las inversiones clave que el equipo de MRTK pretende llevar a cabo.

- Expansión de la plataforma
- Extensibilidad
- Modularidad
- Características de accesibilidad
- Mejoras de globalización
- Compatibilidad con servicios en la nube
- Herramientas
