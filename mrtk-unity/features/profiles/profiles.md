---
title: Profiles
description: Perfiles de documentación en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, perfiles,
ms.openlocfilehash: 785d402e924a534627dfd1d742d2019d9ce9dd5a
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908246"
---
# <a name="profiles"></a>Profiles

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Introduction-to-MRTK-Profiles/player]

Una de las formas principales de configurar MRTK es a través de los perfiles disponibles en el paquete de base. El objeto [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) principal de una escena tendrá el perfil activo, que es scriptableObject. El perfil de configuración de MRTK de nivel superior contiene datos de sub-perfil para cada núcleo de los sistemas principales, cada uno de los cuales está diseñado para configurar el comportamiento de sus subsistemas correspondientes. Además, estos sub profiles también son ScriptableObjects y, por tanto, pueden contener referencias a otros objetos de perfil un nivel por debajo de ellos. Básicamente, hay un árbol completo de perfiles conectados que son la información de configuración para inicializar los subsistemas y características de MRTK.

Por ejemplo, el comportamiento del sistema de entrada se rige por un perfil de sistema de entrada, como `DefaultMixedRealityInputSystemProfile` (Assets/MRTK/SDK/Profiles).

<img src="../images/profiles/input_profile.png" width="650px" alt="Input profile" style="display:block;">
<sup>Inspector de perfil</sup>

## <a name="background"></a>Información previa

Los perfiles están diseñados principalmente para admitir escenarios específicos en varios dispositivos, que se controlan a través de los proveedores de datos. De este modo, una aplicación se puede diseñar lo más independiente del dispositivo como sea posible y permitir que MRTK y los proveedores de datos del perfil controlen la compatibilidad multiplataforma.

También hay perfiles creados en torno a las características de entrada de dispositivos específicos, como el perfil de HoloLens 1, que tiene como valor predeterminado interacciones de estilo GGV.

## <a name="xr-sdk"></a>XR SDK

::: moniker range=">= mrtkunity-2021-05"
Use cualquiera de los perfiles de MRTK predeterminados, que están configurados en las canalizaciones XR de Unity. Los valores anteriores "DefaultOpenXRConfigurationProfile" y "DefaultXRSDKConfigurationProfile" ahora están etiquetados como obsoletos.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Actualmente, hay dos perfiles proporcionados para el SDK de XR, `DefaultXRSDKConfigurationProfile` y `DefaultHoloLens2XRSDKConfigurationProfile` . Como resultado, no todas las escenas de ejemplo son totalmente compatibles debido a configuraciones específicas de la escena y del escenario. Los ejemplos que usan `DefaultMixedRealityToolkitConfigurationProfile` y `DefaultHoloLens2ConfigurationProfile` _se_ pueden intercambiar a sus perfiles correspondientes del SDK de XR. Si usa OpenXR con el SDK de XR, use en `DefaultOpenXRConfigurationProfile` su lugar.

Se está trabajando más para facilitar la configuración y admitir todas las escenas de ejemplo, lo que permite configurar el SDK de XR y XR heredado en paralelo. Consulte el tema [#9419](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9419) para el seguimiento.
::: moniker-end

Consulte [Configuring MRTK for the XR SDK pipeline (Configuración de MRTK](../../configuration/getting-started-with-mrtk-and-xrsdk.md#configuring-mrtk-for-the-xr-sdk-pipeline) para la canalización del SDK de XR) para obtener más información sobre la conversión de perfiles entre XR heredado y el SDK de XR.

## <a name="default-profile"></a>Perfil predeterminado

MRTK proporciona un conjunto de perfiles predeterminados que cubren la mayoría de las plataformas y escenarios que admite MRTK. Por ejemplo, al seleccionar `DefaultMixedRealityToolkitConfigurationProfile` (Assets/MRTK/SDK/Profiles), podrá probar escenarios en VR (OpenVR, WMR) y HoloLens (1 y 2).

Tenga en cuenta que, dado que se trata de un perfil de uso general, no está optimizado para ningún caso de uso determinado. Si desea tener una configuración más específica o de mayor rendimiento que sea mejor en otras plataformas, consulte los demás perfiles siguientes, que se han ajustado ligeramente para mejorar sus respectivas plataformas.

## <a name="hololens-2-profile"></a>HoloLens 2 perfil

MRTK también proporciona un perfil predeterminado optimizado para la implementación y las pruebas en HoloLens 2: `DefaultHoloLens2ConfigurationProfile` (Assets/MRTK/SDK/Profiles/HoloLens2).

Cuando se le pida que elija un perfil para el objeto MixedRealityToolkit, use este perfil en lugar del perfil seleccionado predeterminado.

Las principales diferencias entre el perfil de HoloLens2 y el perfil predeterminado son:

**Características deshabilitadas:**

- [Sistema de límites](../boundary/boundary-system-getting-started.md)
- [Teleport system](../teleport-system/teleport-system.md)
- [Sistema de reconocimiento espacial](../spatial-awareness/spatial-awareness-getting-started.md)
- [Visualización de malla de mano](../input/hand-tracking.md) (debido a la sobrecarga de rendimiento)

**Sistemas** habilitados:

- El [proveedor de seguimiento de los ojos](../input/eye-tracking/eye-tracking-main.md)
- Simulación de entrada de ojos

La configuración del perfil de la cámara se establece para que coincida, de modo que la calidad del editor y la calidad del reproductor sean iguales. Esto es diferente del perfil de cámara predeterminado, donde las pantallas opacas se establecen en una mayor calidad. Este cambio significa que la calidad en el editor será menor, lo que coincidirá más estrechamente con lo que se representará en el dispositivo.

> [!NOTE]
> El sistema de reconocimiento espacial está desactivado de forma predeterminada en función de los comentarios del cliente: es una visualización interesante que se puede ver inicialmente, pero normalmente se apaga para evitar la distracción visual y el impacto adicional en el rendimiento de tenerla activada. El sistema se puede volver a habilitar siguiendo las [instrucciones que se indican aquí.](../spatial-awareness/spatial-awareness-getting-started.md)
