---
title: Introducción al sistema de escenas
description: Página de aterrizaje del sistema de escena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 5b4f1c3b0f069d320feca8ccecacc6c66576b50339ea7b7733f34525005dd842
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191565"
---
# <a name="scene-system-getting-started"></a>Introducción al sistema de escenas

## <a name="when-to-use-the-scene-system"></a>Cuándo usar el sistema de escena

Si el proyecto consta de una sola escena, es probable que el sistema de escena no sea necesario. Resulta muy útil cuando se cumple una o varias de las siguientes condiciones:

- El proyecto tiene varias escenas.
- Está acostumbrado a cargar una sola escena, pero no le gusta la forma en que destruye la instancia de MixedRealityToolkit.
- Quiere una manera sencilla de cargar varias escenas de forma aditiva para construir su experiencia.
- Quiere una manera sencilla de realizar un seguimiento de las operaciones de carga en curso o una manera sencilla de controlar la activación de la escena para varias escenas que se cargan a la vez.
- Quiere mantener la iluminación coherente y predecible en todas las escenas.

## <a name="scene-system-resources"></a>Recursos del sistema de escena

De forma predeterminada, scene system usa un par de objetos de escena (escena DefaultManagerScene y DefaultLighting). Si no se encuentra ninguna de estas escenas, aparecerá un mensaje en el inspector de perfil del sistema de escena.

![Mensaje de recursos predeterminados](../images/scene-system/DefaultResourcesMessage.png)

>! [Nota] Si el proyecto usa escenas de iluminación y administrador personalizados, este mensaje se puede omitir de forma segura.

En las secciones siguientes se describe ahora para resolver este mensaje, en función del método que se usó para importar el Mixed Reality Toolkit.

### <a name="unity-package-manager-upm"></a>Unity Administrador de paquetes (UPM)

En el Mixed Reality Toolkit paquetes UPM, los recursos del sistema de escena se empaquetan como ejemplo. Debido a que los paquetes UPM son inmutables, Unity no puede abrir el archivo de escena necesario a menos que se importen explícitamente en el proyecto.

Para importar, siga estos pasos:

- Seleccione **Ventana**  >  **Administrador de paquetes**
- Selección **de Mixed Reality Toolkit Foundation**
- Buscar **recursos del sistema de escena** en la sección **Ejemplos**

  ![Importación de recursos del sistema de escena](../images/scene-system/UpmImportSceneSystemResources.png)

- Seleccione **Importar.**

### <a name="asset-unitypackage-files"></a>Archivos de recursos (.unitypackage)

Si se ha eliminado la carpeta SceneSystemResources o se ha deseleccionado durante la importación, se puede recuperar mediante los pasos siguientes:

- Seleccionar recursos  >  **Import Package** Custom  >  **Package**
- Abra **Microsoft.MixedReality.Toolkit. Paquete foundation**
- Asegúrese de **que Services/SceneSystem/SceneSystemResources** y todas las opciones secundarias están seleccionadas.

  ![Volver a importar recursos del sistema de escena](../images/scene-system/ReimportSceneSystemResources.png)

- Seleccione **Importar.**

## <a name="how-to-use-the-scene-system"></a>Uso del sistema de escena

- [Tipos de escena](scene-system-scene-types.md)
- [Carga de escena de contenido](scene-system-content-loading.md)
- [Supervisión de la carga de contenido](scene-system-load-progress.md)
- [Carga de escena de iluminación](scene-system-lighting-scenes.md)

## <a name="editor-settings"></a>Configuración del editor

De forma predeterminada, scene system aplica varios comportamientos en el editor de Unity. Si encuentra cualquiera de estos comportamientos con mucha mano, se pueden deshabilitar en la sección **Editor Configuración** del perfil del sistema de escena.

- `Editor Manage Build Settings:` Si es true, el servicio actualizará la configuración de compilación automáticamente, lo que garantiza que se agregan todas las escenas de contenido, iluminación y administrador. Deshabilite esta opción si desea un control total sobre la configuración de compilación.

- `Editor Enforce Scene Order:` Si es true, el servicio se asegurará de que la escena del administrador se muestra primero en la jerarquía de la escena, seguido de iluminación y, a continuación, contenido. Deshabilite esta opción si desea un control total sobre la jerarquía de escena.

- `Editor Manage Loaded Scenes:` Si es true, el servicio garantizará que siempre se carguen el administrador, el contenido y las escenas de iluminación. Deshabilite si desea un control total sobre las escenas que se cargan en el editor.

- `Editor Enforce Lighting Scene Types:` Si es true, el servicio se asegurará de que solo se permiten los componentes relacionados con la iluminación definidos en `PermittedLightingSceneComponentTypes` en las escenas de iluminación. Deshabilite si desea un control total sobre el contenido de las escenas de iluminación.

![Configuración del editor del sistema de escena](../images/scene-system/MRTK_SceneSystemProfileEditorSettings.PNG)
