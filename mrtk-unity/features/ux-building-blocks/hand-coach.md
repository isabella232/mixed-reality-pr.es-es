---
title: Asesor manual
description: descripción y ejemplos de Hand coach.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 3e5a56f7498288e79963acea6fca223421fee2607004a9a2bae639f81441e0d9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209034"
---
# <a name="hand-coach"></a>Asesor manual

![Menú del seleccionador de mano](../images/hand-coach/MRTK_UX_HandCoach_Main.jpg)

El carro de la mano es una mano modelada en 3D que se desencadena cuando el sistema no detecta las manos del usuario. Esto se implementa como un componente de "enseñanza" que ayuda a guiar al usuario cuando no se ha aprendido el gesto. Si los usuarios no han realizado el gesto especificado durante un período, las manos se pondrán en bucle con un retraso. El carro de la mano se puede usar para representar la pulsación de un botón o la selección de un holograma.

El modelo de interacción actual representa una amplia variedad de controles de gestos, como desplazamiento, selección lejana y pulsación cercana. A continuación se muestra una lista completa de ejemplos de seleccionador de mano existentes:

- Pulsar cerca: se usa para botones o cerrar objetos interactuables.
- Selección lejana: se usa para objetos que están lejos
- Mover: se usa para mover un holograma en el espacio
- Girar: se usa para mostrar cómo girar hologramas u objetos
- Escala: se usa para mostrar cómo manipular hologramas para que sean más grandes o más pequeños.
- Volteo con la mano: se usa para abrir un panel de inicio de la interfaz de usuario o menús de mano
- Pie arriba: se usa para disfrutar de un momento en el que se usa de forma personalizada. Otra sugerencia podría ser abrir un panel de inicio de la interfaz de usuario.
- Scroll: se usa para desplazar una lista o un documento largo

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos en la escena **HandCoachExample** en: [MixedRealityToolkit.Examples/Experimental/HandCoach/Scenes](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach/Scenes)

## <a name="hand-3d-assets"></a>Recursos 3D de mano

Puede encontrar los recursos en: [MixedRealityToolkit.SDK/Experimental/HandCoach](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/HandCoach)

## <a name="quality"></a>Calidad

Si observa distorsión en la malla de máscara, debe asegurarse de que el proyecto usa la cantidad adecuada de uniones.
Vaya a Edit (Editar) de Unity > Project Configuración > Quality > Other > Blend Weights (Otros pesos > Blend). Asegúrese de que se seleccionan "4 esqueletos" para ver las uniones suavizadas.
![Project Ajuste](../images/hand-coach/MRTK_ProjectSettings.png)

## <a name="scripts"></a>Scripts

### <a name="interaction-hint"></a>Sugerencia de interacción

El `InteractionHint.cs` script proporciona funcionalidad de contenedor para desencadenar animaciones y atenuaciones para el equipo de mano.

#### <a name="how-to-set-up-an-interaction-hint"></a>Configuración de una sugerencia de interacción

Para configurar una sugerencia de interacción, se recomienda usar los requisitos previos proporcionados "StaticHandCoachRoot_L.prefab" y "StaticHandCoachRoot_R.prefab". Este objeto prefab contiene el script InteractionHint y el equipo de mano, así como la jerarquía adecuada para garantizar que las animaciones de sugerencias proporcionadas funcionan según lo previsto.
De lo contrario, deberá colocar el script en un gameObject un nivel primario desde el equipo de mano con el animador.

#### <a name="inspector-properties"></a>Propiedades del inspector

- **HideIfHandTracked** Este booleano especifica si se debe usar el estado de seguimiento de las manos para ocultar objetos visuales cuando se realiza un seguimiento de las manos de un usuario. Si se establece en false, solo se usará la propiedad de scripting "customShouldHideVisuals" para determinar si se debe ocultar la sugerencia.

- **MinDelay** Esta propiedad especifica el retraso mínimo para mostrar los objetos visuales. De forma predeterminada, los objetos visuales de la mano aparecerán después de estos muchos segundos si no se realiza el seguimiento de las manos del usuario.

- **MaxDelay** Esta propiedad especifica el retraso máximo para mostrar los objetos visuales. De forma predeterminada, los objetos visuales de la mano aparecerán después de estos muchos segundos, incluso si se realiza un seguimiento de las manos del usuario.

- **UseMaxTimer** Si este valor booleano se establece en false, deshabilita el temporizador máximo y solo permite mostrar la sugerencia de mano cuando las manos del usuario están fuera de la vista o la condición personalizada devuelve false.

- **Repeticiones** Esta propiedad controla cuántas veces se reproduce la animación de sugerencias cuando ha pasado el temporizador mínimo o máximo. A continuación, la sugerencia se oculta y espera de nuevo el retraso.

- **Autoactivate** Cuando este valor booleano se establece en true, la sugerencia se ejecutará automáticamente a través de la lógica del temporizador cuando el Elemento GameObject del script esté activo en la jerarquía y el script esté habilitado. Esto solo debe establecerse en false si tiene previsto controlar manualmente la apariencia de la sugerencia y la insondimiento a través del código.

- **AnimationState** Nombre del estado de animación que debe reproducirse cuando la sugerencia está activa. Debe establecerse antes de llamar a la función StartHintLoop() (durante OnEnable si se activa AutoActivate).

#### <a name="controlling-interactionhint-via-script"></a>Controlar InteractionHint mediante script

- **StartHintLoop** Esta función inicia el bucle show/hide que, de lo contrario, inicia OnEnable si la marca AutoActivate está establecida en true.
- **StopHintLoop** Esta función llama al estado de animación de atenuación si no se está reproduciendo actualmente, desactivará el bucle show/hide y establecerá el mano a mano inactivo en la jerarquía.
- **AnimationState** Esta cadena determina qué estado de animación se reproduce durante el bucle. Puede cambiar esta cadena para cambiar qué estado se reproduce, pero debe hacerlo después de llamar a StopHintLoop y debe volver a llamar a StartHintLoop después de haber cambiado el estado.
- **CustomShouldHideVisuals** Puede establecer esto con su propia función, que debe devolver true cuando desee ocultar los objetos visuales de la mano (tenga en cuenta MinMaxTimer, específicamente el parámetro max).

#### <a name="custom-animation-considerations"></a>Consideraciones sobre animaciones personalizadas

El valor predeterminado de los atenuados es 0,5 segundos, por lo que las animaciones personalizadas creadas para su uso con la plataforma deben ser de 1,5 segundos como mínimo para que se transmita cualquier información significativa.

Los estados de atenuación y atenuación predeterminados proporcionados, Fade_In y Fade_Out se pueden ajustar cambiando la marca de tiempo del segundo fotograma clave para establecer la longitud de atenuación.

El animador y el script se configuraron de forma que la configuración fuera lo más sencilla posible. Para agregar nuevos estados de animación, simplemente importe el fbx, asegúrese de que el nombre de la animación está establecido con un nombre distinto y arrastre esa animación al animador.

### <a name="movetotarget"></a>MoveToTarget

El script MoveToTarget.cs proporciona funcionalidad para mover la sugerencia de mano de una posición de seguimiento a una posición de destino a lo largo del tiempo.

#### <a name="how-to-set-up-movetotarget"></a>Configuración de MoveToTarget

Los elementos prefabs "MovingHandCoachRoot_L.prefab" y "MovingHandCoachRoot_R.prefab" proporcionados contienen un objeto MoveToTarget en sus jerarquías. Si desea usar este script en su propia configuración, debe colocarlo en el objeto gameobject raíz que contiene animator para el equipo.

#### <a name="inspector-properties"></a>Propiedades del inspector

- **TrackingObject** Establezca esta opción con el objeto que desea que siga el equipo antes de iniciar su movimiento. Se recomienda crear un GameObject vacío y moverlo a una posición específica para ayudarle a identificar el seguimiento.
- **TargetObject** Establezca esta opción con el objeto al que desea que se mueva el equipo durante su movimiento. Se recomienda crear un GameObject vacío y moverlo a una posición específica para ayudarle a identificar el seguimiento.
- **RootObject** Establezca esta opción en un elemento primario compartido entre el seguimiento y el objeto de destino para que las posiciones relativas se puedan calcular correctamente. El objeto prefab incluido tiene objetos de seguimiento y de destino en su jerarquía, pero puede establecer el objeto de destino como gameObject fuera del objeto prefab y cambiar el objeto raíz a un elemento primario compartido.
- **Duración** Cantidad de tiempo que se debe tardar (en segundos) en pasar de TrackingObject a TargetObject en segundos.
- **TargetOffset** Desplazamiento ajustable para que GameObject llegue a la posición de destino correcta. Esto resulta útil si la animación incluye un desplazamiento de posición durante la animación.
- **AnimationCurve** El valor predeterminado es una curva lineal, pero puede modificarla para proporcionar una aceleración de entrada y salida al iniciar y detener la ruta de movimiento.

#### <a name="controlling-movetotarget-via-script"></a>Control de MoveToTarget mediante script

En el script personalizado, realice una llamada a Follow() mientras quiere que el dispositivo de mano siga el objeto TrackingObject y, a continuación, realice una llamada a MoveToTargetPosition() cuando desee que el dispositivo de mano comience su movimiento al Objeto Target.

#### <a name="controlling-movetotarget-via-animations"></a>Control de MoveToTarget mediante animaciones

En la animación que debe moverse, establezca dos eventos: uno con una llamada a Follow() y otro con una llamada a MoveToTargetPosition(). Follow debe establecerse en el primer fotograma clave, ya que hace que el dispositivo de mano siga el objeto TrackingObject. MoveToTargetPosition debe establecerse en el fotograma clave donde desea que el equipo empiece a moverse al destino. Así es como se usa la funcionalidad de script en los requisitos previos proporcionados.

### <a name="rotatearoundpoint"></a>RotateAroundPoint

El script RotateAroundPoint.cs proporciona funcionalidad para girar la sugerencia de mano alrededor de un punto de pivote a lo largo del tiempo.

#### <a name="how-to-set-up-rotatearoundpoint"></a>Configuración de RotateAroundPoint

Los elementos prefabs "RotatingHandCoachRoot_L.prefab" y "RotatingHandCoachRoot_R.prefab" proporcionados contienen rotateAroundPoint en sus jerarquías. Si desea usar este script en su propia configuración, debe colocarlo en el objeto gameobject raíz que contiene animator para el equipo.

#### <a name="inspector-properties"></a>Propiedades del inspector

- **CenteredParent** Establezca esta opción con el objeto primario en el que desea que el equipo pivote.
- **InverseParent** Establezca esta opción con el elemento primario para girar inversamente a centeredParent con el fin de mantener la orientación de la mano igual. En general, este será el objeto primario con el script InteractionHint en él.
- **PivotPosition** Establezca esta opción en un punto en el que desee que la sugerencia empiece a movement.
- **Duración** Cantidad de tiempo que se debe tardar (en segundos) en girar alrededor de CenteredParent.
- **AnimationCurve** El valor predeterminado es una curva lineal, pero puede modificarla para proporcionar una aceleración de entrada y salida al iniciar y detener la ruta de movimiento.
- **RotationVector** Cuántos grados se giran a lo largo de cada eje.

#### <a name="controlling-rotatearoundpoint-via-script"></a>Controlar RotateAroundPoint mediante script

En el script personalizado, realice una llamada a RotateToTarget() cuando desee que el ala de mano comience su rotación alrededor de CenteredParent. Si desea que la posición se restablezca a la pivotPosition original, realice una llamada a ResetAndDeterminePivot().

#### <a name="controlling-rotatearoundpoint-via-animations"></a>Controlar RotateAroundPoint mediante animaciones

En la animación que debe moverse, establezca dos eventos: uno con una llamada a ResetAndDeterminePivot() y otro con una llamada a RotateToTarget(). ResetAndDeterminePivot debe establecerse en el primer fotograma clave, ya que hace que el dispositivo de mano se restablezca a pivotPosition. RotateToTarget debe establecerse en el fotograma clave donde desea que el apareado comience a girar alrededor del elemento CenteredParent. Así es como se usa la funcionalidad de script en los requisitos previos proporcionados.
