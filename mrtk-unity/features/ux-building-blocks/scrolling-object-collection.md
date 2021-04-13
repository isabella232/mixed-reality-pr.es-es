---
title: Desplazamiento por la colección de objetos
description: Tipos de menús de información general MRTK
author: vaoliva
ms.author: vaolivaa
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, desplazamiento de objetos
ms.openlocfilehash: 0ed1d61aed203a5daa45c5d89990e66115cc3abb
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300120"
---
# <a name="scrolling-object-collection"></a>Desplazamiento por la colección de objetos

![Desplazamiento por la colección de objetos](../images/scrolling-collection/ScrollingCollection_Main.jpg)

La colección de objetos de desplazamiento MRTK es un componente de experiencia de usuario que permite desplazarse por el contenido 3D a través de un área visible incluida. El movimiento de desplazamiento se puede desencadenar mediante la interacción de entrada near o FAR y la paginación discreta. Admite objetos interactivos y no interactivos.

## <a name="getting-started-with-the-scrolling-object-collection"></a>Introducción a la colección de objetos de desplazamiento

### <a name="setting-up-the-scene"></a>Configuración de la escena

1. Cree una nueva escena de Unity.
1. Agregue MRTK a la escena; para ello, vaya al **Kit de herramientas de realidad mixta**  >  **Agregar a la escena y configurar**.

### <a name="setting-up-the-scrolling-object"></a>Configurar el objeto de desplazamiento

1. Cree un objeto de juego vacío en la escena y cambie su posición a (0, 0, 1).
1. Agregue un componente de [colección de objetos de desplazamiento](xref:Microsoft.MixedReality.Toolkit.UI.ScrollingObjectCollection) al objeto de juego.

    Cuando se agrega la colección de objetos de desplazamiento, se adjuntará automáticamente un Colisionador de cuadro y un componente [táctil cercano](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) a la interacción con el objeto de juego raíz. Estos componentes permiten que el objeto scroll escuche eventos de entrada de interacción Near y Far, como un toque de puntero o un clic.  

    La colección de objetos de desplazamiento MRTK tiene dos elementos importantes que se crean como objetos de juego secundarios en la jerarquía de objetos de desplazamiento raíz:
    * `Container` -Todos los objetos de contenido de desplazamiento deben ser secundarios del objeto de juego del contenedor.
    * `Clipping bounds` -Si se habilita el enmascaramiento de contenido de desplazamiento, el elemento de límite de recorte garantiza que solo esté visible el contenido desplazable dentro de sus límites. El objeto de juego de los límites de recorte tiene dos componentes: un Colisionador de cuadro deshabilitado y un [cuadro de recorte](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox).

![Desplazar elementos de la colección de objetos](../images/scrolling-collection/ScrollingObjectCollection.png)

### <a name="adding-content-to-the-scrolling-object"></a>Agregar contenido al objeto de desplazamiento

La colección de objetos de desplazamiento se puede combinar con una [colección de objetos Grid](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) para diseñar contenido en una cuadrícula de elementos alineados que tengan un tamaño y espaciado uniformes.

1. Cree un objeto de juego vacío como un elemento secundario del contenedor de desplazamiento.
1. Agregue un componente de colección de objetos de cuadrícula al objeto de juego.
1. Para un desplazamiento de una sola columna vertical, en la pestaña inspector, configure la colección de objetos Grid de la siguiente manera:
    * **Número de columnas**: 1
    * **Diseño**: columna y fila
    * **Delimitador**: superior izquierda
1. Cambiar el **ancho** y el **alto** de la celda según las dimensiones de los objetos de contenido.
1. Agregue los objetos de contenido como elementos secundarios del objeto Grid.
1. Presione **Actualizar colección**.

![Diseño de cuadrícula](../images/scrolling-collection/ScrollingObjectCollection_GridLayout.png)

> [!IMPORTANT]
> Cualquier material de objeto de contenido de desplazamiento debe usar el [sombreador estándar de MRTK](../rendering/MRTK-standard-shader.md) para que el efecto de recorte en el área visible funcione correctamente.

> [!NOTE]
> Si está habilitado el enmascaramiento de contenido de desplazamiento, la colección de objetos de desplazamiento agregará un componente de [instancia de material](../rendering/material-instance.md) a los objetos de contenido que tengan un representador adjunto. Este componente se utiliza para administrar la duración de los materiales de instancia y mejorar el rendimiento de la memoria.

### <a name="configuring-the-scrolling-viewable-area"></a>Configurar el área visible de desplazamiento

1. Para el desplazamiento vertical a través de una sola columna de objetos, en la pestaña inspector, configure la colección de objetos de desplazamiento de la siguiente manera:
    * **Celdas por nivel**: 1
    * Elija el número de **niveles por página** según el número deseado de filas visibles.
1. Cambiar el **ancho**, el **alto** y la **profundidad** de celda de la página según las dimensiones de los objetos de contenido.

Observe que los objetos de contenido que se encuentran fuera del área visible de desplazamiento están ahora deshabilitados, mientras que los objetos que interseccionan el alambre de desplazamiento pueden estar parcialmente enmascarados por el primitivo de recorte.

![Área visible](../images/scrolling-collection/ScrollingObjectCollection_ViewableArea.png)

### <a name="testing-the-scrolling-object-collection-in-the-editor"></a>Probar la colección de objetos de desplazamiento en el editor

1. Presione reproducir y mantenga presionada la barra espaciadora para mostrar una simulación de entrada.
1. Mueva la mano hasta que el dedor de desplazamiento o cualquier contenido interactivo de desplazamiento esté en el foco y desencadene el movimiento de desplazamiento haciendo clic y arrastrando hacia arriba y hacia abajo con el botón primario del mouse.

## <a name="controlling-the-scrolling-object-from-code"></a>Controlar el objeto de desplazamiento desde el código

La colección de objetos de desplazamiento MRTK expone algunos métodos públicos que permiten mover el contenedor de desplazamiento ajustando su posición de acuerdo con la `pagination` configuración de las propiedades.

Un ejemplo de cómo tener acceso a la interfaz de paginación de la colección de objetos de desplazamiento está disponible para su uso en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Scripts`` carpeta. El script de ejemplo de [paginación desplazable](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.ScrollablePagination) se puede vincular a cualquier colección de objetos de desplazamiento existente en la escena. A continuación, los componentes de la escena que exponen eventos de Unity pueden hacer referencia al script (por ejemplo, el [botón MRTK](button.md)).

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

## <a name="scrolling-object-collection-properties"></a>Propiedades de la colección de desplazamiento de objetos

| General                                                                                                                                                                                                     |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Desplazarse en un sentido             | Dirección en la que se debe desplazar el contenido.|

| Paginación                   |               Descripción                                                                                                                                                                                      |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Celdas por nivel               | Número de celdas de una fila en la vista de desplazamiento hacia abajo o el número de celdas de una columna en la vista de desplazamiento a la izquierda.                                                                                                         |
| Niveles por página               | Número de niveles visibles en el área de desplazamiento.                                                                                                                                                                         |
| Celda de página                    | Dimensiones de la celda de paginación.                  |

| Configuración avanzada            |                  Descripción                                                                                                                                                                                    |
|:-----------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Modo de edición de máscara               | Modos de edición para definir los límites de enmascaramiento del cuadro de recorte. Elija ' automático ' para usar automáticamente los valores de paginación. Elija ' manual ' para habilitar la manipulación directa del objeto de cuadro de recorte.|
| Modo de edición de Colisionador           | Modos de edición para definir los límites del Colisionador de interacción de desplazamiento. Elija ' automático ' para usar automáticamente los valores de paginación. Elija ' manual ' para habilitar la manipulación directa del Colisionador.|
| Se puede desplazar                   | Habilita o deshabilita el desplazamiento con interacción cercana/lejos.                  |
| Usar en la representación previa            | Alterna si scrollingObjectCollection usará el evento de cámara OnPreRender para administrar la visibilidad del contenido.                  |
| Curva de paginación             | Curva de animación para la paginación.                  |
| Longitud de la animación             | Cantidad de tiempo (en segundos) que el PaginationCurve tardará en evaluar.                  |
| Umbral de desplazamiento de Delta de mano  | Distancia, en metros, que el puntero actual puede viajar a lo largo de la dirección de desplazamiento antes de desencadenar una arrastre de desplazamiento.                  |
| Distancia táctil frontal         | Distancia, en metros, para colocar un plano XY local que se usa para comprobar si se inició una interacción táctil en la parte delantera de la vista de desplazamiento.                  |
| Umbral de versión            | Retire el importe, en metros, de los límites de desplazamiento necesarios para la transición de la entrada táctil a la versión de lanzamiento.                  |

| Velocidad |               Descripción                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Tipo de velocidad       | Tipo deseado de reducción de velocidad para el desplazador.                                                                                        |
| Multiplicador de velocidad     | Cantidad de velocidad (extra) que se va a aplicar al desplazador.                                                                                                                                                        |
| Amortiguación de velocidad     | Cantidad de disminución aplicada a la velocidad. |
| Multiplicador de rebote     | Multiplicador para agregar más rebote al desplazado de una lista cuando se usa la disminución por fotograma o disminución por elemento. |

| Opciones de depuración |            Descripción                                                                                                                                                                         |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Máscara habilitada       | Modo de visibilidad del contenido de desplazamiento. El valor predeterminado enmascarará todos los objetos fuera del área visible de desplazamiento.                                                                                        |
| Mostrar planos de umbral     | Si es true, el editor representará los planos de umbral de la versión táctil alrededor de los límites de desplazamiento.                                                                                                                                                        |
| Depurar paginación     | Utilice esta sección para depurar la paginación de desplazamiento durante el tiempo de ejecución. |

| Eventos|    Descripción                                                                                                                                                                                 |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Al hacer clic       | Evento que se desencadena cuando el Colisionador de fondo de desplazamiento o cualquiera de sus contenidos interactivos reciben un clic.                                                                                        |
| Al iniciar Touch     | Evento que se desencadena cuando el Colisionador de fondo de desplazamiento o cualquiera de sus contenidos interactivos reciben un toque de interacción cercano.                                                                                                                                                        |
| En el toque finalizado     | Evento que se desencadena cuando se termina una interacción táctil activa haciendo que el puntero de interacción aproximado cruce uno de los planos de umbral de versión. |
| En el momento en que se inicia     | Evento desencadenado cuando el contenedor de desplazamiento comienza a moverse por interacción, velocidad fallofff o paginación. |
| En el momento de finalizar     | Evento que se desencadena cuando el contenedor de desplazamiento deja de moverse por interacción, velocidad fallofff o paginación. |

## <a name="scrolling-example-scene"></a>Escena de ejemplo de desplazamiento

La escena de ejemplo de **ScrollingObjectCollection. Unity** consta de tres ejemplos desplazables, cada uno con una configuración de reducción de velocidad diferente. La escena de ejemplo contiene paredes para mostrar el comportamiento de selección de ubicación de la superficie que está deshabilitado de forma predeterminada en la jerarquía. La escena de ejemplo puede encontrarse en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Scenes`` carpeta.

![Escena de ejemplo de colección de objetos de desplazamiento](../images/scrolling-collection/ScrollingObjectCollection_ExampleScene.png)

## <a name="scrolling-example-prefabs"></a>Ejemplo de desplazamiento Prefabs

Para mayor comodidad, se pueden usar dos Prefabs de colección de objetos de desplazamiento. El ejemplo de Prefabs se puede encontrar en la ``MRTK/Examples/Demos/ScrollingObjectCollection/Prefabs`` carpeta.

![Desplazarse por la colección de objetos Prefabs](../images/scrolling-collection/ScrollingObjectCollection_Prefabs.png)

## <a name="see-also"></a>Consulte también

* [Primitivo de recorte](../rendering/clipping-primitive.md)
* [Instancia de material](../rendering/material-instance.md)
* [Sombreador estándar](../rendering/MRTK-standard-shader.md)
* [Colección de objetos](object-collection.md)
