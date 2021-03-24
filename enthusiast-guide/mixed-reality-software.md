---
title: Información general de software y historial de versiones
description: Información general de los principales componentes de software para Windows Mixed Reality, auriculares más inmersivo y su historial de versiones.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, componentes de software, historial de versiones, notas de la versión, historial de versiones
appliesto:
- Windows 10
ms.openlocfilehash: ea65dd2c6c821189b1248bf3b418e38fdd7a6d7f
ms.sourcegitcommit: 919bdc3e46325f3c44a022c8852cd38ffec33d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2021
ms.locfileid: "105029393"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Información general de software de Mixed Reality e historial de versiones

## <a name="introduction-to-mixed-reality-software"></a>Introducción al software de realidad mixta

Windows Mixed Reality consta de los siguientes componentes de software principales:

1. **Portal de realidad mixta**, que proporciona la experiencia principal de Windows Mixed Reality
    * En las versiones 1709 y 1803 de Windows 10, el portal de realidad mixta es un componente clave del sistema operativo Windows 10 actualizado a través de Windows Update.
    * En Windows 10 versión 1809 y versiones más recientes, el portal de realidad mixta se actualiza a través de la aplicación Microsoft Store.
2. El **paquete de características a petición** (du) de realidad mixta se descarga e instala automáticamente durante la primera ejecución del portal de realidad mixta. Puede encontrar más información sobre el paquete de du [aquí](/windows/application-management/manage-windows-mixed-reality)
3. El **controlador de casco y controlador de movimiento de realidad mixta**, también conocido como controlador de sensores de HoloLens, es el paquete de controladores clave que permite a los auriculares con Windows Mixed Reality trabajar con Windows Mixed Reality. Esto se descarga e instala automáticamente a través de Windows Update la primera vez que el casco de la realidad mixta está conectado y se actualiza regularmente mediante Windows Update
4. Los controladores de modelos de modelo de movimiento de realidad mixta contienen los modelos 3D de los controladores de movimiento de realidad mixta y son necesarios para experiencias de realidad mixta de terceros. Esto se descarga e instala automáticamente a través de Windows Update la primera vez que los controladores de movimiento de realidad mixta se emparejan con el equipo y se actualizan a través de Windows Update
5. **Windows 10, versión 1709 (actualización de Fall Creator) o posterior** contiene tecnologías y componentes principales del sistema operativo que habilitan Windows Mixed Reality

El uso de Windows Mixed Reality en SteamVR requiere el siguiente software:

6. **SteamVR**, desarrollada y mantenida por válvulas Corporation que permite aplicaciones de realidad virtual y juegos en vapor. Puede obtener más información [aquí](https://go.microsoft.com/fwlink/?linkid=862788)
7. **Windows Mixed Reality para** el componente SteamVR, que une SteamVR con Windows Mixed Reality. Puede encontrar más información sobre este componente [en la página de Windows Mixed Reality para SteamVR](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Administrar el casco de la realidad mixta de Windows:

8. La **aplicación complementaria de dispositivo**, desarrollada y mantenida por cada uno de los fabricantes de auriculares, proporciona una introducción rápida a los auriculares con Windows Mixed Reality. En los auriculares con capacidad integrada de Bluetooth, la aplicación complementaria de dispositivo permite restaurar los controladores de movimiento en el emparejamiento de Bluetooth de fábrica. Algunos auriculares (como Samsung Odyssey y Samsung Odyssey +) también usan la aplicación de dispositivo complementario para proporcionar actualizaciones de firmware del casco del fabricante del casco. Esta aplicación se descarga automáticamente la primera vez que el casco está enchufado y se encuentra en el menú Inicio de Windows.

## <a name="windows-10-release-notes---may-2020"></a>Notas de la versión de Windows 10: mayo 2020

La **actualización 2020 de Windows 10 de mayo (v2004)** incluye nuevas características para los auriculares de Windows Mixed Reality (VR), como la capacidad de iniciar aplicaciones Win32 en la Página principal de la realidad mixta. HoloLens (1ª generación) está en el servicio a largo plazo (LTS), con actualizaciones de servicio que se publican mensualmente.

Actualización a la versión más reciente del equipo para auriculares con Windows Mixed Reality inmersivo (VR), Abra **configuración > actualizar & seguridad** y seleccione **Buscar actualizaciones**. En un equipo con Windows 10, también puede instalar manualmente la **actualización de Windows 10 de mayo de 2020** mediante la [herramienta de creación de Windows Media](https://www.microsoft.com/software-download/windows10).

**Versión más reciente del escritorio**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Actualizaciones para auriculares con Windows Mixed Reality

#### <a name="introducing-the-new-microsoft-edge"></a>Presentación del nuevo Microsoft Edge

Como se [anunció anteriormente](/windows/mixed-reality/new-microsoft-edge), hemos realizado actualizaciones para mejorar la compatibilidad con el nuevo explorador Microsoft Edge en Windows Mixed Reality. El nuevo Microsoft Edge adopta el proyecto de código abierto de cromo para crear una mejor compatibilidad web para los clientes y menos fragmentación de la web para todos los desarrolladores Web. También es compatible con WebXR, el nuevo estándar para crear experiencias Web envolventes para auriculares VR en lugar de WebVR.

#### <a name="improved-settings-for-wmr"></a>Configuración mejorada de WMR

Gracias a sus comentarios, hemos agregado y aclarado la configuración de la página de visualización de los auriculares:

* **Calidad visual de mi hogar** : el cambio de esta configuración solo afecta al entorno de inicio de la realidad mixta (acantilado House y Skyloft):

* **Ajuste el nivel de detalle y la calidad de los efectos en la Página principal de la realidad mixta** ; esto cambia algunos de los efectos de representación que usamos en el hogar. En concreto, la calidad visual de materiales diferentes (madera, hormigón, etc.) se escalará a medida que cambie esta configuración de baja a alta.

* **Cambiar la resolución** de la ventana de la aplicación: de forma predeterminada, la mayoría de las ventanas de 2D iniciadas en el hogar se inician con una resolución 720-p. Aunque puede cambiar el tamaño de forma manual horizontalmente & verticalmente, también puede hacer que todos se inicien en 1080p en su lugar. Anteriormente, esta opción estaba disponible como la opción muy alta (beta) en calidad visual. Lo hemos dividido correctamente como una configuración independiente.

* **Opciones de experiencia** : estas opciones ajustan la experiencia de realidad mixta para reducir la carga en los sistemas en los que es posible que el hardware tenga dificultades para mantenerse al día con 90 fps sin restricciones. Puede habilitar o deshabilitar explícitamente esta configuración adicional o elegir dejar que Windows decida y dejar que nuestra heurística siga decidiendo Cuándo activarlas y desactivarlas.

* **Resolución** : Si tiene auriculares de alta resolución como la reverberación de HP, admitimos su ejecución en su resolución nativa o con una resolución reducida por motivos de rendimiento. Los auriculares anteriores, como Samsung Odyssey y Odyssey +, solo admiten una resolución única, por lo que no puede cambiar esta configuración en esos auriculares.

* **Velocidad de fotogramas** : ahora puede establecer manualmente la velocidad de fotogramas de la pantalla del casco o continuar para que Windows use su heurística para determinar si los 60 hz o 90 Hz son más adecuados.

* **Calibración** : como antes, puede ajustar el IPD (distancia interpupillary) si lo admiten los auriculares.

* **Cambio de entrada** : alterne el comportamiento de cambio de foco de entrada (Win + Y) para que sea automático (según los comentarios del sensor de presencia) o manual.

#### <a name="new-cortana-app"></a>Nueva aplicación de Cortana

Esta actualización a Windows incluye la versión más reciente de la aplicación Cortana, que actualmente es solo en inglés y ya no es compatible con determinados comandos específicos de realidad mixta, como "tomar una imagen" y "tomar un vídeo". Puede usar el nuevo Cortana para iniciar aplicaciones y también es compatible con los nuevos comandos de productividad, como "¿Cuál es mi próxima reunión?". o bien, "enviar un correo electrónico a <name> que estoy ejecutando tarde".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Hay actualizaciones adicionales disponibles en 19041,546 (publicada el 2020 de octubre)

Esta actualización de mantenimiento mensual del escritorio incluye los siguientes cambios en los dispositivos de Windows Mixed Reality: 
* Reduce las distorsiones y aberraciones en las pantallas montadas por el cabezal de Windows Mixed Reality (HMD). 
* Agrega compatibilidad con los próximos controladores de movimiento de la realidad mixta de HP Windows. 
* Cambia el comportamiento de la configuración de frecuencia de actualización de 90-Hz en Windows Mixed Reality a no volver a cambiar automáticamente a 60 Hz en ciertos casos en los que no se puede lograr 90 Hz. 

#### <a name="help-us-improve"></a>Ayúdenos a mejorar.

Veremos continuamente cómo mejorar la compatibilidad.  Si encuentra que su aplicación favorita de Win32 clásica no se comporta correctamente en Windows Mixed Reality, envíe sus comentarios a través de nuestro [centro de opiniones](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión: mayo 2019](release-notes-may-2019.md)
* [Notas de la versión (octubre de 2018)](release-notes-october-2018.md)
* [Notas de la versión: abril 2018](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Historial de versiones de controlador de movimiento y auriculares de realidad mixta ###

Este controlador se descarga e instala automáticamente a través de Windows Update, pero los vínculos de descarga se proporcionan en línea:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versión 2004 (actualización de mayo de 2020) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 de marzo de 2021  | Compatible con Windows 10, la versión 1903 y versiones más recientes.<br/><ul><li>Actualice el orden de bobinado de la malla de área oculta para que la reverberación de HP G2 sea coherente con otros auriculares.</li><li>Objetos visuales: mejoras de calidad para los auriculares de reverberación de HP G2.</li><li>Mejoras en la confiabilidad y la plataforma con auriculares de realidad mixta de Windows.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 de diciembre de 2020  | Compatible con Windows 10, la versión 1903 y versiones más recientes.<br/><ul><li>Nuevo firmware del controlador para el controlador de HP para solucionar un problema en el que algunos controladores tienen desencadenadores no en funcionamiento.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 de octubre de 2020  | Compatible con Windows 10, la versión 1903 y versiones más recientes.<br/><ul><li>Compatibilidad oficial con la reverberación de HP G2, HP Omnicept y el nuevo controlador de HP.</li><li>Correcciones de pantalla secundarias para la reverberación de HP y los auriculares de Samsung Odyssey +. (Requiere la [compilación de so 19041,546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) o posterior o las [compilaciones de sistema operativo 18362,1110 y 18363,1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) o posterior).</li><li>Mejoras en el estado de la alimentación del equipo transición de la suspensión para reducir los errores de SWW 1-4.</li><li>Correcciones secundarias y mejoras de confiabilidad de la plataforma con auriculares de realidad mixta de Windows.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 de mayo de 2020      | Compatible con Windows 10, la versión 1903 y versiones más recientes.<br/><ul><li>Correcciones secundarias y mejoras de confiabilidad de la plataforma con auriculares de realidad mixta de Windows.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versión 1903 (actualización de mayo de 2019) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 de octubre de 2019      | Compatible con Windows 10, la versión 1809 y versiones más recientes.<br/><ul><li>Correcciones secundarias de la plataforma con auriculares de realidad mixta de Windows.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 de junio de 2019      | Compatible con Windows 10, la versión 1809 y versiones más recientes.<br/><ul><li>Mejoras en la confiabilidad y la plataforma con auriculares de realidad mixta en torno a equipos inactivos y transiciones de estado de energía.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1 de mayo de 2019      | Compatible con Windows 10, la versión 1809 y versiones más recientes.<br/><ul><li>Contiene la actualización de firmware para auriculares 2017 Acer, ASUS, Dell, Fujitsu, HP, Lenovo y Medion Windows Mixed Reality. Esta actualización de firmware mejora la compatibilidad y la confiabilidad de la pantalla con ciertos adaptadores de gráficos o controladores de gráficos.</li><li>Mejoras en la confiabilidad y la plataforma con auriculares de realidad mixta de Windows</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versión 1803 (actualización de abril de 2018) y versión 1809 (actualización de octubre de 2018) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 de enero de 2019      | Compatible con Windows 10, la versión 1803 y versiones más recientes.<br/><ul><li>Correcciones de vibración de seguimiento y resaltos</li><li>Correcciones de confiabilidad del modo de linterna</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 de octubre de 2018      | Versión pública inicial del controlador para Windows 10, versión 1809.<br/>Compatible con Windows 10, la versión 1803 y versiones más recientes.<br/><ul><li>Habilita las nuevas características de Windows Mixed Reality, como el modo de linterna, en Windows 10, versión 1809</li><li>Mejoras en el seguimiento y la confiabilidad de los auriculares</li><li>Mejoras en el rendimiento y el seguimiento del controlador de movimiento</li><li>Rendimiento y mejoras de USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 de abril de 2018      | Versión pública inicial del controlador para Windows 10, versión 1803<br/> <ul><li>Mejoras en el seguimiento y la confiabilidad de los auriculares</li><li>Mejoras en el rendimiento y el seguimiento del controlador de movimiento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versión 1709 (Fall Creators Update) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 de febrero de 2018    | <ul><li>Compatibilidad oficial con 3Glasses Blubur S2 con auriculares de realidad mixta</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 de diciembre de 2017   | <ul><li>Resuelve un problema de HID que provoca *un* error en el código de error 2181038087-7 en algunos equipos.</li><li>Varias correcciones de estabilidad y confiabilidad</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 de diciembre de 2017    | <ul><li>Seguimiento mejorado del casco</li><li>Mejoras de la capacidad de respuesta de Touchpad de controlador de movimiento</li><li>Resuelve el problema por el que a veces se podría producir un error en la instalación del controlador</li><li>Varias correcciones de estabilidad y confiabilidad</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 de noviembre de 2017   | <ul><li>Resuelve un problema que provocaba que los auriculares se muestren a veces en negro durante el uso.</li><li>Resuelve un problema que a veces provocó la desapariencia de los controladores de movimiento</li><li>Mejoras en el rendimiento del sensor de presencia para el casco del parasol de Dell</li><li>Varias correcciones de estabilidad y confiabilidad</li></ul> |
   | 10.0.16299.1036  | 7 de noviembre de 2017    | <ul><li>Aumento de las mejoras del mecánico en el controlador de movimiento:<ul><li>La velocidad ahora se informará correctamente cuando la precisión de la posición sea aproximada, por lo que ahora puede iniciarse detrás de la cabeza.</li><li>El código de ejemplo para iniciar puede encontrarse [aquí](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)en el paquete de Unity "ThrowingStarter". Apertura de la escena de lanzamiento para empezar</li></ul></li><li>Informes mejorados de batería de controlador de movimiento</li><li>Varias correcciones de estabilidad y confiabilidad</li></ul> |
   | 10.0.16299.1012  | 17 de octubre de 2017    | Versión pública inicial del controlador                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Historial de versiones del controlador del modelo de controlador de movimiento de realidad mixta ###

Este controlador también se descarga e instala automáticamente a través de Windows Update, pero los vínculos de descarga se proporcionan en línea:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versión 2004 (actualización de mayo de 2020)

| Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 de septiembre de 2020      | Versión pública inicial del controlador para los nuevos controladores de movimiento de HP. Compatible con Windows 10, la versión 1903 y versiones más recientes. Este controlador solo es compatible con los nuevos controladores de movimiento de HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versión 1803 (actualización de abril de 2018) y versión 1809 (actualización de octubre de 2018) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 de octubre de 2018      | Versión pública inicial del controlador para Windows 10, versión 1809. Compatible con Windows 10, la versión 1803 y versiones más recientes.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 de abril de 2018      | Versión pública inicial del controlador para Windows 10, versión 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versión 1709 (Fall Creators Update) ####

   | Versión          | Fecha de la versión          | Principales cambios                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 de octubre de 2017    | Versión pública inicial del controlador                          |

### <a name="mixed-reality-portal-release-history"></a>Historial de versiones del portal de realidad mixta ###

En Windows 10, la versión 1809 y versiones más recientes, el [portal de realidad mixta](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) se actualiza a través de la aplicación Microsoft Store.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versión 1809 y versiones más recientes ####

   | Versión            | Fecha de la versión          | Principales cambios                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20111.1381.0  | 10 de diciembre de 2020        | <ul><li>Actualiza la página de aterrizaje del portal de realidad mixta.</li><li>Reduce los errores de conectividad con auriculares durante las actualizaciones de firmware. </li></ul>  |    | 2000.20071.1133.0  | 5 de agosto de 2020        | <ul><li>Compatibilidad con [OpenXR](/windows/mixed-reality/openxr) para pausar la ventana de vista previa.</li></ul>  | 
   | 2000.20071.1133.0  | 5 de agosto de 2020        | <ul><li>Compatibilidad con [OpenXR](/windows/mixed-reality/openxr) para pausar la ventana de vista previa.</li></ul>  | 
   | 2000.20041.1212.0  | 11 de mayo de 2020          | <ul><li>Soluciona un problema de control de tiempo que ha generado un error 15-5 incoherente.</li><li>Compatibilidad mejorada para ejecutar Windows Mixed Reality sin conexión a Internet.</li><li>Compatibilidad mejorada para emparejar controladores de movimiento a través de **controladores de instalación**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 de abril de 2020        | <ul><li>Compatibilidad con la suscripción para obtener información, sugerencias y ofertas sobre Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 de febrero de 2020     | <ul><li>Compatibilidad mejorada para aplicaciones que usan [OpenXR](/windows/mixed-reality/openxr) en dispositivos con la actualización de mayo de 2019.</li><li>Aborda los problemas de accesibilidad y foco de teclado</li></ul>  | 
   | 2000.19101.1211.0  | 11 de noviembre de 2019     | <ul><li>Soluciona un problema que impide alternar los objetos visuales de límite de la habitación.</li><li>Soluciona un problema que impide centrar un casco durante la configuración del límite de la habitación.</li></ul>  | 
   | 2000.19081.1301.0  | 23 de septiembre de 2019    | <ul><li>Soluciona un problema en el que se muestra un mensaje de error incorrecto en los auriculares con problemas de hardware. Los usuarios que recibieron un código de error 1-4 en versiones anteriores ahora pueden recibir un código de error más específico para su estado de dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 de agosto de 2019     | <ul><li>Compatibilidad con aplicaciones que usan [OpenXR](/windows/mixed-reality/openxr) en dispositivos con la actualización de mayo de 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 de julio de 2019         | <ul><li>Compatibilidad con opciones de configuración de JSON para personalizar el comportamiento de la aplicación. Lea más en https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Historial de versiones de SteamVR ###

Las notas de la versión de la válvula para SteamVR se pueden encontrar aquí: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Historial de versiones de Windows Mixed Reality para SteamVR ###

Las notas de la versión de Windows Mixed Reality para el componente SteamVR se pueden encontrar aquí: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)