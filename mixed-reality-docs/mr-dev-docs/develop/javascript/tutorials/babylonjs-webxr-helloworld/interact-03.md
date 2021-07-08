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
# <a name="tutorial-interact-with-3d-object"></a>Tutorial: Interacción con objetos 3D

Aprenda a crear objetos 3D e interacciones para una experiencia de realidad mixta mediante babylon.js. En esta sección, comenzará con algo sencillo, como pintar las caras de un cubo cuando selecciona el objeto.

En este tutorial se tratan los temas siguientes:

> [!div class="checklist"]
> * Adición de interacciones
> * Habilitación del modo envolvente de WebXR
> * Ejecución de la aplicación en el simulador de Windows Mixed Reality
> * Ejecución y depuración de la aplicación en Android Chrome

## <a name="before-you-begin"></a>Antes de empezar

En el paso anterior del tutorial, se creó una página web básica con una escena. Abra la página web de hospedaje para su edición.

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

## <a name="add-interaction"></a>Adición de una interacción

1. En primer lugar, vamos a actualizar el código que crea el cubo, para que el cubo esté pintado con un color aleatorio. Para ello, agregaremos [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) al cubo. El material nos permite especificar el color y las texturas, y se puede usar para cubrir otros objetos. La manera en que aparece un material depende de la o las luces que se usan en la escena y de cómo está configurado para reaccionar. Por ejemplo, diffuseColor distribuye el color por toda la malla a la que está asociada. Agregue el código siguiente:

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Ahora que el cubo está pintado con un color aleatorio, vamos a agregar una interacción para lo siguiente:

    * Cambiar el color al hacer clic en el cubo
    * Mover el cubo después de que cambia de color

    Para agregar interacciones, debemos usar [action](https://doc.babylonjs.com/divingDeeper/events/actions). Una acción se inicia en respuesta al desencadenador de eventos. Por ejemplo, cuando el usuario hace clic en el cubo. Todo lo que tenemos que hacer es crear una instancia de BABYLON.ActionManager y registrar una acción para determinado desencadenador. [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) ejecutará la función de JavaScript cuando alguien haga clic en el cubo:

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

1. El código final de la página web tendrá el aspecto siguiente:

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

## <a name="enable-webxr-immersive-experience"></a>Habilitación de la experiencia envolvente de WebXR

Ahora que el cubo cambia de color, estamos listos para probar la experiencia envolvente.

1. En este paso, vamos a introducir [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground). El cubo estará colgando en el aire y veremos el suelo en la parte inferior. Agregue el suelo como se indica a continuación:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Esto crea un piso sencillo de 4×4 metros.

1. Para agregar compatibilidad con WebXR, es necesario llamar a *createDefaultXRExperienceAsync*, que tiene un resultado *Promise*. Agregue este código al final de la función *createScene*, en lugar de *return scene;* :

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. Puesto que la función *createScene* ahora devuelve una promesa en lugar de una escena, es necesario modificar cómo se llama a *createScene* y *engine.runRenderLoop*. Reemplace las llamadas actuales de estas funciones, que se encuentran justo antes de la etiqueta *\</script>* , por el código siguiente:

    ```javascript
    createScene().then(sceneToRender => {
        engine.runRenderLoop(() => sceneToRender.render());
    });
    ```

1. El código final de la página web tendrá el aspecto siguiente:

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

1. En el código anterior se genera la siguiente salida en la ventana del explorador: ![Escena de WebXR](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Ejecución en un simulador de Windows Mixed Reality

1. [Habilite el simulador de Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) si no lo hizo anteriormente.

1. Seleccione el botón VR envolvente en la esquina inferior derecha: ![Botón de VR envolvente](../images/immersive-vr-button.png)

1. Esta acción iniciará la ventana del simulador de Windows Mixed Reality como se muestra a continuación: ![Portal de realidad mixta](../images/mixed-reality-portal.png)

1. Use las teclas W, A, S y D del teclado para avanzar, retroceder, ir a la izquierda y a la derecha. Use la mano simulada para dirigirse al cubo y presione la tecla ENTRAR en el teclado para realizar la acción de clic. El cubo cambiará de color y se moverá a una nueva posición.

> [!NOTE]
> Al dirigirse al cubo, asegúrese de que el final del haz de mano (círculo blanco) interseque el cubo, como se muestra en la imagen anterior. Obtenga más información sobre [Apuntar y confirmar con las manos.](../../../../design/point-and-commit.md)

## <a name="run-and-debug-on-android-device"></a>Ejecución y depuración en un dispositivo Android

Siga los pasos a continuación para habilitar la depuración en un dispositivo Android:

### <a name="prerequisites"></a>Prerrequisitos

* Un servidor web que presenta una página HTML estática en un contexto seguro (https:// o a través del reenvío de puertos en localhost) en el equipo de desarrollo. Por ejemplo, aproveche el paquete npm *serve* como servidor web ligero simple que presenta archivos HTML estáticos, compruebe más [npm serve](https://github.com/vercel/serve#readme).
* El dispositivo se envió originalmente con Google Play Store y debe ejecutar Android 7.0 o posterior.
* La versión más reciente de [Google Chrome](https://support.google.com/chrome/answer/95346), tanto en la estación de trabajo de desarrollo como en el dispositivo.
* Para comprobar que el dispositivo esté configurado correctamente para ejecutar WebXR, vaya a una [página de WebXR de ejemplo](https://immersive-web.github.io/webxr-samples/) en el dispositivo. Debería ver un mensaje como el siguiente:

    > El explorador admite WebXR y puede ejecutar experiencias de realidad virtual y realidad aumentada si tiene el hardware adecuado.

1. Habilite el modo de desarrollador y la depuración USB en un dispositivo Android. Vea cómo hacerlo para su versión de Android en la página de documentación oficial [Cómo configurar las opciones para desarrolladores en el dispositivo](https://developer.android.com/studio/debug/dev-options).
1. A continuación, conecte el dispositivo Android a la máquina de desarrollo o portátil a través de un cable USB.
1. Asegúrese de que el servidor web de la máquina de desarrollo esté en ejecución. Por ejemplo, vaya a la carpeta raíz que contiene la página de hospedaje web (index.html) y ejecute el código siguiente (suponiendo que use el paquete serve npm):

    ```bash
    serve
    ```

1. Abra Google Chrome en la máquina de desarrollo y escriba el texto siguiente en la barra de direcciones:
    > chrome://inspect#devices ![Ventana de depuración USB de Chrome](../images/chrome-usb-debug.png)
1. Asegúrese de que la casilla *Discover USB devices* (Detectar dispositivos USB) esté habilitada.
1. Haga clic en el botón *Port forwarding* (Reenvío de puertos) y asegúrese de que *Port forwarding* esté habilitado y contenga una entrada *localhost:5000* como se muestra a continuación: ![Ventana Port Forwarding de Chrome](../images/chrome-port-forwarding.png)
1. En el dispositivo Android conectado, abra una ventana de Google Chrome y vaya a *http://localhost:5000* , debería ver el cubo.
1. En la máquina de desarrollo, en Chrome, verá el dispositivo y una lista de páginas web abiertas actualmente allí: ![Ventana Inspect de Chrome.](../images/chrome-inspect.png)
1. Haga clic en el botón *Inspect* (Inspeccionar) junto a una entrada *http://localhost:5000* : ![ Ventana de depuración de Chrome DevTools](../images/chrome-debug.png)
1. Use [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) para depurar la página.

## <a name="takeaways"></a>Puntos clave

Las siguientes son las conclusiones más importantes de este tutorial:
* Babylon.js facilita la creación de experiencias envolventes mediante JavaScript.
* Para crear escenas virtuales, no es necesario escribir código de bajo nivel ni aprender una nueva tecnología.
* Puede compilar aplicaciones de realidad mixta con un explorador compatible con WebXR sin necesidad de comprar un casco.

## <a name="next-steps"></a>Pasos siguientes

Felicidades. Ha completado nuestra serie de tutoriales de babylon.js y ha aprendido a:
> [!div class="checklist"]
> * Configurar entorno de desarrollo
> * Crear una nueva página web para mostrar los resultados
> * Usar la API babylon.js para crear e interactuar con elementos 3D básicos
> * Ejecutar y probar la aplicación en un simulador de Windows Mixed Reality

Para más información sobre el desarrollo de realidad mixta en JavaScript, consulte [Introducción al desarrollo con JavaScript](/javascript-development-overview.md).
