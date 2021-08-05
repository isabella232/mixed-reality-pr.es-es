---
title: Persistencia en Unity
description: La persistencia permite anclar hologramas individuales del usuario donde quiera y, a continuación, encontrarlos más adelante en muchos usos de la aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistencia, Unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 9283191c024cbe33ecda3946a4e9bcbd5f3708c21a3578484b547207ee70a49b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208975"
---
# <a name="persistence-in-unity"></a>Persistencia en Unity

**Espacio de nombres:** *UnityEngine.XR.WSA.Persistence*<br>
**Clase:** *WorldAnchorStore*

WorldAnchorStore es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real en las instancias de la aplicación. A continuación, los usuarios pueden anclar hologramas individuales donde quieran y encontrarlos más adelante en el mismo lugar en muchos usos de la aplicación.

## <a name="how-to-persist-holograms-across-sessions"></a>Conservación de hologramas entre sesiones

WorldAnchorStore le permitirá conservar la ubicación de WorldAnchor entre sesiones. Para conservar los hologramas en las sesiones, deberá realizar un seguimiento por separado de los objetos GameObject que usan un delimitador de mundo determinado. A menudo tiene sentido crear una raíz de GameObject con un delimitador de mundo y tener hologramas secundarios delimitados por él con un desplazamiento de posición local.

Para cargar hologramas de sesiones anteriores:
1. Obtener WorldAnchorStore
2. Carga de datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial.
3. Carga de un delimitador de mundo desde su identificador

Para guardar hologramas para sesiones futuras:
1. Obtener WorldAnchorStore
2. Guardar un delimitador de mundo especificando un identificador
3. Guardar los datos de la aplicación relacionados con el anclaje mundial junto con un identificador

### <a name="getting-the-worldanchorstore"></a>Obtención de WorldAnchorStore

Querrá mantener una referencia a WorldAnchorStore para saber cuándo está listo para realizar una operación. Puesto que se trata de una llamada asincrónica, posiblemente en cuanto se inicie, querrá llamar a:

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded en este caso es nuestro controlador cuando WorldAnchorStore ha completado la carga:

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar anclajes de mundo específicos.

### <a name="saving-a-worldanchor"></a>Guardar un WorldAnchor

Para guardar, basta con nombrar lo que guardamos y pasarlo en el WorldAnchor que hemos conseguido antes cuando queremos guardar. Nota: Se producirá un error al intentar guardar dos delimitadores en la misma cadena (almacenar. Guardar devolverá false). Elimine el guardado anterior antes de guardar el nuevo:

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>Carga de un WorldAnchor

Y para cargar:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

Además, podemos usar store. Delete() para quitar un delimitador que hemos guardado y almacenado previamente. Clear() para quitar todos los datos guardados previamente.

### <a name="enumerating-existing-anchors"></a>Enumeración de delimitadores existentes

Para detectar delimitadores almacenados previamente, llame a GetAllIds.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>Conservación de hologramas para varios dispositivos

Puede usar <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors para</a> crear un anclaje de nube duradero a partir de un WorldAnchor local, que la aplicación puede encontrar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si esos dispositivos no están presentes juntos al mismo tiempo.  Dado que los delimitadores de nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.

Para empezar a crear experiencias compartidas en Unity, pruebe los inicios rápidos de 5 minutos <a href="/azure/spatial-anchors/unity-overview" target="_blank">de Azure Spatial Anchors Unity.</a>

Una vez que esté en funcionamiento con Azure Spatial Anchors, puede crear <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">y buscar anclajes en Unity.</a>

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, se encuentra a punto de explorar Mixed Reality bloques de creación principales. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Asignación espacial](spatial-mapping-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulte también
* [Persistencia del delimitador espacial](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de Azure Spatial Anchors para Unity</a>