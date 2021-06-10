---
title: Ventana de dependencias
description: Documentación sobre el uso de la ventana de dependencia en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: fd17db3f365d8bd97b8cd9c43a6111e2b82a61fe
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647030"
---
# <a name="dependency-window"></a><span data-ttu-id="7efaf-104">Ventana Dependencia</span><span class="sxs-lookup"><span data-stu-id="7efaf-104">Dependency window</span></span>

<span data-ttu-id="7efaf-105">En Unity, a menudo es difícil deducir qué recursos se usan y qué hace referencia a ellos.</span><span class="sxs-lookup"><span data-stu-id="7efaf-105">In Unity, it is often difficult to gleam which assets are being used, and what is referencing them.</span></span> <span data-ttu-id="7efaf-106">La opción "Buscar referencias en la escena" funciona muy bien cuando solo está interesado en la escena actual, pero ¿qué ocurre con todo el proyecto de Unity?</span><span class="sxs-lookup"><span data-stu-id="7efaf-106">The "Find References in Scene" option works great when you are only concerned with the current scene, but what about your entire Unity project?</span></span> <span data-ttu-id="7efaf-107">Aquí es donde **la ventana de dependencias** (Assets/MRTK/Tools/DependencyWindow) puede ser útil.</span><span class="sxs-lookup"><span data-stu-id="7efaf-107">This is where the **Dependency Window** (Assets/MRTK/Tools/DependencyWindow) can be useful.</span></span>

<span data-ttu-id="7efaf-108">La ventana Dependencia muestra cómo los recursos hacen referencia y dependen entre sí.</span><span class="sxs-lookup"><span data-stu-id="7efaf-108">The Dependency Window displays how assets reference and depend on each other.</span></span> <span data-ttu-id="7efaf-109">Las dependencias se calculan mediante el análisis de guides dentro de los archivos YAML del proyecto (tenga en cuenta que no se tienen en cuenta las dependencias de script a script).</span><span class="sxs-lookup"><span data-stu-id="7efaf-109">Dependencies are calculated by parsing guids within project YAML files (note, script to script dependencies are not considered).</span></span>

## <a name="usage"></a><span data-ttu-id="7efaf-110">Uso</span><span class="sxs-lookup"><span data-stu-id="7efaf-110">Usage</span></span>

<span data-ttu-id="7efaf-111">Para abrir la ventana, seleccione **Mixed Reality** Ventana de dependencia de utilidades del kit de herramientas, que abrirá la ventana y comenzará automáticamente a compilar el gráfico de  >    >    >   dependencias del proyecto.</span><span class="sxs-lookup"><span data-stu-id="7efaf-111">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Dependency Window** which will open the window and automatically begin building your project's dependency graph.</span></span> <span data-ttu-id="7efaf-112">Una vez creado el gráfico de dependencias, puede seleccionar recursos en la pestaña del proyecto para inspeccionar sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="7efaf-112">Once the dependency graph is built, you can select assets in the project tab to inspect their dependencies.</span></span>

![Ventana Dependencia](../images/dependency-window/MRTK_Dependency_Window.png)

<span data-ttu-id="7efaf-114">La ventana muestra una lista de recursos de los que depende el recurso seleccionado actualmente y una lista jerárquica de recursos que dependen de él.</span><span class="sxs-lookup"><span data-stu-id="7efaf-114">The window displays a list of assets that the currently selected asset depends on, and a hierarchical list of assets that depend on it.</span></span> <span data-ttu-id="7efaf-115">Si nada depende del recurso seleccionado actualmente, puede considerar la posibilidad de eliminarlo del proyecto (tenga en cuenta que algunos recursos se cargan mediante programación a través de API como Shader.Find() y es posible que el seguimiento de dependencias no lo pueda capturar.</span><span class="sxs-lookup"><span data-stu-id="7efaf-115">If nothing depends on the currently selected asset, you can consider deleting it from your project (note that some assets are loaded programmatically via APIs like Shader.Find() and may not be caught by the dependency tracker).</span></span>

<span data-ttu-id="7efaf-116">La ventana también puede mostrar solo una lista de todos los recursos a los que no hace referencia ningún otro activo y que se podrían considerar para su eliminación:</span><span class="sxs-lookup"><span data-stu-id="7efaf-116">The window can also display just a list of all assets which are not referenced by any other assets and could be considered for deletion:</span></span>

![Ventana de dependencia que muestra los recursos sin referencia](../images/dependency-window/MRTK_Dependency_Window_Unreferenced.png)

> [!NOTE]
> <span data-ttu-id="7efaf-118">Si los recursos se modifican, agregan o quitan mientras la ventana de dependencias está en uso, se recomienda actualizar el gráfico de dependencias para obtener los resultados más "actualizados".</span><span class="sxs-lookup"><span data-stu-id="7efaf-118">If assets are modified, added, or removed while the dependency window is in use, it is advised to refresh the dependency graph for the most "up to date" results.</span></span>
