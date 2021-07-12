---
ms.openlocfilehash: eaa2651a22fd5b2b601493845d507aeda6745f1a
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603721"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

El Mixed Reality complemento OpenXR es la recomendación de **Microsoft** para **Unity 2020 LTS** o posterior. A medida que se desarrollan nuevas características en el futuro, solo se incluirán en el Mixed Reality complemento OpenXR en el futuro.

El Mixed Reality complemento OpenXR es totalmente compatible con AR Foundation 4.0, lo que proporciona implementaciones de ARPlaneManager y ARRaycastManager. Esto le permite escribir código de difusión por rayos una vez que, a continuación, HoloLens 2 teléfonos y tabletas ARCore/ARKit.

### <a name="prerequisites"></a>Requisitos previos 

* Herramientas [más recientes para HoloLens 2 desarrollo](../../../install-the-tools.md?tabs=unity#installation-checklist)
* Versión más reciente de Unity 2020.3 LTS: versión 2020.3.8f1 o posterior

### <a name="recommended-package-versions"></a>Versiones de paquete recomendadas

Las instrucciones de esta página le configurarán con los paquetes principales de Unity OpenXR necesarios para implementar HoloLens 2 o Windows Mixed Reality aplicaciones:

* Complemento OpenXR de Unity: versión 1.2 o posterior
* Mixed Reality complemento OpenXR: versión 1.0.0 o posterior

Si usa los siguientes paquetes en el proyecto, deberá asegurarse de usar al menos las versiones mínimas enumeradas a continuación:

* MRTK: versión 2.7.2 o posterior
* AR Foundation: versión 4.1.1 o posterior
* Canalización de representación universal (URP): versión 10.5.1 o posterior
* Azure Spatial Anchors: versión 2.10 o posterior
* Azure Remote Rendering: versión 1.0.15 o posterior

> [!NOTE]
> Si va a compilar aplicaciones vr en Windows pc, Mixed Reality complemento OpenXR no es estrictamente necesario. Sin embargo, querrá instalar el complemento si va a configurar enlaces de entrada para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de HoloLens 2 y VR.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Microsoft no recomienda usar el complemento Windows XR para proyectos nuevos en Unity 2020.  En su lugar, debe usar Mixed Reality complemento OpenXR.

Sin embargo, si usa Unity 2019 y necesita AR Foundation 2.0 para la compatibilidad con dispositivos ARCore/ARKit, este complemento habilita esa compatibilidad.

> [!IMPORTANT]
> El uso de este complemento en Unity 2019 no es compatible con Azure Spatial Anchors.

# <a name="legacy-xr"></a>[XR heredado](#tab/legacy)

Si todavía está en **Unity 2019** o versiones anteriores, Microsoft recomienda usar la compatibilidad con **XR integrada heredada.**

Aunque el Windows XR es funcional en Unity 2019, no se recomienda porque este complemento no es compatible con Azure Spatial Anchors en Unity 2019.

Si va a iniciar un nuevo proyecto, se recomienda instalar [Unity 2020](../../choosing-unity-version.md) en su lugar y usar Mixed Reality complemento OpenXR.