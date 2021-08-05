---
title: Seguimiento de las manos en Unreal
description: Aprenda a usar la entrada de seguimiento de manos, la posición, las mallas de mano y las animaciones de vínculos en directo en aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, seguimiento de manos, Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 4c3b86c842fc875ebedbdf2527bf962fd8afd4d19cef90d168293cc85b664f70
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187425"
---
# <a name="hand-tracking-in-unreal"></a>Seguimiento de las manos en Unreal

El sistema de seguimiento de manos usa los dedos y los dedos de una persona como entrada. Hay disponibles datos sobre la posición y rotación de cada dedo, la mano entera y los gestos de mano. A partir de Unreal 4.26, el seguimiento manual se basa en el complemento Unreal HeadMountedDisplay y usa una API común en todas las plataformas y dispositivos XR. La funcionalidad es la misma para los sistemas Windows Mixed Reality y OpenXR.

## <a name="hand-pose"></a>Posición de la mano

La posición con la mano le permite realizar un seguimiento y usar las manos y los dedos de los usuarios como entrada, a los que se puede acceder tanto en Blueprints como en C++. La API de Unreal envía los datos como un sistema de coordenadas, con tics sincronizados con Unreal Engine.

![Imagen de esqueleto de mano con juntas superpuestas ](images/hand-tracking-img-02.png)
 ![ a Hand Skeleton](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animación de vínculos en directo con la mano

Las poses de mano se exponen a Animation mediante el [complemento Live Link](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Si los Windows Mixed Reality y los complementos de Live Link están habilitados:
1. Seleccione **Ventana > Live Link para** abrir la ventana del editor de Live Link.
2. Seleccione **Origen y** habilite Windows Mixed Reality origen de seguimiento de **mano**

![Origen de Live Link](images/unreal/live-link-source.png)

Después de habilitar el origen y abrir un recurso de animación, expanda la sección **Animación** de la pestaña **Escena** de vista previa. También verá opciones adicionales.

![Animación de vínculos en directo](images/unreal/live-link-animation.png)

La jerarquía de animación manual es la misma que en `EWMRHandKeypoint` . La animación se puede redestinar **mediante WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Live Link Animation 2](images/unreal/live-link-animation2.png)

También se pueden crear subclases en el editor:

![Reasignación de Vínculos en vivo](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Malla de mano

### <a name="hand-mesh-as-a-tracked-geometry"></a>Malla de mano como geometría con seguimiento

> [!IMPORTANT]
> Para obtener mallas de mano como geometría de seguimiento en OpenXR, es necesario llamar a **Set Use Hand Mesh** with Enabled Tracking Geometry (Establecer usar malla de mano con geometría de seguimiento **habilitada).**

Para habilitar ese modo, debe llamar a Set Use Hand Mesh with Enabled Tracking Geometry **(Establecer** usar malla de mano con **geometría de seguimiento habilitada):**

![Plano técnico de la reproducción de inicio de eventos conectada para establecer el uso de la función de malla de mano con el modo de geometría de seguimiento habilitado](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> No es posible habilitar ambos modos al mismo tiempo. Si habilita una, la otra se deshabilita automáticamente.

### <a name="accessing-hand-mesh-data"></a>Acceso a datos de malla de mano

![Malla de mano](images/unreal/hand-mesh.png)

Para poder acceder a los datos de malla de mano, deberá hacer lo siguiente:
- Seleccione el **recurso ARSessionConfig,** expanda la configuración de AR **Configuración -> World Mapping** y active Generar datos de malla a partir de geometría con **seguimiento.**

A continuación se muestran los parámetros de malla predeterminados:

1.  Uso de datos de malla para la oclusión
2.  Generar colisión para datos de malla
3.  Generación de malla de navegación para datos de malla
4.  Representar datos de malla en Wireframe: parámetro de depuración que muestra la malla generada

Estos valores de parámetro se usan como valores predeterminados de malla de asignación espacial y malla de mano. Puede cambiarlos en cualquier momento en Planos técnico o código para cualquier malla.

### <a name="c-api-reference"></a>Referencia de api de C++
Use `EEARObjectClassification` para buscar valores de malla de mano en todos los objetos de los que se puede realizar un seguimiento.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

Se llama a los delegados siguientes cuando el sistema detecta cualquier objeto de seguimiento, incluida una malla de mano.

```cpp
class FARSupportInterface
{
    public:
    // Other params
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Asegúrese de que los controladores delegados siguen la firma de función siguiente:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Puede acceder a los datos de malla a través de  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Referencia de la API de plano técnico

Para trabajar con mallas de mano en planos técnico:
1. Agregar un **componente ARTrackableNotify** a un actor de plano técnico

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)

2. Vaya al panel **Detalles** y expanda la **sección** Eventos.

![NOTIFICACIÓN DE ARTrackable 2](images/unreal/ar-trackable-notify2.png)

3. Sobrescriba al agregar, actualizar o quitar geometría con seguimiento con los siguientes nodos en el cuadro de Graph:

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualización de Hand Mesh en OpenXR

La manera recomendada de visualizar la malla manual es usar el complemento XRVisualization de Epic junto con el complemento [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

A continuación, en el editor de planos técnico, debe usar la función Set **Use Hand Mesh** del complemento Microsoft [OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **Enabled XRVisualization** como parámetro:

![Plano técnico de la reproducción de inicio de eventos conectada para establecer el uso de la función de malla de mano con el modo xrvisualización habilitado](images/unreal-hand-tracking-img-05.png)

Para administrar el proceso de representación, debe usar **El controlador de movimiento de representación** de XRVisualización:

![Plano técnico de la función de datos get motion controller conectada para representar la función del controlador de movimiento](images/unreal-hand-tracking-img-06.png)

El resultado es:

![Imagen de la mano digital superpuesta en una mano humana real](images/unreal-hand-tracking-img-07.png) 

Si necesita algo más complicado, como dibujar una malla de mano con un sombreador personalizado, debe obtener las mallas como geometría con seguimiento. 

## <a name="hand-rays"></a>Rayos de las manos

La obtención de la posición de la mano funciona para interacciones cercanas, como agarrar objetos o presionar botones. Sin embargo, a veces es necesario trabajar con hologramas que están lejos de los usuarios. Esto se puede lograr con rayos de mano, que se pueden usar como dispositivos de punto en C++ y planos planos. Puede dibujar un rayo de la mano a un punto lejano y, con ayuda del seguimiento de un rayo de Unreal, seleccionar un holograma que, de lo contrario, estaría fuera de alcance. 

> [!IMPORTANT]
> Puesto que todos los resultados de la función cambian cada fotograma, todos se pueden llamar. Para obtener más información sobre las funciones puras e impuras o a las que se puede llamar, consulte el GUID de usuario de Blueprint en [las funciones](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gestos

El HoloLens 2 realiza un seguimiento de los gestos espaciales, lo que significa que puede capturar esos gestos como entrada. El seguimiento de gestos se basa en un modelo de suscripción. Debe usar la función "Configurar gestos" para decir al dispositivo los gestos de los que desea realizar el seguimiento.  Puede encontrar más detalles sobre los gestos en el [HoloLens 2 Basic Usage (Uso](/hololens/hololens2-basic-usage) básico).

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Anclajes espaciales locales](unreal-spatial-anchors.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.