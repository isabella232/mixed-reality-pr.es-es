---
title: Conexión del casco
description: Obtenga información acerca de cómo conectar los auriculares de la realidad mixta de Windows a USB 3,0 y HDMI, y cómo conectar sus auriculares al casco.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, auriculares, configuración, introducción
appliesto:
- Windows 10
ms.openlocfilehash: 46b40a09c88013515911026cbd03a6fc6d19e1ca
ms.sourcegitcommit: 2cdc2e38990fff24972d98f9e74f0dabacbffa7d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2020
ms.locfileid: "92153501"
---
# <a name="plug-in-your-headset"></a>Conexión del casco

## <a name="connect-your-headset-to-your-pcs-usb-30-port"></a>Conecte los auriculares al puerto USB 3,0 de su PC

Identifique el puerto USB 3,0 en el equipo y conecte el cable USB. Los puertos USB 3,0 tienen SS (súper velocidad) escrito junto a ellos. Suelen ser (pero no siempre) azules.

Si no tiene suficientes puertos USB abiertos en el equipo, puede usar un [concentrador usb 3,0 externo con alimentación de CA](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets).

## <a name="connect-your-headset-to-your-pcs-hdmi-out-port"></a>Conecte los auriculares al puerto de salida de HDMI de su PC

Identifique el puerto de salida de HDMI en el equipo y conecte el cable HDMI del casco. Asegúrese de que **no** está enchufando en el puerto HDMI.

## <a name="connect-headphones-to-your-headset"></a>Conectar auriculares a los auriculares

A menos que haya adquirido un auricular de Samsung HMD Odyssey, HP reverberation o HP Reverberate G2 (que han integrado auriculares de AKG y un micrófono de matriz dual integrado), deberá conectar los auriculares (preferiblemente con un micrófono en línea) que pueda conectarse al conector de audio de 3,5 mm del casco.

## <a name="common-issues"></a>Problemas comunes
* Conectó el cable HDMI antes de conectar el cable USB 3,0.  Asegúrese de que conecta el cable USB 3,0 **antes** de conectar el cable HDMI.
* Conectó un adaptador Bluetooth junto al cable USB de su HMD.  Si usa un adaptador de Bluetooth, **no** Conecte el cable USB del casco junto a ese adaptador, ya que las interferencias de radio resultantes pueden afectar negativamente al rendimiento de Bluetooth.
* Ha enchufado el cable HDMI en el puerto HDMI de iGPU en lugar de su puerto HDMI dGPU (para PC con ambos). Algunos equipos de escritorio tienen una unidad de procesamiento de gráficos (iGPU) integrada y una unidad de procesamiento de gráficos discretos (dGPU) y, a menudo, se deshabilitan los puertos iGPU. Si el equipo tiene un dGPU, el casco debe estar conectado a dGPU.  
* Si el equipo no tiene un puerto HDMI, es posible que necesite un adaptador. [Vea la lista completa de adaptadores recomendados aquí](recommended-adapters-for-windows-mixed-reality-capable-pcs.md). 
* Está conectando los auriculares a un dispositivo Surface. Lea [uso de Surface con Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="see-also"></a>Vea también

* [Solución de problemas de conectividad con auriculares](headset-connectivity.md)
* [Instalación de Windows Mixed Reality](install-windows-mixed-reality.md)
* [Adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* [Directrices mínimas de hardware de PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
