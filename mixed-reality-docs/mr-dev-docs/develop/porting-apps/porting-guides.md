---
title: Portabilidad de aplicaciones de VR a Windows Mixed Reality
description: Un tutorial paso a paso que explica cómo migrar una aplicación envolvente existente a Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: puerto, Unity, no real, middleware, motor, UWP, Win32, portabilidad, HoloLens primera generación, auriculares de realidad mixta, auriculares de realidad mixta de Windows, migración, Windows 10, asignación de entrada
ms.openlocfilehash: f1cb7cd96ee1d6e32c9ef1f8d3e0e1b2654e0a79
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009875"
---
# <a name="porting-vr-apps-to-windows-mixed-reality"></a>Portabilidad de aplicaciones de VR a Windows Mixed Reality

Windows 10 incluye compatibilidad con auriculares envolventes y holográficas. Si ha creado contenido para otros dispositivos, como Oculus Rift o HTC Naopak, tienen dependencias en las bibliotecas que existen por encima de la API de plataforma del sistema operativo. La incorporación de aplicaciones de la aplicación existente de Win32 Unity a Windows Mixed Reality implica la redestinación del uso de los SDK de VR específicos del proveedor a las API de VR entre proveedores de Unity.

## <a name="porting-requirements"></a>Requisitos de portabilidad

En un nivel alto, los siguientes pasos están relacionados con el traslado de contenido existente:
1. **Asegúrese de que el equipo ejecuta Windows 10 Fall Creators Update (16299).** Ya no se recomienda recibir compilaciones de vista previa del anillo de Insider SKIP Preview, ya que esas compilaciones no serán las más estables para el desarrollo de realidad mixta.
2. **Actualice a la versión más reciente de los gráficos o del motor de juegos.** Los motores de juegos deberán admitir la versión 10.0.15063.0 del SDK de Windows 10 (Publicada en el 2017 de abril) o superior.
3. **Actualice cualquier middleware, complemento o componente.** Si la aplicación contiene componentes, es una buena idea actualizar a la versión más reciente.
4. **Quite las dependencias de los SDK duplicados**. En función del dispositivo al que se dirija el contenido, tendrá que quitar o compilar de forma condicional ese SDK para que pueda establecer como destino las API de Windows en su lugar. Un ejemplo de este escenario sería SteamVR.
5. **Trabaje con problemas de compilación.** En este momento, el ejercicio de portabilidad es específico de la aplicación, el motor y las dependencias de componentes que tiene.

## <a name="common-porting-steps"></a>Pasos de portabilidad comunes

### <a name="1-make-sure-you-have-the-right-development-hardware"></a>1. Asegúrese de que tiene el hardware de desarrollo correcto

En la página [instalar las herramientas](../install-the-tools.md#immersive-vr-headset-requirements) se muestra el hardware de desarrollo recomendado.

### <a name="2-upgrade-to-the-latest-flight-of-windows-10"></a>2. actualizar al vuelo más reciente de Windows 10

La plataforma Windows Mixed Reality todavía está en desarrollo activo. Se recomienda [unirse al programa Windows Insider](https://insider.windows.com/) para tener acceso al vuelo "Windows Insider Fast".
1. Instalación de [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Únase](https://insider.windows.com/) al programa Windows Insider.
3. Habilitar el [modo de desarrollador](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Cambiar a los [vuelos rápidos de Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) a través de la **configuración > actualización & sección de seguridad**

### <a name="3-upgrade-to-the-most-recent-build-of-visual-studio"></a>3. actualizar a la compilación más reciente de Visual Studio
* Si usa Visual Studio, actualice a la compilación más reciente
* Vea [instalar la](../install-the-tools.md#installation-checklist) página de herramientas en Visual Studio 2019

### <a name="4-choose-the-correct-adapter"></a>4. Elija el adaptador correcto
* En sistemas como notebooks con dos GPU, [el destino es el adaptador correcto](../native/rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Esto se aplica a las aplicaciones de Unity y de DirectX nativas donde se crea un ID3D11Device, ya sea de forma explícita o implícita (Media Foundation), para su funcionalidad.

## <a name="unity-porting-guidance"></a>Guía de portabilidad de Unity

[!INCLUDE[](includes/unity-porting-guidance.md)]

## <a name="unreal-porting-guidance"></a>Instrucciones de portabilidad inreal

> [!IMPORTANT]
> Si usa controladores de HP reverberación G2, consulte [este artículo](../unreal/unreal-reverb-g2-controllers.md) para obtener instrucciones adicionales de asignación de entrada.

## <a name="see-also"></a>Consulte también
* [Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Descripción del rendimiento de la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](../unity/performance-recommendations-for-unity.md)
* [Controladores de movimiento](../../design/motion-controllers.md)
* [Gestos y controladores de movimiento en Unity](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guías de migración](porting-guides.md)