---
title: Experiencias compartidas en realidad mixta
description: Las aplicaciones holográficas pueden compartir delimitadores espaciales de un HoloLens a otro, lo que permite a los usuarios representar un holograma en el mismo lugar del mundo real, en varios dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiencia compartida, realidad mixta, holograma, delimitador espacial, multiusuista, multiusu
ms.openlocfilehash: fe738d07e57bd2f62cab8036a09ca6ab31d6544bdd9b6dacc8dde3445fa58214
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193595"
---
# <a name="shared-experiences-in-mixed-reality"></a>Experiencias compartidas en realidad mixta

Hologramas no es necesario mantener la privada a un solo usuario. Las aplicaciones [holográficas](../../design/spatial-anchors.md) pueden compartir delimitadores espaciales de un dispositivo HoloLens, iOS o Android a otro, lo que permite a los usuarios representar un holograma en el mismo lugar del mundo real en varios dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis preguntas para definir escenarios compartidos

Antes de empezar a diseñar para experiencias compartidas, es importante definir los escenarios de destino. Estos escenarios ayudan a aclarar lo que está diseñando y a establecer un vocabulario común para ayudar a comparar y contrastar las características necesarias en su experiencia. Comprender el problema principal y las distintas vías de soluciones es clave para descubrir las oportunidades inherentes a este nuevo medio.

A través de prototipos internos y exploraciones de nuestros HoloLens asociados, creamos seis preguntas para ayudarle a definir escenarios compartidos. Estas preguntas forman un marco de trabajo, no diseñado para ser exhaustivo, para ayudar a desatilr los atributos importantes de los escenarios.

### <a name="1-how-are-they-sharing"></a>1. ¿Cómo se comparten?

Una presentación podría estar dirigida por un solo usuario virtual, mientras que varios usuarios pueden colaborar, o un profesor podría proporcionar instrucciones a los alumnos virtuales que trabajan con materiales virtuales: la complejidad de las experiencias aumenta en función del nivel de agencia que un usuario tiene o puede tener en un escenario.

![Man and women with holograph on table (Hombre y mujeres con holograma en la tabla)](images/man-and-women-with-holograph-on-table-500px.png)

Hay muchas maneras de compartir, pero hemos descubierto que la mayoría de ellas se divide en tres categorías:

* **Presentación:** cuando se muestra el mismo contenido a varios usuarios. Por ejemplo: un profesor está dando una conferencia a varios alumnos con el mismo material holográfico que se presenta a todo el mundo. Sin embargo, el profesor podría tener sus propias sugerencias y notas que pueden no ser visibles para otros.
* **Colaboración:** cuando las personas trabajan juntas para lograr algunos objetivos comunes. Por ejemplo: el profesor ha dado un proyecto para aprender a realizar una operación de cáncer de corazón. Los alumnos se emparejan y crean una experiencia de laboratorio de aptitudes compartidas, que permite a los alumnos médicos colaborar en el modelo de corazón y aprender.
* **Guía:** cuando una persona ayuda a alguien a resolver un problema en una interacción de estilo más uno a uno. Por ejemplo: El profesor que proporciona orientación a un alumno cuando está realizando el laboratorio de aptitudes para la salud en la experiencia compartida.

### <a name="2-what-is-the-group-size"></a>2. ¿Cuál es el tamaño del grupo?

**Las experiencias de uso compartido uno** a uno pueden proporcionar una línea de base sólida y, idealmente, las pruebas de concepto se pueden crear en este nivel. Pero tenga en cuenta que compartir con grupos grandes (más de seis personas) puede provocar dificultades tanto técnicas (datos y redes) como sociales (el impacto de estar en una sala con varios [avatares).](https://vimeo.com/160704056) La complejidad aumenta exponencialmente a medida que se va de **grupos pequeños** **a grandes.**

Hemos descubierto que las necesidades de los grupos pueden estar en tres categorías de tamaño:
* 1:1
* Small < 7
* Tamaño >= 7

El tamaño del grupo es una pregunta importante porque influye en:

* Representaciones de personas en el espacio holográfico
* Escala de objetos
* Escala del entorno

### <a name="3-where-is-everyone"></a>3. ¿Dónde está todo el mundo?

La intensidad de la realidad mixta entra en juego cuando una experiencia compartida puede tener lugar en la misma ubicación. A eso se **le llama colocated**. Por el contrario, cuando se distribuye el grupo y al menos un participante no se encuentra en el mismo espacio físico (como suele ser el caso de vr) llamamos a esa experiencia **remota**. A menudo, es el caso  de que el grupo tenga participantes tanto agrupados como remotos (por ejemplo, dos grupos en salas de conferencias).

![Tres personas con holograma en la tabla](images/three-people-with-holograph-on-table-500px.png)

Las siguientes categorías ayudan a transmitir dónde se encuentran los usuarios:

* **Colocated**: todos los usuarios estarán en el mismo espacio físico.
* **Remoto:** todos los usuarios estarán en espacios físicos independientes.
* **Ambos:** los usuarios serán una combinación de espacios colocados y remotos.

Esta pregunta es fundamental porque influye en:

* ¿Cómo se comunican las personas?
    * Por ejemplo: ¿Si deben tener avatares?
* Qué objetos ven. ¿Se comparten todos los objetos?
* ¿Si necesitamos adaptarnos a su entorno?

### <a name="4-when-are-they-sharing"></a>4. ¿Cuándo comparten?

Normalmente se piensa en **experiencias sincrónicas** cuando se nos vienen a la mente experiencias compartidas: todos lo estamos haciendo juntos. Pero si se incluye un único elemento virtual agregado por otra persona, tenemos un **escenario** asincrónico. Imagine una nota, o nota de voz, dejada en un entorno virtual. ¿Cómo se controlan las 100 notas virtuales que quedan en el diseño? ¿Qué ocurre si son de decenas de personas con distintos niveles de privacidad?

Considere sus experiencias como una de estas categorías de tiempo:

* **Sincrónicamente:** uso compartido de la experiencia holográfica al mismo tiempo. Por ejemplo: dos alumnos que hacen el laboratorio de aptitudes al mismo tiempo.
* **De forma asincrónica:** uso compartido de la experiencia holográfica en momentos diferentes. Por ejemplo: dos alumnos que hacen el laboratorio de aptitudes pero trabajan en secciones independientes en momentos diferentes.
* **Ambos:** los usuarios a veces compartirán sincrónicamente, pero otras veces de forma asincrónica. Por ejemplo: un profesor que califica la asignación realizada por los alumnos más adelante y deja notas para los alumnos para el día siguiente.

Esta pregunta es importante porque influye en:

* Persistencia de objetos y entornos. Por ejemplo: Almacenar los estados para que se puedan recuperar.
* Perspectiva del usuario. Por ejemplo: quizás recuerde lo que el usuario estaba viendo al dejar notas.

### <a name="5-how-similar-are-their-physical-environments"></a>5. ¿Qué aspectos son similares a sus entornos físicos?

La probabilidad de que dos entornos de la vida real idénticos, fuera de las experiencias colocadas, sean más finos, a menos que esos entornos se hayan diseñado para ser idénticos. Es más probable que tenga **entornos** similares. Por ejemplo, las salas de conferencias son similares, normalmente tienen una tabla ubicada en el centro rodeado de cocina. Las salas de estar, por otro lado, son diferentes** y pueden incluir cualquier número de piezas de cocina en una matriz infinita de diseños.

![Holograph en la tabla](images/holograph-on-table-500px.png)

Considere la posibilidad de que las experiencias de uso compartido se ajusten a una de estas dos categorías:

* **Similar:** entornos que tienden a tener ambientes similares, luz ambiental y sonido, tamaño físico de la sala. Por ejemplo: el profesor está en el aula A y los alumnos están en el aula B. El aula A podría tener menos alumnos que B, pero ambos pueden tener un escritorio físico en el que colocar hologramas.
* **Diferente: entornos que** son diferentes en la configuración de los suelos, el tamaño de las habitaciones, la luz y las consideraciones de sonido. Por ejemplo: un profesor está en una sala de enfoque, pero los alumnos están en un aula grande, llena de alumnos y profesores.

Es importante pensar en [el entorno](/hololens/hololens-environment-considerations), ya que influirá en:

* Cómo experimentarán los usuarios estos objetos. Por ejemplo: ¿Si su experiencia funciona mejor en una tabla y el usuario no tiene ninguna tabla? O bien, en una superficie plana, pero el usuario tiene un espacio desordenado.
* Escala de los objetos. Por ejemplo: colocar un modelo humano de seis pies en una tabla podría ser un desafío, pero un modelo de corazón funcionaría bien.

### <a name="6-what-devices-are-they-using"></a>6. ¿Qué dispositivos usan?

Hoy en día es probable que vea experiencias compartidas entre dos dispositivos inmersivos [**(esos**](../../discover/immersive-headset-hardware-details.md) dispositivos pueden diferir ligeramente para los botones y la funcionalidad relativa, pero no en gran medida) o dos dispositivos holográficos dadas las soluciones destinadas a estos dispositivos.  Pero considere si los dispositivos **2D** (un participante o observador de escritorio o móvil) serán una consideración necesaria, especialmente en situaciones de dispositivos **2D y 3D mixtos.** Comprender los tipos de dispositivos que usarán los participantes es importante, no solo porque vienen con diferentes restricciones y oportunidades de fidelidad y datos, sino porque los usuarios tienen expectativas únicas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Exploración del potencial de las experiencias compartidas

Las respuestas a las preguntas anteriores se pueden combinar para comprender mejor el escenario compartido, lo que mejora los desafíos a medida que amplía la experiencia. Para el equipo de Microsoft, esto ha ayudado a establecer un mapa de ruta para mejorar las experiencias que usamos hoy en día, comprender el matiz de estos problemas complejos y cómo aprovechar las experiencias compartidas en la realidad mixta.

Por ejemplo, considere uno de los escenarios de Skype desde el inicio [](https://www.youtube.com/watch?v=iBfzs3G8BEA) de HoloLens: un usuario ha trabajado en cómo corregir un conmutador de luz roto con la ayuda de un experto ubicado de forma remota.

![Corrección de un conmutador de luz con ayuda a través Skype para HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

*Un experto proporciona **instrucciones 1:1** desde su equipo de escritorio **2D** a un usuario de un dispositivo **de realidad mixta 3D.** La **guía** es **sincrónica** y los entornos **físicos no son similares.***

Una experiencia como esta es un cambio paso a paso respecto a nuestra experiencia actual: aplicar el paradigma del vídeo y la voz a un nuevo medio. Pero a medida que miramos al futuro, debemos definir mejor la oportunidad de nuestros escenarios y crear experiencias que reflejen la fuerza de la realidad mixta.

Considere la [herramienta de colaboración OnSight,](https://www.youtube.com/watch?v=XtUyUJAVQ6w)desarrollada por el laboratorio Jet Jet Deon de la NASA. Los científicos que trabajan en datos de las misiones del rover de Mars pueden colaborar con compañeros en tiempo real dentro de los datos del entorno de Marte.

![Colaboración entre compañeros separados de forma remota para planear el trabajo de Mars Rover](images/onsight-nasa-jpl.gif)

*Un científico explora un entorno mediante un dispositivo **3D**  de realidad  mixta con un pequeño grupo de compañeros remotos que usan dispositivos 3D y **2D.** La **colaboración** **es sincrónica** (pero se puede volver a visitar de forma asincrónica) y los entornos físicos son (virtualmente) **similares.***

Experiencias como OnSight presentan nuevas oportunidades de colaboración. Desde señalar físicamente elementos en el entorno virtual hasta posiciones al lado de un compañero y compartir su perspectiva a medida que explican sus conclusiones. OnSight usa la lente de la presencia y la presencia para replantearse las experiencias de uso compartido en la realidad mixta.

La colaboración intuitiva es la base de la conversación, trabajar juntos y comprender cómo podemos aplicar esta intuición a la complejidad de la realidad mixta es fundamental. Si no solo podemos volver a crear experiencias de uso compartido en la realidad mixta, sino también sobrecargarlas, será un cambio de paradigma para el futuro del trabajo. El diseño de experiencias compartidas en la realidad mixta es un espacio nuevo y emocionante, y solo estamos al principio.

## <a name="get-started-building-shared-experiences"></a>Introducción a la creación de experiencias compartidas

En función de la aplicación y el escenario, habrá varios requisitos para lograr la experiencia deseada. Algunas son:

* **Creación de coincidencias:** capacidad de crear sesiones, anunciar sesiones, detectar e invitar a personas específicas, tanto de forma local como remota, para unirse a la sesión.
* **Uso compartido de** delimitadores: capacidad de alinear coordenadas entre varios dispositivos en un espacio local común, de modo que los hologramas aparezcan en el mismo lugar para todas las personas.
* **Redes:** capacidad de tener posiciones, interacciones y movimientos de personas y hologramas sincronizados en tiempo real entre todos los participantes.
* **Almacenamiento de estado:** capacidad para almacenar las características y ubicaciones del holograma en el espacio para la unión a mitad de la sesión, recuperación en un momento posterior y solidez frente a problemas de red.

La clave de las experiencias compartidas es hacer que varios usuarios vean los mismos hologramas del mundo en su propio dispositivo, lo que suele hacerse mediante el uso compartido de anclajes para alinear las coordenadas entre los dispositivos.

Para compartir delimitadores, use azure [Spatial Anchors](/azure/spatial-anchors):

* En primer lugar, el usuario coloca el holograma.
* La aplicación crea [un delimitador espacial](../../design/spatial-anchors.md)para anclar ese holograma exactamente en el mundo.
* Los anclajes se pueden compartir con dispositivos HoloLens, iOS y Android a través de [Azure Spatial Anchors](/azure/spatial-anchors/).

Con un delimitador espacial compartido, la aplicación en cada dispositivo ahora tiene un [sistema de](../../design/coordinate-systems.md) coordenadas común en el que pueden colocar contenido. Ahora la aplicación puede asegurarse de colocar y orientar el holograma en la misma ubicación.

En HoloLens dispositivos, también puede compartir delimitadores sin conexión de un dispositivo a otro.  Use los vínculos siguientes para decidir qué es lo mejor para la aplicación.

## <a name="evaluating-tech-options"></a>Evaluación de opciones tecnológicas

Hay varias opciones de servicio y tecnología disponibles para ayudar a crear experiencias de realidad mixta con varios usuarios.  Puede ser complicado elegir una ruta de acceso, por lo que al tomar una perspectiva centrada en el escenario, a continuación se detallan algunas opciones.

## <a name="shared-static-holograms-no-interactions"></a>Hologramas estáticos compartidos (sin interacciones)

Aproveche [azure Spatial Anchors](/azure/spatial-anchors/) en la aplicación.  Habilitar y compartir delimitadores espaciales entre dispositivos permite crear una aplicación en la que los usuarios ven hologramas en el mismo lugar al mismo tiempo.  Se necesita una sincronización adicional entre dispositivos para permitir a los usuarios interactuar con hologramas y ver movimientos o actualizaciones de estado de hologramas.

## <a name="share-first-person-perspective"></a>Perspectiva compartir en primera persona

Aproveche la compatibilidad integrada Miracast, para los usuarios locales cuando tenga un receptor Miracast compatible, como un equipo o un televisor: no se necesita ningún código de aplicación adicional.

Aproveche [MixedReality-WebRTC](https://github.com/microsoft/mixedreality-webrtc) en la aplicación, para los usuarios remotos o cuando tenga dispositivos no Miracast que quiera compartir.  La habilitación de una conexión WebRTC permite secuencias de audio y vídeo 1:1 entre los usuarios, con un canal de datos para la mensajería entre dispositivos.  La implementación de realidad mixta se optimiza para HoloLens, ya que proporciona a otros usuarios la secuencia de vídeo de captura de realidad mixta de la vista HoloLens usuario.  Si desea escalar verticalmente el streaming de vídeo a varios clientes remotos, normalmente se usa un proveedor de servicios [MCU](https://webrtcglossary.com/mcu/) (unidad de conferencia multipunto), como [SignalWire](https://signalwire.com/).  Hay disponible una implementación de SignalWire con un solo clic en Azure a través [de Freeswitch](https://github.com/andywolk/azure-freeswitch-gpu-windows).

> [!NOTE]
> Tenga en cuenta que SignalWire es un servicio de pago y no es propiedad ni está afiliada a Microsoft.

## <a name="presenter-spectator-applications-and-demos"></a>Presenter-Spectator aplicaciones y demostraciones

Aproveche [MixedReality-DesenlazableView para](https://github.com/microsoft/MixedReality-SpectatorView) llevar la funcionalidad [de vista del espectador](spectator-view.md) a la aplicación.  Habilite otros dispositivos (HL, Android, iOS y cámaras de vídeo) para ver lo que ve el HoloLens desde una perspectiva diferente en la misma ubicación y recibir actualizaciones sobre las interacciones del host HoloLens el usuario que interactúa con los hologramas.  Vea, tome imágenes y grabe vídeo de lo que hace el host con los hologramas de la aplicación desde su propia perspectiva espacial con el compañero espectador de la misma aplicación.

**Nota:** Las imágenes se toman a través de una captura de pantalla en dispositivos iOS/Android.

## <a name="multi-user-collaborative-experience"></a>Experiencia colaborativa con varios usuarios

Comience con nuestro [tutorial](../unity/tutorials/mr-learning-sharing-02.md)de aprendizaje para varios usuarios, que aprovecha [Azure Spatial Anchors](/azure/spatial-anchors/) para los usuarios locales y el SDK [de Photon](https://www.photonengine.com/PUN) para sincronizar el contenido o el estado de la escena. Cree aplicaciones de colaboración local en las que cada usuario tenga su propia perspectiva sobre los hologramas de la escena y cada una de ellas pueda interactuar completamente con los hologramas.  Las actualizaciones se proporcionan en todos los dispositivos y photon controla la administración de conflictos de interacción.

> [!NOTE]
> Tenga en cuenta que [Photon](https://www.photonengine.com/) es un producto que no es de Microsoft, por lo que es posible que se requiera una relación de facturación con Photon para productizar y escalar para un uso mayor.

## <a name="future-work"></a>Trabajo futuro

Las funcionalidades e interfaces de los componentes ayudarán a proporcionar una coherencia común y una sólida compatibilidad en los distintos escenarios y tecnologías subyacentes.  Hasta entonces, elija la mejor ruta de acceso que se alinee con el escenario que está intentando lograr en la aplicación.

¿Diferente escenario o deseo de usar un servicio o tecnología diferente? Proporcione comentarios como GitHub problemas en el repositorio correspondiente, en la parte inferior de esta página, o bien puede comunicarse con [holodevelopers slack](https://holodevelopers.slack.com/).

## <a name="see-also"></a>Consulta también

* [Azure Spatial Anchors](/azure/spatial-anchors)
* [Delimitadores espaciales compartidos en DirectX](shared-spatial-anchors-in-directx.md)
* [Experiencias compartidas en Unity](../unity/shared-experiences-in-unity.md)
* [Vista del espectador](spectator-view.md)