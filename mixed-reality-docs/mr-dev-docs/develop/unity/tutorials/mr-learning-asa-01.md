---
title: Introducción a los tutoriales sobre Azure Spatial Anchors
description: Siga este curso para aprender a implementar Azure Spatial Anchors en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, ios, android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 613aa50e1cfaadcf245b719d5a846f35e9e6159e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "101883370"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Introducción a los tutoriales sobre Azure Spatial Anchors

Le damos la bienvenida a los tutoriales sobre Azure Spatial Anchors. En esta serie de tutoriales, aprenderá los aspectos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) y cómo anclar una experiencia de realidad mixta completa en el mundo real. También aprenderá a implementar el proyecto en iOS y Android.

Tutoriales de esta serie:

1. [Introducción](mr-learning-asa-01.md) (ya está aquí)
2. [Introducción a Azure Spatial Anchors](mr-learning-asa-02.md)
3. [Almacenamiento, recuperación y uso compartido de Azure Spatial Anchors](mr-learning-asa-03.md)
4. [Visualización de comentarios de Azure Spatial Anchors](mr-learning-asa-04.md)
5. [Azure Spatial Anchors para iOS y Android](mr-learning-asa-05.md)

## <a name="objectives"></a>Objetivos

* Aprender a crear anclajes espaciales y a capturarlos desde Azure
* Aprender a lograr la alineación espacial entre sesiones de una aplicación
* Aprender a lograr la alineación espacial entre varios dispositivos
* Aprender a preparar, compilar e implementar el proyecto en iOS y Android

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)
* Windows 10, SDK 10.0.18362.0 o una versión posterior
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado
* Haber completado la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).
* Haber finalizado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK.
* Si va a realizar la implementación en Android y en HoloLens
  * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de Android agregado
* Si va a realizar la implementación en iOS y en HoloLens
  * Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a>
  * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de iOS agregado

> [!CAUTION]
> La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.6.

> [!CAUTION]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019 LTS. Esto sustituye cualquier requisito de versión de Unity indicado en los requisitos previos vinculados más arriba.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 2. Introducción a Azure Spatial Anchors](mr-learning-asa-02.md)
