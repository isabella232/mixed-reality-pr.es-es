---
title: Delimitadores espaciales
description: Obtenga información sobre los procedimientos recomendados para usar anclajes espaciales para representar hologramas estables en aplicaciones de realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, escala mundial, mundo, escala, posición, orientación, delimitador, delimitador espacial, bloqueado por el mundo, bloqueo mundial, persistencia, uso compartido, casco de realidad mixta, casco de realidad mixta de windows, casco de realidad virtual, HoloLens
ms.openlocfilehash: dc9b57d51f4202499d82abb8d210261d2ee36dc60bb90ed039a7554f82af79a0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193519"
---
# <a name="spatial-anchors"></a>Delimitadores espaciales

Un delimitador espacial representa un punto importante del mundo del que el sistema realiza un seguimiento a lo largo del tiempo. Cada delimitador tiene un sistema de coordenadas [ajustable,](coordinate-systems.md)basado en otros anclajes o marcos de referencia, para garantizar que los hologramas delimitados permanezcan exactamente en su lugar.  La representación de un holograma en el sistema de coordenadas de un delimitador proporciona el posicionamiento más preciso para ese holograma en un momento dado. Esto se produce a costa de pequeños ajustes con el tiempo en la posición del holograma, ya que el sistema lo vuelve a mover continuamente a su lugar en función del mundo real.

También puede conservar y compartir delimitadores espaciales entre sesiones de aplicación y entre dispositivos:
* Al guardar anclajes espaciales locales en el disco y cargarlos más adelante, la aplicación puede calcular la misma ubicación en el mundo real en varias sesiones de aplicación en un único HoloLens.
* Mediante el <a href="/azure/spatial-anchors/overview" target="_blank">uso de Azure Spatial Anchors</a> para crear un delimitador de nube, la aplicación puede compartir un delimitador espacial entre varios dispositivos HoloLens, iOS y Android. Al hacer que cada dispositivo represente un holograma con el mismo delimitador espacial, los usuarios verán que el holograma aparece en el mismo lugar del mundo real. Esto permite compartir experiencias en tiempo real.
* También puede usar Azure Spatial Anchors para <a href="/azure/spatial-anchors/overview" target="_blank">la</a> persistencia asincrónica de hologramas en HoloLens, iOS y Dispositivos Android. Al compartir un anclaje espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

En el caso de las experiencias de escala de pie o de escala de sala para [](coordinate-systems.md#stage-frame-of-reference) cascos de escritorio tethered que permanecerán dentro de un alcance de 5 metros, normalmente puede usar el marco de fase de referencia en lugar de los anclajes espaciales, lo que proporciona un sistema de coordenadas único en el que representar todo el contenido. Sin embargo, si la aplicación permite a los usuarios recorrer más de 5 metros en HoloLens, quizás funcionando en toda una planta de un edificio, necesitará anclajes espaciales para mantener estable el contenido.

Aunque los delimitadores espaciales son estupendos para los hologramas que deben permanecer fijos en el mundo, una vez colocados, no se pueden mover. Hay alternativas a los delimitadores que son más adecuados para los hologramas dinámicos que etiquetan junto con el usuario. Es mejor colocar hologramas dinámicos mediante un marco estático de referencia (la base de las coordenadas del mundo de Unity) o un marco de referencia adjunto.

## <a name="best-practices"></a>Procedimientos recomendados

Estas directrices de delimitación espacial te ayudarán a representar hologramas estables que realizan un seguimiento preciso del mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Crear delimitadores espaciales donde los usuarios los colocan

Normalmente, los usuarios son los que colocan explícitamente anclajes espaciales.

Por ejemplo, en HoloLens, una aplicación puede intersecar el [](spatial-mapping.md) rayo de mirada del usuario con la malla de asignación espacial para permitir que el usuario decida dónde colocar un holograma. [](gaze-and-commit.md) Cuando el usuario pulse para colocar ese holograma, cree un delimitador espacial en el punto de intersección y, a continuación, coloque el holograma en el origen del sistema de coordenadas de ese delimitador.

Los anclajes espaciales locales son fáciles de crear y de gran rendimiento. El sistema combina datos internos si varios anclajes pueden compartir sus datos de sensor subyacentes. Se recomienda crear un nuevo delimitador espacial local para cada holograma que un usuario coloca explícitamente, excepto en los casos descritos a continuación, como grupos rígidas de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Procesar siempre hologramas delimitados en un radio de 3 metros a partir del delimitador

Los delimitadores espaciales estabilizan su sistema de coordenadas cerca del origen del delimitador. Si representa hologramas a más de 3 metros del origen, es posible que los hologramas experimenten errores posicionales perceptibles en proporción a su distancia desde ese origen debido a los efectos de los aceleradores. Esto funciona si el usuario se encuentra cerca del delimitador, ya que el holograma también está lejos del usuario. En otras palabras, el error angular del holograma lejano será pequeño. Sin embargo, si el usuario se acerca a ese holograma lejano, será grande en su vista, lo que hará que los efectos de la fuerza del acelerador desde el origen del anclaje lejana sean obvios.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupar los hologramas que deban formar un clúster rígido

Varios hologramas pueden compartir el mismo delimitador espacial si la aplicación espera que esos hologramas mantengan relaciones fijas entre sí.

Por ejemplo, si anima un sistema solar holográfico en una sala, es mejor vincular todos los objetos del sistema solar a un único anclaje en el centro. De este modo, se moverán sin problemas entre sí. En este caso, es el sistema solar en su conjunto el que está anclado, aunque sus partes componentes se mueven dinámicamente alrededor del anclaje.

La advertencia clave para mantener la estabilidad del holograma es seguir la regla de 3 metros anterior.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Representar hologramas muy dinámicos mediante el marco estático de referencia en lugar de usar un delimitador espacial local

Si tienes un holograma muy dinámico, como un carácter que pasea por una sala o una interfaz de usuario flotante que sigue a lo largo de la pared cerca del usuario, es mejor omitir los delimitadores espaciales locales y representar esos hologramas directamente en el sistema de coordenadas proporcionado por el marco estático de [referencia](coordinate-systems.md#stationary-frame-of-reference). En Unity, esto se consigue colocando hologramas directamente en coordenadas del mundo sin un WorldAnchor. Hologramas en un marco de referencia estacional podría experimentar un desarrase cuando el usuario está lejos del holograma. Pero es menos probable que esto sea perceptible para los hologramas dinámicos: el holograma se mueve constantemente de todos modos o su movimiento lo mantiene constantemente cerca del usuario donde se minimizará el desplazamiento.

Un caso interesante de hologramas dinámicos es un objeto animado desde un sistema de coordenadas delimitado a otro. Por ejemplo, podría tener dos cohetes a 10 metros de distancia, cada uno en su propio anclaje espacial con un campo que lanza una bola de nieve en el otro. Cuando se desencadena el globo de agua, puede representarlo en la ubicación adecuada en el marco de referencia estacionado para que coincida con el torte del sistema de coordenadas delimitado del primer hotel. Después, seguirá su trayectoria de 10 metros por el aire en el marco estático de referencia. A medida que el juego de mesa alcanza el otro campo, puede moverlo al sistema de coordenadas delimitado del segundo campo para permitir cálculos físicos con los cuerpos rígidas de ese vuelo.

Si comparte un holograma muy dinámico entre dispositivos, elija algún delimitador espacial en la nube para que actúe como su elemento primario, ya que los fotogramas de referencia estáticos no se pueden compartir entre dispositivos.  Sin embargo, debe asegurarse de que el holograma dinámico o los dispositivos que lo ven permanecen dentro del radio de 3 metros del delimitador para que el holograma parezca estable en todos los dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitar la creación de una cuadrícula de delimitadores espaciales

Es posible que se le tiente a que la aplicación coloque una cuadrícula normal de anclajes espaciales a medida que el usuario se desplaza, lo que hace que los objetos dinámicos pasen de un delimitador a otro a medida que se mueven. Sin embargo, esto implica más administración para la aplicación, sin la ventaja de los datos profundos del sensor que el propio sistema mantiene internamente. En estos casos, logrará mejores resultados colocando los hologramas en el marco de referencia estacionado, tal y como se describe en la sección anterior.
Al colocar previamente un conjunto de anclajes espaciales en la nube alrededor de un espacio estático, considere la posibilidad de colocar los delimitadores espaciales en las ubicaciones de los hologramas clave que encuentra el usuario según el principio anterior en lugar de crear una cuadrícula arbitraria de anclajes. Esto garantiza la máxima estabilidad de esos hologramas clave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Liberar los delimitadores espaciales locales que ya no se necesitan

Mientras un delimitador espacial local está activo, el sistema da prioridad a mantener los datos del sensor que están cerca de ese delimitador. Si ya no usa un delimitador espacial, deje de acceder a su sistema de coordenadas. Esto permite quitar los datos del sensor subyacentes según sea necesario.

Esto es especialmente importante para los delimitadores locales que ha persistente en el almacén de anclajes espaciales. Los datos del sensor detrás de estos anclajes se conservarán permanentemente para permitir que la aplicación encuentre ese anclaje en sesiones futuras, lo que reduce el espacio disponible para realizar el seguimiento de otros anclajes. Conserve solo los delimitadores locales que necesite buscar de nuevo en sesiones futuras. Se recomienda quitarlos del almacén cuando ya no son significativos para el usuario.

Para los delimitadores espaciales en la nube, el almacenamiento puede escalar según las necesidades del escenario. Puede almacenar tantos anclajes en la nube como necesite y liberarlos cuando sepa que los usuarios no volverán a necesitar el delimitador.

## <a name="see-also"></a>Consulte también

* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiencias compartidas en realidad mixta](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistencia en Unity](../develop/unity/persistence-in-unity.md)
* [Delimitadores espaciales en DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Looking through holes in your reality](../out-of-scope/case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)