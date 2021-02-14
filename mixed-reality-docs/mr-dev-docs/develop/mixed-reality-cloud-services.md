---
layout: LandingPage
title: Introducción a los servicios en la nube de realidad mixta de Azure
description: Obtenga información sobre todos los servicios en la nube de Azure Mixed Reality que puede integrar en sus aplicaciones de Unity o Unreal.
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, develop, development, HoloLens, cloud services, Azure, remote rendering, spatial anchors, cognitive services, cognition, unity, machine learning, speech translation, computer vision, Microsoft Graph
ms.openlocfilehash: abd1515b587842dbccb1747b606059e190559480
ms.sourcegitcommit: 07d6a5c19c9f6ffd0316bce5629ab0e185e1d542
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99973075"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Introducción a los servicios en la nube de realidad mixta de Azure

![ Imagen de Azure Spatial Anchors](../design/images/AzureSpatialAnchors.jpg)

Libere las mejores aptitudes de los usuarios del mundo físico tridimensional que nos rodea mediante los servicios de realidad mixta de Azure. Ayude a los usuarios a crear, aprender y colaborar de forma más eficaz mediante la captura y exposición de información digital en el contexto de su trabajo y mundo. Incorpore la opción 3D en dispositivos móviles, cascos y otros dispositivos no vinculados. Con Azure, asegúrese de que la información más confidencial está protegida.

## <a name="mixed-reality-services"></a>Servicios de realidad mixta

Los servicios en la nube de realidad mixta, como **Azure Remote Rendering** y **Azure Spatial Anchors**, ayudan a los desarrolladores a crear atractivas experiencias envolventes en una gran variedad de plataformas. Estos servicios permiten integrar el reconocimiento espacial en los proyectos al crear aplicaciones para el aprendizaje en 3D, el mantenimiento predictivo de los equipos y la revisión del diseño. Todo esto, en el contexto de los entornos de los usuarios.

### <a name="azure-remote-rendering"></a>Azure Remote Rendering

[Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering/) o ARR es un servicio que le permite representar modelos 3D muy complejos en tiempo real y hacer streaming de ellos en un dispositivo. Actualmente, ARR se encuentra en versión preliminar y se puede agregar a los proyectos de Unity o C++ nativo que tienen HoloLens 2 o el equipo de escritorio de Windows como destino.

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR es un componente esencial de cualquier aplicación de realidad mixta que se ejecuta en un dispositivo sin vincular, ya que tiene menos potencia de representación de cálculo. Realice la siguiente comparación de modelos de motor en paralelo como ejemplo. el modelo de alta fidelidad de la izquierda tiene más de 18 millones triángulos, mientras que el modelo reducido de la derecha tiene solo unos 200 000. En aquellos escenarios en los que cada detalle es importante, la administración de plantas industrial, la revisión de diseños de los recursos, como los motores de camiones, la planificación de cirugías preoperatorias, etc., la visualización 3D aporta ese detalle al ciclo de vida. Permite a los diseñadores, ingenieros, médicos y estudiantes entender mejor la información compleja y adoptar la medida correcta. Sin embargo, esta simplificación puede dar lugar a una pérdida de detalles importantes que se necesitan en las decisiones clave sobre la empresa y el diseño.

![Ejemplo de Azure Remote Rendering en la aplicación de presentación de Unity](images/arr-engine.png)

ARR resuelve este problema, ya que mueve la carga de trabajo de representación a las GPU de alta gama en la nube. A continuación, un motor de gráficos hospedado en la nube toma la imagen y la representa, la codifica como una secuencia de vídeo y transmite el modelo directamente al dispositivo de destino. 

* En el caso de los modelos complejos que son demasiado grandes para que pueda controlarlos una GPU de alta gama, ARR distribuye la carga de trabajo a varias GPU y combina el resultado en una sola imagen, lo que permite que el proceso sea completamente transparente para el usuario. 

Como ventaja adicional, ARR no restringe el tipo de interfaz de usuario que puede usar en la aplicación. Al final de un fotograma, el contenido representado localmente se combina automáticamente con la imagen remota, tal como se muestra en la imagen siguiente:

![Ejemplo de Azure Remote Rendering en la aplicación de presentación de Unity](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

[Azure Spatial Anchors](https://docs.microsoft.com /azure/spatial-anchors/) es un servicio multiplataforma que permite crear aplicaciones de realidad mixta con reconocimiento espacial. Con Azure Spatial Anchors, puede asignar, conservar y compartir contenido holográfico en varios dispositivos a escala real. 

Azure Spatial Anchors es una solución especialmente adaptada a casos de uso comunes de realidad mixta, entre otros:
* **Orientación**: en que dos o más anclajes espaciales podrían conectarse para crear una lista de tareas o puntos de interés con los que un usuario debe interactuar.
* **Experiencias de varios usuarios**: En que los usuarios pueden hacer o deshacer movimientos al interactuar con los objetos del mismo espacio virtual.
* **Conservación del contenido virtual en el mundo real**: en que los usuarios podrían colocar objetos virtuales en el mundo real que se puedan ver desde otros dispositivos compatibles.

![Ejemplo de Azure Spatial Anchors](images/persistence.gif)

El servicio puede desarrollarse en un host de entornos e implementarse en un gran grupo de dispositivos y plataformas. Esto les proporciona una distribución especial de su propia lista de plataformas disponibles:
* Unity para HoloLens
* Unity para iOS
* Unity para Android
* iOS nativo
* Android nativo
* C++/WinRT y DirectX para HoloLens
* Xamarin para iOS
* Xamarin para Android

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![Voz](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Voz](/azure/cognitive-services/speech-service/)
        Descubra cómo Speech permite la integración de funcionalidades de procesamiento de voz en cualquier aplicación o servicio. Convierta el idioma hablado en texto o genere voz que suene de forma natural a partir del texto con fuentes de voz estándar (o personalizables). Pruebe cualquier servicio gratis y compile rápidamente aplicaciones y servicios habilitados para voz con las siguientes funcionalidades.
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![Visión](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Visión](/azure/cognitive-services/computer-vision/)
        Reconozca, identifique, subtitule, indexe y modere sus imágenes, vídeos y contenido de entrada de lápiz digital. Descubra cómo Vision permite que las aplicaciones y los servicios identifiquen y analicen con precisión el contenido de imágenes, vídeos y entrada de lápiz digital.
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>Servicios de Unity independientes

Los servicios independientes que se enumeran a continuación no se aplican a la realidad mixta, pero pueden resultar útiles en una amplia variedad de contextos de desarrollo. Si está desarrollando contenido en Unity, cada uno de estos servicios se puede integrar en proyectos nuevos o existentes.

### <a name="device-support"></a>Compatibilidad con dispositivos
<table>
    <tr>
        <td><strong>Servicio en la nube de Azure</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1.ª generación</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">Traducción de idiomas</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Computer Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Custom Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">Notificaciones entre dispositivos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">Reconocimiento facial</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Funciones y almacenamiento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">Vídeo en streaming</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Aprendizaje automático</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Funciones y almacenamiento</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">Detección de objetos</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">Integración de bots</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>Consulte también

* Tutoriales de Azure Spatial Anchors para HoloLens 2: [1 de 3 Introducción a Azure Spatial Anchors](./unity/tutorials/mr-learning-asa-02.md)
* Tutoriales de Azure Speech Services para HoloLens 2: [1 de 4; Integración y uso del reconocimiento de voz y la transcripción](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
