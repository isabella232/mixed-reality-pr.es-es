---
title: Empezar a diseñar y a crear prototipos
description: Si estás listo para crear, aprende los conceptos básicos que necesitas para empezar a diseñar y a crear prototipos.
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, discover, distribute, index, landing page, design, development, tutorials, sample apps, fundamentals, case studies, resources, HoloLens how-to, Open source projects, core concepts, interaction, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f4a4ea50c45263f18079da76dd8dfd5f31e2af44
ms.sourcegitcommit: 44d0f2873c75003caf9d8d244ceaeb3faa89df63
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2021
ms.locfileid: "98110453"
---
# <a name="start-designing-and-prototyping"></a>Empezar a diseñar y a crear prototipos

![resumen de diseño de realidad mixta](images/design-hero-image.png)

En la actualidad, las aplicaciones de realidad mixta son distintas de cualquier otra cosa del mundo y diseñarlas resulta complicado. No solo tiene que tener en cuenta las nuevas combinaciones de los mundos reales y virtuales que cree, sino también las nuevas experiencias de usuario que estos aportan. Dado que la realidad mixta es un lugar muy amplio, hemos seleccionado aspectos importantes de su espectro de diseño y los hemos expuesto en una serie de puntos de control. Están pensadas para ser secuenciales, pero si ya ha empezado a profundizar en el tema, no dude en ir a cualquiera de las secciones siguientes. 

Eche un vistazo a nuestro vídeo de información general sobre el diseño para empezar:

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a>Diseño de puntos de control

Use los siguientes puntos de control para incorporar ideas y conceptos de la aplicación en el mundo de la realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

Al igual que con todos los recorridos, la aventura para diseñar aplicaciones de realidad mixta comienza con los conceptos básicos. Le recomendamos que se familiarice con los artículos [¿Qué es la realidad mixta](../discover/mixed-reality.md) y [¿Qué es un holograma?](../discover/hologram.md) para obtener una idea inicial sobre el diseño envolvente. Una vez los haya leído detenidamente, estará listo para empezar el recorrido de diseño de la realidad mixta.

![GIF de introducción de la aplicación Designing Holograms](images/HandTracking2.gif)

|  Punto de control  |  Resultado  |
| --- | --- |
| [Ampliar el proceso de diseño](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Obtenga una vista de primera mano del proceso de diseño de Mixed Reality, recopilado de diseñadores de dentro y fuera de Microsoft. |
| [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md) | Decida dónde residirá su experiencia de la aplicación en el espectro de realidad mixta. |
| [Aplicación Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | Conozca los aspectos básicos del diseño de la experiencia de usuario de Mixed Reality a través de comportamientos, sugerencias y recomendaciones para crear fantásticas aplicaciones de HoloLens (disponible para su descarga en HoloLens 2 de Microsoft Store). |
| [Centro de conectividad de ejemplos de MRTK](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | Experimente interacciones espaciales comunes y bloques de creación de experiencia de usuario para Mixed Reality (disponible para su descarga desde Microsoft Store en HoloLens 2) |

### <a name="2-core-concepts"></a>2. Conceptos principales

Tanto si desarrolla contenido para realidad virtual como para realidad aumentada, existen varios conceptos básicos que se aplican al diseño de experiencias envolventes fluidas. Comprender el punto de vista de los usuarios, colocar los objetos y asegurarse de que todo el mundo se siente cómodo y seguro son las prioridades principales en esta fase del recorrido. Al final de esta sección contará con una base sólida para llevar a cabo el diseño de interacción.

![Imagen de ejemplo de los conceptos básicos](images/fragments-750px.jpg)

|  Concepto  |  Resultado  |
| --- | --- |
| [Marco holográfico](holographic-frame.md) | Comprenda cómo ven los usuarios el contenido que se encuentra en el mundo real cuando llevan puesto el casco. |
| [Sistemas de coordenadas](coordinate-systems.md) | Obtenga información sobre cómo colocar los hologramas en lugares significativos del mundo, ya sea en una habitación física o en un dominio virtual que haya creado. |
| [Asignación espacial](spatial-mapping.md) | Ancle objetos en el mundo del usuario y aproveche las superficies físicas del mundo real. |
| [Consideraciones de comodidad](comfort.md) | Cree y presente contenido envolvente que imite el mundo natural a fin de garantizar la seguridad y la comodidad del usuario. |

### <a name="3-interaction-design"></a>3. Diseño de la interacción

Independientemente de lo bonita y envolvente que sea una experiencia virtual, ello no servirá de nada si esta no ofrece interacción. En esta sección obtendrá información acerca de los modelos de interacción básicos, los controladores de movimiento y manos, el uso de la entrada de voz y la recopilación de datos de seguimiento ocular de los usuarios. Al final de esta sección, estará listo para abordar el último tema importante sobre el recorrido del diseño: la experiencia del usuario.

![Factores de diseño de la interacción](images/UX_Hero_Manipulation.jpg)

|  Concepto  |  Resultado  |
| --- | --- |
| [Modelos de interacción](interaction-fundamentals.md) | Proporcione a los usuarios interacciones instintivas a través de la entrada ocular, de manos y de voz. |
| [Controladores de movimiento y manos](hands-and-tools.md) | Obtenga información sobre cómo interactuar con hologramas de cerca con las manos del usuario o desde lejos con interacciones precisas. |
| [Entrada de voz](voice-input.md) | Use comandos de voz como entrada en las aplicaciones inmersivas para controlar los hologramas y los entornos circundantes.  |
| [Seguimiento ocular](eye-tracking.md) | Agregue un nuevo nivel de contexto y comprensión humana en una experiencia holográfica mediante el uso de información sobre lo que ven los usuarios. |

### <a name="4-user-experience-elements"></a>4. Elementos de la experiencia del usuario

Ahora que ya domina las interacciones básicas, puede centrarse en los puntos más precisos de los elementos de la experiencia del usuario y en cómo adaptarlos a los entornos únicos de la realidad mixta. Tratará los comportamientos comunes, el diseño de los recursos, el escalado de los objetos y la tipografía; todo ello mientras consigue que las aplicaciones sean lo más intuitivas posible para los usuarios. Esta sección marca el final del recorrido oficial del diseño de la realidad mixta, pero dispone de más recursos en la sección [¿Cuál es el siguiente paso?](#whats-next) a fin de poder seguir avanzando.

![Elementos de la experiencia del usuario](images/UX_Hero_BoundingBox.jpg)

|  Concepto  |  Resultado  |
| --- | --- |
| [Controles y comportamientos comunes](app-patterns-landingpage.md) | Obtenga información sobre las interacciones espaciales y los bloques de compilación de la interfaz de usuario que se usan con frecuencia. |
| [Color, luz y materiales](color-light-and-materials.md) | Diseñe recursos de calidad para la realidad mixta que tengan en cuenta el color, la iluminación y los materiales. |
| [Escala de objetos](scale.md) | Incorpore tantas indicaciones visuales como sea posible a fin de ayudar a los usuarios a comprender dónde se encuentran los objetos, cuál es su tamaño y de qué material están hechos. |
| [Tipografía](typography.md) | Use texto claro y legible en un espacio tridimensional para ofrecer a los usuarios la información importante que necesitan. |

## <a name="whats-next"></a>¿Qué sigue?

El trabajo de los diseñadores nunca termina, especialmente cuando se aprende a crear experiencias envolventes en un nuevo paradigma. En las secciones siguientes se le llevará más allá del material de diseño de nivel principiante que ya ha completado a fin de explorar el mundo del desarrollo de realidad mixta. Estos temas y recursos no están ordenados de manera secuencial, así que no dude en explorarlos según le apetezca.

### <a name="choose-a-prototyping-option"></a>Elección de una opción de creación de prototipos  

:::row:::   
    :::column:::    
       [![Información sobre Unity](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[Información sobre Unity](https://learn.unity.com/)**<br>
        Aprende a crear experiencias interactivas con Unity. Aprende con la práctica, de principio a fin.
    :::column-end:::    
    :::column:::    
        [![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        Con la interacción espacial y los bloques de creación de la interfaz de usuario, pon en marcha el diseño y desarrollo de la realidad mixta con Unity.   
    :::column-end:::
    :::column:::    
        [![Laboratorios de diseño de realidad mixta](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Laboratorios de diseño de realidad mixta](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        Obtén aplicaciones de ejemplo que te muestren cómo usar los bloques de creación de MRTK para crear experiencias de realidad mixta.
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        Diseño para VR. Microsoft Maquette hace que la creación de prototipos espaciales sea fácil, rápida y envolvente. 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>Otros recursos

:::row:::
    :::column:::
       [![Comprender los conceptos básicos](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[Comprender los conceptos básicos](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Obtén una mejor comprensión de lo que define la realidad mixta y cómo se usa.
    :::column-end:::
    :::column:::
        [![Asistir a un evento](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[Asistir a un evento](../whats-new/sf-academy-events.md)**<br>
        Observa el hardware y obtén un tutorial práctico para crear tu primera aplicación de HoloLens 2.
    :::column-end:::
    :::column:::
        [![Instalar las herramientas](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[Instalar las herramientas](../develop/install-the-tools.md)**<br>
        Usa la lista de comprobación de instalación para obtener las herramientas que necesitas para crear aplicaciones para HoloLens y realidad mixta.
    :::column-end:::
    :::column:::
        [![Empezar a desarrollar](images/74-18.png)](../develop/development.md)<br>
        **[Empezar a desarrollar](../develop/development.md)**<br>
        Elige un método de desarrollo en función de tu nivel de aptitud, estilo de trabajo o preferencia de plataforma.
    :::column-end:::
:::row-end:::

<br>

<br>
