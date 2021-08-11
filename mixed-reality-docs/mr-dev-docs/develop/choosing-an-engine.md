---
title: Elección del motor
description: Introducción a las opciones de motor disponibles para el Mixed Reality desarrollo para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: 14235852f8c90e7ccc4f105f2938ce514ae2933973469db9a0e01bd03d2c1b6d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227561"
---
# <a name="choosing-your-engine"></a>Elección del motor

Hay varias rutas de desarrollo que puede seguir a través de nuestra documentación. El primer paso es encontrar la tecnología adecuada para usted. Si ya tiene una en mente, vaya directamente a la pestaña correspondiente a continuación. Si aún no se decide o recién está empezando, eche un vistazo a cada una y comprenda lo que ofrecen, las plataformas y herramientas disponibles, ¡y empiece a crear!

> [!IMPORTANT]
> Eche un vistazo a nuestra **[introducción a las guías de migración](porting-apps/porting-overview.md)** si tiene proyectos existentes que quiere llevar a HoloLens 2 o a un casco de VR envolvente, como Reverb G2. Contamos con guías para los proyectos que usan HTK, MRTK v1, SteamVR o que se desarrollaron para cascos envolventes, como Oculus Rift o HTC Vive.

## <a name="engine-overview"></a>Información general del motor

* **Unity** es una de las principales plataformas de desarrollo en tiempo real del mercado, con código en tiempo de ejecución subyacente escrito en C++ y todo el scripting de desarrollo se realiza en C#. Tanto si desea crear juegos, películas y animaciones cinematográficas, como representar conceptos arquitectónicos o de ingeniería en un mundo virtual, Unity tiene la infraestructura necesaria para ayudarle.

* **Unreal Engine 4** es un motor de creación de código abierto eficaz con compatibilidad total con la realidad mixta en C++ y blueprints. A partir de Unreal Engine 4.25, la compatibilidad con HoloLens es completa y está lista para la producción. Con funcionalidades como el sistema de scripting visual de Blueprints flexible, los diseñadores pueden usar prácticamente toda la gama de conceptos y herramientas que, por lo general, solo están disponibles para los programadores. Los creadores de distintos sectores pueden aprovechar la libertad y el control que ofrece para proporcionar contenido de vanguardia, experiencias interactivas y mundos virtuales inmersivos.

* **Los desarrolladores** nativos con experiencia en la escritura de sus propios representadores 3D pueden crear un motor personalizado mediante OpenXR. OpenXR es un estándar de API abierto libre de regalías de Khronos que proporciona a los motores acceso nativo a una amplia gama de dispositivos de proveedores del espectro de realidad mixta. Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.

* **Los desarrolladores** web que crean atractivas experiencias web ar/VR entre exploradores pueden **usar WebXR.**

    > [!NOTE]
    > **Babylon.js** para HoloLens desarrollo está actualmente en curso. Consulte las noticias [más recientes e interactúe con la comunidad.](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR)

<!-- Babylon is a Javascript-based, open source, 3D graphics engine capable of powering 3D scenes in a web browser. Babylon.js 4.2+ includes support for WebXR. With Babylon React Native, you can even build cross-platform native     applications for PC, mobile, and mixed reality devices. -->

## <a name="features-and-devices"></a>Características y dispositivos

<br>

| Logística | Unity | Unreal | JavaScript | Motor personalizado <br>(mediante OpenXR) |
|---|---|---|---|---|
| Lenguaje | C# | C++ | JavaScript | C/C++ |
| Precios | [Precios de Unity](https://store.unity.com/#plans-individual) | [Precios de Unreal](https://www.unrealengine.com/download) | Gratuito | Gratuito |

<br>

| Características del dispositivo | Unity | Unreal | JavaScript | Motor personalizado <br>(mediante OpenXR) |
|---|---|---|---|---|
| Seguimiento de dispositivos y pantallas | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrada de mano | ✔️ | ✔️ | ✔️ | ✔️ |
| Entrada de los ojos | ✔️ | ✔️ | ❌ | ✔️ |
| Entrada de voz | ✔️ | ✔️ | ✔️ | ✔️ |
| Controladores de movimiento | ✔️ | ✔️ | ✔️ | ✔️ |
| Pruebas de impacto de plano o malla | ✔️ | ✔️ | ✔️ | ✔️ |
| Descripción de escenas | ✔️ | ✔️ | ❌ | ✔️ |
| Sonido espacial | ✔️ | ✔️ | ✔️ | ✔️ |
| Detección de código QR | ✔️ | ✔️ | ❌ | ✔️ |

<br>

| Hardware | Unity | Unreal | JavaScript | Motor personalizado <br>(mediante OpenXR) |
|---|---|---|---|---|
| HoloLens 2 | ✔️ | ✔️ | ✔️ | ✔️ |
| HoloLens (1.ª generación) | ✔️ | ✔️ | ❌ | Solo WinRT (heredado) |
| [Cascos de Windows Mixed Reality](../discover/immersive-headset-hardware-details.md) | ✔️ | ✔️ | ✔️ | ✔️ |
| Cascos de SteamVR | ✔️ | ✔️ | ✔️ | ✔️ |
| Oculus:/Desastroso | ✔️ | ✔️ | ✔️ | ✔️ |
| Mobile (ARCore/ARKit) | ✔️ | ✔️ | ✔️ | ❌ |

<br>

| Herramientas | Unity | Unreal | JavaScript | Motor personalizado <br>(mediante OpenXR) |
|---|---|---|---|---|
| Mixed Reality Toolkit | ✔️ | ✔️ | ❌  | ❌ |
| World Locking Tools | ✔️ | ❌ | ❌  | ❌ |
<!-- | En malla | ❌ | ❌ | ❌ | ❌ | -->

<br>

| Servicios en la nube | Unity | Unreal | JavaScript | Motor personalizado <br>(mediante OpenXR) |
|---|---|---|---|---|
| Azure Spatial Anchors | ✔️ | ✔️ | ❌ | ✔️ |
| Azure Object Anchors | ✔️ | ❌ | ❌ | ✔️ |
| Azure Remote Rendering | ✔️ * | ❌ | ❌ | ✔️ * |

> [!NOTE]
> * Azure Remote Rendering se admite actualmente en aplicaciones que usan las API heredadas de WinRT (Windows complemento XR en Unity). La compatibilidad de ARR con aplicaciones OpenXR estará disponible próximamente.

## <a name="next-steps"></a>Pasos siguientes

[!INCLUDE[](includes/tools-next-steps.md)]