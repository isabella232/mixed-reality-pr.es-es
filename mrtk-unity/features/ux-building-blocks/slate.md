---
title: Claqueta
description: Documentación sobre Slate en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Slate,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224029"
---
# <a name="slate"></a>Claqueta

![Claqueta](../images/slate/MRTK_Slate_Main.png)

El objeto prefab Slate ofrece un control de estilo de ventana fino para mostrar contenido 2D, por ejemplo, texto sin formato o artículos que incluyen elementos multimedia. Ofrece una barra de título que se puede agarrar, así *como la funcionalidad Seguirme* *y* Cerrar. La ventana de contenido se puede desplazar a través de una entrada de mano articulada.

## <a name="how-to-use-a-slate-control"></a>Uso de un control de pizarra

Un control de pizarra se compone de los siguientes elementos:

* **TitleBar:** barra de título completa en la parte superior de la pizarra.
* **Título:** área de título en el lado izquierdo de la barra de título.
* **Botones:** área de botón en el lado derecho de la barra de título.
* **BackPlate:** el lado posterior de la pizarra.
* **ContentQuad:** el contenido se asigna como material. En el ejemplo se usa un material de ejemplo "PanContent".

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Control de límites

Un control de pizarra contiene un script de control de límites para el escalado y la rotación. Para obtener más información sobre el control de límites, consulte la página [de control de límites.](bounds-control.md)

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Botones

Una pizarra estándar ofrece dos botones de forma predeterminada en la parte superior derecha de la barra de título:

* **Sígueme:** alterna los componentes de un solucionador orbital para que el objeto de pizarra siga al usuario.
* **Cerrar:** deshabilita el objeto de pizarra.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>Scripts

En general, el script debe adjuntarse a cualquier objeto que esté diseñado `NearInteractionTouchable.cs` para recibir eventos táctiles de `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs`Este script controla la entrada de mano articulada para tocar y mover el contenido en *contentquad de la pizarra.*

* `HandInteractionPanZoom.cs`: además de la interacción de movimiento panorámico, este script admite el zoom con dos manos.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
