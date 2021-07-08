---
title: Tutoriales de introducción a babylon.js y WebXR
description: Complete este curso para aprender a usar babylon.js y crear una aplicación básica de realidad mixta.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600124"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="f2c8d-104">Tutorial: Creación de la primera aplicación WebXR mediante babylon.js</span><span class="sxs-lookup"><span data-stu-id="f2c8d-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="f2c8d-105">En este tutorial verá cómo crear una aplicación básica de realidad mixta mediante babylon.js y Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="f2c8d-106">La aplicación que va a compilar representará un cubo, le permitirá girarlo para poder ver las otras caras, y agregar interacciones.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="f2c8d-107">En este tutorial aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="f2c8d-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="f2c8d-108">Configurar entorno de desarrollo</span><span class="sxs-lookup"><span data-stu-id="f2c8d-108">Set up a development environment</span></span>
> * <span data-ttu-id="f2c8d-109">Usar la API babylon.js para crear elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="f2c8d-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="f2c8d-110">Crear una nueva página web</span><span class="sxs-lookup"><span data-stu-id="f2c8d-110">Create a new web page</span></span>
> * <span data-ttu-id="f2c8d-111">Interactuar con elementos 3D</span><span class="sxs-lookup"><span data-stu-id="f2c8d-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="f2c8d-112">Ejecutar la aplicación en un simulador de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f2c8d-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f2c8d-113">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="f2c8d-113">Prerequisites</span></span>

* <span data-ttu-id="f2c8d-114">Explorador compatible con WebXR, por ejemplo, [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span><span class="sxs-lookup"><span data-stu-id="f2c8d-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="f2c8d-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o superior</span><span class="sxs-lookup"><span data-stu-id="f2c8d-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="f2c8d-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="f2c8d-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="f2c8d-117">Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) si desea usar un simulador de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f2c8d-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="f2c8d-118">Opcional: [Simulador de Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="f2c8d-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="f2c8d-119">Introducción</span><span class="sxs-lookup"><span data-stu-id="f2c8d-119">Getting started</span></span>

<span data-ttu-id="f2c8d-120">Para crear este proyecto desde cero, comience con un proyecto de Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="f2c8d-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="f2c8d-121">No es obligatorio usar VSCode, pero lo usaremos para mayor practicidad a lo largo del tutorial.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="f2c8d-122">Los desarrolladores de JavaScript más experimentados pueden usar cualquier otro editor de su elección, incluso el más sencillo Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="f2c8d-123">Descargue el archivo único [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) o use una versión en línea que se puede encontrar en el [sitio web oficial de babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span><span class="sxs-lookup"><span data-stu-id="f2c8d-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="f2c8d-124">También puede clonar todo el proyecto de babylon.js desde [GitHub](https://github.com/BabylonJS/Babylon.js).</span><span class="sxs-lookup"><span data-stu-id="f2c8d-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="f2c8d-125">Cree un archivo vacío y guárdelo como página HTML, por ejemplo, index.html.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="f2c8d-126">Cree un marcado HTML básico y haga referencia al archivo de JavaScript babylon.js.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="f2c8d-127">El código final se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="f2c8d-127">The final code is as shown below:</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. <span data-ttu-id="f2c8d-128">Agregue un elemento HTML *canvas* dentro del cuerpo para representar el contenido de babylon.js.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="f2c8d-129">Tenga en cuenta que canvas tiene un atributo id, lo que le permite acceder a este elemento HTML desde JavaScript más adelante.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. <span data-ttu-id="f2c8d-130">Canvas ocupa toda la página web.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="f2c8d-131">Con esto se completa nuestra página web.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-131">That completes our web page.</span></span> <span data-ttu-id="f2c8d-132">Llegados a este punto, la página web está lista.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-132">At this point, the web page is ready.</span></span> <span data-ttu-id="f2c8d-133">Puede abrirla en cualquier explorador y asegurarse de que no aparezca ningún error, aunque todavía no hay ninguna experiencia envolvente.</span><span class="sxs-lookup"><span data-stu-id="f2c8d-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f2c8d-134">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="f2c8d-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f2c8d-135">Siguiente tutorial siguiente: 2. Preparación de una escena</span><span class="sxs-lookup"><span data-stu-id="f2c8d-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)