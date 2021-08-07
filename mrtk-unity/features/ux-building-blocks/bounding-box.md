---
title: Rectángulo de selección
description: Información general sobre Bounding Box en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Bounding Box
ms.openlocfilehash: fa1ace9d7aaf547ee677accfc4254ce9c64aebdfa6a01f11962812b058bc9ceb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214253"
---
# <a name="bounding-box"></a>Rectángulo de selección

![Rectángulo de selección](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> El rectángulo de selección está en desuso y se reemplaza por su control de [límites sucesor.](bounds-control.md) Use [una de las opciones de migración para](#migrating-to-bounds-control) actualizar los objetos de juego existentes.

El [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script proporciona funcionalidad básica para transformar objetos en realidad mixta. Un cuadro de límite mostrará un cubo alrededor del holograma para indicar que se puede interactuar con él. Los identificadores de las esquinas y bordes del cubo permiten escalar o girar el objeto. El cuadro de límite también reacciona a la entrada del usuario. Por HoloLens 2, por ejemplo, el cuadro de límite responde a la proximidad de los dedos, proporcionando comentarios visuales para ayudar a percibir la distancia desde el objeto. Todas las interacciones y objetos visuales se pueden personalizar fácilmente.

Para obtener más información, vea [Rectángulo de selección y Barra de](/windows/mixed-reality/app-bar-and-bounding-box) aplicación en la Windows Centro de desarrollo.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos de configuraciones de rectángulo de selección en la `BoundingBoxExamples` escena.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Adición y configuración de un rectángulo de selección mediante Unity Inspector

1. Agregar Box Collider a un objeto
2. Asignación `BoundingBox` de un script a un objeto
3. Configurar opciones, como los métodos de activación (consulte la [sección Propiedades del inspector](#inspector-properties) a continuación)
4. (Opcional) Asignación de prefabs y materiales para un HoloLens 2 de estilo personalizado (consulte [la](#handle-styles) sección Estilos de control a continuación)

> [!NOTE]
> Use *el campo Target Object* (Objeto de destino) y Bounds Override (Invalidación de *límites)* en el inspector para asignar un objeto específico y un colisionador en el objeto con varios componentes secundarios.

![Rectángulo de selección 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Cómo agregar y configurar un cuadro de límite en el código

1. Creación de instancias de GameObject de cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Asignación `BoundingBox` de un script a un objeto con colisionador mediante AddComponent<>()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurar opciones (consulte la [sección Propiedades del inspector a](#inspector-properties) continuación)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (Opcional) Asigne prefabs y materiales para un HoloLens 2 de selección de estilo. Esto todavía requiere asignaciones a través del inspector, ya que los materiales y los objetos prefabs deben cargarse dinámicamente.

> [!NOTE]
> No se recomienda usar la carpeta "Resources" de Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para cargar sombreadores dinámicamente, ya que es posible que falte permutaciones del sombreador en tiempo de ejecución.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Ejemplo: Establecer la escala mínima y máxima del cuadro de límite mediante MinMaxScaleConstraint

Para establecer la escala mínima y máxima, use [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . También puede usar MinMaxScaleConstraint para establecer la escala mínima y máxima para [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Ejemplo: Agregar un rectángulo de selección alrededor de un objeto de juego

Para agregar un rectángulo de selección alrededor de un objeto, basta con agregarle `BoundingBox` un componente:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Propiedades del inspector

### <a name="target-object"></a>Objeto de destino

Esta propiedad especifica qué objeto se transformará mediante la manipulación del rectángulo delimitador. Si no se establece ningún objeto, el rectángulo delimitador tiene como valor predeterminado el objeto propietario.

### <a name="bounds-override"></a>Invalidación de límites

Establece un colisionador de cuadro del objeto para el cálculo de límites.

### <a name="activation-behavior"></a>Comportamiento de activación

Hay varias opciones para activar la interfaz del cuadro de límite.

* *Activar al iniciar:* el cuadro de límite se vuelve visible una vez iniciada la escena.
* *Activar por proximidad:* el cuadro de límite se vuelve visible cuando una mano articulada está cerca del objeto.
* *Activar mediante puntero:* el rectángulo de selección se vuelve visible cuando se apunta a él mediante un puntero de rayo de mano.
* *Activar manualmente:* el cuadro de límite no se vuelve visible automáticamente. Puede activarlo manualmente a través de un script accediendo a la propiedad boundingBox.Active.

### <a name="scale-minimum"></a>Escala mínima

Escala mínima permitida. Esta propiedad está en desuso y es preferible agregar un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Si se agrega este script, la escala mínima se toma de él en lugar del cuadro de límite.

### <a name="scale-maximum"></a>Escalado máximo

Escala máxima permitida. Esta propiedad está en desuso y es preferible agregar un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Si se agrega este script, se toma la escala máxima de él en lugar del cuadro de límite.

### <a name="box-display"></a>Presentación del cuadro

Varias opciones de visualización del cuadro de límite.

Si Eje de aplanar está establecido en *Aplanar automático,* el script no permitirá la manipulación a lo largo del eje con la extensión más pequeña. Esto da como resultado un cuadro de límite 2D, que normalmente se usa para objetos finos.

### <a name="handles"></a>Asas

Puede asignar el material y el prefab para invalidar el estilo de identificador. Si no se asignan identificadores, se mostrarán en el estilo predeterminado.

## <a name="events"></a>Eventos

El cuadro de límite proporciona los siguientes eventos. En este ejemplo se usan estos eventos para reproducir comentarios de audio.

* **Girar iniciado:** se desencadena cuando se inicia la rotación.
* **Girar finalizado:** se desencadena cuando finaliza la rotación.
* **Escalado iniciado:** se inicia cuando se inicia el escalado.
* **Escala finalizada:** se produce cuando finaliza el escalado.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Estilos de control

De forma predeterminada, al asignar el script, se mostrará el identificador del HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) de primera generación. Para usar HoloLens 2 estilo, debe asignar prefabs y materiales de identificador adecuados.

![Estilos de identificador de cuadro de límite](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

A continuación se muestran los requisitos previos, los materiales y los valores de escalado para los identificadores HoloLens 2 de rectángulo de selección de estilo. Puede encontrar este ejemplo en la `BoundingBoxExamples` escena.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>Identificadores (configuración para HoloLens 2 estilo)

* **Material de** identificador: BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat
* **Prefab del identificador de** escala: MRTK_BoundingBox_ScaleHandle.prefab
* **Prefab de pizarra del** controlador de escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Tamaño del identificador de** escala: 0,016 (1,6 cm)
* **Relleno del colisionador del** controlador de escala: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)
* **Prefab de** identificador de rotación: MRTK_BoundingBox_RotateHandle.prefab
* **Tamaño del identificador de** rotación: 0,016
* **Relleno del colisionador del** controlador de rotación: 0,016 (hace que el colisionador que se puede agarrar sea ligeramente mayor que el objeto visual del controlador)

### <a name="proximity-setup-for-hololens-2-style"></a>Proximidad (configuración para HoloLens 2 estilo)

Mostrar y ocultar los controladores con animación en función de la distancia a las manos. Tiene animación de escalado en dos pasos.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Efecto de proximidad activo:** habilitación de la activación del identificador basado en proximidad
* **Controlar la proximidad media:** distancia para el escalado del primer paso
* **Controlar la proximidad: distancia** para el escalado del segundo paso
* **Escala lejana:** valor de escala predeterminado del recurso de controlador cuando las manos están fuera del intervalo de la interacción del cuadro de límite (distancia definida anteriormente por "Controlar la proximidad media". Use 0 para ocultar el identificador de forma predeterminada)
* **Escala media:** valor de escala del recurso de identificador cuando las manos están dentro del intervalo de la interacción del cuadro de límite (distancia definida anteriormente por "Controlar proximidad cercana". Use 1 para mostrar el tamaño normal)
* **Close Scale**(Escala de cierre): valor de escala del recurso de controlador cuando las manos están dentro del intervalo de la interacción de la toma (distancia definida anteriormente por "Controlar proximidad cercana". Usar 1.x para mostrar un tamaño mayor)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Hacer que un objeto se puede mover con el controlador de manipulación

Un rectángulo de selección se puede combinar con [`ManipulationHandler.cs`](manipulation-handler.md) para que el objeto se pueda mover mediante la interacción lejana. El controlador de manipulación admite interacciones de una y dos manos. [El seguimiento](../input/hand-tracking.md) manual se puede usar para interactuar con un objeto de cerca.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Para que los bordes del cuadro de límite se comporten de la misma manera al moverlo mediante la interacción lejana, se recomienda conectar sus eventos para On Manipulation Started On Manipulation Ended (Al manipular iniciada al finalizar la manipulación), respectivamente, como se muestra en la captura de pantalla [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` anterior.

## <a name="migrating-to-bounds-control"></a>Migración al control de límites

Las instancias y los requisitos previos existentes que usan el [](../tools/migration-window.md) cuadro de límite se pueden actualizar al nuevo control de límites a través de la ventana de migración que forma parte del paquete de herramientas de MRTK. [](bounding-box.md)

Para actualizar instancias individuales del rectángulo de selección, también hay una opción de migración dentro del inspector de propiedades del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">
