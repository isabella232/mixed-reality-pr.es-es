---
title: 'Tutoriales de introducción: 4. Posicionamiento de los objetos en la escena'
description: En este curso se muestra cómo colocar objetos en la escena y cómo usar Mixed Reality Toolkit (MRTK) para organizar los objetos en una cuadrícula.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, solvers, grid object collection
ms.localizationpriority: high
ms.openlocfilehash: b49d1b93b98a68e253239647262edc737fdbeb58
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679314"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. Posicionamiento de los objetos en la escena

## <a name="overview"></a>Introducción

En este tutorial, importará los recursos del tutorial y colocará los objetos proporcionados en la escena.

## <a name="objectives"></a>Objetivos

* Obtener información sobre cómo colocar objetos en la escena
* Aprender a usar la característica de colección de objetos de la cuadrícula de MRTK

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descargue e importe el paquete personalizado de Unity siguiente:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta las instrucciones de [Importación de MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit).

## <a name="creating-the-parent-object"></a>Creación del objeto principal

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena:

![Menú contextual emergente de Create Empty (Crear vacío) de Unity](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> Para mostrar las ventanas Scene (Escena) y Game (Juego) una al lado de otra como se muestra en la imagen anterior, arrastra la ventana Game (Juego) al lado derecho de la ventana Scene (Escena). Para obtener más información sobre cómo personalizar el área de trabajo, puedes consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">personalización del área de trabajo</a> de Unity.

Haga clic con el botón derecho en el objeto recién creado, seleccione **Rename** (Cambiar nombre) y cambie el nombre a **RoverExplorer**:

![Menú contextual emergente Rename (Cambiar nombre) de Unity](images/mr-learning-base/base-04-section2-step1-2.png)

Con el objeto RoverExplorer todavía seleccionado, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición**: X = 0, Y = -0.6, Z = 2
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity con el objeto RoverExplorer seleccionado y colocado](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> La cámara representa la cabeza del usuario y se coloca en el origen, X = 0, Y = 0, Z = 0. En general, 1 unidad en Unity es aproximadamente 1 metro en el mundo físico. Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala. En el escenario anterior, el objeto RoverExplorer se coloca a 2 metros por delante y 0,6 metros por debajo de la cabeza del usuario.

## <a name="adding-the-tutorial-prefabs"></a>Adición de los elementos prefabricados del tutorial

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**:

![Ventana Project (Proyecto) de Unity con la carpeta Prefabs seleccionada](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.

En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **Table** (Tabla) sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición**: X = 0, Y = -0.005, Z = 0
* **Rotación**: X = 0, Y = 0, Z = 0
* **Escala**: X = 1.2, Y = 0.01, Z = 1.2

![Unity con el objeto prefabricado Table recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> Para mostrar la escena tal y como se muestra en la imagen anterior, use <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a> (Gizmo de escena), situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z, haga doble clic en el objeto MixedRealityPlayspace para enfocar la cámara y acérquese según sea necesario.

En la ventana Project (Proyecto), haga clic y arrastre el elemento prefabricado **RoverAssembly** sobre el objeto **RoverExplorer** para convertirlo en un elemento secundario del objeto RoverExplorer y, a continuación, en la ventana Inspector, configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición**: X = -0.1, Y = 0, Z = 0
* **Rotación**: X = 0, Y = 135, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity con el objeto prefabricado RoverAssembly recién agregado seleccionado y colocado](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>Organización de los objetos de una colección

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **RoverParts** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición**: X = 0, Y = 0.06, Z = 0
* **Rotación**: X = 0, Y = 90, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity con el objeto RoverParts recién creado seleccionado y colocado](images/mr-learning-base/base-04-section4-step1-1.png)

En la ventana Hierarchy (Jerarquía), seleccione todos los objetos secundarios de RoverExplorer > RoverAssembly > RoverModel > **Parts**, haga clic derecho en ellos y seleccione **Duplicate** (Duplicar) para crear una copia de cada una de las partes:

![Unity con todos los objetos Parts seleccionados y el menú contextual emergente Duplicate](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> Para seleccionar varios objetos adyacentes, mantenga presionada la tecla Mayús mientras usa el mouse para seleccionar el primer y el último objeto.

Con los objetos secundarios de Parts recién duplicados todavía seleccionados, haga clic en ellos y arrástrelos sobre el objeto **RoverParts** para convertirlos en objetos secundarios del objeto RoverParts:

![Unity con los objetos Parts recién duplicados como elementos secundarios del objeto RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

Para que resulte más fácil trabajar con esta escena, en la ventana Jerarquía, haga clic en el icono del **ojo** situado a la izquierda del objeto para desactivar la **visibilidad de la escena** del objeto **RoverExplorer**. Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:

![Unity con visibilidad de la escena RoverAssembly desactivada](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> Para obtener más información sobre los controles de visibilidad de la escena y cómo puede usarlos para optimizar la vista de la escena y el flujo de trabajo, puede consultar la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.

En la ventana Hierarchy (Jerarquía), borre los nombres de los objetos secundarios de RoverParts reemplazando el **(1)** anexado por **_Part**:

![Unity con el nombre de las partes duplicadas borrado](images/mr-learning-base/base-04-section4-step1-5.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverParts**; a continuación, en la ventana Inspector, haga clic en el botón **Add Component** (Agregar componente) y busque y seleccione **GridObjectCollection** para agregar el componente GridObjectCollection al objeto RoverParts:

![Objeto RoverParts de Unity con Add Component (Agregar componente) GridObjectCollection en curso](images/mr-learning-base/base-04-section4-step1-6.png)

Configure los valores del componente **GridObjectCollection** como se indica a continuación:

* **Tipo de orden**: Alfabético
* **Diseño**: Horizontal
* **Ancho de celda**: 0.25
* **Distancia desde el elemento principal**: 0.38

![Unity con el componente GridObjectCollection configurado](images/mr-learning-base/base-04-section4-step1-7.png)

A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios de RoverParts:

![Unity con el componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a colocar objetos en la escena en relación con el usuario y a usar la característica de colección de objetos de la cuadrícula de MRTK para organizar los objetos de una colección.

[Tutorial siguiente: 5. Creación de contenido dinámico mediante el uso de solucionadores](mr-learning-base-05.md)