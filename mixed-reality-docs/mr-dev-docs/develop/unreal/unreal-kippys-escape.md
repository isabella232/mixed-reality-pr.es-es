---
title: La realización del escape de Kippy
description: Siga con nosotros a medida que exploramos la creación de la aplicación de realidad mixta de escape de Kippy para HoloLens 2 en el motor inreal.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: No real, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, implementación en dispositivo, PC, documentación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
appliesto:
- HoloLens 2
ms.openlocfilehash: df199b6a3215158e15fb1252dd75c58aea5bc2ab
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010045"
---
# <a name="the-making-of-kippys-escape"></a>La realización del escape de Kippy

Kippy el robot se reactiva para encontrarse en una isla. Es el usuario quien puede poner en marcha su solución de problemas para ayudarle a encontrar una ruta de acceso a su barco. Correa en HoloLens 2 y [Descargue la aplicación](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) desde el Microsoft Store o Clone el [repositorio](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) de Github y obtenga Kippy Home Safe.  

> [!IMPORTANT]
> Asegúrese de que está usando el **motor inreal 4,25 o posterior** si está compilando el escape de Kippy desde el repositorio de github.

El escape de Kippy es una aplicación de ejemplo de [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) de código abierto compilada con las herramientas inreal Engine 4 y [UX de realidad mixta](https://github.com/microsoft/MixedReality-UXTools-Unreal). En esta publicación, le guiaremos a través de nuestro proceso desde los primeros principios y el diseño visual hasta la implementación y optimización de la experiencia. Puede encontrar más información sobre el desarrollo de aplicaciones de realidad mixta con las herramientas de MRTK UX en la [información general sobre el desarrollo inreal](unreal-development-overview.md).

## <a name="first-principles"></a>Primeros principios 

En el establecimiento del escape de la creación de Kippy, nuestro objetivo era crear una experiencia que resaltara la [compatibilidad con hololens 2 del motor](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), las funcionalidades de hololens 2 y el kit de herramientas de realidad mixta. Queríamos inspirar a los desarrolladores a imaginar lo que podían crear con Unreal y HoloLens 2.  

Contamos con tres principios de GUID para la experiencia: que necesitaba ser divertido, interactivo y tener una barrera baja para entrar. Queremos que la experiencia sea lo suficientemente intuitiva como para que incluso un usuario de realidad mixta de primera hora no necesite un tutorial para pasar por él.  

## <a name="designing-the-game"></a>Diseñar el juego 

HoloLens 2 tiene acceso a las características de diseño que se encuentran en ningún otro momento en juegos. Los objetos se pueden insertar o manipular directamente con las manos o destinadas al seguimiento ocular. Estas características clave están detrás de algunos de los momentos divertidos que creamos en el escape de Kippy.  

Mediante el uso de las características únicas de HoloLens 2 como guía para nuestro diseño de juego, nos centramos en unos pocos escenarios de entornos pequeños. Las islas tienen sentido porque se pueden ajustar para diferentes alturas del reproductor y proporcionan algunas ideas de puente entretenido. Nos hemos desembarcado en el tema de las civilizacións de los ancianos, con la idea de que alguien había creado maquinaria a lo largo de un consumo de energía extraño proporcionado por cada isla. Cada una de las islas tenía su propio aspecto y funcionamiento, un detalle que ayudó a crear el interés visual. Un buen equilibrio entre el modelado y la texturización sería que las llamadas de dibujo bajaran para el rendimiento de la representación, por lo que una mirada estilizada se diseñó pensando en ello. 

![El diseño de juego temprano esboza ](images/kippys-escape/kippys-escape-img-01.png)
 *algunos bocetos tempranos sobre el aspecto que podría tener la experiencia*

![Representación de la segunda ](images/kippys-escape/kippys-escape-img-02.png)
 *representación de la isla de la segunda isla*

Para mantenerse dentro de nuestra breve programación de producción, aceptamos que un carácter flotante podría capturar la intención y la emoción sin ciclos de animación rigurosos. Y, por tanto, Kippy nació. Emotes algunas expresiones diferentes a través de sus ojos y a través de efectos sonoros vocales mínimos para ayudar a guiar al jugador a lo largo de la experiencia. 

![Kippy que muestra diferentes expresiones a través de sus ojos](images/kippys-escape/kippys-escape-img-03.gif)

*Kippy que muestra diferentes expresiones a través de sus ojos*

![Si el usuario tarda demasiado tiempo en resolver un rompecabezas, Kippy proporcionará al usuario una sugerencia](images/kippys-escape/kippys-escape-img-04.gif)

*Si el usuario tarda demasiado tiempo en resolver un rompecabezas, Kippy proporcionará al usuario una sugerencia*

Más allá del diseño de caracteres y entornos, hemos realizado un esfuerzo concertado para que el juego sea divertido. El seguimiento ocular nos permitió activar los atributos de material y sonido, que destacan las piezas clave del juego. El audio espacial ayudó a que los niveles se sientan en casa en el entorno del jugador. Poder captar objetos, presionar botones y manipular los controles deslizantes impulsa las nuevas contrataciones de los jugadores. Era importante asegurarse de que estos puntos de conexión se sentían naturales. 

![El final del cable del puente se ilumina cuando el usuario se acerca a él](images/kippys-escape/kippys-escape-img-05.gif)

*El final del cable del puente se ilumina cuando el usuario se acerca a él*

## <a name="building-the-game-mechanics"></a>Crear la mecánica de juego 

El escape de Kippy se basa en gran medida en los componentes de las herramientas de la experiencia de usuario de realidad mixta para que los actores de interacción con nombre interactivo de juego, controles de límites, manipuladores, controles deslizantes y botones.   

El [actor de interacción a mano](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) permite la manipulación directa y lejana de los hologramas. Al principio del escape de Kippy, el usuario tiene la oportunidad de establecer la ubicación del juego. Los haces de mano que se extienden desde la palmera del usuario facilitan la manipulación de hologramas grandes, tal como se muestra en el GIF siguiente.  

![GIF de interacción de mano de actor](images/kippys-escape/kippys-escape-img-06.gif)

La propia escena de marcador de posición se puede arrastrar y girar mediante el componente de [control de límites](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) de las herramientas de la experiencia del usuario.  

En la segunda isla, el usuario debe recoger las gemas y colocarlas en sus ranuras coincidentes. Las gemas tienen [manipuladores](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) asociados que permiten al usuario seleccionarlos y colocarlos. 

![GIF de ejemplo de manipulador](images/kippys-escape/kippys-escape-img-07.gif)

Un [botón](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) que se pueda presionar es la clave para abrir bombas para su uso en la tercera isla.  

![GIF de ejemplo de botón que se ha presionado](images/kippys-escape/kippys-escape-img-08.gif)

Un componente de [control deslizante](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) aparece en la cuarta isla, lo que desencadena el último puente que se va a generar.  

![GIF de ejemplo de componente de control deslizante](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimización de HoloLens 2 

Con cualquier experiencia creada para ejecutarse en un dispositivo móvil, es fundamental vigilar el rendimiento. Unreal 4,25 incluye una actualización importante para la compatibilidad con varias vistas móviles, lo que reduce significativamente la sobrecarga de representación y aumenta la velocidad de fotogramas. Le recomendamos que Compruebe nuestra otra [configuración de rendimiento recomendada](performance-recommendations-for-unreal.md) para el desarrollo de HoloLens 2 con inreal cuando esté optimizando.  

Los objetos de física siguen siendo costosos por el rendimiento, por lo que se usaron algunas soluciones de Clever. Por ejemplo, el tercer "puente" requiere apagar algunos residuos que bloquean la escalera. En lugar de tener una fuerza que afecte a las piedras como objetos de física, la detonación de bomba desencadena un intercambio y cambia las piedras estáticas de un efecto de partículas de explosión. 

![Ejemplo optimizado para archivo GIF de HoloLens 2](images/kippys-escape/kippys-escape-img-10.gif) 

También se reducen las llamadas a Draw de más de 400 a ~ 260 por: 
* Reducir la complejidad de la malla
* Combinación de mallas
* Quitar algunos de nuestros elementos de iluminación dinámica iniciales

Aunque es probable que podamos haber hecho algo más, pensamos que era un buen equilibrio entre el rendimiento y la calidad visual.  

## <a name="try-it-out"></a>Haga la prueba 

Arranque HoloLens 2 y [Descargue](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) la aplicación desde el Microsoft Store, o bien Clone el [repositorio](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) desde Github y compile la aplicación usted mismo.  

## <a name="about-the-team"></a>Acerca del equipo

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Acento anticircunflejo</b><br><i>Diseñador de juegos principales</i><br>Jack actualmente funciona en experiencias de realidad mixta para Microsoft, incluidos los proyectos de HoloLens 2 y AltspaceVR, y antes era un diseñador en el equipo de la plataforma HoloLens.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Verano de Wu</b><br><i>Productor</i><br>El verano funciona en la plataforma de desarrollo de la realidad mixta y se centra en los esfuerzos inreales relacionados con el motor del equipo.</td>
</tr>
</table>

Gracias por nuestros amigos en [Framestore](https://www.framestore.com/) para ayudarnos a poner el escape de Kippy a la vida. Desde el desarrollo de caracteres hasta el diseño de activos hasta la programación de juegos, su colaboración en este proyecto era dinámica.  