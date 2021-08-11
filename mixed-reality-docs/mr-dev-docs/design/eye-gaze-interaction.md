---
title: Interacción basada en el control con los ojos
description: Obtenga información sobre las interacciones basadas en los ojos y la mirada en HoloLens 2 y los nuevos niveles de contexto y comprensión humana si se ofrece en experiencias holográficas.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Eye Tracking, Mixed Reality, Input, eye-gaze, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, design, interactions
ms.openlocfilehash: aec41c6654ce10254648e90e08a09ff9adade75a3dc63af81a0953b67b95729f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220961"
---
# <a name="eye-gaze-based-interaction-on-hololens-2"></a>Interacción basada en la mirada con los ojos en HoloLens 2

![Demostración de seguimiento de los ojos en MRTK](images/mrtk_et_scenemenu.jpg)

Una de nuestras nuevas y emocionantes funcionalidades en HoloLens 2 es el seguimiento de los ojos. En nuestra [página Seguimiento](eye-tracking.md) de los HoloLens 2, mencionamos la necesidad de que cada usuario pase por una calibración, proporcionó algunas instrucciones para desarrolladores y resaltó los casos de uso para el seguimiento de los ojos. [](/hololens/hololens-calibration) La entrada con mirada con los ojos sigue siendo un nuevo tipo de entrada de usuario y hay mucho que aprender. 

Aunque la entrada de mirada con los ojos solo se usa sutilmente en nuestra experiencia de Holographic Shell (la interfaz de usuario que se ve al iniciar la HoloLens 2), varias aplicaciones, como ["HoloLens Playground",](https://www.microsoft.com/p/mr-playground/9nb31lh723s2)muestran excelentes ejemplos sobre cómo la entrada de mirada con los ojos puede agregar a la magia de la experiencia holográfica.
En esta página, analizaremos las consideraciones de diseño para integrar la entrada de mirada con los ojos para interactuar con las aplicaciones holográficas.

Aprenderá sobre las ventajas clave y también los desafíos únicos que se incluyen con la entrada de mirada con los ojos. En función de estos, se proporcionan varias recomendaciones de diseño que le ayudarán a crear interfaces de usuario compatibles con la mirada con los ojos. 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
</colgroup>
<tr>
     <td><strong>Característica</strong></td>
     <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Mirada con los ojos</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demostración de los conceptos de diseño de seguimiento de la cabeza y los ojos

Si quiere ver en acción los conceptos de diseño de seguimiento de cabeza y manos, consulte nuestra demostración de vídeo **Diseño de hologramas: Seguimiento de cabeza y seguimiento de manos** a continuación. Cuando haya terminado, continúe para profundizar más en detalle en temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Designing Holograms" para HoloLens 2. Descargue y disfrute de la experiencia completa [aquí](https://aka.ms/dhapp).*

## <a name="eye-gaze-input-design-guidelines"></a>Directrices de diseño de entrada con mirada con los ojos

Crear una interacción que aproveche las ventajas de la orientación con los ojos de movimiento rápido puede ser un desafío. En esta sección, se resumen las principales ventajas y desafíos que se deben tener en cuenta al diseñar la aplicación. 

### <a name="benefits-of-eye-gaze-input"></a>Ventajas de la entrada de mirada con los ojos

- **Señalización a alta velocidad.** El ojo es el más rápido que reacciona en el cuerpo humano. 

- **Poco esfuerzo.** Prácticamente no se necesita ningún movimiento físico. 

- **Implícito.** A menudo descrita por los usuarios como "lectura de mente", la información sobre los movimientos de los ojos de un usuario permite al sistema saber qué destino planea interactuar con el usuario. 

- **Canal de entrada alternativo.** La mirada con los ojos puede proporcionar una entrada auxiliar eficaz para la entrada de mano y voz a partir de años de experiencia de los usuarios en función de su coordinación con los ojos.

- **Atención visual.** Otra ventaja importante es la posibilidad de deducir a qué está prestando atención un usuario. Esto puede ayudar en varias áreas de aplicación, desde la evaluación más eficaz de diferentes diseños hasta la ayuda en interfaces de usuario más inteligentes y indicaciones sociales mejoradas para la comunicación remota.

En pocas palabras, el uso de la mirada con los ojos como entrada ofrece una señal de entrada contextual rápida y sin esfuerzo. Esto es eficaz cuando se combina  con otras entradas, como la voz y la entrada *manual,* para confirmar la intención del usuario.


### <a name="challenges-of-eye-gaze-as-an-input"></a>Desafíos de la mirada con los ojos como entrada

Aunque la mirada con los ojos se puede usar para crear experiencias de usuario satisfactorias, lo que le hace sentir como un héroe, también es importante saber en qué no es bueno tener en cuenta esto correctamente. En la lista siguiente se analizan algunos *desafíos* que se deben tener en cuenta y cómo abordarlos al trabajar con la entrada de mirada con los ojos: 

- **La mirada con los ojos está "siempre on"** En el momento en que se abren los ojos, los ojos empiezan a corregirse en las cosas del entorno. Reaccionar a cada aspecto que realice y emitir acciones accidentalmente, porque ha visto algo durante demasiado tiempo, daría lugar a una experiencia insatisfecho.
Se recomienda combinar la mirada con los ojos  con un comando de voz *,* un gesto con la *mano,* un clic en el botón o una permanencia extendida para desencadenar la selección de un destino (para más información, consulte mirada con los ojos y [confirmación).](gaze-and-commit-eyes.md)
Esta solución también permite un modo en el que el usuario puede mirar libremente sin verse sobrecargado al desencadenar algo involuntariamente. Este problema también debe tenerse en cuenta al diseñar comentarios visuales y auditivas al mirar un destino.
Intente no sobrecargar al usuario con efectos emergentes inmediatos o sonidos de mantener el puntero. La sutilidad es clave. A continuación se analizarán algunos procedimientos recomendados para esto al hablar de las [recomendaciones de diseño](eye-gaze-interaction.md#design-recommendations).

- **Observación frente a control** Imagine que quiere enderezar con precisión una fotografía en la pared. Miras los bordes y la zona circundante para ver si está bien alineada. Ahora imagine cómo lo haría cuando quiera usar la mirada con los ojos como entrada para mover la imagen. Difícil, ¿verdad? Esto describe el doble rol de la mirada con los ojos cuando es necesario tanto para la entrada como para el control. 

- **Déjelo antes de hacer clic:** En el caso de las selecciones de destino rápidas, la investigación ha demostrado que la mirada con los ojos de un usuario puede avanzar antes de concluir un clic manual (por ejemplo, un toque de aire). Preste especial atención a la sincronización de la señal de mirada rápida con una entrada de control más lenta (por ejemplo, voz, manos, controlador).

- **Destinos pequeños:** ¿Conoce la sensación cuando intenta leer texto que es un poco demasiado pequeño para leer cómodamente? Esta sensación de presión en los ojos puede hacer que se sienta cómodo y agotado, ya que intenta reajustar los ojos para centrarse mejor.
Se trata de una sensación que puede invocar en los usuarios al forzarles a seleccionar destinos demasiado pequeños en la aplicación mediante la selección de los ojos.
Al diseñar la aplicación, para crear una experiencia agradable y cómoda para los usuarios, se recomienda que los objetivos sean al menos de 2° en ángulo visual, o preferiblemente mayores.

- **Movimientos de mirada con los ojos desiguales** Nuestros ojos realizan movimientos rápidos de la fijación a la corrección. Si observas las trayectorias de movimientos registrados de ojos, podrás ver que son irregulares. Los ojos se mueven rápidamente y en saltos escarnósmos en comparación con los movimientos *de* mirada con la cabeza *o de la mano.*  

- **Confiabilidad de seguimiento:** La precisión del seguimiento de los ojos puede disminuir un poco en la luz cambiante a medida que los ojos se ajustan a las nuevas condiciones.
Aunque esto no debe afectar necesariamente al diseño de la aplicación, ya que la precisión debe estar dentro de la limitación de 2°, puede ser necesario que el usuario vuelva a calibrar. 


## <a name="design-recommendations"></a>Recomendaciones de diseño
A continuación se muestra una lista de recomendaciones de diseño específicas basadas en las ventajas y desafíos descritos para la entrada de mirada con los ojos:

1. **La mirada con los ojos no es la misma que la mirada con la cabeza:**
    - **Tenga en cuenta si los movimientos de los ojos rápidos pero desiguales se ajustan a la tarea de entrada:** Aunque los movimientos de los ojos rápidos y desiguales son excelentes para seleccionar rápidamente los destinos en nuestro campo de visión, es menos aplicable a las tareas que requieren entradas fluidas (por ejemplo, dibujar o rodear anotaciones). En este caso, es preferible apuntar con la mano o con la cabeza.
  
    - **Evite adjuntar algo directamente a la mirada con los ojos del usuario (por ejemplo, un control deslizante o un cursor).**
Con los cursores, esto puede dar lugar a un efecto de "cursor de desplazamiento" debido a pequeños desplazamientos en la señal de mirada con los ojos proyectada. Con un control deslizante, puede estar en conflicto con el doble rol de controlar el control deslizante con los ojos, al tiempo que desea comprobar si el objeto está en la ubicación correcta. En el ejemplo del control deslizante, tiene más sentido usar la mirada con los ojos en combinación con los gestos de la mano. Esto significa que el usuario podría cambiar rápida y sin esfuerzo entre muchos controles deslizantes, elevar la mano y deslizar el dedo índice y el dedo para agarrarlo y moverlo. Cuando se libera el control deslizante, el control deslizante deja de moverse. Los usuarios podrían sobrecargarse y distraerse, especialmente si la señal es imprecisa para ese usuario. 
  
2. **Combine la mirada con los ojos con otras entradas:** La integración del seguimiento de los ojos con otras entradas, como gestos de mano, comandos de voz o pulsaciones de botón, proporciona varias ventajas:
    - **Permitir la observación libre:** Dado que el rol principal de nuestros ojos es observar nuestro entorno, es importante que los usuarios puedan mirar sin desencadenar comentarios o acciones (visuales, auditivas, entre otros). 
    La combinación del seguimiento de los ojos con otro control de entrada permite realizar una transición fluida entre los modos de observación de seguimiento de los ojos y de control de entrada.
  
    - **Proveedor de contexto eficaz:** El uso de información sobre dónde y lo que el usuario está mirando mientras dice un comando de voz o un gesto con la mano permite canalizar sin problemas la entrada a través del campo de vista. Por ejemplo: diga _"put that there"_ (colocarlo allí) para seleccionar y colocar un holograma de forma rápida y fluida en la escena mediante la búsqueda de un destino y su destino previsto. 

    - **Necesidad de sincronizar entradas multimodales:** La combinación de movimientos rápidos de los ojos con entradas más complejas, como comandos de voz largos o gestos de mano, conlleva el riesgo de que el usuario ya siga observando antes de que el comando de entrada adicional finalice y se reconozca. Si crea sus propios controles de entrada (por ejemplo, gestos de mano personalizados), asegúrese de registrar el inicio de esta entrada o la duración aproximada para correlacionarse con lo que un usuario había visto en el pasado.
    
3. **Comentarios sutiles sobre la entrada de seguimiento de los ojos:** Es útil proporcionar comentarios cuando se busca un destino para indicar que el sistema funciona según lo previsto, pero debe ser sutil. Esto puede incluir la combinación lenta de entrada y salida, resaltados visuales o realizar otros comportamientos de destino sutiles, como movimientos lentos, como aumentar ligeramente el tamaño de destino. Esto indica que el sistema detectó correctamente que el usuario está mirando un destino sin interrumpir innecesariamente el flujo de trabajo actual del usuario. 

4. **Evite aplicar movimientos de los ojos no naturales como entrada:** No fuerce a los usuarios a usar movimientos de los ojos específicos (gestos de mirada) para desencadenar acciones en la aplicación.

5. **Cuentas de imprecisiones:** Se distinguen dos tipos de imprecisiones, que son apreciables para los usuarios: desplazamiento y vibración. La manera más fácil de abordar un desplazamiento es proporcionar destinos lo suficientemente grandes con los que interactuar. Se recomienda usar un ángulo visual superior a 2° como referencia. Por ejemplo, la miniatura tiene un ángulo visual de aproximadamente 2° cuando se extiende el brazo. Esto conduce a la siguiente pauta:
    - No fuerce a los usuarios a seleccionar destinos pequeños. La investigación ha demostrado que si los objetivos son lo suficientemente grandes y el sistema está bien diseñado, los usuarios describen sus interacciones como sencillas y mágicas. Si los objetivos son demasiado pequeños, los usuarios describen la experiencia como agotadora y frustrante.
  
<br>

Esta página le proporcionó una buena introducción para empezar a comprender la mirada con los ojos como entrada en realidad mixta. Para empezar a desarrollar, consulte nuestra información sobre la mirada con los ojos [en Unity](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) y la mirada con los ojos [en DirectX.](../develop/native/gaze-in-directx.md)


## <a name="see-also"></a>Consulta también
* [Comodidad](comfort.md)
* [Mirada con los ojos en DirectX](../develop/native/gaze-in-directx.md)
* [Mirada con los ojos en Unity (Mixed Reality Toolkit)](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)
* [Seguimiento de los ojos en HoloLens 2](eye-tracking.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Entrada de voz](../out-of-scope/voice-design.md)