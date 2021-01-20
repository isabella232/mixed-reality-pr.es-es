---
title: Desarrollo de Unity para HoloLens
description: Empiece a compilar aplicaciones de realidad mixta en Unity y HoloLens con nuestro recorrido de puntos de control seleccionados.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, mixed reality, development, getting started, new project, porting, capability, camera, simulation, emulation, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset, what is virtual reality, what is augmented reality, MRTK, mixed reality toolkit, spatial mapping, voice input, locatable camera, emulator, Azure, tutorials
ms.openlocfilehash: c5b7683574378565c71e95bc6205be3dbf92fcaf
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226444"
---
# <a name="unity-development-for-hololens"></a>Desarrollo de Unity para HoloLens

![Logotipo del banner de Unity](../images/unity_logo_banner.png)

La forma más rápida de compilar una [aplicación de realidad mixta](../../design/app-views.md) de HoloLens en [Unity](https://unity.com) es mediante el kit de herramientas de Mixed Reality. Si no está familiarizado con Unity, le recomendamos que explore los [tutoriales](https://unity3d.com/learn/tutorials) de nivel principiante en la plataforma de aprendizaje de Unity antes de continuar. También puede resultarle útil visitar la exhaustiva tienda [Asset Store](https://www.assetstore.unity3d.com/) y los [foros de realidad mixta de Unity](https://forum.unity3d.com/forums/hololens.102/) a fin de interactuar con la comunidad en línea que crea aplicaciones de realidad mixta. Nunca se sabe qué recursos o soluciones interesantes pueden encontrarse allí. Cuando esté listo para empezar a usar MRTK, diríjase a los puntos de control de desarrollo siguientes.

> [!IMPORTANT]
> Eche un vistazo a nuestras **[guías de migración](../porting-apps/porting-overview.md)** si tiene un proyecto de Unity existente que quiere llevar a HoloLens 2. Tenemos guías para los proyectos que usan HTK, MRTK V1 o SteamVR.

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta. Si aún no ha explorado la [aplicación de ejemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), le recomendamos que la descargue y la use para familiarizarse con los aspectos básicos de la experiencia de usuario de realidad mixta.

### <a name="1-getting-started"></a>1. Introducción

La forma más fácil de desarrollar aplicaciones en Unity es con Mixed Reality Toolkit. MRTK le permitirá definir automáticamente la configuración de un proyecto de realidad mixta y le proporcionará un conjunto de características para acelerar el proceso de desarrollo. Al final de esta sección, habrá adquirido conocimientos básicos sobre Mixed Reality Toolkit, un entorno de desarrollo configurado correctamente para aplicaciones de realidad mixta y un proyecto de MRTK de trabajo en Unity que ha creado usted mismo.

|  Punto de control  |  Resultado  |
| --- | --- |
| [¿Qué es MRTK?](mrtk-getting-started.md) | Comience su recorrido y familiarícese con Mixed Reality Toolkit y lo que puede ofrecerle. |
| [Instale las actualizaciones más recientes.](../install-the-tools.md) | Descargue e instale el paquete de Unity más reciente y configure el proyecto para la realidad mixta. |
| [Serie de tutoriales de HoloLens 2](tutorials/mr-learning-base-01.md) | Profundice en los tutoriales de MRTK de nivel principiante para el hardware de HoloLens 2. |

> [!IMPORTANT]
> Si quieres crear un nuevo proyecto de Unity sin importar Mixed Reality Toolkit, hay un pequeño conjunto de opciones de configuración de Unity que debes cambiar manualmente para Windows Mixed Reality. Se dividen en dos categorías: por proyecto y por escena. Eche un vistazo a nuestra [guía de configuración](configure-unity-project.md) para ver el proceso paso a paso.

> [!NOTE]
> Una vez que haya configurado MRTK V2 en el proyecto, los objetos de juego de Unity estándar, como la cámara, se activarán inmediatamente para ofrecerle una experiencia sentado. Puede encontrar instrucciones sobre cómo cambiar la escala de la experiencia de la aplicación en la página de [sistemas de coordenadas](coordinate-systems-in-unity.md).

### <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Todos los bloques de creación básicos para las aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity. Estos bloques de creación están disponibles como características independientes y a través de Mixed Reality Toolkit. Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio. Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en un proyecto de realidad mixta de forma independiente o a través de MRTK.

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-advanced-features"></a>3. Características avanzadas

Hay otras características clave que desempeñan un rol en las aplicaciones de realidad mixta disponibles a través de las API de Unity sin que se requiera ningún paquete o instalación adicional. Estas características se pueden agregar a proyectos de Unity tanto si se instala MRTK como si no. Después de profundizar en las funcionalidades más avanzadas que ofrece Unity, podrá crear aplicaciones de realidad mixta más completas y complejas.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Experiencias compartidas](shared-experiences-in-unity.md) | Permite ver e interactuar de forma colectiva con el mismo holograma en un punto fijo en el espacio mediante el uso compartido del anclaje espacial. |
| [Cámara localizable](locatable-camera-in-unity.md) | Permite capturar fotos y contenido de vídeo en su aplicación de realidad mixta. |
| [Punto de enfoque](focus-point-in-unity.md) | Permite proporcionar a HoloLens una sugerencia sobre cómo mejorar la estabilización en los hologramas que se muestran actualmente. |
| [Pérdida de seguimiento](tracking-loss-in-unity.md) | Permite controlar los escenarios en los que el dispositivo no se encuentra en el espacio del mundo de las aplicaciones |
| [Entrada de teclado](keyboard-input-in-unity.md) | Permite obtener información sobre los teclados del mundo real y de la realidad mixta en sus aplicaciones. |

### <a name="4-deploying-to-a-device-or-emulator"></a>4. Implementación en un dispositivo o emulador

Una vez que tengas el proyecto holográfico de Unity listo para las pruebas, el paso siguiente consiste en exportar y compilar una solución de Visual Studio de Unity. Teniendo en cuenta esa solución de VS, puede ejecutar su aplicación en una de estas tres formas en un dispositivo real o simulado. Al final de esta sección, podrá implementar la aplicación en el dispositivo o el emulador que mejor se adapte a sus necesidades de desarrollo.

* [Casco envolvente de HoloLens o Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulador del casco envolvente de Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a>5. Adición de servicios

En este momento del recorrido de desarrollo, es posible que quiera agregar servicios o obtener ayuda con la implementación comercial. La integración de las características de [Azure Cloud Services](../mixed-reality-cloud-services.md) y Dynamics 365 pueden mejorar sus los proyectos de una manera significativa. Hemos recopilado algunos puntos de partida para que pueda explorar y ampliar su conocimiento de realidad mixta.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

También disponemos de una [lista completa de documentación de soporte técnico para los servicios de Azure adicionales](../mixed-reality-cloud-services.md#standalone-unity-services) que puede agregar a los proyectos de Unity de manera automática.

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="porting"></a>Migración

Si tiene aplicaciones que quiere migrar, consulte los artículos que se enumeran a continuación:

* [De HoloToolkit/MRTK a MRTK v2](mrtk-porting-guide.md)
* [Guía de portabilidad para aplicaciones envolventes](../porting-apps/porting-guides.md)
* [Guía de migración de entrada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Tutoriales

Si está pensando en agregar características específicas de realidad mixta a sus aplicaciones, hemos seleccionado varios tutoriales que pueden guiarle a lo largo de todo el proceso. El contenido de HoloLens 2 y HoloLens (1.ª generación) más popular se muestra a continuación, pero puede encontrar toda la colección si visita la información general de los tutoriales.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Recursos adicionales

Antes de que se sumerja en el mundo de la realidad mixta por su cuenta, le recomendamos que eche un vistazo a la documentación relacionada con MRTK que se indica a continuación. Estos artículos son excelentes puntos de partida para comprender cómo funciona MRTK con mayor detalle y le proporcionarán información sobre cómo aumentar el rendimiento de su aplicación.

|  Tema  |  Descripción  |
| --- | --- |
| [Introducción a la arquitectura de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | Conozca mejor cómo funciona el SDK de MRTK en sus proyectos. |
| [Configuración y rendimiento](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | Genere perfiles de la aplicación, actualice la configuración de Unity y obtenga el mejor rendimiento de estabilización de hologramas disponible. |
| [Introducción a MRTK y XR](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | Realice la transferencia a la canalización de XR alternativa que proporciona Unity. |

### <a name="unity-resources"></a>Recursos de Unity

Además de esta documentación disponible en docs.microsoft.com, Unity instala la documentación de la funcionalidad de Windows Mixed Reality junto con Unity Editor. La documentación proporcionada por Unity incluye dos secciones independientes.

|  Resource  |  Descripción  |
| --- | --- |
| [Referencia de scripting](https://docs.unity3d.com/ScriptReference/) | Esta sección de la documentación contiene detalles de la API de scripting que Unity proporciona y es accesible en línea desde el editor de Unity si hace clic en **Ayuda > Referencia de scripting**. |
| [Manual](https://docs.unity3d.com/Manual/index.html) | Este manual se ha diseñado para ayudarle a aprender a usar Unity, desde las técnicas básicas a las avanzadas, y es accesible en línea o desde el editor de Unity haciendo clic en **Ayuda > Manual**. |

> [!div class="nextstepaction"]
> [Explorar MRTK](mrtk-getting-started.md)

## <a name="have-feedback"></a>¿Quiere hacer algún comentario?

Puede encontrarnos en los [foros de Unity](https://aka.ms/unityforums). Para ello, etiquete a **Microsoft** y use una combinación de las siguientes etiquetas para ayudarnos a comprender de qué complemento está proporcionando comentarios:

* HoloLens 2 
* Windows Mixed Reality
* OpenXR
* XRSDK
* XR heredado 

## <a name="see-also"></a>Consulta también

* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR Basics 100: introducción a Unity](tutorials/holograms-100.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Uso del espacio de nombres de Windows con las aplicaciones de Unity para HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Modo de reproducción de Unity](unity-play-mode.md)
* [Guías de migración](../porting-apps/porting-guides.md)
