---
title: Introducción al solucionador
description: Información general de los solucionadores en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, solucionadores
ms.openlocfilehash: bf9bbfe578ace576fca8870f038f145037a6838d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176456"
---
# <a name="solver-overview"></a>Introducción al solucionador

![Principal del solucionador](../../images/solver/MRTK_Solver_Main.png)

Los solucionadores son componentes que facilitan los medios para calcular la posición y la orientación de un objeto según un algoritmo predefinido. Un ejemplo puede ser la colocación de un objeto en la superficie donde golpea actualmente el raycast de la mirada del usuario.

Además, el sistema de solucionadores define de manera determinista un orden de operaciones para estos cálculos de transformación, ya que no hay ninguna manera confiable de especificar a Unity el orden de actualización de los componentes.

Los solucionadores ofrecen una variedad de comportamientos para adjuntar objetos a otros objetos o sistemas. Otro ejemplo sería un objeto con etiquetas continuas que mantiene el puntero delante del usuario (en función de la cámara). También se puede adjuntar un solucionador a un controlador y un objeto para que el objeto etiquete el controlador de manera continua. Todos los solucionadores se pueden apilar de manera segura, por ejemplo, un comportamiento de etiquetas continuas + magnetismo de superficie + impulso.

## <a name="how-to-use-a-solver"></a>Procedimiento para usar un solucionador

El sistema de solucionadores consta de tres categorías de scripts:

* [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver): Clase abstracta base de la que derivan todos los solucionadores. Ofrece seguimiento del estado, parámetros de suavizado e implementación, integración automática del sistema de solucionadores y orden de actualización.
* [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler): Establece el objeto de referencia con el que se realiza el seguimiento (por ejemplo, la transformación de la cámara principal, el haz de mano, etc.), controla la recopilación de componentes de los solucionadores y ejecuta la actualización en el orden correcto.

La tercera categoría es el solucionador mismo. Los siguientes solucionadores brindan los bloques de creación para el comportamiento básico:

* [`Orbital`](#orbital): Se bloquea en una posición y desplazamiento especificados con respecto al objeto referenciado.
* [`ConstantViewSize`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.ConstantViewSize): Escala para mantener un tamaño constante con respecto a la vista del objeto referenciado.
* [`RadialView`](#radialview): Mantiene el objeto dentro de una proyección cónica de vista por el objeto referenciado.
* [`Follow`](#follow): Mantiene el objeto dentro de un conjunto de límites del objeto referenciado definidos por el usuario.
* [`InBetween`](#inbetween): Mantiene un objeto entre dos objetos a los que se hace un seguimiento.
* [`SurfaceMagnetism`](#surfacemagnetism): Proyecta rayos en las superficies del mundo y alinea el objeto con esa superficie.
* [`DirectionalIndicator`](#directionalindicator): Establece la posición y la orientación de un objeto como indicador direccional. Desde el punto de la referencia del destino de seguimiento de SolverHandler, este indicador se orientará hacia el directionalTarget señalado.
* [`Momentum`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Momentum): Aplica aceleración, velocidad o fricción para simular el impulso y la elasticidad de un objeto que es movido por otros solucionadores o componentes.
* [`HandConstraint`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Restringe el objeto para que siga las manos en una región que no interseca GameObject con las manos. Resulta útil para contenido interactivo restringido a mano, como menús, etc. Este solucionador está pensado para funcionar con [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand), pero también funciona con [IMixedRealityController](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController).
* [`HandConstraintPalmUp`](#hand-menu-with-handconstraint-and-handconstraintpalmup): Proviene de HandConstraint, pero incluye lógica para probar si la palma está orientada hacia el usuario antes de la activación. Este solucionador solo funciona con controladores [IMixedRealityHand](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand); con otros tipos de controlador, este solucionador se comportará igual que su clase base.

Para usar el sistema de solucionadores, simplemente agregue uno de los componentes enumerados anteriormente a un GameObject. Dado que todos los solucionadores requieren una clase [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), Unity creará una automáticamente.

> [!NOTE]
> Puede encontrar ejemplos de cómo usar el sistema de solucionadores en el archivo **SolverExamples.scene**.

## <a name="how-to-change-tracking-reference"></a>Procedimiento para cambiar la referencia de seguimiento

La propiedad *Tracked Target Type* del componente [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) define el punto de referencia que todos los solucionadores usarán para calcular sus algoritmos. Por ejemplo, un tipo de valor de [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head) con un componente [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) simple dará como resultado un raycast desde la cabeza y en la dirección de la mirada del usuario para resolver qué superficie alcanza. Los valores potenciales para la propiedad `TrackedTargetType` son:

* *Head*: El punto de referencia es la transformación de la cámara principal.
* *ControllerRay*: El punto de referencia es la transformación [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer) en un controlador (es decir, el origen del puntero en un controlador de movimiento o controlador de mano) que apunta en la dirección del rayo de línea.
  * Use la propiedad `TrackedHandedness` para seleccionar la preferencia de diestro o zurdo (es decir, izquierda, derecha, ambas).
* *HandJoint*: El punto de referencia es la transformación de una articulación específica de la mano.
  * Use la propiedad `TrackedHandedness` para seleccionar la preferencia de diestro o zurdo (es decir, izquierda, derecha, ambas).
  * Use la propiedad `TrackedHandJoint` para determinar la transformación de la articulación que se usará.
* *CustomOverride*: Punto de referencia de la `TransformOverride` asignada.

> [!NOTE]
> Para los tipos *ControllerRay* y *HandJoint*, el controlador del solucionador intentará proporcionar primero la transformación de mano/controlador izquierdo y, luego, la derecha si la primera no está disponible o a menos que la propiedad `TrackedHandedness` especifique lo contrario.

![Objeto con seguimiento del solucionador](../../images/solver/TrackedObjectType-Example.gif) 
*Ejemplo de varias propiedades asociadas a cada TrackedTargetType*

> [!IMPORTANT]
> La mayoría de los solucionadores usan el vector hacia delante del destino de transformación con seguimiento proporcionado por `SolverHandler`. Cuando se usa un tipo de destino con seguimiento de *HandJoint*, el vector hacia delante de la articulación de la mano puede apuntar a través de los dedos y no a través de la palma. Esto depende de la plataforma que suministra los datos de la articulación de la mano. En el caso de la simulación de entrada y Windows Mixed Reality, es el *vector ascendente* el que apunta hacia arriba a través de la palma (es decir, el vector verde está hacia arriba, el vector azul hacia delante).
>
> ![Vector ascendente hacia delante](../../images/solver/HandJoint_ForwardUpVectors.png)
>
> Para solucionar este problema, actualice la propiedad *Additional Rotation* (Rotación adicional) en `SolverHandler` a **<90, 0, 0>** . Esto garantizará que el vector hacia delante proporcionado a los solucionadores apunte a través de la palma y alejándose de la mano.
>
> ![Rotación adicional](../../images/solver/SolverHandler_AdditionalRotation.png)
>
> Como alternativa, use el tipo de destino con seguimiento *Controller Ray* (Rayo del controlador) para obtener un comportamiento similar para apuntar con las manos.

## <a name="how-to-chain-solvers"></a>Procedimiento para encadenar solucionadores

Es posible agregar varios componentes `Solver` al mismo GameObject, con lo que sus algoritmos se encadenan. El componente `SolverHandler` controla la actualización de todos los solucionadores en el mismo GameObject. De manera predeterminada, `SolverHandler` llama a `GetComponents<Solver>()` en el inicio, lo que devolverá los solucionadores en el orden en que aparecen en el inspector.

Además, al establecer la propiedad *Updated Linked Transform* (Transformación vinculada actualizada) en true (verdadero), se indicará que `Solver` guarde su posición, orientación y escala calculadas en una variable intermedia a la que puedan acceder todos los solucionadores (es decir, `GoalPosition`). Cuando se establece en false (falso), `Solver` actualizará la transformación de GameObject directamente. Al guardar las propiedades de la transformación en una ubicación intermediaria, otros solucionadores pueden realizar sus cálculos a partir de la variable intermediaria. Esto se debe a que Unity no permite que las actualizaciones de gameObject.transform se apilen dentro del mismo fotograma.

> [!NOTE]
> Para modificar el orden de ejecución de los solucionadores, los desarrolladores pueden establecer la propiedad `SolverHandler.Solvers` directamente.

## <a name="how-to-create-a-new-solver"></a>Procedimiento para crear un nuevo solucionador

Todos los solucionadores deben heredar de la clase base abstracta, [`Solver`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Solver). Los requisitos principales de una extensión de solucionador implican invalidar el método `SolverUpdate`. En este método, los desarrolladores deben actualizar las propiedades `GoalPosition`, `GoalRotation` y `GoalScale` heredadas a los valores deseados. Además, suele ser útil aprovechar `SolverHandler.TransformTarget` como fotograma de referencia deseado por el consumidor.

El código que se brinda a continuación ofrece un ejemplo de un nuevo componente de solucionador denominado `InFront` que coloca el objeto adjunto 2 m delante de `SolverHandler.TransformTarget`. Si el consumidor establece el valor de `SolverHandler.TrackedTargetType` como [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), `SolverHandler.TransformTarget` será la transformación de la cámara y, por tanto, este solucionador colocará el GameObject adjunto 2 m delante de la mirada de los usuarios en cada fotograma.

```c#
/// <summary>
/// InFront solver positions an object 2m in front of the tracked transform target
/// </summary>
public class InFront : Solver
{
    ...

    public override void SolverUpdate()
    {
        if (SolverHandler != null && SolverHandler.TransformTarget != null)
        {
            var target = SolverHandler.TransformTarget;
            GoalPosition = target.position + target.forward * 2.0f;
        }
    }
}
```

## <a name="solver-implementation-guides"></a>Guías de implementación de solucionadores

### <a name="common-solver-properties"></a>Propiedades comunes de los solucionadores

Cada componente del solucionador tiene un conjunto básico de propiedades idénticas que controlan el comportamiento principal del solucionador.

Si *Smoothing* está habilitado, el solucionador actualizará gradualmente la transformación de GameObject con el tiempo a los valores calculados. La velocidad de este cambio viene determinada por la propiedad *LerpTime* de cada componente de transformación. Por ejemplo, un valor *MoveLerpTime* mayor generará incrementos más lentos en el movimiento entre fotogramas.

Si *MaintainScale* está habilitado, el solucionador usará la escala local predeterminada del GameObject.

![Propiedades básicas de los solucionadores](../../images/solver/GeneralSolverProperties.png)  
*Propiedades comunes heredadas por todos los componentes de los solucionadores*

### <a name="orbital"></a>Orbital

La clase [`Orbital`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Orbital) es un componente de etiquetas continuas que se comporta como los planetas en un sistema solar. Este solucionador garantizará que los GameObject adjuntos orbiten alrededor de la transformación a la que se hace el seguimiento. Por lo tanto, si *Tracked Target Type* (Tipo de destino con seguimiento) de [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) está establecido en [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), el GameObject orbitará alrededor de la cabeza del usuario con la aplicación de un desplazamiento fijo.

Los desarrolladores pueden modificar este desplazamiento fijo para mantener los menús u otros componentes de la escena en el nivel ocular o de la cintura, etc., en torno a un usuario. Para ello, modifique las propiedades *Local Offset* (Desplazamiento local) y *World Offset* (Desplazamiento del mundo). La propiedad *Orientation Type* (Tipo de orientación) determina la rotación que se aplica al objeto si debe mantener su rotación original, o estar siempre frente a la cámara o frente a cualquier transformación que impulse su posición, etc.

![Ejemplo de Orbital](../../images/solver/OrbitalExample.png)  
*Ejemplo de Orbital*

### <a name="radialview"></a>RadialView

[`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) es otro componente de etiquetas continuas que mantiene una parte determinada de un GameObject dentro del tronco de la vista del usuario.

Las propiedades *Min/Max View Degrees* (Mín. y Máx. de grados de visión) determinan el tamaño de una parte del GameObject que siempre debe estar a la vista.

Las propiedades *Min/Max View Degrees* (Mín. y Máx. de grados de visión) determinan hasta qué punto se debe mantener alejado el GameObject del usuario. Por ejemplo, si se avanza hacia el GameObject con *Min Distance* (Distancia mínima) de 1 m, el GameObject se alejará para asegurarse de que nunca esté a menos de 1 m del usuario.

Por lo general, [`RadialView`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.RadialView) se usa junto con *Tracked Target Type* (Tipo de destino con seguimiento) establecido en [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head), de modo que el componente siga la mirada del usuario. Sin embargo, este componente puede funcionar para mantenerse en la *"vista"* de cualquier *Tracked Target Type* (Tipo de destino con seguimiento).

![Ejemplo de RadialView](../../images/solver/RadialViewExample.png)  
*Ejemplo de RadialView*

### <a name="follow"></a>Seguir

La clase [`Follow`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.Follow) coloca un elemento delante del destino al que se hace el seguimiento en relación con su eje de avance local. El elemento se puede restringir de forma flexible (también conocido como, etiqueta continua o tag-along) para que no siga hasta que el destino con seguimiento supere los límites definidos por el usuario.

Funciona de forma similar al solucionador RadialView, con controles adicionales para administrar *Max Horizontal/Vertical View Degrees* (Máx. de grados de visión horizontal y vertical), y mecanismos para modificar *Orientation* (Orientación) del objeto.

![Propiedades de Follow](../../images/solver/FollowExample.png)  
*Propiedades de Follow*

![Escena de ejemplo de Follow](../../images/solver/FollowExampleScene.gif)  
*Escena de ejemplo de Follow (Assets/MRTK/Examples/Demos/Solvers/Scenes/FollowSolverExample.unity)*

### <a name="inbetween"></a>InBetween

La clase [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) mantendrá el GameObject adjunto entre dos transformaciones. Estos dos puntos de transformación se definen mediante *Tracked Target Type* (Tipo de destino con seguimiento) del propio [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) del GameObject, y la propiedad *Second Tracked Target Type* (Segundo tipo de destino con seguimiento) del componente [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween). Por lo general, ambos tipos se establecerán en [`CustomOverride`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.CustomOverride), y los valores `SolverHandler.TransformOverride` y `InBetween.SecondTransformOverride` resultantes se establecerán en los dos puntos con seguimiento.

En tiempo de ejecución, el componente [`InBetween`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.InBetween) creará otro componente [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) según las propiedades *Second Tracked Target Type* (Segundo tipo de destino con seguimiento) y *Second Transform Override* (Segunda invalidación de transformación).

`PartwayOffset` define dónde, a lo largo de la línea entre dos transformaciones, se colocará el objeto; donde 0,5 es la mitad, 1,0 en la primera transformación, y 0,0 en la segunda transformación.

![Ejemplo de InBetween](../../images/solver/InBetweenExample.png)  
*Ejemplo de uso del solucionador InBetween para mantener el objeto entre dos transformaciones*

### <a name="surfacemagnetism"></a>SurfaceMagnetism

[`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) funciona mediante la aplicación de un raycast frente a un LayerMask establecido de superficies y colocando el GameObject en ese punto de contacto.

*Surface Normal Offset* (Desplazamiento normal de la superficie) colocará el GameObject a una distancia establecida en metros de distancia de la superficie en la dirección de la normal en el punto de impacto en la superficie.

Por el contrario, *Surface Ray Offset* (Desplazamiento del rayo en la superficie) colocará el Objeto GameObject a una distancia establecida en metros de la superficie, pero en la dirección opuesta del raycast aplicado. Por lo tanto, si el raycast es la mirada del usuario, el GameObject se acercará a lo largo de la línea desde el punto de impacto en la superficie hasta la cámara.

*Orientation Mode* (Modo de orientación) determina el tipo de rotación que se aplicará en relación con la normal en la superficie.

* *None*: No se aplica ninguna rotación.
* *TrackedTarget*: El objeto se enfrentará a la transformación con seguimiento que controla el raycast.
* *SurfaceNormal*: El objeto se alineará en función de la normal en el punto de impacto en la superficie.
* *Blended*: El objeto se alineará en función de la normal en el punto de impacto en la superficie, y en función de la orientación de la transformación con seguimiento.

Para forzar que el Objeto GameObject asociado permanezca vertical en cualquier modo distinto de *None*, habilite *Keep Orientation Vertical* (Mantener orientación vertical).

> [!NOTE]
> Use la propiedad *Orientation Blend* (Combinación de orientación) para controlar el equilibrio entre los factores de rotación *Orientation Mode* (Modo de orientación) está establecido en *Blended*. Con un valor de 0,0, la orientación se controlará completamente con el modo *TrackedTarget*; y con un valor de 1,0, la orientación se controlará completamente con *SurfaceNormal*.

![Ejemplo de SurfaceMagnetism](../../images/solver/SurfaceMagExample.png)

#### <a name="determining-what-surfaces-can-be-hit"></a>Establecimiento de qué superficies se pueden impactar

Al agregar un componente [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) a un GameObject, es importante tener en cuenta la capa del GameObject y sus elementos secundarios, si alguno tiene colisionadores. El componente funciona mediante la aplicación de varios tipos de raycasts para determinar con qué superficie se va a "imantar". Si el GameObject del solucionador tiene un colisionador en una de las capas enumeradas en la propiedad `MagneticSurfaces` de `SurfaceMagnetism`, es probable que el raycast se alcance a sí mismo, lo que dará lugar a que el GameObject se adjunte a su propio punto de colisión. Para evitar este comportamiento extraño, se puede establecer el GameObject principal y todos los elementos secundarios en la capa *Ignore Raycast* (Omitir raycast) o modificar correctamente la matriz LayerMask de `MagneticSurfaces`.

Por el contrario, un GameObject de [`SurfaceMagnetism`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SurfaceMagnetism) no colisionará con las superficies de una capa que no aparezca en la propiedad `MagneticSurfaces`. Por lo general, se recomienda colocar todas las superficies deseadas en una capa dedicada (es decir, *Surfaces*) y establecer la propiedad `MagneticSurfaces` solo en esta capa.  El uso de *default* o *everything* puede dar lugar a que los componentes de la interfaz de usuario o los cursores contribuyan al solucionador.

Por último, los raycasts de `SurfaceMagnetism` omitirán las superficies más alejadas de la configuración de la propiedad `MaxRaycastDistance`.

### <a name="directionalindicator"></a>DirectionalIndicator

La clase [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) es un componente de etiquetas continuas que se orienta a sí mismo a la dirección de un punto deseado en el espacio.

Se usa normalmente cuando *Tracked Target Type* (Tipo de destino con seguimiento) de [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler) se establece en [`Head`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedObjectType.Head). De este modo, un componente de la experiencia de usuario con el solucionador [`DirectionalIndicator`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.DirectionalIndicator) dirigirá a un usuario a que mire el punto deseado en el espacio.

El punto deseado en el espacio se determina a través de la propiedad *Directional Target* (Destino direccional).

Si el usuario puede ver el destino direccional, o cualquier fotograma de referencia se establece en [`SolverHandler`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.SolverHandler), este solucionador deshabilitará todos los componentes [`Renderer`](https://docs.unity3d.com/ScriptReference/Renderer.html) debajo de él. Si no se puede ver, todo se habilitará en el indicador.

El tamaño del indicador se reducirá cuanto más se acerque el usuario a capturar el valor de *Directional Target* (Destino direccional) en su campo de visión.

* *Min Indicator Scale* (Escala mínima del indicador): Escala mínima para el objeto indicador.
* *Max Indicator Scale* (Escala máxima del indicador): Escala máxima para el objeto indicador.

* *Visibility Scale Factor* (Factor de escala de visibilidad): Multiplicador para aumentar o disminuir el campo de visión que determina si el punto *Directional Target* (Destino direccional) se puede ver o no.
* *View Offset* (Desplazamiento de vista): Desde el punto de vista del fotograma de referencia (es decir, la camera posiblemente), esta propiedad define hasta qué punto en la dirección del indicador debe estar el objeto desde el centro de la ventanilla.

![Propiedades de DirectionalIndicator](../../images/solver/DirectionalIndicatorExample.png)  
*Propiedades de DirectionalIndicator*

![Escena de ejemplo de DirectionalIndicator](../../images/solver/DirectionalIndicatorExampleScene.gif)  
*Escena de ejemplo de DirectionalIndicator (Assets/MRTK/Examples/Demos/Solvers/Scenes/DirectionalIndicatorSolverExample.unity)*

### <a name="hand-menu-with-handconstraint-and-handconstraintpalmup"></a>Menú Mano con HandConstraint y HandConstraintPalmUp

![Ejemplo de experiencia de usuario del menú Mano](../../images/solver/MRTK_UX_HandMenu.png)

El comportamiento de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) proporciona un solucionador que restringe el objeto con seguimiento a una región segura para el contenido restringido a la mano (como la interfaz de usuario de la mano, los menús, etc.). Las regiones seguras se consideran áreas que no se intersecan con la mano. También se incluye una clase derivada de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) llamada [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) para mostrar un comportamiento común de activar el objeto con seguimiento del solucionador cuando la palma mira hacia el usuario.

[Consulte la página Menú Mano](../hand-menu.md) para ver los ejemplos de uso del solucionador HandConstraint para crear menús de mano.

## <a name="see-also"></a>Vea también

* [Seguimiento de manos](../../input/hand-tracking.md)
* [Gaze](../../input/gaze.md)
