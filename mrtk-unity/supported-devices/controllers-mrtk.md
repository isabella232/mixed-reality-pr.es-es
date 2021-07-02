---
title: Detección de controladores en MRTK
description: Documentación sobre el uso de varios controladores con MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity,HoloLens, HoloLens 2, Mixed Reality, development, MRTK, Controllers, HP Reverb, Oculus, WIRELESS Vive, Hands
ms.openlocfilehash: 2bb749f4e2f6294c4feb74f97af55ecb857d5f76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175595"
---
# <a name="detecting-controllers-in-mrtk"></a>Detección de controladores en MRTK

MRTK admite muchos controladores diferentes. Muchos controladores, comoCARE Vive Knuckles y USB Vive Wands, funcionarán de forma nativa una vez que se inicia una aplicación creada con MRTK en el dispositivo compatible. Otros controladores, como las manos articuladas de Oculus Packs y los controladores HP Reverb G2, requieren paquetes adicionales antes de que MRTK los reconozca.

En este documento se describen los escenarios comunes en los que es necesario instalar paquetes adicionales. Para obtener instrucciones sobre cómo implementar en el dispositivo, consulte las páginas de implementación [**hololens/WMR**](./wmr-mrtk.md) o [**Oculus Wmr.**](/windows/mixed-reality/mrtk-unity/supported-devices/oclus-quest-mrtk) Para obtener información adicional sobre los controladores, visite la [**página de características**](../features/input/controllers.md). Para depurar problemas con controladores, consulte la herramienta [ **de asignación de controladores.**](../features/tools/controller-mapping-tool.md)

## <a name="hp-reverb-g2-controllers"></a>Controladores HP Reverb G2

Para detectar y mostrar los controladores HP Reverb G2 al usar MRTK, siga estos pasos para instalar el [**paquete Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) Una vez instalado este paquete, no es necesario realizar ningún otro cambio en los perfiles predeterminados para que los controladores se muestren en HP Reverb. 

Para mostrar los controladores en el editor, debe asegurarse de que usa el mediante el [**complemento OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).

## <a name="oculus-controllers"></a>Controladores de Oculus 

Para visualizar los modelos de controlador de Oculus, siga las instrucciones de implementación de Oculus Raid. Si desea mostrar las manos virtuales al usar los controladores, asegúrese de que la opción Representar las manos **de Avatar** en lugar de controladores está activada en el sdk de XR Oculus Administrador de dispositivos. De lo contrario, desactive esta opción.

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
