---
title: Configuración del proyecto con Unreal
description: Obtenga información sobre cómo configurar el proyecto con la versión más reciente de Unreal Engine y Mixed Reality Feature Tool.
author: hferrone
ms.author: v-hferrone
ms.date: 4/28/2021
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, realidad mixta, desarrollo, características, nuevo proyecto, emulador, documentación, guías, hologramas, desarrollo de juegos, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual
ms.openlocfilehash: 8201e97ed35d11404928c1dfe94ad9b7e626e51b
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394617"
---
# <a name="setting-up-your-unreal-project"></a>Configuración del proyecto con Unreal

Se recomienda instalar [Unreal Engine, versión 4.25 ](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o posterior, para aprovechar al máximo la compatibilidad integrada de HoloLens.

Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**. En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.
![Opción de instalación no real de HoloLens 2](../images/Unreal_Install_Option_HoloLens2.png)

## <a name="import-mixed-reality-toolkit-for-unreal"></a>Importación de Mixed Reality Toolkit para Unreal

![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales. El kit de herramientas está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.

Para la instalación, le recomendamos que complete la [sección Introducción](unreal-development-overview.md#1-getting-started) de nuestro [recorrido de desarrollo de Unreal](unreal-development-overview.md) seleccionado. Si ya sigue el recorrido de desarrollo de Unreal, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagen del logotipo de Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si no desea usar MRTK para Unreal, tendrá que crear scripts para todas las interacciones y comportamientos.