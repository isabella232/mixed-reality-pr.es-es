---
title: Audio en realidad mixta
description: El audio en realidad mixta puede aumentar la confianza del usuario en las interacciones de la interfaz de usuario y insociar a los usuarios en la experiencia.
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3d, sonido 3d, audio espacial, casco de realidad mixta, casco de windows de realidad mixta, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit, casos prácticos, acústica
ms.openlocfilehash: 75b87098f90611140d2c43bb596e7c5d50dab9c47fc49426d5bcbbe0095c3847
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188825"
---
# <a name="audio-in-mixed-reality"></a>Audio en realidad mixta

El audio es una parte esencial del diseño y la productividad en la realidad mixta. El sonido puede:
* Aumentar la confianza del usuario en las interacciones de gestos y voz.
* Guía a los usuarios para los pasos siguientes.
* Combine eficazmente objetos virtuales con el mundo real.

El seguimiento de la cabeza de baja latencia de los cascos de realidad mixta, incluido HoloLens, admite la espacialización basada en HRTF de alta calidad. Puede espacializar el audio en la aplicación para:
* Llame la atención sobre los elementos visuales.
* Ayudar a los usuarios a conocer su entorno real.

La acústica conecta más profundamente los hologramas al mundo de la realidad mixta. Proporciona indicaciones sobre el entorno y el estado del objeto.

Vea ejemplos detallados [de diseño que usan audio](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (primera generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Espacialización</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Aceleración de hardware de espacialización</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso de sonidos en realidad mixta

[El uso de sonidos en realidad mixta](spatial-sound-design.md) requiere un enfoque diferente al de las aplicaciones táctiles y de teclado y mouse. Entre las decisiones clave de diseño de sonido se incluyen los sonidos que se espacializan y qué interacciones sonificar. Estas decisiones tienen un efecto fuerte en la confianza del usuario, la productividad y la curva de aprendizaje.

### <a name="case-studies"></a>Casos prácticos

HoloTour lleva virtualmente a los usuarios a sitios históricos y populares de todo el mundo. Consulte el caso práctico Diseño de sonido [para HoloTour.](case-study-spatial-sound-design-for-holotour.md) Se usó un micrófono especial y una configuración de representación para capturar los espacios de asunto.

RoboRaid es un sistema de energía alta para HoloLens. El caso práctico Diseño de sonido para [RoboRaid](case-study-using-spatial-sound-in-roboraid.md) describe las opciones de diseño que se realizaron para garantizar que el audio espacial se usó al máximo efecto drástico.

## <a name="spatialization"></a>Espacialización

La espacialización es el componente direccional del audio espacial. Para una configuración de 7.1 home,1, la espacialización es tan sencilla como el movimiento panorámico entre los altavoces. Pero para los cascos de realidad mixta, es esencial usar una tecnología basada en HRTF para la precisión y la comodidad. Windows ofrece espacialización basada en HRTF y esta compatibilidad se acelera por hardware en HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>¿Debo espacializar?

La espacialización puede mejorar muchos sonidos en aplicaciones de realidad mixta. La espacialización saca un sonido de la cabeza del agente de escucha y lo coloca en el mundo. Para obtener sugerencias sobre el uso eficaz de la espacialización en la aplicación, consulte [Diseño de sonido espacial.](spatial-sound-design.md)

### <a name="spatializer-personalization"></a>Personalización del espacializador

Los HRF manipulan las diferencias de nivel y fase entre las manos en el espectro de frecuencia. Se basan en modelos físicos y medidas de formas humanas de cabeza, torso y oído (pinnae). Nuestros cerebros responden a estas diferencias para proporcionar una dirección percibida en el sonido.

Cada individuo tiene una forma de oído única, el tamaño de la cabeza y la posición del oído. Por lo tanto, los mejores HRFS se ajustan a usted. Para aumentar la precisión de la espacialización, HoloLens la distancia interespatilaria (IPD) de las pantallas de los cascos para ajustar los HRFS para el tamaño de la cabeza.

### <a name="spatializer-platform-support"></a>Compatibilidad con la plataforma de espacializador

Windows espacialización, incluidos los HRF, a través de [la API ISpatialAudioClient](/windows/win32/coreaudio/spatial-sound). Esta API expone la aceleración de hardware HoloLens 2 HRTF a las aplicaciones.

### <a name="spatializer-middleware-support"></a>Compatibilidad con middleware de espacializador

La compatibilidad con Windows HRF de Windows está disponible para los siguientes motores de audio de terceros.
* Un [complemento del motor de audio de Unity](../develop/unity/spatial-sound-in-unity.md)
* Un [complemento del motor de audio de Wwise](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acústica

El audio espacial es más que una dirección. Otras dimensiones incluyen la oclusión, la obstrucción, la reverberación, el portal y el modelado de origen. Colectivamente, estas dimensiones se conocen como *acústicas.* Sin acústica, los sonidos espacializados carecen de distancia percibida.

Los tratamientos acústicos van de simple a complejo. Puede usar una reverberación compatible con cualquier motor de audio para insertar sonidos espacializados en el entorno del agente de escucha. Los sistemas acústicos [como Project Acoustics](/gaming/acoustics/what-is-acoustics) proporcionan un tratamiento acústico más completo y atractivo. Project La acústica puede modelar el efecto de las paredes, las puertas y otra geometría de la escena en un sonido. Es una opción eficaz para los casos en los que la geometría de la escena pertinente se conoce en tiempo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes

- [Sonido espacial en Unity](../develop/unity/spatial-sound-in-unity.md)
- [Uso del sonido en aplicaciones de realidad mixta](spatial-sound-design.md)