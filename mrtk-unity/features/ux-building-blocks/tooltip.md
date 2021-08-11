---
title: Información sobre herramientas
description: Información general sobre la información sobre herramientas en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, información sobre herramientas,
ms.openlocfilehash: af848db0962948b1f2ada73066c4ae90730b09a99dea231ebf468a05441b85ef
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193262"
---
# <a name="tooltip"></a>Información sobre herramientas

![Información sobre herramientas principal](../images/tooltip/MRTK_Tooltip_Main.png)

La información sobre herramientas se usa normalmente para transmitir una sugerencia o información adicional tras una inspección más detallada de un objeto. La información sobre herramientas se puede usar para anotar objetos en el entorno físico.

## <a name="how-to-use-a-tooltip"></a>Uso de una información sobre herramientas

Se puede agregar información sobre herramientas directamente a la jerarquía y tener como destino un objeto .

Para usar este método, basta con agregar un objeto de juego y uno de los elementos prefabs de información sobre herramientas (Assets/MRTK/SDK/Features/UX/Prefabs/Tooltips) a la jerarquía de escena. En el panel del inspector del prefab, expanda el [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script. Seleccione un estado de propina y configure la información sobre herramientas.  Escriba el texto correspondiente para la información sobre herramientas en el campo de texto. Expanda el script y arrastre el objeto que va a tener la información sobre herramientas de la jerarquía al [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) campo con la etiqueta *Target*. Esto asocia la información sobre herramientas al objeto .
![Conector de información sobre herramientas](../images/tooltip/MRTK_Tooltip_Connector.png)

Este uso supone una información sobre herramientas que siempre se muestra o que se muestra u oculta mediante script cambiando la propiedad de estado de la información sobre herramientas del componente de información sobre herramientas.

## <a name="dynamically-spawning-tooltips"></a>Generación dinámica de información sobre herramientas

Una información sobre herramientas se puede agregar dinámicamente a un objeto en tiempo de ejecución, así como establecer previamente para mostrar y ocultar en una pulsación o el foco. Simplemente agregue el [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script a cualquier objeto de juego. Los retrasos por aparecer y desaparecer se pueden establecer en el inspector de scripts, así como una duración, para que la información sobre herramientas desaparezca después de una duración establecida. La información sobre herramientas también ofrece propiedades de estilo, como objetos visuales de fondo en el script de generación. De forma predeterminada, la información sobre herramientas se anclará al objeto con el script de generación. Esto se puede cambiar mediante la asignación de un Elemento GameObject al campo delimitador.

## <a name="example-scene"></a>Escena de ejemplo

En las escenas de ejemplo (Assets/MRTK/Examples/Demos/UX/Tooltips/Scenes), podrá encontrar varios ejemplos de información sobre herramientas.

![Ejemplos de información sobre herramientas](../images/tooltip/MRTK_Tooltip_Examples.png)
