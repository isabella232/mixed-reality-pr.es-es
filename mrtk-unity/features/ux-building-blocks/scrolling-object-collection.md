---
title: Desplazamiento por la colección de objetos
description: Tipos de menú información general MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, objeto de desplazamiento
ms.openlocfilehash: a97ea9919cf484cf5240dde027f38baca37ba9570588bca032bee9c116aed873
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221757"
---
# <a name="scrolling-object-collection"></a>Desplazamiento por la colección de objetos

![Desplazamiento por la colección de objetos](../images/scrolling-collection/ScrollingCollection_Main.jpg)

La colección de objetos de desplazamiento de MRTK es un componente de la experiencia de usuario que permite el desplazamiento de contenido 3D a través de un área de visualización independiente. El movimiento de desplazamiento se puede desencadenar mediante la interacción de entrada cercana o lejana y mediante la paginación discreta. Admite objetos interactivos y no interactivos.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Introducción a la colección de objetos de desplazamiento

### <a name="setting-up-the-scene"></a>Configuración de la escena

1. Cree una escena de Unity.
1. Para agregar MRTK a la escena, vaya a la Mixed Reality Toolkit Agregar a la escena  >  **y configure**.

### <a name="setting-up-the-scrolling-object"></a>Configuración del objeto de desplazamiento

1. Cree un objeto de juego vacío en la escena y cambie su posición a (0, 0, 1).
1. Agregue un [componente de colección de objetos de desplazamiento](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) al objeto de juego.

    Cuando se agrega la colección de objetos de [](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) desplazamiento, un colisionador de cuadro y un componente táctil de interacción cercana se asociarán automáticamente al objeto raíz del juego. Estos componentes permiten que el objeto de desplazamiento escuche eventos de entrada de interacción cercanos y lejanos, como un puntero táctil o un clic.  

    La colección de objetos de desplazamiento de MRTK tiene dos elementos importantes que se crean como objetos de juego secundarios en la jerarquía de objetos de desplazamiento raíz:
    * `Container` - Todos los objetos de contenido de desplazamiento deben ser secundarios del objeto de juego de contenedor.
    * `Clipping bounds` - Si está habilitado el enmascaramiento de contenido de desplazamiento, el elemento de límites de recorte garantiza que solo esté visible el contenido desplazable dentro de sus límites. El objeto de juego de límites de recorte tiene dos componentes: un colisionador de cuadro deshabilitado y un [cuadro de recorte](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Desplazamiento de elementos de colección de objetos](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Agregar contenido al objeto de desplazamiento

La colección de objetos de [](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) desplazamiento se puede combinar con una colección de objetos de cuadrícula para el contenido de diseño en una cuadrícula de elementos alineados que tienen un tamaño y espaciado uniformes.

1. Cree un objeto de juego vacío como elemento secundario del contenedor de desplazamiento.
1. Agregue un componente de colección de objetos de cuadrícula al objeto de juego.
1. Para un desplazamiento vertical de una sola columna, en la pestaña inspector, configure la colección de objetos de cuadrícula de la siguiente manera:
    * **Columnas num:** 1
    * **Diseño:** columna y fila
    * **Delimitador:** parte superior izquierda
1. Cambie el **ancho y el** alto de la **celda** según las dimensiones de los objetos de contenido.
1. Agregue los objetos de contenido como elementos secundarios del objeto de cuadrícula.
1. Presione **actualizar colección**.

![Diseño de cuadrícula](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Cualquier material de objeto de contenido de desplazamiento debe usar el sombreador estándar [MRTK](../rendering/MRTK-standard-shader.md) para que el efecto de recorte en el área visualizable funcione correctamente.

> [!NOTE]
> Si está habilitado el enmascaramiento de contenido de desplazamiento, la colección de objetos de desplazamiento agregará un componente de instancia de [material](../rendering/material-instance.md) a cualquier objeto de contenido que tenga asociado un representador. Este componente se usa para administrar la duración de los materiales de instancia y mejorar el rendimiento de la memoria.

### <a name="configuring-the-scrolling-viewable-area"></a>Configuración del área de desplazamiento que se puede ver

1. Para el desplazamiento vertical a través de una sola columna de objetos, en la pestaña inspector, configure la colección de objetos de desplazamiento de la siguiente manera:
    * **Celdas por nivel:** 1
    * Elija el número de **niveles por página** según el número deseado de filas visibles.
1. Cambie el **ancho, el** **alto** y la profundidad de la celda **de** página según las dimensiones de los objetos de contenido.

Observe que los objetos de contenido que se encuentran fuera del área de desplazamiento visualizable ahora están deshabilitados, mientras que los objetos que intersecan con el wireframe de desplazamiento podrían enmascararse parcialmente mediante la primitiva de recorte.

![Área que se puede ver](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Prueba de la colección de objetos de desplazamiento en el editor

1. Presione el botón de reproducción y mantenga presionada la barra espaciador para mostrar una mano de simulación de entrada.
1. Mueva la mano hasta que el colisionador de desplazamiento o cualquier contenido interactivo de desplazamiento esté en el foco y desencadene el movimiento de desplazamiento haciendo clic y arrastrando hacia arriba y hacia abajo con el mouse izquierdo.

## <a name="controlling-the-scrolling-object-from-code"></a>Controlar el objeto de desplazamiento desde el código

La colección de objetos de desplazamiento de MRTK expone algunos métodos públicos que permiten mover el contenedor de desplazamiento al ajustar su posición según la configuración `pagination` de propiedades.

Un ejemplo de cómo acceder a la interfaz de paginación de la colección de objetos de desplazamiento está disponible para su uso en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` carpeta . El [script de ejemplo de paginación](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) desplazable se puede vincular a cualquier colección de objetos de desplazamiento existente en la escena. Los componentes de escena que exponen eventos de Unity (por ejemplo, [el botón MRTK)](button.md)pueden hacer referencia al script.

```c#
public class ScrollablePagination : MonoBehaviour
{
    [SerializeField]
    private ScrollingObjectCollection scrollView;

    public void ScrollByTier(int amount)
    {
        scrollView.MoveByTiers(amount);
    }
}
```

## <a name="scrolling-object-collection-properties"></a>Desplazamiento de las propiedades de la colección de objetos

| General          | Description                                   |
| :--------------- | :-------------------------------------------- |
| Desplazarse en un sentido | Dirección en la que se debe desplazar el contenido. |

| Paginación     | Description                                                                                               |
| :------------- | :-------------------------------------------------------------------------------------------------------- |
| Celdas por nivel | Número de celdas de una fila en la vista de desplazamiento hacia abajo o número de celdas de una columna en la vista de desplazamiento izquierda-derecha. |
| Niveles por página | Número de niveles visibles en el área de desplazamiento.                                                            |
| Celda de página      | Dimensiones de la celda de paginación.                                                                        |

| Configuración avanzada           | Description                                                                                                                                                                |
| :-------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Modo de edición de máscara              | Modos de edición para definir los límites del enmascaramiento del cuadro de recorte. 'Auto' usa automáticamente valores de paginación. 'Manual' permite la manipulación directa del objeto del cuadro de recorte. |
| Modo de edición de colisionador          | Modos de edición para definir los límites del colisionador de interacción de desplazamiento. 'Auto' usa automáticamente valores de paginación. 'Manual' permite la manipulación directa del colisionador.     |
| Se puede desplazar                  | Habilita o deshabilita el desplazamiento con una interacción cercana o lejana.                                                                                                                      |
| Usar en la representación previa           | Alterna si scrollingObjectCollection usará el evento Camera OnPreRender para administrar la visibilidad del contenido.                                                          |
| Curva de paginación            | Curva de animación para la paginación.                                                                                                                                            |
| Longitud de animación            | Cantidad de tiempo (en segundos) que paginationCurve llevará evaluar.                                                                                                 |
| Umbral de desplazamiento diferencial de mano | La distancia, en metros, el puntero actual puede desplazarse a lo largo de la dirección de desplazamiento antes de desencadenar un arrastre de desplazamiento.                                                        |
| Distancia táctil frontal        | Distancia, en metros, para colocar un plano xy local usado para comprobar si se inició una interacción táctil en la parte frontal de la vista de desplazamiento.                                           |
| Umbral de versión           | Retirar la cantidad, en metros, de los límites de desplazamiento necesarios para pasar de la entrada táctil a la liberada.                                                                |

| Velocidad            | Description                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------- |
| Tipo de velocidad    | Tipo deseado de caída de velocidad para el scroller.                                                      |
| Multiplicador de velocidad | Cantidad de velocidad (adicional) que se va a aplicar al desplazamiento.                                                       |
| Velocidad de la aceleración     | Cantidad de reserva aplicada a la velocidad.                                                                  |
| Multiplicador de saltos   | Multiplicador para agregar más saltos al sobrescroll de una lista cuando se usa la reserva por fotograma o la reserva por elemento. |

| Opciones de depuración         | Description                                                                                                 |
| --------------------- | ----------------------------------------------------------------------------------------------------------- |
| Máscara habilitada          | Modo de visibilidad del contenido de desplazamiento. El valor predeterminado enmascarará todos los objetos fuera del área visualizable de desplazamiento. |
| Mostrar planos de umbral | Si es true, el editor representará los planos de umbral de lanzamiento táctil alrededor de los límites de desplazamiento.            |
| Paginación de depuración      | Use esta sección para depurar la paginación de desplazamiento durante el tiempo de ejecución.                                             |

| Eventos              | Descripción                                                                                                                   |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Al hacer clic en            | Se desencadena cuando el colisionador de fondo de desplazamiento o cualquiera de su contenido interactivo recibe un clic.                             |
| On touch started    | Se desencadena cuando el colisionador de fondo de desplazamiento o cualquiera de su contenido interactivo recibe un toque de interacción cercano.            |
| Al tocar finalizado      | Se desencadena cuando finaliza una interacción táctil activa cuando el puntero de interacción cercana cruza un plano de umbral de versión. |
| En el momento en que se inició | Se desencadena cuando el contenedor de desplazamiento comienza a moverse por interacción, caída de velocidad o paginación.                            |
| Al finalizar el impulso   | Se desencadena cuando el contenedor de desplazamiento deja de moverse por interacción, caída de velocidad o paginación.                             |

## <a name="scrolling-example-scene"></a>Escena de ejemplo de desplazamiento

**La escena de ejemplo ScrollingObjectCollection.unity** consta de tres ejemplos desplazables, cada uno con una configuración de reserva de velocidad diferente. La escena de ejemplo contiene paredes para mostrar los comportamientos de colocación en la superficie, que están deshabilitados de manera predeterminada en la jerarquía. La escena de ejemplo se puede encontrar en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` carpeta .

![Escena de ejemplo de colección de objetos de desplazamiento](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Prefabs de ejemplo de desplazamiento

Para mayor comodidad, hay dos elementos prefabs de colección de objetos de desplazamiento disponibles para su uso. Los requisitos previos de ejemplo se pueden encontrar en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` carpeta .

![Elementos prefabs de la colección de objetos de desplazamiento](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Consulte también

* [Primitivo de recorte](../rendering/clipping-primitive.md)
* [Instancia de material](../rendering/material-instance.md)
* [Sombreador estándar](../rendering/MRTK-standard-shader.md)
* [Colección de objetos](object-collection.md)
