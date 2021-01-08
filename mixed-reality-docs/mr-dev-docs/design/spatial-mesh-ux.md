---
title: Visualización de malla espacial
description: Obtenga información sobre las directrices de diseño y la comprensión del entorno físico con la visualización de malla espacial en MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realidad mixta, HoloLens, controles de IU, interacción, IU, experiencia de usuario, diseño de la experiencia del usuario, interfaz de usuario espacial, interacción espacial, interfaz de usuario 3D, experiencia en 3D, auriculares
ms.openlocfilehash: 0f9cdc218c6fe54b8892c39a6a76f023e203d334
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009925"
---
# <a name="spatial-mesh"></a>Malla espacial

![Malla espacial](images/MRTK_PulseShader_SpatialMesh.gif)

Los usuarios aprenden cómo un dispositivo percibe y comprenden el entorno físico a través de la visualización de malla espacial. La visualización correcta de la malla espacial puede crear una experiencia agradables y mágica a la vez que proporciona un contexto espacial.  

## <a name="design-guideline"></a>Directrices de diseño

Es importante permitir que el usuario se Centre e interactúe con el contenido. La visualización continua de la malla espacial en segundo plano puede distraerse. Se recomienda visualizar el entorno de forma moderada, ya sea una sola vez en el inicio inicial o cuando el usuario muestra claramente que quieren ver la malla del entorno mediante el destino y el espacio de punteo aéreo. Puede observar este comportamiento en el portal de realidad mixta.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualización de malla espacial en MRTK (kit de herramientas de realidad mixta) para Unity

MRTK proporciona varios materiales para la visualización de la malla espacial.

- **MRTK_Wireframe. MAT, MRTK_Wireframe. MAT**: material de malla espacial estático predeterminado, que muestra los contornos de la malla sin animación. Este material es útil para la depuración, ya que muestra todas las geometrías espaciales de la malla. Sin embargo, no se recomienda para la producción.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction. MAT**: este material proporciona un efecto de pulso animado en la malla espacial. Puede usar este material para visualizar el entorno en un momento específico o en la entrada de punteo de aire del usuario. Consulte **PulseShaderExamples. Unity** Scene para ver los ejemplos.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* Para obtener más información, consulte [MRTK-Spatial awareing](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) y [MRTK-Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html).

<br>

---

## <a name="see-also"></a>Consulte también

* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Botón](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulación](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Cerca](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Información sobre herramientas](tooltip.md)
* [Claqueta](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
