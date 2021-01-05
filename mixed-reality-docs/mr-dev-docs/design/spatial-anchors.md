---
title: Delimitadores espaciales
description: Procedimientos recomendados de uso de delimitadores espaciales para representar hologramas estables.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, escala mundial, mundo, escala, posición, orientación, delimitador, anclaje espacial, bloqueo mundial, bloqueo mundial, persistencia, uso compartido, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens
ms.openlocfilehash: 7f6997e491f76e66845b88ea0897dbb037495ba6
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848214"
---
# <a name="spatial-anchors"></a>Delimitadores espaciales

Un delimitador espacial representa un punto importante del mundo en el que el sistema realiza un seguimiento a lo largo del tiempo. Cada delimitador tiene un [sistema de coordenadas](coordinate-systems.md)ajustable, basado en otros delimitadores o fotogramas de referencia, para asegurarse de que los hologramas anclados se mantienen exactamente en su lugar.  La representación de un holograma en el sistema de coordenadas de un delimitador proporciona el posicionamiento más preciso para ese holograma en un momento dado. Esto se debe a un costo de pequeños ajustes a lo largo del tiempo a la posición del holograma, ya que el sistema lo mueve continuamente a su lugar en función del mundo real.

También puede conservar y compartir los delimitadores espaciales en las sesiones de aplicación y en los dispositivos:
* Al guardar los delimitadores espaciales locales en el disco y volver a cargarlos más tarde, la aplicación puede calcular la misma ubicación en el mundo real en varias sesiones de aplicación en una sola HoloLens.
* Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para crear un delimitador de nube, la aplicación puede compartir un anclaje espacial en varios dispositivos de HoloLens, iOS y Android. Cuando cada dispositivo representa un holograma mediante el mismo delimitador espacial, los usuarios verán que el holograma aparece en el mismo lugar del mundo real. Esto permite compartir experiencias en tiempo real.
* También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">delimitadores espaciales de Azure</a> para la persistencia asincrónica de hologramas en dispositivos de HoloLens, iOS y Android. Al compartir un delimitador espacial en la nube duradero, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes juntos al mismo tiempo.

En el caso de las experiencias de escalado permanente o de escala de sala para auriculares de escritorio anclados que permanecerán dentro de un diámetro de 5 metros, normalmente puede usar el [marco de fase de referencia](coordinate-systems.md#stage-frame-of-reference) en lugar de los delimitadores espaciales, lo que proporciona un sistema de coordenadas único en el que se va a representar todo el contenido. Sin embargo, si la aplicación permite a los usuarios ir más allá de 5 metros en HoloLens, quizás funcionando en todo el piso de un edificio, necesitará anclajes espaciales para mantener el contenido estable.

Aunque los delimitadores espaciales son estupendos para los hologramas que deben permanecer fijos en el mundo, una vez colocados, no se pueden mover. Hay alternativas a los delimitadores más adecuadas para los hologramas dinámicos que etiquetan junto con el usuario. Es mejor posicionar los hologramas dinámicos con un marco estacionario de referencia (la base para las coordenadas universales de Unity) o un marco de referencia asociado.

## <a name="best-practices"></a>Procedimientos recomendados

Estas directrices de delimitación espacial te ayudarán a representar hologramas estables que realizan un seguimiento preciso del mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Crear delimitadores espaciales donde los usuarios los colocan

Normalmente, los usuarios son los que colocan delimitadores espaciales de forma explícita.

Por ejemplo, en HoloLens, una aplicación puede intersectar el [rayo del](gaze-and-commit.md) usuario con la malla de [asignación espacial](spatial-mapping.md) para permitir que el usuario decida dónde colocar un holograma. Cuando el usuario puntea para colocar el holograma, cree un delimitador espacial en el punto de intersección y, a continuación, coloque el holograma en el origen del sistema de coordenadas del delimitador.

Los delimitadores espaciales locales son sencillos y se pueden crear. El sistema combina los datos internos si varios delimitadores pueden compartir los datos subyacentes del sensor. Se recomienda crear un nuevo delimitador espacial local para cada holograma que un usuario coloque explícitamente, excepto en los casos descritos a continuación, como los grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Procesar siempre hologramas delimitados en un radio de 3 metros a partir del delimitador

Los delimitadores espaciales estabilizan su sistema de coordenadas cerca del origen del delimitador. Si representa hologramas de más de 3 metros desde el origen, los hologramas podrían experimentar errores posicionales perceptibles en proporción a su distancia desde ese origen debido a los efectos de la ARM. Esto funciona si el usuario está cerca del delimitador, ya que el holograma también está alejado del usuario. En otras palabras, el error angular del holograma distante será pequeño. Sin embargo, si el usuario avanza hasta ese holograma distante, será grande en su vista, lo que hará que los efectos de brazo de palanca del origen del delimitador lejanos sean obvios.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupar los hologramas que deban formar un clúster rígido

Varios hologramas pueden compartir el mismo delimitador espacial si la aplicación espera que esos hologramas mantengan relaciones fijas entre sí.

Por ejemplo, si está animando un sistema solar Holographic en una habitación, es mejor unir todos los objetos del sistema solar a un solo delimitador en el centro. De este modo, se moverán sin problemas entre sí. En este caso, es el sistema solar como un conjunto que está anclado, aunque sus partes componentes se mueven dinámicamente alrededor del delimitador.

La advertencia clave para mantener la estabilidad del holograma es seguir la regla de 3 metros anterior.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Representar hologramas muy dinámicos mediante el marco estático de referencia en lugar de usar un delimitador espacial local

Si tiene un holograma muy dinámico, como un carácter que recorre una habitación o una interfaz de usuario flotante que sigue a la pared cerca del usuario, es mejor omitir los delimitadores espaciales locales y representar esos hologramas directamente en el sistema de coordenadas proporcionado por el [marco estacionario de referencia](coordinate-systems.md#stationary-frame-of-reference). En Unity, puede lograr esto colocando hologramas directamente en coordenadas universales sin WorldAnchor. Los hologramas de un marco estacionario de referencia pueden experimentar un desplazamiento cuando el usuario está lejos del holograma. Pero es menos probable que se aprecie en los hologramas dinámicos: el holograma se mueve constantemente de todas formas o su movimiento lo mantiene constantemente cerca del usuario donde se minimizará el desplazamiento.

Un caso interesante de hologramas dinámicos es un objeto animado desde un sistema de coordenadas delimitado a otro. Por ejemplo, podría tener dos metros de Castles de 10, cada uno en su propio delimitador espacial con un nivel de espacio de arranque que activa un Cannonball en el otro. Cuando se desencadene el Cannonball, puede representarlo en la ubicación adecuada en el marco estacionario de referencia para que coincida con el cañón en el sistema de coordenadas anclado del primer golpe. Después, seguirá su trayectoria de 10 metros por el aire en el marco estático de referencia. A medida que el Cannonball alcanza el otro, puede moverlo en el sistema de coordenadas anclado del segundo de la segunda para permitir cálculos físicos con los cuerpos rígidos de ese equipo.

Si va a compartir un holograma de gran nivel en todos los dispositivos, seleccione algún delimitador espacial de la nube para que actúe como su elemento primario, ya que los marcos de referencia no se pueden compartir entre los dispositivos.  Sin embargo, debe asegurarse de que el holograma dinámico o los dispositivos que lo ven permanecen dentro del radio de 3 metros del delimitador para que el holograma parezca estable en todos los dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitar la creación de una cuadrícula de delimitadores espaciales

Es posible que se sienta tentado a que la aplicación coloque una cuadrícula normal de anclajes espaciales a medida que el usuario se desplace, pasando objetos dinámicos del delimitador al delimitador mientras se mueven. Sin embargo, esto implica más administración para la aplicación, sin la ventaja de los datos de sensor profundos que mantiene internamente el sistema. En estos casos, obtendrá mejores resultados colocando los hologramas en el marco estacionario de referencia como se describe en la sección anterior.
Cuando esté colocando previamente un conjunto de delimitadores espaciales en la nube en torno a un espacio estático, considere la posibilidad de colocar los delimitadores espaciales en las ubicaciones de los hologramas de clave que el usuario incluye en el principio, en lugar de crear una cuadrícula arbitraria de delimitadores. Esto garantiza la máxima estabilidad de esos hologramas clave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Liberar los delimitadores espaciales locales que ya no se necesitan

Mientras un delimitador espacial local está activo, el sistema prioriza el mantenimiento de los datos del sensor que están cerca del delimitador. Si ya no usa un delimitador espacial, detenga el acceso a su sistema de coordenadas. Esto permite quitar los datos del sensor subyacentes según sea necesario.

Esto es especialmente importante para los delimitadores locales que ha conservado en el almacén de delimitador espacial. Los datos de sensor que se encuentran detrás de estos delimitadores se conservarán de forma permanente para permitir que la aplicación encuentre ese anclaje en futuras sesiones, lo que reduce el espacio disponible para realizar el seguimiento de otros delimitadores. Solo debe conservar los delimitadores locales que necesite buscar de nuevo en futuras sesiones. Se recomienda quitarlos de la tienda cuando ya no sean significativos para el usuario.

Para los delimitadores espaciales en la nube, el almacenamiento puede escalar según las necesidades del escenario. Puede almacenar tantos delimitadores de nube como sea necesario y liberarlos cuando sepa que los usuarios no necesitarán el delimitador de nuevo.

## <a name="see-also"></a>Consulte también

* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiencias compartidas en realidad mixta](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistencia en Unity](../develop/unity/persistence-in-unity.md)
* [Delimitadores espaciales en DirectX](../develop/native/coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Looking through holes in your reality](../out-of-scope/case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)
