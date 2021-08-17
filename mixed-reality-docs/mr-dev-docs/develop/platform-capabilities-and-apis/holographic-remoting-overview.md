---
title: Información general sobre la comunicación remota holográfica
description: Obtenga información sobre qué es la comunicación remota holográfica y cómo puede beneficiar al proceso de desarrollo.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, learn, tutorial, getting started, holographic remoting, desktop, preview
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184606"
---
# <a name="holographic-remoting-overview"></a>Información general sobre la comunicación remota holográfica

Puede usar Holographic Remoting para transmitir contenido holográfico a su HoloLens en tiempo real. Hay dos usos principales para esto y es importante comprender la diferencia:

1. (Unity o **Unreal):** quiere obtener una vista previa y depurar la aplicación durante el proceso de desarrollo: puede ejecutar la aplicación localmente en el editor de Unity en el equipo en modo de reproducción y transmitir la experiencia a su HoloLens. Esto proporciona una manera de depurar rápidamente la aplicación sin compilar e implementar un proyecto completo. A este tipo de aplicación se le llama aplicación _holographic remoting Play Mode Preview_.

    - [Más información sobre la vista previa y depuración de la aplicación en Unity](../unity/preview-and-debug-your-app.md)

    - [Más información sobre la vista previa y depuración de la aplicación en Unreal](../unreal/unreal-streaming.md)

1. (Unity, Unreal o C++): quiere que los recursos de un equipo enciendan la aplicación en lugar de depender de los recursos de **HoloLens** internos: puede crear y compilar una aplicación que tenga la funcionalidad de comunicación remota holográfica. El usuario experimenta la aplicación en el HoloLens, pero la aplicación se ejecuta realmente en un equipo, lo que le permite aprovechar los recursos más eficaces del equipo. Esto puede resultar especialmente útil si la aplicación tiene modelos o activos de alta resolución y no desea que la velocidad de fotogramas sufra. Este tipo de aplicación se llama aplicación _remota de comunicación remota holográfica._

    - [Más información sobre el uso de recursos de PC en Unity](../unity/use-pc-resources.md)

    - [Más información sobre el uso de recursos de PC en Unreal](../unreal/unreal-streaming.md)

    - [Escritura de una aplicación remota de comunicación remota holográfica Windows Mixed Reality API (C++)](holographic-remoting-create-remote-wmr.md)

    - [Escritura de una aplicación remota de comunicación remota holográfica mediante las API de OpenXR (C++)](holographic-remoting-create-remote-openxr.md)

En cualquier caso, las entradas de HoloLens (mirada, gesto, voz y asignación espacial) se envían al equipo, el contenido se representa en una vista inmersiva virtual y, a continuación, los fotogramas representados se envían al HoloLens. 

## <a name="see-also"></a>Consulte también

* [Holographic Remoting Player](holographic-remoting-player.md)
* [Tutorial: Introducción a la comunicación remota holográfica de PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Creación de una aplicación de pc de comunicación remota holográfica](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
