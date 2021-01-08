---
title: Habilitación de la colocación de modelos 3D en el hogar
description: Obtenga información sobre cómo colocar modelos 3D desde su sitio web o aplicación en la Página principal de Windows Mixed Reality.
author: thmignon
ms.author: thmignon
ms.date: 05/04/2018
ms.topic: article
keywords: 3D, modelo, lugar en casa, lugar, mundo, modelado, Inicio de la realidad mixta, Web, aplicación, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: c92ba7a3242b618b9ef9cef01ae400cf4dbf36b2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010105"
---
# <a name="enable-placement-of-3d-models-in-the-mixed-reality-home"></a><span data-ttu-id="e07e4-104">Habilitación de la colocación de modelos 3D en el ambiente principal</span><span class="sxs-lookup"><span data-stu-id="e07e4-104">Enable placement of 3D models in the mixed reality home</span></span>

> [!NOTE]
> <span data-ttu-id="e07e4-105">Esta característica se agregó como parte de la [actualización 2018 de abril de Windows 10](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span><span class="sxs-lookup"><span data-stu-id="e07e4-105">This feature was added as part of the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018).</span></span> <span data-ttu-id="e07e4-106">Las versiones anteriores de Windows no son compatibles con esta característica.</span><span class="sxs-lookup"><span data-stu-id="e07e4-106">Older versions of Windows are not compatible with this feature.</span></span>

<span data-ttu-id="e07e4-107">La [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e07e4-107">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="e07e4-108">En algunos escenarios, las aplicaciones 2D (como la aplicación de hologramas) permiten colocar los modelos 3D directamente en la Página principal de la realidad mixta como decoración o para realizar más inspecciones en 3D completo.</span><span class="sxs-lookup"><span data-stu-id="e07e4-108">In some scenarios, 2D apps (like the Holograms app) enable placement of 3D models directly into the mixed reality home as decorations or for further inspection in full 3D.</span></span> <span data-ttu-id="e07e4-109">El *Protocolo agregar modelo* le permite enviar un modelo 3D desde su sitio web o aplicación directamente a la Página principal de Windows Mixed Reality, donde se conservará como [iniciadores de aplicaciones 3D](3d-app-launcher-design-guidance.md), aplicaciones 2D y hologramas.</span><span class="sxs-lookup"><span data-stu-id="e07e4-109">The *add model protocol* allows you to send a 3D model from your website or application directly into the Windows Mixed Reality home, where it will persist like [3D app launchers](3d-app-launcher-design-guidance.md), 2D apps, and holograms.</span></span> 

<span data-ttu-id="e07e4-110">Por ejemplo, si está desarrollando una aplicación que muestra un catálogo de mobiliario 3D para diseñar un espacio, use el *Protocolo agregar modelo* para permitir que los usuarios coloquen los modelos de mobiliario 3D del catálogo.</span><span class="sxs-lookup"><span data-stu-id="e07e4-110">For example, if you're developing an application that surfaces a catalog of 3D furniture for designing a space, use the *add model protocol* to allow users to place those 3D furniture models from the catalog.</span></span> <span data-ttu-id="e07e4-111">Una vez colocado en el mundo, los usuarios pueden moverse, cambiar de tamaño y quitar estos modelos 3D igual que otros hologramas en el hogar.</span><span class="sxs-lookup"><span data-stu-id="e07e4-111">Once placed in the world, users can move, resize, and remove these 3D models just like other holograms in the home.</span></span> <span data-ttu-id="e07e4-112">En este artículo se proporciona información general sobre la implementación del *Protocolo de incorporación de modelos* para permitir a los usuarios decorar su mundo con objetos 3D desde la aplicación o la Web.</span><span class="sxs-lookup"><span data-stu-id="e07e4-112">This article provides an overview of implementing the *add model protocol* for enabling users to decorate their world with 3D objects from your app or the web.</span></span>

## <a name="device-support"></a><span data-ttu-id="e07e4-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e07e4-113">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e07e4-114"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="e07e4-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e07e4-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="e07e4-115"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="e07e4-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="e07e4-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e07e4-117">Agregar protocolo de modelo</span><span class="sxs-lookup"><span data-stu-id="e07e4-117">Add model protocol</span></span></td>
        <td><span data-ttu-id="e07e4-118">✔️</span><span class="sxs-lookup"><span data-stu-id="e07e4-118">✔️</span></span></td>
        <td><span data-ttu-id="e07e4-119">✔️</span><span class="sxs-lookup"><span data-stu-id="e07e4-119">✔️</span></span></td>
    </tr>
</table>

## <a name="the-basics"></a><span data-ttu-id="e07e4-120">Conceptos básicos</span><span class="sxs-lookup"><span data-stu-id="e07e4-120">The basics</span></span>

<span data-ttu-id="e07e4-121">Hay dos pasos para habilitar la selección de ubicación de modelos 3D en la Página principal de Windows Mixed Reality:</span><span class="sxs-lookup"><span data-stu-id="e07e4-121">There are two steps to enabling the placement of 3D models in the Windows Mixed Reality home:</span></span>
1. <span data-ttu-id="e07e4-122">[Asegúrese de que el modelo 3D es compatible con la Página principal de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span><span class="sxs-lookup"><span data-stu-id="e07e4-122">[Ensure your 3D model is compatible with the Windows Mixed Reality home](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md).</span></span>
2. <span data-ttu-id="e07e4-123">Implemente el *Protocolo de adición de modelos* en la aplicación o la página web (este artículo).</span><span class="sxs-lookup"><span data-stu-id="e07e4-123">Implement the *add model protocol* in your application or webpage (this article).</span></span>

## <a name="implementing-the-add-model-protocol"></a><span data-ttu-id="e07e4-124">Implementación del *Protocolo Add Model*</span><span class="sxs-lookup"><span data-stu-id="e07e4-124">Implementing the *add model protocol*</span></span>

<span data-ttu-id="e07e4-125">Una vez que tenga un [modelo 3D compatible](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), puede implementar el *Protocolo agregar modelo* activando el URI siguiente desde cualquier página web o aplicación:</span><span class="sxs-lookup"><span data-stu-id="e07e4-125">Once you have a [compatible 3D model](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md), you can implement the *add model protocol* by activating the following URI from any webpage or application:</span></span>

```
ms-mixedreality:addmodel?uri=<Path to a .glb 3D model either local or remote>
```

<span data-ttu-id="e07e4-126">Si el URI apunta a un recurso remoto, se descargará automáticamente y se colocará en el hogar.</span><span class="sxs-lookup"><span data-stu-id="e07e4-126">If the URI points to a remote resource, then it will automatically be downloaded and placed in the home.</span></span> <span data-ttu-id="e07e4-127">Los recursos locales se copiarán en la carpeta de datos de la aplicación de la Página principal de la realidad mixta antes de colocarse en el hogar.</span><span class="sxs-lookup"><span data-stu-id="e07e4-127">Local resources will be copied to the mixed reality home's app data folder before being placed in the home.</span></span> <span data-ttu-id="e07e4-128">Se recomienda diseñar su experiencia para tener en cuenta los escenarios en los que el usuario podría estar ejecutando una versión anterior de Windows que no admita esta característica ocultando el botón o deshabilitando si es posible.</span><span class="sxs-lookup"><span data-stu-id="e07e4-128">We recommend designing your experience to account for scenarios where the user might be running an older version of Windows that doesn't support this feature by hiding the button or disabling it if possible.</span></span> 

### <a name="invoking-the-add-model-protocol-from-a-universal-windows-platform-app"></a><span data-ttu-id="e07e4-129">Invocar el *Protocolo agregar modelo* desde una aplicación plataforma universal de Windows:</span><span class="sxs-lookup"><span data-stu-id="e07e4-129">Invoking the *add model protocol* from a Universal Windows Platform app:</span></span>

```C#
private async void launchURI_Click(object sender, RoutedEventArgs e)
{
   // Define the add model URI
   var uriAddModel = new Uri(@"ms-mixedreality:addModel?uri=sample.glb");

   // Launch the URI to invoke the placement
   var success = await Windows.System.Launcher.LaunchUriAsync(uriAddModel);

   if (success)
   {
      // URI launched
   }
   else
   {
      // URI launch failed
   }
}
```

### <a name="invoking-the-add-model-protocol-from-a-webpage"></a><span data-ttu-id="e07e4-130">Invocar el *Protocolo de agregar modelo* desde una página web:</span><span class="sxs-lookup"><span data-stu-id="e07e4-130">Invoking the *add model protocol* from a webpage:</span></span>

```html
<a class="btn btn-default" href="ms-mixedreality:addModel?uri=sample.glb"> Place 3D Model </a>
```

## <a name="considerations-for-immersive-vr-headsets"></a><span data-ttu-id="e07e4-131">Consideraciones sobre los auriculares envolventes (VR)</span><span class="sxs-lookup"><span data-stu-id="e07e4-131">Considerations for immersive (VR) headsets</span></span>

* <span data-ttu-id="e07e4-132">En el caso de los auriculares envolventes (VR), el portal de realidad mixta no tiene que estar en ejecución antes de invocar el *Protocolo de adición del modelo*.</span><span class="sxs-lookup"><span data-stu-id="e07e4-132">For immersive (VR) headsets, the Mixed Reality Portal doesn't have to be running before invoking the *add model protocol*.</span></span> <span data-ttu-id="e07e4-133">En este caso, el *Protocolo de adición del modelo* iniciará el portal de realidad mixta y colocará el objeto directamente, donde el casco está mirando una vez que llega a la Página principal de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="e07e4-133">In this case, the *add model protocol* will launch the Mixed Reality Portal and place the object directly where the headset is looking once you arrive in the mixed reality home.</span></span> 
* <span data-ttu-id="e07e4-134">Al invocar el *Protocolo agregar modelo* desde el escritorio con el portal de realidad mixta que ya se está ejecutando, asegúrese de que el casco esté "activo".</span><span class="sxs-lookup"><span data-stu-id="e07e4-134">When invoking the *add model protocol* from the desktop with the Mixed Reality Portal already running, ensure that the headset is "awake".</span></span> <span data-ttu-id="e07e4-135">Si no es así, la selección de ubicación no se realizará correctamente.</span><span class="sxs-lookup"><span data-stu-id="e07e4-135">If not, the placement won't succeed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="e07e4-136">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e07e4-136">See also</span></span>

* [<span data-ttu-id="e07e4-137">Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e07e4-137">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="e07e4-138">Desplazamiento por la página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e07e4-138">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
