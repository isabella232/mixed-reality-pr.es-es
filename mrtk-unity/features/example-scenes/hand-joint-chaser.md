---
title: Seguimiento de las articulaciones de la mano
description: "\"Hand joint chaser\" en MRTK"
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189572"
---
# <a name="hand-joint-chaser"></a>Seguimiento de las articulaciones de la mano

![Buscadores de manos En esta escena de ejemplo se muestra cómo usar ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) solver para adjuntar objetos a las uniones de la mano.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar la escena de ejemplo **HandJointChaserExample** en la `Assets/MRTK/Examples` carpeta en `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Controlador de solucionador

Haga **clic en Objeto al que se ha hecho seguimiento y** seleccione Hand Joint Left or Hand Joint Right (Hacer referencia a un objeto al que se ha hecho seguimiento) y seleccione Hand Joint **Left** (Unión de mano izquierda) o Hand Joint **Right (Derecha de** Podrá ver la lista desplegable **Tracked Hand Joint (Unión de** mano con seguimiento). En la lista desplegable, puede seleccionar una unión específica de la que realizar el seguimiento. En esta escena de ejemplo se usa el solucionador de vistas radiales para hacer que un objeto siga el objeto de destino. Consulte [la página Solucionador](../ux-building-blocks/solvers/solver.md) para obtener más detalles.

![Solucionador de juntas de mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
