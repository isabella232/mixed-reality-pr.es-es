---
title: Tipos de escenas del sistema de escenas
description: Documentación sobre diferentes tipos de escena en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: be34110c693c749535f6bfcd0411ecbd0bafc3bb48ab2392b3635c2e86a4dfb1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203335"
---
# <a name="scene-types"></a>Tipos de escena

Las escenas se han dividido en tres tipos y cada tipo tiene una función diferente.

![Sistema de escena en la jerarquía](../images/scene-system/MRTK_SceneSystemEditorSceneHierarchy.PNG)

## <a name="content-scenes"></a>Escenas de contenido

Estas son las escenas con las que está acostumbrado. Cualquier tipo de contenido se puede almacenar en ellos y se puede cargar o descargar en cualquier combinación.

Las escenas de contenido están habilitadas de forma predeterminada. El servicio puede cargar o descargar cualquier escena incluida en la matriz `Content Scenes` del perfil.

___

## <a name="manager-scenes"></a>Escenas de administrador

Una sola escena con una instancia de MixedRealityToolkit necesaria. Esta escena se cargará primero en el inicio y permanecerá cargada durante la vigencia de la aplicación. La escena del administrador también puede hospedar otros objetos que nunca deben destruirse. Esta es la alternativa preferida a DontDestroyOnLoad.

Para habilitar esta característica, compruebe `Use Manager Scene` el perfil y arrastre un objeto de escena al `Manager Scene` campo.

___

## <a name="lighting-scenes"></a>Escenas de iluminación

Conjunto de escenas que almacenan información de iluminación y objetos de iluminación. Solo se puede cargar uno a la vez y su configuración se puede combinar durante las cargas para realizar transiciones de iluminación fluidas.

La configuración de iluminación de Unity (luz ambiente, skyboxes, etc.) puede ser difícil de administrar al usar la carga aditiva porque están asociadas a escenas individuales y el comportamiento de invalidación no es sencillo. En la práctica, esto puede causar confusión cuando los recursos se crearon en condiciones de iluminación que no se obtienen en tiempo de ejecución.

![Configuración de iluminación del sistema de escena](../images/scene-system/MRTK_SceneSystemLightingSettings.PNG)

El sistema de escena usa escenas de iluminación para garantizar que esta configuración siga siendo coherente independientemente de las escenas que se carguen o activen, tanto en modo de edición como en modo de reproducción.

Para habilitar esta característica, compruebe `Use Lighting Scene` el perfil y rellene la `Lighting Scenes` matriz.

### <a name="cached-lighting-settings"></a>Configuración de iluminación almacenada en caché

El perfil almacena copias almacenadas en caché de la configuración de iluminación que se mantiene en las escenas de iluminación. Si esa configuración cambia en las escenas de iluminación, deberá actualizar la memoria caché para asegurarse de que la iluminación aparece según lo previsto en el modo de reproducción. El perfil mostrará una advertencia cuando sospeche que la configuración almacenada en caché no está actualizada. Al hacer clic, se cargará cada una de las escenas `Update Cached Lighting Settings` de iluminación, se extraerá su configuración y, a continuación, se almacenará en el perfil.

![Configuración de iluminación almacenada en caché del sistema de escena](../images/scene-system/MRTK_SceneSystemCachedLightingSettings.PNG)

### <a name="editor-behavior"></a>Comportamiento del editor

Una ventaja de usar escenas de iluminación es saber que el contenido está encendido correctamente durante la edición. Con este fin, scene service mantendrá una escena de iluminación cargada en todo momento y copiará la configuración de iluminación de esa escena en la escena activa actual.\*

Para cambiar la escena de iluminación que se carga, abra el inspector de servicio del sistema de [escena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) En el modo de edición, puede realizar una transición instantánea entre escenas de iluminación. En el modo de reproducción, puede obtener una vista previa de las transiciones.

![Inspector del sistema de escena](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

\**Nota: Normalmente, la escena activa determina la configuración de iluminación en el editor. Sin embargo, se decide no usar esta característica para aplicar la configuración de iluminación, ya que la escena activa también es donde los objetos recién creados se colocan de forma predeterminada, y las escenas de iluminación solo pueden contener componentes de iluminación. En su lugar, la configuración de la escena de iluminación actual se copia automáticamente en la configuración de la escena activa. Tenga en cuenta que esto dará lugar a que la configuración de iluminación de la escena de contenido se sobresalte.*
