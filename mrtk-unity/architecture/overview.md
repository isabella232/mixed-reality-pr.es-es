---
title: Información general sobre la arquitectura
description: Información general sobre la arquitectura de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, arquitectura de MRTK,
ms.openlocfilehash: 7113ee68a3d8bae016236996725a879c95e31f410cb273184ddcc255ae7a0685
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186610"
---
# <a name="architecture-overview"></a>Información general sobre la arquitectura

Para obtener una introducción general al contenido de MRTK, la información de arquitectura contenida en este documento le ayudará a comprender lo siguiente:

- Grandes fragmentos de MRTK y cómo se conectan
- Conceptos que MRTK introduce y que pueden no existir en unity de la vaina
- Cómo funcionan algunos de los sistemas más grandes (como entrada)

Esta sección no está pensada para enseñar a realizar tareas, sino a cómo estas tareas están estructuradas y por qué.

## <a name="many-audiences-one-toolkit"></a>Muchas audiencias, un kit de herramientas

MRTK no tiene una sola audiencia uniforme. Se ha escrito para admitir casos de uso que abarcan desde hackathones por primera vez hasta personas que construyen experiencias complejas y compartidas para empresas. Es posible que se hayan escrito código y API optimizados para uno más que el otro (es decir, algunas partes de MRTK parecen más optimizadas para la "configuración de un solo clic"), pero es importante tener en cuenta que algunas de ellas son más por motivos históricos y de recursos. A medida que MRTK evoluciona, las características que se crearán deben diseñarse para escalar para admitir la gama de casos de uso.

MRTK también tiene requisitos para escalar correctamente entre experiencias de realidad virtual y ar. Debe ser fácil compilar aplicaciones que se retrasen correctamente en el comportamiento cuando se implementan en un HoloLens 2 O un HoloLens 1, y debería ser sencillo compilar aplicaciones destinadas a OpenVR y WMR (y otras plataformas). Aunque en ocasiones el equipo puede centrar una iteración determinada en un sistema o plataforma específicos, el objetivo a largo plazo es crear una amplia gama de soporte técnico para cualquier lugar en el que las personas estén creando experiencias de realidad mixta.

## <a name="high-level-breakdown"></a>Desglose de alto nivel

MRTK es una colección de herramientas para obtener rápidamente experiencias de realidad mixta (MR) y también un marco de trabajo de aplicación con opiniones sobre su propio tiempo de ejecución, cómo se debe extender y cómo se debe configurar.

En un nivel alto, mrtk se puede desglosar de las maneras siguientes:

![Diagrama de información general de la arquitectura](../features/images/architecture/MRTK_Architecture.png)

MRTK también contiene otro conjunto de utilidades de bolsa de agarre que tienen poca o ninguna dependencia en el resto de MRTK (para enumerar algunas: herramientas de compilación, solucionadores, influenciadores de audio, utilidades de suavizado y representadores de línea).

El resto de la documentación de la arquitectura se compilará de abajo hacia arriba, empezando por el marco y el entorno de ejecución, progresando a sistemas más interesantes y complejos, como la entrada. Consulte la tabla de contenido para continuar con la introducción a la arquitectura.
