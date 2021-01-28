---
title: Introducción al desarrollo con Unreal
description: Iníciese en el desarrollo de realidad mixta para HoloLens y VR con Unreal Engine 4 y nuestro recorrido de puntos de control seleccionados.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicación remota, realidad mixta, desarrollo, introducción, características, nuevo proyecto, emulador, documentación, guías, hologramas, desarrollo del juego, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, OpenXR
ms.openlocfilehash: a5b65bbfe5a1f365a93836406365fdc395b73c47
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580034"
---
# <a name="unreal-development-overview"></a>Introducción al desarrollo con Unreal

![Logotipo del banner de Unreal](../images/unreal_logo_banner.png)

La introducción a <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="los documentos de realidad mixta"> aplicaciones de realidad mixta</a> es una gran tarea. Los nuevos conceptos, las plataformas y el hardware de vanguardia pueden parecer un obstáculo. Sin embargo, si es un desarrollador de Unreal, tiene suerte. Unreal Engine 4 tiene compatibilidad total con los dispositivos de <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="documentos de Windows Mixed Reality">Windows Mixed Reality</a> (VR) y <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="documentos de HoloLens 2">HoloLens 2</a> (AR).

[!INCLUDE[](includes/tabs-unreal-features.md)]

Si no está familiarizado con el desarrollo en Unreal, no empiece a ciegas. Explore la <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">serie de tutoriales</a> de Unreal y busque recursos en el <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> de Unreal. También puede encontrar soporte en los <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">foros</a> de realidad mixta. Estos recursos son vínculos a la comunidad de creadores y solucionadores de problemas en el mercado de realidad mixta de hoy en día.

> [!IMPORTANT]
> Eche un vistazo a nuestra **[guía de migración](unreal-reverb-g2-controllers.md)** si tiene un proyecto de Unreal existente que quiere utilizar con cascos envolventes, como Reverb G2.

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unreal en el mundo de la realidad mixta. Si no ha explorado la [aplicación de ejemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), le recomendamos que la descargue para familiarizarse con los aspectos básicos de la experiencia de usuario de realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

En primer lugar, debe instalar las herramientas para el desarrollo de HoloLens 2. A continuación, revise nuestra serie de tutoriales para adquirir conocimientos básicos sobre Mixed Reality Toolkit, un entorno de desarrollo configurado correctamente para aplicaciones de realidad mixta y un proyecto de MRTK de trabajo en Unreal. A partir de la versión 4.26 de Unreal, también tiene la opción de desarrollar una aplicación de OpenXR para HoloLens 2.

|  Punto de control  |  Resultado  |
| --- | --- |
| [Instale las actualizaciones más recientes.](../install-the-tools.md) | Descargue e instale la versión más reciente de Unreal Engine y configure el proyecto para la realidad mixta. |
| [Serie de tutoriales de HoloLens 2](tutorials/unreal-uxt-ch1.md) | Prepárese para el desarrollo de realidad mixta en Unreal, compile su primera aplicación con MRTK e implemente la aplicación en HoloLens 2. |
| (Opcional) Introducción a [OpenXR](../native/openxr.md) en Unreal | Si está pensando en compilar una aplicación de OpenXR en Unreal, debe deshabilitar el siguiente complemento de motor:<ul><li>Windows Mixed Reality</li></ul><br>Descargue y habilite el siguiente complemento en el proyecto desde GitHub:<ul><li> [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)</li></ul><br>La lista completa de las características admitidas actualmente en OpenXR se incluye [a continuación](#supported-features).|

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Hay varias características clave de la realidad mixta que nuestra serie de tutoriales no cubre. Estos bloques de creación están disponibles como características independientes y a través de Mixed Reality Toolkit. Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio. Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en sus proyectos de realidad mixta.

[Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) es un conjunto de complementos diseñados para acelerar el desarrollo en Unreal. Cada complemento incluye componentes, ejemplos y documentación para configurar experiencias envolventes.

* [UX Tools para Unreal](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) es el primer complemento que se va a publicar y actualmente solo se admite en HoloLens 2. El complemento incluye código C++, planos técnicos y recursos de ejemplo de las características comunes de la experiencia de usuario para la simulación de entradas, las interacciones con la mano, el magnetismo de superficie y mucho más.

* [Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/) es un complemento de juego de UE con código, planos técnicos y recursos de ejemplo creados para ayudar a mejorar la fidelidad visual de las aplicaciones de realidad mixta sin salirse de los presupuestos de rendimiento.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Puede explorar el repositorio de **[GitHub de UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)** para obtener más detalles.

### <a name="3-advanced-features"></a>3. Características avanzadas

Hay otras características clave que desempeñan un rol en las aplicaciones de realidad mixta disponibles sin que se requiera ningún paquete o instalación adicional. Estas características se pueden agregar a proyectos de Unreal tanto si se instala MRTK como si no. Después de profundizar en las funcionalidades más avanzadas, podrá crear aplicaciones de realidad mixta más complejas.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Cámara de HoloLens](unreal-hololens-camera.md) | Capture el contenido visual de realidad mixta y del mundo real de la aplicación que se ejecuta en un dispositivo HoloLens. |
| [Códigos QR](unreal-qr-codes.md) | Represente códigos QR como hologramas mediante un sistema de coordenadas en la posición del mundo real de cada código. |
| [WinRT](unreal-winrt.md) | Cree un archivo binario independiente con código de WinRT que el sistema de compilación de Unreal pueda usar. |

### <a name="4-streaming-and-deploying-to-a-device"></a>4. Streaming e implementación en un dispositivo

Si quiere probar la aplicación en un dispositivo HoloLens mientras esta sigue en desarrollo, puede [hacer streaming de ella directamente desde su PC](unreal-streaming.md) mediante el editor de Unreal o el archivo ejecutable de Windows empaquetado.

Si esta es la primera vez que implementa una aplicación de Unreal para HoloLens 2, deberá [descargar los archivos auxiliares](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) desde el iniciador de Epic. Una vez que haya instalado los archivos, estará listo para realizar la implementación desde el [editor de Unreal](unreal-deploying.md) o el [Portal de dispositivos](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Adición de servicios

En este momento del recorrido de desarrollo, es posible que quiera agregar servicios u obtener ayuda con la implementación comercial. La integración de las características de [Azure Cloud Services](../mixed-reality-cloud-services.md) y Dynamics 365 pueden mejorar sus los proyectos de una manera significativa. Hemos recopilado algunos puntos de partida para que pueda explorar y ampliar su conocimiento de realidad mixta.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="debugging"></a>Depuración

Si está pensando en la posibilidad de depurar la aplicación mientras se ejecuta en el dispositivo con Visual Studio, siga estas [instrucciones](/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Rendimiento

El desarrollo para la realidad mixta incluye puntos de control de rendimiento que dependen de la plataforma. Una aplicación de HoloLens 2 debe ejecutarse a 60 fotogramas por segundo para que los hologramas presenten estabilidad y capacidad de respuesta. Afortunadamente, tenemos [recomendaciones](performance-recommendations-for-unreal.md) para actualizar el rendimiento en las aplicaciones de Unreal.

## <a name="supported-features"></a>Funciones admitidas

| Característica de HoloLens 2 | Versión anterior de Unreal Engine admitida | Compatible con OpenXR (4.26) |
| ----------- | ----------- | ----------- |
| Compatibilidad con ARM64 | 4.23 | ✔️ |
| Streaming desde un equipo | 4.23 | ✔️ |
| Asignación espacial | 4.23 | ✔️ |
| Seguimiento de manos y articulaciones | 4.23 | ✔️ |
| Seguimiento de los ojos | 4.23 | ✔️ |
| Entrada de voz | 4.23 | ✔️ |
| Delimitadores espaciales | 4.23 | ✔️ |
| Acceso a la cámara | 4.23 |
| Códigos QR | 4.23 | ✔️ |
| Audio espacial | 4.23 | ✔️ |
| Compatibilidad con la pantalla de espectador para streaming | 4.24 |
| LSR plana por streaming | 4.24 |
| [Aplicaciones de ejemplo](../features-and-samples.md) | 4.24 | ✔️ |
| Modo multivista móvil: resultados de rendimiento de 60 fps | 4.25 | ✔️ |
| Representación de tercera cámara | 4.25 |
| Streaming desde una aplicación de escritorio empaquetada | 4.25.1 | ✔️ |
| Azure Spatial Anchors para HoloLens 2 (beta) | 4.25 |
| Compatibilidad de UX Tools de Mixed Reality | 4.25 | ✔️ |
| Tutoriales y documentación para desarrolladores | 4.25 | ✔️ |
| Teclado del sistema | 4.26 | ✔️ |
| Complemento de Media Player de HoloLens | 4.26 | ✔️ |
| Azure Spatial Anchors para iOS y Android (beta) | 4.26 |
| Complemento de Microsoft OpenXR con extensiones de OpenXR específicas del proveedor de Microsoft | 4.26 | ✔️ |
| Streaming de Azure a HoloLens 2 | 4.26 | ✔️ |
| Compatibilidad del kit para la certificación de aplicaciones en Windows para aplicaciones empaquetadas | 4.26 | ✔️ |
| Compatibilidad con el controlador de HP Reverb G2 | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [Instalación de las herramientas](../install-the-tools.md)

## <a name="see-also"></a>Consulta también
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Documentación de Unreal para streaming e implementación en el emulador y el dispositivo</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Instrucciones de rendimiento de Unreal para dispositivos móviles</a>