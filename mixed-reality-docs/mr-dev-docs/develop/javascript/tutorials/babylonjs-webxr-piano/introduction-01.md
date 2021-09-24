---
title: Crear un piano en WebXR mediante BabylonJS
description: Complete esta serie de tutoriales para aprender a crear un teclado de 88 teclas funcional en WebXR con BabylonJS.
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932499"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Tutorial: Crear un piano en WebXR mediante Babylon.js

La creación de un piano en el mundo real requiere mucho tiempo, aptitudes y materiales. ¿Qué sucede al crear uno para VR o AR?

En esta serie de tutoriales, aprenderá a usar Babylon.js para crear una aplicación web de realidad mixta que contenga un piano levantado de 88 teclas funcional en el mundo virtual. En la aplicación completada, podrá teletransportarse al piano y tocar sus teclas con los mandos de realidad mixta.

En esta serie de tutoriales, aprenderá a:

> [!div class="checklist"]
> * Crear, colocar y combinar mallas para crear un teclado de piano
> * Importar un modelo de Babylon.js de un marco de piano levantado
> * Agregar interacciones de puntero a cada tecla del piano
> * Habilitar la compatibilidad con el teletransporte y los punteros múltiples en WebXR

## <a name="prerequisites"></a>Requisitos previos

* Un equipo conectado a Internet
* Conocimientos básicos de JavaScript
* [Tutorial de Hola mundo de JavaScript de WebXR](../babylonjs-webxr-helloworld/introduction-01.md)
* Explorador compatible con WebXR, por ejemplo, [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o superior
* Cualquier [casco de VR](../../../../discover/immersive-headset-hardware-details.md) o [simulador de Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) si desea usar un simulador de Windows Mixed Reality

## <a name="getting-started"></a>Introducción

Para empezar, vamos a configurar la página web HTML que contendrá la escena de Babylon.js.

1. Cree una carpeta denominada *babylonjs-piano-tutorial* y ábrala en Visual Studio Code.

    > [!NOTE]
    > Aunque puede usar cualquier editor de código para hacer el seguimiento, usaremos Visual Studio Code a lo largo de este tutorial para mayor comodidad.

1. Dentro de la carpeta, cree un archivo denominado *index.html* e inserte la plantilla siguiente en el archivo:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Si necesita más explicaciones sobre el contenido de esta plantilla, consulte el [tutorial de Hola mundo](../babylonjs-webxr-helloworld/introduction-01.md), que es un requisito previo de este tutorial.

1. Si intenta abrir este archivo en un explorador, la consola muestra un error que indica que no se encuentra la función `createScene()`. Para resolver este error, vamos a implementar la función `createScene()` en la sección siguiente.

## <a name="setup-the-scene"></a>Configuración de la escena

1. En la misma carpeta que *index.html*, cree otro archivo denominado *scene.js*. Almacenaremos todo el código JavaScript relacionado con la configuración de la escena y la creación del piano en el archivo.

1. Vamos a agregar la función `createScene()` a *scene.js*:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Tenga en cuenta que estamos convirtiendo `createScene()` en una función asincrónica. Manténgase atento para averiguar por qué.

1. A continuación, necesitamos una luz y una cámara para que la escena sea visible para nosotros. Actualización de la función `createScene()`:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    En este caso, hemos creado [arcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que apunta casi completamente hacia abajo y tiene como destino el punto de origen del espacio. La luz que hemos creado es [HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light), que apunta al cielo y es útil para simular un espacio ambiente. También hemos atenuado un poco la luz al reducir su intensidad.

    Si necesita un recordatorio sobre cómo crear una cámara y una luz, vuelva a visitar la [sección Preparar la escena de la serie de tutoriales de Hola mundo](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) antes de continuar con el paso siguiente.

1. Por último, dado que estamos desarrollando para una plataforma WebXR, será necesario [habilitar la experiencia de XR](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) en la escena mediante la inserción de la siguiente línea antes de `return scene;`:

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    En JavaScript, para usar el teclado `await` en una función `async` dentro de una función, la función primaria también tendría que ser `async`, por lo que definimos la función `createScene` como asincrónica antes. Más adelante, en esta serie de tutoriales, usaremos `xrHelper` para habilitar y configurar diferentes características de WebXR compatibles con Babylon.js.

1. *scene.js*, una vez completado, debería tener este aspecto:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Ahora que tenemos una función `createScene()` en funcionamiento, haremos que *index.html* cargue el archivo *scene.js* como script para que la función `createScene()` se reconozca en *index.html*. Agregue esta línea de código dentro de la sección `<header>` del archivo HTML:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Abra *index.html* en el explorador y verá que el mensaje de error que vimos anteriormente ya no está presente y que tenemos una escena Babylon.js vacía en la página.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Siguiente tutorial: Crear un modelo de piano en 3D](keyboard-model-02.md)
