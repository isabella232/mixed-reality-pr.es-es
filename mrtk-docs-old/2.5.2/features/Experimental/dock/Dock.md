---
title: Acoplar
description: Descripción de controles de acople.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 3c1235e972de18686800b3dfcd7c7deee194957d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681408"
---
# <a name="dock"></a><span data-ttu-id="f0b1b-104">Acoplar</span><span class="sxs-lookup"><span data-stu-id="f0b1b-104">Dock</span></span>

![Acoplar](../../Images/Dock/MRTK_UX_Dock_Main.png)

<span data-ttu-id="f0b1b-106">Este control permite que los objetos entren y salgan de las posiciones predeterminadas para crear paletas, estanterías y barras de navegación.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-106">This control enables moving objects in and out of predetermined positions, to create palettes, shelves and navigation bars.</span></span>

## <a name="features"></a><span data-ttu-id="f0b1b-107">Características</span><span class="sxs-lookup"><span data-stu-id="f0b1b-107">Features</span></span>

- <span data-ttu-id="f0b1b-108">Admite cualquier número de posiciones y diseños de acoplamiento (funciona muy bien con [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection)).</span><span class="sxs-lookup"><span data-stu-id="f0b1b-108">Supports any number of dock positions and layouts (works great with [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection))</span></span>
- <span data-ttu-id="f0b1b-109">Los objetos acoplados se alejan automáticamente para dejar espacio para los nuevos objetos.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-109">Docked objects automatically move away to make space for new objects</span></span>
- <span data-ttu-id="f0b1b-110">Los objetos se escalan para ajustarse al espacio acoplado y, luego, cambian de tamaño hasta su posición original cuando se arrastran hacia afuera.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-110">Objects scale to fit the docked space, then resize to their original position when dragged out.</span></span>

## <a name="getting-started-with-dock"></a><span data-ttu-id="f0b1b-111">Introducción a Acoplar</span><span class="sxs-lookup"><span data-stu-id="f0b1b-111">Getting started with Dock</span></span>

- <span data-ttu-id="f0b1b-112">Cree un GameObject con el componente Acoplar y agréguele algunos elementos secundarios GameObjects.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-112">Create a GameObject with the Dock component and add some children GameObjects to it.</span></span>
- <span data-ttu-id="f0b1b-113">Agregue el componente DockPosition a cada uno de los elementos secundarios.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-113">Add the DockPosition component to each of the children.</span></span>
- <span data-ttu-id="f0b1b-114">Agregue el componente acoplable a cualquier número de objetos de la escena para permitir que se acoplen.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-114">Add the Dockable component to any number of objects in the scene to allow them to be docked.</span></span> <span data-ttu-id="f0b1b-115">También deben tener el componente [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) y un colisionador.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-115">They must have the [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) component and a Collider as well.</span></span>
- <span data-ttu-id="f0b1b-116">*Opcional:* Use una clase [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) en Acoplar para disponer automáticamente los componentes DockPosition.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-116">*Optional:* use a [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to the Dock to automatically lay out the DockPositions.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f0b1b-117">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="f0b1b-117">Prerequisites</span></span>

- <span data-ttu-id="f0b1b-118">Todos los objetos acoplables deben tener un colisionador con una clase [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) o [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span><span class="sxs-lookup"><span data-stu-id="f0b1b-118">Every dockable object must have a collider with an [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) or [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>
- <span data-ttu-id="f0b1b-119">Si quiere que un objeto se inicie acoplado cuando se cargue la escena, asígnelo a cualquier propiedad de objeto acoplado de DockPosition.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-119">If you want an object to start Docked when the scene loads, assign it to any DockPosition's docked object property.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="f0b1b-120">Funcionamiento</span><span class="sxs-lookup"><span data-stu-id="f0b1b-120">How it works</span></span>

<span data-ttu-id="f0b1b-121">El componente acoplable se basa en los eventos de manipulación para permitir que los objetos arrastrados se acoplen y desacoplen en posiciones específicas.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-121">The Dockable component builds upon manipulation events to allow dragged objects to be docked and undocked in specific positions.</span></span> <span data-ttu-id="f0b1b-122">La selección de ubicación está determinada por el componente DockPosition desencadenado superpuesto más cercano al objeto arrastrado, por lo que ambos objetos deben tener colisionadores para que se active el desencadenador.</span><span class="sxs-lookup"><span data-stu-id="f0b1b-122">The placement is determined by the closest overlapping triggered DockPosition to the dragged object, so both objects need to have Colliders for the trigger to activate.</span></span>
