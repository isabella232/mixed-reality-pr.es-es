---
title: Utilidad de intercambio de recursos
description: Documentación sobre el uso de la utilidad de intercambio de recursos en MRTK para Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144135"
---
# <a name="asset-swap-utility"></a>Utilidad de intercambio de recursos

Buscar y reemplazar es ubicuo cuando se trabaja en herramientas de creación de texto y contenido. Cuando necesite intercambiar muchos recursos dentro de una escena de Unity, aquí es donde [assetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) y el editor pueden echar una mano. La utilidad se incluye con el `Microsoft.MixedReality.Toolkit.Unity.Tools` paquete.

guarda todas las acciones de buscar y reemplazar como ScriptableObject para que sea una trival intercambiar entre sí o guardar "temas" de intercambio para su `AssetSwapUtility` uso futuro.

## <a name="swapping-assets"></a>Intercambio de recursos

El intercambio de recursos es fácil una vez que se ha creado `AssetSwapCollection` un . Vamos a demostrar el uso mediante el intercambio de dos cubos rojos con dos esferas azules en una escena. En primer lugar, agregue dos cubos rojos a la escena que usen el cubo de Unity predeterminado y el `MRTK_Standard_Red` material.

Para crear un , vaya a `AssetSwapCollection` Mixed Reality Toolkit > Utilities > Create Asset Swap **Collection**. Con el `AssetSwapCollection` seleccionado, rellene las propiedades como se muestra en la imagen siguiente:

![Colección de intercambio de recursos en el editor de Unity](images/asset-swap-img-01.png)

A continuación, seleccione "Esferas azules" en la lista desplegable "Tema seleccionado" y presione "Aplicar". Todos los cubos rojos de la escena deben reemplazarse por esferas azules.

![Colección de intercambio de recursos en el editor de Unity con el tema seleccionado resaltado](images/asset-swap-img-02.png)

En este ejemplo hemos realizado un reemplazo completo de la escena, pero puede reemplazar partes de la escena cambiando el "Modo de selección". También puede volver a cambiar a cubos rojos seleccionando "Cubos rojos" en la lista desplegable "Tema seleccionado" y presionando de nuevo "Aplicar".

> [!NOTE]
> Es posible intercambiar cualquier tipo de recurso, como archivos de audio, fuentes, prefabs, etc. realizará `AssetSwapUtility` algunas comprobaciones de integridad para asegurarse de que está intercambiando a tipos similares.