---
title: Aplicaciones de ejemplo y características
description: Manténgase al día con todos los ejemplos de Microsoft disponibles y las aplicaciones de características de realidad mixta para HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, learn, ejemplos, MRTK, modo de investigación, HoloLens 2, códigos qr, WebRTC, captura de realidad mixta, control remoto de holografías, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 1c713604f3a73620c4b7314afe7b70e0b2a59bef1c4e0ae0482c7f0143c38e71
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227677"
---
# <a name="samples-and-feature-apps"></a>Aplicaciones de ejemplo y características

![Imagen de un usuario con HoloLens manipulando un holograma con movimiento de mano](unreal/images/unreal-developer.jpg)

Cada recorrido de desarrollo comienza con un vistazo a lo que otros desarrolladores han compilado correctamente. En el caso de la realidad mixta, no es diferente. Actualmente, todos nuestros tutoriales y aplicaciones de ejemplo se basan en Unity o Unreal. A medida que desarrollamos contenido para otros motores y plataformas, los encontrará en el encabezado correspondiente de la tabla de contenido.

## <a name="sample-apps"></a>Aplicaciones de ejemplo

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Ejemplos de características

Los ejemplos de características que se enumeran a continuación corresponden a implementaciones específicas que se tratan en nuestra documentación y abarcan una variedad de plataformas de desarrollo y dispositivos de hardware.

### <a name="openxr"></a>OpenXR

Para los desarrolladores que usan Unity 2020 para compilar aplicaciones para HoloLens 2 o Mixed Reality, se puede usar el complemento de OpenXR en lugar del complemento de WindowsXR para mejorar las compatibilidades multiplataforma. Mixed Reality OpenXR Plugin también funciona bien con la versión Mixed Reality Toolkit 2.7 más reciente.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [Uso del complemento OpenXR](./unity/xr-project-setup.md) | [Mixed Reality OpenXR con ejemplos de Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| N/D | [Proyecto OpenXR MRTK Base de Unity](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a>Modo de investigación

El modo de investigación se presentó en la primera generación de HoloLens para dar acceso a los sensores de claves en el dispositivo, específicamente para las aplicaciones de investigación que no están pensadas para la implementación. Las aplicaciones de ejemplo siguientes son ejemplos de acceso y grabación de secuencias de modo de investigación y el uso de los atributos [intrinsics y extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Artículo de referencia | Aplicación de ejemplo |
| --- | --- |
| [Modo de investigación](platform-capabilities-and-apis/research-mode.md) | [HoloLens (1ª generación)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Modo de investigación](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>Códigos QR

HoloLens 2 puede detectar códigos QR en el entorno alrededor del caso, estableciendo un sistema de coordenadas en la ubicación real de cada código.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [Códigos QR](platform-capabilities-and-apis/qr-code-tracking.md) | [Seguimiento de códigos QR en Unity](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a>Descripción de escenas

La descripción de escenas aporta a los desarrolladores de realidad mixta una representación estructurada y general del entorno, diseñada para que el desarrollo para aplicaciones con control del entorno sea intuitivo. Para ello, la descripción de escenas combina la potencia de los entornos en tiempo de ejecución de realidad mixta existentes, como la asignación espacial altamente precisa, pero menos estructurada, y los nuevos entornos en tiempo de ejecución controlados por IA.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [Descripción de escenas](../design/scene-understanding.md) | [Ejemplos de descripción de escenas de realidad mixta](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a>WebRTC

El proyecto MixedReality-WebRTC es una colección de componentes que ayudan a los desarrolladores de aplicaciones de realidad mixta a integrar la comunicación punto a punto en tiempo real de audio, vídeo y datos en los componentes de WebRTC de sus aplicaciones. Se basa en el protocolo de WebRTC para la comunicación en tiempo real (RTC), que es compatible con la mayoría de los exploradores web modernos.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [Aplicaciones de ejemplo de Unreal](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Captura holográfica de realidad mixta

Captura de realidad mixta (MRC) captura la experiencia en primera persona de combinar mundos reales y digitales como una foto o un vídeo, compartiendo lo que se ve con otros usuarios en tiempo real.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [Captura de realidad mixta](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Ejemplos de Captura de realidad mixta](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Control remoto de holografías

Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de PC que admiten el control remoto de holografías. El control remoto de holografías transmite contenido holográfico desde un PC a su Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi y es compatible con HoloLens (1.ª generación) y HoloLens 2.

<br>

| Artículo de referencia | Muestra |
| --- | --- |
| [Control remoto de holografías](platform-capabilities-and-apis/holographic-remoting-player.md) | [Ejemplos de control remoto de holografías](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |