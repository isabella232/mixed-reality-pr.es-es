---
title: Mirada con la cabeza y permanencia
description: Introducción a la información general sobre el modelo de entrada de la vista principal y la vivienda, incluidos escenarios comunes y principios de diseño.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realidad mixta, miradas, viviendas, interacción, diseño, auriculares de realidad mixta, auriculares Windows Mixed Reality, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta, experiencia de usuario, directrices, vista de lista
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007085"
---
# <a name="head-gaze-and-dwell"></a>Mirada con la cabeza y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible. Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto. Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad. El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens. Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.

## <a name="scenarios"></a>Escenarios

La mirada y la vivienda son excelentes en escenarios en los que las manos de una persona están ocupadas por otras tareas. La característica también es útil cuando la voz no es 100% confiable o disponible debido a restricciones ambientales o sociales. Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil. Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor. En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz. El encabezado y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo. 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y permanencia</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>


## <a name="design-principles"></a>Principios de diseño

**Evitar miradas a discreción**

El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante. Los comentarios deben ayudar a un usuario a saber lo que tienen como destino, pero no seleccionarlo para su intención. Al leer texto, iconos y etiquetas, debe proporcionar tiempo a los usuarios para absorber la información antes de seleccionarla.
    
**Buscar una velocidad adecuada**
    
Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado. Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido. Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.
    
**Evitar el efecto yo-yo**

El efecto yo-yo es un patrón incómodo de movimiento de cabeza que se produce cuando la colocación del contenido y los controles de cabeza y vista del cabezal y la vivienda obligan a las personas a buscarse y reducirse repetidamente. Por ejemplo, una lista de navegación con el botón de AvPág y el botón de permanencia en la parte inferior induce un bucle de-mirar a la vivienda, buscar en los resultados, buscar en la vivienda, etc. El patrón resultante es inestable, por lo que se recomienda colocar los controles de navegación en una ubicación centralizada que requiera menos. La colocación de los botones de permanencia en función de sus efectos es importante para la comodidad.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Directrices y procedimientos recomendados para la experiencia del usuario

### <a name="target-sizes"></a>Tamaños de los destinos

Para que se pueda acceder fácilmente, los objetivos de la vista de cabeza y de la vivienda deben ser lo suficientemente grandes como para examinarlos de forma cómoda y mantener una ventaja estable en el destino durante el tiempo previsto. Se recomienda un tamaño mínimo de destino de 2 grados para lograr la experiencia más cómoda. 

### <a name="visual-feedback"></a>Información visual

Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón. Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta. 

  * Esta regla se puede romper a pesar de las interacciones direccionales (por ejemplo, NAV arriba/abajo/izquierda/derecha, etc.). Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.
  * Considere la posibilidad de invertir el relleno radial desde fuera, en escenarios como la alternancia de un botón. La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener. 

### <a name="progressive-disclosure"></a>Muestra progresiva

La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción. En el caso de la vivienda, esto significa que el destino de la vivienda se revela en el resaltado (por ejemplo, en un control de lista).

 ### <a name="oversized-targets"></a>Objetivos demasiado grandes

La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar el parpadeo con información retrasada

Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.
* En el caso de los botones interactivos con frecuencia, mantenga el retraso corto para que la aplicación se sienta reactiva.
* En el caso de los botones que se interactúan con poca frecuencia, un retraso más largo puede ser adecuado para evitar la sensación de interfaz twitchy.

<br>

---

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia

:::row:::
    :::column:::
        Los botones de alta frecuencia son botones que se usan habitualmente en una aplicación. Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.<br>
        <br>
        **Recomendaciones**<br>
  * Los botones de alta frecuencia deben ser grandes y más fáciles de visitar
  * Manténgase cerca de la altura para evitar una presión ergonómica.<br>
        <br>
*Imagen: botón siguiente de las guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Botón siguiente de las guías de Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Botones de baja frecuencia

Los botones de baja frecuencia son botones que no interactúan con tan solo en la aplicación. Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.

* Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente. 

<br>

---

### <a name="confirmations"></a>Confirmaciones

:::row:::
    :::column:::
        Cuando una acción tiene un impacto significativo, como la carga de dinero, la eliminación de trabajo o el inicio de un proceso largo, es útil confirmar que una persona está pensada para seleccionar un botón.<br>
        <br>
        **Recomendaciones**<br>
  * Muestra el resaltado de la selección en el botón principal.
  * Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.
  * Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.<br>
        <br>
*Imagen: cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Botones de alternancia

Los botones de alternancia requieren una lógica matizada para que funcionen correctamente. Cuando una persona se aloja en un botón de alternancia y lo activa, debe salir del botón y volver a iniciar la lógica de permanencia. Es importante que los botones que se van a alternar tengan un estado activo e inactivo. 

<br>

---

### <a name="list-views"></a>Vistas de lista

:::row:::
    :::column:::
        Las vistas de lista presentan un desafío determinado para la entrada de encabezado y de continuación. Los usuarios pueden examinar el contenido sin tener que tiptoe en torno a los objetivos de la vivienda.<br>
        <br>
**Recomendaciones**<br>
  * Hacer que la fila completa se resalte cuando se mira por la cabeza, pero no comienza la permanencia, a menos que la punta de la mirada esté en el destino de vivienda específico.
  * Muestre solo el destino de permanencia cuando la fila esté resaltada para reducir el ruido visual.
  * Ser claros y coherentes con la posición de los objetivos de la vivienda.
  * No muestre todos los destinos de permanencia a la vez para evitar la interfaz de usuario repetida.
  * Reutilice el mismo patrón tantas veces como sea posible para establecer la familiaridad de la experiencia del usuario.<br>
        <br>
*Imagen: lista de guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Lista de guías de Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Consulte también

* [Mirada y confirmación](gaze-and-commit.md)
* [Manos: manipulación directa](direct-manipulation.md)
* [Manos: gestos](gaze-and-commit.md#composite-gestures)
* [Manos: apuntar y confirmar](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
