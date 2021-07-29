---
title: La realización del escape de Asínpy
description: Siga con nosotros mientras exploramos la realización de la aplicación escape mixed reality de Vapy para HoloLens 2 en Unreal Engine.
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, deploy to device, PC, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
appliesto:
- HoloLens 2
ms.openlocfilehash: 353df2f2f5bc9a1d70fc354fd3014f10c0ba95d9
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757122"
---
# <a name="the-making-of-kippys-escape"></a>La realización de Escape de Asínpy
![Imagen de escape de Escape hero dePy](images/KippysEscape_1920.jpg)

Py el robot se reactiva para encontrarse en una isla. Depende de usted ponerse en su casco de solución de problemas para ayudarle a encontrar un camino de vuelta a su cohete. Sujete el HoloLens 2 [](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) y descargue la aplicación desde la [](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) Microsoft Store o clone el repositorio desde GitHub y haga que El hogar dePy sea seguro.  

> [!IMPORTANT]
> Asegúrese de que usa **Unreal Engine 4.25** o una versión posterior si va a compilar Escape de Asínpy desde el repositorio de GitHub.

Escape dePy es una aplicación [](/hololens/hololens2-hardware) de ejemplo de HoloLens 2 código abierto creada con Unreal Engine 4 y [Mixed Reality UX Tools para Unreal.](https://github.com/microsoft/MixedReality-UXTools-Unreal) En esta publicación, le llevamos por el proceso desde los primeros principios y el diseño visual hasta la implementación y optimización de la experiencia. Puede encontrar más información sobre el desarrollo de aplicaciones Mixed Reality con herramientas de experiencia de usuario de MRTK en la introducción [al desarrollo de Unreal](unreal-development-overview.md).

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Descarga de la aplicación Microsoft Store en HoloLens 2
Si tiene un HoloLens 2, puede descargar e instalar directamente la aplicación en el dispositivo.

<a href='//www.microsoft.com/store/apps/9nbd7gl86vkd?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="first-principles"></a>Primeros principios 

Al establecer la creación de escape de Finpy, nuestro objetivo era crear una experiencia que resaltara la compatibilidad con HoloLens 2 de [Unreal Engine,](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)las funcionalidades de HoloLens 2 y la Mixed Reality Toolkit. Queríamos inspirar a los desarrolladores a imaginar lo que podían crear con Unreal y HoloLens 2.  

Se han ideado tres principios rectores para la experiencia: que era necesario ser divertido, interactivo y tener una barrera baja para la entrada. Queríamos que la experiencia fuera lo suficientemente intuitiva como para que incluso un usuario de realidad mixta por primera vez no necesite un tutorial para realizarla.  

## <a name="designing-the-game"></a>Diseño del juego 

El HoloLens 2 tiene acceso a características de diseño que se encuentran en otras partes de los juegos de hoy en día. Los objetos se pueden insertar o manipular directamente con las manos o dirigidos con el seguimiento de los ojos. Estas características clave están detrás de algunos de los momentos divertidos que se han creado en Escape deImospy.  

Mediante el uso de HoloLens 2 características únicas como guía para nuestro diseño de juegos, hemos limitado algunos escenarios de entorno pequeños. Las islas tienen sentido porque se pueden ajustar para diferentes alturas de jugador y proporcionan algunas ideas de puente interesantes. Hemos empezado a trabajar en el tema de la ciencia de la ciencia y la ciencia de la ciencia, con la idea de que alguien había construido maquinaria sobre los terrenos aprovechando una energía extraña proporcionada por cada isla. Cada una de las islas recibió su propia apariencia, un detalle que ayudó a crear interés visual. Un buen equilibrio entre el modelado y la texturización mantenería las llamadas a draw bajas para el rendimiento de la representación, por lo que se diseñó una apariencia con este aspecto en mente. 

![Primeros bocetos de diseño de juegos ](images/kippys-escape/kippys-escape-img-01.png)
 *Algunos bocetos iniciales para el aspecto que podría tener la experiencia*

![Representaciones de la segunda isla ](images/kippys-escape/kippys-escape-img-02.png)
 *Representaciones de la segunda isla*

Para mantener la programación de producción corta, hemos acordado que un carácter flotante podría capturar intenciones y emociones sin ciclos de animación rigurosos. ¡Y así ha nado Así que Hapy ha nado! Se degradan algunas expresiones diferentes a través de los ojos y a través de efectos de sonido faciales sintrónicos para ayudar a guiar al jugador a lo largo de la experiencia. 

![Py mostrando diferentes expresiones a través de sus ojos](images/kippys-escape/kippys-escape-img-03.gif)

*Py mostrando diferentes expresiones a través de sus ojos*

![Si el usuario tarda demasiado tiempo en resolver un problema,Certpy le dará una sugerencia.](images/kippys-escape/kippys-escape-img-04.gif)

*Si el usuario tarda demasiado tiempo en resolver un problema,Certpy le dará una sugerencia.*

Más allá del diseño de caracteres y entornos, hicimos un esfuerzo conjunto para que el juego se sintase divertido. El seguimiento de los ojos nos permitió desactivar los atributos de material y sonido, que resaltaban partes clave del juego. El audio espacial ayudó a que los niveles se sintase como en casa en el entorno del reproductor. La capacidad de agarrar objetos, presionar botones y manipular controles deslizantes impulsa interacciones innovadoras del jugador. Era importante asegurarse de que estos puntos de conexión se encontraban naturales. 

![El final del cable del puente se brilló cuando la mano del usuario se aproxima a él.](images/kippys-escape/kippys-escape-img-05.gif)

*El final del cable del puente se brilló cuando la mano del usuario se aproxima a él.*

## <a name="building-the-game-mechanics"></a>Creación de la mecánica del juego 

Escape dePy se basa en gran medida en los componentes de UX Tools de Mixed Reality para que el juego sea interactivo, es decir, actores de interacción con las manos, controles de límites, manipuladores, controles deslizantes y botones.   

El [actor de interacción con la mano](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) permite la manipulación directa y lejana de hologramas. Al principio de Escape de Chancepy, el usuario tiene la oportunidad de establecer la ubicación del juego. Los haces de mano que se extienden desde la mano del usuario hacen que sea fácil manipular hologramas grandes que están lejos, como se ve en el gif siguiente.  

![Gif de actor de interacción con la mano](images/kippys-escape/kippys-escape-img-06.gif)

La propia escena de marcador de posición se puede arrastrar y girar mediante el componente de [control de límites](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/BoundsControl.html) de herramientas de UX.  

En la segunda isla, el usuario debe recoger las gemas y colocarlas en sus ranuras correspondientes. Las gemas tienen [manipuladores asociados](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html) que permiten al usuario recogerlas y colocarlas. 

![Gif de ejemplo del manipulador](images/kippys-escape/kippys-escape-img-07.gif)

Un [botón que se puede](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html) presionar es la clave para poner en marcha los hadas para su uso en la tercera isla.  

![Gif de ejemplo de botón presionable](images/kippys-escape/kippys-escape-img-08.gif)

Aparece [un](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PinchSlider.html) componente deslizante en la cuarta isla, lo que desencadena el puente final que se va a generar.  

![Gif de ejemplo de componente de control deslizante](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a>Optimización para HoloLens 2 

Con cualquier experiencia creada para ejecutarse en un dispositivo móvil, es fundamental estar atento al rendimiento. Unreal 4.25 incluye una actualización importante para admitir la vista múltiple móvil, lo que reduce significativamente la sobrecarga de representación y aumenta la velocidad de fotogramas. Se recomienda consultar la otra configuración [de rendimiento recomendada](performance-recommendations-for-unreal.md) para HoloLens 2 desarrollo con Unreal al optimizar.  

Los objetos físicos siguen siendo costosos para el rendimiento, por lo que se usaron un par de soluciones alternativas inteligentes. Por ejemplo, el tercer "puente" requiere la acumulación de algunos bloqueos que bloquean el sitio. En lugar de tener una fuerza que afecta a los rayos como objetos físicos, la detonación de la bomba desencadena un intercambio, cambiando la estática por un efecto de partícula en expansión. 

![Ejemplo optimizado para HoloLens 2 gif](images/kippys-escape/kippys-escape-img-10.gif) 

También se reducen las llamadas a draw de más de 400 a ~260 por: 
* Reducción de la complejidad de la malla
* Combinación de mallas
* Eliminación de algunos de nuestros elementos de iluminación dinámica iniciales

Aunque es probable que haya más cosas que podríamos haber hecho, creemos que era un buen equilibrio entre el rendimiento y la calidad visual.  

## <a name="try-it-out"></a>Haga la prueba 

Arranque el HoloLens 2 y [](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) descargue la aplicación desde el Microsoft Store, [](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) o bien clone el repositorio desde GitHub y compile la aplicación usted mismo.  

## <a name="about-the-team"></a>Acerca del equipo

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Diseñador de juegos principal</i><br>Actualmente, Jack trabaja en Mixed Reality experiencias para Microsoft, incluidos los proyectos de HoloLens 2 y AltspaceVR, y anteriormente era diseñador del equipo de HoloLens plataforma.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Wu de verano</b><br><i>Productor</i><br>El verano trabaja en la plataforma de desarrolladores de realidad mixta y dirige los esfuerzos relacionados con Unreal Engine del equipo.</td>
</tr>
</table>

Gracias especial a nuestros amigos de [Framestore](https://www.framestore.com/) por ayudarnos a dar vida a Escape dePy. Desde el desarrollo de caracteres hasta el diseño de recursos, hasta la programación de juegos, su colaboración en este proyecto fue fundamental.