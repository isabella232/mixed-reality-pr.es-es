---
title: GettingStartedWithMRTKAndXRSDK
description: Página de aterrizaje de MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, XRSDK,
ms.openlocfilehash: fe50de31ae24b415738db64073822b2aff061636
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2021
ms.locfileid: "109850431"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introducción al SDK de MRTK y XR

El SDK de XR es la nueva canalización de XR de [Unity en Unity 2019.3 y posteriores.](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) En Unity 2019, proporciona una alternativa a la canalización XR existente. En Unity 2020, se convertirá en la única canalización XR en Unity.

## <a name="prerequisites"></a>Prerrequisitos

Para empezar a trabajar con Mixed Reality Toolkit, siga los pasos [proporcionados](../install-the-tools.md#importing-the-mixed-reality-toolkit) para agregar MRTK a un proyecto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configuración de Unity para la canalización del SDK de XR

La canalización del SDK de XR admite actualmente 3 plataformas: Windows Mixed Reality, Oculus y OpenXR. En las secciones siguientes se detendrán los pasos necesarios para configurar el SDK de XR para cada plataforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Vaya a **unity's Administrador de paquetes** e instale el paquete del complemento XR de Windows, que agrega compatibilidad con Windows Mixed Reality sdk de XR. Esto también extraerá algunos paquetes de dependencias. 

1. Asegúrese de que todo lo siguiente se ha instalado correctamente:
   * Administración de complementos XR
   * Complemento XR de Windows
   * Asistentes de entrada heredados de XR

2. Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).
3. Haga clic en la pestaña XR Plug-in Management (Administración de complementos XR) en la ventana Project Settings (Configuración del proyecto).
4. Vaya a la configuración Plataforma universal de Windows y asegúrese de Windows Mixed Reality esté activada en Proveedores de complementos.
5. Asegúrese de que initialize XR on Startup (Inicializar XR al iniciar) está activado.
6. (Obligatorio **_para la comunicación remota de HoloLens en el editor; de lo contrario, opcional)_** Vaya a la configuración independiente y asegúrese de que Windows Mixed Reality en Proveedores de complementos. Asegúrese también de que la opción Inicializar XR al iniciar está activada.

![Administración de complementos XR con la pestaña Independiente seleccionada](images/xr-management-img-02.png)

7. (**_Opcional)_** Haga clic en la Windows Mixed Reality en Administración de complementos XR y cree un perfil de configuración personalizado para cambiar los valores predeterminados. Si la lista de configuraciones ya está ahí, no es necesario crear ningún perfil.

![Administración de complementos XR con la pestaña Windows seleccionada](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Siga la [guía How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end (Cómo configurar Oculus Quest en MRTK mediante la canalización del SDK de XR hasta el final). En la guía se describen los pasos necesarios para configurar Unity y MRTK para usar la canalización del SDK de XR para Oculus Unity.

### <a name="openxr-preview"></a>OpenXR (versión preliminar)

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020.2 y versiones posteriores.
>
> Actualmente, solo admite compilaciones x64 y ARM64.

1. Siga la guía Using [the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del complemento OpenXR para Unity), incluidos los pasos para configurar la administración y optimización de complementos XR para instalar el complemento OpenXR en el proyecto. Asegúrese de que lo siguiente se ha instalado correctamente:
   1. Administración de complementos XR
   1. Complemento OpenXR
   1. Mixed Reality complemento OpenXR
1. Vaya a Editar > configuración del proyecto.
1. Haga clic en la pestaña Administración de complementos XR en la ventana Configuración del proyecto.
1. Asegúrese de que la opción Inicializar XR al iniciar está activada.
1. (**_Opcional)_** Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y seleccione Microsoft HoloLens conjunto de características.

![Administración de complementos Open XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Si tiene un proyecto preexistente que usa MRTK de UPM, asegúrese de que la línea siguiente se encuentra en el archivo **link.xml** ubicado en la carpeta MixedRealityToolkit.Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Para la versión inicial de MRTK y OpenXR, solo se admiten de forma nativa las HoloLens 2 y Windows Mixed Reality de movimiento. En las próximas versiones se agregará compatibilidad con hardware adicional.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configuración de MRTK para la canalización del SDK de XR

Si usa OpenXR, elija "DefaultOpenXRConfigurationProfile" como perfil activo o clone para realizar personalizaciones.

Si usa otros entornos de ejecución de XR en la configuración de administración de complementos de XR, como Windows Mixed Reality u Oculus, elija "DefaultXRSDKConfigurationProfile" como perfil activo o clone para realizar personalizaciones.

Estos perfiles se establecen con los sistemas y proveedores correctos, cuando sea necesario. Consulte [los documentos de perfiles para](../features/profiles/profiles.md#xr-sdk) obtener más información sobre el perfil y la compatibilidad de ejemplo con el SDK de XR.

Para migrar un perfil existente al SDK de XR, se deben actualizar los siguientes servicios y proveedores de datos:

### <a name="camera"></a>Cámara

De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configuración de la cámara heredada](../features/images/xrsdk/CameraSystemLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**y**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Configuración de la cámara del SDK de XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configuración de entrada heredada](../features/images/xrsdk/InputSystemWMRLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Configuración de entrada de OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configuración de entrada del SDK de XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Límite

De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configuración de límites heredada](../features/images/xrsdk/BoundarySystemLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configuración de límites del SDK de XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Reconocimiento espacial

De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configuración de reconocimiento espacial heredado](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| En curso | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configuración de reconocimiento espacial del SDK de XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Asignaciones de controladores

Si usa perfiles de asignación de controladores personalizados, abra uno de ellos y ejecute el elemento de menú Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles para asegurarse de que se definen los nuevos tipos de controlador del SDK de XR.

## <a name="see-also"></a>Consulte también

* [Introducción al desarrollo de AR en Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introducción al desarrollo de realidad virtual en Unity](https://docs.unity3d.com/Manual/VROverview.html)