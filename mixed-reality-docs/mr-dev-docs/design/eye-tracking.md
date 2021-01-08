---
title: Seguimiento de los ojos
description: Obtenga información sobre el seguimiento ocular de HoloLens 2 y los nuevos niveles de comprensión humana si se ofrece experiencias holográficas.
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
keywords: Seguimiento ocular, realidad mixta, entrada, ojo ocular, calibración, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, conjunto de herramientas de realidad mixta, intención, acciones
ms.openlocfilehash: ffc9fd172f3e9a1cfd648e3fb431274690c9f190
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009605"
---
# <a name="eye-tracking-on-hololens-2"></a>Seguimiento de los ojos en HoloLens 2

![Demostración de seguimiento ocular en MRTK](images/mrtk_et_scenemenu.jpg)

HoloLens 2 permite un nuevo nivel de contexto y comprensión humana dentro de la experiencia holográfica, ya que proporciona a los desarrolladores la capacidad de usar información sobre lo que el usuario está examinando. En esta página se explica cómo los desarrolladores pueden beneficiarse del seguimiento ocular de varios casos de uso y qué buscar al diseñar interacciones de usuario basadas en el ojo. 

La API de seguimiento ocular se ha diseñado pensando en la privacidad del usuario, evitando pasar cualquier información identificable, especialmente cualquier biometría. En el caso de las aplicaciones compatibles con el seguimiento ocular, el usuario debe conceder permiso a la aplicación para usar la información de seguimiento ocular.

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
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Miras hacia abajo</td>
     <td>❌</td>
     <td>✔️</td>
     <td>❌</td>
</tr>
</table>

<br>

## <a name="calibration"></a>Calibración 

Para que el seguimiento de los ojos funcione con precisión, cada usuario tiene que pasar por una [calibración de usuario de seguimiento ocular](../calibration.md) en la que el usuario tiene que mirar un conjunto de destinos holográficas. Esto permite que el dispositivo ajuste el sistema para una experiencia de visualización más cómoda y de mayor calidad para el usuario y para garantizar un seguimiento de ojo preciso al mismo tiempo. 

El seguimiento ocular debe funcionar para la mayoría de los usuarios, pero hay casos poco frecuentes en los que un usuario no se puede calibrar correctamente. Podría producirse un error en la calibración por varias razones, entre las que se incluyen, entre otras: 
* El usuario previamente decidió salir del proceso de calibración
* El usuario se ha retirado y no ha seguido los objetivos de calibración
* El usuario tiene determinados tipos de lentes de contacto y gafas, que el sistema todavía no admite 
* El usuario tiene determinados physiologys de ojos, condiciones oculares o tiene cirugía ocular, que el sistema todavía no admite.  
* Factores externos que impiden el seguimiento de ojos fiables, como manchas en el parasol o anteojos de HoloLens, luz solar directa y oclusión debido al pelo delante de los ojos

Los desarrolladores deben asegurarse de proporcionar soporte técnico adecuado a los usuarios para los que es posible que los datos de seguimiento ocular no estén disponibles (que no pueden calibrarse correctamente). En la sección de la parte inferior de esta página se proporcionan recomendaciones para las soluciones de reserva. 

Para obtener más información sobre la calibración y cómo garantizar una experiencia fluida, consulte nuestra página de [calibración de usuario de seguimiento ocular](../calibration.md) .

<br>

## <a name="available-eye-tracking-data"></a>Datos de seguimiento ocular disponibles

Antes de entrar en detalles sobre los casos de uso específicos de la entrada ocular y mirarnos, queremos señalar brevemente las funcionalidades que proporciona la [API de seguimiento](https://docs.microsoft.com/uwp/api/windows.perception.people.eyespose) de la vista de HoloLens 2. Los desarrolladores obtienen acceso a un solo rayo de mira fijamente (miran el origen y la dirección) a aproximadamente _30 fps (30 Hz)_.
Para obtener información más detallada sobre cómo obtener acceso a los datos de seguimiento de los ojos, consulte nuestras guías del desarrollador para usar [miras en DirectX](../develop/native/gaze-in-directx.md) y [mirarnos en Unity](https://aka.ms/mrtk-eyes).

El ojo de miración predicho es aproximadamente de 1,5 grados en el ángulo visual alrededor del destino real (vea la ilustración siguiente). A medida que se esperan ligeras imprecisiones, los desarrolladores deben planear algún margen alrededor de este valor de límite inferior (por ejemplo, los grados 2.0-3.0 pueden dar lugar a una experiencia mucho más cómoda). Veremos cómo abordar la selección de destinos pequeños con más detalle a continuación. Para que el seguimiento de los ojos funcione con precisión, cada usuario debe realizar una calibración de seguimiento de los ojos. 

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño óptimo de destino a una distancia de 2 metros*

<br>

## <a name="use-cases"></a>Casos de uso

El seguimiento de los ojos permite a las aplicaciones realizar un seguimiento de dónde mira el usuario en tiempo real. En los siguientes casos de uso se describen algunas interacciones que son posibles con el seguimiento ocular en HoloLens 2 en la realidad mixta.
Estos casos de uso todavía no forman parte de la experiencia de Shell holográfica (es decir, la interfaz que ve al iniciar su HoloLens 2).
Puede probar algunas de ellas en el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html), que proporciona varios ejemplos interesantes y eficaces para usar el seguimiento ocular, como selecciones de destino compatibles con la vista rápida y sin esfuerzo, y desplazarse automáticamente por el texto en función de la apariencia del usuario. 

### <a name="user-intent"></a>Intento del usuario    

Información sobre dónde y qué mira un usuario proporciona un contexto eficaz **para otras entradas**, como voz, manos y controladores.
Esta información puede utilizarse para varias tareas.
Por ejemplo, esto puede variar de forma rápida y sin **esfuerzo a través de** la escena mirando un holograma y diciendo *"Select"* (consulte también [mirarnos y confirmar](gaze-and-commit.md)) o *"Put this..."* y, a continuación, buscar dónde desea colocar el holograma y decir *"... allí "*. Puedes consultar varios ejemplos en [Mixed Reality Toolkit: Selección de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html) y [Mixed Reality Toolkit: Posicionamiento de objetivos con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Positioning.html).

Además, un ejemplo de intención del usuario podría incluir el uso de información sobre lo que los usuarios ven para mejorar la interacción con agentes virtuales incorporados y hologramas interactivos. Por ejemplo, los agentes virtuales pueden adaptar las opciones disponibles y su comportamiento, en función del contenido que se vea actualmente. 

### <a name="implicit-actions"></a>Acciones implícitas

La categoría de acciones implícitas está estrechamente relacionada con la intención del usuario.
La idea es que los hologramas o los elementos de la interfaz de usuario reaccionan de una manera instinctual que puede que no se parezca incluso a la interacción del usuario con el sistema, sino que el sistema y el usuario estén sincronizados. Un ejemplo es el **desplazamiento automático basado en la mirada** , en el que el usuario puede leer un texto largo, que inicia automáticamente el desplazamiento una vez que el usuario llega a la parte inferior del cuadro de texto para mantener al usuario en el flujo de lectura, sin levantar el dedo.  
Un aspecto clave de esto es que la velocidad de desplazamiento se adapta a la velocidad de lectura del usuario.
Otro ejemplo es el **zoom y la panorámica que se admiten,** donde el usuario puede sentir como sumergir exactamente en lo que se ha centrado. La activación y el control de la velocidad de zoom se pueden controlar con una entrada de voz o de forma manual, lo que es importante para proporcionar al usuario la sensación de control mientras evita estar abrumado. Hablaremos sobre estas consideraciones de diseño con más detalle a continuación. Una vez que se ha ampliado, el usuario puede seguir sin problemas, por ejemplo, en el transcurso de una calle para explorar su entorno con sus ojos.
Puedes consultar ejemplos de demostración de estos tipos de interacciones en el ejemplo [Mixed Reality Toolkit - Navegación con los ojos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html).

Otros casos de uso de _acciones implícitas_ pueden incluir:
- **Notificaciones inteligentes:** ¿Alguna vez le molestan las notificaciones que se exponen en el lugar donde está buscando? Teniendo en cuenta la atención de un usuario, puede mejorar esta experiencia mediante el desplazamiento de notificaciones desde donde el usuario está Gazing actualmente. Esto limita las distracciones y las descarta automáticamente una vez que el usuario haya terminado de leer. 
- **Attentive hologramas:** Hologramas que reaccionan sutilmente cuando se miran. Esto puede oscilar entre elementos de la interfaz de usuario ligeramente iluminados, una flor de floración lenta hasta un perro virtual que empieza a volver al usuario y wagging su cola. Esta interacción podría proporcionar una sensación interesante de conectividad y satisfacción en la aplicación.

### <a name="attention-tracking"></a>Seguimiento de la atención   

La información sobre dónde o qué ven los usuarios puede ser una herramienta enormemente eficaz. Puede ayudar a evaluar la facilidad de uso de los diseños e identificar problemas en los flujos de trabajo para que sean más eficientes.
La visualización y el análisis de seguimiento ocular son una práctica común en diversas áreas de la aplicación. Con HoloLens 2, se proporciona una nueva dimensión para esta comprensión, ya que los hologramas 3D se pueden colocar en contextos reales y evaluarse como corresponda. El [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html) proporciona ejemplos básicos para registrar y cargar datos de seguimiento ocular y cómo visualizarlos.
Microsoft está dedicado a facilitar la innovación a la vez que garantiza que los usuarios tengan una experiencia informada y transparente con respecto al uso de su información de seguimiento ocular.  Trabajaremos con nuestros desarrolladores y equipos de experiencia del usuario para proporcionar orientación a terceros con el fin de garantizar que las experiencias se centren en torno al usuario.  


Algunas aplicaciones en esta área son las siguientes: 
-   **Visualización de ojo remoto:** Visualizaciones miradas en el ojo remoto: visualice qué colaboradores remotos están examinando, para poder proporcionar comentarios inmediatos y facilitar el procesamiento de información más preciso.
-   **Estudios de investigación de usuarios:** El seguimiento de atención puede ayudar a los investigadores a obtener más información sobre el modo en que los usuarios perciben y se relacionan con el entorno natural, sin interferir, para diseñar más interacciones de equipos humanos instinctual. El seguimiento ocular puede proporcionar información que no está directamente articulada por los participantes del estudio, lo que, de lo contrario, el investigador podría omitir fácilmente. 
-   **Supervisión de aprendizaje y rendimiento:** Practicar y optimizar la ejecución de tareas mediante la identificación más eficaz de los cuellos de botella en el flujo de ejecución. El seguimiento ocular puede proporcionar información natural, en tiempo real y objetiva para ayudar a mejorar el entrenamiento, la productividad y la seguridad en el lugar de trabajo. 
-   **Diseñe evaluaciones, marketing e investigación de consumidores:** El seguimiento ocular permite a las empresas comerciales realizar estudios de marketing y de consumidores en entornos reales o analizar lo que capta la atención de un usuario para mejorar el diseño del producto o el espacio. 

### <a name="other-use-cases"></a>Otros casos de uso

- **Juegos:** ¿Alguna vez quería tener superalimentación? Esta es tu oportunidad. Puede levitater los hologramas mediante la estrella. Capte vigas láser de los ojos: pruébelos en [RoboRaid para HoloLens 2](https://www.microsoft.com/p/roboraid/9nblggh5fv3j).
Convierta los enemigos en piedra o inmovilice. Usa tu visión de rayos X para explorar edificios. El límite es tu imaginación.
Tenga cuidado de no abrumar al usuario a pesar de ello, eche un vistazo a las [directrices de diseño de entrada basadas en el ojo](eye-gaze-interaction.md).

- **Avatares expresivos:** El seguimiento ocular ayuda en avatares 3D más expresivos mediante el uso de datos de seguimiento de ojos en directo para animar los ojos del Avatar que indican lo que el usuario está mirando. 

- **Entrada de texto:** El seguimiento ocular se puede usar como alternativa a la entrada de texto de bajo esfuerzo, especialmente cuando la voz o las manos no son prácticas de usar. 

<br>

## <a name="using-eye-gaze-for-interaction"></a>Uso de la mirada a la interacción

Crear una interacción que aproveche los objetivos de vista rápida en movimiento puede ser un reto.
Por un lado, los ojos se mueven tan rápido que debe tener cuidado al usar la entrada mirada, ya que, de lo contrario, los usuarios pueden encontrar la experiencia abrumadora o distraer. Por otro lado, también puede crear experiencias realmente mágicas que impedirán a los usuarios. Para ayudarle, eche un vistazo a nuestra información general sobre las ventajas principales, los desafíos y las recomendaciones de diseño para [la interacción](eye-gaze-interaction.md). 
 
## <a name="fallback-solutions-when-eye-tracking-isnt-available"></a>Soluciones de reserva cuando el seguimiento ocular no está disponible

En raras ocasiones, es posible que los datos de seguimiento ocular no estén disponibles.
Esto puede deberse a diferentes motivos entre los que se enumeran los más comunes:
* El sistema no pudo [calibrar al usuario](../calibration.md).
* El usuario omitió la [calibración](../calibration.md).    
* El usuario está calibrado, pero decidió no conceder permiso a la aplicación para usar los datos de seguimiento ocular.    
* El usuario tiene anteojos únicos o alguna condición de ojo que el sistema todavía no admite. 
* Factores externos que impiden el seguimiento de ojos fiables, como manchas en el parasol o anteojos de HoloLens, una luz solar directa y las oclusións por el pelo en la parte delantera de los ojos.  

Los desarrolladores deben asegurarse de que haya soporte de reserva adecuado para estos usuarios. En la página [seguimiento ocular en DirectX](../develop/native/gaze-in-directx.md#fallback-when-eye-tracking-isnt-available) , se explican las API necesarias para detectar si hay datos de seguimiento ocular disponibles. 

Aunque algunos usuarios pueden tener consciously decidido revocar, acceder a sus datos de seguimiento ocular y ser correctos con la desventaja de una experiencia de usuario inferior a la privacidad de no proporcionar acceso a los datos de seguimiento ocular, en algunos casos esto puede ser involuntaria. Si su aplicación usa el seguimiento ocular y esta es una parte importante de la experiencia, recomendamos que se comunique claramente al usuario.   

Informar a los usuarios de por qué el seguimiento ocular es fundamental para su aplicación (quizás incluso mostrar algunas características mejoradas) para experimentar todo el potencial de su aplicación, puede ayudar al usuario a comprender mejor lo que están ofreciendo.    
Ayudar al usuario a identificar por qué es posible que el seguimiento ocular no funcione (según las comprobaciones anteriores) y ofrecer algunas sugerencias para solucionar rápidamente posibles problemas. 
    
Por ejemplo, si puede detectar que el sistema es compatible con el seguimiento ocular, se calibra el usuario y se le ha dado su permiso todavía, pero no se reciben datos de seguimiento ocular, puede que esto señale a otros problemas, como manchas o ojos que se ocluidos.    

Hay casos raros de usuarios para los que es posible que el seguimiento ocular no funcione.   
Por lo tanto, sea respetuoso de eso permitiendo descartar o incluso deshabilitar recordatorios para habilitar el seguimiento ocular en la aplicación.

### <a name="fall-back-for-apps-using-eye-gaze-as-a-primary-input-pointer"></a>Revertir para aplicaciones con miras ocular como puntero de entrada principal

Si la aplicación usa la vista de puntero para seleccionar rápidamente los hologramas en toda la escena, aunque los datos de seguimiento ocular no están disponibles, se recomienda revertir al encabezado y empezar a mostrar el cursor de miras hacia abajo. Se recomienda utilizar un tiempo de espera (por ejemplo, 500 – 1500 MS) para determinar si se debe cambiar o no. Esta acción evita que los cursores aparezcan cada vez que el sistema puede perder el seguimiento por poco debido a movimientos de ojo rápido o a guiños y parpadeos. Si es un desarrollador de Unity, la reserva automática para la cabeza de mira ya está controlada en el kit de herramientas de realidad mixta. Si es desarrollador de DirectX, debe administrar este conmutador usted mismo.

### <a name="fall-back-for-other-eye-tracking-specific-applications"></a>Revertir para otras aplicaciones específicas del seguimiento ocular

La aplicación puede usar miras en un modo único que se adapte específicamente a los ojos. Por ejemplo, animar los ojos de un avatar o la atención Mapas térmicos basada en el ojo con información precisa sobre la atención visual. En este caso, no hay ninguna reserva clara. Si el seguimiento ocular no está disponible, es posible que sea necesario deshabilitar estas funcionalidades.
De nuevo, se recomienda comunicar esto al usuario que puede no ser consciente de que la funcionalidad no funciona.

<br>

Esperamos que esta página le haya proporcionado una buena introducción para empezar a comprender el papel del seguimiento ocular y la entrada de mirada para HoloLens 2. Para empezar a desarrollar, eche un vistazo a nuestra información sobre el papel de la mirada [para interactuar con los hologramas](eye-gaze-interaction.md), [mirando en Unity](https://aka.ms/mrtk-eyes) y miramos [a la vista en DirectX](../develop/native/gaze-in-directx.md).

## <a name="see-also"></a>Consulte también

* [Calibración](../calibration.md)
* [Comodidad](comfort.md)
* [Interacción basada en el control con los ojos](eye-gaze-interaction.md)
* [Miras a la vista en DirectX](../develop/native/gaze-in-directx.md)
* [Mirada a la vista de Unity (kit de herramientas de realidad mixta)](https://aka.ms/mrtk-eyes)
* [Mirada y confirmación](gaze-and-commit.md)
* [Entrada de voz](../out-of-scope/voice-design.md)


