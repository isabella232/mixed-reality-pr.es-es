---
title: Introducción a los tutoriales de MRTK
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta desde cero.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, solvers, eye-tracking, voice commands
ms.localizationpriority: high
ms.openlocfilehash: 27a5f2cae4f08fbc142c8b872c22d23ab41cdc62
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008085"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="b18ce-104">1. Introducción a los tutoriales de MRTK</span><span class="sxs-lookup"><span data-stu-id="b18ce-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="b18ce-105">¡Le damos la bienvenida a la serie de tutoriales de introducción!</span><span class="sxs-lookup"><span data-stu-id="b18ce-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="b18ce-106">En el transcurso de estos tutoriales, aprenderá sobre Mixed Reality Toolkit (MRTK) y algunas de las características que ofrece.</span><span class="sxs-lookup"><span data-stu-id="b18ce-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="b18ce-107">También creará una experiencia de realidad mixta en la que el usuario podrá explorar un holograma basado en el vehículo explorador de Marte Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="b18ce-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="b18ce-108">Al final de esta serie, tendrá un buen dominio de MRTK y de cómo puede acelerar el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="b18ce-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="b18ce-109">Los tutoriales de esta serie están diseñados para realizarse de forma secuencial, por lo que debe repasarlos en el orden correcto:</span><span class="sxs-lookup"><span data-stu-id="b18ce-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="b18ce-110">[Introducción](mr-learning-base-01.md) (ya está aquí)</span><span class="sxs-lookup"><span data-stu-id="b18ce-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="b18ce-111">Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="b18ce-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="b18ce-112">Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="b18ce-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="b18ce-113">Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="b18ce-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="b18ce-114">Creación de contenido dinámico mediante solucionadores</span><span class="sxs-lookup"><span data-stu-id="b18ce-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="b18ce-115">Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="b18ce-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="b18ce-116">Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="b18ce-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="b18ce-117">Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="b18ce-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="b18ce-118">Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="b18ce-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="b18ce-119">Objetivos</span><span class="sxs-lookup"><span data-stu-id="b18ce-119">Objectives</span></span>

* <span data-ttu-id="b18ce-120">Aprender a configurar Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="b18ce-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="b18ce-121">Aprender a crear e implementar en su dispositivo</span><span class="sxs-lookup"><span data-stu-id="b18ce-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="b18ce-122">Aprender a usar algunas de las características importantes de MRTK</span><span class="sxs-lookup"><span data-stu-id="b18ce-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="b18ce-123">Crear una experiencia de realidad mixta completa</span><span class="sxs-lookup"><span data-stu-id="b18ce-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b18ce-124">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b18ce-124">Prerequisites</span></span>

* <span data-ttu-id="b18ce-125">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="b18ce-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="b18ce-126">[SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) versión 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="b18ce-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="b18ce-127">Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="b18ce-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="b18ce-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="b18ce-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="b18ce-129">La versión de MRTK recomendada para esta serie de tutoriales es MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="b18ce-129">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="b18ce-130">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="b18ce-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="b18ce-131">Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b18ce-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b18ce-132">Tutorial siguiente: 2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="b18ce-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)

