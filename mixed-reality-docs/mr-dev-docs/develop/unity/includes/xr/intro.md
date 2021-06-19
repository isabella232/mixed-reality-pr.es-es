---
ms.openlocfilehash: ca3589364fb27c3f8087572113f09e48d30e087e
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394579"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

El Mixed Reality complemento OpenXR es la recomendación **de Microsoft** para Unity 2020 LTS o posterior. A medida que se desarrollan nuevas características en el futuro, solo se incluirán en el Mixed Reality complemento OpenXR en el futuro.

El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager. Esto le permite escribir código de difusión por rayos una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.

### <a name="prerequisites"></a>Requisitos previos 

* Herramientas [más recientes para HoloLens 2 desarrollo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)
* Versión más reciente de Unity 2020.3 LTS(se recomienda 2020.3.8f1 o superior)

### <a name="minimum-versions"></a>Versiones mínimas

Las instrucciones de esta página le configurarán con los requisitos más recientes y más importantes de Unity y OpenXR que se enumeran a continuación:

* Complemento OpenXR de Unity más reciente (se recomienda la versión 1.2 o posterior)
* Versión Mixed Reality complemento OpenXR(se recomienda la versión 1.0.0 o posterior)
* **(Opcional)** MRTK más reciente, (se recomienda la versión 2.7 o posterior)
* **(Opcional)** Paquete de canalización de representación universal más reciente (se recomienda la versión 10.5.1 o posterior)

<!-- ![Screenshot of the open xr unity basic sample running on a HoloLens](../../images/openxr-example.png) -->

> [!NOTE]
> Si va a compilar aplicaciones de realidad virtual en pc Windows, Mixed Reality complemento OpenXR no es necesariamente necesario. Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.

# <a name="windows-xr"></a>[Windows XR](#tab/windowsxr)

Microsoft no recomienda usar el complemento XR de Windows para proyectos nuevos en Unity 2020.

Sin embargo, si usa Unity 2019 y necesita AR Foundation 2.0 para la compatibilidad con dispositivos ARCore/ARKit, este complemento habilita esa compatibilidad.

> [!IMPORTANT]
> El uso de este complemento en Unity 2019 no admite Azure Spatial Anchors. 

# <a name="legacy-xr"></a>[XR heredado](#tab/legacy)

Si todavía está en Unity 2019 o versiones anteriores, Microsoft recomienda usar la compatibilidad con XR integrada heredada. Aunque el complemento XR de Windows es funcional en Unity 2019, no se recomienda porque azure Spatial Anchors no se admite.