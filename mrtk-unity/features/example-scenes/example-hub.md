---
title: Centro de conectividad de ejemplos de MRTK
description: Información general sobre escenas de ejemplo en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 6f86a7b6469a8dc7f6253d81f8cf647fbcfe35830fa8cf044066ba8ae9c5a286
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209378"
---
# <a name="mrtk-examples-hub"></a>Centro de conectividad de ejemplos de MRTK

![Centro de conectividad de ejemplos de MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

El centro de ejemplos de MRTK es una escena de Unity que facilita la experiencia de varias escenas. Usa el sistema de escena de MRTK para cargar & descargar las escenas.

**MRTKExamplesHub.unity es** la escena del contenedor que tiene componentes compartidos, como ``MixedRealityToolkit`` y ``MixedRealityPlayspace`` . **La escena MRTKExamplesHubMainMenu.unity** tiene los botones de cubo.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Descarga de la aplicación Microsoft Store en HoloLens 2
Si tiene un HoloLens 2, puede descargar e instalar directamente la aplicación en el dispositivo.

<a href='//www.microsoft.com/store/apps/9mv8c39l2sj4?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="prerequisite"></a>Requisito previo

El centro de ejemplos de MRTK usa [scene transition service y](../extensions/scene-transition-service.md) scripts relacionados. Si usa MRTK a través de paquetes de Unity, importe **Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage,** que forma parte de los [paquetes de versión](https://github.com/microsoft/MixedRealityToolkit-Unity/releases). Si usa MRTK a través del clon del repositorio, ya debe tener la **carpeta MRTK/Extensions** en el proyecto.

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a>MRTKExamplesHub scene y el sistema de escena

Abra **MRTKExamplesHub.unity,** que se encuentra en Es una escena vacía con `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace y LoadHubOnStartup. Esta escena está configurada para usar el sistema de escena de MRTK. Haga `MixedRealitySceneSystem` clic en MixedRealityToolkit. Se mostrará la información del sistema de escena en el panel Inspector.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

En la parte inferior del inspector, muestra la lista de las escenas definidas en el perfil del sistema de escena. Puede hacer clic en los nombres de escena para cargarlos o descargarlos.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3">Ejemplo de carga _de la escena de MRTKExamplesHub_ haciendo clic en el nombre de la escena en la lista.
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4">Ejemplo de carga _de la escena HandInteractionExamples._
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
Ejemplo de carga de varias escenas.

## <a name="running-the-scene"></a>Ejecución de la escena

La escena funciona tanto en el modo de juego de Unity como en el dispositivo. Ejecute la **escena MRTKExamplesHub** en el editor de Unity y use la simulación de entrada de MRTK para interactuar con el contenido de la escena. Para compilar e implementar, basta con compilar la escena **de MRTKExamplesHub** con otras escenas que se incluyen en la lista del sistema de escenas. El inspector también facilita la adición de escenas al cuadro de Configuración. En el cuadro Configuración, asegúrese de que la escena **de MRTKExamplesHub** se encuentra en la parte superior de la lista en el índice 0.

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a>Cómo carga MRTKExamplesHub una escena

En la **escena de MRTKExamplesHub,** puede encontrar el ``ExamplesHubButton`` prefab.
Hay un objeto **FrontPlate** en el objeto prefab que contiene ``Interactable`` .
Con el evento y de Interactable, desencadena la función ``OnClick()`` ``OnTouch()`` **LoadContent()** del script **LoadContentScene.**
En el inspector del script **LoadContentScene,** puede definir el nombre de la escena que se va a cargar.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

El script usa la función LoadContent() de Scene System para cargar la escena.
Consulte la página [Scene System (Sistema de](../scene-system/scene-system-getting-started.md) escena) para obtener más detalles.

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a>Volver a la escena del menú principal

Para volver a la escena del menú principal (MRTKExamplesHubMainMenu), puede usar el mismo método scene `LoadContent()` system. **ToggleFeaturesPanelExamplesHub.prefab** proporciona el botón "Inicio" que contiene el script **LoadContentScene.** Use este elemento prefab o proporcione un botón de inicio personalizado en cada escena para permitir que el usuario vuelva a la escena principal. Se puede colocar **ToggleFeaturesPanelExamplesHub.prefab** en la escena **de MRTKExamplesHub** para que siempre sea visible, ya que **MRTKExamplesHub es** una escena de contenedor compartido. Asegúrese de ocultar o desactivar **ToggleFeaturesPanel.prefab en** cada escena de ejemplo.

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a>Agregar botones adicionales

En el **objeto CubeCollection,** duplique (o agregue) los elementos prefabs _ExampleHubButton_ y haga clic en **Actualizar** colección en `GridObjectCollection` .
Esto actualizará el diseño del cilindro en función del nuevo número total de botones.
Consulte la página [Colección de objetos](../ux-building-blocks/object-collection.md) para obtener más detalles.

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

Después de agregar los botones, actualice el nombre de la escena en el script **LoadContentScene** (explicado anteriormente).
Agregue escenas adicionales al perfil del sistema de escena.
