---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)
description: Aprenda a crear iniciadores de aplicaciones 3D y logotipos para aplicaciones y juegos UWP de Windows Mixed Reality en los auriculares HoloLens y VR.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, selector 3D, mosaico, cubo activo, vínculo profundo, secondarytile, mosaico secundario, UWP, auricular de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, XML, cuadro de límite, Unity
ms.openlocfilehash: 40a68d0835ec8fb92d6417650700f41e8a31aab6
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009685"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a><span data-ttu-id="4d651-104">Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)</span><span class="sxs-lookup"><span data-stu-id="4d651-104">Implement 3D app launchers (UWP apps)</span></span>

> [!NOTE]
> <span data-ttu-id="4d651-105">Esta característica se agregó como parte de la actualización de 2017 Fall Creators Update (RS3) para los auriculares más envolventes y es compatible con HoloLens con la actualización de Windows 10 de abril de 2018.</span><span class="sxs-lookup"><span data-stu-id="4d651-105">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive headsets and is supported by HoloLens with the  Windows 10 April 2018 Update.</span></span> <span data-ttu-id="4d651-106">Asegúrese de que la aplicación tiene como destino una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4d651-106">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive Headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="4d651-107">Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="4d651-107">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

<span data-ttu-id="4d651-108">La [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) es el punto de partida en el que los usuarios se colocan antes de iniciar las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4d651-108">The [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) is the starting point where users land before launching applications.</span></span> <span data-ttu-id="4d651-109">Al crear una aplicación para UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras bidimensionales con el logotipo de su aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-109">When creating a UWP application for Windows Mixed Reality, by default, apps are launched as 2D slates with their app's logo.</span></span> <span data-ttu-id="4d651-110">Al desarrollar experiencias para Windows Mixed Reality, opcionalmente se puede definir un selector 3D para invalidar el iniciador de 2D predeterminado de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-110">When developing experiences for Windows Mixed Reality, a 3D launcher can optionally be defined to override the default 2D launcher for your application.</span></span> <span data-ttu-id="4d651-111">En general, los iniciadores 3D se recomiendan para iniciar aplicaciones envolventes que sacan provecho de la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4d651-111">In general, 3D launchers are recommended for launching immersive applications that take users out of the Windows Mixed Reality home.</span></span> <span data-ttu-id="4d651-112">Se prefiere el selector de 2D predeterminado cuando la aplicación está activada en contexto.</span><span class="sxs-lookup"><span data-stu-id="4d651-112">The default 2D launcher is preferred when the app is activated in place.</span></span> <span data-ttu-id="4d651-113">También puede crear un [vínculo profundo en 3D (secondaryTile)](#3d-deep-links-secondarytiles) como un selector 3D para el contenido de una aplicación de UWP en 2D.</span><span class="sxs-lookup"><span data-stu-id="4d651-113">You can also create a [3D deep link (secondaryTile)](#3d-deep-links-secondarytiles) as a 3D launcher to content within a 2D UWP app.</span></span>

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="4d651-114">proceso de creación del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="4d651-114">3D app launcher creation process</span></span>

<span data-ttu-id="4d651-115">Hay tres pasos para crear un iniciador de aplicaciones 3D:</span><span class="sxs-lookup"><span data-stu-id="4d651-115">There are three steps to creating a 3D app launcher:</span></span>
1. [<span data-ttu-id="4d651-116">Diseño y concepto</span><span class="sxs-lookup"><span data-stu-id="4d651-116">Designing and concepting</span></span>](3d-app-launcher-design-guidance.md)
2. [<span data-ttu-id="4d651-117">Modelado y exportación</span><span class="sxs-lookup"><span data-stu-id="4d651-117">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="4d651-118">Integrarlo en la aplicación (este artículo)</span><span class="sxs-lookup"><span data-stu-id="4d651-118">Integrating it into your application (this article)</span></span>

<span data-ttu-id="4d651-119">los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las [directrices de creación de Windows Mixed Reality](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) para garantizar la compatibilidad.</span><span class="sxs-lookup"><span data-stu-id="4d651-119">3D assets to be used as launchers for your application should be authored using the [Windows Mixed Reality authoring guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) to ensure compatibility.</span></span> <span data-ttu-id="4d651-120">Los recursos que no cumplan esta especificación de creación no se representarán en la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4d651-120">Assets that fail to meet this authoring specification won't be rendered in the Windows Mixed Reality home.</span></span>

## <a name="configuring-the-3d-launcher"></a><span data-ttu-id="4d651-121">Configurar el iniciador 3D</span><span class="sxs-lookup"><span data-stu-id="4d651-121">Configuring the 3D launcher</span></span>

<span data-ttu-id="4d651-122">Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-122">When you create a new project in Visual Studio, it creates a simple default tile that displays your app's name and logo.</span></span> <span data-ttu-id="4d651-123">Para reemplazar esta representación 2D por un modelo 3D personalizado, edite el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición del mosaico predeterminado.</span><span class="sxs-lookup"><span data-stu-id="4d651-123">To replace this 2D representation with a custom 3D model edit the app manifest of your application to include the “MixedRealityModel” element as part of your default tile definition.</span></span> <span data-ttu-id="4d651-124">Para revertir al iniciador de 2D, solo tiene que quitar la definición de MixedRealityModel del manifiesto.</span><span class="sxs-lookup"><span data-stu-id="4d651-124">To revert to the 2D launcher just remove the MixedRealityModel definition from the manifest.</span></span>

### <a name="xml"></a><span data-ttu-id="4d651-125">XML</span><span class="sxs-lookup"><span data-stu-id="4d651-125">XML</span></span>

<span data-ttu-id="4d651-126">En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual.</span><span class="sxs-lookup"><span data-stu-id="4d651-126">First, locate the app package manifest in your current project.</span></span> <span data-ttu-id="4d651-127">De forma predeterminada, el manifiesto se denominará package. appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="4d651-127">By default, the manifest will be named Package.appxmanifest.</span></span> <span data-ttu-id="4d651-128">Si usa Visual Studio, haga clic con el botón derecho en el manifiesto en el visor de soluciones y seleccione **Ver código fuente** para abrir el código XML y editarlo.</span><span class="sxs-lookup"><span data-stu-id="4d651-128">If you're using Visual Studio, then right-click the manifest in your solution viewer and select **View source** to open the xml for editing.</span></span> 

<span data-ttu-id="4d651-129">En la parte superior del manifiesto, agregue el esquema uap5 e inclúyalo como un espacio de nombres que se va a omitir:</span><span class="sxs-lookup"><span data-stu-id="4d651-129">At the top of the manifest, add the uap5 schema and include it as an ignorable namespace:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

<span data-ttu-id="4d651-130">A continuación, especifique "MixedRealityModel" en el icono predeterminado de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="4d651-130">Next specify the "MixedRealityModel" in the default tile for your application:</span></span>

```xml
<Applications>
    <Application Id="App"
      Executable="$targetnametoken$.exe"
      EntryPoint="ExampleApp.App">
      <uap:VisualElements
        DisplayName="ExampleApp"
        Square150x150Logo="Assets\Logo.png"
        Square44x44Logo="Assets\SmallLogo.png"
        Description="ExampleApp"
        BackgroundColor="#464646">
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb" />
        </uap:DefaultTile>
        <uap:SplashScreen Image="Assets\SplashScreen.png" />
      </uap:VisualElements>
    </Application>
</Applications>
```

<span data-ttu-id="4d651-131">El elemento MixedRealityModel acepta una ruta de acceso de archivo que apunta a un recurso 3D almacenado en el paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-131">The MixedRealityModel element accepts a file path pointing to a 3D asset stored in your app package.</span></span> <span data-ttu-id="4d651-132">Actualmente solo se admiten los modelos 3D que se entregan con el formato de archivo. glb y se crean con las [instrucciones de creación de recursos de Windows Mixed Reality 3D](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) .</span><span class="sxs-lookup"><span data-stu-id="4d651-132">Currently only 3D models delivered using the .glb file format and authored against the [Windows Mixed Reality 3D asset authoring instructions](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) are supported.</span></span> <span data-ttu-id="4d651-133">Los recursos deben almacenarse en el paquete de la aplicación y la animación no se admite actualmente.</span><span class="sxs-lookup"><span data-stu-id="4d651-133">Assets must be stored in the app package and animation isn't currently supported.</span></span> <span data-ttu-id="4d651-134">Si el parámetro "path" se deja en blanco, Windows mostrará la pizarra 2D en lugar del iniciador 3D.</span><span class="sxs-lookup"><span data-stu-id="4d651-134">If the “Path” parameter is left blank Windows will show the 2D slate instead of the 3D launcher.</span></span> <span data-ttu-id="4d651-135">**Nota:** el recurso. glb debe estar marcado como "contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-135">**Note:** the .glb asset must be marked as "Content" in your build settings before building and running your app.</span></span>


<span data-ttu-id="4d651-136">![Seleccione el. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación.](images/buildsetting-content-300px.png)</span><span class="sxs-lookup"><span data-stu-id="4d651-136">![Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings](images/buildsetting-content-300px.png)</span></span><br>
<span data-ttu-id="4d651-137">*Seleccione el. glb en el explorador de soluciones y use la sección Propiedades para marcarlo como "contenido" en la configuración de compilación.*</span><span class="sxs-lookup"><span data-stu-id="4d651-137">*Select the .glb in your solution explorer and use the properties section to mark it as "Content" in the build settings*</span></span>

### <a name="bounding-box"></a><span data-ttu-id="4d651-138">Rectángulo de selección</span><span class="sxs-lookup"><span data-stu-id="4d651-138">Bounding box</span></span>

<span data-ttu-id="4d651-139">Un cuadro de límite se puede usar para agregar opcionalmente una región de búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d651-139">A bounding box can be used to optionally add an extra buffer region around the object.</span></span> <span data-ttu-id="4d651-140">El cuadro de límite se especifica mediante un punto central y extensiones, que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje.</span><span class="sxs-lookup"><span data-stu-id="4d651-140">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="4d651-141">Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="4d651-141">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="4d651-142">Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d651-142">If a bounding box isn't provided, then one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="4d651-143">Si el cuadro de límite proporcionado es menor que el modelo, se cambiará de tamaño para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="4d651-143">If the provided bounding box is smaller than the model, then it will be resized to fit the mesh.</span></span>

<span data-ttu-id="4d651-144">La compatibilidad con el atributo de cuadro de límite incluirá la actualización de RS4 de Windows como una propiedad en el elemento MixedRealityModel.</span><span class="sxs-lookup"><span data-stu-id="4d651-144">Support for the bounding box attribute will come with the Windows RS4 update as a property on the MixedRealityModel element.</span></span> <span data-ttu-id="4d651-145">Para definir un cuadro de límite primero en la parte superior del manifiesto de la aplicación, agregue el esquema uap6 e inclúyalo como espacios de nombres que se van a omitir:</span><span class="sxs-lookup"><span data-stu-id="4d651-145">To define a bounding box first at the top of the app manifest add the uap6 schema and include it as ignorable namespaces:</span></span>

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
<span data-ttu-id="4d651-146">A continuación, en MixedRealityModel, establezca la propiedad SpatialBoundingBox para definir el cuadro de límite:</span><span class="sxs-lookup"><span data-stu-id="4d651-146">Next, on the MixedRealityModel set the SpatialBoundingBox property to define the bounding box:</span></span> 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a><span data-ttu-id="4d651-147">Con Unity</span><span class="sxs-lookup"><span data-stu-id="4d651-147">Using Unity</span></span>

<span data-ttu-id="4d651-148">Al trabajar con Unity, el proyecto se debe compilar y abrir en Visual Studio para poder editar el manifiesto de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d651-148">When working with Unity the project must be built and opened in Visual Studio before the App Manifest can be edited.</span></span> 

>[!NOTE]
><span data-ttu-id="4d651-149">El iniciador 3D debe volver a definirse en el manifiesto al compilar e implementar una nueva solución de Visual Studio desde Unity.</span><span class="sxs-lookup"><span data-stu-id="4d651-149">The 3D launcher must be redefined in the manifest when building and deploying a new Visual Studio solution from Unity.</span></span>

## <a name="3d-deep-links-secondarytiles"></a><span data-ttu-id="4d651-150">vínculos profundos 3D (secondaryTiles)</span><span class="sxs-lookup"><span data-stu-id="4d651-150">3D deep links (secondaryTiles)</span></span>

> [!NOTE]
> <span data-ttu-id="4d651-151">Esta característica se agregó como parte de 2017 Fall Creators Update (RS3) para auriculares envolventes (VR) y como parte de la actualización de abril de 2018 (RS4) para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4d651-151">This feature was added as part of the 2017 Fall Creators Update (RS3) for immersive (VR) headsets and as part of the April 2018 Update (RS4) for HoloLens.</span></span> <span data-ttu-id="4d651-152">Asegúrese de que la aplicación esté destinada a una versión de la Windows SDK mayor o igual que 10.0.16299 en auriculares inmersivo (VR) y 10.0.17125 en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4d651-152">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.16299 on immersive (VR) headsets and 10.0.17125 on HoloLens.</span></span> <span data-ttu-id="4d651-153">Puede encontrar el Windows SDK más reciente [aquí](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span><span class="sxs-lookup"><span data-stu-id="4d651-153">You can find the latest Windows SDK [here](https://developer.microsoft.com/windows/downloads/windows-10-sdk).</span></span>

>[!IMPORTANT]
><span data-ttu-id="4d651-154">los vínculos profundos 3D (secondaryTiles) solo funcionan con aplicaciones UWP de 2D.</span><span class="sxs-lookup"><span data-stu-id="4d651-154">3D deep links (secondaryTiles) only work with 2D UWP apps.</span></span> <span data-ttu-id="4d651-155">Sin embargo, puede crear un [iniciador de aplicaciones 3D](implementing-3d-app-launchers.md) para iniciar una aplicación exclusiva desde la Página principal de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="4d651-155">You can, however, create a [3D app launcher](implementing-3d-app-launchers.md) to launch an exclusive app from the Windows Mixed Reality home.</span></span>

<span data-ttu-id="4d651-156">Las aplicaciones 2D se pueden mejorar para Windows Mixed Reality agregando la capacidad de colocar modelos 3D desde la aplicación en la [Página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md) como vínculos profundos al contenido dentro de la aplicación 2D, al igual que los [mosaicos secundarios 2D](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) en el menú Inicio de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d651-156">Your 2D applications can be enhanced for Windows Mixed Reality by adding the ability to place 3D models from your app into the [Windows Mixed Reality home](../discover/navigating-the-windows-mixed-reality-home.md) as deep links to content within your 2D app, just like [2D secondary tiles](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) on the Windows Start menu.</span></span> <span data-ttu-id="4d651-157">Por ejemplo, puede crear fotoesferas 360 ° que se vinculan directamente a una aplicación de visor de fotos de 360 °, o bien permitir que los usuarios coloquen contenido 3D de una colección de recursos que abre una página de detalles sobre el autor.</span><span class="sxs-lookup"><span data-stu-id="4d651-157">For example, you can create 360° photospheres that link directly into a 360° photo viewer app, or let users place 3D content from a collection of assets that opens a details page about the author.</span></span> <span data-ttu-id="4d651-158">Se trata de un par de formas de ampliar la funcionalidad de la aplicación 2D con contenido 3D.</span><span class="sxs-lookup"><span data-stu-id="4d651-158">These are just a couple ways to expand the functionality of your 2D application with 3D content.</span></span>

### <a name="creating-a-3d-secondarytile"></a><span data-ttu-id="4d651-159">Crear un "secondaryTile" 3D</span><span class="sxs-lookup"><span data-stu-id="4d651-159">Creating a 3D “secondaryTile”</span></span>

<span data-ttu-id="4d651-160">Puede colocar contenido 3D de la aplicación mediante "secondaryTiles" definiendo un modelo de realidad mixta en el momento de la creación.</span><span class="sxs-lookup"><span data-stu-id="4d651-160">You can place 3D content from your application using “secondaryTiles” by defining a mixed reality model at creation time.</span></span> <span data-ttu-id="4d651-161">Los modelos de realidad mixta se crean haciendo referencia a un recurso 3D en el paquete de la aplicación y definiendo opcionalmente un cuadro de límite.</span><span class="sxs-lookup"><span data-stu-id="4d651-161">Mixed reality models are created by referencing a 3D asset in your app package and optionally defining a bounding box.</span></span> 

> [!NOTE]
> <span data-ttu-id="4d651-162">Actualmente no se admite la creación de "secondaryTiles" desde una vista exclusiva.</span><span class="sxs-lookup"><span data-stu-id="4d651-162">Creating “secondaryTiles” from within an exclusive view is not currently supported.</span></span>

```cs
using Windows.UI.StartScreen;
using Windows.Foundation.Numerics;
using Windows.Perception.Spatial;

// Initialize the tile
SecondaryTile tile = new SecondaryTile("myTileId")
{
    DisplayName = "My Tile",
    Arguments = "myArgs"
};

tile.VisualElements.Square150x150Logo = new Uri("ms-appx:///Assets/MyTile/Square150x150Logo.png");

//Assign 3D model (only ms-appx and ms-appdata are allowed)
TileMixedRealityModel model = tile.VisualElements.MixedRealityModel;
model.Uri = new Uri("ms-appx:///Assets/MyTile/MixedRealityModel.glb");
model.ActivationBehavior = TileMixedRealityModelActivationBehavior.Default;
model.BoundingBox = new SpatialBoundingBox
{
    Center = new Vector3 { X = 1, Y = 0, Z = 0 },
    Extents = new Vector3 { X = 3, Y = 5, Z = 4 }
};

// And place it
await tile.RequestCreateAsync();
```

### <a name="bounding-box"></a><span data-ttu-id="4d651-163">Rectángulo de selección</span><span class="sxs-lookup"><span data-stu-id="4d651-163">Bounding box</span></span>

<span data-ttu-id="4d651-164">Un cuadro de límite se puede usar para agregar una región de búfer adicional alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d651-164">A bounding box can be used to add an extra buffer region around the object.</span></span> <span data-ttu-id="4d651-165">El cuadro de límite se especifica mediante un punto central y extensiones, que indican la distancia desde el centro del cuadro de límite a sus bordes a lo largo de cada eje.</span><span class="sxs-lookup"><span data-stu-id="4d651-165">The bounding box is specified using a center point and extents, which indicate the distance from the center of the bounding box to its edges along each axis.</span></span> <span data-ttu-id="4d651-166">Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 metro.</span><span class="sxs-lookup"><span data-stu-id="4d651-166">Units for the bounding box can be mapped to 1 unit = 1 meter.</span></span> <span data-ttu-id="4d651-167">Si no se proporciona un cuadro de límite, uno se ajustará automáticamente a la malla del objeto.</span><span class="sxs-lookup"><span data-stu-id="4d651-167">If a bounding box isn't provided, one will be automatically fitted to the mesh of the object.</span></span> <span data-ttu-id="4d651-168">Si el cuadro de límite proporcionado es menor que el modelo, se cambiará de tamaño para ajustarse a la malla.</span><span class="sxs-lookup"><span data-stu-id="4d651-168">If the provided bounding box is smaller than the model, it will be resized to fit the mesh.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="4d651-169">Comportamiento de activación</span><span class="sxs-lookup"><span data-stu-id="4d651-169">Activation behavior</span></span>

> [!NOTE]
> <span data-ttu-id="4d651-170">Esta característica se admitirá a partir de la actualización de RS4 de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d651-170">This feature will be supported as of the Windows RS4 update.</span></span> <span data-ttu-id="4d651-171">Asegúrese de que la aplicación tenga como destino una versión de la Windows SDK mayor o igual que 10.0.17125 si tiene previsto usar esta característica.</span><span class="sxs-lookup"><span data-stu-id="4d651-171">Make sure your application is targeting a version of the Windows SDK greater than or equal to 10.0.17125 if you plan to use this feature</span></span>

<span data-ttu-id="4d651-172">Puede definir el comportamiento de activación de un secondaryTile de 3D para controlar cómo reacciona cuando un usuario lo selecciona.</span><span class="sxs-lookup"><span data-stu-id="4d651-172">You can define the activation behavior for a 3D secondaryTile to control how it reacts when a user selects it.</span></span> <span data-ttu-id="4d651-173">Se puede usar para colocar objetos 3D en la Página principal de la realidad mixta que son meramente informativas o decorativas.</span><span class="sxs-lookup"><span data-stu-id="4d651-173">This can be used to place 3D objects in the Mixed Reality home that are purely informative or decorative.</span></span> <span data-ttu-id="4d651-174">Se admiten los siguientes tipos de comportamiento de activación:</span><span class="sxs-lookup"><span data-stu-id="4d651-174">The following activation behavior types are supported:</span></span>
1. <span data-ttu-id="4d651-175">Valor predeterminado: cuando un usuario selecciona el secondaryTile 3D, se activa la aplicación</span><span class="sxs-lookup"><span data-stu-id="4d651-175">Default: When a user selects the 3D secondaryTile the app is activated</span></span>
2. <span data-ttu-id="4d651-176">Ninguno: cuando el usuario selecciona el secondaryTile 3D, no sucede nada y la aplicación no está activada.</span><span class="sxs-lookup"><span data-stu-id="4d651-176">None: When the user selects the 3D secondaryTile nothing happens and the app isn't activated.</span></span>

### <a name="obtaining-and-updating-an-existing-secondarytile"></a><span data-ttu-id="4d651-177">Obtener y actualizar un "secondaryTile" existente</span><span class="sxs-lookup"><span data-stu-id="4d651-177">Obtaining and updating an existing “secondaryTile”</span></span>

<span data-ttu-id="4d651-178">Los desarrolladores pueden volver a obtener una lista de los mosaicos secundarios existentes, que incluye las propiedades especificadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4d651-178">Developers can get back a list of their existing secondary tiles, which includes the properties that they previously specified.</span></span> <span data-ttu-id="4d651-179">También pueden actualizar las propiedades cambiando el valor y llamando a UpdateAsync ().</span><span class="sxs-lookup"><span data-stu-id="4d651-179">They can also update the properties by changing the value and then calling UpdateAsync().</span></span>

```cs
// Grab the existing secondary tile
SecondaryTile tile = (await SecondaryTile.FindAllAsync()).First();

Uri updatedUri = new Uri("ms-appdata:///local/MixedRealityUpdated.glb");

// See if the model needs updating
if (!tile.VisualElements.MixedRealityModel.Uri.Equals(updatedUri))
{
    // Update it
    tile.VisualElements.MixedRealityModel.Uri = updatedUri;

    // And apply the changes
    await tile.UpdateAsync();
}
```

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a><span data-ttu-id="4d651-180">Comprobar que el usuario está en Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d651-180">Checking that the user is in Windows Mixed Reality</span></span>

<span data-ttu-id="4d651-181">solo se pueden crear vínculos profundos 3D (secondaryTiles) mientras la vista se muestra en un casco de realidad mixta de Windows.</span><span class="sxs-lookup"><span data-stu-id="4d651-181">3D deep links (secondaryTiles) can only be created while the view is being displayed in a Windows Mixed Reality headset.</span></span> <span data-ttu-id="4d651-182">Cuando la vista no se presenta en un casco de realidad mixta de Windows, se recomienda controlarlo correctamente ocultando el punto de entrada o mostrando un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="4d651-182">When your view isn't being presented in a Windows Mixed Reality headset, we recommend gracefully handling this by either hiding the entry point or showing an error message.</span></span> <span data-ttu-id="4d651-183">Para comprobarlo, consulte [IsCurrentViewPresentedOnHolographic ()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span><span class="sxs-lookup"><span data-stu-id="4d651-183">You can check this by querying [IsCurrentViewPresentedOnHolographic()](https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_).</span></span>

## <a name="tile-notifications"></a><span data-ttu-id="4d651-184">Notificaciones de icono</span><span class="sxs-lookup"><span data-stu-id="4d651-184">Tile notifications</span></span>

<span data-ttu-id="4d651-185">Las notificaciones de icono no admiten actualmente el envío de una actualización con un recurso 3D.</span><span class="sxs-lookup"><span data-stu-id="4d651-185">Tile notifications don't currently support sending an update with a 3D asset.</span></span> <span data-ttu-id="4d651-186">Esto significa que los desarrolladores no pueden hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4d651-186">This means that developers can't do the following:</span></span>

* <span data-ttu-id="4d651-187">Notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="4d651-187">Push Notifications</span></span>
* <span data-ttu-id="4d651-188">Sondeo periódico</span><span class="sxs-lookup"><span data-stu-id="4d651-188">Periodic Polling</span></span>
* <span data-ttu-id="4d651-189">Notificaciones programadas</span><span class="sxs-lookup"><span data-stu-id="4d651-189">Scheduled Notifications</span></span>

<span data-ttu-id="4d651-190">Para obtener más información sobre las características y los atributos de los iconos y cómo se usan para los mosaicos 2D, consulte la [documentación de los iconos de las aplicaciones para UWP](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span><span class="sxs-lookup"><span data-stu-id="4d651-190">For more information on the other tiles features and attributes and how they're used for 2D tiles, see the [Tiles for UWP Apps documentation](https://docs.microsoft.com/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).</span></span>

## <a name="see-also"></a><span data-ttu-id="4d651-191">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4d651-191">See also</span></span>

* <span data-ttu-id="4d651-192">[Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.</span><span class="sxs-lookup"><span data-stu-id="4d651-192">[Mixed reality model sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) containing a 3D app launcher.</span></span>
* [<span data-ttu-id="4d651-193">Guía de diseño del iniciador de aplicaciones 3D</span><span class="sxs-lookup"><span data-stu-id="4d651-193">3D app launcher design guidance</span></span>](3d-app-launcher-design-guidance.md)
* [<span data-ttu-id="4d651-194">Crear modelos 3D para su uso en la Página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d651-194">Creating 3D models for use in the Windows Mixed Reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="4d651-195">Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)</span><span class="sxs-lookup"><span data-stu-id="4d651-195">Implementing 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
* [<span data-ttu-id="4d651-196">Desplazamiento por la página principal de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="4d651-196">Navigating the Windows Mixed Reality home</span></span>](../discover/navigating-the-windows-mixed-reality-home.md)
