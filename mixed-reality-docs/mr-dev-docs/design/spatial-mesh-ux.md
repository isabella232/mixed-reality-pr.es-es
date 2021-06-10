---
title: Visualización de malla espacial
description: Obtenga información sobre las directrices de diseño y la comprensión del entorno físico con la visualización de malla espacial en MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Mixed Reality, HoloLens, controles de interfaz de usuario, interacción, ui, ux, UX Design, spatial UI, spatial interaction, 3D UI, 3D UX, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600634"
---
# <a name="spatial-mesh"></a>Malla espacial

![Malla espacial](images/MRTK_PulseShader_SpatialMesh.gif)

Los usuarios aprenden cómo un dispositivo percibe y entiende el entorno físico a través de la visualización de malla espacial. La visualización adecuada de la malla espacial puede crear una experiencia atractiva y mágica a la vez que proporciona contexto espacial.  

## <a name="design-guideline"></a>Guía de diseño

Es importante permitir que el usuario se centre e interactúe con el contenido. La visualización continua de la malla espacial en segundo plano puede distraer. Se recomienda visualizar el entorno con moderación, ya sea solo una vez en el lanzamiento inicial o cuando el usuario muestre claramente que quiere ver la malla ambiental mediante el destino y el espacio de pulsación en el aire. Puede observar este comportamiento en el Portal de realidad mixta.
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a>Visualización de malla espacial en MRTK (Mixed Reality Toolkit) para Unity

MRTK proporciona varios materiales para la visualización de malla espacial.

- **MRTK_Wireframe.mat, MRTK_Wireframe.mat:** material de malla espacial estático predeterminado, que muestra los contornos de la malla sin animación. Este material es útil para la depuración, ya que muestra todas las geometrías de la malla espacial. Sin embargo, no se recomienda para producción.
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- **MRTK_SurfaceReconstruction.mat:** este material proporciona un efecto de pulso animado en la malla espacial. Puede usar este material para visualizar el entorno en un momento específico o en la entrada de pulsación en el aire del usuario. Consulte **la escena pulseShaderExamples.unity** para ver los ejemplos.
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* Para obtener más información, [vea MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) y [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).

<br>

---

## <a name="see-also"></a>Vea también

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