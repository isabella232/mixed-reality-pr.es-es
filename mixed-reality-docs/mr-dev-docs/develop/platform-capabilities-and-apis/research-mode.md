---
title: Modo de investigación de HoloLens
description: Con el modo de investigación en HoloLens, una aplicación puede acceder a las secuencias de sensor del dispositivo clave (profundidad, seguimiento del entorno y interreflectividad de INFRARROJOs).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modo de investigación, CV, RS4, Computer Vision, investigación, HoloLens, HoloLens 2
ms.openlocfilehash: 6737f9b668b73258e65f8d00e85dcd19c28ddfb5
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237136"
---
# <a name="hololens-research-mode"></a>Modo de investigación de HoloLens

El modo de investigación se presentó en los dispositivos de HoloLens (primera generación) para dar acceso a los sensores clave, específicamente para las aplicaciones de investigación que no están pensadas para la implementación.  El modo de investigación de HoloLens 2 mantiene las capacidades de HoloLens 1, pero agrega acceso a los siguientes flujos:

* **Cámaras de seguimiento de entornos claros visibles** : cámaras de escala de grises usadas por el sistema para el seguimiento de los cabezales y el edificio de mapas.
* **Cámara de profundidad** : funciona en dos modos:  
    + Detección de profundidad de AHAT, alta frecuencia (45 FPS) utilizada para el seguimiento manual. De forma diferente al modo de inicio de la primera versión, AHAT proporciona una pseudo profundidad con ajuste de fase superior a 1 medidor. 
    + Detección de profundidad larga de baja frecuencia (1-5 FPS) usada por la [asignación espacial](../../design/spatial-mapping.md)

* **Dos versiones de la secuencia ir-reflectividad** : usadas por HoloLens para calcular la profundidad. Estas imágenes se iluminan por infrarrojos y no se ven afectadas por la luz visible de ambiente.

Si usa HoloLens 2, también tiene acceso a las entradas adicionales siguientes:

* **Acelerómetro** : lo usa el sistema para determinar la aceleración lineal a lo largo de los ejes X, y y Z y la gravedad.
* **Gyro** : el sistema lo usa para determinar los giros.
* **Magnetómetro** : lo usa el sistema para calcular la orientación absoluta.

> [!IMPORTANT]
> El modo de investigación está actualmente en versión preliminar pública. 

![Captura de pantalla de la aplicación de modo de investigación](images/sensor-stream-viewer.jpg)<br>
*Una captura de realidad mixta de una aplicación de prueba que muestra ocho flujos de sensor disponibles en el modo de investigación*

## <a name="usage"></a>Uso

El modo de investigación está diseñado para investigadores académicos e industriales que exploran ideas nuevas en los campos de Computer Vision y robótica.  No está diseñado para aplicaciones implementadas en entornos empresariales o disponibles a través del Microsoft Store u otros canales de distribución.

Además, Microsoft no proporciona garantías de que el modo de investigación o la funcionalidad equivalente se admitirán en futuras actualizaciones de hardware o del sistema operativo. Sin embargo, no deje que le dejen de usarlo para desarrollar y probar ideas nuevas.

## <a name="security-and-performance"></a>Seguridad y rendimiento

Al habilitar el modo de investigación se usa más energía de la batería que el uso de HoloLens 2 en condiciones normales, aunque no se esté ejecutando la aplicación que usa las características del modo de investigación.  Habilitar este modo también puede reducir la seguridad general del dispositivo, ya que las aplicaciones pueden hacer uso indebido de los datos del sensor.  Puede encontrar más información sobre la seguridad de los dispositivos en las [preguntas más frecuentes sobre seguridad de HoloLens](/hololens/hololens-faq-security).  

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
        <td>Cámaras de seguimiento de cabezales</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profundidad & cámara de INFRARROJOs</td>
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

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Habilitación del modo de investigación (HoloLens First gen y HoloLens 2)

El modo de investigación es una extensión del modo de programador. Antes de comenzar, las características del desarrollador del dispositivo deben estar habilitadas para tener acceso a la configuración del modo de investigación: 

* Abra el **menú inicio > configuración** y seleccione **actualizaciones**.
* Seleccione **para desarrolladores** y habilite el **modo de desarrollador**.
* Desplázate hacia abajo y habilita **Portal de dispositivos**.

Una vez habilitadas las características de desarrollador, [Conéctese al portal de dispositivos](/windows/uwp/debug-test-perf/device-portal-hololens) para habilitar las características del modo de investigación:

* Vaya al **modo System > Research** en el **portal de dispositivos**.
* Seleccione **permitir el acceso a la secuencia del sensor**.
* Reinicie el dispositivo desde el elemento de menú de **energía** en la parte superior de la página.

Una vez que haya reiniciado el dispositivo, las aplicaciones que se cargan a través del **portal de dispositivos** pueden acceder a los flujos del modo de investigación.

![Pestaña del modo de investigación del portal de dispositivos de HoloLens](images/ResearchModeDevPortal.png)<br>
*Ventana del modo de investigación en el portal de dispositivos de HoloLens*

> [!IMPORTANT]
> El modo de investigación de HoloLens 2 está disponible a partir de la compilación 19041,1364. Si necesita tener acceso en una compilación anterior, Regístrese en el programa de [versión preliminar de Insider](/hololens/hololens-insider) . Puede encontrar más detalles en el [repositorio de github del modo de investigación](https://github.com/microsoft/HoloLens2ForCV).

### <a name="using-sensor-data-in-your-apps"></a>Uso de datos de sensor en las aplicaciones

Las aplicaciones pueden tener acceso a los datos del flujo del sensor de la misma manera que [Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk) accede a las secuencias de la cámara de vídeo y de fotos. 

Todas las API que funcionan con el desarrollo de HoloLens también están disponibles en el modo de investigación. En concreto, la aplicación sabe exactamente dónde se encuentra HoloLens en el espacio 6DoF en cada tiempo de captura de fotogramas del sensor.

Tenemos aplicaciones de ejemplo en las que se muestra el acceso a secuencias en modo de referencia, con los [intrínsecos y extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)y las secuencias de registro:
* [HoloLens (primera generación)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Soporte técnico

Para HoloLens (primera generación), use el [seguimiento de problemas](https://github.com/Microsoft/HololensForCV/issues) en el repositorio de HoloLensForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.

Para HoloLens 2, use el [seguimiento de problemas](https://github.com/microsoft/HoloLens2ForCV/issues) en el repositorio de HoloLens2ForCV para publicar comentarios y realizar un seguimiento de los problemas conocidos.

## <a name="see-also"></a>Consulte también

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [Repositorio de GitHub de HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Repositorio de GitHub de HoloLens2ForCV](https://github.com/microsoft/HoloLens2ForCV)
* [Uso del Portal de dispositivos Windows](using-the-windows-device-portal.md)