---
title: Menú Cerca
description: Introducción a los tipos de menús cercanos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, menú cercano,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175656"
---
# <a name="near-menu"></a>Menú Cerca

![Menú Cerca](../images/near-menu/MRTK_UX_NearMenu.png)

Near Menu es un control de experiencia de usuario que proporciona una colección de botones u otros componentes de la interfaz de usuario. Está flotante alrededor del cuerpo del usuario y es fácilmente accesible en cualquier momento. Dado que se acopla de forma flexible con el usuario, no afecta a la interacción del usuario con el contenido de destino. El usuario puede usar el botón "Anclar" para bloquear o desbloquear el menú. El menú se puede agarrar y colocar en una posición específica.

## <a name="interaction-behavior"></a>Comportamiento de interacción

- **Etiqueta: el** menú le sigue y permanece dentro del intervalo de 30-60 cm desde el usuario para las interacciones cercanas.
- **Anclar:** con el botón "Anclar", el menú se puede bloquear y liberar.
- **Agarrar y mover:** el menú siempre se puede agarrar y mover. Independientemente del estado anterior, el menú se anclará (bloqueado por el mundo) cuando se agarrá y se liberará. Hay indicaciones visuales para el área que se puede agarrar. Se revelan por proximidad.

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a>Requisitos previos

Los elementos prefabs de menú cercano están diseñados para mostrar cómo usar los distintos componentes de MRTK para crear menús para interacciones cercanas.

- **NearMenu2x4.prefab**
- **NearMenu3x1.prefab**
- **NearMenu3x2.prefab**
- **NearMenu3x3.prefab**
- **NearMenu4x1.prefab**
- **NearMenu4x2.prefab**

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos de elementos prefabs de menú cercano en la `NearMenuExamples` escena.

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a>Estructura

Los elementos prefabs del menú cercano se realizan con los siguientes componentes de MRTK.

- [**Prefab PressableButtonHoloLens2**](button.md)
- [**Colección de objetos grid:**](object-collection.md)diseño de varios botones en la cuadrícula
- [**Controlador de manipulación:**](manipulation-handler.md)agarrar y mover el menú
- [**Solucionador radialView:**](solvers/solver.md)seguir el comportamiento de me (etiqueta)

![Menú cercano prefab](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a>Cómo realizar la personalización

**1. Agregar o quitar botones**

En `ButtonCollection` objeto , agregue o quite botones.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

**2. Actualización de la colección de objetos Grid**

Haga `Update Collection` clic en el botón del inspector del `ButtonCollection` objeto. Actualizará el diseño de la cuadrícula.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

Puede configurar el número de filas mediante la `Rows` propiedad de la colección de objetos Grid.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

**3. Ajuste del tamaño de la placa trasera**

Ajuste el tamaño del objeto `Quad` `Backplate` debajo de . El ancho y alto de la placa trasera deben ser `0.032 * [Number of the buttons + 1]` . Por ejemplo, si tiene 3 x 2 botones, el ancho de la placa trasera es `0.032 * 4` y el alto es `0.032 * 3` . Puede colocar directamente esta expresión en el campo de Unity.  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- El tamaño predeterminado del botón HoloLens 2 es 3,2 x 3,2 cm (0,032 m)

## <a name="see-also"></a>Consulte también

- [**Botones**](button.md)
- [**Control de límites**](bounds-control.md)
- [**Slider**](sliders.md)
- [**Colección de objetos Grid**](object-collection.md)
- [**Controlador de manipulación**](manipulation-handler.md)
- [**RadialView Solver**](solvers/solver.md)
