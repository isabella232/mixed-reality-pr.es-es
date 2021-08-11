---
title: Procedimientos recomendados generales
description: Manténgase al día de todas las prácticas recomendadas para desarrollar aplicaciones de realidad mixta en Unreal Engine.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, editor extensions, Unreal editor, UE4, HoloLens, HoloLens 2, mixed reality, development, documentation, guides, features, mixed reality headset, windows mixed reality headset, virtual reality headset, porting, upgrading
ms.openlocfilehash: 822e64d873952bdb4bb1fb91da4c85f956a1eb513c92d4afee7bfebb18a824eb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203276"
---
# <a name="general-best-practices"></a>Procedimientos recomendados generales

A continuación se indican algunos procedimientos recomendados generales que se recomienda que sigan todos los desarrolladores al crear un proyecto de Unreal Engine para Mixed Reality.

## <a name="constructors"></a>Constructores

Si necesita el equivalente a un "constructor" en planos técnicos, use el [script de construcción](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html) de Unreal. La principal ventaja de usar los eventos "BeginPlay" es que el script del constructor se ejecuta también en el "editor". La mayoría de las veces, los valores se pueden almacenar en caché directamente desde el principio o en el momento de la compilación.

> [!NOTE]
> Puede encontrar más información complementaria para los scripts de construcción en nuestra [introducción a las extensiones de editor](unreal-editor-extensions.md#construction-scripts).

## <a name="3d-buttons-and-textures"></a>Botones y texturas 3D

Es natural pensar en el rendimiento al crear o planear usar botones 3D en aplicaciones de realidad mixta. Sin embargo, no es necesario hacerlo todo desde mallas para que se perciba como 3D. Tiene la opción de usar Paper2D con texturas diseñadas cuidadosamente para obtener ese aspecto 3D. Esto funciona realmente bien con los botones que "parecen" 3D, pero que solo son imágenes retocadas en un cuádruplo. Una versión sofisticada de esto se denomina [sprite](https://docs.unrealengine.com/AnimatingObjects/Paper2D/Sprites/index.html).

## <a name="variants"></a>Variantes

Use [variantes de Unreal](https://docs.unrealengine.com/Basics/Levels/Variants/index.html) en escenarios en los que esté creando una escena con varias configuraciones de objeto en tiempo de ejecución. Las variaciones pueden incluir materiales o mallas cambiantes. 

## <a name="animation"></a>Animación

Aproveche las ventajas del [componente spline](https://docs.unrealengine.com/API/Runtime/Engine/Components/USplineComponent/index.html) (no del componente de "malla" de spline) y los [nodos de escala de tiempo](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Timelines/index.html) si va a crear una gran cantidad de "animaciones interactuables". 

<!-- You can find a comprehensive [video tutorial here](https://www.youtube.com/watch?v=bWXI91FdMtk&ab_channel=DoubleCrossGames). -->

## <a name="communications"></a>Comunicaciones

Use un [plano técnico de nivel](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/Types/LevelBlueprint/index.html) si tiene problemas para encontrar objetos de forma dinámica o se usa demasiado ancho de banda para comunicarse entre varios actores y planos técnicos. Recuerde que Unreal Engine 4 no es como Unity, no todo debe estar dentro de un componente. Los planos técnicos de nivel son una manera perfectamente válida y recomendada de simplificar la comunicación entre varios actores. Las referencias a objetos incluso se pueden "almacenar en caché" en el inicio en el plano técnico de nivel OnBeginPlay.

## <a name="global-state"></a>Estado global

A menudo, necesitará almacenar el estado específico del nivel, como la puntuación, los datos de nivel, la información específica del jugador o cualquier otro elemento que no pertenezca a un objeto determinado. No pase por alto [GameMode](https://docs.unrealengine.com/en-US/InteractiveExperiences/Framework/GameMode/index.html). La mayoría de los usuarios olvidan que existe, pero GameMode se puede crear por nivel y contener datos específicos para cada nivel.

## <a name="optimizing-blueprints"></a>Optimización de planos técnicos

Si observa que los planos técnicos son demasiado lentos, deje que Unreal los "nativice" antes de realizar una reordenación para reescribir el código en C++. Pruebe a usar la [nativización](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/TechnicalGuide/NativizingBlueprints/index.html) automática antes de crear su propia solución personalizada.

![Configuración de Blueprints con el método de nativización de plano técnico con la opción Inclusive (Incluido) resaltada](images/unreal-general-practices-img-01.jpg)
