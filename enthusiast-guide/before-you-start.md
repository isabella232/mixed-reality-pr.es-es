---
title: Antes de comenzar
description: Cómo asegurarse de que su equipo es compatible con Windows Mixed Reality y está listo para ello.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, compatible, compatibilidad, introducción, configuración, equipos, requisitos del sistema
appliesto:
- Windows 10
ms.openlocfilehash: f4743b6548def227675944fcd742b1596963cb3c
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725496"
---
# <a name="before-you-start"></a>Antes de comenzar

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Lo que necesitará para ejecutar Windows Mixed Reality

* Una [pantalla montada de encabezado de Windows Mixed Reality (HMD)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).
* Un nuevo [equipo preparado para Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) o un equipo compatible con Windows Mixed Reality que ejecute Windows 10, versión 1709 o posterior.
* Una conexión a Internet
* Adaptadores de pantalla, USB y Bluetooth (si no están integrados en auriculares o en un equipo)
* Ambos controladores de movimiento, un controlador Xbox o un mouse y un teclado
* Auriculares con micrófono (si su HMD no los tiene integrados)
* Un espacio de apertura grande

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>Asegúrese de que su equipo es compatible con Windows Mixed Reality.

Compruebe los [requisitos de hardware de equipo mínimo de Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o ejecute el [portal de Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) en su equipo para comprobar la compatibilidad con Windows Mixed Reality.

Lea los [problemas de compatibilidad de equipos](https://support.microsoft.com/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality) para más información.

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Asegúrese de que tiene instalada la versión 1709 o posterior de Windows 10.

Debe ejecutar la versión 1903 o posterior de Windows 10 para usar Windows Mixed Reality. Las versiones compatibles de Windows 10 incluyen:

* Windows 10 versión 1903
* Windows 10 versión 1909
* Windows 10 versión 2004
* Windows 10 versión 20H2

Para ver qué versión de Windows 10 está ejecutando actualmente el dispositivo, seleccione el botón **Inicio** y, a continuación, seleccione **configuración > sistema > acerca de**.

Para asegurarse de que Windows 10 está actualizado en su PC, seleccione el botón **Inicio** y, a continuación, seleccione **configuración > actualizar & seguridad > Windows Update**.  Haga clic en **Buscar actualizaciones**. Si hay actualizaciones disponibles, instálela.

Para obtener más información, consulte [mantener el equipo](https://support.microsoft.com/help/12373/windows-update-faq) actualizado.

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Asegurarse de que el equipo está conectado a Internet

Compruebe que el equipo está conectado a Internet y descargue los controladores y cualquier software adicional para poner en marcha Windows Mixed Reality.

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Asegúrese de que tiene un controlador de gráficos compatible

El equipo necesita un controlador de gráficos WDDM 2,2 o posterior para poder completar la instalación de Windows Mixed Reality. Si aún no tiene un controlador de gráficos compatible, pruebe estos orígenes:

* Busque las actualizaciones de controladores críticas más recientes mediante Windows Update (**inicio > configuración de Windows > actualización y seguridad > buscar actualizaciones**)
* Busque las actualizaciones de controladores opcionales más recientes:
    1. Haga clic con el botón secundario en **inicio > Device Manager**.
    2. Expanda **adaptadores de pantalla**.
    3. Haga clic con el botón derecho en la tarjeta gráfica y elija **Actualizar controlador > buscar automáticamente en el software de controlador actualizado**.
* Compruebe el sitio web del fabricante (OEM) del equipo.
* Compruebe el sitio web del fabricante de la tarjeta gráfica del equipo (por ejemplo, AMD, Intel o NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Asegúrese de que tiene los adaptadores necesarios

Es posible que el equipo compatible con Windows Mixed Reality no tenga los puertos HDMI y USB 3,0 de tamaño completo necesarios para conectar los auriculares que se incluyen. También es posible que necesite un adaptador de Bluetooth para cumplir los requisitos del portal de Windows Mixed Reality.  En ese caso, necesitará adaptadores para conectar los auriculares y los controladores de movimiento. Asegúrese de revisar la lista de [tipos de adaptador y recomendaciones en modelos de adaptador específicos](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

## <a name="make-sure-that-you-have-input-devices"></a>Asegúrese de que tiene dispositivos de entrada

Windows Mixed Reality está diseñado para funcionar mejor con los controladores de movimiento de Windows Mixed Reality, que proporcionan interacciones precisas y naturales sin necesidad de instalar hardware en las paredes. Pero también puede usar un controlador de Xbox o un mouse y un teclado.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Asegúrese de que tiene un espacio de apertura grande

Si desea desplazarse mientras usa Windows Mixed Reality, deberá tener un espacio abierto grande.  Durante la instalación, se le pedirá que elija entre "sentado y permanente" o "todas las experiencias". Elija "todas las experiencias" y configure un límite Si desea desplazarse. Revise las [directrices de mantenimiento, seguridad y confort del casco envolvente](wmr-health-safety-comfort.md) para comprender los requisitos de espacio.

### <a name="seated-and-standing-no-boundary"></a>Sentado y permanente (sin límite)

Si selecciona "sentado y permanente", utilizará el casco sin límite. Esto significa que tendrá que permanecer en un lugar al usar los auriculares para evitar obstáculos físicos y hacer posibles riesgos. Puede ponerse al día, pero no debería moverse. Algunas aplicaciones pueden estar diseñadas para funcionar con un límite, por lo que es posible que no funcionen o que proporcionen la misma experiencia si las usa sin una.

### <a name="all-experiences-boundary"></a>Todas las experiencias (límite)

Si elige "todas las experiencias", configurará un límite y podrá desplazarse por las experiencias de las aplicaciones que funcionan con un límite y las que no requieren una. Prepare su espacio asegurándose de que no hay obstáculos, peligros o elementos frágiles en el área que va a usar, incluido encima de la cabeza. No configure en la parte superior de una escalera o bajo un ventilador de techo extra inferior. Quite breakables y obstáculos del área y asegúrese de que todos los usuarios que usan el casco leen y entienden las [directrices de seguridad](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

## <a name="see-also"></a>Consulte también

* [Conecte su HMD](plug-in-your-headset.md)
* [Requisitos mínimos de hardware de equipo](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)