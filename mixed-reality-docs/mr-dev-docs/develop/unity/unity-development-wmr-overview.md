---
title: Desarrollo de Unity para VR
description: Introducción a la compilación de aplicaciones de realidad mixta en Unity para VR y cascos envolventes de Windows Mixed Reality.
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, realidad mixta, mixed reality, desarrollo, introducción, nuevo proyecto, portabilidad, funcionalidad, cámara, simulación, emulación, documentación, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, qué es la realidad virtual, qué es la realidad aumentada, MRTK, kit de herramientas de realidad mixta, entrada de voz, cámara localizable, emulador, Azure, tutoriales
ms.openlocfilehash: 074f42fd077d888523c2cf0a7da5bcafcfadb0f0
ms.sourcegitcommit: 72970dbe6674e28c250f741e50a44a238bb162d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112906971"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>Desarrollo de Unity para VR y Windows Mixed Reality

![Logotipo del banner de Unity](../images/unity_logo_banner.png)

Si no está familiarizado con Unity, le recomendamos que explore los [tutoriales](https://unity3d.com/learn/tutorials) de nivel principiante en la plataforma de aprendizaje de Unity antes de continuar. También puede resultarle útil visitar los [foros de Mixed Reality de Unity](https://forum.unity3d.com/forums/hololens.102/) a fin de interactuar con la comunidad en línea que compila aplicaciones de realidad mixta. Nunca se sabe qué recursos o soluciones interesantes pueden encontrarse allí. Cuando esté listo para empezar a usar MRTK, diríjase a los puntos de control de desarrollo siguientes.

> [!IMPORTANT]
> Eche un vistazo a nuestras **[guías de migración](../porting-apps/porting-overview.md)** si tiene un proyecto de Unity existente que quiere llevar a un casco envolvente de Windows Mixed Reality. 

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

Hay un pequeño conjunto de opciones de configuración de Unity que debe cambiar manualmente para el desarrollo de Windows Mixed Reality y VR. Se dividen en dos categorías: por proyecto y por escena. Al final de esta sección, tendrá las herramientas y la configuración del proyecto para empezar a crear sus propias aplicaciones.

|  Punto de control  |  Resultado  |
| --- | --- |
| [Instale las actualizaciones más recientes.](../install-the-tools.md) | Descargue e instale el paquete de Unity más reciente y configure el proyecto para la realidad mixta. |
| [Configuración de un proyecto para VR y cascos de Windows Mixed Reality](./xr-project-setup.md?tabs=openxr) | Obtenga información sobre cómo compilar aplicaciones que representen contenido digital en dispositivos de pantalla holográfica y VR. |

> [!IMPORTANT]
> Consulte nuestra [guía de configuración](choosing-unity-version.md) de proyectos de Unity para obtener más información sobre cómo configurar los proyectos.

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Después de iniciar un nuevo proyecto envolvente, necesitará algunos bloques de creación básicos para desarrollar aplicaciones envolventes. Todos los bloques de creación básicos para las aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity. Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio. Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en un proyecto de VR.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Cámara](../unity/camera-in-unity.md) | Permite optimizar totalmente la calidad visual y la estabilidad del holograma en las aplicaciones de realidad mixta. |
| [Anclajes espaciales y de bloqueo del mundo](spatial-anchors-in-unity.md) | Permite resolver problemas de estabilización, de ajuste de la cámara, e integrar una solución estable del sistema de coordenadas. || [Controladores de movimiento](../unity/motion-controllers-in-unity.md) | Permite agregar acciones espaciales a las aplicaciones de Mixed Reality. |
| [Gestos](../unity/gestures-in-unity.md) | Uso de gestos con la mano como entrada en las experiencias de Mixed Reality |
| [Sonido espacial](../unity/spatial-sound-in-unity.md) | Permite mejorar sus aplicaciones mediante el audio 3D envolvente. |
| [Texto](../unity/text-in-unity.md) | Permite obtener texto nítido y de alta calidad con un tamaño y una representación de calidad que se pueden administrar. |
| [Entrada de voz](../unity/voice-input-in-unity.md) | Permite capturar palabras clave, frases y dictado en voz alta de los usuarios.|

### <a name="3-advanced-features"></a>3. Características avanzadas

Hay otras características clave que desempeñan un rol en las aplicaciones envolventes disponibles a través de las API de Unity sin que se requiera ningún paquete o instalación adicional. Después de profundizar en las funcionalidades más avanzadas que ofrece Unity, podrá crear aplicaciones de VR más completas y complejas.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Pérdida de seguimiento](tracking-loss-in-unity.md) | Permite controlar los escenarios en los que el dispositivo no se encuentra en el espacio del mundo de las aplicaciones |
| [Entrada de teclado](keyboard-input-in-unity.md) | Permite obtener información sobre los teclados del mundo real y de la realidad mixta en sus aplicaciones. |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Implementación en un dispositivo o emulador

Una vez que tengas el proyecto holográfico de Unity listo para las pruebas, el paso siguiente consiste en exportar y compilar una solución de Visual Studio de Unity. Teniendo en cuenta esa solución de VS, puede ejecutar su aplicación en dispositivos reales o simulados. Al final de esta sección, podrá implementar la aplicación en un dispositivo o emulador que se adapte a sus necesidades de desarrollo.

* [Casco envolvente de Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Simulador del casco envolvente de Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="porting"></a>Migración

Si tiene aplicaciones que quiere migrar, consulte los artículos que se enumeran a continuación:

* [Portabilidad de aplicaciones de VR a Windows Mixed Reality](../porting-apps/porting-guides.md?tabs=project)
* [Actualización de aplicaciones de SteamVR para Windows Mixed Reality](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>Recursos adicionales

Antes de que se sumerja en el mundo de la realidad mixta por su cuenta, le recomendamos que eche un vistazo a la documentación adicional que se indica a continuación. 

* [Guía para entusiastas de la realidad virtual](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Almacén de recursos de Unity](https://assetstore.unity.com)

## <a name="see-also"></a>Consulte también 

* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)