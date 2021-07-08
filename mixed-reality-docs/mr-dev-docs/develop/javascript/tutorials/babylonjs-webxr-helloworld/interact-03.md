---
title: Tutorial de babylon.js para interactuar con objetos 3D
description: Aprenda a usar babylon.js y a interactuar con objetos 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: a3dbab0572cd50105dac3d877a0d72c5cbc504b6
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584524"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="ff07a-104">Tutorial: Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="ff07a-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="ff07a-105">Aprenda a crear objetos 3D e interacciones para una experiencia de realidad mixta mediante babylon.js.</span><span class="sxs-lookup"><span data-stu-id="ff07a-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="ff07a-106">En esta sección, comenzará con algo sencillo, como pintar las caras de un cubo cuando selecciona el objeto.</span><span class="sxs-lookup"><span data-stu-id="ff07a-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="ff07a-107">En este tutorial se tratan los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="ff07a-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ff07a-108">Adición de interacciones</span><span class="sxs-lookup"><span data-stu-id="ff07a-108">How to add interactions</span></span>
> * <span data-ttu-id="ff07a-109">Habilitación del modo envolvente de WebXR</span><span class="sxs-lookup"><span data-stu-id="ff07a-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="ff07a-110">Ejecución de la aplicación en el simulador de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ff07a-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="ff07a-111">Ejecución y depuración de la aplicación en Android Chrome</span><span class="sxs-lookup"><span data-stu-id="ff07a-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="ff07a-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="ff07a-112">Before you begin</span></span>

<span data-ttu-id="ff07a-113">En el paso anterior del tutorial, se creó una página web básica con una escena.</span><span class="sxs-lookup"><span data-stu-id="ff07a-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="ff07a-114">Abra la página web de hospedaje para su edición.</span><span class="sxs-lookup"><span data-stu-id="ff07a-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="ff07a-115">Adición de una interacción</span><span class="sxs-lookup"><span data-stu-id="ff07a-115">Add interaction</span></span>

1. <span data-ttu-id="ff07a-116">En primer lugar, vamos a actualizar el código que crea el cubo, para que el cubo esté pintado con un color aleatorio.</span><span class="sxs-lookup"><span data-stu-id="ff07a-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="ff07a-117">Para ello, agregaremos [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) al cubo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="ff07a-118">El material nos permite especificar el color y las texturas, y se puede usar para cubrir otros objetos.</span><span class="sxs-lookup"><span data-stu-id="ff07a-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="ff07a-119">La manera en que aparece un material depende de la o las luces que se usan en la escena y de cómo está configurado para reaccionar.</span><span class="sxs-lookup"><span data-stu-id="ff07a-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="ff07a-120">Por ejemplo, diffuseColor distribuye el color por toda la malla a la que está asociada.</span><span class="sxs-lookup"><span data-stu-id="ff07a-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="ff07a-121">Agregue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="ff07a-122">Ahora que el cubo está pintado con un color aleatorio, vamos a agregar una interacción para lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="ff07a-123">Cambiar el color al hacer clic en el cubo</span><span class="sxs-lookup"><span data-stu-id="ff07a-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="ff07a-124">Mover el cubo después de que cambia de color</span><span class="sxs-lookup"><span data-stu-id="ff07a-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="ff07a-125">Para agregar interacciones, debemos usar [action](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="ff07a-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="ff07a-126">Una acción se inicia en respuesta al desencadenador de eventos.</span><span class="sxs-lookup"><span data-stu-id="ff07a-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="ff07a-127">Por ejemplo, cuando el usuario hace clic en el cubo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="ff07a-128">Todo lo que tenemos que hacer es crear una instancia de BABYLON.ActionManager y registrar una acción para determinado desencadenador.</span><span class="sxs-lookup"><span data-stu-id="ff07a-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="ff07a-129">[BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) ejecutará la función de JavaScript cuando alguien haga clic en el cubo:</span><span class="sxs-lookup"><span data-stu-id="ff07a-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="ff07a-130">El código final de la página web tendrá el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="ff07a-131">Habilitación de la experiencia envolvente de WebXR</span><span class="sxs-lookup"><span data-stu-id="ff07a-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="ff07a-132">Ahora que el cubo cambia de color, estamos listos para probar la experiencia envolvente.</span><span class="sxs-lookup"><span data-stu-id="ff07a-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="ff07a-133">En este paso, vamos a introducir [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span><span class="sxs-lookup"><span data-stu-id="ff07a-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="ff07a-134">El cubo estará colgando en el aire y veremos el suelo en la parte inferior.</span><span class="sxs-lookup"><span data-stu-id="ff07a-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="ff07a-135">Agregue el suelo como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ff07a-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="ff07a-136">Esto crea un piso sencillo de 4×4 metros.</span><span class="sxs-lookup"><span data-stu-id="ff07a-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="ff07a-137">Para agregar compatibilidad con WebXR, es necesario llamar a *createDefaultXRExperienceAsync*, que tiene un resultado *Promise*.</span><span class="sxs-lookup"><span data-stu-id="ff07a-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="ff07a-138">Agregue este código al final de la función *createScene*, en lugar de *return scene;* :</span><span class="sxs-lookup"><span data-stu-id="ff07a-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="ff07a-139">Puesto que la función *createScene* ahora devuelve una promesa en lugar de una escena, es necesario modificar cómo se llama a *createScene* y *engine.runRenderLoop*.</span><span class="sxs-lookup"><span data-stu-id="ff07a-139">Since the *createScene* function is now returning a promise instead of a scene, we need to modify how *createScene* and *engine.runRenderLoop* are called.</span></span> <span data-ttu-id="ff07a-140">Reemplace las llamadas actuales de estas funciones, que se encuentran justo antes de la etiqueta *\</script>* , por el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-140">Replace the current calls of these functions, which are located right before the *\</script>* tag, with the code below:</span></span>

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. <span data-ttu-id="ff07a-141">El código final de la página web tendrá el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-141">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="ff07a-142">En el código anterior se genera la siguiente salida en la ventana del explorador: ![Escena de WebXR](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-142">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="ff07a-143">Ejecución en un simulador de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ff07a-143">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="ff07a-144">[Habilite el simulador de Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) si no lo hizo anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ff07a-144">[Enable the Windows Mixed Reality Simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) if you have not done so in the past.</span></span>

1. <span data-ttu-id="ff07a-145">Seleccione el botón VR envolvente en la esquina inferior derecha: ![Botón de VR envolvente](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-145">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="ff07a-146">Esta acción iniciará la ventana del simulador de Windows Mixed Reality como se muestra a continuación: ![Portal de realidad mixta](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-146">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="ff07a-147">Use las teclas W, A, S y D del teclado para avanzar, retroceder, ir a la izquierda y a la derecha.</span><span class="sxs-lookup"><span data-stu-id="ff07a-147">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="ff07a-148">Use la mano simulada para dirigirse al cubo y presione la tecla ENTRAR en el teclado para realizar la acción de clic.</span><span class="sxs-lookup"><span data-stu-id="ff07a-148">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="ff07a-149">El cubo cambiará de color y se moverá a una nueva posición.</span><span class="sxs-lookup"><span data-stu-id="ff07a-149">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="ff07a-150">Al dirigirse al cubo, asegúrese de que el final del haz de mano (círculo blanco) interseque el cubo, como se muestra en la imagen anterior.</span><span class="sxs-lookup"><span data-stu-id="ff07a-150">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="ff07a-151">Obtenga más información sobre [Apuntar y confirmar con las manos.](../../../../design/point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="ff07a-151">Learn more about [Point and commit with hands](../../../../design/point-and-commit.md).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="ff07a-152">Ejecución y depuración en un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="ff07a-152">Run and debug on Android device</span></span>

<span data-ttu-id="ff07a-153">Siga los pasos a continuación para habilitar la depuración en un dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="ff07a-153">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="ff07a-154">Prerrequisitos</span><span class="sxs-lookup"><span data-stu-id="ff07a-154">Prerequisites</span></span>

* <span data-ttu-id="ff07a-155">Un servidor web que presenta una página HTML estática en un contexto seguro (https:// o a través del reenvío de puertos en localhost) en el equipo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-155">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="ff07a-156">Por ejemplo, aproveche el paquete npm *serve* como servidor web ligero simple que presenta archivos HTML estáticos, compruebe más [npm serve](https://github.com/vercel/serve#readme).</span><span class="sxs-lookup"><span data-stu-id="ff07a-156">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="ff07a-157">El dispositivo se envió originalmente con Google Play Store y debe ejecutar Android 7.0 o posterior.</span><span class="sxs-lookup"><span data-stu-id="ff07a-157">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="ff07a-158">La versión más reciente de [Google Chrome](https://support.google.com/chrome/answer/95346), tanto en la estación de trabajo de desarrollo como en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-158">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="ff07a-159">Para comprobar que el dispositivo esté configurado correctamente para ejecutar WebXR, vaya a una [página de WebXR de ejemplo](https://immersive-web.github.io/webxr-samples/) en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-159">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="ff07a-160">Debería ver un mensaje como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="ff07a-160">You should see the message, such as:</span></span>

    > <span data-ttu-id="ff07a-161">El explorador admite WebXR y puede ejecutar experiencias de realidad virtual y realidad aumentada si tiene el hardware adecuado.</span><span class="sxs-lookup"><span data-stu-id="ff07a-161">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="ff07a-162">Habilite el modo de desarrollador y la depuración USB en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="ff07a-162">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="ff07a-163">Vea cómo hacerlo para su versión de Android en la página de documentación oficial [Cómo configurar las opciones para desarrolladores en el dispositivo](https://developer.android.com/studio/debug/dev-options).</span><span class="sxs-lookup"><span data-stu-id="ff07a-163">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="ff07a-164">A continuación, conecte el dispositivo Android a la máquina de desarrollo o portátil a través de un cable USB.</span><span class="sxs-lookup"><span data-stu-id="ff07a-164">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="ff07a-165">Asegúrese de que el servidor web de la máquina de desarrollo esté en ejecución.</span><span class="sxs-lookup"><span data-stu-id="ff07a-165">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="ff07a-166">Por ejemplo, vaya a la carpeta raíz que contiene la página de hospedaje web (index.html) y ejecute el código siguiente (suponiendo que use el paquete serve npm):</span><span class="sxs-lookup"><span data-stu-id="ff07a-166">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="ff07a-167">Abra Google Chrome en la máquina de desarrollo y escriba el texto siguiente en la barra de direcciones:</span><span class="sxs-lookup"><span data-stu-id="ff07a-167">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="ff07a-168">chrome://inspect#devices ![Ventana de depuración USB de Chrome](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-168">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="ff07a-169">Asegúrese de que la casilla *Discover USB devices* (Detectar dispositivos USB) esté habilitada.</span><span class="sxs-lookup"><span data-stu-id="ff07a-169">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="ff07a-170">Haga clic en el botón *Port forwarding* (Reenvío de puertos) y asegúrese de que *Port forwarding* esté habilitado y contenga una entrada *localhost:5000* como se muestra a continuación: ![Ventana Port Forwarding de Chrome](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-170">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="ff07a-171">En el dispositivo Android conectado, abra una ventana de Google Chrome y vaya a *http://localhost:5000* , debería ver el cubo.</span><span class="sxs-lookup"><span data-stu-id="ff07a-171">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="ff07a-172">En la máquina de desarrollo, en Chrome, verá el dispositivo y una lista de páginas web abiertas actualmente allí: ![Ventana Inspect de Chrome.](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-172">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="ff07a-173">Haga clic en el botón *Inspect* (Inspeccionar) junto a una entrada *http://localhost:5000* : ![ Ventana de depuración de Chrome DevTools](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="ff07a-173">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="ff07a-174">Use [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) para depurar la página.</span><span class="sxs-lookup"><span data-stu-id="ff07a-174">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="ff07a-175">Puntos clave</span><span class="sxs-lookup"><span data-stu-id="ff07a-175">Takeaways</span></span>

<span data-ttu-id="ff07a-176">Las siguientes son las conclusiones más importantes de este tutorial:</span><span class="sxs-lookup"><span data-stu-id="ff07a-176">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="ff07a-177">Babylon.js facilita la creación de experiencias envolventes mediante JavaScript.</span><span class="sxs-lookup"><span data-stu-id="ff07a-177">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="ff07a-178">Para crear escenas virtuales, no es necesario escribir código de bajo nivel ni aprender una nueva tecnología.</span><span class="sxs-lookup"><span data-stu-id="ff07a-178">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="ff07a-179">Puede compilar aplicaciones de realidad mixta con un explorador compatible con WebXR sin necesidad de comprar un casco.</span><span class="sxs-lookup"><span data-stu-id="ff07a-179">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="ff07a-180">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="ff07a-180">Next steps</span></span>

<span data-ttu-id="ff07a-181">Felicidades.</span><span class="sxs-lookup"><span data-stu-id="ff07a-181">Congratulations!</span></span> <span data-ttu-id="ff07a-182">Ha completado nuestra serie de tutoriales de babylon.js y ha aprendido a:</span><span class="sxs-lookup"><span data-stu-id="ff07a-182">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="ff07a-183">Configurar entorno de desarrollo</span><span class="sxs-lookup"><span data-stu-id="ff07a-183">Set up a development environment</span></span>
> * <span data-ttu-id="ff07a-184">Crear una nueva página web para mostrar los resultados</span><span class="sxs-lookup"><span data-stu-id="ff07a-184">Create a new web page to display results</span></span>
> * <span data-ttu-id="ff07a-185">Usar la API babylon.js para crear e interactuar con elementos 3D básicos</span><span class="sxs-lookup"><span data-stu-id="ff07a-185">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="ff07a-186">Ejecutar y probar la aplicación en un simulador de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="ff07a-186">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="ff07a-187">Para más información sobre el desarrollo de realidad mixta en JavaScript, consulte [Introducción al desarrollo con JavaScript](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ff07a-187">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>
