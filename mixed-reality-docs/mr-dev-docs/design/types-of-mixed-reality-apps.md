---
title: Tipos de aplicaciones de realidad mixta
description: Obtenga información sobre las experiencias admitidas por la plataforma Mixed Reality, desde entornos envolventes hasta la capa de información ligera sobre el entorno de un usuario.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, patrones de aplicación, cascos de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, HoloLens
ms.openlocfilehash: 13d4f538148b2c6b6f4df422c6c423f2b2710ca1ba2d98fe4f952c14284035f8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218932"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicaciones de realidad mixta

Una de las ventajas del desarrollo de aplicaciones para Windows Mixed Reality es el espectro de experiencias que la plataforma puede admitir. Desde entornos virtuales totalmente envolventes hasta la disposición en capas de información de iluminación en el entorno actual de un usuario, Windows Mixed Reality proporciona un sólido conjunto de herramientas para convertir cualquier experiencia en realidad. Es importante que un creador de aplicaciones comprenda al principio de su proceso de desarrollo dónde se encuentra su experiencia a lo largo de este espectro. En última instancia, esta decisión afectará tanto al diseño de aplicaciones como a la ruta tecnológica para el desarrollo.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicaciones de entorno mejoradas (HoloLens solo)

Una de las formas más eficaces que la realidad mixta puede aportar valor es permitir que los desarrolladores coloquen información digital o contenido en el entorno actual de un usuario. Este enfoque es popular para las aplicaciones en las que la ubicación contextual del contenido digital en el mundo real es fundamental y mantener el entorno real del usuario "presente" durante su experiencia es clave. Los usuarios también pueden moverse fácilmente entre tareas digitales del mundo real. Esto presta aún más crédito a la promesa de que las aplicaciones de realidad mixta que ve el usuario son realmente una parte de su entorno.

![Aplicaciones de entorno mejoradas](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno mejoradas*

**Usos de ejemplo**
* Una aplicación de estilo bloc de notas de realidad mixta que permite a los usuarios crear y colocar notas en su entorno
* Una aplicación de televisión de realidad mixta colocada en un lugar cómodo para ver
* Una aplicación de cocina de realidad mixta colocada encima de la isla de la cocina para ayudar a una tarea de cocina
* Una aplicación de realidad mixta que ofrece a los usuarios la sensación de "visión de rayos X" (es decir, un holograma colocado encima de e imita un objeto del mundo real, al tiempo que permite al usuario ver "dentro de él" holográficamente)
* Anotaciones de realidad mixta colocadas en toda una fábrica para proporcionar la información necesaria del trabajador
* Búsqueda de forma de realidad mixta en un espacio de oficina
* Experiencias de tabla de realidad mixta (es decir, experiencias de estilo de juego de mesa)
* Aplicaciones de comunicación de realidad mixta como Skype

## <a name="blended-environment-apps"></a>Aplicaciones de entorno combinado

Dada Windows Mixed Reality capacidad de reconocer y asignar el entorno del usuario, es capaz de crear una capa digital que se puede superlair en el espacio del usuario. La capa fina respeta la forma y los límites del entorno del usuario, pero la aplicación puede optar por transformar determinados elementos más adecuados para inmersar al usuario en la aplicación. Esto se denomina aplicación de entorno combinado. A diferencia de una aplicación de entorno mejorada, las aplicaciones de entorno combinados solo pueden ocuparse lo suficiente del entorno para usar mejor su comodidad para fomentar el comportamiento específico del usuario (por ejemplo, fomentar el movimiento o la exploración) o reemplazar elementos por cambios (se desenlazada un contador de cocina para mostrar un patrón de mosaico diferente). Este tipo de experiencia puede incluso transformar un elemento en un objeto completamente diferente, pero mantener las dimensiones aproximadas del objeto como base (una isla de cocina se transforma en un contenedor de contenedores para un juego delictivo).

![Aplicaciones de entorno combinado](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno combinado*

**Usos de ejemplo**
* Una aplicación de diseño interior de realidad mixta que puede pintar paredes, contracarros o plantas con diferentes colores y patrones
* Una aplicación de realidad mixta que permite a un diseñador de automoción crear nuevas iteraciones de diseño para una próxima actualización de automóvil sobre un automóvil existente
* Una habitación está "cubierta" y reemplazada por un puesto de árboles de realidad mixta en un juego para niños
* Un escritorio está "cubierto" y reemplazado por un contenedor de realidad mixta en un juego delictivo
* Un poste de suspensión está "cubierto" y se reemplaza por un signo que usa aproximadamente la misma forma y dimensión
* Una aplicación que permite a los usuarios hacer huecos en sus paredes reales o envolventes, que revelan un mundo mágico

## <a name="immersive-environment-apps"></a>Aplicaciones de entorno inmersivo

Las aplicaciones de entorno inmersivo se centra en un entorno que cambia completamente el mundo del usuario y puede colocarlas en un espacio y un tiempo diferentes. Estos entornos pueden ser reales, creando experiencias envolventes y emocionantes que solo están limitadas por la imaginación del creador de la aplicación. A diferencia de las aplicaciones de entorno combinado, una vez que Windows Mixed Reality identifica el espacio del usuario, una aplicación de entorno envolvente puede ignorar totalmente el entorno actual del usuario y reemplazarlo por uno propio. Estas experiencias también pueden separar el tiempo y el espacio, lo que significa que un usuario podría recorrer las calles de Rome en una experiencia envolvente, mientras permanece relativamente todavía en su espacio real. Es posible que el contexto del entorno real no sea importante para una aplicación de entorno envolvente.

![Aplicaciones de entorno inmersivo](images/windows-mixed-reality-640px.jpg)<br>
*Aplicaciones de entorno inmersivo*

**Usos de ejemplo**
* Una aplicación inmersiva que permite a un usuario recorrer un espacio independiente del suyo propio (es decir, recorrer un edificio famoso, un paseo por un paseo por la ciudad popular).
* Una aplicación inmersiva que orquesta un evento o escenario en torno al usuario (es decir, un partido o un rendimiento).

## <a name="see-also"></a>Consulta también

* [Introducción al desarrollo](../develop/development.md)
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
