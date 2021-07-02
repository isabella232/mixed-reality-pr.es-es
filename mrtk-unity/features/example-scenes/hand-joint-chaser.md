---
title: Buscada de juntas de mano
description: "\"Hand joint chaser\" en MRTK"
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175359"
---
# <a name="hand-joint-chaser"></a>Buscada de juntas de mano

![Buscadores de manos En esta escena de ejemplo se muestra cómo usar ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) solver para adjuntar objetos a las uniones de la mano.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar la escena de ejemplo **HandJointChaserExample** en la `Assets/MRTK/Examples` carpeta en `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Controlador de solucionador

Haga **clic en Objeto al que se ha hecho seguimiento y** seleccione Hand Joint Left or Hand Joint Right (Conjunto de manos a la **izquierda** o a la derecha de **la mano).** Podrá ver la lista desplegable **Tracked Hand Joint (Unión de** mano con seguimiento). En la lista desplegable, puede seleccionar una unión específica de la que realizar el seguimiento. En esta escena de ejemplo se usa el solucionador de vistas radiales para hacer que un objeto siga el objeto de destino. Consulte [la página Solucionador](../ux-building-blocks/solvers/solver.md) para obtener más detalles.

![Solucionador de juntas de mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
