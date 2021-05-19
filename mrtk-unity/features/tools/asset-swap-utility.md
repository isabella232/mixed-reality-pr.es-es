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
# <a name="asset-swap-utility"></a><span data-ttu-id="0da3e-104">Utilidad de intercambio de recursos</span><span class="sxs-lookup"><span data-stu-id="0da3e-104">Asset swap utility</span></span>

<span data-ttu-id="0da3e-105">Buscar y reemplazar es ubicuo cuando se trabaja en herramientas de creación de texto y contenido.</span><span class="sxs-lookup"><span data-stu-id="0da3e-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="0da3e-106">Cuando necesite intercambiar muchos recursos dentro de una escena de Unity, aquí es donde [assetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) y el editor pueden echar una mano.</span><span class="sxs-lookup"><span data-stu-id="0da3e-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="0da3e-107">La utilidad se incluye con el `Microsoft.MixedReality.Toolkit.Unity.Tools` paquete.</span><span class="sxs-lookup"><span data-stu-id="0da3e-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="0da3e-108">guarda todas las acciones de buscar y reemplazar como ScriptableObject para que sea una trival intercambiar entre sí o guardar "temas" de intercambio para su `AssetSwapUtility` uso futuro.</span><span class="sxs-lookup"><span data-stu-id="0da3e-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="0da3e-109">Intercambio de recursos</span><span class="sxs-lookup"><span data-stu-id="0da3e-109">Swapping assets</span></span>

<span data-ttu-id="0da3e-110">El intercambio de recursos es fácil una vez que se ha creado `AssetSwapCollection` un .</span><span class="sxs-lookup"><span data-stu-id="0da3e-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="0da3e-111">Vamos a demostrar el uso mediante el intercambio de dos cubos rojos con dos esferas azules en una escena.</span><span class="sxs-lookup"><span data-stu-id="0da3e-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="0da3e-112">En primer lugar, agregue dos cubos rojos a la escena que usen el cubo de Unity predeterminado y el `MRTK_Standard_Red` material.</span><span class="sxs-lookup"><span data-stu-id="0da3e-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="0da3e-113">Para crear un , vaya a `AssetSwapCollection` Mixed Reality Toolkit > Utilities > Create Asset Swap **Collection**.</span><span class="sxs-lookup"><span data-stu-id="0da3e-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="0da3e-114">Con el `AssetSwapCollection` seleccionado, rellene las propiedades como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="0da3e-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Colección de intercambio de recursos en el editor de Unity](images/asset-swap-img-01.png)

<span data-ttu-id="0da3e-116">A continuación, seleccione "Esferas azules" en la lista desplegable "Tema seleccionado" y presione "Aplicar".</span><span class="sxs-lookup"><span data-stu-id="0da3e-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="0da3e-117">Todos los cubos rojos de la escena deben reemplazarse por esferas azules.</span><span class="sxs-lookup"><span data-stu-id="0da3e-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Colección de intercambio de recursos en el editor de Unity con el tema seleccionado resaltado](images/asset-swap-img-02.png)

<span data-ttu-id="0da3e-119">En este ejemplo hemos realizado un reemplazo completo de la escena, pero puede reemplazar partes de la escena cambiando el "Modo de selección".</span><span class="sxs-lookup"><span data-stu-id="0da3e-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="0da3e-120">También puede volver a cambiar a cubos rojos seleccionando "Cubos rojos" en la lista desplegable "Tema seleccionado" y presionando de nuevo "Aplicar".</span><span class="sxs-lookup"><span data-stu-id="0da3e-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="0da3e-121">Es posible intercambiar cualquier tipo de recurso, como archivos de audio, fuentes, prefabs, etc. realizará `AssetSwapUtility` algunas comprobaciones de integridad para asegurarse de que está intercambiando a tipos similares.</span><span class="sxs-lookup"><span data-stu-id="0da3e-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>