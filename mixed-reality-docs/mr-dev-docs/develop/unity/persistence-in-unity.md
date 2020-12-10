---
title: Persistencia en Unity
description: La persistencia permite que el usuario ancle los hologramas individuales donde quiera y, después, buscarlo más adelante en muchos usos de la aplicación.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistencia, Unity, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: d74f9c0a118c1886037c564073742ebedc7d0146
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010446"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="b73f0-104">Persistencia en Unity</span><span class="sxs-lookup"><span data-stu-id="b73f0-104">Persistence in Unity</span></span>

<span data-ttu-id="b73f0-105">**Espacio de nombres:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="b73f0-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="b73f0-106">**Clase:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="b73f0-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="b73f0-107">WorldAnchorStore es la clave para crear experiencias holográficas en las que los hologramas permanecen en posiciones específicas del mundo real entre instancias de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b73f0-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="b73f0-108">Después, los usuarios pueden anclar los hologramas individuales dondequiera que quieran y encontrarlos más adelante en el mismo punto en muchos usos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b73f0-108">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="b73f0-109">Cómo conservar los hologramas entre sesiones</span><span class="sxs-lookup"><span data-stu-id="b73f0-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="b73f0-110">El WorldAnchorStore le permitirá conservar la ubicación de los WorldAnchor de las sesiones.</span><span class="sxs-lookup"><span data-stu-id="b73f0-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="b73f0-111">Para conservar los hologramas en todas las sesiones, deberá realizar un seguimiento por separado de los GameObjects que usan un delimitador mundial determinado.</span><span class="sxs-lookup"><span data-stu-id="b73f0-111">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="b73f0-112">A menudo tiene sentido crear una raíz GameObject con un delimitador mundial y tener los hologramas secundarios anclados por él con un desplazamiento de posición local.</span><span class="sxs-lookup"><span data-stu-id="b73f0-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="b73f0-113">Para cargar hologramas de sesiones anteriores:</span><span class="sxs-lookup"><span data-stu-id="b73f0-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="b73f0-114">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b73f0-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="b73f0-115">Cargar datos de la aplicación relacionados con el anclaje mundial, que le proporciona el identificador del anclaje mundial</span><span class="sxs-lookup"><span data-stu-id="b73f0-115">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="b73f0-116">Carga de un delimitador mundial desde su identificador</span><span class="sxs-lookup"><span data-stu-id="b73f0-116">Load a world anchor from its ID</span></span>

<span data-ttu-id="b73f0-117">Para guardar los hologramas para las sesiones futuras:</span><span class="sxs-lookup"><span data-stu-id="b73f0-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="b73f0-118">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b73f0-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="b73f0-119">Guardar un delimitador mundial especificando un identificador</span><span class="sxs-lookup"><span data-stu-id="b73f0-119">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="b73f0-120">Guardar datos de la aplicación relacionados con el delimitador mundial junto con un identificador</span><span class="sxs-lookup"><span data-stu-id="b73f0-120">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="b73f0-121">Obtención de WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="b73f0-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="b73f0-122">Querrá mantener una referencia a WorldAnchorStore para que sepa cuándo está listo para realizar una operación.</span><span class="sxs-lookup"><span data-stu-id="b73f0-122">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="b73f0-123">Dado que se trata de una llamada asincrónica, posiblemente en cuanto se inicia, desea llamar a:</span><span class="sxs-lookup"><span data-stu-id="b73f0-123">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="b73f0-124">En este caso, StoreLoaded es el controlador para cuando se haya completado la carga de WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="b73f0-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="b73f0-125">Ahora tenemos una referencia a WorldAnchorStore, que usaremos para guardar y cargar delimitadores del mundo específicos.</span><span class="sxs-lookup"><span data-stu-id="b73f0-125">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="b73f0-126">Guardar un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="b73f0-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="b73f0-127">Para ahorrar, simplemente necesitamos asignar un nombre a lo que estamos guardando y pasarlo en el WorldAnchor que obtuvimos antes cuando queremos ahorrar.</span><span class="sxs-lookup"><span data-stu-id="b73f0-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="b73f0-128">Nota: Si intenta guardar dos delimitadores en la misma cadena, se producirá un error (Store. Save devolverá FALSE).</span><span class="sxs-lookup"><span data-stu-id="b73f0-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="b73f0-129">Elimine el guardado anterior antes de guardar el nuevo:</span><span class="sxs-lookup"><span data-stu-id="b73f0-129">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="b73f0-130">Carga de un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="b73f0-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="b73f0-131">Y para cargar:</span><span class="sxs-lookup"><span data-stu-id="b73f0-131">And to load:</span></span>

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

<span data-ttu-id="b73f0-132">Además, podemos usar Store. Elimine () para quitar un delimitador que se guardó y almacenó anteriormente. Borre () para quitar todos los datos guardados previamente.</span><span class="sxs-lookup"><span data-stu-id="b73f0-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="b73f0-133">Enumerar delimitadores existentes</span><span class="sxs-lookup"><span data-stu-id="b73f0-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="b73f0-134">Para detectar los delimitadores almacenados previamente, llame a GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="b73f0-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="b73f0-135">Persistencia de hologramas para varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="b73f0-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="b73f0-136">Puede usar los <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a> para crear un delimitador de la nube durable desde un WorldAnchor local, que la aplicación puede ubicar a continuación en varios dispositivos HoloLens, iOS y Android, incluso si dichos dispositivos no están presentes juntos al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="b73f0-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="b73f0-137">Dado que los delimitadores en la nube son persistentes, varios dispositivos a lo largo del tiempo pueden ver el contenido representado en relación con ese delimitador en la misma ubicación física.</span><span class="sxs-lookup"><span data-stu-id="b73f0-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="b73f0-138">Para empezar a crear experiencias compartidas en Unity, pruebe las guías de <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Inicio rápido</a>de 5 minutos de anclaje espacial de Azure.</span><span class="sxs-lookup"><span data-stu-id="b73f0-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="b73f0-139">Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y buscar delimitadores en Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="b73f0-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b73f0-140">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="b73f0-140">Next Development Checkpoint</span></span>

<span data-ttu-id="b73f0-141">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar los bloques de creación principales de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b73f0-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="b73f0-142">Desde aquí, puede continuar con el siguiente bloque de creación:</span><span class="sxs-lookup"><span data-stu-id="b73f0-142">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b73f0-143">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="b73f0-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="b73f0-144">O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:</span><span class="sxs-lookup"><span data-stu-id="b73f0-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b73f0-145">Experiencias compartidas</span><span class="sxs-lookup"><span data-stu-id="b73f0-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="b73f0-146">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="b73f0-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b73f0-147">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b73f0-147">See Also</span></span>
* [<span data-ttu-id="b73f0-148">Persistencia del delimitador espacial</span><span class="sxs-lookup"><span data-stu-id="b73f0-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="b73f0-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="b73f0-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="b73f0-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">SDK de anclajes espaciales de Azure para Unity</a></span><span class="sxs-lookup"><span data-stu-id="b73f0-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
