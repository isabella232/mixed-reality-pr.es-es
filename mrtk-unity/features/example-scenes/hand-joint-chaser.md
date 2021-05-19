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
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="151b9-104">Ejemplo de "hand joint chaser"</span><span class="sxs-lookup"><span data-stu-id="151b9-104">Hand joint chaser example</span></span>

<span data-ttu-id="151b9-105">![Buscadores de manos En esta escena de ejemplo se muestra cómo usar ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) solver para adjuntar objetos a las uniones de la mano.</span><span class="sxs-lookup"><span data-stu-id="151b9-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="151b9-106">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="151b9-106">Example scene</span></span>

<span data-ttu-id="151b9-107">Puede encontrar la escena de ejemplo **HandJointChaserExample** en la `Assets/MRTK/Examples` carpeta en `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="151b9-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="151b9-108">Controlador de solucionador</span><span class="sxs-lookup"><span data-stu-id="151b9-108">Solver handler</span></span>

<span data-ttu-id="151b9-109">Haga **clic en Objeto al que se ha hecho seguimiento y** seleccione Hand Joint Left or Hand Joint Right (Conjunto de manos a la **izquierda** o a la derecha de **la mano).**</span><span class="sxs-lookup"><span data-stu-id="151b9-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="151b9-110">Podrá ver la lista desplegable **Tracked Hand Joint (Unión de** mano con seguimiento).</span><span class="sxs-lookup"><span data-stu-id="151b9-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="151b9-111">En la lista desplegable, puede seleccionar una unión específica de la que realizar el seguimiento. En esta escena de ejemplo se usa el solucionador de vistas radiales para hacer que un objeto siga el objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="151b9-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="151b9-112">Consulte [la página Solucionador](../ux-building-blocks/solvers/solver.md) para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="151b9-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Solucionador de juntas de mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
