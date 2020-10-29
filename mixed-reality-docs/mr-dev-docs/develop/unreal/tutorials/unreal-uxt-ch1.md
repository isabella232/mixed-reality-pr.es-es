---
title: 1. Introducción
description: Parte 1 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation
ms.openlocfilehash: 5c4ce7c50e252a7b52a1d2e29d47642cfcda6e10
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701163"
---
# <a name="1-getting-started"></a><span data-ttu-id="a6db7-104">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="a6db7-104">1. Getting started</span></span>

<span data-ttu-id="a6db7-105">Independientemente de que no esté familiarizado con la realidad virtual o que sea un profesional experimentado, aquí empieza su camino con [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) y [Unreal Engine](https://www.unrealengine.com/en-US/).</span><span class="sxs-lookup"><span data-stu-id="a6db7-105">Whether you're new to mixed reality or a seasoned pro, this is the place to start your journey with [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/).</span></span> <span data-ttu-id="a6db7-106">En esta serie de tutoriales se ofrece una guía paso a paso sobre cómo compilar una aplicación de ajedrez interactiva con el [complemento UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal), parte de [Mixed Reality Toolkit para Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span><span class="sxs-lookup"><span data-stu-id="a6db7-106">This tutorial series will give you a step by step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="a6db7-107">El complemento le ayudará a agregar características comunes de UX a sus proyectos con código, planos técnicos y ejemplos.</span><span class="sxs-lookup"><span data-stu-id="a6db7-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="a6db7-109">Al final de la serie tendrá experiencia práctica en las siguientes tareas:</span><span class="sxs-lookup"><span data-stu-id="a6db7-109">By the end of the series you'll have hands-on experience with:</span></span>
* <span data-ttu-id="a6db7-110">Inicio de un nuevo proyecto</span><span class="sxs-lookup"><span data-stu-id="a6db7-110">Starting a new project</span></span>
* <span data-ttu-id="a6db7-111">Configuración para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="a6db7-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="a6db7-112">Trabajo con la entrada de usuario</span><span class="sxs-lookup"><span data-stu-id="a6db7-112">Working with user input</span></span>
* <span data-ttu-id="a6db7-113">Adición de botones</span><span class="sxs-lookup"><span data-stu-id="a6db7-113">Adding buttons</span></span>
* <span data-ttu-id="a6db7-114">Reproducción en un emulador o un dispositivo</span><span class="sxs-lookup"><span data-stu-id="a6db7-114">Playing on an emulator or device</span></span>


## <a name="prerequisites"></a><span data-ttu-id="a6db7-115">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a6db7-115">Prerequisites</span></span>
<span data-ttu-id="a6db7-116">Asegúrese de haber instalado lo siguiente antes de empezar:</span><span class="sxs-lookup"><span data-stu-id="a6db7-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="a6db7-117">Windows 10 1809 o posterior</span><span class="sxs-lookup"><span data-stu-id="a6db7-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="a6db7-118">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="a6db7-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a6db7-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 o posterior</span><span class="sxs-lookup"><span data-stu-id="a6db7-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="a6db7-120">Un dispositivo Microsoft HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) o un emulador</span><span class="sxs-lookup"><span data-stu-id="a6db7-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="a6db7-121">Visual Studio 2019 con las cargas de trabajo siguientes</span><span class="sxs-lookup"><span data-stu-id="a6db7-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="a6db7-122">Instalación de Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="a6db7-122">Installing Visual Studio 2019</span></span>
<span data-ttu-id="a6db7-123">Hay algunos pasos que debe completar para asegurarse de que tiene todos los paquetes de Visual Studio necesarios:</span><span class="sxs-lookup"><span data-stu-id="a6db7-123">There are a few steps to ensure you have all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="a6db7-124">Instale la versión más reciente de [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="a6db7-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="a6db7-125">Instale las [cargas de trabajo](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads) siguientes:</span><span class="sxs-lookup"><span data-stu-id="a6db7-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="a6db7-126">Desarrollo de escritorio con C++</span><span class="sxs-lookup"><span data-stu-id="a6db7-126">Desktop development with C++</span></span>
    * <span data-ttu-id="a6db7-127">Desarrollo de escritorio de .NET</span><span class="sxs-lookup"><span data-stu-id="a6db7-127">.NET desktop development</span></span>
    * <span data-ttu-id="a6db7-128">Desarrollo con la Plataforma universal de Windows</span><span class="sxs-lookup"><span data-stu-id="a6db7-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="a6db7-129">Instale los [componentes](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components) siguientes:</span><span class="sxs-lookup"><span data-stu-id="a6db7-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="a6db7-130">Compiladores, herramientas de compilación y entornos en tiempo de ejecución > herramientas de desarrollo para ARM64 en C++ de MSVC v142 - VS 2019 (versión más reciente)</span><span class="sxs-lookup"><span data-stu-id="a6db7-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="a6db7-131">Eso es todo.</span><span class="sxs-lookup"><span data-stu-id="a6db7-131">That's it!</span></span> <span data-ttu-id="a6db7-132">Está listo para continuar e iniciar el proyecto de ajedrez.</span><span class="sxs-lookup"><span data-stu-id="a6db7-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="a6db7-133">Sección siguiente: 2. Inicialización del proyecto y primera aplicación</span><span class="sxs-lookup"><span data-stu-id="a6db7-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)