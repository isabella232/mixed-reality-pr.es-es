---
title: Preguntas más frecuentes sobre rendimiento
description: Solución de Windows Mixed Reality de rendimiento que va más allá de la documentación de soporte técnico estándar del consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Performance
appliesto:
- Windows 10
ms.openlocfilehash: 6754923a07d4c75c6f0f44aad07c5d3c55c28ae4673900531d8a4af663d9e7c2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219421"
---
# <a name="performance-faqs"></a>Preguntas más frecuentes sobre rendimiento

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>¿Es mi Windows Mixed Reality casco a una velocidad de fotogramas de 60 Hz o 90 Hz?

Si tiene una GPU discreta con puertos HDMI 2.0 y una CPU con cuatro o más núcleos físicos, debería obtener 90 Hz. Para confirmarlo, compruebe la **Portal de dispositivos > Rendimiento.**

Nota: Si la GPU solo tiene una salida HDMI 1.4, puede usar un adaptador DisplayPort a [HDMI 2.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) como solución alternativa.

Nota: La configuración de calidad visual de "Pantalla del casco" solo afecta a la representación de la Windows Mixed Reality de inicio.

## <a name="my-pc-is-running-slowly"></a>Mi PC se ejecuta lentamente

El sistema puede ser lento por muchas razones, lo que suele durar solo unos segundos. Si experimenta este problema durante largos períodos de tiempo:

1. Cierre todas las aplicaciones no usadas en el escritorio.
2. Asegúrese de que el portátil está conectado a una fuente de alimentación.
3. Asegúrese de que el equipo no se está entrenando.
4. Reduzca la calidad visual de su Windows Mixed Reality inicio.
5. Asegúrese de que tiene los controladores de [gráficos más recientes](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) para el equipo.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mi PC se está entrenando a medida que se ejecutan las Mixed Reality experiencias. Cómo mantener la refrigeración

1. Compruebe que la batería está cargada y que la fuente de alimentación está conectada.
2. Asegúrese de que los ventiladores del equipo no están bloqueados.
3. Use el equipo en un entorno relativamente es cool.
4. Asegúrese de que no hay ninguna fuente de calor (por ejemplo, el sol o los rayos térmicos) que apuntan al equipo.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mis objetos visuales son descuartados, se cargan lentamente o no se ven bien

* Asegúrese de que el casco está conectado a la tarjeta gráfica correcta del equipo. Algunos equipos tienen tarjetas gráficas integradas y discretas. Por lo general, la tarjeta discreta proporcionará el mejor rendimiento. [Obtenga más información sobre el hardware del equipo.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Cierre las aplicaciones no usadas en el escritorio.
* Asegúrese de que el casco se ajusta perfectamente (muévelo hacia abajo y hacia arriba, o a la izquierda y a la derecha, para ajustarlo).
* Ajuste la configuración visual del casco en Configuración > **pantalla Mixed reality > Headset (Casco).** Cuando "Calidad visual" se establece en "Automático", la experiencia de realidad mixta para el equipo se elegirá automáticamente. Para obtener más detalles visuales, establezca "Calidad visual" en "Alta". Si los objetos visuales están descuartados, seleccione una configuración inferior.
* Ajuste el mando de calibración del casco para asegurarse de que las lentes están establecidas en la distancia correcta entre las alumno (denominada IPD). Si no conoce el IPD, un optometrista puede medirlo por usted o usar un sitio web diseñado para medir el IPD. Si el casco no tiene un mando de calibración, seleccione Configuración > **Mixed reality > Headset display** (Pantalla del casco de realidad mixta) y ajuste el "control de calibración".
* Si usa un adaptador USB-C o DisplayPort a HDMI, pruebe otro diferente. Consulte [los adaptadores recomendados.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Desconecte los monitores adicionales que puedan estar conectados a la tarjeta gráfica del equipo.
* Pruebe algunas aplicaciones de realidad mixta diferentes de Windows Store: algunas pueden funcionar mejor con la configuración del equipo.
