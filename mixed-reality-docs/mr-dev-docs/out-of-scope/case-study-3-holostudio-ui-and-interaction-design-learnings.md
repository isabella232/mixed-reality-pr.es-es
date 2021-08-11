---
title: 'Caso práctico: 3 aprendizajes de diseño HoloStudio interfaz de usuario e interacción'
description: Conocimientos acerca del diseño de interacción yd e la interfaz de usuario de HoloStudio
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, HoloStudio, Windows Mixed Reality
ms.openlocfilehash: 1b384a10d3fe53cf7e69c2e8437904040322dc213d9473d9ae9abf272c08ec5e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195908"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a>Caso práctico: 3 aprendizajes de diseño HoloStudio interfaz de usuario e interacción

[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) fue una de las primeras aplicaciones de Microsoft para HoloLens. Debido a esto, hemos tenido que crear nuevos procedimientos recomendados para la interfaz de usuario 3D y el diseño de interacción. Lo hicimos a través de una gran cantidad de pruebas de usuario, creación de prototipos y pruebas y errores.

Sabemos que no todo el mundo tiene los recursos a su disposición para realizar este tipo de investigación, por lo que nuestro diseñador holográfico sr., Senior Holographic Designer, Senior Threely, compartimos tres cosas que aprendimos durante el desarrollo de HoloStudio sobre la interfaz de usuario y el diseño de interacción para aplicaciones de HoloLens.

## <a name="watch-the-video"></a>Visualización del vídeo

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a>Problema #1: las personas no deseaban moverse por sus creaciones

Originalmente diseñamos el área de trabajo en HoloStudio como un rectángulo, de forma muy parecido a como lo encontraría en el mundo real. El problema es que las personas tienen una experiencia de duración que les indica que permanezcan quietos cuando están sentados en un escritorio o trabajando delante de un equipo, por lo que no se desplazaban por el área de trabajo y exploraban su creación en 3D desde todos los lados.

![El diseño rectangular del área de trabajo en HoloStudio disuadir a los usuarios de moverse y ver sus creaciones desde todos los lados.](images/rectangular-workbench-500px.jpg)

Hemos tenido la información para que el área de trabajo se redondee, de modo que no haya ningún lugar "frontal" o claro en el que se supone que debía ponerse de pie. Cuando lo probamos, de repente, los usuarios empezaron a moverse y explorar sus creaciones por sí solas.

![El diseño circular del área de trabajo animaba a los usuarios a recorrer sus creaciones.](images/circular-workbench-500px.jpg)

**¿Qué hemos aprendido?**

Piense siempre en lo que es cómodo para el usuario. Aprovechar su espacio físico es una característica interesante de HoloLens y algo que no se puede hacer con otros dispositivos.

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a>Problema #2: los diálogos modales a veces están fuera del marco holográfico

A veces, es posible que el usuario esté mirando en una dirección diferente a la de algo que necesita su atención en la aplicación. En un equipo, solo puede mostrar un cuadro de diálogo, pero si lo hace en la cara de alguien en un entorno 3D, puede parecerse a que el diálogo se está metiendo en su camino. Los necesita para leer el mensaje, pero su instintiva es intentar salir de él. Esta reacción es excelente si está haciendo un juego, pero en una herramienta diseñada para el trabajo, es menor que ideal.

Después de probar algunas cosas diferentes, finalmente nos hemos decidido a usar un sistema de "burbuja de reflexión" para nuestros diálogos y se han agregado las tendenciaes que los usuarios pueden seguir hasta donde se necesita su atención en nuestra aplicación. También hemos realizado el pulso de tendrils, lo que implicaba una sensación de direccionalidad para que los usuarios sabían a dónde ir.

![El sistema de "burbuja de reflexión" incluía tendres de pulsación que proporcionaban una sensación de dirección, lo que conduce a los usuarios a dónde se necesitaba su atención en la aplicación.](images/thought-bubble-500px.jpg)

**¿Qué hemos aprendido?**

Es mucho más difícil en 3D alertar a los usuarios sobre las cosas a las que deben prestar atención. El uso de directores de atención, como [el sonido espacial,](../design/spatial-sound.md)los rayos de luz o las burbujas de reflexión, puede llevar a los usuarios a donde deben estar.

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a>Problema #3: A veces, otros hologramas pueden bloquear la interfaz de usuario

Hay ocasiones en las que un usuario desea interactuar con un holograma y sus controles de interfaz de usuario asociados, pero se les bloquea la vista porque hay otro holograma delante de ellos. Mientras desarrollamos el HoloStudio, hemos usado la prueba y el error para llegar a una solución para esto.

![Un control de interfaz de usuario asociado a un holograma se puede bloquear si hay otro holograma entre él y el usuario HoloLens.](images/ui-blocked-500px.jpg)

Intentamos acercar el control de interfaz de usuario al usuario para que no se bloqueara, pero descubrimos que no era cómodo para el usuario ver un control que estaba cerca de usted mientras miraba simultáneamente un holograma que estaba lejos. Sin embargo, si hemos movido el control delante del holograma más cercano al usuario, parece que se ha desasociado del holograma que debería estar afectando.

Por último, terminamos fantasmaando el control de interfaz de usuario y lo colocamos a la misma distancia del usuario que el holograma al que está asociado, por lo que ambos se sienten conectados. Esto permite al usuario interactuar con el control aunque se haya ocultado.

![La solución: hemos fantasmaado el control de la interfaz de usuario, que permitió la interacción con el control y hizo que se sincronizó conectado al holograma que estaba afectando.](images/ghosting-ui-500px.jpg)

**¿Qué hemos aprendido?**

Los usuarios deben poder acceder fácilmente a los controles de interfaz de usuario incluso si se han bloqueado, por lo que deben averiguar los métodos para asegurarse de que los usuarios puedan completar sus tareas independientemente de dónde estén sus hologramas en el mundo real.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><b>No hay más que una</b><br>Diseñador holográfico sr. @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también
* [Interacciones instintivas](../design/interaction-fundamentals.md)
