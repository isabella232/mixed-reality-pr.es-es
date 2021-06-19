---
title: Elección de la canalización para desarrolladores
description: Manténgase al día de las recomendaciones de canalización de desarrollo de Unity más recientes para el desarrollo de aplicaciones de HoloLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: b7896c2426ff9adb1133e86a5e3204bff1249ebc
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394559"
---
# <a name="choosing-your-developer-pipeline"></a>Elección de la canalización para desarrolladores

![Banner del logotipo de Unity](../images/unity_logo_banner.png)<br>

Aunque actualmente se recomienda instalar **Unity 2019.4 LTS** y usar XR integrado heredado para el desarrollo de Mixed Reality, también puede compilar aplicaciones con otras configuraciones de Unity.

## <a name="mixed-reality-toolkit-recommended"></a>Mixed Reality Toolkit (recomendado)

La configuración de Unity recomendada actualmente de Microsoft para HoloLens 2 es Mixed Reality Toolkit...

### <a name="install-the-mixed-reality-feature-tool"></a>Instalación de la herramienta Mixed Reality características

La [herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md) es una nueva manera de que los desarrolladores detecten y agreguen paquetes de características de Mixed Reality en proyectos de Unity. 

Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación. Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto que elija.

### <a name="importing-the-mixed-reality-toolkit-for-unity"></a>Importación de Mixed Reality Toolkit para Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](mrtk-getting-started.md) (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. 

* Instale el paquete de Mixed Reality Toolkit según las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md#system-requirements) y seleccione el paquete **Mixed Reality Toolkit Foundation**.

Se recomienda que complete la sección Introducción de nuestros recorridos de desarrollo de [HoloLens](unity-development-overview.md#1-getting-started) o [VR](unity-development-wmr-overview.md#1-getting-started) seleccionados. Si ya sigue el recorrido de desarrollo de Unity para HoloLens, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Tenga en cuenta que las instrucciones de instalación están destinadas a la combinación estable más reciente de las versiones de MRTK y Unity, que son **MRTK 2.6.1** y **Unity 2019.4 LTS**.

> [!NOTE]
> Si no quiere usar MRTK para Unity, tendrá que [crear scripts para todas las interacciones y comportamientos](configure-unity-project.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner de Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit - Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

## <a name="manual"></a>Manual 

Tbd...