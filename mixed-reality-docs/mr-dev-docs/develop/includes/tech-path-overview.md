---
ms.openlocfilehash: 514062ea4b0343eae6d4e0b05097b4c65ca3de22
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2020
ms.locfileid: "91989748"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

Crea una aplicación de realidad mixta completa y multiplataforma con Unity. Consulte [Introducción al desarrollo de Unity](../unity/unity-development-overview.md) para empezar a desarrollar con Unity para los cascos envolventes HoloLens o Windows Mixed Reality.

## <a name="what-does-unity-offer"></a>¿Qué ofrece Unity?

Unity es una de las principales plataformas de desarrollo en tiempo real que se encuentra en el mercado y cuenta con un ecosistema con una [plataforma de aprendizaje](https://unity.com/products/learn-premium) dedicada, un [almacén de recursos](https://assetstore.unity.com/), [documentación completa](https://docs.unity3d.com/Manual/index.html) y una próspera comunidad. El código en tiempo de ejecución subyacente de Unity está escrito en C++, pero todo el script de desarrollo se realiza en C#. Tanto si desea crear juegos, películas y animaciones cinematográficas, como representar conceptos arquitectónicos o de ingeniería en un mundo virtual, Unity tiene la infraestructura necesaria para ayudarle.

## <a name="available-hardware-platforms"></a>Plataformas de hardware disponibles

Al compilar aplicaciones de realidad mixta con Unity, cuenta con varias opciones de hardware y de emulador. Si bien nuestra documentación para desarrolladores se centra en los dispositivos HoloLens, encontrará secciones de compatibilidad de dispositivos con detalles sobre la implementación de cascos envolventes cuando proceda.

**Dispositivos de realidad aumentada**
* [HoloLens (1.ª generación)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Cascos envolventes de VR**
* Reverb y Reverb G2 de HP
* Odyssey y Odyssey+ de Samsung
* Casco de Windows Mixed Reality de HP
* Explorer de Lenovo
* AH101 de Acer
* Visor de Dell
* HC102 de Asus
* OJO 500 de Acer

## <a name="available-tools-and-sdks"></a>Herramientas y SDK disponibles

|  Herramienta/SDK  |  Descripción  |
| --- | --- |
| [Mixed Reality Toolkit para Unity](../unity/mrtk-getting-started.md) | Mixed Reality Toolkit para Unity es un kit de desarrollo multiplataforma de código abierto para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. |

## <a name="cloud-services"></a>Servicios en la nube

Hay varios servicios en la nube que se pueden integrar en proyectos de realidad mixta creados en Unity, específicamente **Azure Remote Rendering** y **Azure Spatial Anchors**. Estos servicios pueden agregar contenido holográfico compartido y una representación 3D en tiempo real a las aplicaciones, lo que hace que sean más atractivas y envolventes para los usuarios.

Todos estos servicios se tratarán en el curso del [recorrido de desarrollo de Unity](../unity/unity-development-overview.md), que es la **guía que se recomienda seguir para aprender a usar Mixed Reality con Unity**. Dado que ya empezó dicho recorrido, simplemente siga leyendo y haga clic en el botón azul grande que hay en la parte inferior del artículo. Sin embargo, si se encuentra en una fase de desarrollo más avanzada y ya sabe que quiere profundizar en ello, consulte la [información general de Cloud Services](../mixed-reality-cloud-services.md) o vaya directamente a los [recursos de servicios](../unity/unity-development-overview.md#5-adding-services).

## <a name="dynamics-365-guides"></a>Dynamics 365 Guides

Puede usar **Microsoft Dynamics 365 Guides** para vincular visualmente las instrucciones holográficas al entorno virtual de las aplicaciones, lo que proporciona a los usuarios información importante cuando y donde convenga. Esta característica también se trata en el recorrido de desarrollo de Unity, pero si quiere avanzar y ver lo que se ofrece, seleccione la pestaña **Dynamics 365** [aquí](../unity/unity-development-overview.md#5-adding-services).

## <a name="examples"></a>Ejemplos

Tenemos varias [aplicaciones de ejemplo](../unity/samples.md) de código abierto que puede descargar y probar para hacerse una idea de un producto final de realidad mixta en Unity. También hay disponibles escenas de ejemplo de MRTK para probar características específicas:
* [Escena de ejemplos de interacción de la mano (MRTK) para Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#open-and-run-the-handinteractionexamples-scene-in-editor): La escena de ejemplo HandInteractionExamples.unity contiene varios tipos de interacciones y controles de interfaz de usuario que resaltan la entrada de mano articulada.

* [Ejemplos de seguimiento de los ojos (MRTK) para Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_ExamplesOverview.html): En esta página se explica cómo empezar a trabajar rápidamente con el seguimiento de los ojos en MRTK mediante la creación que toma como base nuestros ejemplos de seguimiento de los ojos de MRTK proporcionados.

>[!NOTE]
>Las dos escenas de ejemplo de MRTK requieren la instalación de los paquetes MRTK Foundation y Example Unity.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

Cree una aplicación de realidad mixta completa y multiplataforma con Unreal. Consulte [Introducción al desarrollo con Unreal](../unreal/unreal-development-overview.md) para empezar a desarrollar con Unreal para HoloLens.

## <a name="what-does-unreal-offer"></a>¿Qué ofrece Unreal?

Unreal Engine 4 es un potente motor de creación de código abierto con compatibilidad total con la realidad mixta en C++ y Blueprints. A partir de Unreal Engine 4.25, la compatibilidad con HoloLens es completa y está lista para la producción.

## <a name="available-hardware-platforms"></a>Plataformas de hardware disponibles

Al compilar aplicaciones de realidad mixta con Unreal Engine, cuenta con varias opciones de hardware, de emulador y de streaming. Si bien nuestra documentación para desarrolladores se centra en los dispositivos HoloLens, puede empaquetar los proyectos de Unreal como aplicaciones de escritorio x64 y ejecutarlas en cascos envolventes sin problemas.

**Dispositivos de realidad aumentada**
* [HoloLens (1.ª generación)](https://docs.microsoft.com/hololens/hololens1-hardware)
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Cascos envolventes de VR**
* Reverb y Reverb G2 de HP
* Odyssey y Odyssey+ de Samsung
* Casco de Windows Mixed Reality de HP
* Explorer de Lenovo
* AH101 de Acer
* Visor de Dell
* HC102 de Asus
* OJO 500 de Acer

## <a name="available-tools-and-sdks"></a>Herramientas y SDK disponibles

|  Herramienta/SDK  |  Descripción  |
| --- | --- |
| [Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) | Mixed Reality Toolkit para Unreal (MRTK-Unreal) es un conjunto de componentes, en forma de complementos, muestras y documentación, diseñado para acelerar el desarrollo de aplicaciones de realidad mixta con Unreal Engine. |

## <a name="cloud-services"></a>Servicios en la nube

Al compilar aplicaciones de realidad mixta en Unreal, tiene acceso a un eficaz servicio en la nube llamado **Azure Spatial Anchors**, que puede usar para agregar, conservar y compartir contenido holográfico en distintos dispositivos. 

Azure Spatial Anchors, se tratará en el curso del [recorrido de desarrollo de Unity](../unreal/unreal-development-overview.md), que es la **guía que se recomienda seguir para aprender a usar Mixed Reality con Unity**. Dado que ya empezó dicho recorrido, simplemente siga leyendo y haga clic en el botón azul grande que hay en la parte inferior del artículo. Sin embargo, si se encuentra en una fase de desarrollo más avanzada y ya sabe que quiere profundizar en ello, consulte la [información general de Cloud Services](../mixed-reality-cloud-services.md) o vaya directamente a los [recursos de servicios](../unreal/unreal-development-overview.md#5-adding-services).

## <a name="dynamics-365-guides"></a>Dynamics 365 Guides

Puede usar **Microsoft Dynamics 365 Guides** para vincular visualmente las instrucciones holográficas al entorno virtual de las aplicaciones, lo que proporciona a los usuarios información importante cuando y donde convenga. Esta característica también se trata en el recorrido de desarrollo de Unreal, pero si quiere avanzar y ver lo que se ofrece, seleccione la pestaña **Dynamics 365** [aquí](../unreal/unreal-development-overview.md#5-adding-services).

## <a name="examples"></a>Ejemplos

* [Kippy's Escape](../unreal/unreal-kippys-escape.md) es una aplicación de ejemplo de HoloLens 2 de código abierto compilada con Unreal Engine 4 y Mixed Reality UX Tools for Unreal. El juego presenta las características exclusivas del hardware de HoloLens 2 y la eficacia de desarrollo de Mixed Reality UX Tools.


# <a name="javascript"></a>[JavaScript](#tab/web)

![Web](../images/javascript_logo_banner.png)

La API de dispositivo WebXR es una especificación abierta que permite experimentar con aplicaciones de realidad mixta en un explorador en cualquier plataforma. Consulte [Información general sobre el desarrollo con JavaScript](../web/javascript-development-overview.md) para empezar a crear aplicaciones de realidad mixta para cualquier plataforma.


# <a name="native-openxr"></a>[Nativo (OpenXR)](#tab/native)

 ![Nativo](../images/native_logo_banner.png)

Cree aplicaciones de realidad mixta mediante una línea directa a las API de Windows Mixed Reality. Consulte [Introducción al desarrollo nativo](../native/directx-development-overview.md) para empezar a desarrollar aplicaciones nativas con OpenXR o WinRT heredado para los cascos envolventes HoloLens 2 o de Windows Mixed Reality. La API de Windows Mixed Reality es compatible con las aplicaciones escritas en C++ y C#, lo que le permite crear su propio marco o middleware en cualquier lenguaje.

## <a name="what-does-openxr-offer"></a>¿Qué ofrece OpenXR?

OpenXR es un estándar de API abierto libre de regalías de Khronos que proporciona a los motores acceso nativo a una amplia gama de dispositivos de proveedores del espectro de realidad mixta. Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio. Si no tiene acceso a un casco, hay disponibles emuladores de los cascos HoloLens 2 y de Windows Mixed Reality.

## <a name="available-hardware-platforms"></a>Plataformas de hardware disponibles

Al compilar aplicaciones de realidad mixta con OpenXR, cuenta con varias opciones de hardware, de emulador y de streaming. 

**Dispositivos de realidad aumentada**
* [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)

**Cascos envolventes de VR**
* Reverb y Reverb G2 de HP
* Odyssey y Odyssey+ de Samsung
* Casco de Windows Mixed Reality de HP
* Explorer de Lenovo
* AH101 de Acer
* Visor de Dell
* HC102 de Asus
* OJO 500 de Acer

## <a name="available-tools-and-sdks"></a>Herramientas y SDK disponibles

|  Herramienta/SDK  |  Descripción  |
| --- | --- |
| [Herramientas de desarrollo de OpenXR](../native/openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-tools) | Proporciona una escena de demostración que prueba varias características de OpenXR, junto con una página de estado del sistema que proporciona información clave sobre el tiempo de ejecución activo y el casco actual. |
| [Especificación de OpenXR](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html) |  Describe qué es OpenXR, qué funcionalidades y características ofrece, y cómo implementarlo en sus propios proyectos. |
| [Cargador de OpenXR](../native/openxr-getting-started.md#integrate-the-openxr-loader-into-a-project) | Detecta el tiempo de ejecución de OpenXR activo en el dispositivo y proporciona acceso a las funciones básicas y a las funciones de extensión que implementa. |

## <a name="examples"></a>Ejemplos

No dude en experimentar con la aplicación de ejemplo para hacerse una idea de lo que es posible con el desarrollo nativo y la realidad mixta.

<!-- Go to actual GH link for more samples -->
* [BasicXrApp](https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp): Demuestra un ejemplo de OpenXR simple con dos archivos de proyecto de Visual Studio, uno para una aplicación de escritorio de Win32 y otro para una aplicación para UWP de HoloLens 2.
