---
title: Seguimiento de los ojos
description: Obtenga información sobre el seguimiento de los HoloLens 2 y los nuevos niveles de comprensión humana si se ofrece en experiencias holográficas.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Seguimiento de los ojos, realidad mixta, entrada, mirada con los ojos, calibración, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, intención, acciones
ms.openlocfilehash: 4dac059f72dd043802286081a54137c392c1e912
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110119"
---
# <a name="eye-tracking-on-hololens-2"></a>Seguimiento de los ojos en HoloLens 2

![Demostración de seguimiento de los ojos en MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 permite un nuevo nivel de contexto y comprensión humana dentro de la experiencia holográfica al proporcionar a los desarrolladores la capacidad de usar información sobre lo que el usuario está viendo. En esta página se explica cómo los desarrolladores pueden beneficiarse del seguimiento de los ojos para varios casos de uso y qué buscar al diseñar interacciones de usuario basadas en la mirada con los ojos. 

Eye Tracking API se ha diseñado pensando en la privacidad de un usuario, lo que evita pasar cualquier información identificable, especialmente cualquier biométrica. En el caso de las aplicaciones compatibles con el seguimiento de los ojos, el usuario debe conceder permiso a la aplicación para usar la información de seguimiento de los ojos.

### <a name="device-support"></a>Compatibilidad con dispositivos

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

<br>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demostración de conceptos de diseño de seguimiento de la cabeza y los ojos

Si quiere ver los conceptos de diseño de Head and Eye Tracking en acción, consulte la demostración de vídeo Diseño de **hologramas:** seguimiento de la cabeza y seguimiento de los ojos a continuación. Cuando haya terminado, continúe para obtener un análisis más detallado de temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*

## <a name="calibration"></a>Calibración 

Para que el seguimiento de los ojos funcione [](/hololens/hololens-calibration) con precisión, se requiere que cada usuario pase por una calibración de usuario de seguimiento de los ojos para la que el usuario tenga que ver un conjunto de destinos holográficos. Esto permite al dispositivo ajustar el sistema para una experiencia de visualización más cómoda y de mayor calidad para el usuario y garantizar un seguimiento preciso de los ojos al mismo tiempo. 

El seguimiento de los ojos debe funcionar para la mayoría de los usuarios, pero hay casos excepcionales en los que un usuario no puede calibrar correctamente. La calibración podría producir un error por varias razones, entre las que se incluyen, entre otras: 
* El usuario ha optado previamente por no participar en el proceso de calibración.
* El usuario se distraía y no sigue los objetivos de calibración
* El usuario tiene ciertos tipos de lentes de contacto y gafas, que el sistema aún no admite. 
* El usuario tiene cierta fisonología ocular, condiciones de los ojos o una operación ocular, que el sistema aún no admite.  
* Factores externos que impiden el seguimiento confiable de los ojos, como los movimientos en el visor o las gafas de HoloLens, una intensa presión directa y oclusiones debido al vello delante de los ojos

Los desarrolladores deben asegurarse de proporcionar soporte técnico adecuado a los usuarios para los que es posible que los datos de seguimiento de los ojos no estén disponibles (que no puedan calibrarse correctamente). Hemos proporcionado recomendaciones para soluciones de reserva en la sección de la parte inferior de esta página. 

Para obtener más información sobre la calibración y sobre cómo garantizar una experiencia sin problemas, consulte nuestra página [de calibración del usuario de seguimiento de los](/hololens/hololens-calibration) ojos.

<br>

## <a name="available-eye-tracking-data"></a>Datos de seguimiento de los ojos disponibles

Antes de entrar en detalles sobre casos de uso específicos para la entrada de mirada con los ojos, queremos señalar brevemente las funcionalidades que proporciona HoloLens 2 [Eye Tracking API.](/uwp/api/windows.perception.people.eyespose) Los desarrolladores obtienen acceso a un solo rayo de mirada con los ojos (origen y dirección de la mirada) a aproximadamente _30 FPS (30 Hz)._
Para obtener información más detallada sobre cómo acceder a los datos de seguimiento de los ojos, consulte nuestras guías para desarrolladores para usar la mirada con los ojos en [DirectX](../develop/native/gaze-in-directx.md) y la mirada [con los ojos en Unity.](https://aka.ms/mrtk-eyes)

La mirada con los ojos predicho está aproximadamente en 1,5 grados en ángulo visual alrededor del destino real (consulte la ilustración siguiente). Como se esperan ligeras imprecisiones, los desarrolladores deben planear algún margen alrededor de este valor de límite inferior (por ejemplo, entre 2,0 y 3,0 grados puede dar lugar a una experiencia mucho más cómoda). A continuación se explica cómo abordar la selección de destinos pequeños con más detalle. Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar una calibración de seguimiento de los ojos. 

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de destino óptimo a una distancia de 2 metros*

<br>

## <a name="use-cases"></a>Casos de uso

El seguimiento de los ojos permite a las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. En los siguientes casos de uso se describen algunas interacciones que son posibles con el seguimiento de los HoloLens 2 en realidad mixta.
Estos casos de uso aún no forman parte de la experiencia de Holographic Shell (es decir, la interfaz que se ve al iniciar el HoloLens 2).
Puede probar algunas de ellas en el kit de herramientas de [Mixed Reality,](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)que proporciona varios ejemplos interesantes y eficaces para usar el seguimiento de los ojos, como selecciones de destino rápidas y sencillas compatibles con los ojos, y desplazarse automáticamente por el texto en función de lo que el usuario vea. 

### <a name="user-intent"></a>Intento del usuario

La información sobre dónde y qué examina un usuario proporciona un contexto eficaz para **otras** entradas, como la voz, las manos y los controladores.
Esta información puede utilizarse para varias tareas.
Por ejemplo, esto puede oscilar  entre dirigirse rápida y sin esfuerzo por toda la escena; para ello, puede mirar un holograma y decir *"seleccionar"* (vea también mirar y [confirmar)](gaze-and-commit.md)o *"poner esto..."* y, a continuación, examinar dónde quiere colocar el holograma y decir *"... allí".* Puedes consultar varios ejemplos en [Mixed Reality Toolkit: Selección de objetivos con los ojos](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-target-selection) y [Mixed Reality Toolkit: Posicionamiento de objetivos con los ojos](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-positioning).

Además, un ejemplo de intención del usuario podría incluir el uso de información sobre lo que los usuarios ven para mejorar la interacción con agentes virtuales y hologramas interactivos. Por ejemplo, los agentes virtuales pueden adaptar las opciones disponibles y su comportamiento, en función del contenido actualmente visto. 

### <a name="implicit-actions"></a>Acciones implícitas

La categoría de acciones implícitas está estrechamente relacionada con la intención del usuario.
La idea es que los hologramas o los elementos de la interfaz de usuario reaccionen de forma instintiva que ni siquiera parece que el usuario interactúa con el sistema, sino que el sistema y el usuario están sincronizados. Un ejemplo  es el desplazamiento automático basado en la mirada con los ojos, donde el usuario puede leer un texto largo, que comienza automáticamente a desplazarse una vez que el usuario llega a la parte inferior del cuadro de texto para mantener al usuario en el flujo de lectura, sin mover un dedo.  
Un aspecto clave de esto es que la velocidad de desplazamiento se adapta a la velocidad de lectura del usuario.
Otro ejemplo es **el zoom y** el desplazamiento panorámico compatibles con los ojos en los que el usuario puede tener la sensación de que se está centrando exactamente en lo que se centra. La activación y el control de la velocidad de zoom se pueden controlar mediante la entrada de voz o mano, lo que es importante para proporcionar al usuario la sensación de control y evitar que se sobresalte. A continuación hablaremos sobre estas consideraciones de diseño con más detalle. Una vez acercado, el usuario puede seguir sin problemas, por ejemplo, el curso de una calle para explorar su barrio mediante la mirada con los ojos.
Puedes consultar ejemplos de demostración de estos tipos de interacciones en el ejemplo [Mixed Reality Toolkit - Navegación con los ojos](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-navigation).

Otros casos de uso _para acciones implícitas_ pueden incluir:
- **Notificaciones inteligentes:** ¿Alguna vez se han visto afectados por las notificaciones que aparecen justo donde está buscando? Teniendo en cuenta lo que un usuario está prestando atención, puede mejorar esta experiencia mediante la compensación de las notificaciones desde donde el usuario está mirando actualmente. Esto limita las distracciones y las descarta automáticamente una vez que el usuario termina de leer. 
- **Hologramas de limpieza:** Hologramas que reaccionan sutilmente cuando se miran. Esto puede abarcar desde elementos de la interfaz de usuario ligeramente brillantes, una flor lentamente a un perro virtual que empieza a mirar al usuario y a etiquetar su cola. Esta interacción puede proporcionar una sensación interesante de conectividad y satisfacción en la aplicación.

### <a name="attention-tracking"></a>Seguimiento de la atención

La información sobre dónde o qué ven los usuarios puede ser una herramienta enormemente eficaz. Puede ayudar a evaluar la facilidad de uso de los diseños e identificar problemas en los flujos de trabajo para que sea más eficaz.
La visualización y el análisis del seguimiento de los ojos son una práctica común en varias áreas de aplicación. Con HoloLens 2, proporcionamos una nueva dimensión a esta comprensión, ya que los hologramas 3D se pueden colocar en contextos reales y evaluarse en consecuencia. El [Mixed Reality kit de herramientas proporciona](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main) ejemplos básicos para registrar y cargar datos de seguimiento de los ojos y cómo visualizarlos.
Microsoft se dedica a facilitar la innovación y garantiza que los usuarios tengan una experiencia informada y transparente con la forma en que se usa su información de seguimiento de los ojos.  Trabajaremos con nuestros desarrolladores y equipos de experiencias de usuario para proporcionar instrucciones a terceros para garantizar que las experiencias se centren en torno al usuario.  

Algunas aplicaciones en esta área son las siguientes: 
-   **Visualización remota de la mirada con los ojos:** Visualizaciones remotas de mirada con los ojos: visualice lo que los colaboradores remotos están viendo, para poder proporcionar comentarios inmediatos y facilitar el procesamiento de información más preciso.
-   **Estudios de investigación de usuarios:** El seguimiento de la atención puede ayudar a los investigadores a obtener más información sobre cómo los usuarios perciben y interactúan con el entorno natural, sin interferir, para diseñar interacciones humanas-informáticas más instintiva. El seguimiento de los ojos puede proporcionar información no articulada directamente por los participantes en el estudio, que de lo contrario el investigador podría perder fácilmente. 
-   **Supervisión del entrenamiento y el rendimiento:** Practique y optimice la ejecución de tareas mediante la identificación de cuellos de botella de forma más eficaz en el flujo de ejecución. El seguimiento de los ojos puede proporcionar información natural, en tiempo real y objetivo para ayudar a mejorar el entrenamiento, la productividad y la seguridad en el área de trabajo. 
-   **Diseño de evaluaciones, marketing e investigación de consumidores:** El seguimiento de los ojos permite a las empresas comerciales realizar estudios de marketing y consumidor en entornos del mundo real o analizar lo que captura la atención de un usuario para mejorar el diseño de productos o espacios. 

### <a name="other-use-cases"></a>Otros casos de uso

- **Juegos:** ¿Alguna vez ha deseado tener superpoderes? Esta es tu oportunidad. Puede lear hologramas si los mira fijamente. Sacar haces de rayos de rayos de los ojos: pruébalo en [RoboRaid para HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Convierta los insensos en piedras o inutilizarlos. Usa tu visión de rayos X para explorar edificios. El límite es tu imaginación.
Tenga cuidado de no sobresalar al usuario; para más información, consulte nuestras directrices de diseño de entrada basadas en la [mirada con los ojos.](eye-gaze-interaction.md)

- **Avatares expresivos:** El seguimiento de los ojos ayuda en avatares 3D más expresivos mediante el uso de datos de seguimiento de los ojos en directo para animar los ojos del avatar que indican lo que el usuario está mirando. 

- **Entrada de texto:** El seguimiento de los ojos se puede usar como alternativa para la entrada de texto de poco esfuerzo, especialmente cuando la voz o las manos no son convenientes para su uso. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Uso de la mirada con los ojos para la interacción

Crear una interacción que aproveche las ventajas de la orientación con los ojos de movimiento rápido puede ser un desafío.
Por un lado, los ojos se mueven tan rápido que debe tener cuidado sobre cómo usar la entrada de mirada con los ojos, ya que de lo contrario, los usuarios pueden encontrar la experiencia abrumadora o distraída. Por otro lado, también puede crear experiencias realmente mágicas que excite a los usuarios. Para ayudarle, consulte nuestra introducción a las principales ventajas, desafíos y recomendaciones de diseño para la mirada con los ojos [para la interacción.](eye-gaze-interaction.md) 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Soluciones de reserva cuando el seguimiento de los ojos no está disponible

En raras ocasiones, es posible que los datos de seguimiento de los ojos no estén disponibles.
Esto puede deberse a diferentes razones de las que se enumeran las más comunes a continuación:
* El sistema no pudo [calibrar el usuario](/hololens/hololens-calibration).
* El usuario omitió la [calibración](/hololens/hololens-calibration).   
* El usuario está calibrado, pero decidió no conceder permiso a la aplicación para usar sus datos de seguimiento de los ojos.    
* El usuario tiene gafas únicas o alguna condición ocular que el sistema aún no admite. 
* Factores externos que impiden el seguimiento de los ojos confiables, como los movimientos en el visor o las gafas de HoloLens, la intensa presión directa y las oclusiones debido al vello delante de los ojos.

Los desarrolladores deben asegurarse de que hay compatibilidad con la reserva adecuada para estos usuarios. En la [página Seguimiento de los ojos en DirectX,](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) se explican las API necesarias para detectar si los datos de seguimiento de los ojos están disponibles. 

Aunque es posible que algunos usuarios han decidido revocar conscientemente el acceso a sus datos de seguimiento de los ojos y están de acuerdo con el intercambio de una experiencia de usuario inferior a la privacidad de no proporcionar acceso a sus datos de seguimiento de los ojos, en algunos casos esto puede ser involuntario. Si la aplicación usa el seguimiento de los ojos y esta es una parte importante de la experiencia, se recomienda comunicarlo claramente al usuario.   

Informar al usuario por qué el seguimiento de los ojos es fundamental para que la aplicación (quizás incluso enumerar algunas características mejoradas) experimente todo el potencial de la aplicación, puede ayudar al usuario a comprender mejor lo que está entregando. Ayude al usuario a identificar por qué es posible que el seguimiento de los ojos no funcione (en función de las comprobaciones anteriores) y ofrezca algunas sugerencias para solucionar rápidamente posibles problemas. 

Por ejemplo, si puede detectar que el sistema admite el seguimiento de los ojos, el usuario está calibrado e incluso ha dado su permiso, pero no se reciben datos de seguimiento de los ojos, esto puede apuntar a otros problemas, como los desenlazados o los ojos que se están ocultando. 

Hay casos excepcionales de usuarios para los que es posible que el seguimiento de los ojos no funcione. Por lo tanto, tenga en cuenta que permite descartar o incluso deshabilitar los recordatorios para habilitar el seguimiento de los ojos en la aplicación.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Re atrás para aplicaciones que usan la mirada con los ojos como puntero de entrada principal

Si la aplicación usa la mirada con los ojos como entrada de puntero para seleccionar rápidamente hologramas en la escena, pero los datos de seguimiento de los ojos no están disponibles, se recomienda volver a la mirada con la cabeza y empezar a mostrar el cursor de mirada con la cabeza. Se recomienda usar un tiempo de espera (por ejemplo, de 500 a 1500 ms) para determinar si se debe cambiar o no. Esta acción evita que los cursores aparezcan cada vez que el sistema puede perder brevemente el seguimiento debido a movimientos rápidos de los ojos o guijos y parpadeos. Si es desarrollador de Unity, la reserva automática de la mirada con la cabeza ya se controla en Mixed Reality Toolkit. Si es desarrollador de DirectX, debe controlar este cambio usted mismo.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Resalte para otras aplicaciones específicas del seguimiento de los ojos

La aplicación puede usar la mirada con los ojos de una manera única que se adapte específicamente a los ojos. Por ejemplo, animar los ojos de un avatar o para los mapas térmicos de atención basados en los ojos que dependen de información precisa sobre la atención visual. En este caso, no hay ninguna reserva clara. Si el seguimiento de los ojos no está disponible, es posible que sea necesario deshabilitar estas funcionalidades.
Una vez más, se recomienda comunicar esto claramente al usuario que puede no ser consciente de que la funcionalidad no funciona.

<br>

Esta página le ha proporcionado una buena información general para empezar a comprender el rol del seguimiento de los ojos y la entrada de mirada con los ojos para HoloLens 2. Para empezar a desarrollar, consulte nuestra información sobre el rol de la mirada con los ojos para interactuar con [hologramas,](eye-gaze-interaction.md)la mirada con los ojos en [Unity](https://aka.ms/mrtk-eyes) y la mirada con los ojos [en DirectX.](../develop/native/gaze-in-directx.md)

## <a name="see-also"></a>Vea también

* [Calibración](/hololens/hololens-calibration)
* [Comodidad](comfort.md)
* [Interacción basada en el control con los ojos](eye-gaze-interaction.md)
* [Mirada con los ojos en DirectX](../develop/native/gaze-in-directx.md)
* [Mirada con los ojos en Unity (Mixed Reality Toolkit)](https://aka.ms/mrtk-eyes)
* [Mirada y confirmación](gaze-and-commit.md)
* [Entrada de voz](../out-of-scope/voice-design.md)
