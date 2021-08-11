---
title: Acoplar
description: Descripción de controles de acople.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 4446dbe3199aab63d7ee85474d3696a45cf4401f1d8100a8d99885a7265c7fe2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226577"
---
# <a name="dock"></a>Acoplar

![Acoplar](../images/dock/MRTK_UX_Dock_Main.png)

Este control permite que los objetos entren y salgan de las posiciones predeterminadas para crear paletas, estanterías y barras de navegación.

## <a name="features"></a>Características

- Admite cualquier número de posiciones y diseños de acoplamiento (funciona muy bien con [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection)).
- Los objetos acoplados se alejan automáticamente para dejar espacio para los nuevos objetos.
- Los objetos se escalan para ajustarse al espacio acoplado y, luego, cambian de tamaño hasta su posición original cuando se arrastran hacia afuera.

## <a name="getting-started-with-dock"></a>Introducción a Acoplar

- Cree un GameObject con el componente Acoplar y agréguele algunos elementos secundarios GameObjects.
- Agregue el componente DockPosition a cada uno de los elementos secundarios.
- Agregue el componente acoplable a cualquier número de objetos de la escena para permitir que se acoplen. También deben tener el componente [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) y un colisionador.
- *Opcional:* Use una clase [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) en Acoplar para disponer automáticamente los componentes DockPosition.

### <a name="prerequisites"></a>Prerrequisitos

- Todos los objetos acoplables deben tener un colisionador con una clase [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) o [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).
- Si quiere que un objeto se inicie acoplado cuando se cargue la escena, asígnelo a cualquier propiedad de objeto acoplado de DockPosition.

## <a name="how-it-works"></a>Funcionamiento

El componente acoplable se basa en los eventos de manipulación para permitir que los objetos arrastrados se acoplen y desacoplen en posiciones específicas. La selección de ubicación está determinada por el componente DockPosition desencadenado superpuesto más cercano al objeto arrastrado, por lo que ambos objetos deben tener colisionadores para que se active el desencadenador.
