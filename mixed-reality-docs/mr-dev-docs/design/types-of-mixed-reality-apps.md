---
title: Tipos de aplicaciones de realidad mixta
description: Obtenga información sobre las experiencias admitidas por la plataforma de realidad mixta, desde entornos inmersivo hasta la distribución de información a través del entorno de un usuario.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, patrones de aplicaciones, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens
ms.openlocfilehash: 795d8733b9f509a79d9429f75dff2f88a2a63c93
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007625"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicaciones de realidad mixta

Una de las ventajas de desarrollar aplicaciones para Windows Mixed Reality es el espectro de experiencias que la plataforma puede admitir. Desde entornos virtuales totalmente envolventes hasta la disposición en capas de información de iluminación en el entorno actual de un usuario, Windows Mixed Reality proporciona un sólido conjunto de herramientas para convertir cualquier experiencia en realidad. Es importante que un creador de aplicaciones entienda pronto en su proceso de desarrollo en cuanto a la ubicación de este espectro. Esta decisión afectará en última instancia a la composición del diseño de la aplicación y a la ruta tecnológica para el desarrollo.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicaciones de entorno mejoradas (solo HoloLens)

Una de las formas más eficaces en las que la realidad mixta puede aportar valor es permitir que los desarrolladores coloquen información o contenido digital en el entorno actual de un usuario. Este enfoque es popular para las aplicaciones en las que la ubicación contextual del contenido digital en el mundo real es primordial y mantener el entorno real del usuario "presente" durante su experiencia es clave. Los usuarios también pueden moverse con facilidad entre tareas digitales reales. Esto presta más credibilidad a la promesa de que las aplicaciones de realidad mixta que ve el usuario realmente forman parte de su entorno.

![Aplicaciones de entorno mejoradas](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno mejoradas*

**Ejemplo se usa**
* Una aplicación de estilo de Bloc de notas de realidad mixta que permite a los usuarios crear y colocar notas en torno a su entorno
* Una aplicación de televisión de realidad mixta colocada en un lugar cómodo para ver
* Una aplicación de cocina de realidad mixta colocada sobre la isla de cocina para ayudar a una tarea de cocina
* Una aplicación de realidad mixta que ofrece a los usuarios la sensación de "x-Ray Vision" (es decir, un holograma colocado encima de y imita un objeto del mundo real, a la vez que permite al usuario ver "dentro de ti" de manera holográfica)
* Anotaciones de realidad mixta colocadas en una fábrica para proporcionar la información necesaria del trabajador
* La realidad mixta es encontrar en un espacio de oficina
* Experiencias de sobremesa de realidad mixta (es decir, experiencias de estilo de juego de tablero)
* Aplicaciones de comunicación de realidad mixta como Skype

## <a name="blended-environment-apps"></a>Aplicaciones de entorno mixtas

Dada la capacidad de Windows mixed reality de reconocer y asignar el entorno del usuario, es capaz de crear una capa digital que se puede superponer en el espacio del usuario. El nivel fino respeta la forma y los límites del entorno del usuario, pero la aplicación puede optar por transformar determinados elementos que mejor se adapten para sumergir al usuario en la aplicación. Esto se denomina aplicación de entorno combinada. A diferencia de las aplicaciones de entorno mejoradas, las aplicaciones de entorno combinadas solo pueden ser suficientes para el entorno para usar mejor su composición con el fin de animar el comportamiento de un usuario específico (por ejemplo, para fomentar el movimiento o la exploración) o mediante la sustitución de elementos con cambios (un contador de cocina está desollado para mostrar un patrón de mosaico diferente). Este tipo de experiencia puede incluso transformar un elemento en un objeto totalmente diferente, pero seguir manteniendo las dimensiones aproximadas del objeto como su base (una isla de cocina se transforma en un contenedor para un juego de un emocionante delito).

![Aplicaciones de entorno mixtas](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno mixtas*

**Ejemplo se usa**
* Una aplicación de diseño interior de realidad mixta que puede pintar paredes, contrapartes o plantas en diferentes colores y patrones
* Una aplicación de realidad mixta que permite a un diseñador de automóviles crear capas de nuevas iteraciones de diseño para una próxima actualización del automóvil sobre un automóvil existente
* Una cama está "estudiada" y se reemplaza por un stand de realidad mixta del juego de niños
* Un servicio de escritorio está "Tratado" y se reemplaza por un contenedor de realidad mixta en un juego de un emocionante delito
* Una linterna colgante está "tratada" y se reemplaza por el indicador con la misma forma y dimensión.
* Una aplicación que permite a los usuarios sacudir agujeros en sus muros mundiales reales o envolventes, lo que revela un mundo mágico.

## <a name="immersive-environment-apps"></a>Aplicaciones de entorno inmersivo

Las aplicaciones de entorno inmersivo se centran en torno a un entorno que cambia completamente el mundo del usuario y puede colocarlas en un espacio y una hora distintos. Estos entornos pueden sentir real y crear experiencias envolventes y emocionantes que solo están limitadas por la imaginación del creador de la aplicación. A diferencia de las aplicaciones de entorno mixtas, una vez que Windows Mixed Reality identifica el espacio del usuario, una aplicación de entorno inmersivo puede descartar completamente el entorno actual del usuario y reemplazar las existencias por una sola. Estas experiencias también pueden separar el tiempo y el espacio, lo que significa que un usuario podría recorrer las calles de Roma en una experiencia envolvente, a la vez que permanece relativamente en su espacio real. Es posible que el contexto del entorno real no sea importante para una aplicación de entorno envolvente.

![Aplicaciones de entorno inmersivo](images/windows-mixed-reality-640px.jpg)<br>
*Aplicaciones de entorno inmersivo*

**Ejemplo se usa**
* Una aplicación envolvente que permite a un usuario retrasar un espacio independiente de su propia (es decir, recorrer un famoso edificio, Museo, ciudad popular)
* Una aplicación envolvente que organiza un evento o escenario alrededor del usuario (es decir, una batalla o un rendimiento)

## <a name="see-also"></a>Consulta también

* [Introducción al desarrollo](../develop/development.md)
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
