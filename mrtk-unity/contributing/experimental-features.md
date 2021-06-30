---
title: Características experimentales
description: Documento relacionado con las características experimentales de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 341ba0ee3e5900cc52f1ef715232f49064102309
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121383"
---
# <a name="experimental-features"></a><span data-ttu-id="ddbbf-104">Características experimentales</span><span class="sxs-lookup"><span data-stu-id="ddbbf-104">Experimental features</span></span>

<span data-ttu-id="ddbbf-105">Algunas características en las que trabaja el equipo de MRTK parecen tener un gran valor inicial, aunque no hayamos aprendido por completo los detalles.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-105">Some features the MRTK team works on appear to have a lot of initial value even if we haven’t fully fleshed out the details.</span></span> <span data-ttu-id="ddbbf-106">Para estos tipos de características, queremos que la comunidad pueda verlas pronto.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-106">For these types of features, we want the community to get a chance to see them early.</span></span> <span data-ttu-id="ddbbf-107">Dado que están al principio del ciclo, las etiquetamos como experimentales para indicar que siguen evolucionando y sujetas a cambios con el tiempo.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-107">Because they are early in the cycle, we label them as experimental to indicate that they are still evolving, and subject to change over time.</span></span>

## <a name="what-to-expect-from-an-experimental-feature"></a><span data-ttu-id="ddbbf-108">Qué esperar de una característica experimental</span><span class="sxs-lookup"><span data-stu-id="ddbbf-108">What to expect from an experimental feature</span></span>

<span data-ttu-id="ddbbf-109">Si un componente está marcado como experimental, puede esperar lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-109">If a component is marked experimental you can expect the following:</span></span>

- <span data-ttu-id="ddbbf-110">Una escena de ejemplo que muestra el uso, que se encuentra en `MRTK/Examples/Experimental` la sub carpeta</span><span class="sxs-lookup"><span data-stu-id="ddbbf-110">An example scene demonstrating usage, located under `MRTK/Examples/Experimental` sub-folder</span></span>
- <span data-ttu-id="ddbbf-111">Es posible que las características experimentales no tengan documentos.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-111">Experimental features may not have docs.</span></span>
- <span data-ttu-id="ddbbf-112">Probablemente no tengan pruebas.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-112">They probably don't have tests.</span></span>
- <span data-ttu-id="ddbbf-113">Las características experimentales están sujetas a cambios.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-113">Experimental features are subject to change.</span></span>

## <a name="experimental-feature-guidelines"></a><span data-ttu-id="ddbbf-114">Directrices de características experimentales</span><span class="sxs-lookup"><span data-stu-id="ddbbf-114">Experimental feature guidelines</span></span>

### <a name="experimental-code-should-live-in-a-separate-folder"></a><span data-ttu-id="ddbbf-115">El código experimental debe estar en una carpeta independiente</span><span class="sxs-lookup"><span data-stu-id="ddbbf-115">Experimental code should live in a separate folder</span></span>

<span data-ttu-id="ddbbf-116">El código experimental debe ir a una carpeta experimental de nivel superior seguida del nombre de la característica experimental.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-116">Experimental code should go into a top-level experimental folder followed by the experimental feature name.</span></span> <span data-ttu-id="ddbbf-117">Por ejemplo, si intenta aportar una nueva característica FooBar, coloque el código en lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-117">For example, if trying to contribute a new feature FooBar, put code in the following:</span></span>

- <span data-ttu-id="ddbbf-118">Escenas de ejemplo en las que los scripts van a `MRTK/Examples/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="ddbbf-118">Example scenes, scripts go into `MRTK/Examples/Experimental/FooBar/`</span></span>
- <span data-ttu-id="ddbbf-119">Scripts de componentes, elementos prefabs `MRTK/SDK/Experimental/FooBar/`</span><span class="sxs-lookup"><span data-stu-id="ddbbf-119">Component scripts, prefabs go into `MRTK/SDK/Experimental/FooBar/`</span></span>
- <span data-ttu-id="ddbbf-120">Los inspectores de componentes van a `MRTK/SDK/Inspectors/Experimental/FooBar`</span><span class="sxs-lookup"><span data-stu-id="ddbbf-120">Component inspectors go into `MRTK/SDK/Inspectors/Experimental/FooBar`</span></span>

<span data-ttu-id="ddbbf-121">Al usar subcarpetas con el nombre de característica experimental, intente reflejar la misma estructura de carpetas de MRTK.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-121">When using sub-folders under the experimental feature name, try to mirror the same folder structure of MRTK.</span></span>

<span data-ttu-id="ddbbf-122">Por ejemplo, los solucionadores entrarían en `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span><span class="sxs-lookup"><span data-stu-id="ddbbf-122">For example, solvers would go under `MRTK/SDK/Experimental/FooBar/Features/Utilities/Solvers/FooBarSolver.cs`</span></span>

<span data-ttu-id="ddbbf-123">Mantenga las escenas en una carpeta de escena cerca de la parte superior: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span><span class="sxs-lookup"><span data-stu-id="ddbbf-123">Keep scenes in a scene folder near the top: `MRTK/Examples/Experimental/FooBar/Scenes/FooBarExample.unity`</span></span>

> [!NOTE]
> <span data-ttu-id="ddbbf-124">Consideramos que no había una sola carpeta raíz experimental y, en su lugar, colocamos Experimental en say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity` .</span><span class="sxs-lookup"><span data-stu-id="ddbbf-124">We considered not having a single Experimental root folder and instead putting Experimental under say `MRTK/Examples/HandTracking/Scenes/Experimental/HandBasedMenuExample.unity`.</span></span> <span data-ttu-id="ddbbf-125">Hemos decidido usar carpetas en la base para que las características experimentales sean más fáciles de detectar.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-125">We decided to go with folders at the base to make the experimental features easier to discover.</span></span>

### <a name="experimental-code-should-be-in-a-special-namespace"></a><span data-ttu-id="ddbbf-126">El código experimental debe estar en un espacio de nombres especial</span><span class="sxs-lookup"><span data-stu-id="ddbbf-126">Experimental code should be in a special namespace</span></span>

<span data-ttu-id="ddbbf-127">Asegúrese de que el código experimental reside en un espacio de nombres experimental que coincida con la ubicación no experimental.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-127">Ensure that the experimental code lives in an experimental namespace that matches the non-experimental location.</span></span> <span data-ttu-id="ddbbf-128">Por ejemplo, si el componente forma parte de solucionadores en `Microsoft.MixedReality.Toolkit.Utilities.Solvers` , su espacio de nombres debe ser `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers` .</span><span class="sxs-lookup"><span data-stu-id="ddbbf-128">For example, if your component is part of solvers at `Microsoft.MixedReality.Toolkit.Utilities.Solvers`, its namespace should be `Microsoft.MixedReality.Toolkit.Experimental.Utilities.Solvers`.</span></span>

<span data-ttu-id="ddbbf-129">Consulte [esta pr.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) para obtener un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-129">See [this PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) for an example.</span></span>

### <a name="experimental-features-should-have-an-experimental-attribute"></a><span data-ttu-id="ddbbf-130">Las características experimentales deben tener un atributo [Experimental]</span><span class="sxs-lookup"><span data-stu-id="ddbbf-130">Experimental features should have an [Experimental] attribute</span></span>

<span data-ttu-id="ddbbf-131">Agregue un atributo encima de uno de los campos para que aparezca un pequeño cuadro de diálogo en el editor de componentes que mencione que la característica es experimental y está sujeta `[Experimental]` a cambios importantes.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-131">Add an `[Experimental]` attribute above one of your fields to have a small dialog appear in the component editor that mentions your feature is experimental and subject to significant changes.</span></span>

### <a name="menus-for-experimental-features-should-go-under-experimental-sub-menu"></a><span data-ttu-id="ddbbf-132">Los menús de las características experimentales deben ir en el submenú "Experimental".</span><span class="sxs-lookup"><span data-stu-id="ddbbf-132">Menus for experimental features should go under "Experimental" sub-menu</span></span>

<span data-ttu-id="ddbbf-133">Asegúrese de que las características experimentales están en submenúes "experimentales" al agregar comandos a los menús del editor.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-133">Ensure that experimental features are under "experimental" sub-menus when adding commands to menus in the editor.</span></span> <span data-ttu-id="ddbbf-134">Estos son algunos ejemplos:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-134">Here are a few examples:</span></span>

<span data-ttu-id="ddbbf-135">Agregar un comando de menú de nivel superior:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-135">Adding a top-level menu command:</span></span>

```c#
[MenuItem("Mixed Reality Toolkit/Experimental/MyCommand")]
public static void MyCommand()
```

<span data-ttu-id="ddbbf-136">Agregar un menú de componentes:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-136">Adding a component menu:</span></span>

```c#
[AddComponentMenu("MRTK/Experimental/MyCommand")]
```

## <a name="documentation"></a><span data-ttu-id="ddbbf-137">Documentación</span><span class="sxs-lookup"><span data-stu-id="ddbbf-137">Documentation</span></span>

<span data-ttu-id="ddbbf-138">Siga estos pasos para agregar documentación para la característica experimental:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-138">Follow these steps to add documentation for your experimental feature:</span></span>

1. <span data-ttu-id="ddbbf-139">Cualquier documentación de una característica experimental debe ir en un `readme.md` archivo de la carpeta experimental.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-139">Any documentation for an experimental feature should go in a `readme.md` file in the experimental folder.</span></span> <span data-ttu-id="ddbbf-140">Por ejemplo, MRTK/SDK/Experimental/PulseShader/readme.md.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-140">For example, MRTK/SDK/Experimental/PulseShader/readme.md.</span></span>

1. <span data-ttu-id="ddbbf-141">En *Información general de características,* agregue un vínculo en la sección *Experimental* de [`Documentation/toc.yml`](../toc.yml) .</span><span class="sxs-lookup"><span data-stu-id="ddbbf-141">Under *Feature Overviews* Add a link in the *Experimental* section at [`Documentation/toc.yml`](../toc.yml).</span></span>

### <a name="minimize-impact-to-mrtk-code"></a><span data-ttu-id="ddbbf-142">Minimizar el impacto en el código MRTK</span><span class="sxs-lookup"><span data-stu-id="ddbbf-142">Minimize impact to MRTK code</span></span>

<span data-ttu-id="ddbbf-143">Aunque el cambio de MRTK puede hacer que el experimento funcione, podría afectar a otras personas de maneras que no se esperan.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-143">While your MRTK change might get your experiment to work, it could impact other people in ways you do not expect.</span></span>
<span data-ttu-id="ddbbf-144">Las regresiones que realice al código principal de MRTK darían lugar a la reversión de la solicitud de extracción.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-144">Any regressions you make to the MRTK core code would result in your pull request getting reverted.</span></span>

<span data-ttu-id="ddbbf-145">El objetivo es tener cero cambios en las carpetas que no son las carpetas experimentales.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-145">Aim to have zero changes in folders other than experimental folders.</span></span> <span data-ttu-id="ddbbf-146">Esta es una lista de carpetas que pueden tener cambios experimentales:</span><span class="sxs-lookup"><span data-stu-id="ddbbf-146">Here is a list of folders that can have experimental changes:</span></span>

- <span data-ttu-id="ddbbf-147">MRTK/SDK/Experimental</span><span class="sxs-lookup"><span data-stu-id="ddbbf-147">MRTK/SDK/Experimental</span></span>
- <span data-ttu-id="ddbbf-148">MRTK/SDK/Inspectors/Experimental</span><span class="sxs-lookup"><span data-stu-id="ddbbf-148">MRTK/SDK/Inspectors/Experimental</span></span>
- <span data-ttu-id="ddbbf-149">MRTK/Examples/Experimental</span><span class="sxs-lookup"><span data-stu-id="ddbbf-149">MRTK/Examples/Experimental</span></span>

<span data-ttu-id="ddbbf-150">Los cambios fuera de estas carpetas se deben tratar con mucho cuidado.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-150">Changes outside of these folders should be treated very carefully.</span></span> <span data-ttu-id="ddbbf-151">Si la característica experimental debe incluir cambios en el código principal de MRTK, considere la posibilidad de dividir los cambios de MRTK en una solicitud de extracción independiente que incluya pruebas y documentación.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-151">If your experimental feature must include changes to MRTK core code, consider splitting out MRTK changes into a separate pull request that includes tests and documentation.</span></span>

### <a name="using-your-experimental-feature-should-not-impact-peoples-ability-to-use-core-controls"></a><span data-ttu-id="ddbbf-152">El uso de la característica experimental no debería afectar a la capacidad de las personas de usar controles principales</span><span class="sxs-lookup"><span data-stu-id="ddbbf-152">Using your experimental feature should not impact people's ability to use core controls</span></span>

<span data-ttu-id="ddbbf-153">La mayoría de las personas usan componentes principales de la experiencia de usuario como el botón, ManipulationHandler e Interactable con mucha frecuencia.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-153">Most people use core UX components like the button, ManipulationHandler and Interactable very frequently.</span></span> <span data-ttu-id="ddbbf-154">Es probable que no usen la característica experimental si les impide usar botones.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-154">They will likely not use your experimental feature if it prevents them from using buttons.</span></span>

<span data-ttu-id="ddbbf-155">El uso del componente no debe interrumpir botones, ManipulationHandler, BoundingBox o interactuable.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-155">Using your component should not break buttons, ManipulationHandler, BoundingBox, or interactable.</span></span>

<span data-ttu-id="ddbbf-156">Por ejemplo, en esta [pr. ScrollableObjectCollection,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001)la adición de ScrollableObjectCollection hizo que los usuarios no puedan usar los elementos prefabs del botón HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-156">For example, in [this ScrollableObjectCollection PR](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6001), adding a ScrollableObjectCollection caused people to not be able to use the HoloLens button prefabs.</span></span> <span data-ttu-id="ddbbf-157">Aunque esto no fue causado por un error en la pr (sino que expuso un error existente), impidió que la PR se registrase.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-157">Even though this was not caused by a bug in the PR (but rather exposed an existing bug), it prevented the PR from getting checked in.</span></span>

### <a name="provide-an-example-scene-that-demonstrates-how-to-use-the-feature"></a><span data-ttu-id="ddbbf-158">Proporcionar una escena de ejemplo que muestra cómo usar la característica</span><span class="sxs-lookup"><span data-stu-id="ddbbf-158">Provide an example scene that demonstrates how to use the feature</span></span>

<span data-ttu-id="ddbbf-159">Los usuarios deben ver cómo usar la característica y cómo probarla.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-159">People need to see how to use your feature, and how to test it.</span></span>

<span data-ttu-id="ddbbf-160">Proporcione un ejemplo en MRTK/Examples/Experimental/YOUR_FEATURE</span><span class="sxs-lookup"><span data-stu-id="ddbbf-160">Provide an example under MRTK/Examples/Experimental/YOUR_FEATURE</span></span>

### <a name="minimize-user-visible-flaws-in-experimental-features"></a><span data-ttu-id="ddbbf-161">Minimizar los errores visibles del usuario en las características experimentales</span><span class="sxs-lookup"><span data-stu-id="ddbbf-161">Minimize user visible flaws in experimental features</span></span>

<span data-ttu-id="ddbbf-162">Otros no usarán la característica experimental si no funciona, no se graduará en una característica.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-162">Others will not use the experimental feature if it does not work, it will not graduate to a feature.</span></span>

<span data-ttu-id="ddbbf-163">Pruebe la escena de ejemplo en la plataforma de destino y asegúrese de que funciona según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-163">Test your example scene on your target platform, make sure it works as expected.</span></span> <span data-ttu-id="ddbbf-164">Asegúrese de que la característica también funciona en el editor, para que los usuarios puedan iterar rápidamente y ver la característica incluso si no tienen la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-164">Make sure your feature also works in editor, so people can rapidly iterate and see your feature even if they don’t have the target platform.</span></span>

## <a name="graduating-experimental-code-into-mrtk-code"></a><span data-ttu-id="ddbbf-165">Pasar código experimental al código MRTK</span><span class="sxs-lookup"><span data-stu-id="ddbbf-165">Graduating experimental code into MRTK code</span></span>

<span data-ttu-id="ddbbf-166">Si una característica termina viendo bastante uso, debemos convertirla en código MRTK básico.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-166">If a feature ends up seeing quite a lot of use, then we should graduate it into core MRTK code.</span></span> <span data-ttu-id="ddbbf-167">Para ello, la característica debe tener pruebas, documentación y una escena de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-167">To do this, the feature should have tests, documentation, and an example scene.</span></span>

<span data-ttu-id="ddbbf-168">Cuando esté listo para recibir la característica MRTK, cree un problema con el que comprobar la pr.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-168">When you are ready to graduate the feature MRTK, create an issue to check in your PR against.</span></span> <span data-ttu-id="ddbbf-169">La PR debe incluir todas las cosas necesarias para convertir esta característica en una característica principal: pruebas, documentación y una escena de ejemplo que muestra el uso.</span><span class="sxs-lookup"><span data-stu-id="ddbbf-169">The PR should include all the things needed to make this a core feature: tests, documentation, and an example scene showing usage.</span></span>

<span data-ttu-id="ddbbf-170">Además, no olvide actualizar los espacios de nombres para quitar el subespacio "Experimental".</span><span class="sxs-lookup"><span data-stu-id="ddbbf-170">Also, don’t forget to update the namespaces to remove the “Experimental” subspace.</span></span>
