---
title: Visualización de dedo
description: Información general sobre la visualización de información sobre dedos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, dedo
ms.openlocfilehash: af23fdb9b618e276b7442405e54b7dccd141e4ee
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177535"
---
# <a name="fingertip-visualization"></a>Visualización de dedo

![Visualización de dedo principal](../images/fingertip/MRTK_FingertipVisualization_Main.png)

La asequibilidad de dedo ayuda al usuario a reconocer la distancia desde el objeto de destino. El objeto visual de forma de anillo ajusta su tamaño en función de la distancia entre el dedo y el objeto. La visualización de dedo se controla principalmente mediante `FingerCursor` (Assets/MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab) (y script) que se genera como el prefab del cursor de *la herramienta Delepointer.* Otros componentes de la visualización incluyen el script *ProximityLight* y *el sombreador MixedRealityStandard.*

## <a name="how-to-use-the-fingertip-visualization"></a>Uso de la visualización de dedo

De forma predeterminada, la visualización de dedo funcionará en cualquier escena de Unity que esté configurada para generar un FingerCursor. La generación de FingerCursor se produce en *DefaultMixedRealityToolkitConfigurationProfile* en:

*DefaultMixedRealityInputSystemProfile > DefaultMixedRealityInputPointerProfile > PokePointer > FingerCursor*

En un nivel alto, la visualización de dedo funciona mediante una luz de proximidad para proyectar un degradado de color en cualquier superficie cercana que acepte luces de proximidad. A continuación, el cursor del dedo busca cualquier superficie interactuable cercana, determinada por el elemento primario , para alinear el anillo de dedo con una superficie a medida que el dedo se mueve `IMixedRealityNearPointer(s)` hacia una superficie. A medida que un dedo se aproxima a una superficie, el anillo de dedo también se anima dinámicamente mediante las propiedades de redondeo del sombreador MixedRealityStandard.

## <a name="example-scene"></a>Escena de ejemplo

Puede encontrar ejemplos de visualización de dedo en casi cualquier escena que funcione con las manos articuladas, pero que sea destacada en la [escena HandInteractionExample](../example-scenes/hand-interaction-examples.md).

![Estados de visualización de dedo](../images/fingertip/MRTK_FingertipVisualization_States.png)

## <a name="inspector-properties"></a>Propiedades del inspector

**FingerCursor** Muchas de las propiedades del cursor de dedo se heredan de la clase de cursor base. Las propiedades importantes incluyen los márgenes y anchos de la superficie lejana o cercana que impulsan la animación de anillo de dedo en el sombreador MixedRealityStandard. Para otras propiedades, mantenga el puntero sobre las sugerencias de la herramienta inspector.

<img src="../images/fingertip/MRTK_FingertipVisualization_Finger_Cursor_Inspector.png" width="600" alt="Cursor Inspector">

**ProximityLight** La configuración de la luz de proximidad controla el aspecto de la luz cuando está cerca y lejos de una superficie. Los colores central, central y exterior controlan el aspecto degradado de la luz y se pueden personalizar para la paleta de colores de la aplicación. Tenga en cuenta que los colores son HDR (Alto rango dinámico) para permitir que los usuarios ilumen la luz de proximidad a los valores por encima de uno. Para otras propiedades, mantenga el puntero sobre las sugerencias de la herramienta inspector.

**MixedReality Sombreador estándar** El sombreador MixedRealityStandard se usa para muchos efectos en MRTK. Los dos valores importantes para la visualización de dedo son "Near Fade" y "Proximity Light". Near Fade permite que los objetos se desvanezzcan a medida que se acerca una cámara o una luz. Asegúrese de comprobar "Light" (Luz) para permitir que las luces de proximidad impulsen la atenuación (en lugar de la cámara). Puede invertir los valores de "Fade Begin" y "Fade Complete" para invertir un atenuación. Compruebe "Proximity Light" (Luz de proximidad) para ver cualquier superficie que le gustaría que la luz de proximidad se ilumen. Para otras propiedades, mantenga el puntero sobre las sugerencias de la herramienta inspector.

<img src="../images/fingertip/MRTK_FingertipVisualization_Mixed_Reality_Standard_Shader_Inspector.png" width="600" alt="Shader Inspector">
