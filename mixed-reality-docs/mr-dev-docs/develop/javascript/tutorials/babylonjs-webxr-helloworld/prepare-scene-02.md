---
title: Tutorial de babylon.js para preparar una escena con objetos 3D básicos
description: Aprenda a usar babylon.js y a agregar objetos 3D básicos a una escena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: 9d74104924aa859f5ab18248a487a7e80392809adb09361e84c5ad386f1321c4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212396"
---
# <a name="tutorial-prepare-a-scene"></a>Tutorial: Preparación de una escena

Aprenda a preparar una escena y agregarle algunos elementos 3D básicos.

En este tutorial, aprenderá a:

> [!div class="checklist"]
> * Crear una escena
> * Agregar una cámara
> * Agregar luz
> * Agregar elementos 3D básicos

## <a name="before-you-begin"></a>Antes de empezar

En el paso anterior del tutorial, se creó una página web básica. Abra la página web para su edición.

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

## <a name="create-a-scene"></a>Creación una escena

Una escena es donde se mostrará todo el contenido. Puede haber varias escenas, y es posible cambiar entre una escena y otra. Lea más sobre [Scene de babylon.js](https://doc.babylonjs.com/divingDeeper/scene).

1. Agregue la etiqueta de script después del elemento HTML de lienzo (canvas), y agregue el código siguiente para crear una escena rellena de color negro:

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

    En el código anterior, tenemos que crear una instancia del motor de representación web de babylon.js que represente una escena y enlace eventos en el lienzo. Para más información sobre el motor, consulte la página de documentación de [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine).

1. La escena no se representa de manera predeterminada. Recuerde que puede haber varias escenas y que usted controla qué escena se muestra. Para representar la escena repetidamente en cada fotograma, ejecute el código siguiente después de la llamada a la función *createScene*:

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Adición de elementos 3D básicos

1. Vamos a agregar la primera forma 3D. En el mundo virtual 3D, las formas se construyen a partir de *mallas*, muchas facetas triangulares unidas, donde cada faceta está compuesta a partir de tres vértices. Puede usar una malla predefinida o crear su propia malla personalizada. Aquí usaremos una malla de cuadro predefinida, es decir, un cubo. Para crear el cuadro, use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). Los parámetros son el nombre y las opciones (las opciones son diferentes según el tipo de malla). Anexe el código siguiente a la función *createScene*:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Abra la página web en el explorador Microsoft Edge y compruebe la salida. La ventana del explorador muestra una página en blanco. Abra DevTools con el teclado y seleccione F12, Control+Mayús+I (Windows, Linux) o Comando+Opción+I (macOS). Después de abrir la pestaña *Consola*, puede empezar a buscar errores. Aparecerá un error: "Uncaught Error: No camera defined" (Error no detectado: No hay definida ninguna cámara). Ahora tenemos que agregar una cámara a la escena.

## <a name="add-a-camera"></a>Agregar una cámara

1. Para ver el mundo virtual e interactuar con él, tiene que haber una cámara conectada al lienzo. Vamos a agregar la cámara de tipo [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), que se puede girar alrededor de un destino. Los parámetros necesarios para crear una instancia de la cámara son:
    1. **name**: Nombre de la cámara.
    1. **alpha**: Posición angular a lo largo del eje longitudinal (en radianes).
    1. **beta**: Posición angular a lo largo del eje latitudinal (en radianes).
    1. **radius**: Distancia desde el destino.
    1. **target**: Punto hacia el que siempre se enfrentaría la cámara (definido por coordenadas x-y-z).
    1. **scene**: Escena en la que se encuentra la cámara.

    Alpha, beta, radius y target, en su conjunto, definen la posición de la cámara en el espacio, como se muestra en el diagrama siguiente:

    ![Alpha Beta Radius de la cámara](../images/camera-alpha-beta-radius.jpg)

    Agregue el código siguiente a la función *createScene*:

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Si comprueba la salida en el explorador, verá un lienzo negro. Nos falta la luz.

## <a name="add-light"></a>Adición de luz

1. Hay cuatro tipos de luces que se pueden usar con una variedad de propiedades de iluminación: luz puntual, direccional, angular y hemisférica. Vamos a agregar la luz ambiente [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), como se muestra a continuación:

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
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

1. Compruebe la salida en el explorador. Debería ver el cubo y, con el mouse, puede girar la cámara alrededor del cubo y ver las distintas caras del cubo:

![Escena básica con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Siguiente tutorial: 3. Interacción con un objeto 3D](interact-03.md)
