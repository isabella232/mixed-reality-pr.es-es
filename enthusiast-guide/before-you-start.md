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
ms.openlocfilehash: c76f670230a4a19b53b7e8f938b13e79bb7c8db7
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174441"
---
# <a name="before-you-start"></a>Antes de empezar

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>Lo que necesitará para ejecutar Windows Mixed Reality

* Una [pantalla montada de encabezado de Windows Mixed Reality (HMD)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).
* Un nuevo [equipo preparado para Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) o un equipo compatible con Windows Mixed Reality que ejecute Windows 10, versión 1709 o posterior.
* Una conexión a Internet
* Adaptadores de pantalla, USB y Bluetooth (si no están integrados en auriculares o en un equipo)
* Ambos controladores de movimiento, un controlador Xbox o un mouse y un teclado
* Auriculares con micrófono (si su HMD no los tiene integrados)
* Un espacio de apertura grande

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>Asegúrese de que su equipo es compatible con Windows Mixed Reality.

Para ver si su equipo es compatible con Windows Mixed Reality, compruebe los [requisitos de hardware de equipo mínimo de Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o ejecute el [portal de Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) en su PC.

Para obtener más información sobre los problemas de compatibilidad de equipos, vaya [aquí](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality).

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Asegúrese de que tiene instalada la versión 1709 o posterior de Windows 10.

Debe ejecutar la versión 1709 de Windows 10 (Fall Creators Update) o una más reciente para usar Windows Mixed Reality. Las versiones compatibles de Windows 10 incluyen:
* Windows 10 versión 1709 (Fall Creators Update, compilación 16299)
* Windows 10 versión 1803 (actualización de Spring, compilación 17134)
* Windows 10 versión 1809 (actualización de octubre, compilación 17763)

Para ver qué versión de Windows 10 está ejecutando actualmente el dispositivo, seleccione el botón **Inicio** y, a continuación, seleccione **configuración > sistema > acerca de**.

Para asegurarse de que Windows 10 está actualizado en su PC, seleccione el botón **Inicio** y, a continuación, seleccione **configuración > actualizar & seguridad > Windows Update**.  Haga clic en **Buscar actualizaciones**. Si hay actualizaciones disponibles, instálela.

Para obtener más información sobre cómo mantener el equipo actualizado, vaya [aquí](https://support.microsoft.com/en-us/help/12373/windows-update-faq)

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Asegurarse de que el equipo está conectado a Internet

Compruebe que el equipo está conectado a Internet. Tendrá que descargar los controladores y el software adicional para poner en marcha Windows Mixed Reality.  Si el Wi-Fi conexión de red está establecido en medido, cámbielo a no medido. [Más información](https://support.microsoft.com/en-us/help/4028458/windows-metered-connections-in-windows-10).

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Asegúrese de que tiene un controlador de gráficos compatible

El equipo debe tener un controlador de gráficos WDDM 2,2 o posterior para poder completar la configuración de la realidad mixta. Si aún no tiene un controlador de gráficos compatible, pruebe estos orígenes:

* Busque las actualizaciones de controladores críticas más recientes mediante Windows Update (**inicio > configuración de Windows > actualización y seguridad > buscar actualizaciones**)
* Busque las actualizaciones de controladores opcionales más recientes:
    1. Haga clic con el botón secundario en **inicio > Device Manager**.
    2. Expanda **adaptadores de pantalla**.
    3. Haga clic con el botón derecho en la tarjeta gráfica y elija **Actualizar controlador > buscar automáticamente en el software de controlador actualizado**.
* Compruebe el sitio web del fabricante (OEM) del equipo.
* Compruebe el sitio web del fabricante de la tarjeta gráfica del equipo (por ejemplo, AMD, Intel o NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Asegúrese de que tiene los adaptadores necesarios

Es posible que el equipo compatible con Windows Mixed Reality no tenga los puertos HDMI y USB 3,0 de tamaño completo necesarios para conectar los auriculares que se incluyen. O bien, puede que necesite un adaptador de Bluetooth para cumplir con los requisitos del portal de realidad mixta.  En ese caso, necesitará adaptadores para conectar los auriculares y los controladores de movimiento. Encontrará una lista de tipos de adaptador que puede necesitar y algunas recomendaciones sobre [los modelos de](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)adaptador específicos.

## <a name="make-sure-that-you-have-input-devices"></a>Asegúrese de que tiene dispositivos de entrada

Windows Mixed Reality está diseñado para funcionar mejor con los controladores de movimiento de Windows Mixed Reality, que proporcionan interacciones precisas y naturales sin necesidad de instalar hardware en las paredes. Pero también puede usar un controlador de Xbox o un mouse y un teclado.

## <a name="get-headphones-if-your-headset-didnt-come-with-them"></a>Obtener auriculares Si el casco no se ha incorporado

A menos que haya adquirido un Odyssey Samsung HMD, HP reverberation o HP reverberación G2 (que tienen auriculares AKG integrados y un micrófono de matriz dual integrado), tendrá que obtener un casco de audio a un par de auriculares que pueden conectarse al conector de audio de headset's 3.5 mm de HMD.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Asegúrese de que tiene un espacio de apertura grande

Si desea desplazarse mientras usa Windows Mixed Reality, deberá tener un espacio abierto grande.  Durante la instalación se le pedirá que elija entre "sentado y permanente" o "todas las experiencias". Seleccione "todas las experiencias" y configure un límite Si desea desplazarse.

### <a name="seated-and-standing-no-boundary"></a>Sentado y permanente (sin límite)

Si selecciona "sentado y permanente", utilizará el casco sin límite. Esto significa que tendrá que permanecer en un lugar al usar los auriculares para que pueda evitar obstáculos físicos y que se produzcan riesgos. Puede ponerse al día, pero no debería moverse. Algunas aplicaciones pueden estar diseñadas para trabajar con un límite, por lo que es posible que no pueda usarlas, o que no tengan la misma experiencia, si las usa sin límite.

### <a name="all-experiences-boundary"></a>Todas las experiencias (límite)

Si elige "todas las experiencias", configurará un límite y podrá desplazarse y usar aplicaciones y experiencias que funcionan con un límite, así como las que no requieren una. Tendrá que preparar el espacio para asegurarse de que no haya obstáculos, peligros ni elementos frágiles en el área que va a usar (incluido por encima de su cabeza). No configure en la parte superior de una escalera o bajo un ventilador de techo extra inferior. Quite breakables y obstáculos del área y asegúrese de que usted y cualquier persona que use el casco Lea y comprenda las [directrices de seguridad](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

## <a name="see-also"></a>Consulte también

* [Conecte su HMD](plug-in-your-headset.md)
* [Requisitos mínimos de hardware de equipo](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)