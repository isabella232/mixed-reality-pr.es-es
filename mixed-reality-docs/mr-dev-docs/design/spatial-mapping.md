---
title: Asignación espacial
description: La asignación espacial proporciona una representación detallada de las superficies del mundo real en el entorno alrededor de HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: asignación espacial, HoloLens, realidad mixta, reconstrucción de la superficie, malla, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, kit de herramientas de Mixed Reality, comprensión de la escena, malla mundial, oclusión, física, navegación, observador de la superficie, representación, procesamiento de malla
ms.openlocfilehash: 3268f25f86cdfea3aa1ae0b77c4fbeb9aa0ce1b9
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196430"
---
# <a name="spatial-mapping"></a>Asignación espacial

La asignación espacial proporciona una representación detallada de las superficies del mundo real en el entorno alrededor de HoloLens, lo que permite a los desarrolladores crear una experiencia de realidad mixta convincente. Al combinar el mundo real con el mundo virtual, una aplicación puede hacer que los hologramas parezcan reales. Las aplicaciones también se pueden alinear de forma más natural con las expectativas del usuario proporcionando interacciones y comportamientos conocidos del mundo real.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-supports"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Asignación espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>


## <a name="why-is-spatial-mapping-important"></a>¿Por qué es importante la asignación espacial?

La asignación espacial permite colocar objetos en superficies reales. Esto ayuda a delimitar objetos en el mundo del usuario y aprovecha las indicaciones de profundidad del mundo real. La ocultación de los hologramas en función de otros hologramas y objetos del mundo real ayuda a convencer al usuario de que estos hologramas están realmente en su espacio. Los hologramas que flotan en el espacio o se mueven con el usuario no se verán como reales. Cuando sea posible, coloque elementos para mayor comodidad.

Visualizar superficies al colocar o mover hologramas (use una cuadrícula proyectada). Esto ayuda a los usuarios a saber dónde pueden colocar mejor sus hologramas y muestra si el punto en el que intentan colocar el holograma no está asignado. Puede "agregar elementos" al usuario si terminan en demasiado ángulo.

## <a name="conceptual-overview"></a>Información general conceptual

![Superficies de malla que cubren una sala](images/SurfaceReconstruction.jpg)<br>
*Un ejemplo de una malla de asignación espacial que cubre una sala*

Los dos tipos de objetos principales que se usan para la asignación espacial son "Observador de superficie espacial" y "Superficie espacial".

La aplicación proporciona al observador de superficie espacial uno o varios volúmenes delimitadores para definir las regiones de espacio en las que la aplicación desea recibir datos de asignación espacial. Para cada uno de estos volúmenes, la asignación espacial proporcionará a la aplicación un conjunto de superficies espaciales.

Estos volúmenes pueden ser fijos (en una ubicación fija basada en el mundo real) o pueden asociarse a HoloLens (se mueven, pero no giran, con HoloLens a medida que se mueve por el entorno). Cada superficie espacial describe las superficies del mundo real en un pequeño volumen de espacio, representado como una malla de triángulo conectada a un sistema de coordenadas espaciales bloqueado por [el mundo.](coordinate-systems.md)

A medida que HoloLens recopila nuevos datos sobre el entorno y, a medida que se producen cambios en el entorno, las superficies espaciales aparecerán, desaparecerán y cambiarán.

## <a name="spatial-awareness-design-concepts-demo"></a>Demostración de conceptos de diseño de reconocimiento espacial

Si quiere ver los conceptos de diseño de reconocimiento espacial en acción, consulte la demostración de vídeo Diseño de **hologramas:** reconocimiento espacial a continuación. Cuando haya terminado, continúe con un análisis más detallado de temas específicos.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*

## <a name="spatial-mapping-vs-scene-understanding-worldmesh"></a>Spatial Mapping frente a Scene Understanding WorldMesh

Por HoloLens 2, es posible consultar una versión estática de los datos de asignación espacial mediante [scene understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) (configuración EnableWorldMesh). Estas son las diferencias entre dos formas de acceder a los datos de asignación espacial:
* Spatial Mapping API:
   * Intervalo limitado: los datos de asignación espacial disponibles para las aplicaciones en una "burbuja" almacenada en caché de tamaño limitado en torno al usuario.
   * Proporciona actualizaciones de baja latencia de regiones de malla modificadas a través de eventos SurfacesChanged.
   * Nivel variable de detalles controlado por el parámetro Triángulos por medidor cúbica.
* SDK de descripción de la escena:
   * Intervalo ilimitado: proporciona todos los datos de asignación espacial examinados dentro del radio de consulta.
   * Proporciona una instantánea estática de los datos de asignación espacial. La obtención de los datos de asignación espacial actualizados requiere ejecutar una nueva consulta para toda la malla.
   * Nivel coherente de detalles controlado por la configuración RequestedMeshLevelOfDetail.

## <a name="what-influences-spatial-mapping-quality"></a>¿Qué influye en la calidad de la asignación espacial?

Varios factores, que se [detallan aquí,](/hololens/hololens-environment-considerations)pueden afectar a la frecuencia y gravedad de estos errores.  Sin embargo, debe diseñar la aplicación para que el usuario pueda lograr sus objetivos incluso en presencia de errores en los datos de asignación espacial.

## <a name="common-usage-scenarios"></a>Escenarios de uso comunes

![Ilustraciones de escenarios comunes de uso de asignaciones espaciales: selección de ubicación, oclusión, física y navegación](images/sm-concepts-1000px.png)

### <a name="placement"></a>Selección de ubicación

La asignación espacial proporciona a las aplicaciones la oportunidad de presentar formas naturales y familiares de interacción al usuario. ¿Qué podría ser más natural que colocar el teléfono en el escritorio?

Restringir la colocación de hologramas (o más generalmente, cualquier selección de ubicaciones espaciales) para colocarse en las superficies proporciona una asignación natural de 3D (punto en el espacio) a 2D (punto en superficie). Esto reduce la cantidad de información que el usuario necesita proporcionar a la aplicación y hace que las interacciones del usuario sean más rápidas, sencillas y precisas. Esto es así porque "distancia a distancia" no es algo que se esté acostumbrado a comunicarse físicamente con otras personas o con equipos. Cuando señalamos con el dedo, se especifica una dirección, pero no una distancia.

Una advertencia importante aquí es que cuando una aplicación deduce la distancia desde la dirección (por ejemplo, haciendo un raycast a lo largo de la dirección de mirada del usuario para encontrar la superficie espacial más cercana), esto debe producir resultados que el usuario pueda predecir de forma confiable. De lo contrario, el usuario perderá su sentido del control y esto puede resultar frustrante rápidamente. Un método que ayuda con esto es realizar varios raycasts en lugar de solo uno. Los resultados agregados deben ser más fluidos y predecibles, menos susceptibles a la influencia de los resultados transitorios de "valores atípicos" (como puede deberse a que los rayos pasan a través de pequeños huecos o alcanzan pequeños bits de geometría que el usuario no conoce). La agregación o el suavizado también se pueden realizar con el tiempo. Por ejemplo, puede limitar la velocidad máxima a la que un holograma puede variar en distancia con respecto al usuario. Limitar el valor de distancia mínima y máxima también puede ayudar, por lo que el holograma que se mueve no desaparece repentinamente a la distancia ni vuelve a bloquearse en la cara del usuario.

Las aplicaciones también pueden usar la forma y la dirección de las superficies para guiar la ubicación del holograma. Una buta holográfica no debe atravesar las paredes y debe vaciarse con el suelo aunque sea ligeramente desigual. Este tipo de funcionalidad probablemente se basaría en el uso de colisiones físicas en lugar de raycasts, pero se aplicarán preocupaciones similares. Si el holograma que se va a colocar tiene muchos polígonos pequeños que se adhieren, como las ruedas de una buta, puede tener sentido expandir la representación física de esos polígonos a algo más ancho y más suave para que puedan deslizarse sobre las superficies espaciales sin etiquetar.

En su extremo, la entrada del usuario se puede simplificar completamente y las superficies espaciales se pueden usar para realizar la colocación de hologramas completamente automática. Por ejemplo, la aplicación podría colocar un conmutador de luz holográfica en algún lugar de la pared para que el usuario lo presione. La misma advertencia sobre la previsibilidad se aplica doblemente aquí; Si el usuario espera el control sobre la ubicación del holograma, pero la aplicación no siempre coloca los hologramas donde espera (si el conmutador de luz aparece en algún lugar al que el usuario no puede llegar), esta será una experiencia frustrante. En realidad, puede ser peor realizar la selección de ubicación automática que requiere una corrección del usuario algunas veces, que simplemente requerir que el usuario siempre realice la selección de ubicación por sí mismo. dado que se espera una colocación *automática correcta,* la corrección manual parece una carga.

Tenga en cuenta también que la capacidad de una aplicación para usar superficies espaciales para la selección de ubicación depende en gran medida de la experiencia de [examen de la aplicación.](spatial-mapping.md#the-environment-scanning-experience) Si no se ha examinado una superficie, no se puede usar para la selección de ubicación. La aplicación debe dejar esto claro al usuario para que pueda ayudar a examinar nuevas superficies o seleccionar una nueva ubicación.

Los comentarios visuales al usuario son de suma importancia durante la selección de ubicación. El usuario debe saber dónde se basa el holograma en la superficie más cercana con efectos [de tierra.](spatial-mapping.md#visualization) Deben comprender por qué se restringe el movimiento de su holograma (por ejemplo, debido a colisiones con otra superficie cercana). Si no pueden colocar un holograma en la ubicación actual, los comentarios visuales deben dejar claro por qué no. Por ejemplo, si el usuario está intentando colocar un diván holográfico atascado a medio camino en la pared, las partes del diván que están detrás de la pared deben pulsar en un color tonificado. O, por el contrario, si la aplicación no puede encontrar una superficie espacial en una ubicación donde el usuario pueda ver una superficie real, la aplicación debe dejar esto claro. La ausencia obvia de un efecto de base en esta área puede lograr este propósito.

### <a name="occlusion"></a>Oclusión

Uno de los principales usos de las superficies de asignación espacial es simplemente occluir hologramas. Este comportamiento simple tiene un gran impacto en el realismo percibido de los hologramas, lo que ayuda a crear un sentido visceral que realmente resalte el mismo espacio físico que el usuario.

La oclusión también proporciona información al usuario; cuando un holograma parece estar ocluso por una superficie real, esto proporciona comentarios visuales adicionales sobre la ubicación espacial de ese holograma en el mundo. Por el contrario, la oclusión también puede ocultar *información* al usuario; oclusión de hologramas detrás de las paredes puede reducir el desorden visual de una manera intuitiva. Para ocultar o revelar un holograma, el usuario simplemente tiene que mover la cabeza.

La oclusión también se puede usar para cumplir las expectativas de una interfaz de usuario natural basada en interacciones físicas conocidas. Si un holograma está ocluido por una superficie, es porque esa superficie  es sólida, por lo que el usuario debe esperar que el holograma colisione con esa superficie y no pase a través de ella.

A veces, no se desea la oclusión de hologramas. Si un usuario necesita interactuar con un holograma, debe verlo, incluso si está detrás de una superficie real. En tales casos, normalmente tiene sentido representar este holograma de forma diferente cuando está ocluso (por ejemplo, reduciendo su brillo). De este modo, el usuario puede localizar visualmente el holograma, pero seguirá sabendo que está detrás de algo.

### <a name="physics"></a>Física

El uso de la simulación física es otra manera  de usar la asignación espacial para reforzar la presencia de hologramas en el espacio físico del usuario. Cuando mi bola holográfica de hule se lanza de forma realista fuera de mi escritorio, salta por el suelo y desaparece debajo del diván, podría ser difícil para mí pensar que no está ahí.

La simulación física también proporciona la oportunidad de que una aplicación use interacciones naturales y familiares basadas en la física. Mover un fragmento de piezas holográficas por el suelo probablemente será más fácil para el usuario si el hogar responde como si estuviera deslizándose por el suelo con la inercia y la fricción adecuadas.

Para generar comportamientos físicos realistas, es [](spatial-mapping.md#mesh-processing) probable que deba realizar algún procesamiento de malla, como rellenar los huecos, quitar las aclaraciones flotantes y suavizar las superficies aproximadas.

También deberá tener en cuenta cómo la experiencia de análisis de la [aplicación](spatial-mapping.md#the-environment-scanning-experience) influye en su simulación física. En primer lugar, las superficies que faltan no colisionan con nada; ¿Qué ocurre cuando la bola de cristal se despeda hacia abajo y fuera del fin del mundo conocido? En segundo lugar, debe decidir si seguirá respondiendo a los cambios en el entorno a lo largo del tiempo. En algunos casos, querrá responder lo antes posible. Por ejemplo, si el usuario usa puertas y ramas como ramas móviles en defensa frente a una tempestad de flechas de román entrantes. Sin embargo, en otros casos, es posible que quiera omitir las nuevas actualizaciones. Es posible que, de repente, conducir el coche deportivo holográfico alrededor del circuito en el suelo no sea tan divertido si el perro decide quedarse en medio de la pista.

### <a name="navigation"></a>Navegación

Las aplicaciones pueden usar datos de asignación espacial para conceder a los caracteres holográficos (o agentes) la capacidad de navegar por el mundo real de la misma manera que lo haría una persona real. Esto puede ayudar a reforzar la presencia de caracteres holográficos al restringirlos al mismo conjunto de comportamientos naturales y familiares que los del usuario y sus amigos.

Las funcionalidades de navegación también pueden ser útiles para los usuarios. Una vez que se ha creado un mapa de navegación en un área determinada, se podría compartir para proporcionar instrucciones holográficas a los nuevos usuarios que no están familiarizados con esa ubicación. Este mapa podría diseñarse para ayudar a mantener el flujo de tráfico "tráfico" sin problemas o para evitar accidentes en ubicaciones peligrosas, como sitios de construcción.

Los principales desafíos técnicos implicados en la implementación de la funcionalidad de navegación serán la detección confiable de superficies paseables (los seres humanos no andan en tablas) y la adaptación correcta a los cambios en el entorno (los seres humanos no atraviesan puertas cerradas). La malla puede requerir algún [procesamiento](spatial-mapping.md#mesh-processing) antes de que se pueda usar para el planeamiento de rutas de acceso y la navegación por un carácter virtual. Suavizar la malla y quitar las salas puede ayudar a evitar que los caracteres se atascarán. También puede simplificar drásticamente la malla para acelerar los cálculos de navegación y planeamiento de rutas de acceso del carácter. Estos desafíos han recibido una gran atención en el desarrollo de tecnología de juegos de vídeo y hay una gran cantidad de documentación de investigación disponible sobre estos temas.

La funcionalidad integrada NavMesh en Unity no se puede usar con superficies de asignación espacial. Esto se debe a que las superficies de asignación espacial no se conocen hasta que se inicia la aplicación, pero los archivos de datos NavMesh deben generarse a partir de recursos de origen con antelación. Tenga en cuenta también que el sistema de asignación espacial no proporcionará información sobre las [superficies](spatial-mapping.md#the-environment-scanning-experience) lejos de la ubicación actual del usuario. Por lo tanto, la aplicación debe "recordar" superficies si se va a crear un mapa de un área grande.

### <a name="visualization"></a>Visualización

La mayoría de las veces es adecuado que las superficies espaciales sean invisibles; para minimizar el desorden visual y dejar que el mundo real hable por sí mismo. Sin embargo, a veces resulta útil visualizar las superficies de asignación espacial directamente, a pesar de que sus homólogos reales sean visibles.

Por ejemplo, cuando el usuario intenta colocar un holograma en una superficie (colocar un gabinete holográfico en la pared, por ejemplo) puede ser útil "colocar" el holograma mediante la conversión de una sombra en la superficie. Esto proporciona al usuario una idea mucho más clara de la proximidad física exacta entre el holograma y la superficie. Este es también un ejemplo de la práctica más general de "obtener una vista previa" visual de un cambio antes de que el usuario se confirme en él.

Al visualizar las superficies, la aplicación puede compartir con el usuario su comprensión del entorno. Por ejemplo, un juego de mesa holográfica podría visualizar las superficies horizontales que ha identificado como "tablas", por lo que el usuario sabe a dónde debe ir para interactuar.

La visualización de superficies puede ser una manera útil de mostrar los espacios cercanos del usuario que están ocultos en la vista. Esto podría proporcionar una manera de proporcionar al usuario acceso a su cocina (y a todos sus hologramas contenidos) desde su sala de estar.

Es posible que las mallas de superficie proporcionadas por la asignación espacial no sean especialmente "limpias". Es importante visualizarlos correctamente. Los cálculos de iluminación tradicionales pueden resaltar los errores en las normales de la superficie de una manera visualmente distraída, mientras que las texturas "limpias" proyectadas en la superficie pueden ayudar a darle un aspecto más ordenado. También es posible realizar el procesamiento de [malla](spatial-mapping.md#mesh-processing) para mejorar las propiedades de la malla, antes de que se representen las superficies.

> [!NOTE]
> HoloLens 2 implementa una nueva instancia de [Scene Understanding Runtime](scene-understanding.md)que proporciona a los desarrolladores de Mixed Reality una representación de entorno estructurada y de alto nivel diseñada para simplificar la implementación de la selección de ubicación, oclusión, física y navegación.

## <a name="using-the-surface-observer"></a>Uso del observador de surface

El punto inicial de la asignación espacial es el observador de superficie. El flujo del programa es el siguiente:
* Creación de un objeto observador de superficie
   * Proporcione uno o varios volúmenes espaciales para definir las regiones de interés en las que la aplicación desea recibir datos de asignación espacial. Un volumen espacial es simplemente una forma que define una región de espacio, como una esfera o un cuadro.
   * Use un volumen espacial con un sistema de coordenadas espaciales bloqueado por el mundo para identificar una región fija del mundo físico.
   * Use un volumen espacial, actualizado cada fotograma con un sistema de coordenadas espaciales bloqueado por el cuerpo, para identificar una región de espacio que se mueve (pero no gira) con el usuario.
   * Estos volúmenes espaciales se pueden cambiar más adelante en cualquier momento, a medida que cambia el estado de la aplicación o del usuario.
* Uso de sondeo o notificación para recuperar información sobre superficies espaciales
   * Puede "sondear" el observador de la superficie en busca del estado de la superficie espacial en cualquier momento. En su lugar, puede registrarse para el evento "surfaces changed" del observador de la superficie, que notificará a la aplicación cuándo han cambiado las superficies espaciales.
   * Para un volumen espacial dinámico, como el frustum de vista o un volumen bloqueado por el cuerpo, las aplicaciones tendrán que sondear los cambios en cada fotograma estableciendo la región de interés y, a continuación, obteniendo el conjunto actual de superficies espaciales.
   * En el caso de un volumen estático, como un cubo bloqueado por el mundo que abarca una sola sala, las aplicaciones pueden registrarse para que se notifique el evento "surfaces changed" cuando las superficies espaciales dentro de ese volumen puedan haber cambiado.
* Cambios en las superficies de proceso
   * Iteración del conjunto de superficies espaciales proporcionado.
   * Clasifique las superficies espaciales como agregadas, modificadas o quitadas.
   * Para cada superficie espacial agregada o modificada, si procede, envíe una solicitud asincrónica para recibir una malla actualizada que represente el estado actual de la superficie en el nivel de detalle deseado.
* Procese la solicitud de malla asincrónica (más detalles en las secciones siguientes).

## <a name="mesh-caching"></a>Almacenamiento en caché de malla

Las superficies espaciales se representan mediante mallas de triángulo densas. Almacenar, representar y procesar estas mallas puede consumir importantes recursos de cálculo y almacenamiento. Por lo tanto, cada aplicación debe adoptar un esquema de almacenamiento en caché de malla adecuado para sus necesidades, a fin de minimizar los recursos usados para el procesamiento y el almacenamiento de la malla. Este esquema debe determinar qué mallas conservar y cuáles descartar, y cuándo actualizar la malla para cada superficie espacial.

Muchas de las consideraciones que se analizan allí informarán directamente de cómo la aplicación debe abordar el almacenamiento en caché de malla. Debe tener en cuenta cómo se mueve el usuario a través del entorno, qué superficies son necesarias, cuándo se observarán distintas superficies y cuándo se deben capturar los cambios en el entorno.

Al interpretar el evento "surfaces changed" proporcionado por el observador de superficie, la lógica básica de almacenamiento en caché de malla es la siguiente:
* Si la aplicación ve un identificador de superficie espacial que no ha visto antes, debe tratarlo como una nueva superficie espacial.
* Si la aplicación ve una superficie espacial con un identificador conocido pero con un nuevo tiempo de actualización, debe tratarla como una superficie espacial actualizada.
* Si la aplicación ya no ve una superficie espacial con un identificador conocido, debe tratarla como una superficie espacial quitada.

Es decisión de cada aplicación tomar las siguientes decisiones:
* En el caso de las nuevas superficies espaciales, ¿se debe solicitar la malla?
   * Por lo general, la malla debe solicitarse inmediatamente para nuevas superficies espaciales, lo que puede proporcionar información nueva útil al usuario.
   * Sin embargo, las nuevas superficies espaciales cerca y delante del usuario deben tener prioridad y su malla debe solicitarse primero.
   * Si la nueva malla no es necesaria, si, por ejemplo, la aplicación ha "inmovilizado" permanente o temporalmente su modelo del entorno, no se debe solicitar.
* En el caso de las superficies espaciales actualizadas, ¿se debe solicitar la malla?
   * Las superficies espaciales actualizadas cerca y delante del usuario deben tener prioridad y se debe solicitar primero su malla.
   * También puede ser adecuado dar mayor prioridad a las superficies nuevas que a las superficies actualizadas, especialmente durante la experiencia de examen.
   * Para limitar los costos de procesamiento, es posible que las aplicaciones deseen limitar la velocidad a la que procesan las actualizaciones de las superficies espaciales.
   * Es posible deducir que los cambios en una superficie espacial son menores, por ejemplo, si los límites de la superficie son pequeños, en cuyo caso es posible que la actualización no sea lo suficientemente importante como para procesarla.
   * Las actualizaciones de superficies espaciales fuera de la región actual de interés del usuario pueden omitirse por completo, aunque en este caso puede ser más eficaz modificar los volúmenes de límite espacial en uso por parte del observador de la superficie.
* En el caso de las superficies espaciales quitadas, ¿se debe descartar la malla?
   * Por lo general, la malla debe descartarse inmediatamente para las superficies espaciales quitadas, de modo que la oclusión del holograma siga siendo correcta.
   * Sin embargo, si la aplicación tiene motivos para pensar que una superficie espacial volverá a aparecer en breve (en función del diseño de la experiencia del usuario), puede ser más eficaz conservarla que descartar su malla y volver a crearla más adelante.
   * Si la aplicación está creando un modelo a gran escala del entorno del usuario, es posible que no quiera descartar ninguna malla en absoluto. Sin embargo, tendrá que limitar el uso de recursos, posiblemente mediante la cola de mallas en el disco a medida que desaparecen las superficies espaciales.
   * Algunos eventos relativamente poco frecuentes durante la generación de la superficie espacial pueden hacer que las superficies espaciales se reemplazan por nuevas superficies espaciales en una ubicación similar, pero con identificadores diferentes. Por lo tanto, las aplicaciones que deciden no descartar una superficie quitada deben tener cuidado de no acabar con varias mallas de superficies espaciales superpuestas que abarcan la misma ubicación.
* ¿Se debe descartar la malla para cualquier otra superficie espacial?
   * Aunque exista una superficie espacial, si ya no es útil para la experiencia del usuario, se debe descartar. Por ejemplo, si la aplicación "reemplaza" la sala del otro lado de una puerta por un espacio virtual alternativo, las superficies espaciales de esa sala ya no importan.

A continuación se muestra una estrategia de almacenamiento en caché de malla de ejemplo, mediante la histeresis espacial y temporal:
* Considere una aplicación que desee usar un volumen espacial con forma de frustum de interés que siga la mirada del usuario mientras mira y le guía.
* Una superficie espacial puede desaparecer temporalmente de este volumen simplemente porque el usuario mira fuera de la superficie o se aleja más de ella... solo para mirar hacia atrás o acercarse de nuevo un momento más tarde. En este caso, descartar y volver a crear la malla para esta superficie representa muchos procesamientos redundantes.
* Para reducir el número de cambios procesados, la aplicación usa dos observadores de superficie espacial, uno incluido dentro del otro. El volumen mayor es esférico y sigue al usuario "de forma lazily". solo se mueve cuando es necesario para asegurarse de que su centro está a menos de 2,0 metros del usuario.
* Las mallas de superficie espacial nuevas y actualizadas siempre se procesan desde el observador de superficie interna más pequeño, pero las mallas se almacenan en caché hasta que desaparecen del observador de superficie externa más grande. Esto permite a la aplicación evitar el procesamiento de muchos cambios redundantes debido al movimiento del usuario local.
* Puesto que una superficie espacial también puede desaparecer temporalmente debido a la pérdida de seguimiento, la aplicación también aplaza el descarte de las superficies espaciales quitadas durante la pérdida de seguimiento.
* En general, una aplicación debe evaluar el equilibrio entre el menor procesamiento de actualizaciones y el aumento del uso de memoria para determinar su estrategia de almacenamiento en caché ideal.

## <a name="rendering"></a>Representación

Hay tres formas principales en las que las mallas de asignación espacial tienden a usarse para la representación:
* Para la visualización de la superficie
   * A menudo resulta útil visualizar las superficies espaciales directamente. Por ejemplo, la conversión de "sombras" de objetos en superficies espaciales puede proporcionar comentarios visuales útiles al usuario mientras coloca hologramas en superficies.
   * Algo que hay que tener en cuenta es que las mallas espaciales son diferentes al tipo de mallas que un dibujante 3D podría crear. La topología de triángulo no será tan "limpia" como la topología creada por el usuario y la malla sufrirá [varios errores](spatial-mapping.md#what-influences-spatial-mapping-quality).
   * Para crear una apariencia visual agradable, puede que desee realizar algún procesamiento de [malla,](spatial-mapping.md#mesh-processing)por ejemplo, para rellenar los huecos o normales de superficie suavizada. También puede usar un sombreador para proyectar texturas diseñadas por el autor en la malla en lugar de visualizar directamente la topología y las normales de la malla.
* Para oclusión de hologramas detrás de superficies reales
   * Las superficies espaciales se pueden representar en un paso [](/windows/win32/direct3d9/depth-buffers) de solo profundidad, lo que solo afecta al búfer de profundidad y no afecta a los destinos de representación de color.
   * Esto prime el búfer de profundidad para occluir hologramas representados posteriormente detrás de superficies espaciales. La oclusión precisa de hologramas mejora la sensación de que los hologramas existen realmente dentro del espacio físico del usuario.
   * Para habilitar la representación de solo profundidad, actualice el estado de mezcla para establecer [RenderTargetWriteMask](/windows/win32/api/d3d11_1/ns-d3d11_1-d3d11_render_target_blend_desc1) en cero para todos los destinos de representación de color.
* Para modificar la apariencia de los hologramas ocluido por superficies del mundo real
   * Normalmente, la geometría que se representa se oculta cuando se oculta. Esto se consigue estableciendo la [](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) función de profundidad en el estado de la galería de símbolos de profundidad  en "menor o igual", lo que hace que la geometría sea visible solo cuando está más cerca de la cámara que toda la geometría que se representó anteriormente.
   * Sin embargo, puede ser útil mantener cierta geometría visible incluso cuando se haya ocluido y modificar su apariencia cuando se haya ocluido como una forma de proporcionar comentarios visuales al usuario. Por ejemplo, esto permite que la aplicación muestre al usuario la ubicación de un objeto a la vez que deja claro que está detrás de una superficie real.
   * Para ello, represente la geometría una segunda vez con un sombreador diferente que cree la apariencia "ocluida" deseada. Antes de representar la geometría por segunda vez, realice dos cambios en el estado de la galería de símbolos [de profundidad.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) En primer lugar, establezca la función de profundidad en "mayor o igual  que" para que la geometría solo sea visible cuando esté más lejos de la cámara que toda la geometría que se representó anteriormente. En segundo lugar, establezca DepthWriteMask en cero, para que no se modifique el búfer de  profundidad (el búfer de profundidad debe seguir representando la profundidad de la geometría más cercana a la cámara).

[El rendimiento](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) es un problema importante al representar mallas de asignación espacial. Estas son algunas técnicas de rendimiento de representación específicas de la representación de mallas de asignación espacial:
* Ajustar la densidad del triángulo
   * Al solicitar mallas de superficie espacial del observador de superficie, solicite la menor densidad de mallas de triángulo que sea suficiente para sus necesidades.
   * Puede tener sentido variar la densidad del triángulo en una superficie por superficie, en función de la distancia de la superficie con el usuario y su relevancia para la experiencia del usuario.
   * La reducción de los recuentos de triángulos reducirá el uso de memoria y los costos de procesamiento de vértices en la GPU, aunque no afectará a los costos de procesamiento de píxeles.
* Uso de la selección de frustum
   * La selección de frustum omite los objetos de dibujo que no se pueden ver porque están fuera del frustum de presentación actual. Esto reduce los costos de procesamiento de CPU y GPU.
   * Dado que la selección se realiza por malla y las superficies espaciales pueden ser grandes, dividir cada malla de superficie espacial en fragmentos más pequeños puede dar lugar a una selección más eficaz (en que se representan menos triángulos fuera de pantalla). Sin embargo, hay un acuerdo; Entre más mallas tenga, más llamadas a draw debe realizar, lo que puede aumentar los costos de CPU. En un caso extremo, los cálculos de cálculos de cálculos frustum podrían incluso tener un costo de CPU cuantificable.
* Ajustar el orden de representación
   * Las superficies espaciales tienden a ser grandes, ya que representan todo el entorno del usuario que las rodea. Los costos de procesamiento de píxeles en la GPU pueden ser elevados, especialmente en los casos en los que hay más de una capa de geometría visible (incluidas las superficies espaciales y otros hologramas). En este caso, la capa más cercana al usuario estará ocultando las capas más alejadas, por lo que cualquier tiempo de GPU dedicado a representar esas capas más lejanas se desperdicia.
   * Para reducir este trabajo redundante en la GPU, ayuda a representar superficies opacas en orden de front-to-back (más cercanas primero, más lejanas). Por "opaco", nos refieremos a superficies para las que DepthWriteMask se establece en una en el estado de la galería [de símbolos de profundidad.](/windows/win32/api/d3d11/ns-d3d11-d3d11_depth_stencil_desc) Cuando se representan las superficies más cercanas, se prime el búfer de profundidad para que el procesador de píxeles de la GPU omita eficazmente las superficies más lejanas.

## <a name="mesh-processing"></a>Procesamiento de malla

Es posible que una aplicación quiera realizar [varias operaciones en](spatial-mapping.md#mesh-processing) mallas de superficie espacial para satisfacer sus necesidades. Los datos de índice y vértice proporcionados con cada malla de superficie espacial usan el mismo diseño conocido que los búferes de vértice e índice que se usan para representar [mallas](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) de triángulo en todas las API de representación modernas. Sin embargo, un hecho clave que se debe tener en cuenta es que los triángulos de asignación espacial tienen un orden de sinuoso en el sentido **de las agujas del reloj.** Cada triángulo se representa mediante tres índices de vértice en el búfer de índice de la malla  y estos índices identificarán los  vértices del triángulo en el orden de las agujas del reloj, cuando el triángulo se vea desde el lado frontal. El lado frontal (o exterior) de las mallas de superficie espacial se corresponde con el lado frontal (visible) de las superficies del mundo real.

Las aplicaciones solo deben realizar la simplificación de mallas si la densidad de triángulo más gruesa proporcionada por el observador de la superficie sigue siendo insuficientemente gruesa: este trabajo es costoso desde el punto de vista computacional y ya lo está realizando el tiempo de ejecución para generar los distintos niveles de detalle proporcionados.

Dado que cada observador de superficie puede proporcionar varias superficies espaciales no conectadas, es posible que algunas aplicaciones deseen recortar estas mallas de superficie espacial entre sí y, a continuación, unirlas. En general, el paso de recorte es necesario, ya que las mallas de superficie espacial cercanas a menudo se superponen ligeramente.

## <a name="raycasting-and-collision"></a>Difusión de rayos y colisión

Para que una API física (como [Havok)](https://www.havok.com/)proporcione una aplicación con funcionalidad de rayos y colisión para superficies espaciales, la aplicación debe proporcionar mallas de superficie espacial a la API física. Las mallas usadas para la física a menudo tienen las siguientes propiedades:
* Contienen solo un pequeño número de triángulos. Las operaciones físicas son más computacionalmente intensivas que las operaciones de representación.
* Están "aprietos de agua". Las superficies diseñadas para ser sólidas no deben tener pequeños huecos; incluso los huecos demasiado pequeños para ser visibles pueden causar problemas.
* Se convierten en cascos convexas. Las cascos convexas tienen pocos polígonos y están libres de huecos, y son mucho más eficaces computacionalmente para procesar que las mallas de triángulo sin formato.

Al realizar difusión por rayos en superficies espaciales, tenga en cuenta que estas superficies suelen ser formas complejas y desordenadas llenas de pequeños detalles desordenados, al igual que su escritorio. Esto significa que un único raycast suele ser insuficiente para proporcionar suficiente información sobre la forma de la superficie y la forma del espacio vacío cerca de ella. Normalmente es una buena idea realizar muchos raycasts dentro de un área pequeña y usar los resultados agregados para obtener una comprensión más confiable de la superficie. Por ejemplo, si se usa el promedio de 10 raycasts para guiar la colocación de hologramas en una superficie, se produce un resultado mucho más suave y menos "vibración" que con un solo raycast.

Sin embargo, tenga en cuenta que cada transmisión por rayos puede tener un alto costo computacional. En función del escenario de uso, debe cambiar el costo computacional de los raycasts [](spatial-mapping.md#mesh-processing) adicionales (que se realizan en cada fotograma) con el costo computacional del procesamiento de malla para suavizar y quitar los huecos de las superficies espaciales (que se realizan cuando se actualizan las mallas espaciales).

## <a name="the-environment-scanning-experience"></a>La experiencia de análisis del entorno

Cada aplicación que usa la asignación espacial debe considerar la posibilidad de proporcionar una "experiencia de examen". proceso a través del cual la aplicación guía al usuario para examinar las superficies necesarias para que la aplicación funcione correctamente.

![Ejemplo de examen](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Ejemplo de examen*

La naturaleza de esta experiencia de análisis puede variar considerablemente en función de las necesidades de cada aplicación, pero dos principios principales deben guiar su diseño.

En primer lugar, **la comunicación clara con el usuario es la principal preocupación.** El usuario siempre debe tener en cuenta si se cumplen los requisitos de la aplicación. Cuando no se cumplen, debe ser claro inmediatamente al usuario por qué es así y se le debe llevar rápidamente a realizar la acción adecuada.

En segundo lugar, **las aplicaciones deben intentar lograr un equilibrio entre eficacia y confiabilidad.** Cuando sea posible hacerlo de forma **confiable,** las aplicaciones deben analizar automáticamente los datos de asignación espacial para ahorrar tiempo al usuario. Cuando no es posible hacerlo de forma confiable, las aplicaciones deberían permitir al usuario proporcionar rápidamente a la aplicación la información adicional que requiere.

Para ayudar a diseñar la experiencia de análisis adecuada, tenga en cuenta cuáles de las siguientes posibilidades son aplicables a la aplicación:

* **Sin experiencia de análisis**
   * Una aplicación puede funcionar perfectamente sin ninguna experiencia de examen guiado. aprenderá sobre las superficies que se observan en el transcurso del movimiento natural del usuario.
   * Por ejemplo, una aplicación que permite al usuario dibujar en superficies con pintura de aspersión holográfica solo requiere conocimiento de las superficies visibles actualmente para el usuario.
   * El entorno ya se puede examinar si es uno en el que el usuario ya ha dedicado mucho tiempo a usar HoloLens.
   * Sin embargo, tenga en cuenta que la cámara usada por la asignación espacial solo puede ver 3,1 m delante del usuario, por lo que la asignación espacial no conocerá ninguna superficie más lejana a menos que el usuario las haya observado desde una distancia más cercana en el pasado.
   * Para que el usuario entienda qué superficies se han examinado, la aplicación debe proporcionar comentarios visuales sobre este efecto; por ejemplo, la conversión de sombras virtuales en superficies examinadas puede ayudar al usuario a colocar hologramas en esas superficies.
   * En este caso, los volúmenes delimitadores del observador de superficie espacial deben actualizarse a un sistema de coordenadas [espaciales](coordinate-systems.md)bloqueado por el cuerpo para que sigan al usuario.

* **Buscar una ubicación adecuada**
   * Una aplicación se puede diseñar para su uso en una ubicación con requisitos específicos.
   * Por ejemplo, la aplicación puede requerir un área vacía alrededor del usuario para que pueda practicar con seguridad holographic holo-fu.
   * Las aplicaciones deben comunicar al usuario por adelantado los requisitos específicos y reforzarlos con comentarios visuales claros.
   * En este ejemplo, la aplicación debe visualizar la extensión del área vacía necesaria y resaltar visualmente la presencia de objetos no deseados dentro de esta zona.
   * En este caso, los volúmenes delimitadores del observador de superficie espacial deben usar un sistema de coordenadas [espaciales](coordinate-systems.md) bloqueado por el mundo en la ubicación elegida.

* **Buscar una configuración adecuada de superficies**
   * Una aplicación puede requerir una configuración específica de superficies, por ejemplo, dos grandes paredes planas y opuestas para crear una sala holográfica de reflejos.
   * En tales casos, la aplicación deberá analizar las superficies proporcionadas por la asignación espacial para detectar superficies adecuadas y dirigir al usuario hacia ellas.
   * El usuario debe tener una opción de reserva si el análisis de la superficie de la aplicación no es confiable. Por ejemplo, si la aplicación identifica incorrectamente una puerta como una pared plana, el usuario necesita una manera sencilla de corregir este error.

* **Examen de parte del entorno**
   * Es posible que una aplicación solo desee capturar parte del entorno, tal como lo indica el usuario.
   * Por ejemplo, la aplicación examina parte de una sala para que el usuario pueda publicar un anuncio clasificado holográficamente para los artículos que quiere vender.
   * En este caso, la aplicación debe capturar datos de asignación espacial dentro de las regiones observadas por el usuario durante su examen.

* **Examinar toda la sala**
   * Una aplicación puede requerir un examen de todas las superficies de la sala actual, incluidas las que hay detrás del usuario.
   * Por ejemplo, un juego puede poner al usuario en el rol deIver, bajo el dominio de cientos de pequeños llenses que se aproximan desde todas las direcciones.
   * En tales casos, la aplicación deberá determinar cuántas de las superficies de la sala actual ya se han examinado y dirigir la mirada del usuario para rellenar espacios significativos.
   * La clave de este proceso es proporcionar comentarios visuales que le aclaran al usuario qué superficies aún no se han analizado. La aplicación podría, por [](/windows/win32/direct3d9/fog-formulas) ejemplo, usar la curva basada en la distancia para resaltar visualmente las regiones que no están cubiertas por superficies de asignación espacial.

* **Tomar una instantánea inicial del entorno**
   * Es posible que una aplicación quiera omitir todos los cambios en el entorno después de tomar una "instantánea" inicial.
   * Esto puede ser adecuado para evitar la interrupción de los datos creados por el usuario que están estrechamente acoplados al estado inicial del entorno.
   * En este caso, la aplicación debe realizar una copia de los datos de asignación espacial en su estado inicial una vez completado el examen.
   * Las aplicaciones deben seguir recibiendo actualizaciones de los datos de asignación espacial si el entorno todavía debe ocluyér correctamente los hologramas.
   * Las actualizaciones continuas de los datos de asignación espacial también permiten visualizar los cambios que se han producido, lo que aclara al usuario las diferencias entre los estados anteriores y actuales del entorno.

* **Tomar instantáneas iniciadas por el usuario del entorno**
   * Es posible que una aplicación solo desee responder a los cambios del entorno cuando lo indique el usuario.
   * Por ejemplo, el usuario podría crear varias "lonciones" en 3D de un amigo mediante la captura de sus poses en momentos diferentes.

* **Permitir al usuario cambiar el entorno**
   * Una aplicación puede diseñarse para responder en tiempo real a los cambios realizados en el entorno del usuario.
   * Por ejemplo, el usuario que dibuja una escena podría desencadenar un "cambio de escena" para una reproducción holográfica que tiene lugar en el otro lado.

* **Guía al usuario para evitar errores en los datos de asignación espacial**
   * Es posible que una aplicación desee proporcionar instrucciones al usuario mientras está analizando su entorno.
   * Esto puede ayudar al usuario a evitar ciertos tipos de errores en los datos de asignación [espacial,](spatial-mapping.md#what-influences-spatial-mapping-quality)por ejemplo, al mantenerse alejado de las ventanas o reflejos de la luz solar.

Un detalle adicional que debe tener en cuenta es que el "intervalo" de datos de asignación espacial no es ilimitado. Aunque la asignación espacial crea una base de datos permanente de espacios grandes, solo hace que los datos estén disponibles para las aplicaciones en una "burbuja" de tamaño limitado en torno al usuario. Si empieza al principio de un recorrido largo y se aleja lo suficiente del principio, las superficies espaciales al principio desaparecerán. Puede mitigar esto almacenando en caché esas superficies en la aplicación después de que han desaparecido de los datos de asignación espacial disponibles.

## <a name="mesh-processing"></a>Procesamiento de malla

Puede ayudar a detectar tipos comunes de errores en las superficies y a filtrar, quitar o modificar los datos de asignación espacial según corresponda.

Tenga en cuenta que los datos de asignación espacial están diseñados para ser lo más modernos posible para las superficies del mundo real, por lo que cualquier procesamiento que aplique corre riesgos que desplazan las superficies más allá de la "verdad".

Estos son algunos ejemplos de diferentes tipos de procesamiento de malla que pueden resultar útiles:

* **Relleno de huecos**
   * Si un objeto pequeño hecho de un material oscuro no se puede examinar, dejará un hueco en la superficie circundante.
   * Los huecos afectan a la oclusión: los hologramas se pueden ver "a través" de un hueco en una superficie del mundo real que se supone opaca.
   * Los huecos afectan a los rayos: si usa raycasts para ayudar a los usuarios a interactuar con las superficies, es posible que no sea conveniente que estos rayos pasen por los huecos. Una mitigación es usar un conjunto de varios raycasts que abarcan una región de tamaño adecuado. Esto le permitirá filtrar los resultados de "valores atípicos", de modo que incluso si un raycast pasa a través de un pequeño hueco, el resultado agregado seguirá siendo válido. Sin embargo, este enfoque tiene un costo computacional.
   * Los huecos afectan a las colisiones físicas: un objeto controlado por la simulación física puede pasar por un hueco en el suelo y perderse.
   * Es posible rellenar de forma algorítmica estos huecos en la malla de superficie. Sin embargo, tendrá que ajustar el algoritmo para que los "huecos reales", como las ventanas y las puertas, no se llenen. Puede ser difícil diferenciar de forma confiable los "huecos reales" de los "huecos imaginarios", por lo que deberá experimentar con heurísticas diferentes, como "tamaño" y "forma de límite".

* **Eliminación de la exclamación**
   * Los reflejos, las luces brillantes y los objetos en movimiento pueden dejar pequeñas "salas" persistentes flotantes en el aire.
   * Las salas afectan a la oclusión: las salas pueden ser visibles a medida que las formas oscuras se mueven delante de otros hologramas y se ocultan.
   * Las salas afectan a los rayos: si usas raycasts para ayudar a los usuarios a interactuar con las superficies, estos rayos podrían alcanzar una halluciación en lugar de la superficie subyacente. Al igual que con los huecos, una mitigación es usar muchos raycasts en lugar de un solo raycast, pero de nuevo esto tendrá un costo computacional.
   * Las salas afectan a las colisiones físicas: un objeto controlado por la simulación física puede quedarse bloqueado contra una aclaración y no poder moverse a través de un área de espacio aparentemente clara.
   * Es posible filtrar estas aclaraciones de la malla de superficie. Sin embargo, al igual que con los huecos, deberá ajustar el algoritmo para que no se quiten objetos pequeños reales, como los puestos de luces y los manipuladores de las puertas.

* **Alisar**
   * La asignación espacial puede devolver superficies que parecen ser aproximadas o "ruidosas" en comparación con sus homólogos reales.
   * La suavizado afecta a las colisiones físicas: si el suelo es áspero, es posible que una bola física simulada no se revierte sin problemas a través de ella en una línea recta.
   * La suavizado afecta a la representación: si una superficie se visualiza directamente, las normales de superficie aproximada pueden afectar a su apariencia e interrumpir una apariencia "limpia". Es posible mitigar esto mediante el uso de la iluminación y texturas adecuadas en el sombreador que se usa para representar la superficie.
   * Es posible suavizar la rugosidad en una malla de superficie. Sin embargo, esto puede alejar la superficie de la superficie real correspondiente. Mantener una correspondencia estrecha es importante para generar una oclusión precisa de hologramas y permitir a los usuarios lograr interacciones precisas y predecibles con superficies holográficas.
   * Si solo se requiere un cambio de textura, puede ser suficiente para suavizar las normales de los vértices sin cambiar las posiciones de los vértices.

* **Búsqueda de plano**
   * Hay muchas formas de análisis que una aplicación puede desear realizar en las superficies proporcionadas por la asignación espacial.
   * Un ejemplo sencillo es "búsqueda de plano"; identificar regiones limitadas, principalmente planas de superficies.
   * Las regiones planas se pueden usar como superficies de trabajo holográficas, regiones donde la aplicación puede colocar automáticamente el contenido holográfico.
   * Las regiones planas pueden restringir la interfaz de usuario para guiar a los usuarios a interactuar con las superficies que mejor se adapten a sus necesidades.
   * Las regiones planas se pueden usar como en el mundo real, para homólogos holográficos de objetos funcionales, como pantallas, tablas o pizarras de HOLOR.
   * Las regiones planas pueden definir áreas de juego, formando la base de los niveles de los juegos de vídeo.
   * Las regiones planas pueden ayudar a los agentes virtuales a navegar por el mundo real, mediante la identificación de las áreas de suelo por las que es probable que los usuarios reales pasen.

## <a name="prototyping-and-debugging"></a>Creación de prototipos y depuración

### <a name="useful-tools"></a>Herramientas útiles

* El [emulador de HoloLens](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md) se puede usar para desarrollar aplicaciones mediante asignación espacial sin acceso a un Dispositivo HoloLens físico. Permite simular una sesión en directo en holoLens en un entorno realista, con todos los datos que normalmente consumiría la aplicación, incluidos el movimiento de HoloLens, los sistemas de coordenadas espaciales y las mallas de asignación espacial. Esto se puede usar para proporcionar una entrada confiable y repetible, que puede ser útil para depurar problemas y evaluar los cambios en el código.
* Para reproducir un escenario, capture datos de asignación espacial a través de la red desde un HoloLens dinámico y guárdelos en el disco y reutilice en sesiones de depuración posteriores.
* La [vista 3D del portal de](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#3d-view) dispositivos Windows proporciona una manera de ver todas las superficies espaciales disponibles actualmente a través del sistema de asignación espacial. Esto proporciona una base de comparación para las superficies espaciales dentro de la aplicación. Por ejemplo, puede saber fácilmente si faltan superficies espaciales o si se muestran en un lugar incorrecto.

### <a name="general-prototyping-guidance"></a>Guía general de creación de prototipos

* Dado [que](spatial-mapping.md#what-influences-spatial-mapping-quality) los errores en los datos de asignación espacial pueden afectar en gran medida a la experiencia del usuario, se recomienda probar la aplicación en una amplia variedad de entornos.
* No se queme con el hábito de probar siempre en la misma ubicación, por ejemplo, en el escritorio. Asegúrese de probar en varias superficies de diferentes posiciones, formas, tamaños y materiales.
* De forma similar, aunque los datos sintéticos o registrados pueden ser útiles para la depuración, no dependen demasiado de los mismos casos de prueba. Esto puede retrasar la búsqueda de problemas importantes que las pruebas más diversas hubieran descubierto anteriormente.
* Es una buena idea realizar pruebas con usuarios reales (e idealmente sincoached), ya que es posible que no usen HoloLens o la aplicación exactamente de la misma manera que usted. De hecho, puede que le sorprenda lo divergentes que pueden ser el comportamiento, el conocimiento y las suposiciones de las personas divergentes.

## <a name="troubleshooting"></a>Solución de problemas

* Para que las mallas de superficie se orienten correctamente, cada GameObject debe estar activo antes de que se envíe a SurfaceObserver para que se construya su malla. De lo contrario, las mallas se mostrarán en el espacio, pero giradas en ángulos extraños.
* El Objeto GameObject que ejecuta el script que se comunica con SurfaceObserver debe establecerse en el origen. De lo contrario, todos los Objetos GameObject que cree y envíe a SurfaceObserver para que sus mallas se construyan tendrán un desplazamiento igual al desplazamiento del objeto de juego primario. Esto puede hacer que las mallas se muestren a varios metros de distancia, lo que dificulta la depuración de lo que sucede.

## <a name="see-also"></a>Consulte también

* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial en DirectX](../develop/native/spatial-mapping-in-directx.md)
* [Asignación espacial en Unity](../develop/unity/spatial-mapping-in-unity.md)
* [Descripción de la escena](scene-understanding.md)
* [Visualización de la exploración de la sala](room-scan-visualization.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Case study - Looking through holes in your reality](../out-of-scope/case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)