---
title: Información general de software e historial de versiones
description: Información general de los principales componentes de software para Windows Mixed Reality, cascos envolventes y su historial de versiones.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, componentes de software, historial de versiones, notas de la versión, historial de versiones
appliesto:
- Windows 10
ms.openlocfilehash: 2d11a43e96843073bf86919f1c4a10425fa12c00
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741917"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Información general de software de Mixed Reality e historial de versiones

## <a name="introduction-to-mixed-reality-software"></a>Introducción a Mixed Reality software

Windows Mixed Reality consta de los siguientes componentes de software principales:

1. **Portal de realidad mixta**, que proporciona la experiencia Windows Mixed Reality principal
    * En Windows 10 versiones 1709 y 1803, Portal de realidad mixta es un componente clave del sistema operativo Windows 10 actualizado a través de Windows Update.
    * En Windows 10 versión 1809 y versiones más recientes, Portal de realidad mixta se actualiza a través de la Microsoft Store aplicación.
2. El **Mixed Reality paquete de** características a petición (FOD), que se descarga e instala automáticamente durante Portal de realidad mixta primera ejecución del paquete. Puede encontrar más información sobre el paquete FOD [aquí.](/windows/application-management/manage-windows-mixed-reality)
3. El **controlador Mixed Reality** casco y controlador de movimiento de Mixed Reality, también conocido como controlador holoLens Sensors, es el paquete de controladores clave que permite que los cascos Windows Mixed Reality funcionen con Windows Mixed Reality. Se descarga e instala automáticamente a través de Windows Update la primera vez que el casco de Mixed Reality está conectado y se actualiza periódicamente a través de Windows Update
4. Los controladores de Mixed Reality de controlador de movimiento **contienen los modelos 3D de los controladores de movimiento de Mixed Reality y son necesarios para experiencias de Mixed Reality de terceros. Se descarga e instala automáticamente a través de Windows Update la primera vez que los controladores de movimiento de Mixed Reality se emparejan con el equipo y se actualiza a través de Windows Update
5. **Windows 10, la versión 1709 (Fall Creator's Update)** o posterior contiene componentes y tecnologías clave del sistema operativo que permiten Windows Mixed Reality

El Windows Mixed Reality en SteamVR requiere el siguiente software:

6. **SteamVR,** desarrollado y mantenido por Valve Corporation que permite aplicaciones y juegos de realidad virtual en Steam. Puede obtener más información [aquí](https://go.microsoft.com/fwlink/?linkid=862788)
7. El **Windows Mixed Reality componente de SteamVR,** que une SteamVR con Windows Mixed Reality. Puede encontrar más información sobre este componente en [la Windows Mixed Reality para SteamVR.](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

Administración del casco Windows Mixed Reality de conexión:

8. La **aplicación complementaria de dispositivos,** desarrollada y mantenida por cada uno de los fabricantes de cascos, proporciona una introducción rápida a los cascos Windows Mixed Reality dispositivos. En los cascos con funcionalidad Bluetooth integrada, la aplicación Device Companion permite restaurar controladores de movimiento a su emparejamiento Bluetooth de fábrica. Algunos cascos (como Samsung Samsung Samsung y Samsung Samsung Samsung+) también usan la aplicación Device Companion para entregar actualizaciones de firmware del casco del fabricante del casco. Esta aplicación se descarga automáticamente la primera vez que se conecta el casco y se puede encontrar en el menú Inicio de Windows.

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 notas de la versión: mayo de 2020

La actualización de Windows 10 mayo de **2020 (v2004)** incluye nuevas características para los cascos de Windows Mixed Reality (VR), como la capacidad de iniciar aplicaciones Win32 en el ambiente principal. HoloLens (1.ª generación) está en mantenimiento a largo plazo (LTS), con actualizaciones de mantenimiento que se lanzarán mensualmente.

Al actualizar a la versión más reciente del equipo para Windows Mixed Reality cascos envolventes (VR), abra Configuración > **Update & Security** y seleccione Buscar **actualizaciones.** En un Windows 10, también puede instalar manualmente la actualización de Windows 10 mayo **de 2020** mediante la herramienta de creación [de medios de Windows](https://www.microsoft.com/software-download/windows10).

**Versión más reciente de Desktop:** Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Actualizaciones de cascos Windows Mixed Reality envolventes

#### <a name="introducing-the-new-microsoft-edge"></a>Presentación de la nueva Microsoft Edge

Como [se anunció anteriormente,](/windows/mixed-reality/new-microsoft-edge)hemos realizado actualizaciones para mejorar la compatibilidad con el uso del nuevo explorador Microsoft Edge en Windows Mixed Reality. El nuevo Microsoft Edge adopta el proyecto de código abierto Chromium para crear una mejor compatibilidad web para los clientes y una menor fragmentación de la web para todos los desarrolladores web. También admite WebXR, el nuevo estándar para crear experiencias web envolventes para cascos vr, en lugar de WebVR.

#### <a name="improved-settings-for-wmr"></a>Configuración mejorada para WMR

Gracias a sus comentarios, hemos agregado y aclarado la configuración en la página de presentación del casco:

* **Calidad visual de mi hogar:** el cambio de esta configuración solo afecta al entorno ambiente principal (Casa sobre el acantilado y Skyloft):

* **Ajuste el nivel de detalle y la** calidad de los efectos en el ambiente principal: esto cambia parte de la representación que afecta al uso en el hogar. En concreto, la calidad visual de los distintos materiales (bosque, concreto, entre otros) se escalará a medida que cambie esta configuración de baja a alta.

* **Cambiar la resolución de la** ventana de la aplicación: de forma predeterminada, la mayoría de las ventanas 2D iniciadas en la página principal se inician con una resolución de 720 p. Aunque puede cambiar el tamaño horizontalmente & verticalmente, también puede optar por que todos se inicien a 1080p en su lugar. Anteriormente, esta opción estaba disponible como opción Muy alta (beta) en Calidad visual. Lo hemos dividido correctamente como una configuración independiente ahora.

* **Opciones de experiencia:** estas opciones ajustan la experiencia de realidad mixta para reducir la carga en sistemas en los que el hardware podría tener dificultades para mantenerse al día con 90 fps sin restricciones. Puede habilitar o deshabilitar explícitamente esta configuración adicional, o bien elegir Permitir que Windows decida y dejar que nuestra heurística siga decidiendo cuándo activarlas y desactivarlas.

* **Resolución:** si tiene un casco de alta resolución como HP Reverb, se admite su ejecución en su resolución nativa o a una resolución reducida por motivos de rendimiento. Los cascos anteriores, como Samsung Samsung Samsung y Samsung Samsung+ , solo admiten una única resolución, por lo que no se puede cambiar esta configuración en esos cascos.

* **Velocidad de** fotogramas: ahora puede establecer manualmente la velocidad de fotogramas de la pantalla del casco, o bien seguir haciendo que Windows use su heurística para determinar si 60 Hz o 90 Hz es más adecuado.

* **Calibración:** como antes, puede ajustar el IPD (distancia interpupillaria) si lo admite el casco.

* **Conmutación de entrada:** alterne el comportamiento de cambio de foco de entrada (Win+Y) para que sea automático (en función de los comentarios del sensor de presencia) o manual.

#### <a name="new-cortana-app"></a>Nueva aplicación Cortana

Esta actualización de Windows incluye la versión más reciente de la aplicación Cortana, que actualmente es solo en inglés de Estados Unidos y ya no admite determinados comandos específicos de realidad mixta, como "Tomar una imagen" y "Tomar un vídeo". Puede usar la nueva Cortana para iniciar aplicaciones y también admite nuevos comandos centrados en la productividad, como "¿Cuándo es mi próxima reunión?". o "Enviar un correo <name> electrónico a que se está ejecutando tarde".
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>Actualizaciones adicionales en disponibles en la versión 19041.546 (publicada en octubre de 2020)

Esta actualización de mantenimiento mensual de escritorio incluye los siguientes cambios para Windows Mixed Reality dispositivos: 
* Reduce las distorsiónes y las aberraciones Windows Mixed Reality pantallas montadas en la cabeza (HMD). 
* Agrega compatibilidad con los próximos controladores de movimiento Windows Mixed Reality HP. 
* Cambia el comportamiento de la configuración de frecuencia de actualización de 90 Hz en Windows Mixed Reality para que ya no vuelva automáticamente a 60 Hz en determinados casos cuando no se puede lograr 90 Hz. 

#### <a name="help-us-improve"></a>¡Ayúdenos a mejorar!

Buscamos continuamente mejorar la compatibilidad.  Si encuentra que su aplicación Win32 clásica favorita no se comporta correctamente mientras está en Windows Mixed Reality, envíe comentarios a través de [nuestro Centro de opiniones](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

### <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión: mayo de 2019](release-notes-may-2019.md)
* [Notas de la versión (octubre de 2018)](release-notes-october-2018.md)
* [Notas de la versión: abril de 2018](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Mixed Reality de lanzamiento del controlador de movimiento y casco ###

Este controlador se descarga e instala automáticamente a través de Windows Update, pero los vínculos de descarga se proporcionan en línea:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versión 2004 (actualización de mayo de 2020) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2041](https://www.microsoft.com/download/details.aspx?id=102903)  | 23 de marzo de 2021  | Compatible con Windows 10, versión 1903 y versiones más recientes.<br/><ul><li>Actualice el orden de sinuoso de la malla de área oculta para que HP Reverb G2 sea coherente con otros cascos.</li><li>Mejoras en la calidad de los objetos visuales para los cascos HP Reverb G2.</li><li>Windows Mixed Reality plataforma de cascos y mejoras de confiabilidad.</li>|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 10 de diciembre de 2020  | Compatible con Windows 10, versión 1903 y versiones más recientes.<br/><ul><li>Nuevo firmware del controlador de HP para solucionar un problema en el que algunos controladores tienen desencadenadores que no funcionan.</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 8 de octubre de 2020  | Compatible con Windows 10, versión 1903 y versiones más recientes.<br/><ul><li>Compatibilidad oficial con HP Reverb G2, HP Omnicept y el nuevo controlador hp.</li><li>Correcciones de pantalla secundarias para los cascos HP Reverb y Samsung Samsung+ . (Requiere la compilación del sistema operativo [19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) o superior o las compilaciones del sistema operativo [18362.1110 y 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) o superior).</li><li>Mejoras en la transición del estado de energía del equipo de suspensión para reducir los errores de SWW 1-4.</li><li>Windows Mixed Reality correcciones secundarias de la plataforma de cascos y mejoras de confiabilidad.|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 7 de mayo de 2020      | Compatible con Windows 10, versión 1903 y versiones más recientes.<br/><ul><li>Windows Mixed Reality correcciones secundarias de la plataforma de cascos y mejoras de confiabilidad.</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10, versión 1903 (actualización de mayo de 2019) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 14 de octubre de 2019      | Compatible con Windows 10, versión 1809 y versiones más recientes.<br/><ul><li>Windows Mixed Reality correcciones secundarias de la plataforma de cascos.</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 24 de junio de 2019      | Compatible con Windows 10, versión 1809 y versiones más recientes.<br/><ul><li>Windows Mixed Reality plataforma de cascos y mejoras de confiabilidad en torno a equipos en estado de inmoción y transiciones de estado de energía.</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 1 de mayo de 2019      | Compatible con Windows 10, versión 1809 y versiones más recientes.<br/><ul><li>Contiene la actualización de firmware para los cascos de Windows Mixed Reality 2017 Acer, Conmutadore, Dell,Certtsu, HP, Hp y Medion. Esta actualización de firmware mejora la compatibilidad y confiabilidad de las pantallas de los cascos con determinados adaptadores de gráficos o controladores de gráficos.</li><li>Windows Mixed Reality de la plataforma de casco y las mejoras de confiabilidad</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versión 1803 (actualización de abril de 2018) y versión 1809 (actualización de octubre de 2018) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2 de enero de 2019      | Compatible con Windows 10, versión 1803 y versiones más recientes.<br/><ul><li>Correcciones de vibración y vibración de seguimiento de cascos</li><li>Correcciones de confiabilidad del modo de la luz de la mano</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 1 de octubre de 2018      | Versión pública inicial del controlador para Windows 10, versión 1809.<br/>Compatible con Windows 10, versión 1803 y versiones más recientes.<br/><ul><li>Habilita nuevas características Windows Mixed Reality, como el modo de la luz, en Windows 10, versión 1809</li><li>Mejoras de confiabilidad y seguimiento de cascos</li><li>Mejoras de rendimiento y seguimiento del controlador de movimiento</li><li>Mejoras y rendimiento de USB</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 27 de abril de 2018      | Versión pública inicial del controlador para Windows 10, versión 1803<br/> <ul><li>Mejoras de confiabilidad y seguimiento de cascos</li><li>Mejoras de rendimiento y seguimiento del controlador de movimiento</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versión 1709 (Fall Creators Update) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 6 de febrero de 2018    | <ul><li>Compatibilidad oficial con 3GlassesBur S2 Mixed Reality casco</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 19 de diciembre de 2017   | <ul><li>Resuelve el problema de HID que conduce *a* código de error 2181038087-7 en algunos equipos</li><li>Diversas correcciones de estabilidad y confiabilidad</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 5 de diciembre de 2017    | <ul><li>Seguimiento mejorado de cascos</li><li>Mejoras en la capacidad de respuesta del panel táctil del controlador de movimiento</li><li>Resuelve el problema por el que a veces se podía producir un error en la instalación del controlador</li><li>Diversas correcciones de estabilidad y confiabilidad</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 21 de noviembre de 2017   | <ul><li>Resuelve un problema que provocó que las pantallas de los cascos a veces se en negro durante el uso</li><li>Resuelve un problema que a veces ha provocado que los controladores de movimiento desaparezcan.</li><li>Mejoras de rendimiento del sensor de presencia para el casco de Dell Visor</li><li>Diversas correcciones de estabilidad y confiabilidad</li></ul> |
   | 10.0.16299.1036  | 7 de noviembre de 2017    | <ul><li>Mejoras mecánicas en el controlador de movimiento:<ul><li>Ahora, la velocidad se notifica correctamente cuando la precisión de la posición es aproximada, por lo que ahora puede iniciar detrás de la cabeza.</li><li>Puede encontrar código de ejemplo para iniciar en el paquete de Unity "ThrowingStarter" [aquí.](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/) Abra la escena de lanzamiento para empezar.</li></ul></li><li>Informes mejorados de batería del controlador de movimiento</li><li>Diversas correcciones de estabilidad y confiabilidad</li></ul> |
   | 10.0.16299.1012  | 17 de octubre de 2017    | Versión pública inicial del controlador                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Mixed Reality de lanzamiento del controlador de modelo de movimiento ###

Este controlador también se descarga e instala automáticamente a través de Windows Update, pero los vínculos de descarga se proporcionan en línea:

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10, versión 2004 (actualización de mayo de 2020)

| Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 16 de septiembre de 2020      | Versión pública inicial del controlador para los nuevos controladores de movimiento de HP. Compatible con Windows 10, versión 1903 y versiones más recientes. Este controlador solo es compatible con los nuevos controladores de movimiento de HP.  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10, versión 1803 (actualización de abril de 2018) y versión 1809 (actualización de octubre de 2018) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 1 de octubre de 2018      | Versión pública inicial del controlador para Windows 10, versión 1809. Compatible con Windows 10, versión 1803 y versiones más recientes.  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 17 de abril de 2018      | Versión pública inicial del controlador para Windows 10, versión 1803.  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10, versión 1709 (Fall Creators Update) ####

   | Versión          | Fecha de la versión          | Cambios importantes                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 17 de octubre de 2017    | Versión pública inicial del controlador                          |

### <a name="mixed-reality-portal-release-history"></a>Portal de realidad mixta historial de versiones ###

En Windows 10, versión 1809 y versiones [más recientes, Portal de realidad mixta](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) se actualiza a través de Microsoft Store aplicación.

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10, versión 1809 y versiones más recientes ####

   | Versión            | Fecha de la versión          | Cambios importantes                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.21051.1282.0  | 8 de junio de 2021          | <ul><li>Agrega vínculos de solución de problemas a Obtener ayuda aplicación para los errores comunes de los cascos.</li><li>Soluciona un problema por el que la aplicación complementaria del dispositivo de casco podría omitirse durante la configuración inicial.</li><li>Actualiza la página de requisitos del sistema con información adicional para cascos de alta resolución.</li><li>Actualiza la pantalla de presentación y la página de aterrizaje con nuevos objetos visuales.</li></ul>  |
   | 2000.21041.1051.0  | 26 de abril de 2021        | <ul><li>Actualiza el icono de aplicación para Portal de realidad mixta.</li></ul>  |
   | 2000.20111.1381.0  | 10 de diciembre de 2020     | <ul><li>Actualiza la página de aterrizaje de Portal de realidad mixta.</li><li>Reduce los errores de conectividad de los cascos durante las actualizaciones de firmware. </li></ul>  |
   | 2000.20071.1133.0  | 5 de agosto de 2020        | <ul><li>Compatibilidad con [OpenXR para](/windows/mixed-reality/openxr) pausar la ventana de vista previa.</li></ul>  | 
   | 2000.20041.1212.0  | 11 de mayo de 2020          | <ul><li>Soluciona un problema de tiempo que provocaba un error incoherente de 15 a 5.</li><li>Compatibilidad mejorada para ejecutar Windows Mixed Reality sin conexión a Internet.</li><li>Compatibilidad mejorada para emparejar controladores de movimiento a través **de controladores de configuración**.</li></ul>  | 
   | 2000.20031.1202.0  | 14 de abril de 2020        | <ul><li>Soporte técnico para registrarse para obtener información, sugerencias y ofertas sobre Windows Mixed Reality.</li></ul>  | 
   | 2000.20011.1312.0  | 11 de febrero de 2020     | <ul><li>Compatibilidad mejorada con aplicaciones que usan [OpenXR](/windows/mixed-reality/openxr) en dispositivos con la actualización de mayo de 2019.</li><li>Aborda los problemas de accesibilidad y foco de teclado</li></ul>  | 
   | 2000.19101.1211.0  | 11 de noviembre de 2019     | <ul><li>Soluciona un problema que impide alternar los objetos visuales de límite de la sala.</li><li>Soluciona un problema que impide centrar un casco durante la configuración de los límites de la sala.</li></ul>  | 
   | 2000.19081.1301.0  | 23 de septiembre de 2019    | <ul><li>Soluciona un problema por el que se mostró un mensaje de error incorrecto a los cascos con problemas de hardware. Los usuarios que recibieron un código de error 1 a 4 en versiones anteriores ahora pueden recibir un código de error más específico para su estado de dispositivo.</li></ul>  |
   | 2000.19071.1302.0  | 13 de agosto de 2019     | <ul><li>Compatibilidad con aplicaciones que [usan OpenXR](/windows/mixed-reality/openxr) en dispositivos con la actualización de mayo de 2019.</li></ul>  | 
   | 2000.19061.1011.0  | 16 de julio de 2019         | <ul><li>Compatibilidad con las opciones de configuración de JSON para personalizar el comportamiento de la aplicación. Obtenga más información en https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup .</li></ul>  | 

### <a name="steamvr-release-history"></a>Historial de versiones de SteamVR ###

Las notas de la versión de Valve para SteamVR se pueden encontrar aquí: [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>Windows Mixed Reality para el historial de versiones de SteamVR ###

Nuestras notas de la versión para Windows Mixed Reality componente de SteamVR se pueden encontrar aquí: [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
