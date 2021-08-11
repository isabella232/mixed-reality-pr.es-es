---
title: Desarrollo de Unity para HoloLens
description: Empiece a compilar aplicaciones de realidad mixta en Unity y HoloLens con nuestro recorrido de puntos de control seleccionados.
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, mixed reality, development, getting started, new project, porting, capability, camera, simulation, emulation, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset, what is virtual reality, what is augmented reality, MRTK, mixed reality toolkit, spatial mapping, voice input, locatable camera, emulator, Azure, tutorials
ms.openlocfilehash: f47e37f56f203590a16ec804c4a36a6ac601ec61cb2f3b7dfb69987d411eef15
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202873"
---
# <a name="unity-development-for-hololens"></a>Desarrollo de Unity para HoloLens

![Logotipo del banner de Unity](../images/unity_logo_banner.png)

Unity es una de las plataformas de desarrollo en tiempo real líderes en el mercado, con un código en tiempo de ejecución subyacente escrito en C++ y todo el scripting de desarrollo en C#. Tanto si desea crear juegos, películas y animaciones cinematográficas, como representar conceptos arquitectónicos o de ingeniería en un mundo virtual, Unity tiene la infraestructura necesaria para ayudarle. Cuando esté listo para empezar, diríjase a los puntos de control de desarrollo siguientes.

> [!IMPORTANT]
> Eche un vistazo a nuestras **[guías de migración](../porting-apps/porting-overview.md)** si tiene un proyecto de Unity existente que quiere llevar a HoloLens 2. Tenemos guías para los proyectos que usan HTK, MRTK V1 o SteamVR.

## <a name="development-checkpoints"></a>Puntos de control de desarrollo

Use los siguientes puntos de control para incorporar sus aplicaciones y juegos de Unity en el mundo de la realidad mixta. Si aún no ha explorado la [aplicación de ejemplo Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), le recomendamos que la descargue y la use para familiarizarse con los aspectos básicos de la experiencia de usuario de realidad mixta.

## <a name="1-getting-started"></a>1. Introducción

La forma más fácil de desarrollar aplicaciones en Unity es con Mixed Reality Toolkit. MRTK le permitirá definir automáticamente la configuración de un proyecto de realidad mixta y le proporcionará un conjunto de características para acelerar el proceso de desarrollo. Al final de esta sección, habrá adquirido conocimientos básicos sobre Mixed Reality Toolkit, un entorno de desarrollo configurado correctamente para aplicaciones de realidad mixta y un proyecto de MRTK de trabajo en Unity que ha creado usted mismo.

|  Punto de control  |  Resultado  |
| --- | --- |
| [Introducción a Mixed Reality Toolkit](mrtk-getting-started.md) | Comience su recorrido y familiarícese con Mixed Reality Toolkit y lo que puede ofrecerle. |
| [Descargar la herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md) | Una nueva herramienta de desarrollo para detectar, actualizar y agregar paquetes de características de Mixed Reality a los proyectos de Unity |
| [Configurar el entorno de desarrollo](../install-the-tools.md) | Descargue e instale el paquete de Unity más reciente y configure el proyecto para la realidad mixta. |
| [Completar la serie de tutoriales de HoloLens 2](tutorials/mr-learning-base-01.md) | Profundice en los tutoriales de MRTK de nivel principiante para el hardware de HoloLens 2. |

> [!IMPORTANT]
> Si quieres crear un nuevo proyecto de Unity sin importar Mixed Reality Toolkit, hay un pequeño conjunto de opciones de configuración de Unity que debes cambiar manualmente para Windows Mixed Reality. Eche un vistazo a la [guía de configuración](choosing-unity-version.md) para obtener más información.

> [!NOTE]
> Una vez que haya configurado MRTK en el proyecto, los objetos de juego de Unity estándar, como la cámara, se activarán inmediatamente para ofrecerle una experiencia sentado. Puede encontrar instrucciones sobre cómo cambiar la escala de la experiencia de la aplicación en la página de [sistemas de coordenadas](coordinate-systems-in-unity.md).

## <a name="2-core-building-blocks"></a>2. Bloques de creación principales

Todos los bloques de creación básicos para las aplicaciones de realidad mixta se exponen de forma coherente con otras API de Unity. Estos bloques de creación están disponibles como características independientes y a través de Mixed Reality Toolkit. Es posible que no los necesite todos a la vez, pero le recomendamos que los explore desde el principio. Después de profundizar en los principales bloques de creación que se enumeran a continuación, contará con herramientas que ofrecen muchas características y que puede integrar en un proyecto de realidad mixta de forma independiente o a través de MRTK.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Cámara](../unity/camera-in-unity.md) | Permite optimizar totalmente la calidad visual y la estabilidad del holograma en las aplicaciones de realidad mixta. |
| [Anclajes espaciales y de bloqueo del mundo](spatial-anchors-in-unity.md) | Permite resolver problemas de estabilización, de ajuste de la cámara, e integrar una solución estable del sistema de coordenadas. |
| [Experiencias compartidas](shared-experiences-in-unity.md) | Permite ver e interactuar de forma colectiva con el mismo holograma en un punto fijo en el espacio mediante el uso compartido del anclaje espacial. |
| [Gaze](../unity/gaze-in-unity.md) | Permite que los usuarios se dirijan a los hologramas mediante su mirada. |
| [Controladores de movimiento](../unity/motion-controllers-in-unity.md) | Permite agregar acciones espaciales a las aplicaciones de Mixed Reality. |
| [Gestos](../unity/gestures-in-unity.md) | Uso de gestos con la mano como entrada en las experiencias de Mixed Reality |
| [Seguimiento de manos y ocular](../unity/hand-eye-in-unity.md) | Permite integrar la entrada del seguimiento ocular y de manos articuladas en la experiencia del usuario. |
| [Asignación espacial](../unity/spatial-mapping-in-unity.md) | Permite asignar su espacio físico con una superposición de malla virtual para marcar los límites de su entorno. |
| [Sonido espacial](../unity/spatial-sound-in-unity.md) | Permite mejorar sus aplicaciones mediante el audio 3D envolvente. |
| [Texto](../unity/text-in-unity.md) | Permite obtener texto nítido y de alta calidad con un tamaño y una representación de calidad que se pueden administrar. |
| [Entrada de voz](../unity/voice-input-in-unity.md) | Permite capturar palabras clave, frases y dictado en voz alta de los usuarios.|

## <a name="3-advanced-features"></a>3. Características avanzadas

Hay otras características clave que desempeñan un rol en las aplicaciones de realidad mixta disponibles a través de las API de Unity sin que se requiera ningún paquete o instalación adicional. Estas características se pueden agregar a proyectos de Unity tanto si se instala MRTK como si no. Después de profundizar en las funcionalidades más avanzadas que ofrece Unity, podrá crear aplicaciones de realidad mixta más completas y complejas.

|  Característica  |  Funcionalidades  |
| --- | --- |
| [Cámara de fotos y vídeo](locatable-camera-in-unity.md) | Permite capturar fotos y contenido de vídeo en su aplicación de realidad mixta. |
| [Punto de enfoque](focus-point-in-unity.md) | Permite proporcionar a HoloLens una sugerencia sobre cómo mejorar la estabilización en los hologramas que se muestran actualmente. |
| [Pérdida de seguimiento](tracking-loss-in-unity.md) | Permite controlar los escenarios en los que el dispositivo no se encuentra en el espacio del mundo de las aplicaciones |
| [Entrada de teclado](keyboard-input-in-unity.md) | Permite obtener información sobre los teclados del mundo real y de la realidad mixta en sus aplicaciones. |

## <a name="4-deploying-to-a-device-or-emulator"></a>4. Implementación en un dispositivo o emulador

Una vez que tengas el proyecto holográfico de Unity listo para las pruebas, el paso siguiente consiste en exportar y compilar una solución de Visual Studio de Unity. Teniendo en cuenta esa solución de VS, puede ejecutar su aplicación en una de estas tres formas en un dispositivo real o simulado. Al final de esta sección, podrá implementar la aplicación en el dispositivo o el emulador que mejor se adapte a sus necesidades de desarrollo.

* [Casco envolvente de HoloLens o Windows Mixed Reality](../platform-capabilities-and-apis/using-visual-studio.md)
* [Emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Simulador del casco envolvente de Windows Mixed Reality](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="5-adding-services"></a>5. Adición de servicios

En este momento del recorrido de desarrollo, es posible que quiera agregar servicios o obtener ayuda con la implementación comercial. La integración de [Azure Cloud Services](../mixed-reality-cloud-services.md) puede mejorar sus proyectos de manera significativa. Hemos recopilado algunos puntos de partida para que pueda explorar y ampliar su conocimiento de realidad mixta.

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

También disponemos de una [lista completa de documentación de soporte técnico para los servicios de Azure adicionales](../mixed-reality-cloud-services.md#standalone-unity-services) que puede agregar a los proyectos de Unity de manera automática.

## <a name="6-low-code-alternatives"></a>6. Alternativas de código bajo

[!INCLUDE[](../includes/unity-low-code.md)]

## <a name="whats-next"></a>¿Qué sigue?

Nunca se realiza un trabajo de desarrollador, especialmente cuando se aprende a usar una nueva herramienta o un SDK. En las secciones siguientes se le proporcionará contenido más ampliado sobre lo que ha visto en el nivel principiante, junto con recursos útiles por si se queda bloqueado. Tenga en cuenta que estos temas y recursos no están ordenados de forma secuencial, de modo que no dude en consultar los que le interesen y explorarlos.

### <a name="porting"></a>Migración

Si tiene aplicaciones que quiere migrar, consulte los artículos que se enumeran a continuación:

* [De HoloToolkit/MRTK a MRTK v2](../porting-apps/porting-hl1-hl2.md)
* [Guía de portabilidad para aplicaciones envolventes](../porting-apps/porting-guides.md)
* [Guía de migración de entrada](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>Tutoriales

Si está pensando en agregar características específicas de realidad mixta a sus aplicaciones, hemos seleccionado varios tutoriales que pueden guiarle a lo largo de todo el proceso. El contenido de HoloLens 2 y HoloLens (1.ª generación) más popular se muestra a continuación, pero puede encontrar toda la colección si visita la información general de los tutoriales.

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>Recursos adicionales

Antes de que se sumerja en el mundo de la realidad mixta por su cuenta, le recomendamos que eche un vistazo a la documentación relacionada con MRTK que se indica a continuación. Estos artículos son excelentes puntos de partida para comprender cómo funciona MRTK con mayor detalle y le proporcionarán información sobre cómo aumentar el rendimiento de su aplicación.

|  Tema  |  Descripción  |
| --- | --- |
| [Introducción a la arquitectura de MRTK](/windows/mixed-reality/mrtk-unity/architecture/overview) | Conozca mejor cómo funciona el SDK de MRTK en sus proyectos. |
| [Configuración y rendimiento](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started) | Genere perfiles de la aplicación, actualice la configuración de Unity y obtenga el mejor rendimiento de estabilización de hologramas disponible. |
| [Introducción a MRTK y XR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk) | Realice la transferencia a la canalización de XR alternativa que proporciona Unity. |

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
