---
title: Seguimiento de las manos en Unreal
description: Obtenga información sobre cómo usar la entrada, la postura, las mallas de mano y las animaciones de vínculos activos en aplicaciones de realidad mixta.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, seguimiento de mano, inreal, inreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 415a0773586ab232e925fd0f18a3a8e6f8217e88
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695811"
---
# <a name="hand-tracking-in-unreal"></a>Seguimiento de las manos en Unreal

El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada. Están disponibles los datos sobre la posición y la rotación de cada dedo, la Palma completa y los gestos de mano. A partir de 4,26 inreal, el seguimiento de mano se basa en el complemento HeadMountedDisplay inreal y usa una API común en todas las plataformas y dispositivos de XR. La funcionalidad es la misma para los sistemas OpenXR y de realidad mixta de Windows.

## <a name="hand-pose"></a>Postura de mano

La postura de mano permite realizar el seguimiento y el uso de las manos y los dedos de los usuarios como entrada, a los que se puede tener acceso tanto en Blueprints como en C++. La API no real envía los datos como un sistema de coordenadas, con tics sincronizados con el motor inreal.

![Imagen de esqueleto de mano con ](images/hand-tracking-img-02.png)
 esqueleto de mano superpuesto ![](images/hand-tracking-skeleton-update.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a>Animación de vínculo activo a mano

Los planteamientos de mano se exponen a la animación mediante el [complemento de vínculo dinámico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Si los complementos de Windows Mixed Reality y Live Link están habilitados:
1. Seleccione **window > Live Link** para abrir la ventana del editor de vínculos activos.
2. Seleccionar **origen** y habilitar el origen de seguimiento de la **mano mixta de Windows**

![Origen de vínculo activo](images/unreal/live-link-source.png)

Después de habilitar el origen y abrir un recurso de animación, expanda la sección **animación** en la pestaña **vista previa** de la escena, también puede ver opciones adicionales.

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)

La jerarquía de animaciones a mano es la misma que en `EWMRHandKeypoint` . La animación se puede redestinar mediante **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)

También se puede crear una subclase en el editor:

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a>Malla de mano

### <a name="hand-mesh-as-a-tracked-geometry"></a>Malla de mano como geometría sometida a seguimiento

> [!IMPORTANT]
> La obtención de mallas manuales como geometría sometida a seguimiento en OpenXR requiere que se llame a **set usar malla de mano** con **geometría de seguimiento habilitada**.

Para habilitar ese modo, debe llamar a **set Use Hand Mesh** with **Enabled Tracking Geometry**:

![Plano del evento de inicio de reproducción de eventos conectado para establecer la función usar la malla de mano con el modo de geometría de seguimiento habilitado](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> No es posible habilitar ambos modos al mismo tiempo. Si habilita uno, el otro se deshabilitará automáticamente.

### <a name="accessing-hand-mesh-data"></a>Acceso a los datos de malla manual

![Malla de mano](images/unreal/hand-mesh.png)

Para poder acceder a los datos de malla a mano, deberá:
- Seleccione el recurso **ARSessionConfig** , expanda **configuración de ar-> configuración de asignación de mundo** y active la opción **generar datos de malla a partir de la geometría sometida a seguimiento**.

A continuación se muestran los parámetros de malla predeterminados:

1.  Usar datos de malla para la oclusión
2.  Generar colisión para datos de malla
3.  Generar malla de navegación para datos de malla
4.  Representar datos de malla en el parámetro de trama: Debug que muestra la malla generada

Estos valores de parámetro se usan como la malla de asignación espacial y los valores predeterminados de la malla de mano. Puede cambiarlos en cualquier momento en Blueprints o en el código de cualquier malla.

### <a name="c-api-reference"></a>Referencia de la API de C++
Use `EEARObjectClassification` para buscar valores de malla de mano en todos los objetos de los que se pueda realizar un seguimiento.
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

Se llama a los siguientes delegados cuando el sistema detecta cualquier objeto del que se pueden realizar acciones de seguimiento, incluida una malla de mano.

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

Asegúrese de que los controladores de delegado siguen la firma de la función siguiente:

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

Puede tener acceso a los datos de malla a través del  `UARTrackedGeometry::GetUnderlyingMesh` :

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a>Referencia de la API de Blueprint

Para trabajar con mallas manuales en Blueprints:
1. Agregar un componente **ARTrackableNotify** a un actor Blueprint

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)

2. Vaya al panel de **detalles** y expanda la sección **eventos** .

![ARTrackable notificar 2](images/unreal/ar-trackable-notify2.png)

3. Sobrescriba al agregar, actualizar o quitar la geometría sometida a seguimiento con los siguientes nodos en el gráfico de eventos:

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a>Visualización de la malla de mano en OpenXR

La forma recomendada de visualizar la malla de mano es usar el complemento XRVisualization de Epic junto con el [complemento de OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal). 

Después, en el editor de Blueprint, debe usar la función de **configuración usar la malla de mano** del [complemento de Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal) con **XRVisualization habilitado** como parámetro:

![Plano del evento Begin Play Connected para establecer la función usar la malla de mano con el modo xrvisualization habilitado](images/unreal-hand-tracking-img-05.png)

Para administrar el proceso de representación, debe usar el **controlador de movimiento de representación** de XRVisualization:

![Plano de la función de datos de Get Motion Controller conectada a la función de controlador de movimiento de representación](images/unreal-hand-tracking-img-06.png)

El resultado es:

![Imagen de la mano digital de una mano humana](images/unreal-hand-tracking-img-07.png) 

Si necesita algo más complicado, como dibujar una malla de mano con un sombreador personalizado, debe obtener las mallas como geometría sometida a seguimiento. 

## <a name="hand-rays"></a>Rayos de las manos

La obtención de la mano funciona para las interacciones de cierre, como la captura de objetos o la pulsación de botones. Sin embargo, a veces es necesario trabajar con hologramas alejados de los usuarios. Esto puede hacerse con los rayos de mano, que se pueden usar como dispositivos señaladores en C++ y Blueprints. Puede dibujar un rayo desde su mano hasta un punto lejano y, con algo de ayuda de un seguimiento de rayos no real, seleccione un holograma que, de otro modo, no estará disponible. 

> [!IMPORTANT]
> Dado que todos los resultados de la función cambian cada fotograma, todos ellos se pueden llamar. Para obtener más información sobre las funciones puras e inpuras o que se puede llamar, vea el GUID de usuario de Blueprint en [Functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a>Gestos

HoloLens 2 realiza el seguimiento de gestos espaciales, lo que significa que puede capturar esos gestos como entrada. El seguimiento de gestos se basa en un modelo de suscripción. Debe usar la función "configurar gestos" para indicar al dispositivo qué gestos desea seguir.  Puede encontrar más detalles sobre los movimientos en el documento de [uso básico de HoloLens 2](/hololens/hololens2-basic-usage) .

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Anclajes espaciales locales](unreal-spatial-anchors.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.