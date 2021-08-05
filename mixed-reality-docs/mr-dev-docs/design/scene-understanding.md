---
title: Descripción de escenas
description: Obtenga información sobre cómo desarrollar con la comprensión de la escena HoloLens, incluidos el SDK, las funcionalidades y los escenarios de uso comunes.
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: Comprensión de la escena, asignación espacial, Windows Mixed Reality, Unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, oclusión, SDK
ms.openlocfilehash: 4dd5a2c96478e50b2e9eda35be22c15c1db07f88cfc4d25d753c4860a1283f55
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213474"
---
# <a name="scene-understanding"></a>Descripción de escenas

La descripción de escenas aporta a los desarrolladores de realidad mixta una representación estructurada y general del entorno, diseñada para que el desarrollo para aplicaciones con control del entorno sea intuitivo. La comprensión de la escena lo hace combinando la potencia de los [](spatial-mapping.md) entornos de ejecución de realidad mixta existentes, como la asignación espacial altamente precisa pero menos estructurada y los nuevos entornos de ejecución controlados por IA. Mediante la combinación de estas tecnologías, scene understanding genera representaciones de entornos 3D similares a los que puede haber usado en marcos como Unity o ARKit/ARCore. El punto de entrada scene understanding comienza con un observador de escena, al que llama la aplicación para calcular una nueva escena. En la actualidad, la tecnología puede generar tres categorías de objetos distintas pero relacionadas:

* Mallas de entorno estancas simplificadas que deducen la estructura plana de la sala sin desorden
* Regiones de plano para la selección de ubicación a las que llamamos Quads
* Instantánea de la malla [de asignación](spatial-mapping.md) espacial que se alinea con los datos quads/watertight que se superficie

![Malla de asignación espacial, superficies planas etiquetadas, malla estanca](images/SUScenarios.png)

Este documento está pensado para proporcionar una visión general del escenario y aclarar la relación que comparten La comprensión de la escena y la asignación espacial. Si quiere ver Scene Understanding en acción, consulte nuestra demostración de vídeo **Designing Hologramas - Spatial Awareness** a continuación:

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

*Este vídeo se tomó de la aplicación "Designing Holograms" para HoloLens 2. Descargue y disfrute de la experiencia completa [aquí](https://aka.ms/dhapp).*

## <a name="developing-with-scene-understanding"></a>Desarrollo con Scene Understanding

Este artículo solo sirve para presentar el entorno de ejecución y los conceptos de Scene Understanding. Si busca documentación sobre cómo desarrollar con Scene Understanding, es posible que le interesen los siguientes artículos:

[Introducción al SDK de Scene Understanding](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

Puede descargar la aplicación Scene Understanding Sample desde el sitio de GitHub ejemplo:

[Ejemplo de scene understanding](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

Si no tiene un dispositivo y desea acceder a escenas de ejemplo para probar Scene Understanding out, hay escenas en la carpeta de recursos de ejemplo:

[Escenas de ejemplo de Descripción de la escena](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a>SDK

Si busca detalles específicos sobre el desarrollo con Scene Understanding, consulte la documentación de información general del [SDK de Scene Understanding.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

### <a name="sample"></a>Muestra

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
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Descripción de escenas</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a>Escenarios de uso comunes

![Ilustraciones de escenarios comunes de uso de asignaciones espaciales: selección de ubicación, oclusión, física y navegación](images/sm-concepts-1000px.png)<br>
*Escenarios comunes de uso de asignaciones espaciales: selección de ubicación, oclusión, física y navegación.*

<br>

Muchos de los escenarios principales de las aplicaciones que tienen en cuenta el entorno pueden abordarse mediante la asignación espacial y la comprensión de la escena. Estos escenarios principales incluyen la selección de ubicación, oclusión, física, entre otros. Una diferencia fundamental entre la comprensión de la escena y la asignación espacial es un equilibrio entre la precisión máxima y la latencia de la estructura y la simplicidad. Si la aplicación requiere la latencia más baja posible y triángulos de malla a los que solo desea acceder, use la asignación espacial directamente. Si está realizando un procesamiento de nivel superior, puede considerar la posibilidad de cambiar al modelo de descripción de la escena, ya que debería proporcionar un superconjunto de funcionalidad. Siempre tendrá acceso a los datos de asignación espacial más completos y precisos posibles, ya que la comprensión de la escena proporciona una instantánea de la malla de asignación espacial como parte de su representación.

En las secciones siguientes se revisan los escenarios principales de asignación espacial en el contexto del nuevo SDK de Scene Understanding.

### <a name="placement"></a>Selección de ubicación

La comprensión de la escena proporciona nuevas construcciones diseñadas para simplificar los escenarios de selección de ubicación. Una escena puede calcular primitivas llamadas SceneQuads, que describen superficies planas en las que se pueden colocar hologramas. SceneQuads se ha diseñado en torno a la selección de ubicación y describe una superficie 2D y proporciona una API para la selección de ubicación en esa superficie. Anteriormente, al usar la malla de triángulos para realizar la selección de ubicación, había que examinar todas las áreas del cuadrángulo y realizar el relleno de huecos o el procesamiento posterior para identificar las ubicaciones correctas para la colocación de objetos. Esto no siempre es necesario con quads, ya que scene understanding runtime deduce qué áreas de cuatro áreas no se han examinado e invalida áreas que no forman parte de la superficie.

:::row:::
    :::column:::
       ![SceneQuads con inferencia deshabilitada, capturando áreas de selección de ubicación para regiones examinadas.](images/SUQuads.png)<br>
       **Imagen #1:** SceneQuads con inferencia deshabilitada, capturando áreas de selección de ubicación para regiones examinadas.
    :::column-end:::
        :::column:::
       ![Quads con la inferencia habilitada, la selección de ubicación ya no se limita a las áreas examinadas.](images/SUWatertight.png)<br>
        **Imagen #2:** quads con inferencia habilitada, la selección de ubicación ya no se limita a las áreas examinadas.
    :::column-end:::
:::row-end:::

<br>


Si la aplicación pretende colocar hologramas 2D o 3D en estructuras rígidas de su entorno, es preferible la simplicidad [](spatial-mapping.md) y la comodidad de SceneQuads para la selección de ubicación para calcular esta información desde la malla de asignación espacial. Para obtener más información sobre este tema, consulte la referencia del [SDK de Descripción de la escena.](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

**Nota** Para el código de selección de ubicación heredado que depende de la malla de asignación espacial, la malla de asignación espacial se puede calcular junto con SceneQuads estableciendo la configuración EnableWorldMesh. Si Scene understanding API no satisface los requisitos de latencia de la aplicación, se recomienda seguir usando [la API de asignación espacial.](spatial-mapping.md#placement)

### <a name="occlusion"></a>Oclusión

[La oclusión de asignación](spatial-mapping.md#occlusion) espacial sigue siendo la manera menos latente de capturar el estado en tiempo real del entorno. Aunque esto puede ser útil para proporcionar oclusión en escenas altamente dinámicas, es posible que quiera considerar la comprensión de la escena para la oclusión por varias razones. Si usa la malla de asignación espacial generada por Scene Understanding, puede solicitar datos de la asignación espacial que no se almacenarán en la caché local y no estarán disponibles en las API de percepción. El uso de la asignación espacial para la oclusión junto con mallas estancas proporcionará un valor adicional, específicamente la finalización de la estructura de la sala sin examinar.

Si sus requisitos pueden tolerar el aumento de la latencia de la comprensión de la escena, los desarrolladores de aplicaciones deben considerar el uso de la malla watertight y la malla de asignación espacial al unísono con representaciones planas. Esto proporcionaría un escenario "lo mejor de ambos mundos" en el que la oclusión estanca simplificada se trata con una geometría no plana más fina que proporciona los mapas de oclusión más realistas posibles.

### <a name="physics"></a>Física

La comprensión de la escena genera mallas herméticas que descomponen el espacio con semántica, específicamente para abordar muchas limitaciones de la física que imponen las mallas de asignación espacial. Las estructuras herméticas garantizan que siempre se alcanzarán las contecciones de rayos físicos, y la descomposición semántica permite una generación más sencilla de mallas de navegación para la navegación en interiores. Como se describe en la sección sobre [oclusión,](#occlusion)la creación de una escena con EnableSceneObjectMeshes y EnableWorldMesh producirá la malla más completa físicamente posible. La propiedad estanca de la malla de entorno impide que las pruebas de acceso no se supere en las superficies de acceso. Los datos de malla garantizarán que la física interactúe con todos los objetos de la escena y no solo con la estructura de la sala.

### <a name="navigation"></a>Navegación

Las mallas planas descompuestas por la clase semántica son construcciones ideales para la navegación y el planeamiento de rutas, lo que facilita muchos de los problemas descritos en información general de navegación de asignación [espacial.](spatial-mapping.md#navigation) Los objetos SceneMesh calculados en la escena están descomponido por tipo de superficie, lo que garantiza que la generación de malla de navegación se limita a las superficies que se pueden andar. Debido a la simplicidad de las estructuras de suelo, la generación dinámica de malla de navegación en motores 3D como Unity se puede lograr en función de los requisitos en tiempo real.

La generación de mallas de navegación precisas todavía requiere el procesamiento posterior, es decir, las aplicaciones deben seguir proyectando occluders en la planta para asegurarse de que la navegación no pase por desorden o tablas, y así sucesivamente. La manera más precisa de hacerlo es proyectar los datos de la malla mundial, que se proporcionan si la escena se calcula con la marca EnableWorldMesh.

### <a name="visualization"></a>Visualización

Aunque [la visualización](spatial-mapping.md#visualization) de asignación espacial se puede usar para comentarios en tiempo real del entorno, hay muchos escenarios en los que la simplicidad de los objetos planas y herméticos proporciona más rendimiento o calidad visual. Las técnicas de proyección de sombras y de puesta a tierra que se describen mediante la asignación espacial pueden resultar más agradables si se proyectan en las superficies planas proporcionadas por quads o la malla plana estanca. Esto es especialmente cierto en entornos o escenarios en los que el examen previo exhaustivo no es óptimo porque la escena se deducirá y los entornos completos y las suposiciones planas minimizarán los artefactos.

Además, el número total de superficies devueltas por Asignación espacial está limitado por la caché espacial interna, mientras que la versión de La descripción de la escena de la malla de asignación espacial puede acceder a los datos de asignación espacial que no están almacenados en caché. Debido a esto, la comprensión de la escena es más adecuada para capturar representaciones de malla para espacios más grandes (por ejemplo, más grandes que una sola sala) para la visualización o el procesamiento de malla adicional. La malla mundial devuelta con EnableWorldMesh tendrá un nivel coherente de detalle a lo largo, lo que puede producir una visualización más atractiva si se representa como wireframe.

### <a name="see-also"></a>Consulte también

* [Scene understanding SDK](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [Asignación espacial](spatial-mapping.md)