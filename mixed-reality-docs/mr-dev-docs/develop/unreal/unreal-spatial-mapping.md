---
title: Mapeo espacial en Unreal
description: Aprenda a usar la asignación espacial y las mallas en aplicaciones de realidad mixta de Unreal para dispositivos HoloLens.
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial mapping, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 3f07acc5bb4ad85084f6eb178fd1c33d94224408
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009965"
---
# <a name="spatial-mapping-in-unreal"></a>Mapeo espacial en Unreal

La asignación espacial permite colocar objetos en superficies físicas del mundo real. Cuando se asigna el mundo de HoloLens, los hologramas parecen más reales al usuario. La asignación espacial también delimita objetos en el mundo del usuario mediante el uso de indicadores de profundidad, lo que ayuda a convencerles de que estos hologramas están realmente en su espacio. Los hologramas que flotan en el espacio o se mueven con el usuario no se sienten como si fuesen reales, por lo que siempre que sea posible puede colocar elementos para su comodidad.

Puede encontrar más información sobre la calidad del mapeo espacial, la ubicación, la oclusión, la representación, etc., en el documento [Asignación espacial](../../design/spatial-mapping.md).

## <a name="enabling-spatial-mapping"></a>Habilitación del mapeo espacial

Para habilitar el mapeo espacial en HoloLens:
- Abra **Editar > Configuración del proyecto** y desplácese hacia abajo hasta la sección **Plataformas**.    
    + Seleccione **HoloLens** y marque **Percepción espacial**.

![Captura de pantalla de las funcionalidades de configuración del proyecto de HoloLens con la percepción espacial resaltada](images/unreal-spatial-mapping-img-01.png)

Para participar en el mapeo espacial y depurar **MRMesh** en un juego HoloLens:
1. Abra **ARSessionConfig** y expanda la sección **ARSettings > World Mapping (Mapeo del mundo)** . 

2. Active **Generate Mesh Data from Tracked Geometry** (Generar datos de malla a partir de la geometría de seguimiento), que indica al complemento de HoloLens que empiece a obtener los datos de mapeo espacial de forma asincrónica y los exponga en Unreal a través de **MRMesh**. 
3. Marque **Render Mesh Data in Wireframe (Representar datos de malla en contorno reticular)** para mostrar un contorno reticular blanco de cada triángulo de **MRMesh**. 

![Almacén de anclajes espaciales listo](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a>Mapeo espacial en tiempo de ejecución
Puede modificar los parámetros siguientes para actualizar el comportamiento en tiempo de ejecución del mapeo espacial:

- Abra **Editar > Configuración del proyecto**, desplácese hacia abajo hasta la sección **Plataformas** y seleccione **HoloLens > Mapeo espacial**: 

![Configuración del proyecto de anclajes espaciales](images/unreal-spatialmapping-projectsettings.PNG)

- **Max Triangles Per Cubic Meter** (Máximo de triángulos por metro cúbico) actualice la densidad de los triángulos en la malla de mapeo espacial.  
- **Spatial Meshing Volume Size** (Tamaño del volumen de la malla espacial) es el tamaño del cubo alrededor del jugador para representar y actualizar los datos de mapeo espacial.  
    + Si se espera que el entorno en tiempo de ejecución de la aplicación sea elevado, es posible que este valor tenga que ser grande para que coincida con el espacio del mundo real. El valor puede ser menor si la aplicación solo necesita colocar hologramas en superficies inmediatamente alrededor del usuario. A medida que el usuario se desplaza por el mundo, el volumen de mapeo espacial se moverá con él. 

## <a name="working-with-mrmesh"></a>Utilización de MRMesh

En primer lugar, debe iniciar la asignación espacial:

![Plano técnico de la función ToggleARCapture con el tipo de captura de asignación espacial resaltado](images/unreal-spatial-mapping-img-02.png)

Una vez que se haya capturado la asignación espacial para el espacio, se recomienda desactivar la asignación espacial.  La asignación espacial se puede completar una vez transcurrido un período de tiempo determinado, o cuando los rayos enviados en cada dirección devuelvan colisiones con MRMesh.

Para obtener acceso a **MRMesh** en tiempo de ejecución:
1. Agregue un componente **ARTrackableNotify** a un actor de Blueprint. 

![Notificaciones supervisadas de AR de anclajes espaciales](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleccione el componente **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**. 
    - Seleccione el botón **+** en los eventos que quiera supervisar. 

![Eventos de Spatial Anchors](images/unreal-spatialmapping-events.PNG)

En este caso, se supervisa el evento **On Add Tracked Geometry** (Al agregar geometría de seguimiento), que busca mallas del mundo válidas que coincidan con los datos de mapeo espacial. Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

Puede cambiar el material de la malla en el gráfico de eventos de Blueprint o en C++. En la captura de pantalla siguiente se muestra la ruta de Blueprint: 

![Ejemplo de anclajes espaciales](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a>Asignación espacial en C++

En el archivo build.cs del juego, agregue **AugmentedReality** y **MRMesh** en la lista PublicDependencyModuleNames:

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

Para acceder a MRMesh, suscríbase a los delegados **OnTrackableAdded**:

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> Hay delegados similares para eventos actualizados y eliminados (**AddOnTrackableUpdatedDelegate_Handle** y **AddOnTrackableRemovedDelegate_Handle**, respectivamente).
>
> Puede encontrar la lista completa de eventos en la API [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html).

## <a name="see-also"></a>Consulta también
* [Asignación espacial](../../design/spatial-mapping.md)
