---
title: Mirada con la cabeza y permanencia
description: Introducción al modelo de entrada de mirada con la cabeza y permanencia, incluidos los escenarios comunes y los principios de diseño.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, mirada, permanencia, interacción, diseño, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, experiencia de usuario, directrices, vista de lista
ms.openlocfilehash: e069b0815f69848b7632cb7b1b85d85f328441b7156ae22ffe097fedc3ed6fc1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223630"
---
# <a name="head-gaze-and-dwell"></a>Mirada con la cabeza y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible. Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto. Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad. El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens. Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.

## <a name="scenarios"></a>Escenarios

La mirada con la cabeza y la permanencia son excelentes en escenarios en los que las manos de una persona están ocupadas con otras tareas. La característica también es útil cuando la voz no es 100 % confiable o disponible debido a restricciones ambientales o sociales. Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil. Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor. En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz. La mirada con la cabeza y la permanencia permiten a la persona que usa HoloLens navegar con confianza por su material de referencia sin interrumpir su flujo de trabajo. 

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
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

El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante. Los comentarios deben ayudar a un usuario a saber a qué se dirigirá, pero no seleccionarlo automáticamente con su intención. Al leer texto, iconos y etiquetas, debe proporcionar a los usuarios tiempo para que absorban la información antes de seleccionarla.
    
**Buscar una velocidad adecuada**
    
Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado. Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido. Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.
    
**Evitar el efecto yo-yo**

El efecto yo-yo es un patrón de movimiento de la cabeza no deseado que se produce cuando la colocación del contenido y los controles de mirada con la cabeza o permanencia obligan a los usuarios a buscar y bajar repetidamente. Por ejemplo, una navegación de lista con el botón de mirada con la cabeza y permanencia en la parte inferior induce un bucle de : mirar hacia abajo para permanencia, buscar los resultados, mirar hacia abajo para permanencia, y así sucesivamente. El patrón resultante no es fácil de controlar, por lo que se recomienda colocar controles de navegación en una ubicación centralizada que requiera menos ida y vuelta. La colocación de botones de permanencia en función de sus efectos es importante para la comodidad.
s
<br>

---

## <a name="ux-guidelines-and-best-practices"></a>Directrices y procedimientos recomendados para la experiencia del usuario

### <a name="target-sizes"></a>Tamaños de los destinos

Para ser fácilmente accesibles, los objetivos de mirada con la cabeza y permanencia deben ser lo suficientemente grandes como para mirar cómodamente y mantener la cabeza estable en el destino durante el tiempo prescrito. Se recomienda un tamaño objetivo mínimo de 2 grados para lograr la experiencia más cómoda. 

### <a name="visual-feedback"></a>Información visual

Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón. Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta. 

  * Sin embargo, esta regla se puede dividir para las interacciones direccionales (por ejemplo, navegación hacia arriba, abajo, izquierda o derecha, y así sucesivamente). Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.
  * Considere la posibilidad de invertir el relleno radial desde fuera, en escenarios como desactivar un botón. La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener. 

### <a name="progressive-disclosure"></a>Muestra progresiva

La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción. Para permanencia, esto significa que el objetivo de permanencia se revela al resaltar (por ejemplo, en un control de lista).

 ### <a name="oversized-targets"></a>Objetivos demasiado grandes

La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar el parpadeo con información retrasada

Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.
* En el caso de los botones que interactúan con con frecuencia, mantenga el retraso corto para que la aplicación se sienta reactiva.
* En el caso de los botones que interactúan con con poca frecuencia, un retraso más largo puede ser adecuado para evitar que la interfaz se sienta mal.

<br>

---

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia

:::row:::
    :::column:::
        Los botones de alta frecuencia son botones que se usan normalmente en toda una aplicación. Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.<br>
        <br>
        **Recomendaciones**<br>
  * Los botones de alta frecuencia deben ser grandes, más fáciles de alcanzar con la mirada con la cabeza
  * Permanezca cerca de la altura de los ojos para evitar la tensión de los ojos.<br>
        <br>
*Imagen: Botón siguiente Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![Botón Dynamics 365 Guides siguiente de Microsoft](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Botones de baja frecuencia

Los botones de baja frecuencia son botones que no interactúan con tan regularmente en toda la aplicación. Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.

* Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente. 

<br>

---

### <a name="confirmations"></a>Confirmaciones

:::row:::
    :::column:::
        Cuando una acción tiene un impacto significativo, como cobrar dinero, eliminar trabajo o iniciar un proceso largo, resulta útil confirmar que una persona ha pensado seleccionar un botón.<br>
        <br>
        **Recomendaciones**<br>
  * Muestra el resaltado de la selección en el botón principal.
  * Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.
  * Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.<br>
        <br>
*Imagen: Cuadro de diálogo de confirmación Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![Cuadro de diálogo Dynamics 365 Guides confirmación de Microsoft](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Botones de alternancia

Los botones de alternancia requieren una lógica matizada para que funcionen correctamente. Cuando una persona se detiene en un botón de alternancia y lo activa, debe salir del botón y volver a reiniciar la lógica de permanencia. Es importante que los botones que se pueden alternar tengan un estado activo o inactivo claro. 

<br>

---

### <a name="list-views"></a>Vistas de lista

:::row:::
    :::column:::
        Las vistas de lista presentan un desafío concreto para la mirada con la cabeza y la entrada de permanencia. Las personas pueden examinar el contenido sin tener la sensación de que tienen que propinar en torno a los objetivos de permanencia.<br>
        <br>
**Recomendaciones**<br>
  * Haga que toda la fila se resalte con la cabeza, pero no comience a permanencia a menos que la mirada con la cabeza esté en el objetivo de permanencia específico.
  * Solo se muestra el destino de permanencia cuando la fila está resaltada para reducir el ruido visual.
  * Sea claro y coherente con la posición de los destinos de permanencia.
  * No muestre todos los destinos de permanencia a la vez para evitar una interfaz de usuario repetitiva.
  * Vuelva a usar el mismo patrón tantas veces como sea posible para establecer la familiaridad de la experiencia de usuario.<br>
        <br>
*Imagen: Lista de Dynamics 365 Guides Microsoft*
    :::column-end:::
        :::column:::
       ![Lista de Dynamics 365 Guides Microsoft](images/GuidesListView.png)<br>
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