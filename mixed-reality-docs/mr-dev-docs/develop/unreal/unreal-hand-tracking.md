---
title: Seguimiento de las manos en Unreal
description: Explica cómo usar el seguimiento de manos en inreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, seguimiento de mano, inreal, no real Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691237"
---
# <a name="hand-tracking-in-unreal"></a>Seguimiento de las manos en Unreal

## <a name="overview"></a>Información general

El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada. Puede obtener la posición y la rotación de cada dedo, toda la palma e incluso los gestos de mano que se usarán en el código. 

## <a name="hand-pose"></a>Postura de mano

La postura de mano le permite realizar un seguimiento de las manos y los dedos del usuario activo y usarlo como entrada, a la que puede acceder a través de Blueprints y C++. Puede encontrar más detalles técnicos en la API de [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) de la que no es real. La API no real envía los datos como un sistema de coordenadas, con tics sincronizados con el motor inreal.

### <a name="understanding-the-bone-hierarchy"></a>Descripción de la jerarquía del hueso

La `EWMRHandKeypoint` enumeración describe la jerarquía del hueso de la mano. Puede encontrar cada keypoint de mano enumerado en los planos:

![Mano keypoint BP](images/hand-keypoint-bp.png)

La enumeración completa de C++ se muestra a continuación:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

Puede encontrar los valores numéricos de cada caso de enumeración en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) . En la imagen siguiente se muestra el diseño de pose de mano completo con casos de enumeración coincidentes:

![Esqueleto manual](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>Compatibilidad con el seguimiento de la mano

Puede usar el seguimiento de manos en Blueprints agregando **compatibilidad con** el seguimiento de la mano **> Windows Mixed Reality** :

![Seguimiento de mano BP](images/unreal/hand-tracking-bp.png)

Esta función devuelve `true` si se admite el seguimiento manual en el dispositivo y `false` si el seguimiento de manos no está disponible.

![Admite el seguimiento de manos BP](images/unreal/supports-hand-tracking-bp.png)

C++: 

Incluya `WindowsMixedRealityHandTrackingFunctionLibrary.h`.

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>Obtención del seguimiento manual
Puede usar **GetHandJointTransform** para devolver datos espaciales desde la mano. Los datos se actualizan cada fotograma, pero si se encuentra dentro de un marco, los valores devueltos se almacenan en caché. No se recomienda tener una lógica pesada en esta función por motivos de rendimiento. 

![Obtener transformación Unión a mano](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Desglose de parámetros de función:

* **Mano** : es la mano izquierda o derecha del usuario
* **Keypoint** : el hueso de la mano. 
* **Transformación** : coordenadas y orientación de la base del hueso. Puede solicitar la base del siguiente hueso para obtener los datos de transformación para el final de un hueso. Un hueso de la sugerencia especial proporciona el final de distal. 
* **Radio** : radio de la base del hueso.
* **Valor devuelto** : true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.

## <a name="hand-live-link-animation"></a>Animación de vínculo activo a mano
Los planteamientos de mano se exponen a la animación mediante el [complemento de vínculo dinámico](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).

Si los complementos de Windows Mixed Reality y Live Link están habilitados: 
1. Seleccione **window > Live Link** para abrir la ventana del editor de vínculos activos. 
2. Haga clic en **origen** y habilite el origen de seguimiento de la **mano mixta de Windows**

![Origen de vínculo activo](images/unreal/live-link-source.png)
 
Después de habilitar el origen y abrir un recurso de animación, expanda la sección **animación** en la pestaña **vista previa** de la escena, también puede ver opciones adicionales (los detalles se encuentran en la documentación de Live Link real), ya que el complemento está en versión beta, el proceso puede cambiar más adelante.

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)
 
La jerarquía de animaciones a mano es la misma que en `EWMRHandKeypoint` . La animación se puede redestinar mediante **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)
 
También se puede crear una subclase en el editor:

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>Acceso a los datos de malla manual

![Malla de mano](images/unreal/hand-mesh.png)

Para poder acceder a los datos de malla a mano, deberá:
- Seleccione el recurso **ARSessionConfig** , expanda **configuración de ar-> configuración de asignación de mundo** y active la opción **generar datos de malla a partir de la geometría sometida a seguimiento** . 

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
 
## <a name="hand-rays"></a>Rayos de mano

Puede usar un rayo de mano como dispositivo señalador en C++ y blueprints, que expone la API [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) .

Es importante mencionar que, dado que los resultados de todas las funciones cambian cada fotograma, todos ellos se pueden llamar. Para obtener más información sobre las funciones puras e inpuras o que se puede llamar, consulte el GUID de usuario de Blueprint en [Functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure) .

Para usar rayos de mano en blueprints, busque cualquiera de las acciones en **Windows Mixed Reality HMD** :

![Rayos de mano BP](images/unreal/hand-rays-bp.png)
 
Para tener acceso a ellos en C++, incluya `WindowsMixedRealityFunctionLibrary.h` en la parte superior del archivo de código que realiza la llamada.

### <a name="enum"></a>Enumeración
También tiene acceso a los casos de entrada en **EHMDInputControllerButtons** , que se pueden usar en Blueprints:

![Botones del controlador de entrada](images/unreal/input-controller-buttons.png)

Para el acceso en C++, utilice la `EHMDInputControllerButtons` clase enum:
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:
* **Select** : evento de selección desencadenada por el usuario. 
    * El evento se puede desencadenar en HoloLens 2 con la pulsación aérea, la función de pulsar y confirmar, o bien decir "seleccionar" con [entrada de voz](unreal-voice-input.md) habilitada. 
* **Agarre** : evento de agarre desencadenado por el usuario. 
    * Este evento se puede desencadenar en HoloLens 2 cerrando los dedos del usuario en un holograma. 

Puede tener acceso al estado de seguimiento de la malla de mano en C++ a través de la `EHMDTrackingStatus` enumeración que se muestra a continuación:

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

A continuación se muestra un desglose de los dos casos de enumeración aplicables:
* **NotTracked** : la mano no es visible
* **Seguimiento** : se realiza un seguimiento completo de la mano

### <a name="struct"></a>Estructura
El struct PointerPoseInfo puede proporcionarle información sobre los siguientes datos de la mano:
* **Origin** : origen de la mano
* **Dirección** : dirección de la mano
* **Vertical** : Vector de la mano
* **Orientación** : cuaternión de orientación 
* **Estado de seguimiento** : estado de seguimiento actual

Puede tener acceso a esto a través de blueprints, como se muestra a continuación:

![El puntero representa la información BP](images/unreal/pointer-pose-info-bp.png)

O con C++:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>Functions

Todas las funciones que se enumeran a continuación se pueden llamar en cada fotograma, lo que permite la supervisión continua. 

1. **Obtener** información de la pose de puntero devuelve información completa sobre la dirección del rayo en el marco actual. 

Blueprint

![Obtener información de la repostura de puntero](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Se ha captado** devuelve true si la mano se ha captado en el fotograma actual.

Blueprint

![Se ha captado BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. Si **se selecciona, se** devuelve true si el usuario desencadenó SELECT en el marco actual.

Blueprint

![Seleccione BP presionado](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. Si se **hace clic** en el botón, devuelve true si el evento o el botón se desencadena en el marco actual.

Blueprint

![Clic en el botón BP](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **Obtener estado de seguimiento del controlador** devuelve el estado de seguimiento en el marco actual.

Blueprint

![Obtiene el estado de seguimiento del controlador BP](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>Gestos

Hololens 2 puede realizar el seguimiento de gestos espaciales, lo que significa que puede capturar esos gestos como entrada. Puede encontrar más detalles sobre los movimientos en el documento de [uso básico de HoloLens 2](https://docs.microsoft.com/hololens/hololens2-basic-usage) .

Puede encontrar la función Blueprint en en **entrada espacial de Windows Mixed Reality** y la función de C++ agregando `WindowsMixedRealitySpatialInputFunctionLibrary.h` en el archivo de código que realiza la llamada.

![Capturar movimientos](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumeración
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Blueprint 

![Tipo de gesto](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Función
Puede habilitar y deshabilitar la captura de gestos con la `CaptureGestures` función. Cuando un gesto habilitado activa eventos de entrada, la función devuelve `true` si la captura de gestos se realizó correctamente y se `false` produce un error.

Blueprint

![Movimientos de captura BP](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

Los siguientes son eventos clave, que puede encontrar en Blueprints y C++: ![ eventos de clave.](images/unreal/key-events.png)

![Eventos clave 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de punto de control de desarrollo no real que hemos diseñado, está en medio de explorar los bloques de creación de MRTK Core. Desde aquí, puede continuar con el siguiente bloque de creación: 

> [!div class="nextstepaction"]
> [Anclajes espaciales locales](unreal-spatial-anchors.md)

O salte a las funcionalidades y API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Siempre puede volver a los puntos de [control de desarrollo no reales](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.