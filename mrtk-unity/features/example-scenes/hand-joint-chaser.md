---
title: Seguimiento de las articulaciones de la mano
description: "\"Hand joint chaser\" en MRTK"
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144626"
---
# <a name="hand-joint-chaser-example"></a>Ejemplo de "hand joint chaser"

![Buscadores de manos En esta escena de ejemplo se muestra cómo usar ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) solver para adjuntar objetos a las uniones de la mano.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar la escena de ejemplo **HandJointChaserExample** en la `Assets/MRTK/Examples` carpeta en `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Controlador de solucionador

Haga **clic en Objeto al que se ha hecho seguimiento y** seleccione Hand Joint Left or Hand Joint Right (Conjunto de manos a la **izquierda** o a la derecha de **la mano).** Podrá ver la lista desplegable **Tracked Hand Joint (Unión de** mano con seguimiento). En la lista desplegable, puede seleccionar una unión específica de la que realizar el seguimiento. En esta escena de ejemplo se usa el solucionador de vistas radiales para hacer que un objeto siga el objeto de destino. Consulte [la página Solucionador](../ux-building-blocks/solvers/solver.md) para obtener más detalles.

![Solucionador de juntas de mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
