---
title: Crear un modelo de piano en 3D
description: Aprenda a crear un modelo de piano en 3D con programación en Babylon.js
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932516"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Tutorial: Creación de un modelo de piano en 3D

En el tutorial anterior de la serie, hemos configurado una página web que contiene una escena en Babylon.js con una cámara y una luz. En este tutorial, crearemos y agregaremos un modelo de piano a la escena.

![Levantar una malla de piano](./images/standup-piano-mesh.png)

En este tutorial, aprenderá a:

> [!div class="checklist"]
> * Crear, colocar y combinar mallas
> * Crear un teclado de piano a partir de mallas de cuadro
> * Importar un modelo 3D de un marco de piano

## <a name="before-you-begin"></a>Antes de comenzar

Asegúrese de que ha pasado por el [tutorial anterior de la serie](introduction-01.md) y está listo para continuar ampliando el código.

*index.html*

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

*scene.js*

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

## <a name="getting-started"></a>Introducción

Para empezar, vamos a crear un teclado de piano simple con esta estructura:

![Descripción del registro del piano](./images/piano-register.jpg)

En esta imagen, hay 7 teclas blancas y 5 negras, cada una etiquetada con el nombre de la nota. Un teclado completo de piano de 88 teclas contiene 7 repeticiones completas de esta selección de teclas (también denominada registro) y 4 teclas adicionales. Cada registro tiene el doble de frecuencia que el anterior. Por ejemplo, la frecuencia de tono de C5 (es decir, la nota C del quinto registro) es el doble que la de C4, la frecuencia de tono de D5 es el doble que la de D4, y así sucesivamente.

Visualmente, cada registro tiene exactamente el mismo aspecto que otro, por lo que podemos empezar por investigar cómo crear un teclado de piano simple con esta selección de teclas. Más tarde, podemos encontrar la manera de expandir el ámbito a un teclado de piano completo de 88 teclas.

## <a name="build-a-simple-piano-keyboard"></a>Crear un teclado de piano simple

> [!NOTE]
> Aunque es posible encontrar modelos 3D creados previamente de teclados de piano en línea e importarlos a nuestra página web, crearemos el teclado desde cero en este tutorial para permitir la máxima personalización y mostrar cómo se pueden crear modelos 3D con Babylon.js.

1. Antes de empezar a crear mallas para compilar el teclado, observe que cada tecla negra no está perfectamente alineada en el centro de las dos teclas blancas que la rodean y que no todas las teclas tienen el mismo ancho. Esto significa que debemos crear y colocar la malla para cada tecla individualmente.

    ![Alineación de teclas negras](./images/black-key-position.png)

1. Para las teclas blancas, podemos observar que cada tecla blanca se compone de dos partes: (1) la parte inferior debajo de las teclas negras y (2) la parte superior junto a las teclas negras. Las dos partes tienen dimensiones diferentes, pero se apilan juntas para crear una tecla blanca completa.

    ![Forma de tecla blanca](./images/white-key-shape-label.png)

1. Este es el código para crear una sola tecla blanca para la nota C (no se preocupe por agregarlo a *scene.js* todavía):

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Aquí hemos creado dos mallas de [caja](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh): una para la parte inferior y otra para la parte superior de la tecla blanca. A continuación, modificamos la posición de la parte superior para apilarla sobre la parte inferior y moverla hacia la izquierda para dejar espacio para la tecla negra vecina (C#).

    Por último, estas dos partes se combinaron mediante la función [MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) para convertirse en una tecla blanca completa. Esta es la malla resultante que este código generaría:

    ![Tecla blanca C](./images/white-key-c.png)

1. La creación de una tecla negra es más sencilla. Puesto que todas las teclas negras tienen la forma de un cuadro, para crear una tecla negra, basta con crear una malla de cuadro con un elemento [StandardMaterial](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color) de color negro.

    > [!NOTE]
    > Dado que el color de malla predeterminado es un gris claro similar al blanco, en este tutorial no se incluyen los pasos para agregar un material de color blanco a las teclas blancas. Sin embargo, no dude en agregar el material por sí mismo si quiere un auténtico color blanco brillante para las teclas blancas.

    Este es el código para crear la tecla negra en C# (no se preocupe por agregarlo a *scene.js*):

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    La tecla negra que genera este código (junto con la tecla blanca anterior) tendría el siguiente aspecto:

    ![Tecla negra en C#](./images/black-key-csharp.png)

1. Como puede ver, la creación de cada tecla puede dar lugar a una gran cantidad de código similar, ya que tenemos que especificar cada una de sus dimensiones y posición. Vamos a intentar que el proceso de creación sea más eficiente en la siguiente sección.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Creación eficiente de un teclado de piano sencillo

1. Aunque cada tecla blanca tiene una forma ligeramente diferente, todas se pueden crear mediante la combinación de una parte superior y una inferior. Vamos a implementar una función genérica para crear y colocar cualquier tecla blanca.

    Agregue la función siguiente a *scene.js*, fuera de la función `createScene()`:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    En este bloque de código, creamos una función denominada `buildKey()` que compila y devuelve una tecla blanca si `props.type` es `"white"`. Mediante la identificación del tipo de tecla en el parámetro `props`, podemos crear teclas blancas y negras en la misma función mediante la bifurcación con una instrucción if.

    Los parámetros de `buildKey()` son:
    * **scene**: escena en la que se encuentra la tecla
    * **parent**: elemento primario de la malla (esto nos permite agrupar todas las teclas en un solo elemento primario)
    * **props**: propiedades de la tecla que se construirá

    Para una tecla blanca, `props` incluirá los siguientes elementos:
    * **type**: "white"
    * **name**: nombre de la nota que la tecla representa
    * **topWidth**: ancho de la parte superior
    * **bottomWidth**. ancho de la parte inferior
    * **topPositionX**: posición x de la parte superior respecto a la inferior
    * **wholePositionX**: posición x de toda la tecla respecto al punto final del registro (el borde derecho de la tecla B).
    * **register**: registro al que pertenece la tecla (un número entre 0 y 8)
    * **referencePositionX**: coordenada x del punto final del registro (se usa como punto de referencia).

    Al separar `wholePositionX` y `referencePositionX`, podemos inicializar los parámetros `props` necesarios para crear un tipo específico de tecla (por ejemplo, C) dentro de cualquier registro y, a continuación, agregar `register` y `referencePositionX` a `props` al crear esa tecla en un registro específico (por ejemplo, C4, C5).

1. Del mismo modo, también podemos escribir una función genérica para crear una tecla negra. Vamos a expandir la función `buildKey()` para incluir esa lógica:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }
    ```

    Para una tecla negra, `props` contiene los siguientes elementos:

    * **type**: "black"
    * **name**: nombre de la nota que la tecla representa
    * **wholePositionX**: posición x de toda la tecla respecto al punto final del registro (el borde derecho de la tecla B)
    * **register**: registro al que pertenece la tecla (un número entre 0 y 8)
    * **referencePositionX**: coordenada x del punto final del registro (se usa como punto de referencia).

    `props` para crear una tecla negra es mucho más simple, ya que la creación de una tecla negra solo implica la creación de un cuadro y el ancho y la posición z de cada tecla negra coinciden.

1. Ahora que tenemos una manera más eficaz de crear las teclas, vamos a inicializar una matriz que almacena `props` para cada tecla que corresponde a una nota en un registro y, a continuación, llamar a la función `buildKey()` con cada una de ellas para crear un teclado simple en el 4.º registro.

    También crearemos un elemento [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) denominado `keyboard` para que actúe como el elemento [primario](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) de todas las teclas del piano. Dado que cualquier cambio de posición o escalado aplicado al elemento primario también se aplicaría a los elementos secundarios, la agrupación de las teclas de esta manera nos permitirá escalarlas o moverlas en conjunto.

    Anexe las siguientes líneas de código a la función `createScene()`.

    ```javascript
    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Como probablemente haya observado, en este bloque de código vamos a colocar todas las claves relativas al origen del espacio.

1. Este es el código que *scene.js* contiene hasta ahora:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]

        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. Este es el aspecto que tendría el teclado resultante:

    ![Teclado de piano con un registro](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Expansión a un piano de 88 teclas

En esta sección, expandiremos el uso de las funciones de creación de claves para generar un teclado de piano completo de 88 teclas.

1. Como se mencionó anteriormente, un teclado de piano completo de 88 teclas contiene 7 registros repetidos y otras 4 notas. 3 de esas notas adicionales están en el registro 0 (extremo izquierdo del teclado) y 1, en el registro 8 (extremo derecho del teclado).

    ![Diseño de piano de 88 teclas](./images/88-key-piano-keyboard-layout.jpg)

1. Primero trabajaremos en la creación de las 7 repeticiones completas. Para hacerlo, agregaremos un bucle adicional al bucle que creamos antes. Reemplace el bucle anterior para la función `buildKey()` por el siguiente código:

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    En este bucle, compilamos las teclas para el registro de 1 a 7 e incrementamos la posición de referencia cada vez que pasamos al siguiente registro.

1. A continuación, vamos a crear el resto de teclas. Agregue el siguiente fragmento de código a la función `createScene()`:

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Tenga en cuenta que la tecla más a la izquierda y la tecla más a la derecha del teclado del piano no se ajustan a las dimensiones de las propiedades definidas en `keyParams` (porque no están junto a una tecla negra en el borde), por lo que es necesario definir un nuevo objeto `props` para que cada una de ellas especifique su forma especial.

1. El teclado generado debe tener este aspecto después de los cambios:

    ![Malla de teclado de piano completo](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Agregar un marco de piano

1. La escena parece un poco rara con solo un teclado flotante en el espacio. Vamos a agregar un marco de piano alrededor del teclado para crear el aspecto de un piano levantado.

1. Podemos crear el marco de una forma similar a las teclas. Para hacerlo, se colocan y combinan un grupo de mallas de cuadro.

    Sin embargo, dejaremos ese desafío para que pruebe por su cuenta y use [BABYLON.SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) para importar una malla prefabricada de un marco de piano levantado. Anexe este fragmento de código a `createScene()`:

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Tenga en cuenta que, de nuevo, estamos creando un elemento primario `TransformNode` denominado `piano` para agrupar el teclado y el marco en conjunto. Esto hará que mover o escalar todo el piano resulte mucho más fácil si es necesario hacerlo.

1. Una vez importado el marco, observe que el teclado se encuentra en la parte inferior del marco (ya que las coordenadas y de las teclas están en 0 de forma predeterminada). Vamos a levantar el teclado para que se ajuste al marco del piano levantado:

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Dado que `keyboard` es el elemento primario de todas las teclas del piano, para levantar todas las teclas del piano, basta con cambiar la posición de y de `keyboard`.

1. El código final de *scene.js* debe tener este aspecto:

    ```javascript
    const buildKey = function (scene, parent, props) {
        if (props.type === "white") {
            /*
            Props for building a white key should contain: 
            note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX
    
            As an example, the props for building the middle C white key would be
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
            */
    
            // Create bottom part
            const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);
    
            // Create top part
            const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
            top.position.z =  4.75;
            top.position.x += props.topPositionX;
    
            // Merge bottom and top parts
            // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
            const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.name = props.note + props.register;
            key.parent = parent;
    
            return key;
        }
        else if (props.type === "black") {
            /*
            Props for building a black key should contain: 
            note, wholePositionX, register, referencePositionX
    
            As an example, the props for building the C#4 black key would be
            {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
            */
    
            // Create black color material
            const blackMat = new BABYLON.StandardMaterial("black");
            blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);
    
            // Create black key
            const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
            key.position.z += 4.75;
            key.position.y += 0.25;
            key.position.x = props.referencePositionX + props.wholePositionX;
            key.material = blackMat;
            key.parent = parent;
    
            return key;
        }
    }

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

        const keyParams = [
            {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
            {type: "black", note: "C#", wholePositionX: -13.45},
            {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
            {type: "black", note: "D#", wholePositionX: -10.6},
            {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
            {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
            {type: "black", note: "F#", wholePositionX: -6.35},
            {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
            {type: "black", note: "G#", wholePositionX: -3.6},
            {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
            {type: "black", note: "A#", wholePositionX: -0.85},
            {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
        ]
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
        // Register 1 through 7
        var referencePositionX = -2.4*14;
        for (let register = 1; register <= 7; register++) {
            keyParams.forEach(key => {
                buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
            })
            referencePositionX += 2.4*7;
        }
    
        // Register 0
        buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
        keyParams.slice(10, 12).forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
        })
    
        // Register 8
        buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    
        // Transform node that acts as the parent of all piano components
        const piano = new BABYLON.TransformNode("piano");
        keyboard.parent = piano;
    
        // Import and scale piano frame
        BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
            const frame = meshes[0];
            frame.parent = piano;
        });
    
        // Lift the piano keyboard
        keyboard.position.y += 80;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Ahora deberíamos tener un piano levantado que tenga el siguiente aspecto: ![Malla de piano levantado](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Tutorial siguiente: tocar el piano en 3D](keyboard-interaction-03.md)
