---
title: Configuración de Windows Mixed Reality
description: Cómo configurar los controladores de movimiento, la voz y el audio de Windows Mixed Reality, y definir el límite de la habitación para un espacio de juego seguro.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, introducción, configuración, controlador de movimiento, controlador, voz, audio, sentado, posición, límite, controladores de gráficos, Microsoft Edge, cromo
ms.openlocfilehash: 71775ba03cb143b83f1a4514f62f20df903df96d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174463"
---
# <a name="set-up-windows-mixed-reality"></a>Configuración de Windows Mixed Reality

## <a name="get-ready"></a>Prepárese

Para ejecutar Windows Mixed Reality, necesitará lo siguiente:

* Un casco de realidad mixta compatible. [Más información](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* Un [equipo con Windows Mixed Reality preparado](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) con los puertos correctos para los auriculares
* [Controladores](controllers-in-wmr.md)de movimiento, un controlador Xbox o un mouse y un teclado
* Auriculares con micrófono (si el casco no los tiene integrado)
* Un espacio de apertura grande

## <a name="get-set"></a>Obtener conjunto

Prepare su espacio (incluido el espacio de sobrecarga). Asegúrese de que no hay obstáculos, peligros o elementos frágiles en el área que va a usar. No configure en la parte superior de una escalera o bajo un ventilador de techo extra inferior. Quite breakables y obstáculos del área y asegúrese de que usted y cualquier persona que use el casco Lea y comprenda las [directrices de seguridad](https://support.microsoft.com/help/4039969).

## <a name="go"></a>Venga,

Una vez que el espacio esté listo, conecte el casco, pero no lo ponga en ningún momento; en primer lugar, deberá realizar alguna configuración en su PC. Ejecutaremos una comprobación de PC, descargaremos software, conectaremos los controladores y crearemos un [límite](boundary-questions.md) para ayudarte a evitar obstáculos.

Después, se incluye la parte divertida: Coloque el casco y escriba el mundo mezclado. Cortana estará esperando para darle un paseo. ¡Que te diviertas!

## <a name="get-familiar-with-your-motion-controllers"></a>Familiarícese con los controladores de movimiento

Si el casco tiene una radio integrada, los controladores que se incluyen con los auriculares se emparejan en el generador. Cuando encienda por primera vez los nuevos controladores y auriculares, ya estarán emparejados.

Si tiene un casco sin una radio integrada, tendrá que configurar los controladores de movimiento para emparejarlos con el equipo (la mayoría de los auriculares fabricados después 2018 tienen una radio integrada).

Si solo piensa usar un teclado y un mouse de Xbox, no es necesario emparejar los controladores.  Si alguna vez planea usar controladores, probablemente debería emparejarlos.

**Nota**: los controladores de movimiento de Windows Mixed Reality requieren Bluetooth 4,0. Si su equipo no tiene Bluetooth integrado, tendrá que conectar un adaptador de Bluetooth USB que admita Bluetooth 4,0 para habilitar los controladores de movimiento. Si usa la radio integrada en el casco, no necesita un adaptador Bluetooth.

![Familiarícese con los controladores de movimiento](images/get_to_know_controllers.png)

Si tiene que emparejar los controladores de movimiento, consulte el artículo sobre [controladores en Windows Mixed Reality](controllers-in-wmr.md) .

## <a name="set-up-your-room-boundary"></a>Configurar el límite de la habitación

Elija una escala de sala o una experiencia de escalado de mesa:

**Opción 1: configurar para todas las experiencias (también conocido como escala de sala)** le permitirá desplazarse por el salón y es la experiencia de realidad mixta más envolvente. Le recomendamos que, al menos, 5 pies x 7 pies (1,5 metros x 2 metros) de espacio para la realidad mixta.

**Opción 2: configurar la experiencia de sentado y de posición (también conocida como escala de escritorio)** funcionará en su escritorio. Es una buena opción si no tiene una gran cantidad de espacio en su espacio. También significa que utilizará los auriculares sin límite. Deberá permanecer en un solo lugar, ya que no tendrá ningún límite que le ayude a evitar obstáculos físicos. Además, algunas aplicaciones y juegos pueden estar diseñados para usarse con un límite, por lo que es posible que no funcionen según lo previsto.

![Elegir una configuración](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>Si elige "configurar para todas las experiencias"

Pronto, su habitación se convertirá en un mundo virtual donde podrá recorrer e interactuar. Suba y libere espacio en tu habitación para ejecutar una realidad mixta (por ejemplo, borrar algún espacio en el suelo y trasladar tu silla al lateral de la habitación). Le recomendamos que, al menos, 5 pies x 7 pies (1,5 metros x 2 metros) de espacio para la realidad mixta.

![Asegúrese de que el espacio está claro](images/1050px-createaboundary.png)

Asegúrese de que el espacio esté claro.

![Centre el casco](images/1050px-createaboundary-2.png)

Centre el casco.

![Seguimiento del límite](images/1050px-createaboundary-3.png)

Seguimiento del límite.

![Apunte hacia el equipo](images/1050px-createaboundary-4.png)

Mantenga el casco apuntando hacia su PC.

![Este es el límite](images/1050px-createaboundary-5.png)

Este es el límite.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>Si elige "set me up for encajado y permanente"

No se requieren pasos adicionales si elige esta opción.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>¿Cuál es el tamaño máximo del límite?

El tamaño máximo de límite admitido actualmente en Windows Mixed Reality es 18x18ft (5.7 x 5.7 m) o 13ft (4) RADIUS del centro.  El tamaño del límite depende del punto de anclaje y de la distancia desde el punto de anclaje que puede moverse antes de arriesgar la estabilidad del límite.  Windows Mixed Reality se basa en una abstracción de fase en la plataforma, la fase es el espacio en el que se desplaza y esa fase depende de un solo delimitador (que casi todas las aplicaciones también asume, es el funcionamiento de Naopak y Oculus, ya que solo tienen un único sistema de coordenadas).  La razón por la que esto es importante es que, con el seguimiento interior, a medida que se aleja de un punto de anclaje, el seguimiento del casco es confiable a la vez que se mantiene el límite estable.  En los casos en los que el límite esté diseñado para evitar obstáculos físicos, se vuelve más allá de un problema desde el centro.  Dos factores entraron en la decisión sobre el tamaño máximo del límite. la distancia máxima a la que los auriculares de la realidad mixta de Windows podrían proporcionar la mejor experiencia de escala de sala con un límite y la longitud del cable del casco, que para la mayoría de los auriculares de la realidad mixta de Windows es 10ft (3m). 

## <a name="set-up-speech"></a>Configurar voz

Puede habilitar los comandos de Cortana dentro de la realidad mixta. Esto le permite usar comandos de voz dentro de la realidad mixta para transportar, abrir aplicaciones y hacer otras cosas. Aprenderá más sobre esto en el capítulo [sobre la realidad mixta](learn-mixed-reality.md) .

![La realidad mixta es mejor con la voz](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>Configurar los auriculares de audio

A menos que haya adquirido un Odyssey de Samsung HMD (que tiene conectores de AKG integrados y una matriz de micrófono dual integrada), deberá obtener un casco de audio (que tenga micrófonos y auriculares) y conectarlo al conector de audio de 3,5 mm del casco. El conector de audio de 3,5 mm para el casco dependerá del modelo de casco que se encuentra en la parte inferior del parasol o al final de un cable de audio corto que sale del parasol del casco.

## <a name="adjusting-your-headsets-display-settings"></a>Ajuste de la configuración de pantalla del casco

Windows Mixed Reality elige automáticamente la configuración de pantalla que equilibra la calidad y el rendimiento en función de la configuración de hardware del equipo. Para ajustar esta configuración, vaya a **configuración > realidad mixta > pantalla de auriculares**.

### <a name="visuals"></a>Objetos visuales

Esta configuración controla la calidad visual de la Página principal de la realidad mixta. El valor predeterminado es "Automatic".

### <a name="resolution"></a>Resolución

La resolución nativa del casco se muestra aquí.

Si conecta un casco con pantallas de mayor resolución (por ejemplo, con auriculares con 4320x2160 muestra) al equipo, verá una configuración para ajustar la resolución de pantalla de realidad mixta.

* Esta configuración proporciona la opción para que la pila de composición de la realidad mixta de Windows se represente de forma nativa (por ejemplo, en 4320x2160), o para que la pila de composición se represente en una resolución más baja y una escalabilidad vertical (por ejemplo, se represente en 2880x1440 y escale a 4320x2160.
* La configuración predeterminada es representar de forma nativa (por ejemplo, la opción **4320 x 2160 (calidad óptima)** para proporcionar la mejor calidad visual posible desde los auriculares.
* Si su equipo no cumple los requisitos mínimos de hardware de gráficos para los auriculares con pantallas de mayor resolución, o si ve problemas de rendimiento de gráficos, puede intentar usar la opción de **escalado automático (mejor rendimiento)** .

Esta opción está disponible en Windows 10, versión 1903 o posterior.

### <a name="calibration"></a>Calibración

Esta opción es ajustar la calibración de IPD para los auriculares con compatibilidad con IPD de software.

### <a name="experience-options"></a>Opciones de experiencia

Esta configuración avanzada invalida la experiencia predeterminada de frecuencia de actualización de la pantalla de auriculares.

* **Automático (valor predeterminado)**: seleccione automáticamente la experiencia de 60Hz o 90Hz en función de la configuración de hardware de su equipo.
* **Hz**
* **90Hz**

>[!Note]
>La configuración de frecuencia de actualización automática para la reverberación de HP G2 es 90Hz

Ciertas características de Windows Mixed Reality, incluida la vista previa del portal de realidad mixta y un subproceso de visualización de auriculares más grande, solo están disponibles con la experiencia de 90Hz.

### <a name="input-switching"></a>Conmutación de entrada

Esta configuración controla el comportamiento de Windows Mixed Reality en respuesta al sensor de presencia del casco:

* **Cambiar automáticamente mediante el sensor de presencia de auriculares** (valor predeterminado): Windows dirigirá automáticamente la entrada (teclado, mouse...) a Windows Mixed Reality siempre que esté usando el casco. Puede invalidar esto en cualquier momento con Win + Y.
* **Cambiar manualmente mediante la tecla del logotipo de Windows + Y**: Windows no usará el sensor de presencia de auriculares para detectar cuándo se usa el casco. Tendrá que usar Win + Y para cambiar la entrada entre su PC Desktop y Windows Mixed Reality.

Esta opción está disponible en Windows 10, versión 1903 o posterior.

## <a name="installing-microsoft-edge"></a>Instalación de Microsoft Edge 

Para usar el nuevo Microsoft Edge basado en cromo en la Página principal de Windows Mixed Reality, actualice a la versión 1903 o posterior de Windows 10 para ofrecer compatibilidad nativa con aplicaciones Win32 (como el nuevo Microsoft Edge) en la Página principal de Windows Mixed Reality. Active Windows Update o [Instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/software-download/windows10).

>[!IMPORTANT]
>El nuevo Microsoft Edge se lanza con soporte técnico para WebXR, el nuevo estándar para crear experiencias Web envolventes para auriculares VR. Si instala el nuevo Microsoft Edge, ya no podrá reproducir experiencias de WebVR en Microsoft Edge.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Problemas con el nuevo Microsoft Edge en Windows Mixed Reality

**Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10, versión 1903 (o posterior)**

- Iniciar cualquier aplicación de Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se incongele brevemente.
- El icono de Microsoft Edge desaparece del menú Inicio de Windows Mixed Reality (puede encontrarlo en la carpeta "aplicaciones clásicas").
- Las ventanas del Microsoft Edge anterior se siguen colocando en la Página principal de la realidad mixta, pero no se pueden usar. El intento de activar esas ventanas inicia el borde dentro de la aplicación de escritorio.
- Al seleccionar un hipervínculo en la Página principal de realidad mixta, se inicia un explorador Web en el escritorio en lugar de la Página principal de realidad mixta.
- La aplicación WebVR Showcase está presente en la Página principal de la realidad mixta, a pesar de que WebVR ya no se admite.
- Mejoras generales en el inicio del teclado y los objetos visuales.

**Otros problemas conocidos**

- Los sitios web abiertos en Windows Mixed Reality se perderán cuando se cierre el portal de realidad mixta, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en la Página principal de la realidad mixta.
- El audio de las ventanas de Microsoft Edge no está espacial.
- Se corrigió en la versión de extensión de 360 Viewer 2.3.8: abrir un vídeo de 360 desde YouTube en Windows Mixed Reality puede dar lugar a que el vídeo se distorsione en el casco. El reinicio de Edge debe actualizar de manera invisible la extensión del visor de 360 para resolver este problema. Puede confirmar qué versión de la extensión tiene escribiendo `edge://system/` en la barra de direcciones y seleccionando el botón "expandir" situado junto a "extensiones".
- Durante las sesiones de realidad mixta de Windows, los monitores virtuales aparecerán como monitores físicos genéricos en **configuración > pantalla de > del sistema**.

## <a name="launching-mixed-reality-after-the-first-time"></a>Iniciar la realidad mixta después de la primera vez

Escribir la realidad mixta una segunda vez es tan sencillo como volver a colocar el casco mientras está conectado a su equipo. También puede iniciar manualmente la aplicación del portal de realidad mixta abriéndola desde el menú Inicio. La entrada y el audio se enrutarán automáticamente al casco cuando lo coloque, o bien puede desencadenar esto de forma manual presionando **Windows + Y** en el teclado.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas de instalación](installation_errors.md)
* [Solución de problemas de configuración](set-up-questions.md)
* [Información sobre Mixed Reality](learn-mixed-reality.md)
* [Funcionamiento de los controladores de movimiento](controllers-in-wmr.md)
* [Funcionamiento del seguimiento de la interacción directa](tracking-system.md)
