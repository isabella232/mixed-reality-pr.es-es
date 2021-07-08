---
title: Tutorial de babylon.js para preparar una escena con objetos 3D básicos
description: Aprenda a usar babylon.js y a agregar objetos 3D básicos a una escena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584514"
---
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="058b7-104">Tutorial: Preparación de una escena</span><span class="sxs-lookup"><span data-stu-id="058b7-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="058b7-105">Aprenda a preparar una escena y agregarle algunos elementos 3D básicos.</span><span class="sxs-lookup"><span data-stu-id="058b7-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="058b7-106">En este tutorial, aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="058b7-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="058b7-107">Crear una escena</span><span class="sxs-lookup"><span data-stu-id="058b7-107">Create a scene</span></span>
> * <span data-ttu-id="058b7-108">Agregar una cámara</span><span class="sxs-lookup"><span data-stu-id="058b7-108">Add a camera</span></span>
> * <span data-ttu-id="058b7-109">Agregar luz</span><span class="sxs-lookup"><span data-stu-id="058b7-109">Add light</span></span>
> * <span data-ttu-id="058b7-110">Agregar elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="058b7-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="058b7-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="058b7-111">Before you begin</span></span>

<span data-ttu-id="058b7-112">En el paso anterior del tutorial, se creó una página web básica.</span><span class="sxs-lookup"><span data-stu-id="058b7-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="058b7-113">Abra la página web para su edición.</span><span class="sxs-lookup"><span data-stu-id="058b7-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="058b7-114">Creación una escena</span><span class="sxs-lookup"><span data-stu-id="058b7-114">Create a scene</span></span>

<span data-ttu-id="058b7-115">Una escena es donde se mostrará todo el contenido.</span><span class="sxs-lookup"><span data-stu-id="058b7-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="058b7-116">Puede haber varias escenas, y es posible cambiar entre una escena y otra.</span><span class="sxs-lookup"><span data-stu-id="058b7-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="058b7-117">Lea más sobre [Scene de babylon.js](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="058b7-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="058b7-118">Agregue la etiqueta de script después del elemento HTML de lienzo (canvas), y agregue el código siguiente para crear una escena rellena de color negro:</span><span class="sxs-lookup"><span data-stu-id="058b7-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    <span data-ttu-id="058b7-119">En el código anterior, tenemos que crear una instancia del motor de representación web de babylon.js que represente una escena y enlace eventos en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="058b7-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="058b7-120">Para más información sobre el motor, consulte la página de documentación de [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine).</span><span class="sxs-lookup"><span data-stu-id="058b7-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="058b7-121">La escena no se representa de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="058b7-121">The scene is not rendered by default.</span></span> <span data-ttu-id="058b7-122">Recuerde que puede haber varias escenas y que usted controla qué escena se muestra.</span><span class="sxs-lookup"><span data-stu-id="058b7-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="058b7-123">Para representar la escena repetidamente en cada fotograma, ejecute el código siguiente después de la llamada a la función *createScene*:</span><span class="sxs-lookup"><span data-stu-id="058b7-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="058b7-124">Adición de elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="058b7-124">Add basic 3D element</span></span>

1. <span data-ttu-id="058b7-125">Vamos a agregar la primera forma 3D.</span><span class="sxs-lookup"><span data-stu-id="058b7-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="058b7-126">En el mundo virtual 3D, las formas se construyen a partir de *mallas*, muchas facetas triangulares unidas, donde cada faceta está compuesta a partir de tres vértices.</span><span class="sxs-lookup"><span data-stu-id="058b7-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="058b7-127">Puede usar una malla predefinida o crear su propia malla personalizada.</span><span class="sxs-lookup"><span data-stu-id="058b7-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="058b7-128">Aquí usaremos una malla de cuadro predefinida, es decir, un cubo.</span><span class="sxs-lookup"><span data-stu-id="058b7-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="058b7-129">Para crear el cuadro, use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="058b7-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="058b7-130">Los parámetros son el nombre y las opciones (las opciones son diferentes según el tipo de malla).</span><span class="sxs-lookup"><span data-stu-id="058b7-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="058b7-131">Anexe el código siguiente a la función *createScene*:</span><span class="sxs-lookup"><span data-stu-id="058b7-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="058b7-132">Abra la página web en el explorador Microsoft Edge y compruebe la salida.</span><span class="sxs-lookup"><span data-stu-id="058b7-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="058b7-133">La ventana del explorador muestra una página en blanco.</span><span class="sxs-lookup"><span data-stu-id="058b7-133">The browser window shows a blank page.</span></span> <span data-ttu-id="058b7-134">Abra DevTools con el teclado y seleccione F12, Control+Mayús+I (Windows, Linux) o Comando+Opción+I (macOS).</span><span class="sxs-lookup"><span data-stu-id="058b7-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="058b7-135">Después de abrir la pestaña *Consola*, puede empezar a buscar errores.</span><span class="sxs-lookup"><span data-stu-id="058b7-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="058b7-136">Aparecerá un error: "Uncaught Error: No camera defined" (Error no detectado: No hay definida ninguna cámara).</span><span class="sxs-lookup"><span data-stu-id="058b7-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="058b7-137">Ahora tenemos que agregar una cámara a la escena.</span><span class="sxs-lookup"><span data-stu-id="058b7-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="058b7-138">Agregar una cámara</span><span class="sxs-lookup"><span data-stu-id="058b7-138">Add a camera</span></span>

1. <span data-ttu-id="058b7-139">Para ver el mundo virtual e interactuar con él, tiene que haber una cámara conectada al lienzo.</span><span class="sxs-lookup"><span data-stu-id="058b7-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="058b7-140">Vamos a agregar la cámara de tipo [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que se puede girar alrededor de un destino.</span><span class="sxs-lookup"><span data-stu-id="058b7-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="058b7-141">Los parámetros necesarios para crear una instancia de la cámara son:</span><span class="sxs-lookup"><span data-stu-id="058b7-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="058b7-142">**name**: Nombre de la cámara.</span><span class="sxs-lookup"><span data-stu-id="058b7-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="058b7-143">**alpha**: Posición angular a lo largo del eje longitudinal (en radianes).</span><span class="sxs-lookup"><span data-stu-id="058b7-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="058b7-144">**beta**: Posición angular a lo largo del eje latitudinal (en radianes).</span><span class="sxs-lookup"><span data-stu-id="058b7-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="058b7-145">**radius**: Distancia desde el destino.</span><span class="sxs-lookup"><span data-stu-id="058b7-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="058b7-146">**target**: Punto hacia el que siempre se enfrentaría la cámara (definido por coordenadas x-y-z).</span><span class="sxs-lookup"><span data-stu-id="058b7-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="058b7-147">**scene**: Escena en la que se encuentra la cámara.</span><span class="sxs-lookup"><span data-stu-id="058b7-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="058b7-148">Alpha, beta, radius y target, en su conjunto, definen la posición de la cámara en el espacio, como se muestra en el diagrama siguiente:</span><span class="sxs-lookup"><span data-stu-id="058b7-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Alpha Beta Radius de la cámara](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="058b7-150">Agregue el código siguiente a la función *createScene*:</span><span class="sxs-lookup"><span data-stu-id="058b7-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="058b7-151">Si comprueba la salida en el explorador, verá un lienzo negro.</span><span class="sxs-lookup"><span data-stu-id="058b7-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="058b7-152">Nos falta la luz.</span><span class="sxs-lookup"><span data-stu-id="058b7-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="058b7-153">Adición de luz</span><span class="sxs-lookup"><span data-stu-id="058b7-153">Add light</span></span>

1. <span data-ttu-id="058b7-154">Hay cuatro tipos de luces que se pueden usar con una variedad de propiedades de iluminación: luz puntual, direccional, angular y hemisférica.</span><span class="sxs-lookup"><span data-stu-id="058b7-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="058b7-155">Vamos a agregar la luz ambiente [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="058b7-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="058b7-156">El código final de la página web tendrá el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="058b7-156">The final code of the web page will look as follows:</span></span>

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="058b7-157">Compruebe la salida en el explorador.</span><span class="sxs-lookup"><span data-stu-id="058b7-157">Check the output in the browser.</span></span> <span data-ttu-id="058b7-158">Debería ver el cubo y, con el mouse, puede girar la cámara alrededor del cubo y ver las distintas caras del cubo:</span><span class="sxs-lookup"><span data-stu-id="058b7-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Escena básica con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="058b7-160">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="058b7-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="058b7-161">Siguiente tutorial: 3. Interacción con un objeto 3D</span><span class="sxs-lookup"><span data-stu-id="058b7-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)
