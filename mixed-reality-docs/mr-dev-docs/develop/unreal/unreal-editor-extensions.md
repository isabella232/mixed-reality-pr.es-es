---
title: Extensiones de editor en Unreal
description: Aprenda a ampliar el editor de Unreal Engine con scripts personalizados, acciones con scripts y widgets de utilidad.
author: hferrone
ms.author: safarooq
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, editor extensions, Unreal editor, UE4, HoloLens, HoloLens 2, mixed reality, development, documentation, guides, features, mixed reality headset, windows mixed reality headset, virtual reality headset, porting, upgrading
ms.openlocfilehash: ee0ba5d1d60b83dc334204e12283c76a877b4ec8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584942"
---
# <a name="editor-extensions-in-unreal"></a>Extensiones de editor en Unreal

Unreal proporciona un amplio conjunto de características que le permiten personalizar el motor según sus necesidades. Estas características van desde sencillas, pero limitadas, hasta muy eficaces, pero complejas. Los pasos siguientes se muestran en orden de creciente complejidad. En general, debe acceder a las soluciones más sencillas a su problema y agotar sus opciones antes de pasar a una opción más compleja. Por ejemplo, hemos descubierto que el script de construcción básico se puede usar en lugar de los complementos la mayor parte del tiempo. 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a>Scripts de construcción

Puede usar scripts de construcción para realizar acciones de inicialización, que se ejecutan cuando se crea la instancia del plano técnico.

* [Script de construcciones de usuario](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [Ejemplo de plano técnico](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [Tutorial en vídeo](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a>Acciones con scripts

Las acciones con scripts son planos técnicos de la utilidad del editor. Siga estos pasos para iniciarlos en el editor de Unreal:
* Haga clic con el botón derecho en **Assets** (Recursos) en el explorador de contenido.
* También puede hacer clic con el botón derecho en **Actors** (Actores) en Level Viewport (Ventanilla de nivel) o World Outliner (Esquematizador del mundo).

Las acciones con scripts son exclusivas para momentos en los que necesite que la lógica del plano técnico reconozca los conjuntos de recursos o actores del contexto. Normalmente, una acción con scripts obtiene una lista de recursos o actores que ha seleccionado al ejecutar la acción y, a continuación, modifica esos objetos o los considera en su gráfico.

* [Acciones con scripts](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [Ejecución de acciones con scripts al iniciar un proyecto](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a>Widgets de la utilidad del editor

Puede usar [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) (Widgets de la utilidad del editor) siempre que quiera agregar nuevos elementos de UI para modificar la interfaz de usuario (UI) del editor de Unreal. Los widgets de la utilidad del editor se basan en gráficos de movimiento de Unreal (UMG), por lo que puede configurar widgets en un plano técnico como lo haría con cualquier otro plano técnico de widgets de UMG.

Estos widgets son específicos para la UI del editor y se pueden usar para crear pestañas del editor personalizadas. Después, puede seleccionar estas pestañas personalizadas desde el menú Windows (Ventanas), del mismo modo que seleccionaría pestañas del editor existentes.

## <a name="plugins"></a>Complementos

Unreal le permite desarrollar y administrar sus propios [complementos](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) para usarlos con el entorno en tiempo de ejecución y las herramientas de UE4. Puede habilitar o deshabilitar los complementos en cualquier momento desde el editor de Unreal. Los complementos pueden agregar funcionalidad de juego en tiempo de ejecución, modificar características de Engine integradas, crear nuevos tipos de archivo y ampliar las capacidades del editor.

<!-- ## Engine modifications -->

