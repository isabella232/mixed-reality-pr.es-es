---
title: Manipulador de objetos
description: Uso del manipulador de objetos en MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, manipulación de objetos,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176652"
---
# <a name="object-manipulator"></a>Manipulador de objetos

![Manipulador de objetos](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator es el* nuevo componente para el comportamiento de manipulación, que se encontró anteriormente en *ManipulationHandler*. El manipulador de objetos realiza una serie de mejoras y simplificaciones. Este componente es un reemplazo del controlador de manipulación, que estará en desuso.

El script *ObjectManipulator* hace que un objeto sea móvil, escalable y rotable con una o dos manos. El manipulador de objetos se puede configurar para controlar cómo responderá el objeto a varias entradas. El script debe funcionar con la mayoría de las formas de interacción HoloLens 2, como una mano articulada, un HoloLens 2 de mano, una mirada y gestos de HoloLens y una entrada de controlador de movimiento de casco envolvente.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>Uso del manipulador de objetos

Para usar el manipulador de objetos, agregue primero el `ObjectManipulator` componente de script a un Objeto GameObject. Asegúrese de agregar también un colisionador al objeto, que coincida con sus límites que se pueden agarrar.

Para que el objeto responda a una entrada de mano casi articulada, agregue también `NearInteractionGrabbable` el script.

El comportamiento físico se puede habilitar para el manipulador de objetos agregando un componente rigidbody al objeto. El comportamiento físico habilitado mediante la adición de este componente se describe con más detalle en [*Física y colisiones.*](#physics-and-collisions)

Además de esto, la manipulación se puede restringir agregando componentes de [restricción de manipulación](constraint-manager.md#transform-constraints) al objeto . Se trata de componentes especiales que funcionan con la manipulación y cambian el comportamiento de la manipulación de alguna manera.

![Uso del controlador de manipulación en el editor de Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Propiedades y campos del inspector

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Propiedades generales

#### <a name="host-transform"></a>Transformación de host

Transformación de objeto que se va a manipular. El valor predeterminado es el objeto del componente.

#### <a name="manipulation-type"></a>Tipo de manipulación

Especifica si el objeto se puede manipular con una o dos manos. Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.

- *Con una mano:* habilita la manipulación con una mano si se selecciona.
- *Dos manos:* habilita la manipulación con dos manos si se selecciona.

#### <a name="allow-far-manipulation"></a>Permitir manipulación lejana

Especifica si se puede realizar la manipulación mediante la interacción lejana con punteros.

### <a name="one-handed-manipulation-properties"></a>Propiedades de manipulación con una mano

#### <a name="one-hand-rotation-mode-near"></a>Modo de rotación de una mano cerca

Especifica cómo se comportará el objeto cuando se esté capturando con una mano cerca. Estas opciones solo funcionan para las manos articuladas.

- *Girar sobre el centro de* objetos: el objeto gira mediante la rotación de la mano, pero sobre el punto central del objeto. Parecerá que el objeto se mueve menos a medida que gira, pero puede haber una sensación de desconexión entre la mano y el objeto. Más útil para la interacción lejana.
- *Girar sobre el punto de agarre:* gira el objeto con la mano sobre el punto de agarre entre el dedo índice y el dedo índice. Debería ser como si el objeto se hubiera mantenido con la mano.

#### <a name="one-hand-rotation-mode-far"></a>Modo de rotación de una mano lejos

Especifica cómo se comportará el objeto cuando se esté tomando con una mano a distancia. Estas opciones solo funcionan para las manos articuladas.

- *Girar sobre el centro de* objetos: gira el objeto mediante la rotación de la mano, pero sobre el punto central del objeto. Resulta útil para inspeccionar a una distancia sin que el centro de objetos se mueva a medida que el objeto gira.
- *Girar sobre el punto de agarre:* gira el objeto mediante la rotación de la mano, pero sobre el punto de impacto del rayo del puntero. Útil para la inspección.

### <a name="two-handed-manipulation-properties"></a>Dos propiedades de manipulación con manos

#### <a name="two-handed-manipulation-type"></a>Tipo de manipulación con dos manos

Especifica cómo la manipulación de dos manos puede transformar un objeto. Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.

- *Mover:* se permite el movimiento si se selecciona.
- *Escala:* se permite el escalado si se selecciona.
- *Girar:* se permite la rotación si se selecciona.

![Controlador de manipulación](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Restricciones

#### <a name="enable-constraints"></a>Habilitar restricciones

Esta configuración habilitará el administrador de [restricciones vinculadas.](constraint-manager.md) Los cambios de transformación se procesarán mediante restricciones registradas en el administrador [de restricciones seleccionado.](constraint-manager.md)

#### <a name="constraint-manager"></a>Administrador de restricciones

La lista desplegable permite seleccionar cualquiera de los administradores de [restricciones asociados.](constraint-manager.md) El manipulador de objetos garantiza que haya un administrador [de restricciones](constraint-manager.md) asociado en todo momento.
Tenga en cuenta que varios componentes del mismo tipo se mostrarán con el mismo nombre en Unity. Para facilitar la distinción entre varios administradores de restricciones en el mismo objeto, las opciones disponibles mostrarán una sugerencia sobre la configuración del administrador de restricciones seleccionado (selección manual o automática de restricciones).

#### <a name="go-to-component"></a>Ir al componente

La selección del administrador de restricciones incluye un *botón Ir al* componente. Este botón hará que el inspector se desplace al componente seleccionado para que se pueda configurar.

### <a name="physics"></a>Física

Configuración en esta sección solo aparecen cuando el objeto tiene un componente RigidBody.

#### <a name="release-behavior"></a>Comportamiento de la versión

Especifique las propiedades físicas que un objeto manipulado debe conservar al liberarse. Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.

- *Mantener velocidad:* cuando se libera el objeto, si se selecciona esta opción, mantendrá su velocidad lineal.
- *Mantener Angular velocidad:* cuando se libera el objeto, si se selecciona esta opción, mantendrá su velocidad angular.

#### <a name="use-forces-for-near-manipulation"></a>Uso de fuerzas para la manipulación próxima

Si se usan fuerzas físicas para mover el objeto al realizar manipulaciones cercanas. Si se establece en *false,* el objeto se verá más conectado directamente a la mano de los usuarios. Si se establece en *true,* se respetará la masa y la inercia del objeto, pero puede parecer que el objeto está conectado a través de un spring. El valor predeterminado es *false*.

### <a name="smoothing"></a>Suavizado

#### <a name="smoothing-far"></a>Suavizado lejos

Si el suavizado independiente de velocidad de fotogramas está habilitado para interacciones lejanas. El suavizado lejano está habilitado de forma predeterminada.

#### <a name="smoothing-near"></a>Suavizado cerca de

Si el suavizado independiente de velocidad de fotogramas está habilitado para interacciones cercanas. El suavizado casi está deshabilitado de forma predeterminada porque el efecto se puede percibir como "desconectado" de la mano.

#### <a name="smoothing-active"></a>Suavizado activo

Obsoleto y se quitará en una versión futura. Las aplicaciones deben usar SmoothingFar, SmoothingNear o una combinación de los dos.

#### <a name="move-lerp-time"></a>Mover el tiempo de lerp

Cantidad de suavizado que se aplicará al movimiento. Suavizado de 0 significa que no hay suavizado. El valor máximo significa que no hay ningún cambio en el valor.

#### <a name="rotate-lerp-time"></a>Rotación del tiempo de lerp

Cantidad de suavizado que se aplicará a la rotación. Suavizado de 0 significa que no hay suavizado. El valor máximo significa que no hay ningún cambio en el valor.

#### <a name="scale-lerp-time"></a>Escalado del tiempo de lerp

Cantidad de suavizado que se aplicará a la escala. Suavizado de 0 significa que no hay suavizado. El valor máximo significa que no hay ningún cambio en el valor.

### <a name="manipulation-events"></a>Eventos de manipulación

El controlador de manipulación proporciona los siguientes eventos:

- *OnManipulationStarted:* se desencadena cuando se inicia la manipulación.
- *OnManipulationEnded:* se ejecuta cuando finaliza la manipulación.
- *OnHoverStarted:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.
- *OnHoverEnded:* se activa cuando una mano o un controlador mantiene el puntero sobre el manipulable, cerca o lejos.

El orden de la manipulación de la manipulación del evento es:

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

Si no hay ninguna manipulación, seguirá teniendo eventos de mantener el puntero con el siguiente orden de incendio:

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Física y colisiones

El comportamiento físico se puede habilitar agregando un componente rigidbody al mismo objeto que un manipulador de objetos. Esto no solo habilita la configuración del comportamiento [de la versión](#release-behavior) anterior, sino que también permite colisiones. Sin un componente rigidbody, las colisiones no se comportan correctamente durante la manipulación:

- Las colisiones entre un objeto manipulado y un colisionador estático (es decir, un objeto con un colisionador pero no un elemento rígido) no funcionan, el objeto manipulado pasa directamente a través del colisionador estático sin que se ve afectado.
- Colisiones entre un objeto manipulado y un rígido (es decir, Un objeto con un colisionador y un elemento rigidbody) hace que el elemento rigidbody tenga una respuesta de colisión, pero la respuesta es rápida y no natural. Tampoco hay ninguna respuesta de colisión en el objeto manipulado.

Cuando se agrega un rigidbody, las colisiones deben funcionar correctamente.

### <a name="without-rigidbody"></a>Sin rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Con rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elásticos (experimentales)

Los elásticos se pueden usar al manipular objetos a través del manipulador de objetos. Tenga en cuenta que [el sistema elástico](../experimental/elastic-system.md) sigue en estado experimental. Para habilitar los elásticos, vincule un componente existente del administrador de elásticos o cree y vincule un nuevo administrador de elásticos mediante el `Add Elastics Manager` botón .

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Consulte también

- [Control Bounds](bounds-control.md)
- [Administrador de restricciones](constraint-manager.md)
- [El plazo de migración](../tools/migration-window.md)
- [Sistema elástico (experimental)](../experimental/elastic-system.md)
