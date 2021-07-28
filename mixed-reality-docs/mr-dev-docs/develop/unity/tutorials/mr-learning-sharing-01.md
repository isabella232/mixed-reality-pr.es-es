---
title: Introducción a los tutoriales sobre las funcionalidades multiusuario
description: Complete este curso para aprender a implementar experiencias multiusuario compartidas en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, multi-user capabilities, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: dc8f495bc620eca3539b48f38fa15d089c0e28f4
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702456"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Introducción a los tutoriales sobre las funcionalidades multiusuario

¡Le damos la bienvenida a los tutoriales sobre las funcionalidades multiusuario! A lo largo de esta serie de tutoriales aprenderá los aspectos básicos de la creación de una experiencia multiusuario mediante <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN es una de las diversas opciones de redes disponibles para que los desarrolladores de realidad mixta creen experiencias compartidas.

Tutoriales de esta serie:

* [Configuración de Photon Unity Networking](mr-learning-sharing-02.md)
* [Conexión de varios usuarios](mr-learning-sharing-03.md)
* [Uso compartido de movimientos de objetos con varios usuarios](mr-learning-sharing-04.md)
* [Integración de Azure Spatial Anchors en una experiencia compartida](mr-learning-sharing-05.md)

## <a name="objectives"></a>Objetivos

* Aprender a crear una aplicación de PUN y conectarla al proyecto de Unity
* Aprender a conectar varios usuarios en una experiencia compartida
* Aprender a compartir los movimientos de objetos con otros usuarios
* Aprender a lograr la alineación espacial entre varios dispositivos

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas adecuadas instaladas](../../install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado.
* Haber completado la sección [Creación de un recurso de Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Haber completado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK
* Haber completado la serie de [tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) o contar con experiencia previa en la creación de una cuenta de Azure Spatial Anchors
* Si va a realizar la implementación en Android y en HoloLens
  * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020 LTS instalado y el módulo de compatibilidad con la compilación de Android agregado.
* Si va a realizar la implementación en iOS y en HoloLens
  * Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
  * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020 LTS instalado y el módulo de compatibilidad con la compilación de iOS agregado.

> [!IMPORTANT]
> La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.7.

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2020 LTS. Esta sustituye los requisitos de versión de Unity descritos en los requisitos previos vinculados anteriormente.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 2. Configuración de Photon Unity Networking](mr-learning-sharing-02.md)