---
title: Tutoriales de introducción a babylon.js y WebXR
description: Complete este curso para aprender a usar babylon.js y crear una aplicación básica de realidad mixta.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realidad mixta, javascript, tutorial, BabylonJS, hololens, mixed reality, UWP, Windows 10, WebXR, web envolvente
ms.localizationpriority: high
ms.openlocfilehash: e2006e911ad9dae00252c929c7739ff2209f4bf7796f1c49e713cfaf53267cd2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196829"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Tutorial: Creación de la primera aplicación WebXR mediante babylon.js

En este tutorial verá cómo crear una aplicación básica de realidad mixta mediante babylon.js y Visual Studio Code. La aplicación que va a compilar representará un cubo, le permitirá girarlo para poder ver las otras caras, y agregar interacciones. En este tutorial aprenderá a:

> [!div class="checklist"]
> * Configurar entorno de desarrollo
> * Usar la API babylon.js para crear elementos 3D básicos  
> * Crear una nueva página web
> * Interactuar con elementos 3D
> * Ejecutar la aplicación en un simulador de Windows Mixed Reality

## <a name="prerequisites"></a>Prerrequisitos

* Explorador compatible con WebXR, por ejemplo, [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o superior
* [NodeJS](https://nodejs.org/)
* Opcional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) si desea usar un simulador de Windows Mixed Reality
* Opcional: [Simulador de Windows Mixed Reality](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Introducción

Para crear este proyecto desde cero, comience con un proyecto de Visual Studio Code (VSCode).

> [!NOTE]
> No es obligatorio usar VSCode, pero lo usaremos para mayor practicidad a lo largo del tutorial. Los desarrolladores de JavaScript más experimentados pueden usar cualquier otro editor de su elección, incluso el más sencillo Bloc de notas.

1. Descargue el archivo único [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) o use una versión en línea que se puede encontrar en el [sitio web oficial de babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers). También puede clonar todo el proyecto de babylon.js desde [GitHub](https://github.com/BabylonJS/Babylon.js).
1. Cree un archivo vacío y guárdelo como página HTML, por ejemplo, index.html.
1. Cree un marcado HTML básico y haga referencia al archivo de JavaScript babylon.js. El código final se muestra a continuación:

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

1. Agregue un elemento HTML *canvas* dentro del cuerpo para representar el contenido de babylon.js. Tenga en cuenta que canvas tiene un atributo id, lo que le permite acceder a este elemento HTML desde JavaScript más adelante.

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

1. Canvas ocupa toda la página web. Con esto se completa nuestra página web. Llegados a este punto, la página web está lista. Puede abrirla en cualquier explorador y asegurarse de que no aparezca ningún error, aunque todavía no hay ninguna experiencia envolvente.

## <a name="next-steps"></a>Pasos siguientes

> [!div class="nextstepaction"]
> [Siguiente tutorial siguiente: 2. Preparación de una escena](prepare-scene-02.md)