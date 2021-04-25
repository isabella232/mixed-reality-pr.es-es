---
title: Configuración de Windows Mixed Reality
description: Cómo configurar los controladores de Windows Mixed Reality, voz y audio, y definir el límite de la sala para un espacio de juego seguro.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, get started, setup, motion controller, controller, speech, audio, seated, standing, boundary, graphics drivers, Microsoft Edge, chromium
ms.openlocfilehash: a08982112fea4d1b67b690233ae387b76afc2f90
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944756"
---
# <a name="set-up-windows-mixed-reality"></a>Configuración de Windows Mixed Reality

## <a name="get-ready"></a>Prepárese

Para ejecutar Windows Mixed Reality, necesitará:

* Casco envolvente de realidad mixta compatible. [Más información](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* Un [Windows Mixed Reality equipo listo para usar](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) con los puertos correctos para el casco
* Controladores [de movimiento,](controllers-in-wmr.md)un controlador de Xbox o un mouse y teclado
* Cascos con micrófono (si el casco no los tiene integrados)
* Un espacio grande y abierto

## <a name="get-set"></a>Obtener conjunto

Prepare el espacio (incluido el espacio de sobrecarga). Asegúrese de que no haya obstáculos, peligro ni elementos frágiles en el área que va a usar. No se configure en la parte superior de una escalera o debajo de un ventilador de techo muy bajo. Quite los obstáculos o los obstáculos que puedan interrumpirse del área y asegúrese de que todos los usuarios de cascos lean y comprendan las directrices de seguridad.

Una vez que el espacio esté listo, conecte los cascos, pero no lo ponga aún; primero, es necesario realizar alguna configuración en el equipo. Ejecutaremos una comprobación de PC, descargaremos software, conectaremos [los](boundary-questions.md) controladores y crearemos un límite para evitar obstáculos.

Luego viene la parte divertida: ponerse el casco y entrar en el mundo mixto. Cortana estará esperando para darle un paseo. ¡Que te diviertas!

## <a name="go"></a>Venga,

Una vez que el espacio esté listo, conecte el casco, pero no lo ponga aún; primero, es necesario realizar alguna configuración en el equipo. Ejecutaremos una comprobación de PC, descargaremos software, conectaremos [los](boundary-questions.md) controladores y crearemos un límite para evitar obstáculos.

Luego viene la parte divertida: ponerse el casco y entrar en el mundo mixto. Cortana estará esperando para darle un paseo. ¡Que te diviertas!

## <a name="get-familiar-with-your-motion-controllers"></a>Familiarícese con los controladores de movimiento.

Si el casco tiene una radio integrada, los controladores que vienen con el casco se emparejan en la fábrica. La primera vez que encienda los nuevos controladores y cascos, ya estarán emparejados.

Si tiene un casco sin radio integrado, tendrá que configurar los controladores de movimiento mediante su emparejamiento con el equipo. La mayoría de los cascos fabricados después de 2018 tienen radio integrado.

No es necesario emparejar los controladores si solo tienes previsto usar un controlador para juegos de Xbox o un teclado y un mouse.  Si alguna vez planea usar controladores, debe emparejarlos.

**Nota:** Windows Mixed Reality controladores de movimiento requieren Bluetooth 4.0. Si el equipo no tiene Bluetooth integrado, deberá conectar un adaptador Bluetooth USB compatible con Bluetooth 4.0 para habilitar los controladores de movimiento. No necesita un adaptador bluetooth para usar la radio integrada en el casco.

![Familiarícese con los controladores de movimiento.](images/get_to_know_controllers.png)

Si necesita emparejar los controladores de movimiento, revise los controladores [Windows Mixed Reality](controllers-in-wmr.md) artículo.

## <a name="set-up-your-room-boundary"></a>Configuración del límite de la sala

Elija una experiencia de escala de sala o de escritorio:

**Opción 1:** Configurarme para todas las experiencias (también conocidas como escala de sala) le permitirá recorrer la sala y es la experiencia de realidad mixta más envolvente. Se recomienda borrar al menos cinco pies x siete pies (1,5 metros x 2 metros) de espacio para la realidad mixta.

**Opción 2: Configurarme para** la experiencia de puesto y de pie (también conocida como escala de escritorio) funcionará en su escritorio. Es una buena opción si el espacio no es grande. También significa que va a usar el casco sin límite. Tendrá que permanecer en un solo lugar, ya que no tendrá ningún límite que le ayude a evitar obstáculos físicos. Algunas aplicaciones y juegos no están diseñados para ser una experiencia límite, por lo que es posible que no funcionen según lo previsto.

![Elección de una configuración](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>Si elige "Configurarme para todas las experiencias".

Pronto, su habitación se convertirá en un mundo virtual donde podrá recorrer e interactuar. De pie y despeja algo de espacio en su sala para ejecutar la realidad mixta. Se recomienda borrar al menos cinco pies x siete pies, o 1,5 metros x 2 metros, de espacio para la realidad mixta.

![Asegúrese de que el espacio está despejado.](images/1050px-createaboundary.png)

Asegúrese de que el espacio está despejado.

![Centrar los cascos](images/1050px-createaboundary-2.png)

Centrar los cascos.

![Seguimiento del límite](images/1050px-createaboundary-3.png)

Seguimiento del límite.

![Permanecer apuntado hacia pc](images/1050px-createaboundary-4.png)

Mantenga el casco apuntado hacia el equipo.

![Este es el límite](images/1050px-createaboundary-5.png)

Este es el límite.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>Si elige "Set me up for seated and standing" (Configurarme para estar sentado y de pie)

No se requieren pasos adicionales si elige esta opción.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>¿Cuál es el tamaño máximo del límite?

El tamaño máximo de límite admitido en Windows Mixed Reality es un radio de 18 x 18 pies (5,7 x 5,7 m) o 13 pies (4 m) desde el centro. El tamaño del límite depende del punto de anclaje y del punto de anclaje que se puede mover antes de que se arriesga a la estabilidad del límite.  Windows Mixed Reality se basa en una abstracción de fase, que es el espacio en el que se mueve. Esa fase depende de un único delimitador, que casi todas las aplicaciones también asumen: así es como Vive y Oculus también funcionan con su sistema de coordenadas único.  Esto es importante porque, con el seguimiento interno, a medida que se aleja de un punto de anclaje, el seguimiento de cascos es confiable para mantener el límite estable.  Cuando el límite está pensado para ayudar a evitar obstáculos físicos, se convierte en un problema más allá del centro al que va.  Se han tomado dos factores para decidir el tamaño máximo de los límites. La distancia máxima a la que Windows Mixed Reality cascos podrían proporcionar la mejor experiencia de escala de sala con un límite y la longitud del cable del casco, que para la mayoría de los cascos Windows Mixed Reality son de 10 pies (3 m).

## <a name="set-up-speech"></a>Configuración de voz

Puede habilitar los comandos de Cortana en realidad mixta, lo que le permite usar comandos de voz para teleportar y abrir aplicaciones. Aprenderá más sobre estas acciones en el capítulo [de](learn-mixed-reality.md) Descubrir la realidad mixta.

![La realidad mixta es mejor con la voz](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>Configuración del casco de audio

A menos que haya adquirido un Samsung HMD Oceanía con auriculares ACORE integrados y una matriz de micrófonos duales, debe obtener un casco de audio con micrófono y auriculares y conectarlo al conector de audio de 3,5 mm del casco. El conector de audio de 3,5 mm para el casco se encuentra en la parte inferior del visor del casco o al final de un cable de audio corto conectado al visor del casco, según el modelo de casco.

## <a name="adjusting-your-headsets-display-settings"></a>Ajuste de la configuración de pantalla del casco

Windows Mixed Reality automáticamente la configuración de presentación que equilibra la calidad y el rendimiento, en función de la configuración de hardware del equipo. Para ajustar esta configuración, vaya a **Configuración > Mixed Reality > casco.**

### <a name="visuals"></a>Objetos visuales

Esta configuración controla la calidad visual de la página principal de Mixed Reality. El valor predeterminado es "Automático".

### <a name="resolution"></a>Solución

La resolución nativa del casco se muestra aquí.

Si conecta un casco con pantallas de mayor resolución al equipo, por ejemplo, cascos con pantallas de 4320 x 2160, verá una configuración para ajustar la resolución de pantalla de realidad mixta.

* Esta configuración proporciona la opción de que la pila de composición de Windows Mixed Reality se represente de forma nativa (por ejemplo, a 4320 x 2160) o que la pila de composición se represente con una resolución y una escala inferiores (por ejemplo, se represente a 2880 x 1440 y se ajuste a 4320 x 2160).
* El valor predeterminado es representar de forma nativa (por ejemplo, la opción **4320 x 2160 (mejor calidad)** para proporcionar la mejor calidad visual posible desde el casco.
* Use la **opción Escalado automático (mejor rendimiento)** si:
    * El equipo no cumple los requisitos mínimos de hardware gráfico para los cascos con pantallas de mayor resolución
    * Ve problemas de rendimiento de gráficos.

Esta configuración está disponible en Windows 10, versión 1903 o posterior.

### <a name="calibration"></a>Calibración

Esta configuración es para ajustar la calibración de IPD para cascos con compatibilidad con IPD de software.

### <a name="experience-options"></a>Opciones de experiencia

Esta configuración avanzada invalida la experiencia predeterminada de frecuencia de actualización de la pantalla del casco.

* **Automático (valor predeterminado):** seleccione automáticamente la experiencia de 60 Hz o 90 Hz en función de la configuración de hardware del equipo.
* **60 Hz**
* **90 Hz**

>[!Note]
>La primera vez que se configura el casco HP Reverb G2, la experiencia se cambia a 90Hz para garantizar la mejor experiencia.  Si es necesario, puede volver a cambiarlo a Automático.

### <a name="input-switching"></a>Conmutación de entrada

Esta configuración controla el comportamiento de Windows Mixed Reality en respuesta al sensor de presencia del casco:

* **Cambio automático mediante el sensor** de presencia de cascos (valor predeterminado): Windows dirigirá automáticamente la entrada (teclado, mouse...) a Windows Mixed Reality cada vez que lleve el casco. Puede invalidarlo en cualquier momento con Win + Y.
* **Cambiar manualmente con la tecla del logotipo de Windows + Y:** Windows no usará el sensor de presencia del casco para detectar cuándo lleva el casco. Deberás usar Win + Y para cambiar la entrada entre el escritorio del equipo y Windows Mixed Reality.

Esta configuración está disponible en Windows 10 versión 1903 o posterior.

## <a name="installing-microsoft-edge"></a>Instalación de Microsoft Edge 

Para usar el nuevo Microsoft Edge basado en Chromium en Windows Mixed Reality home, actualice Windows 10 Windows 10 versión 1903 o posterior para obtener compatibilidad nativa con aplicaciones Win32 (como la nueva Microsoft Edge) en Windows Mixed Reality home. Compruebe Windows Update o [instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/software-download/windows10).

>[!IMPORTANT]
>La nueva Microsoft Edge se inicia con compatibilidad con WebXR, el nuevo estándar para crear experiencias web envolventes para cascos vr. Ya no podrá reproducir experiencias webVR en Microsoft Edge si instala el nuevo Microsoft Edge.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Problemas con el nuevo Microsoft Edge en Windows Mixed Reality

**Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10 versión 1903 (o posterior)**

- El inicio de cualquier aplicación Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se congele brevemente.
- El Microsoft Edge de datos desaparece del Windows Mixed Reality menú Inicio (puede encontrarlo en la carpeta "Aplicaciones clásicas").
- Las ventanas de la Microsoft Edge se siguen colocando alrededor del ambiente principal, pero no se pueden usar. Al intentar activar esas ventanas, se inicia Edge en la aplicación de escritorio.
- Al seleccionar un hipervínculo en el ambiente principal se inicia un explorador web en el escritorio en lugar del ambiente principal.
- La aplicación WebVR Showcase está presente en el ambiente principal, a pesar de que Ya no se admite WebVR.
- Mejoras generales en el inicio del teclado y los objetos visuales.

**Otros problemas conocidos**

- Los sitios web abiertos Windows Mixed Reality se perderán cuando Portal de realidad mixta cierre, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en el ambiente principal.
- El audio Microsoft Edge ventanas no está espacializado.
- Se ha corregido en la versión 2.3.8 de la extensión 360 Viewer: abrir un vídeo 360 desde YouTube en Windows Mixed Reality puede provocar que el vídeo se desvirtue en el casco. Reiniciar Edge debe actualizar invisiblemente la extensión 360 Viewer para resolver este problema. Para confirmar qué versión de la extensión tiene, escriba en la barra de direcciones y seleccione el botón `edge://system/` "Expandir" junto a "extensiones".
- Durante Windows Mixed Reality, los monitores virtuales aparecerán como monitores físicos genéricos en Configuración **> sistema > Mostrar**.

## <a name="launching-mixed-reality-after-the-first-time"></a>Inicio de la realidad mixta después de la primera vez

Escribir la realidad mixta una segunda vez es tan fácil como volver a poner el casco mientras está conectado al equipo. También puede iniciar la aplicación Portal de realidad mixta manualmente si la abre desde el menú Inicio. La entrada y el audio se enrutarán automáticamente al casco cuando lo coloque, o bien puede desencadenarlo manualmente presionando **Windows + Y** en el teclado.

## <a name="see-also"></a>Vea también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico.](https://support.microsoft.com/contactus/)
* [Solución de problemas de instalación](installation_errors.md)
* [Solución de problemas de configuración](wmr-setup-faq.yml)
* [Información sobre Mixed Reality](learn-mixed-reality.md)
* [Controladores de movimiento](controllers-in-wmr.md)
* [Funcionamiento del seguimiento de la interacción directa](tracking-system.md)
