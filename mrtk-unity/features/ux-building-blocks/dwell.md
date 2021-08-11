---
title: Permanencia
description: Interacción de permanencia
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, development, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226914"
---
# <a name="dwell"></a>Permanencia

![Elemento principal de permanencia](../images/dwell/MRTK_UX_Dwell.png)

La mirada con la cabeza y la permanencia son excelentes en escenarios en los que las manos de una persona están ocupadas con otras tareas. La característica también es útil cuando la voz no es 100 % confiable o disponible debido a restricciones ambientales o sociales.
Los ejemplos de permanencia de MRTK muestran diferentes tipos de componentes de interfaz de usuario con tiempo de respuesta configurable y comentarios visuales.

Consulte la [página guía de mirada con la](/windows/mixed-reality/design/gaze-and-dwell-head) cabeza y permanencia para ver las recomendaciones de diseño.

## <a name="dwell-scripts"></a>Scripts de permanencia

- **DwellHandler:** agrega una modalidad de permanencia al destino de la interfaz de usuario.
- **DwellStateType:** los estados del controlador de permanencia.
- **DwellUnityEvent:** evento de Unity para un evento de permanencia. Contiene la referencia de puntero.
- **BaseDwellPressableButton.cs:** script que desencadena el evento OnClick() en `Interactable` prefabs PressableButtonHoloLens2.
- **ToggleDwellPressableButton.cs:** este script modifica la propiedad de que usa el sombreador `_BorderWidth` `dwellVisualImage` estándar de MRTK.

## <a name="dwell-profiles"></a>Perfiles de permanencia
El controlador de permanencia usa los perfiles **de** permanencia para configurar los distintos umbrales.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>Requisitos previos

Estos elementos prefabs son variantes de los elementos HoloLens 2 prefabs de botones que se pueden presionar con estilo y que tienen componentes adicionales para admitir interacciones de permanencia.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

Estos elementos prefabs tienen un componente de placa trasera adicional **QuadDwellVisual** para visualizar el estado de entrada de permanencia. Tiene asignado el material **HolographicBackPlateDwellVisual.mat.** **ToggleDwellPressableButton.cs actualiza** la propiedad **_BorderWidth** del sombreador estándar de MRTK para visualizar la entrada de permanencia.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos en la `DwellExample` escena. En la escena de ejemplo se muestran ejemplos de interfaz de usuario volumétrica y ejemplos de interfaz de usuario de Unity.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Consulte también

- [**Botones**](button.md)
- [**Interactuable**](interactable.md)
