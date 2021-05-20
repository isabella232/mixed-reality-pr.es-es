---
title: Visualización de la exploración de la sala
description: Las aplicaciones que requieren asignación espacial usan el dispositivo para recopilar datos a lo largo del tiempo y entre sesiones.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicación, diseño, HoloLens, examen de sala, asignación espacial, malla, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196410"
---
# <a name="room-scan-visualization"></a>Visualización de la exploración de la sala

Las aplicaciones que requieren asignación espacial dependen del dispositivo para recopilar datos a lo largo del tiempo y entre sesiones. La integridad y calidad de los datos de asignación depende de muchos factores, incluida la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos, como los alimentos y las puertas, se han movido desde que el dispositivo ha examinado el área.

Para garantizar datos útiles de asignación espacial, los desarrolladores de aplicaciones tienen varias opciones:
* Dependa de lo que ya se haya recopilado. Estos datos pueden estar incompletos inicialmente.
* Pida al usuario que use el gesto de Bloom para llegar al Windows Mixed Reality inicio y, a continuación, explore el área que desea usar para la experiencia. Pueden usar la pulsación en el aire para confirmar que el dispositivo conoce toda la área necesaria.
* Cree una experiencia de exploración personalizada en su propia aplicación.

En todos estos casos, el sistema almacena los datos reales recopilados durante la exploración y la aplicación no necesita hacerlo. Si quiere ver la visualización del examen de sala en acción, consulte nuestra demostración de vídeo Diseño de **hologramas:** reconocimiento espacial a continuación:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Visualización de la exploración de la sala</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a>Creación de una experiencia de análisis personalizada

Las aplicaciones pueden analizar los datos de asignación espacial al principio de la experiencia para determinar si quieren que el usuario realice pasos adicionales para mejorar su integridad y calidad. Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización que se superponga en el mundo para indicar:
* ¿Cuánto del volumen total en las proximidades de los usuarios debe formar parte de la experiencia?
* Dónde debe ir el usuario para mejorar los datos

Los usuarios no saben qué hace que un examen sea "bueno". Se les debe mostrar o saber qué buscar si se les pide que evalúen un examen: plana, distancia desde las paredes reales, entre otros. El desarrollador debe implementar un bucle de comentarios que incluya la actualización de los datos de asignación espacial durante la fase de exploración o exploración.

En muchos casos, es mejor decir al usuario lo que necesita hacer para obtener la calidad de examen necesaria. Por ejemplo, mire el tope, mire detrás de los suelos, y así sucesivamente.

## <a name="cached-versus-continuous-spatial-mapping"></a>Caché frente a asignación espacial continua

Los datos de asignación espacial son las aplicaciones de origen de datos de mayor peso que pueden consumir. Para evitar problemas de rendimiento, como fotogramas descartados o desordenes, el consumo de estos datos debe realizarse cuidadosamente.

El examen activo durante una experiencia puede ser beneficioso y perjudicial, por lo que deberá decidir qué método usar en función de la experiencia.

### <a name="cached-spatial-mapping"></a>Asignación espacial almacenada en caché

Si hay datos de asignación espacial almacenados en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y usa esta instantánea durante la experiencia.

**Ventajas**
* Se ha reducido la sobrecarga en el sistema mientras se ejecuta la experiencia, lo que provoca importantes mejoras en el rendimiento de la energía, las temperaturas y la CPU.
* Una implementación más sencilla de la experiencia principal, ya que los cambios en los datos espaciales no la interrumpen.
* Un solo costo de un solo tiempo en cualquier procesamiento posterior de los datos espaciales para fines físicos, gráficos y otros fines.

**Inconvenientes**
* Los datos almacenados en caché no reflejan el movimiento de objetos o personas del mundo real. Por ejemplo, la aplicación podría considerar una puerta abierta cuando está cerrada ahora.
* Potencialmente más memoria de aplicación para mantener la versión almacenada en caché de los datos.

Un buen caso para este método es un entorno controlado o un juego de mesa.

### <a name="continuous-spatial-mapping"></a>Asignación espacial continua

Algunas aplicaciones pueden basarse en el análisis continuo para actualizar los datos de asignación espacial.

**Ventajas**
* No es necesario compilar en una experiencia de exploración o exploración independiente por adelantado en la aplicación.
* El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con algún retraso.

**Inconvenientes**
* Mayor complejidad en la implementación de la experiencia principal.
* Posible sobrecarga del procesamiento físico y gráfico adicional, ya que estos sistemas deben ingerir los cambios de forma incremental.
* Mayor impacto en la energía, la temperatura y la CPU.

Un buen caso para este método es aquel en el que se espera que los hologramas interactúen con objetos en movimiento, por ejemplo, un automóvil holográfico que conduce por el suelo puede querer entrar en una puerta en función de si está abierto o cerrado.

## <a name="see-also"></a>Consulta también

* [Asignación espacial](spatial-mapping.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Diseño de sonido espacial](spatial-sound-design.md)