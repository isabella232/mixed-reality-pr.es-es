---
title: Introducción al desarrollo con Unreal
description: Información general sobre el desarrollo para realidad mixta con Unreal Engine 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, remoting, mixed reality, development, getting started, features, new project, emulator, documentation, guides, features, holograms, game development
ms.openlocfilehash: 3b5dc5d0ce1510405960c6effd653acc9c2588b2
ms.sourcegitcommit: 9ab467e36d7d9fad51b0e93a56038a6421a7b09d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/13/2020
ms.locfileid: "91980346"
---
# <a name="unreal-development-overview"></a>Introducción al desarrollo con Unreal

![Logotipo del banner de Unreal](../images/unreal_logo_banner.png)

La introducción a <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="los documentos de realidad mixta"> aplicaciones de realidad mixta</a> es una gran tarea. Los nuevos conceptos, las plataformas y el hardware de vanguardia pueden parecer un obstáculo. Sin embargo, si es un desarrollador de Unreal, tiene suerte. Ahora se incluye compatibilidad con los <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="documentos de Windows Mixed Reality">Windows Mixed Reality</a> (VR) y con los <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="documentos de HoloLens 2">HoloLens 2</a> (AR) en <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="las notas de la versión de Unreal Engine 4.25 más reciente</a>la versión más reciente">. En esta actualización se incluye:
* Compatibilidad del complemento UX Tools de Mixed Reality
* Compatibilidad con OpenXR
* Control remoto de la aplicación desde una aplicación de escritorio
* Un mejor rendimiento
* Captura de realidad mixta
* Compatibilidad inicial con Azure Spatial Anchors

Si no está familiarizado con el desarrollo en Unreal, no empiece a ciegas. Explore la <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">serie de tutoriales</a> de Unreal para ponerse al día y buscar recursos y soporte técnico en <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> de Unreal y en los <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">foros</a> de la realidad mixta. Estos recursos son vínculos a la comunidad de creadores y solucionadores de problemas en el mercado de realidad mixta de hoy en día.

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unreal en el mundo de la realidad mixta. Si aún no ha explorado la [aplicación de ejemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), le recomendamos que la descargue y la use para familiarizarse con los aspectos básicos de la experiencia de usuario de realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

[Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) es un conjunto de componentes diseñados para acelerar el desarrollo en Unreal. Cada componente incluye complementos, ejemplos y documentación para configurar experiencias envolventes.

* [UX Tools para Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) es el primer componente que se va a publicar y actualmente solo se admite en HoloLens 2. El complemento de componente incluye código, planos técnicos y recursos de ejemplo de características de experiencia del usuario comunes para la simulación de entrada, los actores de interacción con manos, componentes de botones que se pueden presionar, componentes de manipulador y componentes de comportamiento de seguimiento.

Al final de esta sección, habrá adquirido conocimientos básicos sobre Mixed Reality Toolkit, un entorno de desarrollo configurado correctamente para aplicaciones de realidad mixta y un proyecto de MRTK de trabajo en Unity.

|  Punto de control  |  Resultado  |
| --- | --- |
| [Instale las actualizaciones más recientes.](../install-the-tools.md) | Descargue e instale el paquete de Unity más reciente y configure el proyecto para la realidad mixta. |
| [Serie de tutoriales de HoloLens 2](tutorials/unreal-uxt-ch1.md) | Profundice en los tutoriales de MRTK de nivel principiante para el hardware de HoloLens 2. |

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Hay varias características clave del desarrollo de la realidad mixta que nuestra serie de tutoriales no cubre. Estos bloques de creación están disponibles como características independientes y a través de Mixed Reality Toolkit. Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio. Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en sus proyectos de realidad mixta.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Puede explorar el repositorio de **[GitHub de UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)** para obtener más detalles.

### <a name="3-platform-capabilities-and-apis"></a>3. Funcionalidades y API de la plataforma

Hay otras características clave que desempeñan un rol en las aplicaciones de realidad mixta disponibles sin que se requiera ningún paquete o instalación adicional. Estas características se pueden agregar a proyectos de Unreal tanto si se instala MRTK como si no. Después de profundizar en las funcionalidades más avanzadas, podrá crear aplicaciones de realidad mixta más complejas.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Cámara de HoloLens](unreal-hololens-camera.md) | Capture el contenido visual de realidad mixta y del mundo real de la aplicación que se ejecuta en un dispositivo HoloLens. |
| [Códigos QR](unreal-qr-codes.md) | Represente códigos QR como hologramas mediante un sistema de coordenadas en la posición del mundo real de cada código. |
| [WinRT](unreal-winrt.md) | Cree un archivo binario independiente con código de WinRT que el sistema de compilación de Unreal pueda usar. |

### <a name="4-deploying-to-a-device"></a>4. Implementación en un dispositivo

Si esta es la primera vez que crea o implementa una aplicación de Unreal para HoloLens, deberá [descargar los archivos auxiliares](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic. Una vez que haya instalado los archivos, estará listo para realizar la implementación desde el [editor de Unreal](unreal-deploying.md) o el [Portal de dispositivos](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Adición de servicios

En este momento del recorrido de desarrollo, es posible que quiera agregar servicios o obtener ayuda con la implementación comercial. La integración de las características de [Azure Cloud Services](../mixed-reality-cloud-services.md) y Dynamics 365 pueden mejorar sus los proyectos de una manera significativa. Hemos recopilado algunos puntos de partida para que pueda explorar y ampliar su conocimiento de realidad mixta.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="streaming--debugging"></a>Streaming y depuración

Si quiere probar la aplicación en un dispositivo HoloLens mientras esta sigue en desarrollo, puede [hacer streaming de ella directamente desde su PC](unreal-streaming.md) mediante el editor de Unreal o el archivo ejecutable de Windows empaquetado.

Si está pensando en la posibilidad de depurar la aplicación con Visual Studio, siga estas [instrucciones](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Rendimiento

El desarrollo para la realidad mixta incluye puntos de control de rendimiento que dependen de la plataforma. Una aplicación de HoloLens 2 debe ejecutarse a 60 fotogramas por segundo para que los hologramas presenten estabilidad y capacidad de respuesta. Afortunadamente, tenemos [recomendaciones de rendimiento](performance-recommendations-for-unreal.md) para lograrlo en sus aplicaciones de Unreal.

## <a name="supported-features"></a>Funciones admitidas

| Característica de HoloLens 2 | Versión anterior de Unreal Engine admitida |
| ----------- | ----------- |
| Compatibilidad con ARM64 | 4.23 |
| Streaming desde un equipo | 4.23 |
| Asignación espacial | 4.23 |
| Seguimiento de manos y articulaciones | 4.23 |
| Seguimiento de los ojos | 4.23 |
| Entrada de voz | 4.23 |
| Delimitadores espaciales | 4.23 |
| Acceso a la cámara | 4.23 |
| Códigos QR | 4.23 |
| Audio espacial | 4.23 |
| Compatibilidad con la pantalla de espectador para streaming | 4.24 |
| LSR plana por streaming | 4.24 |
| Las aplicaciones de muestra ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) y [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Modo multivista móvil: resultados de rendimiento de 60 fps | 4.25 |
| Representación de tercera cámara | 4.25 |
| Streaming desde una aplicación de escritorio empaquetada | 4.25.1 |
| Azure Spatial Anchors para HoloLens 2 (beta) | 4.25 |
| Compatibilidad con OpenXR (beta) | 4.25 |
| Compatibilidad con UX Tools (0.8) | 4.25 |
| Tutoriales y documentación para desarrolladores | 4.25 |

> [!div class="nextstepaction"]
> [Instalación de las herramientas](../install-the-tools.md)

## <a name="see-also"></a>Consulta también
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Documentación de Unreal para streaming e implementación en el emulador y el dispositivo</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Instrucciones de rendimiento de Unreal para dispositivos móviles</a>
