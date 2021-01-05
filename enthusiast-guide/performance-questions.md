---
title: Preguntas más frecuentes sobre rendimiento
description: Rendimiento de Windows Mixed Reality solución de problemas que va más allá de nuestra documentación de soporte técnico estándar para el consumidor.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, rendimiento
appliesto:
- Windows 10
ms.openlocfilehash: dea2e81d53bfbb16a8803fc3f7c4e011741dfce6
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726006"
---
# <a name="performance-faqs"></a>Preguntas más frecuentes sobre rendimiento

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60-hz-or-90-hz-framerate"></a>Es la representación de auriculares de realidad mixta de Windows con una velocidad de fotogramas de 60 Hz o 90-Hz

Si tiene una GPU discreta con puertos HDMI 2,0 y una CPU con cuatro o más núcleos físicos, debe obtener 90 Hz. Para confirmar, consulte la pestaña **rendimiento del portal de dispositivos >** .

Nota: Si la GPU solo tiene una salida HDMI 1,4, puede usar un adaptador de DisplayPort a [hdmi 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) como solución alternativa.

Nota: la configuración de calidad visual de "pantalla de auriculares" solo afecta a la representación de la experiencia principal de Windows Mixed Reality.

## <a name="my-pc-is-running-slowly"></a>Mi PC se ejecuta lentamente

El sistema puede ser lento por muchos motivos, normalmente solo unos pocos segundos. Si experimenta este problema durante largos períodos de tiempo:

1. Cierre todas las aplicaciones sin usar en el escritorio.
2. Asegúrese de que el portátil esté conectado a una fuente de alimentación.
3. Asegúrese de que el equipo no se está preparando.
4. Reduzca la calidad visual en la Página principal de Windows Mixed Reality.
5. Asegúrese de que dispone de los [controladores de gráficos](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) más recientes para su PC.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Mi PC se está preparando mientras ejecuto las experiencias de realidad mixta. Cómo manténgalo frío

1. Compruebe que se cargue la batería y que la fuente de alimentación esté conectada.
2. Asegúrese de que los ventiladores de PC no estén bloqueados.
3. Use el equipo en un entorno relativamente frío.
4. Asegúrese de que no haya fuentes de calor (por ejemplo, el sol o los orificios de ventilación) señalados al equipo.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Mis objetos visuales son entrecortado, se cargan lentamente o no parecen buenos

* Asegúrese de que el casco está enchufado en la tarjeta gráfica correcta del equipo. Algunos equipos tienen tarjetas de gráficos integradas y discretas. Por lo general, la tarjeta discreta proporcionará el mejor rendimiento. [Más información sobre el hardware de PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Cierre las aplicaciones no utilizadas en el escritorio.
* Asegúrese de que el casco se ajusta perfectamente (muévalo hacia abajo y hacia arriba, o a la izquierda y derecha para ajustar).
* Ajusta la configuración visual de los auriculares en **configuración > realidad mixta > pantalla de auriculares**. Cuando "calidad visual" esté establecido en "automático", se elegirá automáticamente la experiencia de realidad mixta para el equipo. Para obtener más detalles visuales, establezca "calidad visual" en "alto". Si los objetos visuales son entrecortado, seleccione un valor inferior.
* Ajuste el botón de calibración de auriculares para asegurarse de que las lentes estén configuradas con la distancia correcta entre los alumnos (denominado IPD). Si no conoce el IPD, un Optometrist puede medirlo por usted o usar un sitio web diseñado para medir el uso de IPD. Si el casco no tiene un botón de calibración, seleccione la **configuración > realidad mixta > auriculares para mostrar** y ajustar el "control de calibración".
* Si usa un adaptador de USB-C o DisplayPort a HDMI, pruebe con otro. Consulte [adaptadores recomendados.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Desconecte los monitores adicionales que puedan estar conectados a la tarjeta gráfica de su PC.
* Pruebe algunas aplicaciones de realidad mixta en la tienda Windows, algunas pueden funcionar mejor con la configuración del equipo.
