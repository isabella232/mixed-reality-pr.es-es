---
title: Control de límites
description: Información general sobre el control de límites en MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, control de límites,
ms.openlocfilehash: 3abefd142753c34c9126d71cde77ebca0b40f1f9b7a81b5815777b9e938e172a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217224"
---
# <a name="bounds-control"></a>Control de límites

![Control de límites](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl es* el nuevo componente para el comportamiento de manipulación, que se encontró anteriormente *en BoundingBox.* El control De límites realiza una serie de mejoras y simplificaciones en la configuración y agrega nuevas características. Este componente es un reemplazo del cuadro de límite, que estará en desuso.

El [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script proporciona funcionalidad básica para transformar objetos en realidad mixta. Un control de límites mostrará un cuadro alrededor del holograma para indicar que se puede interactuar con él. Los identificadores de las esquinas y bordes del cuadro permiten escalar, girar o traducir el objeto. El control de límites también reacciona a la entrada del usuario. Por HoloLens 2, por ejemplo, el control de límites responde a la proximidad de los dedos, proporcionando comentarios visuales para ayudar a percibir la distancia desde el objeto. Todas las interacciones y objetos visuales se pueden personalizar fácilmente.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos de configuraciones de control de límites en la `BoundsControlExamples` escena.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Propiedades del inspector

### <a name="target-object"></a>Objeto de destino

Esta propiedad especifica qué objeto se transformará mediante la manipulación del control de límites. Si no se establece ningún objeto, el valor predeterminado es el objeto propietario.

### <a name="activation-behavior"></a>Comportamiento de activación

Hay varias opciones para activar la interfaz de control de límites.

* *Activar al iniciar:* el control Límites se vuelve visible una vez que se inicia la escena.
* *Activar por proximidad:* el control Límites se hace visible cuando una mano articulada está cerca del objeto.
* *Activar por puntero:* el control Límites se hace visible cuando está dirigido por un puntero de rayos de mano.
* *Activar por proximidad y* puntero: el control Límites se hace visible cuando está dirigido por un puntero de rayo de mano o una mano articulada está cerca del objeto.
* *Activar manualmente:* el control Límites no se hace visible automáticamente. Puede activarlo manualmente a través de un script accediendo a la propiedad boundsControl.Active.

### <a name="bounds-override"></a>Invalidación de límites

Establece un colisionador de cuadros del objeto para el cálculo de límites.

### <a name="box-padding"></a>Relleno de cuadro

Agrega un relleno a los límites del colisionador utilizados para calcular las extensiones del control. Esto influirá no solo en la interacción, sino que también afectará a los objetos visuales.

### <a name="flatten-axis"></a>Aplanar eje

Indica si el control se aplana en uno de los ejes, lo que lo hace 2 dimensiones y no permite la manipulación a lo largo de ese eje. Esta característica se puede usar para objetos finos como pizarras.
Si el eje de aplanar está establecido en *Aplanar* automáticamente, el script seleccionará automáticamente el eje con la extensión más pequeña como eje plano.

### <a name="smoothing"></a>Suavizado

La sección de suavizado permite configurar el comportamiento de suavizado para escalar y girar el control.

### <a name="visuals"></a>Objetos visuales

La apariencia del control de límites se puede configurar modificando una de las configuraciones de objetos visuales correspondientes.
Las configuraciones visuales son objetos vinculados o que pueden incluirse en scripts y se describen con más detalle en la sección [del objeto de configuración](#configuration-objects).

## <a name="configuration-objects"></a>Objetos de configuración

El control viene con un conjunto de objetos de configuración que se pueden almacenar como objetos que pueden incluirse en scripts y compartirse entre instancias o objetos prefabs diferentes. Las configuraciones se pueden compartir y vincular como archivos de recursos individuales que pueden incluirse en scripts o recursos con scripts anidados dentro de objetos prefab. También se pueden definir configuraciones adicionales directamente en la instancia sin vincular a un recurso externo o anidado que permite scripts.

El inspector de control de límites indicará si una configuración se comparte o se inlinea como parte de la instancia actual mostrando un mensaje en el inspector de propiedades. Además, las instancias compartidas no se podrán editar directamente en la propia ventana de propiedades de control de límites, sino que el recurso al que está vinculando debe modificarse directamente para evitar cambios accidentales en las configuraciones compartidas.

Actualmente, el control de límites ofrece opciones de objetos de configuración para las siguientes características:

* Asas
  * [Identificadores de escala](#scale-handles-configuration)
  * [Identificadores de rotación](#rotation-handles-configuration)
  * [Identificadores de traducción](#translation-handles-configuration)
* [Vínculos/Wireframe](#links-configuration-wireframe)
* [Presentación del cuadro](#box-configuration)
* [Efecto de proximidad](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configuración de Box

La configuración del cuadro es responsable de representar un cuadro sólido con límites definidos mediante el tamaño del colisionador y el relleno del cuadro. Se pueden configurar las siguientes propiedades:

* **Material de cuadro:** define el material aplicado al cuadro representado cuando no tiene lugar ninguna interacción. Solo se representará un cuadro si se establece este material.
* **Material de box grabbed:** material para la caja cuando el usuario interactúa con el control mediante la interacción cercana o lejana.
* **Escala de presentación del eje** aplanado: una escala que se aplica a la presentación del cuadro si uno de los ejes está [aplanado.](#flatten-axis)

### <a name="scale-handles-configuration"></a>Configuración de identificadores de escala

Este cajón de propiedades permite modificar el comportamiento y la visualización de los identificadores de escala del control de límites.

* **Material de identificador:** material aplicado a los identificadores.
* **Controle el material que se** ha tomado: material aplicado al manipulado.
* **Control de prefab:** prefab opcional para el identificador de escala. Si no se establece, MRTK usará un cubo como valor predeterminado.
* **Tamaño del identificador:** tamaño del identificador de escala.
* **Relleno del colisionador:** relleno que se agrega al colisionador del controlador.
* **Dibujar tether al manipular**: cuando está activo, dibujará una línea de tether desde el punto de inicio de la interacción a la posición actual de la mano o del puntero.
* **Los controladores omiten al colisionador:** si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.
* **Control del prefab de pizarra:** prefab que se va a usar para el identificador cuando se aplana el control.
* **Mostrar identificadores de escala:** controla la visibilidad del identificador.
* **Comportamiento de escala:** se puede establecer en escalado uniforme o no uniforme.

### <a name="rotation-handles-configuration"></a>Configuración de identificadores de rotación

Esta configuración define el comportamiento del identificador de rotación.

* **Material de identificador:** material aplicado a los identificadores.
* **Controle el material que se** ha tomado: material aplicado al manipulado.
* **Controlar prefab:** prefab opcional para el identificador. Si no se establece, MRTK usará una esfera como valor predeterminado.
* **Tamaño del identificador:** tamaño del identificador.
* **Relleno del colisionador:** relleno que se agrega al colisionador del controlador.
* **Dibujar tether al manipular**: cuando está activo, dibujará una línea de tether desde el punto de inicio de la interacción a la posición actual de la mano o del puntero.
* **Los controladores omiten al colisionador:** si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.
* **Controle el tipo de colisionador prefab:** tipo de colisionador que se usará con el identificador creado.
* **Mostrar identificador para X:** controla la visibilidad del identificador para el eje X.
* **Mostrar identificador para Y:** controla la visibilidad del identificador para el eje Y.
* **Mostrar identificador para Z:** controla la visibilidad del identificador para el eje Z.

### <a name="translation-handles-configuration"></a>Configuración de identificadores de traducción

Permite habilitar y configurar identificadores de traducción para el control de límites. Tenga en cuenta que los identificadores de traducción están deshabilitados de forma predeterminada.

* **Material de identificador:** material aplicado a los identificadores.
* **Controle el material que se** ha tomado: material aplicado al manipulado.
* **Controlar prefab:** prefab opcional para el identificador. Si no se establece, MRTK usará una esfera como valor predeterminado.
* **Tamaño del identificador:** tamaño del identificador.
* **Relleno del colisionador:** relleno que se agrega al colisionador del controlador.
* **Dibujar tether al manipular**: cuando está activo, dibujará una línea de tether desde el punto de inicio de la interacción a la posición actual de la mano o del puntero.
* **Los controladores omiten al colisionador:** si un colisionador se vincula aquí, los controladores omitirán cualquier colisión con este colisionador.
* **Controle el tipo de colisionador prefab:** tipo de colisionador que se usará con el identificador creado.
* **Mostrar identificador para X:** controla la visibilidad del identificador para el eje X.
* **Mostrar identificador para Y:** controla la visibilidad del identificador para el eje Y.
* **Mostrar identificador para Z:** controla la visibilidad del identificador para el eje Z.

### <a name="links-configuration-wireframe"></a>Configuración de vínculos (wireframe)

La configuración de vínculos habilita la característica wireframe del control de límites. Se pueden configurar las siguientes propiedades:

* **Material de wireframe:** el material aplicado a la malla de wireframe.
* **Radio del borde de wireframe:** grosor del wireframe.
* **Forma de wireframe:** la forma del wireframe puede ser cúbica o cilíndrica.
* **Mostrar wireframe:** controla la visibilidad del wireframe.

### <a name="proximity-effect-configuration"></a>Configuración del efecto de proximidad

Muestre y oculte los identificadores con animación en función de la distancia a las manos. Tiene animación de escalado en dos pasos. Los valores predeterminados se establecen en HoloLens 2 comportamiento de estilo.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Efecto de proximidad activo:** habilitación de la activación del identificador basado en proximidad
* **Proximidad media del objeto:** distancia para el escalado del primer paso
* **Proximidad de cierre de objeto:** distancia para el escalado del segundo paso
* **Escala lejana:** valor de escala predeterminado del recurso de identificador cuando las manos están fuera del intervalo de la interacción de control de límites (distancia definida anteriormente por "Controlar la proximidad media". Use 0 para ocultar el identificador de forma predeterminada)
* **Escala media:** valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción de control de límites (distancia definida anteriormente por "Handle Close Proximity". Use 1 para mostrar el tamaño normal)
* **Escala de** cierre: valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción de agarre (distancia definida anteriormente por "Proximidad de cierre del identificador". Usar 1.x para mostrar un tamaño mayor)
* **Frecuencia de crecimiento lejano:** la velocidad de un objeto escalado de proximidad se escala cuando la mano se mueve de proximidad media a lejana.
* **Velocidad de crecimiento medio:** la velocidad de escala de un objeto escalado de proximidad se escala cuando la mano se mueve de proximidad media a cercana.
* **Cerrar velocidad de crecimiento:** la velocidad de escala de un objeto con escala de proximidad se escala cuando la mano se mueve desde la proximidad al centro de objetos.

## <a name="constraint-system"></a>Sistema de restricciones

El control de límites admite el uso del [administrador de restricciones](constraint-manager.md) para limitar o modificar el comportamiento de traducción, rotación o escalado mientras se usan identificadores de control de límites.

El inspector de propiedades mostrará todos los administradores de restricciones disponibles asociados al mismo objeto de juego en una lista desplegable con una opción para desplazarse y resaltar el administrador de restricciones seleccionado.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Eventos

El control Bounds proporciona los siguientes eventos. En este ejemplo se usan estos eventos para reproducir comentarios de audio.

* **Girar iniciado:** se desencadena cuando se inicia la rotación.
* **Girar detenido:** se desencadena cuando se detiene la rotación.
* **Escalado iniciado:** se inicia cuando se inicia el escalado.
* **Escala detenida:** se produce cuando se detiene el escalado.
* **Translate Started**: se inicia cuando se inicia la traducción.
* **Translate Stopped**: se desaso cuando se detiene la traducción.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elásticos (experimentales)

Los elásticos se pueden usar al manipular objetos a través del control de límites. Tenga en cuenta que [el sistema elástico](../experimental/elastic-system.md) sigue en estado experimental. Para habilitar los elásticos, vincule un componente existente del administrador de elásticos o cree y vincule un nuevo administrador de elásticos mediante el `Add Elastics Manager` botón .

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Controlar estilos

De forma predeterminada, al asignar el script, se mostrará el identificador del HoloLens [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) de primera generación. Para usar HoloLens 2 identificadores de estilo, debe asignar prefabs y materiales de identificador adecuados.

![Estilos de identificador de control de límites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

A continuación se muestran los requisitos previos, los materiales y los valores de escalado para los HoloLens 2 de control de límites de estilo. Puede encontrar este ejemplo en la `BoundsControlExamples` escena.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>Identificadores (configuración para HoloLens 2 estilo)

* **Material de identificador:** BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat
* **Prefab del identificador de** escala: MRTK_BoundingBox_ScaleHandle.prefab
* **Prefab de pizarra del** controlador de escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Tamaño del identificador de** escala: 0,016 (1,6 cm)
* **Relleno del colisionador del** controlador de escala: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)
* **Prefab del identificador** de rotación: MRTK_BoundingBox_RotateHandle.prefab
* **Tamaño del identificador de** rotación: 0,016
* **Relleno del colisionador del** controlador de rotación: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)

## <a name="transformation-changes-with-object-manipulator"></a>Cambios de transformación con el manipulador de objetos

Se puede usar un control de límites en combinación con para permitir determinados [`ObjectManipulator.cs`](object-manipulator.md) tipos de manipulación (por ejemplo, mover el objeto) sin usar identificadores. El controlador de manipulación admite interacciones de una y dos manos. [El seguimiento](../input/hand-tracking.md) manual se puede usar para interactuar con un objeto de cerca.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Para que los bordes de control de límites se comporten de la misma manera al moverlo mediante la interacción lejana, se recomienda conectar sus eventos para On Manipulation Started On Manipulation Ended (Manipulación iniciada al finalizar), respectivamente, como se muestra en la captura de pantalla [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` anterior.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Adición y configuración de un control de límites mediante Unity Inspector

1. Adición de Box Collider a un objeto
2. Asignación `BoundsControl` de script a un objeto
3. Configuración de opciones, como los métodos de activación (consulte la [sección Propiedades del inspector](#inspector-properties) a continuación)
4. (Opcional) Asignación de prefabs y materiales para un control de límites HoloLens 2 estilo (consulte la sección Estilos [de](#handle-styles) identificador a continuación)

> [!NOTE]
> Use *el objeto de* destino y el campo Invalidación de *límites* en el inspector para asignar un objeto y colisionador específicos en el objeto con varios componentes secundarios.

![Control de límites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Cómo agregar y configurar un control de límites en el código

1. Creación de instancias de GameObject de cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Asignación `BoundsControl` de script a un objeto con colisionador mediante AddComponent<>()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configure opciones directamente en el control o a través de una de las configuraciones que se pueden incluir en scripts (consulte la [sección Propiedades](#inspector-properties) y [configuraciones del](#configuration-objects) inspector a continuación).

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (Opcional) Asigne prefabs y materiales para un control HoloLens 2 límites de estilo. Esto todavía requiere asignaciones a través del inspector, ya que los materiales y los objetos prefab deben cargarse dinámicamente.

> [!NOTE]
> No se recomienda usar la carpeta "Resources" de Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para cargar de forma dinámica sombreadores, ya que es posible que falte permutaciones del sombreador en tiempo de ejecución.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Ejemplo: Establecer la escala de control de límites mínimo y máximo mediante MinMaxScaleConstraint

Para establecer la escala mínima y máxima, adjunte un al [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) control . A medida que el control de límites asocia y activa automáticamente el administrador de restricciones, MinMaxScaleConstraint se aplicará automáticamente a los cambios de transformación una vez asociado y configurado.

También puede usar MinMaxScaleConstraint para establecer la escala mínima y máxima para [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Ejemplo: Agregar control de límites alrededor de un objeto de juego

Para agregar un control de límites alrededor de un objeto, basta con agregarle `BoundsControl` un componente:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migración desde el rectángulo de selección

Las instancias y los requisitos previos existentes que usan el [](../tools/migration-window.md) cuadro de límite se pueden actualizar al nuevo control de límites a través de la ventana de migración que forma parte del paquete de herramientas de MRTK. [](bounding-box.md)

Para actualizar instancias individuales del rectángulo de selección, también hay una opción de migración dentro del inspector de propiedades del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Consulte también

* [Manipulador de objetos](object-manipulator.md)
* [Administrador de restricciones](constraint-manager.md)
* [El plazo de migración](../tools/migration-window.md)
* [Sistema elástico (experimental)](../experimental/elastic-system.md)
