---
title: Modo de investigación de HoloLens
description: Mediante el modo de investigación HoloLens, una aplicación puede acceder a flujos clave del sensor de dispositivo (profundidad, seguimiento del entorno y reflectividad de IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de investigación, cv, rs4, computer vision, research, HoloLens, HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193694"
---
# <a name="hololens-research-mode"></a>Modo de investigación de HoloLens

El modo de investigación se introdujo en dispositivos HoloLens (1.ª generación) para proporcionar acceso a sensores clave, específicamente para aplicaciones de investigación que no están diseñadas para la implementación.  El modo de investigación HoloLens 2 mantiene las funcionalidades de HoloLens 1, pero agrega acceso a las secuencias siguientes:

* **Cámaras de seguimiento visibles del entorno de** luz: cámaras de escala gris que usa el sistema para el seguimiento de la cabeza y la creación de mapas.
* **Cámara de profundidad:** funciona en dos modos:  
    + AHAT, de alta frecuencia (45 FPS) de detección a gran profundidad que se usa para el seguimiento de las manos. De forma diferente al modo de lanzamiento corto de la primera versión, AHAT proporciona pseudo-profundidad con ajuste de fase más allá de 1 medidor. 
    + Detección de profundidad lejana de lanzamiento largo y baja frecuencia (1-5 FPS) que usa [la asignación espacial](../../design/spatial-mapping.md)

* **Dos versiones de la secuencia de reflectividad de IR:** usadas por el HoloLens para calcular la profundidad. Estas imágenes se encienden por el calor y no se ven afectadas por la luz visible ambiente.

Si usa un HoloLens 2, también tiene acceso a las entradas adicionales siguientes:

* **Acelerómetro:** usado por el sistema para determinar la aceleración lineal a lo largo de los ejes X, Y y Z y gravedad.
* **Girón:** usado por el sistema para determinar las rotaciones.
* **Magnetometer:** usado por el sistema para calcular la orientación absoluta.

> [!IMPORTANT]
> El modo de investigación está actualmente en versión preliminar pública. 

![Captura de pantalla de la aplicación Modo de investigación](images/sensor-stream-viewer.jpg)<br>
*Captura de realidad mixta de una aplicación de prueba que muestra los ocho flujos de sensor disponibles en modo de investigación*

## <a name="usage"></a>Uso

El modo de investigación está diseñado para investigadores académicos e industriales que exploran nuevas ideas en los campos de Computer Vision y la Computer Vision.  No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través de Microsoft Store u otros canales de distribución.

Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se va a dar soporte en futuras actualizaciones de hardware o sistema operativo. Sin embargo, no deje que eso le detenga de usarlo para desarrollar y probar nuevas ideas.

## <a name="security-and-performance"></a>Seguridad y rendimiento

La habilitación del modo de investigación usa más batería que el HoloLens 2 en condiciones normales, incluso si la aplicación que usa las características del modo de investigación no se está ejecutando.  La habilitación de este modo también puede reducir la seguridad general del dispositivo porque las aplicaciones pueden hacer un uso incorrecto de los datos del sensor.  Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes HoloLens seguridad.](/hololens/hololens-faq-security)  

## <a name="device-support"></a>Compatibilidad con dispositivos
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>Primera generación de HoloLens</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Cámaras de seguimiento de la cabeza</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profundidad & ir cámara</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Acelerómetro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Giroscopio</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnetómetro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Habilitar el modo de investigación (HoloLens primera generación y HoloLens 2)

Modo de investigación es una extensión del modo de desarrollador. Antes de empezar, las características para desarrolladores del dispositivo deben estar habilitadas para acceder a la configuración del modo de investigación: 

* Abra **el menú Inicio > Configuración** y seleccione **Actualizaciones.**
* Seleccione **Para desarrolladores** y habilite **modo de desarrollador.**
* Desplázate hacia abajo y habilita **Portal de dispositivos**.

Una vez habilitadas las características del desarrollador, [conéctese al portal de dispositivos](/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación:

* Vaya a **System > Research Mode (Modo** de investigación del sistema) **Portal de dispositivos**.
* Seleccione **Permitir el acceso a la secuencia del sensor.**
* Reinicie el dispositivo desde el **elemento de** menú Energía de la parte superior de la página.

Una vez reiniciado el dispositivo, las aplicaciones cargadas a través **del** Portal de dispositivos pueden acceder a las secuencias del modo de investigación.

![Pestaña Modo de investigación de HoloLens Portal de dispositivos](images/ResearchModeDevPortal.png)<br>
*Ventana Modo de investigación en la HoloLens Portal de dispositivos*

> [!IMPORTANT]
> El modo de investigación HoloLens 2 está disponible a partir de la compilación 19041.1364 . Si necesita acceso en una compilación anterior, regístrese en nuestro programa [Insider Preview.](/hololens/hololens-insider) Puede encontrar más detalles en El modo [de investigación GitHub repositorio](https://github.com/microsoft/HoloLens2ForCV).

### <a name="using-sensor-data-in-your-apps"></a>Uso de datos de sensor en las aplicaciones

Las aplicaciones pueden acceder a los datos del flujo de sensor de la misma manera [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) acceso a las secuencias de cámara de fotos y vídeo. 

Todas las API que funcionan para el desarrollo HoloLens también están disponibles en modo de investigación. En concreto, la aplicación sabe con precisión HoloLens está en el espacio 6DoF en cada tiempo de captura del fotograma del sensor.

Tenemos aplicaciones de ejemplo que muestran el acceso a secuencias en modo de investigación, usando los intrínsecos y [extrínsecos,](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)y registrando secuencias:
* [HoloLens (primera generación)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Soporte técnico

Para HoloLens (primera generación), [](https://github.com/Microsoft/HololensForCV/issues) use el seguimiento de problemas en el repositorio HoloLensForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.

Por HoloLens 2, use el seguimiento [de](https://github.com/microsoft/HoloLens2ForCV/issues) problemas en el repositorio HoloLens2ForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.

## <a name="see-also"></a>Consulte también

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [Repositorio de GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Repositorio de GitHub HoloLens2ForCV](https://github.com/microsoft/HoloLens2ForCV)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)