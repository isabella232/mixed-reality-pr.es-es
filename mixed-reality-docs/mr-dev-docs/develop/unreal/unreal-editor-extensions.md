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
# <a name="editor-extensions-in-unreal"></a><span data-ttu-id="6bcc7-104">Extensiones de editor en Unreal</span><span class="sxs-lookup"><span data-stu-id="6bcc7-104">Editor extensions in Unreal</span></span>

<span data-ttu-id="6bcc7-105">Unreal proporciona un amplio conjunto de características que le permiten personalizar el motor según sus necesidades.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-105">Unreal provides an extensive set of features that allow you to customize the engine to your needs.</span></span> <span data-ttu-id="6bcc7-106">Estas características van desde sencillas, pero limitadas, hasta muy eficaces, pero complejas.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-106">The features range from simple but limited, to very powerful but complex.</span></span> <span data-ttu-id="6bcc7-107">Los pasos siguientes se muestran en orden de creciente complejidad.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-107">The following steps are listed in order of increasing complexity.</span></span> <span data-ttu-id="6bcc7-108">En general, debe acceder a las soluciones más sencillas a su problema y agotar sus opciones antes de pasar a una opción más compleja.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-108">In general, you should reach for simpler solutions to your problem, and exhausting its options, before moving to a more complex option.</span></span> <span data-ttu-id="6bcc7-109">Por ejemplo, hemos descubierto que el script de construcción básico se puede usar en lugar de los complementos la mayor parte del tiempo.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-109">As an example, we have found that the basic Construction Script can be used in lieu of plugins most of the time.</span></span> 

<!-- Also, engine modification should be a last resort, as it is not only complex, but integrating changes back into the engine for simple work-around can take a disproportionately long time. -->

## <a name="construction-scripts"></a><span data-ttu-id="6bcc7-110">Scripts de construcción</span><span class="sxs-lookup"><span data-stu-id="6bcc7-110">Construction scripts</span></span>

<span data-ttu-id="6bcc7-111">Puede usar scripts de construcción para realizar acciones de inicialización, que se ejecutan cuando se crea la instancia del plano técnico.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-111">You can use construction scripts to perform initialization actions, which run when Blueprint instance are created.</span></span>

* [<span data-ttu-id="6bcc7-112">Script de construcciones de usuario</span><span class="sxs-lookup"><span data-stu-id="6bcc7-112">User Constructions script</span></span>](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/UserGuide/UserConstructionScript/index.html)
* [<span data-ttu-id="6bcc7-113">Ejemplo de plano técnico</span><span class="sxs-lookup"><span data-stu-id="6bcc7-113">Blueprint example</span></span>](https://docs.unrealengine.com/Resources/ContentExamples/Blueprints/1_4/index.html)
* [<span data-ttu-id="6bcc7-114">Tutorial en vídeo</span><span class="sxs-lookup"><span data-stu-id="6bcc7-114">Video tutorial</span></span>](https://www.youtube.com/watch?v=z1SD-d9yJmQ&ab_channel=UnrealEngine)

## <a name="scripted-actions"></a><span data-ttu-id="6bcc7-115">Acciones con scripts</span><span class="sxs-lookup"><span data-stu-id="6bcc7-115">Scripted actions</span></span>

<span data-ttu-id="6bcc7-116">Las acciones con scripts son planos técnicos de la utilidad del editor.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-116">Scripted Actions are Editor Utility Blueprints.</span></span> <span data-ttu-id="6bcc7-117">Siga estos pasos para iniciarlos en el editor de Unreal:</span><span class="sxs-lookup"><span data-stu-id="6bcc7-117">You can launch them in the Unreal Editor by:</span></span>
* <span data-ttu-id="6bcc7-118">Haga clic con el botón derecho en **Assets** (Recursos) en el explorador de contenido.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-118">Right-clicking **Assets** in the Content Browser</span></span>
* <span data-ttu-id="6bcc7-119">También puede hacer clic con el botón derecho en **Actors** (Actores) en Level Viewport (Ventanilla de nivel) o World Outliner (Esquematizador del mundo).</span><span class="sxs-lookup"><span data-stu-id="6bcc7-119">Or by right-clicking **Actors** either in the Level Viewport or in the World Outliner</span></span>

<span data-ttu-id="6bcc7-120">Las acciones con scripts son exclusivas para momentos en los que necesite que la lógica del plano técnico reconozca los conjuntos de recursos o actores del contexto.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-120">Scripted Actions are uniquely suited for times when you need your Blueprint logic to have contextual awareness about sets of Assets or Actors.</span></span> <span data-ttu-id="6bcc7-121">Normalmente, una acción con scripts obtiene una lista de recursos o actores que ha seleccionado al ejecutar la acción y, a continuación, modifica esos objetos o los considera en su gráfico.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-121">Typically, a Scripted Action gets a list of Assets or Actors that you've selected when the action is executed, then modifies those objects or considers them in its graph.</span></span>

* [<span data-ttu-id="6bcc7-122">Acciones con scripts</span><span class="sxs-lookup"><span data-stu-id="6bcc7-122">Scripted Actions</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/ScriptedActions/index.html)
* [<span data-ttu-id="6bcc7-123">Ejecución de acciones con scripts al iniciar un proyecto</span><span class="sxs-lookup"><span data-stu-id="6bcc7-123">Running scripted actions on project startup</span></span>](https://docs.unrealengine.com/ProductionPipelines/ScriptingAndAutomation/Blueprints/StartupObjects/index.html)

## <a name="editor-utility-widgets"></a><span data-ttu-id="6bcc7-124">Widgets de la utilidad del editor</span><span class="sxs-lookup"><span data-stu-id="6bcc7-124">Editor utility widgets</span></span>

<span data-ttu-id="6bcc7-125">Puede usar [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) (Widgets de la utilidad del editor) siempre que quiera agregar nuevos elementos de UI para modificar la interfaz de usuario (UI) del editor de Unreal.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-125">You can use [Editor Utility Widgets](https://docs.unrealengine.com/InteractiveExperiences/UMG/UserGuide/EditorUtilityWidgets/index.html) anytime you want to add new UI elements to modify the User Interface (UI) of the Unreal Editor.</span></span> <span data-ttu-id="6bcc7-126">Los widgets de la utilidad del editor se basan en gráficos de movimiento de Unreal (UMG), por lo que puede configurar widgets en un plano técnico como lo haría con cualquier otro plano técnico de widgets de UMG.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-126">Editor Utility Widgets are based on Unreal Motion Graphics (UMG), so you can set up Widgets in a Blueprint like you would for any other UMG Widget Blueprint.</span></span>

<span data-ttu-id="6bcc7-127">Estos widgets son específicos para la UI del editor y se pueden usar para crear pestañas del editor personalizadas.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-127">These Widgets are specifically for the Editor UI, and you can use them to create custom Editor tabs.</span></span> <span data-ttu-id="6bcc7-128">Después, puede seleccionar estas pestañas personalizadas desde el menú Windows (Ventanas), del mismo modo que seleccionaría pestañas del editor existentes.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-128">You can then select these custom tabs from the Windows menu, like you would select existing Editor tabs.</span></span>

## <a name="plugins"></a><span data-ttu-id="6bcc7-129">Complementos</span><span class="sxs-lookup"><span data-stu-id="6bcc7-129">Plugins</span></span>

<span data-ttu-id="6bcc7-130">Unreal le permite desarrollar y administrar sus propios [complementos](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) para usarlos con el entorno en tiempo de ejecución y las herramientas de UE4.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-130">Unreal lets you develop and manage your own custom [plugins](https://docs.unrealengine.com/ProductionPipelines/Plugins/index.html) for use with UE4 tools and runtime.</span></span> <span data-ttu-id="6bcc7-131">Puede habilitar o deshabilitar los complementos en cualquier momento desde el editor de Unreal.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-131">You can enable or disable your plugins at any time in the Unreal Editor.</span></span> <span data-ttu-id="6bcc7-132">Los complementos pueden agregar funcionalidad de juego en tiempo de ejecución, modificar características de Engine integradas, crear nuevos tipos de archivo y ampliar las capacidades del editor.</span><span class="sxs-lookup"><span data-stu-id="6bcc7-132">Plugins can add runtime gameplay functionality, modify built-in Engine features, create new file types, and extend the capabilities of the Editor.</span></span>

<!-- ## Engine modifications -->

