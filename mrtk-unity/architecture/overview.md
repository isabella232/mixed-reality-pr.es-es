---
title: Información general sobre la arquitectura
description: Información general sobre la arquitectura de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, arquitectura de MRTK,
ms.openlocfilehash: 431e091cb6dc0efa0f941b95f58811d57166c82f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281912"
---
# <a name="architecture-overview"></a>Información general sobre la arquitectura

Para obtener una introducción general al contenido de MRTK, la información de arquitectura contenida en este documento le ayudará a comprender lo siguiente:

- Fragmentos grandes de MRTK y cómo se conectan
- Conceptos que MRTK introduce y que pueden no existir en Unity de la vaina
- Cómo funcionan algunos de los sistemas más grandes (como entrada)

Esta sección no está pensada para enseñar a realizar tareas, sino a estructurar estas tareas y por qué.

## <a name="many-audiences-one-toolkit"></a>Muchas audiencias, un kit de herramientas

MRTK no tiene una sola audiencia uniforme. Se ha escrito para admitir casos de uso que van desde hackathons por primera vez hasta personas que construyen experiencias complejas y compartidas para empresas. Es posible que se hayan escrito código y API optimizados para uno más que el otro (es decir, algunas partes de MRTK parecen más optimizadas para la "configuración de un solo clic"), pero es importante tener en cuenta que algunas de ellas son más por motivos históricos y de recursos. A medida que MRTK evoluciona, las características que se van construyendo deben diseñarse para escalarse para admitir la gama de casos de uso.

MRTK también tiene requisitos para escalar correctamente entre las experiencias de REALIDAD virtual y AR. Debe ser fácil compilar aplicaciones que se retrasen correctamente en el comportamiento cuando se implementan en un HoloLens 2 O un HoloLens 1, y debería ser fácil compilar aplicaciones destinadas a OpenVR y WMR (y otras plataformas). Aunque en ocasiones el equipo puede centrar una iteración determinada en un sistema o plataforma específicos, el objetivo a largo plazo es crear una amplia gama de soporte técnico para cualquier lugar donde los usuarios estén creando experiencias de realidad mixta.

## <a name="high-level-breakdown"></a>Desglose de alto nivel

MRTK es una colección de herramientas para obtener rápidamente experiencias de realidad mixta (MR) y también un marco de trabajo de aplicación con opiniones sobre su propio entorno de ejecución, cómo se debe extender y cómo se debe configurar.

En un nivel alto, mrtk se puede desglosar de las maneras siguientes:

![Diagrama de información general de la arquitectura](../features/images/architecture/MRTK_Architecture.png)

MrTK también contiene otro conjunto de utilidades de bolsa de mano que tienen poca o ninguna dependencia en el resto de MRTK (para enumerar algunas: herramientas de compilación, solucionadores, influenciadores de audio, utilidades de suavizado y representadores de línea).

El resto de la documentación de la arquitectura se compilará de abajo hacia arriba, empezando por el marco y el entorno de ejecución, y avanzará a sistemas más interesantes y complejos, como la entrada. Consulte la tabla de contenido para continuar con la introducción a la arquitectura.
