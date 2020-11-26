---
title: 'Tutoriales sobre Azure Spatial Anchors: 1. Introducción a los tutoriales sobre Azure Spatial Anchors'
description: Siga este curso para aprender a implementar Azure Spatial Anchors en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, ios, android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 005bbf3f9ecb7ed7f15f78d4042b4090f00edca7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679404"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="c56e7-105">1. Introducción a los tutoriales sobre Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c56e7-105">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

## <a name="overview"></a><span data-ttu-id="c56e7-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="c56e7-106">Overview</span></span>

<span data-ttu-id="c56e7-107">Le damos la bienvenida a los tutoriales sobre Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="c56e7-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="c56e7-108">En esta serie de tutoriales, aprenderá los aspectos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) y cómo anclar una experiencia de realidad mixta completa en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="c56e7-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="c56e7-109">También aprenderá a implementar el proyecto en iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="c56e7-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="c56e7-110">Tutoriales de esta serie:</span><span class="sxs-lookup"><span data-stu-id="c56e7-110">Tutorials in this series:</span></span>

1. <span data-ttu-id="c56e7-111">[Introducción](mr-learning-asa-01.md) (ya está aquí)</span><span class="sxs-lookup"><span data-stu-id="c56e7-111">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="c56e7-112">Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c56e7-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="c56e7-113">Almacenamiento, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c56e7-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="c56e7-114">Visualización de comentarios de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c56e7-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="c56e7-115">Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="c56e7-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="c56e7-116">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c56e7-116">Objectives</span></span>

* <span data-ttu-id="c56e7-117">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="c56e7-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="c56e7-118">Aprender a lograr la alineación espacial entre sesiones de una aplicación</span><span class="sxs-lookup"><span data-stu-id="c56e7-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="c56e7-119">Aprender a lograr la alineación espacial entre varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="c56e7-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="c56e7-120">Aprender a preparar, compilar e implementar el proyecto en iOS y Android</span><span class="sxs-lookup"><span data-stu-id="c56e7-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c56e7-121">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c56e7-121">Prerequisites</span></span>

* <span data-ttu-id="c56e7-122">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="c56e7-122">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="c56e7-123">Windows 10, SDK 10.0.18362.0 o una versión posterior</span><span class="sxs-lookup"><span data-stu-id="c56e7-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="c56e7-124">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="c56e7-124">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="c56e7-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="c56e7-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="c56e7-126">Haber completado la sección [Creación de un recurso de Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="c56e7-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="c56e7-127">Haber finalizado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK.</span><span class="sxs-lookup"><span data-stu-id="c56e7-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="c56e7-128">Si va a realizar la implementación en Android y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="c56e7-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="c56e7-129">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="c56e7-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="c56e7-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de Android agregado</span><span class="sxs-lookup"><span data-stu-id="c56e7-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="c56e7-131">Si va a realizar la implementación en iOS y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="c56e7-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="c56e7-132">Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="c56e7-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="c56e7-133">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS</span><span class="sxs-lookup"><span data-stu-id="c56e7-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="c56e7-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad con la compilación de iOS agregado</span><span class="sxs-lookup"><span data-stu-id="c56e7-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="c56e7-135">La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="c56e7-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="c56e7-136">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="c56e7-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="c56e7-137">Esta sustituye los requisitos de versión de Unity descritos en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c56e7-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c56e7-138">Tutorial siguiente: 2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="c56e7-138">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
