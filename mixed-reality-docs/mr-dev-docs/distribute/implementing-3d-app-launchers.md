---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)
description: Obtén información sobre cómo crear logotipos y iniciadores de aplicaciones 3D Windows Mixed Reality aplicaciones y juegos para UWP en HoloLens cascos de realidad virtual.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, iniciador 3D, icono, cubo dinámico, vínculo profundo, secundario, icono secundario, UWP, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, XML, rectángulo de selección, unity
ms.openlocfilehash: b0ccff2aaba9c4693f58b134cdb3af9190b59befec0b31851273ed6a3bc1fc04
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196430"
---
# <a name="implement-3d-app-launchers-uwp-apps"></a>Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)

> [!NOTE]
> Esta característica se agregó como parte de Fall Creators Update (RS3) de 2017 para cascos envolventes y es compatible con HoloLens con la actualización de Windows 10 de abril de 2018. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor o igual que 10.0.16299 en cascos envolventes y 10.0.17125 en HoloLens. Puede encontrar la versión más reciente Windows SDK [aquí.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

La [Windows Mixed Reality principal es](../discover/navigating-the-windows-mixed-reality-home.md) el punto de partida donde los usuarios aterrizó antes de iniciar aplicaciones. Al crear una aplicación para UWP para Windows Mixed Reality, de forma predeterminada, las aplicaciones se inician como pizarras 2D con el logotipo de la aplicación. Al desarrollar experiencias para Windows Mixed Reality, opcionalmente se puede definir un iniciador 3D para invalidar el iniciador 2D predeterminado para la aplicación. En general, se recomiendan los iniciadores 3D para iniciar aplicaciones inmersivas que saquen a los usuarios del Windows Mixed Reality inicio. Se prefiere el iniciador 2D predeterminado cuando la aplicación se activa en su lugar. También puedes crear un vínculo [profundo 3D (secondaryTile)](#3d-deep-links-secondarytiles) como iniciador 3D al contenido dentro de una aplicación para UWP en 2D.

>[!VIDEO https://www.youtube.com/embed/TxIslHsEXno]

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:
1. [Diseño y conceptos](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación (este artículo)

Los recursos 3D que se usarán como iniciadores de la aplicación deben crearse mediante las Windows Mixed Reality de creación [para](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) garantizar la compatibilidad. Los recursos que no cumplan esta especificación de creación no se representarán en el Windows Mixed Reality inicio.

## <a name="configuring-the-3d-launcher"></a>Configuración del iniciador 3D

Cuando creas un nuevo proyecto en Visual Studio, se crea un icono predeterminado sencillo que muestra el nombre y el logotipo de la aplicación. Para reemplazar esta representación 2D por un modelo 3D personalizado, edite el manifiesto de aplicación de la aplicación para incluir el elemento "MixedRealityModel" como parte de la definición de icono predeterminada. Para revertir al iniciador 2D, quite la definición de MixedRealityModel del manifiesto.

### <a name="xml"></a>XML

En primer lugar, busque el manifiesto del paquete de aplicación en el proyecto actual. De forma predeterminada, el manifiesto se denominará Package.appxmanifest. Si usa el código Visual Studio, haga clic con el botón derecho  en el manifiesto en el visor de soluciones y seleccione Ver origen para abrir el xml para su edición. 

En la parte superior del manifiesto, agregue el esquema uap5 e insóquelo como un espacio de nombres que se puede omitir:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         IgnorableNamespaces="uap uap2 uap5 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```

A continuación, especifique "MixedRealityModel" en el icono predeterminado de la aplicación:

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

El elemento MixedRealityModel acepta una ruta de acceso de archivo que apunta a un recurso 3D almacenado en el paquete de la aplicación. Actualmente solo se admiten los modelos 3D entregados con el formato de archivo .glb y que se han Windows Mixed Reality instrucciones de creación de recursos [3D.](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) Los recursos deben almacenarse en el paquete de la aplicación y la animación no se admite actualmente. Si el parámetro "Path" se deja en blanco Windows la pizarra 2D en lugar del iniciador 3D. **Nota:** El recurso .glb debe marcarse como "Contenido" en la configuración de compilación antes de compilar y ejecutar la aplicación.


![Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarlo como "Contenido" en la configuración de compilación.](images/buildsetting-content-300px.png)<br>
*Seleccione el .glb en el Explorador de soluciones y use la sección de propiedades para marcarlo como "Contenido" en la configuración de compilación.*

### <a name="bounding-box"></a>Rectángulo de selección

Se puede usar un cuadro de límite para agregar opcionalmente una región de búfer adicional alrededor del objeto . El rectángulo delimitador se especifica mediante un punto central y extensiones, que indican la distancia desde el centro del rectángulo delimitador hasta sus bordes a lo largo de cada eje. Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 medidor. Si no se proporciona un rectángulo de selección, se ajustará automáticamente a la malla del objeto. Si el rectángulo de selección proporcionado es menor que el modelo, se cambiará el tamaño para que se ajuste a la malla.

La compatibilidad con el atributo de cuadro de límite viene con la actualización Windows RS4 como una propiedad en el elemento MixedRealityModel. Para definir un rectángulo de selección en primer lugar en la parte superior del manifiesto de aplicación, agregue el esquema uap6 e inscluyéndolo como espacios de nombres que se pueden omitir:

```xml
<Package xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest" 
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" 
         xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2" 
         xmlns:uap5="http://schemas.microsoft.com/appx/manifest/uap/windows10/5"
         xmlns:uap6="http://schemas.microsoft.com/appx/manifest/uap/windows10/6"
         IgnorableNamespaces="uap uap2 uap5 uap6 mp"
         xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10">
```
A continuación, en MixedRealityModel, establezca la propiedad SpatialBoundingBox para definir el cuadro de límite: 

```xml
        <uap:DefaultTile Wide310x150Logo="Assets\WideLogo.png" >
          <uap5:MixedRealityModel Path="Assets\My3DTile.glb">
              <uap6:SpatialBoundingBox  Center=”1,-2,3” Extents=”1,2,3” />
          </uap5:MixedRealityModel>
        </uap:DefaultTile>
```

### <a name="using-unity"></a>Con Unity

Cuando se trabaja con Unity, el proyecto debe crearse y abrirse en Visual Studio para poder editar el manifiesto de aplicación. 

>[!NOTE]
>El iniciador 3D debe volver a definirse en el manifiesto al compilar e implementar una nueva solución Visual Studio desde Unity.

## <a name="3d-deep-links-secondarytiles"></a>Vínculos profundos 3D (secondaryTiles)

> [!NOTE]
> Esta característica se agregó como parte de Fall Creators Update (RS3) de 2017 para cascos envolventes (VR) y como parte de la actualización de abril de 2018 (RS4) para HoloLens. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor o igual que 10.0.16299 en cascos envolventes (VR) y 10.0.17125 en HoloLens. Puede encontrar la versión más reciente Windows SDK [aquí.](https://developer.microsoft.com/windows/downloads/windows-10-sdk)

>[!IMPORTANT]
>Los vínculos profundos 3D (secondaryTiles) solo funcionan con aplicaciones 2D para UWP. Sin embargo, puede crear un iniciador de aplicaciones [3D](implementing-3d-app-launchers.md) para iniciar una aplicación exclusiva desde Windows Mixed Reality inicio.

Las aplicaciones 2D se pueden mejorar para Windows Mixed Reality agregando la capacidad de colocar modelos 3D desde la aplicación en la página principal de Windows Mixed Reality como vínculos profundos [al](../discover/navigating-the-windows-mixed-reality-home.md) contenido dentro de la aplicación [2D,](/windows/uwp/controls-and-patterns/tiles-and-notifications-secondary-tiles) al igual que los iconos secundarios 2D en el Windows menú Inicio. Por ejemplo, puede crear photospheres de 360° que se vinculen directamente a una aplicación de visor de fotos de 360° o permitir que los usuarios coloquen contenido 3D desde una colección de recursos que abre una página de detalles sobre el autor. Estas son solo un par de maneras de expandir la funcionalidad de la aplicación 2D con contenido 3D.

### <a name="creating-a-3d-secondarytile"></a>Creación de un "secondaryTile" 3D

Puede colocar contenido 3D desde la aplicación mediante "secondaryTiles" mediante la definición de un modelo de realidad mixta en el momento de la creación. Los modelos de realidad mixta se crean haciendo referencia a un recurso 3D en el paquete de la aplicación y definiendo opcionalmente un cuadro de límite. 

> [!NOTE]
> Actualmente no se admite la creación de "secondaryTiles" desde una vista exclusiva.

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

### <a name="bounding-box"></a>Rectángulo de selección

Se puede usar un cuadro de límite para agregar una región de búfer adicional alrededor del objeto . El rectángulo delimitador se especifica mediante un punto central y extensiones, que indican la distancia desde el centro del rectángulo delimitador hasta sus bordes a lo largo de cada eje. Las unidades del cuadro de límite se pueden asignar a 1 unidad = 1 medidor. Si no se proporciona un rectángulo de selección, se ajustará automáticamente a la malla del objeto. Si el rectángulo de selección proporcionado es menor que el modelo, se cambiará el tamaño para que se ajuste a la malla.

### <a name="activation-behavior"></a>Comportamiento de activación

> [!NOTE]
> Esta característica se admite desde la actualización Windows RS4. Asegúrese de que la aplicación tiene como destino una versión del SDK de Windows mayor o igual que 10.0.17125 si tiene previsto usar esta característica.

Puede definir el comportamiento de activación de un secondaryTile 3D para controlar cómo reacciona cuando un usuario lo selecciona. Esto se puede usar para colocar objetos 3D en el Mixed Reality que son puramente informativos o decorados. Se admiten los siguientes tipos de comportamiento de activación:
1. Valor predeterminado: cuando un usuario selecciona la secundaria 3DTile se activa la aplicación
2. Ninguno: cuando el usuario selecciona la secundaria 3D, no ocurre nada y la aplicación no está activada.

### <a name="obtaining-and-updating-an-existing-secondarytile"></a>Obtención y actualización de un elemento "secondaryTile" existente

Los desarrolladores pueden obtener una lista de sus iconos secundarios existentes, que incluye las propiedades que especificaron anteriormente. También pueden actualizar las propiedades cambiando el valor y llamando a UpdateAsync().

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

### <a name="checking-that-the-user-is-in-windows-mixed-reality"></a>Comprobación de que el usuario está en Windows Mixed Reality

Los vínculos profundos 3D (secondaryTiles) solo se pueden crear mientras la vista se muestra en un Windows Mixed Reality casco. Cuando la vista no se presenta en un casco de Windows Mixed Reality, se recomienda controlarlo correctamente ocultando el punto de entrada o mostrando un mensaje de error. Para comprobarlo, consulte [IsCurrentViewPresentedOnHolographic().](/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview#Windows_ApplicationModel_Preview_Holographic_HolographicApplicationPreview_IsCurrentViewPresentedOnHolographicDisplay_)

## <a name="tile-notifications"></a>Notificaciones de icono

Actualmente, las notificaciones de icono no admiten el envío de una actualización con un recurso 3D. Esto significa que los desarrolladores no pueden hacer lo siguiente:

* Notificaciones de inserción
* Sondeo periódico
* Notificaciones programadas

Para obtener más información sobre las otras características y atributos de iconos y cómo se usan para los iconos 2D, consulta la documentación Iconos para [aplicaciones para UWP](/windows/uwp/controls-and-patterns/tiles-and-notifications-creating-tiles).

## <a name="see-also"></a>Consulte también

* [Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.
* [Guía de diseño del iniciador de aplicaciones 3D](3d-app-launcher-design-guidance.md)
* [Creación de modelos 3D para su uso en el Windows Mixed Reality principal](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)](implementing-3d-app-launchers-win32.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)