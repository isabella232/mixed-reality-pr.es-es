---
title: Administrador de restricciones
description: Información general sobre el Administrador de restricciones en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177556"
---
# <a name="constraint-manager"></a>Administrador de restricciones

El administrador de restricciones permite aplicar un conjunto de componentes de restricción a una transformación. Se pueden tener en cuenta los componentes de tipo asociados al objeto [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) de juego.
De forma predeterminada, el administrador de restricciones recopilará automáticamente todos los componentes [de](#transform-constraints) restricción asociados al objeto de juego y los aplicará a las transformaciones procesadas.
Sin embargo, los usuarios pueden optar por configurar la lista de restricciones aplicadas manualmente y permitir que solo se aplique un subconjunto de restricciones asociadas.

Actualmente, los siguientes elementos de la experiencia de usuario de MRTK admiten el administrador de restricciones:

- [Control Bounds](bounds-control.md)
- [Manipulador de objetos](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Propiedades y campos del inspector

El administrador de restricciones se puede operar en dos modos:

- Selección de restricciones automáticas
- Selección manual de restricciones

### <a name="auto-constraint-selection"></a>Selección de restricciones automáticas

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

El modo predeterminado del administrador de restricciones, selección automática de restricciones, proporcionará una lista de todos los componentes de restricción asociados, así como botones y un [botón agregar restricción](#add-constraint-to-game-object). [](#go-to-component)

#### <a name="add-constraint-to-game-object"></a>Agregar restricción al objeto de juego

Este botón permite agregar un componente de restricción directamente desde el inspector del administrador de restricciones. Todos los tipos de restricción de un proyecto deben estar visibles aquí. Consulte [Restricciones de transformación](#transform-constraints) para obtener más información.

#### <a name="go-to-component"></a>Ir al componente

Todas las restricciones que se encuentran en el objeto se mostrarán aquí con un botón *Ir* al componente. Este botón hará que el inspector se desplace hasta el componente de restricción seleccionado para que se pueda configurar.

### <a name="manual-constraint-selection"></a>Selección manual de restricciones

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Si el administrador de restricciones se establece en modo manual, solo las restricciones vinculadas en la lista de restricciones se procesan y se aplican a la transformación. La lista mostrada solo mostrará las restricciones [](#go-to-component) seleccionadas por el usuario, así como los botones u opciones para quitar o agregar entradas.
Al habilitar el modo manual por primera vez, el administrador de restricciones rellenará la lista con todos los componentes disponibles como punto de partida para seleccionar los componentes de restricción asociados.

### <a name="remove-entry"></a>Quitar entrada

Esto quita la entrada de la lista seleccionada manualmente. Tenga en cuenta que esta opción no quitará el componente de restricción del objeto de juego. Los componentes de restricción siempre deben quitarse manualmente para asegurarse de que no se rompe accidentalmente ningún otro componente que hace referencia a este componente.

### <a name="add-entry"></a>Agregar entrada

Agregar entrada abrirá una lista desplegable que muestra todos los componentes de restricción disponibles que aún no están en la lista manual. Al hacer clic en cualquiera de las entradas que el componente agregará a la selección de restricción manual.

### <a name="add-new-constraint"></a>Agregar nueva restricción

Esta opción agregará un componente del tipo seleccionado al objeto de juego y agregará el componente de restricción recién creado a la lista de restricciones manual.

## <a name="transform-constraints"></a>Restricciones de transformación

Las restricciones se pueden usar para limitar la manipulación de alguna manera. Por ejemplo, algunas aplicaciones pueden requerir rotación, pero también requieren que el objeto permanezca vertical. En este caso, se puede agregar un objeto al objeto y usarse para limitar la rotación a `RotationAxisConstraint` la rotación del eje Y. MRTK proporciona una serie de restricciones, todas las cuales se describen a continuación.

También es posible definir nuevas restricciones y usarlas para crear un comportamiento de manipulación único que pueda ser necesario para algunas aplicaciones. Para ello, cree un script que herede de [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implemente la propiedad `ConstraintType` abstracta y el método `ApplyConstraint` abstracto. Al agregar una nueva restricción al objeto , debe restringir la manipulación de la manera que se definió. Esta nueva restricción también debe mostrarse en la lista desplegable de selección [automática](#auto-constraint-selection) del administrador de restricciones o agregar [entrada](#add-entry) en modo manual.

Todas las restricciones proporcionadas por MRTK comparten las siguientes propiedades:

#### <a name="hand-type"></a>Tipo de mano

Especifica si la restricción se usa para una mano, dos manos o ambos tipos de manipulación. Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.

- *Con una mano:* la restricción se usará durante la manipulación con una mano si se selecciona.
- *Dos manos:* la restricción se usará durante la manipulación con dos manos si se selecciona.

#### <a name="proximity-type"></a>Tipo de proximidad

Especifica si la restricción se usa para los tipos de manipulación cercanos, lejanos o ambos. Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.

- *Near*: la restricción se usará durante la manipulación próxima si se selecciona.
- *Far:* la restricción se usará durante la manipulación lejana si se selecciona.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Cuando esta restricción se adjunta a un objeto, la rotación se limitará para que el objeto siempre se enfrentará al usuario. Esto es útil para pizarras o paneles. Las propiedades de `FaceUserConstraint` son las siguientes:

#### <a name="face-away"></a>Distancia de la cara

El objeto se enfrenta al usuario si es true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Esta restricción corrige la distancia entre el objeto manipulado y otra transformación de objeto al iniciar la manipulación. Esto es útil para comportamientos como corregir la distancia desde el objeto manipulado a la transformación principal. Las propiedades de `FixedDistanceConstraint` son las siguientes:

#### <a name="constraint-transform"></a>Transformación de restricciones

Esta es la otra transformación a la que el objeto manipulado tendrá una distancia fija. El valor predeterminado es la transformación de la cámara.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Esta restricción corrige la rotación relativa entre el usuario y el objeto manipulado mientras se manipula. Esto es útil para pizarras o paneles, ya que garantiza que el objeto manipulado siempre muestra la misma cara al usuario que al principio de la manipulación. no `FixedRotationToUserConstraint` tiene ninguna propiedad única.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Esta restricción corrige la rotación global del objeto manipulado mientras se manipula. Esto puede ser útil en casos en los que no se debe realizar ninguna rotación mediante la manipulación. no `FixedRotationToWorldConstraint` tiene ninguna propiedad única:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Cuando esta restricción se adjunta a un objeto, independientemente de lo lejos que esté el objeto del usuario, mantendrá el mismo tamaño aparente para el usuario (es decir, ocupará la misma proporción del campo de vista del usuario). Esto se puede usar para asegurarse de que una pizarra o un panel de texto permanece legible durante la manipulación. no `MaintainApparentSizeConstraint` tiene ninguna propiedad única:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Esta restricción se puede usar para corregir los ejes en los que se puede mover un objeto manipulado. Esto puede ser útil para manipular objetos sobre la superficie de un plano o a lo largo de una línea. Las propiedades de `MoveAxisConstraint` son las siguientes:

#### <a name="constraint-on-movement"></a>Restricción del movimiento

Especifica los ejes en los que se va a evitar el movimiento. De forma predeterminada, estos ejes serán globales en lugar de locales, pero esto se puede cambiar a continuación. Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.

- *Eje X:* el movimiento a lo largo del eje X está restringido si se selecciona.
- *Eje Y:* el movimiento a lo largo del eje Y está restringido si se selecciona.
- *Eje Z:* el movimiento a lo largo del eje Z está restringido si se selecciona.

#### <a name="use-local-space-for-constraint"></a>Uso del espacio local para la restricción

Restringirá los ejes de transformación local del objeto manipulado si es true. El valor predeterminado es false.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Esta restricción se puede usar para corregir los ejes sobre los que se puede girar un objeto manipulado. Esto puede ser útil para mantener un objeto manipulado verticalmente, pero seguir permitiendo rotaciones del eje Y, por ejemplo. Las propiedades de `RotationAxisConstraint` son las siguientes:

#### <a name="constraint-on-rotation"></a>Restricción en la rotación

Especifica los ejes sobre los que se va a evitar la rotación. De forma predeterminada, estos ejes serán globales en lugar de locales, pero esto se puede cambiar a continuación. Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.

- *Eje Y:* la rotación sobre el eje Y está restringida si se selecciona.
- *Eje Z:* la rotación sobre el eje Z está restringida si se selecciona.
- *Eje X:* la rotación sobre el eje X está restringida si se selecciona.

#### <a name="use-local-space-for-constraint"></a>Uso del espacio local para la restricción

Restringirá los ejes de transformación local del objeto manipulado si es true. El valor predeterminado es false.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Esta restricción permite establecer valores mínimos y máximos para la escala del objeto manipulado. Esto es útil para evitar que los usuarios e escalar un objeto demasiado pequeño o demasiado grande. Las propiedades de `MinMaxScaleConstraint` son las siguientes:

#### <a name="scale-minimum"></a>Escala mínima

Valor de escala mínimo durante la manipulación.

#### <a name="scale-maximum"></a>Escalado máximo

Valor de escala máximo durante la manipulación.

#### <a name="relative-to-initial-state"></a>En relación con el estado inicial

Si es true, los valores anteriores se interpretarán como relativos a la escala inicial de los objetos. De lo contrario, se interpretarán como valores de escala absolutos.
