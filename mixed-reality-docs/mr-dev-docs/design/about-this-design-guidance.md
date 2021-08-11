---
title: Acerca de esta guía de diseño
description: Microsoft ha creado esta guía para diseñadores, desarrolladores, administradores de programas e investigadores, cuyo trabajo abarca dispositivos holográficos (por ejemplo, HoloLens) y envolventes (por ejemplo, los cascos Windows Mixed Reality de Acer y HP).
author: mrwied
ms.author: jonwie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, introducción, guía, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, experiencia de usuario, recursos
ms.openlocfilehash: 0bd70e08d55f8d556ff3a612dbbc979dc895cebbfc9950f18d8d474ff347407b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198682"
---
# <a name="about-this-design-guidance"></a>Acerca de esta guía de diseño

## <a name="introduction"></a>Introducción

**Hola, y le damos la bienvenida a sus instrucciones de diseño para la realidad mixta.**

Esta guía está escrita por diseñadores, desarrolladores, administradores de programas e investigadores de Microsoft. El trabajo de nuestros escritores abarca dispositivos holográficos, incluidos HoloLens, dispositivos envolventes y cascos de Windows Mixed Reality HP. Se recomienda pensar en este artículo como un conjunto de temas para Windows diseño montado con la cabeza.

Vamos a entrar en una nueva era de computación enormemente interesante junto con usted. Los avances en las pantallas montadas en la cabeza, el sonido espacial, los sensores, el reconocimiento del entorno, la entrada y los gráficos 3D nos llevan a definir nuevos tipos de experiencias. La nueva frontera es mucho más personal, intuitiva, envolvente y contextual.

Siempre que sea posible, ofreceremos instrucciones de diseño prácticas con código relacionado en GitHub. Dicho esto, dado que estamos aprendiendo junto con usted, no siempre podemos ofrecer instrucciones específicas y prácticas aquí. Algunas de las cosas que compartimos estarán en el camino de "lecciones que hemos aprendido" y "evitar seguir por ese camino".

Y sabemos que la comunidad de diseño más grande generará muchas innovaciones. Por lo tanto, esperamos tener noticias de usted, aprender de usted y trabajar estrechamente con usted. Haremos todo lo posible para compartir nuestra información, incluso si son exploratorias y tempranas. Nuestro objetivo es ayudar a los desarrolladores y diseñadores con sus ideas de diseño, procedimientos recomendados y los controles de código abierto, patrones y aplicaciones de ejemplo relacionados que puede usar directamente en su propio trabajo.

## <a name="overview"></a>Información general

Esta es una introducción rápida de cómo se organiza esta guía de diseño:

* **[Información](design.md)** general: obtenga información sobre el proceso de diseño, los conceptos básicos y los factores de interacción que se deben tener en cuenta.
* **[Conceptos básicos:](core-concepts-landingpage.md)** obtenga información sobre la comodidad, el marco holográfico, la asignación espacial y otros conceptos básicos que se deben tener en cuenta.
* **[Modelos de interacción:](interaction-fundamentals.md)** esta guía se estructura en torno a tres modelos de interacción principales.
* **[Elementos de la experiencia de](app-patterns-landingpage.md)** usuario: use controles y comportamientos como bloques de creación para crear su propia experiencia de aplicación.
* **[Recursos:](design.md#choose-a-prototyping-option)** inicie el proyecto con herramientas de diseño y opciones de creación de prototipos.

Para todo lo anterior, nuestro objetivo es ofrecer la combinación adecuada de texto, ilustraciones y vídeos. Nos verá experimentando con diferentes formatos y técnicas, todo ello con la intención de entregar lo que necesita. Y en los próximos meses, ampliaremos esta taxonomía para incluir un conjunto más amplio de temas de diseño. Siempre que sea posible, le proporcionaremos información sobre lo que viene a continuación, así que siga comprobando.

## <a name="objectives"></a>Objetivos

Este es un vistazo rápido a algunos objetivos de alto nivel que están guiando este trabajo para que pueda comprender de dónde viene.

### <a name="help-solve-customer-challenges"></a>Ayudar a resolver los desafíos de los clientes

![Ayudar a resolver los desafíos de los clientes](images/500px-fix-a-broken-switch-with-hololens.jpg) <br>

Somos conscientes de muchos de los mismos problemas que usted, y comprendemos lo difícil que es su trabajo. Es interesante explorar y definir una nueva frontera... y también puede ser desalentador. Se están replanteados paradigmas y prácticas antiguos, los clientes necesitan nuevas experiencias y hay mucho potencial para la innovación. Dado que queremos que este trabajo sea lo más completo posible, va más allá de una guía de estilo. Nuestro objetivo es ofrecer un conjunto completo de instrucciones de diseño que cubren la interacción de la realidad mixta, los comandos, la navegación, la entrada y el estilo, todo ello en base a escenarios y comportamientos humanos. 

### <a name="point-the-way-towards-a-new-more-human-way-of-computing"></a>Apuntar hacia una forma de computación nueva y más humana

![Apuntar hacia una forma de computación nueva y más humana](images/500px-man-and-women-with-holograph-on-table.png)<br>

Aunque es importante centrarse en problemas específicos de los clientes, también queremos presionarnos para ofrecer más. Creemos que un diseño excelente no es "solo" la resolución de problemas, sino también una manera de activar significativamente la evolución humana. Las nuevas formas de comportamiento humano, relaciones, actividades y entornos humanos impulsan nuestra innovación. Queremos que nuestras instrucciones reflejen también todas estas formas de pensar más a la vez. 

### <a name="meet-creators-where-they-are"></a>Conocer a los creadores en los que se encuentran

![Conocer a los creadores en los que se encuentran](images/500px-creators.jpg) <br>

Esperamos que muchas audiencias encuentren esta guía útil. Tiene conjuntos de aptitudes diferentes (inicial, intermedio, avanzado), usa distintas herramientas (Unity, DirectX, C++, C#, otras), está familiarizado con varias plataformas (Windows, iOS, Android), procede de distintos orígenes (móvil, empresa, juegos) y trabaja en equipos de diferentes tamaños (solo, pequeño, mediano, grande). Por lo tanto, esta guía se puede ver con diferentes perspectivas y necesidades. Siempre que sea posible, intentaremos tener en cuenta esta diversidad y hacer que nuestra guía sea lo más relevante posible para tantas personas como sea posible. Sabemos que muchos de los usuarios ya están GitHub. Por lo tanto, nos vincularemos directamente a GitHub y foros para que se reúnan con usted donde ya está. 

### <a name="share-as-much-as-possible-from-experimental-to-explicit"></a>Compartir tanto como sea posible, de experimental a explícito

![Compartir tanto como sea posible, de experimental a explícito](images/500px-man-playinggame.jpg) <br>

Uno de los desafíos de ofrecer instrucciones de diseño en este nuevo medio 3D es que no siempre tenemos instrucciones definitivas para ofrecer. Al igual que usted, estamos aprendiendo, experimentando, prototipando, resolviendo problemas y ajustando a medida que nos encontramos con obstáculos. En lugar de esperar un momento futuro mético en el que todo se haya descubierto, nuestro objetivo es compartir nuestro pensamiento con usted en tiempo real, aunque no sea concluyente. Nuestro objetivo final es ser definitiva siempre que podamos, proporcionando una guía de diseño clara y flexible vinculada al código de código abierto y que sea útil en las herramientas de desarrollo y diseño de Microsoft. Pero llegar a ese punto requiere muchas rondas de iteración y aprendizaje. Queremos interactuar con usted y aprender con usted a lo largo del proceso. Haremos todo lo posible por compartir a medida que vamos, incluso con nuestras cosas que son experimentales. 

### <a name="the-right-balance-of-global-and-local-design"></a>Equilibrio correcto del diseño global y local

![Equilibrio correcto del diseño global y local](images/500px-fluentdesign.jpg) <br>

Ofreceremos dos niveles de guía de diseño: global y local. Nuestra guía de diseño "global" se incluye en [el Sistema Fluent Design](https://fluent.microsoft.com). Fluent detalles sobre los aspectos básicos como la luz, la profundidad, el movimiento, el material y la escala en todo el diseño de Microsoft: nuestros dispositivos, productos, herramientas y servicios. Dicho esto, existen diferencias significativas específicas del dispositivo en este sistema más grande. Por lo tanto, nuestra guía de diseño "local" para pantallas montadas en la cabeza describe el diseño para dispositivos holográficos y envolventes que a menudo tienen diferentes métodos de entrada y salida y diferentes necesidades y escenarios del usuario. La guía de diseño local trata temas únicos de LOS HMD. Por ejemplo: objetos y entornos 3D; entornos compartidos; el uso de sensores, seguimiento de los ojos y asignación espacial; y las oportunidades de audio espacial. A lo largo de nuestra guía, es probable que vea que nos referimos a estos aspectos globales y locales. Esperamos que esto le ayude a reducir el trabajo en una base de diseño más grande, al tiempo que aprovecha las diferencias de diseño entre dispositivos específicos.

### <a name="have-a-discussion"></a>Tener una discusión

![Tener una discusión](images/500px-share.jpg) <br>

Lo más importante es que queremos interactuar con usted, la comunidad de desarrolladores y diseñadores holográficos y envolventes, para definir esta nueva y emocionante era de diseño. Como se mencionó anteriormente, sabemos que no tenemos todas las respuestas. Por eso creemos que muchas soluciones e innovaciones interesantes procederán de usted. Nuestro objetivo es estar abiertos y disponibles para conocerlos, hablar con usted en línea y en eventos, y agregar valor siempre que podamos. Estamos encantados de formar parte de esta increíble comunidad de diseño, que se lanza a una experiencia juntos. 

## <a name="dive-in"></a>Profundizar

Esperamos que este artículo introductorio proporciona algún contexto significativo a medida que explora nuestra guía de diseño. Prométenos y háganos saber sus opiniones en los foros de GitHub que encontrará vinculados en nuestros artículos, o en Microsoft Design en [Twitter](https://twitter.com/MicrosoftDesign) y [Facebook.](https://www.facebook.com/microsoftdesign/) Vamos a diseñar conjuntamente el futuro.
