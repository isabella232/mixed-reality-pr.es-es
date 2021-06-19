---
title: Portabilidad de aplicaciones de VR a Windows Mixed Reality
description: Tutorial paso a paso que explica cómo portabilidad de una aplicación inmersiva existente a Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: port, unity, unreal, middleware, engine, UWP, Win32, porting, HoloLens 1st gen, mixed reality headset, windows mixed reality headset, migration, Windows 10, input mapping,
ms.openlocfilehash: bb76325c0a2d10150cff6604e29c7ead8a97df8e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394469"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portabilidad de aplicaciones de VR a Windows Mixed Reality

Windows 10 compatibilidad con cascos envolventes y holográficos. Si ha creado contenido para otros dispositivos, como OculusPlataforma o LAN, tienen dependencias en las bibliotecas que existen por encima de la API de la plataforma del sistema operativo. Llevar las aplicaciones existentes de VR de Win32 Unity a Windows Mixed Reality implica redestinar el uso de SDK de VR específicos del proveedor a las API de VR entre proveedores de Unity.

## <a name="porting-requirements"></a>Requisitos de porte

En un nivel alto, los pasos siguientes intervienen en la porción de contenido existente:
1. **Asegúrese de que el equipo ejecuta el Windows 10 Fall Creators Update (16299).** Ya no se recomienda recibir compilaciones en versión preliminar del anillo Omitir paso a paso por adelantado de Insider, ya que esas compilaciones no serán las más estables para el desarrollo de realidad mixta.
2. **Actualice a la versión más reciente del motor de gráficos o juegos.** Los motores de juegos tendrán que admitir la versión 10.0.15063.0 del SDK de Windows 10 (publicada en abril de 2017) o superior.
3. **Actualice cualquier middleware, complementos o componentes.** Si la aplicación contiene algún componente, es una buena idea actualizar a la versión más reciente.
4. **Quite las dependencias de los SDK duplicados.** En función del dispositivo al que se dirigira el contenido, deberá quitar o compilar condicionalmente ese SDK para que pueda dirigirse a las API de Windows en su lugar. Un ejemplo de este escenario sería SteamVR.
5. **Trabaje con problemas de compilación.** En este punto, el ejercicio de porte es específico de la aplicación, el motor y las dependencias de componentes que tiene.

## <a name="common-porting-steps"></a>Pasos comunes de porte

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Asegúrese de que tiene el hardware de desarrollo adecuado

En [la página de la guía para aficionados a la](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines) realidad virtual se muestra el hardware de desarrollo recomendado.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. Actualización al último vuelo de Windows 10

La Windows Mixed Reality está aún en desarrollo activo. Se recomienda [unirse al Programa Windows Insider](https://insider.windows.com/) para acceder al vuelo "Windows Insider Fast".
1. Instale el [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Una](https://insider.windows.com/) el Programa Windows Insider.
3. Habilitación [del modo de desarrollador](/windows/uwp/get-started/enable-your-device-for-development)
4. Cambie a la sección [Windows Insider rápidos a](/archive/blogs/uktechnet/joining-insider-preview) través de **configuración > actualización & seguridad.**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. Actualización a la compilación más reciente de Visual Studio
* Si usa Visual Studio, actualice a la compilación más reciente.
* Consulte [la página Instalar las](../install-the-tools.md#installation-checklist) herramientas en Visual Studio 2019.

### <a name="4-choose-the-correct-adapter"></a>4. Elegir el adaptador correcto
* En sistemas como cuadernos con dos GPU, el [destino es el adaptador correcto.](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications) Esto se aplica a las aplicaciones nativas de Unity y DirectX en las que se crea un dispositivo ID3D11, ya sea de forma explícita o implícita (Media Foundation), para su funcionalidad.

## <a name="unity-porting-guidance"></a>Guía de porte de Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Guía de porte de Unreal

> [!IMPORTANT]
> Si usa controladores HP Reverb G2, consulte este artículo para obtener [instrucciones](../unreal/unreal-reverb-g2-controllers.md) de asignación de entrada adicionales.

## <a name="see-also"></a>Vea también
* [Windows Mixed Reality de compatibilidad de hardware de equipo mínimo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Descripción del rendimiento de Mixed Reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](../unity/performance-recommendations-for-unity.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
* [Controladores de movimiento en Unity](../unity/motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guías de migración](porting-guides.md)