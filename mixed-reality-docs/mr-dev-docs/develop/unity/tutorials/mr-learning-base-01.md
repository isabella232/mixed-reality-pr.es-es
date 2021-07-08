---
title: Introducción a los tutoriales de MRTK
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta desde cero.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, solvers, eye-tracking, voice commands
ms.localizationpriority: high
ms.openlocfilehash: abee2163c3b92897396ea35cc43ae025e8e7b804
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175484"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="43b0f-104">1. Introducción a los tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="43b0f-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="43b0f-105">¡Le damos la bienvenida a la serie de tutoriales de introducción!</span><span class="sxs-lookup"><span data-stu-id="43b0f-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="43b0f-106">En el transcurso de estos tutoriales, aprenderá sobre Mixed Reality Toolkit (MRTK) y algunas de las características que ofrece.</span><span class="sxs-lookup"><span data-stu-id="43b0f-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="43b0f-107">También creará una experiencia de realidad mixta en la que el usuario podrá explorar un holograma basado en el vehículo explorador de Marte Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="43b0f-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="43b0f-108">Al final de esta serie, tendrá un buen dominio de MRTK y de cómo puede acelerar el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="43b0f-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="43b0f-109">Los tutoriales de esta serie están diseñados para realizarse de forma secuencial, por lo que debe repasarlos en el orden correcto:</span><span class="sxs-lookup"><span data-stu-id="43b0f-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="43b0f-110">[Introducción](mr-learning-base-01.md) (ya está aquí)</span><span class="sxs-lookup"><span data-stu-id="43b0f-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="43b0f-111">Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="43b0f-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="43b0f-112">Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="43b0f-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="43b0f-113">Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="43b0f-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="43b0f-114">Creación de contenido dinámico mediante solucionadores</span><span class="sxs-lookup"><span data-stu-id="43b0f-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="43b0f-115">Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="43b0f-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="43b0f-116">Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="43b0f-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="43b0f-117">Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="43b0f-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="43b0f-118">Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="43b0f-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="43b0f-119">Objetivos</span><span class="sxs-lookup"><span data-stu-id="43b0f-119">Objectives</span></span>

* <span data-ttu-id="43b0f-120">Aprender a configurar Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="43b0f-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="43b0f-121">Aprender a crear e implementar en su dispositivo</span><span class="sxs-lookup"><span data-stu-id="43b0f-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="43b0f-122">Aprender a usar algunas de las características importantes de MRTK</span><span class="sxs-lookup"><span data-stu-id="43b0f-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="43b0f-123">Crear una experiencia de realidad mixta completa</span><span class="sxs-lookup"><span data-stu-id="43b0f-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43b0f-124">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="43b0f-124">Prerequisites</span></span>

* <span data-ttu-id="43b0f-125">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="43b0f-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="43b0f-126">[SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) versión 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="43b0f-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="43b0f-127">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="43b0f-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="43b0f-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020.3 LTS o Unity 2019.4 LTS instalado **(OpenXR requiere 2020.3.8 o posterior para evitar errores**)</span><span class="sxs-lookup"><span data-stu-id="43b0f-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020.3 LTS or Unity 2019.4 LTS installed (**OpenXR requires 2020.3.8 or later to prevent bugs**)</span></span>

<span data-ttu-id="43b0f-129">Al instalar Unity, asegúrese de comprobar los siguientes componentes en **"Platforms"** (Plataformas).</span><span class="sxs-lookup"><span data-stu-id="43b0f-129">When installing Unity, please make sure to check following components under **'Platforms'**.</span></span>

* <span data-ttu-id="43b0f-130">**Compatibilidad con la compilación de la Plataforma universal de Windows**</span><span class="sxs-lookup"><span data-stu-id="43b0f-130">**Universal Windows Platform Build Support**</span></span>
* <span data-ttu-id="43b0f-131">**Compatibilidad con la compilación de Windows (IL2CPP)**</span><span class="sxs-lookup"><span data-stu-id="43b0f-131">**Windows Build Support (IL2CPP)**</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP.png" alt="Unity Universal Windows Platform Build Support option" width="600px">

<span data-ttu-id="43b0f-132">Si instaló Unity sin estas opciones, puede agregarlas mediante el menú **"Add Modules"** (Agregar módulos) de Unity Hub.</span><span class="sxs-lookup"><span data-stu-id="43b0f-132">If you installed Unity without these options, you can add them through **'Add Modules'** menu in Unity Hub.</span></span>

<img src="../../../develop/images/Unity_Install_Option_UWP2.png" alt="Unity Hub - Add Module" width="600px">

> [!Important]
> <span data-ttu-id="43b0f-133">La versión de MRTK recomendada para esta serie de tutoriales es MRTK 2.7.2.</span><span class="sxs-lookup"><span data-stu-id="43b0f-133">The recommended MRTK version for this tutorial series is MRTK 2.7.2</span></span>

> [!Important]
> <span data-ttu-id="43b0f-134">Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o el complemento de XR de Windows y también Unity 2019 LTS (actualmente 2019.4.x) si usa WSA heredado o el complemento de XR de Windows.</span><span class="sxs-lookup"><span data-stu-id="43b0f-134">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="43b0f-135">Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="43b0f-135">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43b0f-136">Tutorial siguiente: 2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="43b0f-136">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
