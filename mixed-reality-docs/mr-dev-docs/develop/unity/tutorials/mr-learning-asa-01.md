---
title: Introducción a los tutoriales sobre Azure Spatial Anchors
description: Siga este curso para aprender a implementar Azure Spatial Anchors en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, ios, android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 263575653df8fe22f2c59a00443d788c6598721b
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550345"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="a99d3-104">1. Introducción a los tutoriales sobre Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a99d3-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="a99d3-105">Le damos la bienvenida a los tutoriales sobre Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="a99d3-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="a99d3-106">En esta serie de tutoriales, aprenderá los aspectos básicos de <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) y cómo anclar una experiencia de realidad mixta completa en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="a99d3-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="a99d3-107">También aprenderá a implementar el proyecto en iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="a99d3-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="a99d3-108">Tutoriales de esta serie:</span><span class="sxs-lookup"><span data-stu-id="a99d3-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="a99d3-109">[Introducción](mr-learning-asa-01.md) (ya está aquí)</span><span class="sxs-lookup"><span data-stu-id="a99d3-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="a99d3-110">Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a99d3-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="a99d3-111">Almacenamiento, recuperación y uso compartido de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a99d3-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="a99d3-112">Visualización de comentarios de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a99d3-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="a99d3-113">Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="a99d3-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="a99d3-114">Objetivos</span><span class="sxs-lookup"><span data-stu-id="a99d3-114">Objectives</span></span>

* <span data-ttu-id="a99d3-115">Aprender a crear anclajes espaciales y a capturarlos desde Azure</span><span class="sxs-lookup"><span data-stu-id="a99d3-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="a99d3-116">Aprender a lograr la alineación espacial entre sesiones de una aplicación</span><span class="sxs-lookup"><span data-stu-id="a99d3-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="a99d3-117">Aprender a lograr la alineación espacial entre varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="a99d3-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="a99d3-118">Aprender a preparar, compilar e implementar el proyecto en iOS y Android</span><span class="sxs-lookup"><span data-stu-id="a99d3-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a99d3-119">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a99d3-119">Prerequisites</span></span>

* <span data-ttu-id="a99d3-120">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="a99d3-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="a99d3-121">Windows 10, SDK 10.0.18362.0 o una versión posterior</span><span class="sxs-lookup"><span data-stu-id="a99d3-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="a99d3-122">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="a99d3-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a99d3-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="a99d3-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="a99d3-124">Haber completado la sección [Creación de un recurso de Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) del tutorial [Inicio rápido: Creación de una aplicación de HoloLens en Unity que usa Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens).</span><span class="sxs-lookup"><span data-stu-id="a99d3-124">Completed the [Create a Spatial Anchors resource](/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="a99d3-125">Haber finalizado la serie de [tutoriales de introducción](mr-learning-base-01.md) o contar con experiencia previa básica en el uso de Unity y MRTK.</span><span class="sxs-lookup"><span data-stu-id="a99d3-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="a99d3-126">Si va a realizar la implementación en Android y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="a99d3-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="a99d3-127">Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">habilitado para desarrollo</a> y <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">compatible con ARCore</a>, con conexión USB a tu equipo Windows o macOS</span><span class="sxs-lookup"><span data-stu-id="a99d3-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="a99d3-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de Android agregado</span><span class="sxs-lookup"><span data-stu-id="a99d3-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="a99d3-129">Si va a realizar la implementación en iOS y en HoloLens</span><span class="sxs-lookup"><span data-stu-id="a99d3-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="a99d3-130">Un equipo macOS que tenga instalada la última versión de <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> y <a href="https://cocoapods.org" target="_blank">CocoaPods</a></span><span class="sxs-lookup"><span data-stu-id="a99d3-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="a99d3-131">Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatible con ARKit</a>, con conexión USB a tu equipo macOS</span><span class="sxs-lookup"><span data-stu-id="a99d3-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="a99d3-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de iOS agregado</span><span class="sxs-lookup"><span data-stu-id="a99d3-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="a99d3-133">La versión de Mixed Reality Toolkit recomendada para esta serie de tutoriales es MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="a99d3-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.6.</span></span>

> [!CAUTION]
> <span data-ttu-id="a99d3-134">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019 LTS. Esto sustituye cualquier requisito de versión de Unity indicado en los requisitos previos vinculados más arriba.</span><span class="sxs-lookup"><span data-stu-id="a99d3-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a99d3-135">Tutorial siguiente: 2. Introducción a Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="a99d3-135">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)