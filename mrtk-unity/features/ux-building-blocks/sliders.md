---
title: Control deslizante
description: Información general de MRTK de controles deslizantes
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controles deslizantes,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426881"
---
# <a name="sliders"></a>Controles deslizantes

![Ejemplo de control deslizante](../images/slider/MRTK_UX_Slider_Main.jpg)

Los controles deslizantes son componentes de la interfaz de usuario que permiten cambiar continuamente un valor moviendo un control deslizante en una pista. Actualmente, el control deslizante Desenlazador se puede mover agarrándose directamente al control deslizante, ya sea directamente o a una distancia. Los controles deslizantes funcionan en AR y VR, mediante controladores de movimiento, manos o Gesto + voz.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos en la escena **SliderExample** en `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Uso de controles deslizantes

Arrastre y coloque el prefab **PinchSlider** en la jerarquía de escena. Si desea modificar o crear su propio control deslizante, recuerde hacer lo siguiente:

- Asegúrese de que el objeto de control tiene un colisionador. En el prefab de PinchSlider, el colisionador está en `SliderThumb/Button_AnimationContainer/Slider_Button`
- Asegúrese de que el objeto que contiene el colisionador también tiene un componente Near Interaction Grabbable (Interacción cercana que se puede capturar) si desea poder acercar el control deslizante.

También se recomienda usar la siguiente jerarquía

- PinchSlider: contiene el control deslizanteComponent.
  - TouchCollider: colisionador que contiene todo el área seleccionable del control deslizante. Habilita el comportamiento Ajustar a posición.
  - SliderThumb: contiene el control de posición móvil
  - TrackVisuals: contiene la pista y cualquier otro objeto visual.
  - OtherVisuals: que contiene cualquier otro objeto visual

## <a name="slider-events"></a>Eventos de control deslizante

Los controles deslizantes exponen los siguientes eventos:

- OnValueUpdated: se llama cada vez que cambia el valor del control deslizante.
- OnInteractionStarted: se llama cuando el usuario toma el control deslizante.
- OnInteractionEnded: se llama cuando el usuario suelta el control deslizante.
- OnHoverEntered: se llama cuando la mano o el controlador del usuario mantiene el puntero sobre el control deslizante, mediante una interacción cercana o lejana.
- OnHoverExited: se llama cuando la mano o el controlador del usuario ya no está cerca del control deslizante.

## <a name="configuring-slider-bound-and-axis"></a>Configuración del límite del control deslizante y el eje

Puede mover directamente los puntos inicial y final del control deslizante moviendo los identificadores de la escena:

![Configuración de controles deslizantes](../images/sliders/MRTK_Sliders_Setup.png)

También puede especificar el eje (en el espacio local) del control deslizante a través del _campo Eje deslizante._

Si no puede usar los identificadores, en su lugar puede especificar los puntos inicial y final del control deslizante a través de los campos _Slider Start Distance_ (Distancia de inicio del control deslizante) y Slider End Distance _(Distancia final del_ control deslizante). Estos especifican la posición inicial y final del control deslizante como una distancia desde el centro del control deslizante, en coordenadas locales. Esto significa que, una vez establecidas las distancias de inicio y finalización del control deslizante como quiera, puede escalar el control deslizante para que sea menor o mayor sin necesidad de actualizar las distancias inicial y final.

## <a name="inspector-properties"></a>Propiedades del inspector

**Raíz de thumb** Objeto gameobject que contiene el control deslizante.

**Ajustar a la posición** Si este control deslizante se ajusta o no a la posición designada en el control deslizante

**Es táctil** Si este control deslizante se puede controlar o no a través de eventos táctiles

**Colisionador de thumb** Colisionador que controla el control deslizante

**Colisionador táctil** Área del control deslizante que se puede tocar o seleccionar cuando Ajustar a la posición es true.

**Valor del control deslizante** Valor del control deslizante.

**Usar divisiones de pasos de control deslizante** Controla si este control deslizante se incrementa en pasos o continuamente.

**Divisiones de pasos de control deslizante** Número de subdivisiones en las que se divide el control deslizante cuando se habilita Usar divisiones de pasos deslizantes.

**Seguimiento de objetos visuales** Objeto gameobject que contiene los objetos visuales de seguimiento deseados que van a lo largo del control deslizante.

**Marcas de graduación** Objeto gameobject que contiene las marcas de graduación deseadas que van a lo largo del control deslizante.

**Objetos visuales thumb** El objeto gameobject que contiene el objeto visual de posición deseado que va a lo largo del control deslizante.

**Eje deslizante** Eje a lo largo del que se mueve el control deslizante.

**Distancia de inicio del control deslizante** Donde se inicia la pista del control deslizante, como distancia desde el centro a lo largo del eje deslizante, en unidades de espacio local.

**Distancia final del control deslizante** Donde finaliza la pista del control deslizante, como distancia desde el centro a lo largo del eje deslizante, en unidades de espacio local.

Cuando el usuario actualiza el valor del eje deslizante en el editor, si se especifica Track Visuals o Tick Visuals, se actualiza su transformación.
En concreto, se restablece su posición local y su rotación local se establece para que coincida con la orientación del eje deslizante.
Su escala no se modifica.
Si las marcas de graduación tienen un componente Colección de objetos de cuadrícula, layout y CellWidth o CellHeight se actualizan en consecuencia para que coincidan con el eje deslizante.

## <a name="example-slider-configurations"></a>Configuraciones de control deslizante de ejemplo

Controles deslizantes continuos con controles deslizantes continuos ajustar ![ a la posición](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Controles deslizantes de paso con ajustar a la posición

![Controles deslizantes de pasos](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Controles deslizantes táctiles

![Controles deslizantes táctiles](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)