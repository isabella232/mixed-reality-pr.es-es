---
title: GettingStartedWithMRTKAndXRSDK
description: Página de aterrizaje de MRTK con XRSDK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK, XRSDK,
ms.openlocfilehash: d5ab9bf51828c84759b72e87e1c41f885c7d6738
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300428"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introducción al SDK de MRTK y XR

El SDK de XR es la [nueva canalización XR de Unity en unity 2019,3 y versiones posteriores](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). En Unity 2019, proporciona una alternativa a la canalización XR existente. En Unity 2020, se convertirá en la única canalización de XR en Unity.

## <a name="prerequisites"></a>Requisitos previos

Para empezar a trabajar con el kit de herramientas de realidad mixta, siga [los pasos proporcionados](../install-the-tools.md#importing-the-mixed-reality-toolkit) para agregar MRTK a un proyecto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configuración de Unity para la canalización del SDK de XR

La canalización del SDK de XR actualmente admite 3 plataformas: Windows Mixed Reality, Oculus y OpenXR. En las secciones siguientes se explican los pasos necesarios para configurar el SDK de XR para cada plataforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Vaya al **Administrador de paquetes de Unity** e instale el paquete del complemento de Windows XR, que agrega compatibilidad con Windows Mixed Reality en el SDK de XR. De este modo, se extraerán también algunos paquetes de dependencia. 

1. Asegúrese de que los siguientes elementos se hayan instalado correctamente:
   * Administración de complementos de XR
   * Complemento de Windows XR
   * XR aplicaciones auxiliares de entrada heredadas

2. Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).
3. Haga clic en la pestaña Administración de complementos de XR en la ventana Configuración del proyecto.
4. Vaya a la configuración de Plataforma universal de Windows y asegúrese de que Windows Mixed Reality está activado en proveedores de complementos.
5. Asegúrese de que está activada la opción inicializar XR al iniciar.
6. (**_Necesario para la comunicación remota de HoloLens en el editor; de lo contrario, opcional_**) Vaya a configuración independiente y asegúrese de que Windows Mixed Reality está activado en proveedores de complementos. Asegúrese también de que la opción inicializar XR al iniciar está activada.

![Administración de complementos de XR con pestaña independiente seleccionada](images/xr-management-img-02.png)

7. (**_Opcional_**) Haga clic en la pestaña Windows Mixed Reality en administración de complementos de XR y cree un perfil de configuración personalizada para cambiar los valores predeterminados. Si la lista de valores de configuración ya existe, no es necesario crear ningún perfil.

![XR administración de complementos con la pestaña Windows seleccionada](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Siga las instrucciones para [configurar Oculus Quest in MRTK mediante la guía de canalización del SDK de XR](../features/cross-platform/oculus-quest-mrtk.md) al final. En la guía se describen los pasos necesarios para configurar Unity y MRTK para usar la canalización del SDK de XR para Oculus Quest.

### <a name="openxr-preview"></a>OpenXR (versión preliminar)

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020,2 y versiones posteriores.
>
> Actualmente, también es compatible con las compilaciones x64 y ARM64.

1. Siga las instrucciones que se indican en la guía [usar el complemento Mixed Reality OpenXR plugin para Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) , incluidos los pasos para configurar la administración y optimización del complemento de XR para instalar el complemento OpenXR en el proyecto. Asegúrese de que se han instalado correctamente los siguientes:
   1. Administración de complementos de XR
   1. Complemento de OpenXR
   1. Complemento OpenXR de realidad mixta
1. Vaya a editar > configuración del proyecto.
1. Haga clic en la pestaña Administración de complementos de XR en la ventana Configuración del proyecto.
1. Asegúrese de que está activada la opción inicializar XR al iniciar.
1. (**_Opcional_**) Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione conjunto de características de Microsoft HoloLens.

![Administración de complementos abrir XR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Si tiene un proyecto preexistente que usa MRTK de UPM, asegúrese de que la siguiente línea está en el archivo **link.xml** ubicado en la carpeta MixedRealityToolkit. generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Para la versión inicial de MRTK y OpenXR, solo se admiten de forma nativa las manos articuladas de HoloLens 2 y los controladores de movimiento de Windows Mixed Reality. En las próximas versiones se agregará compatibilidad con hardware adicional.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configuración de MRTK para la canalización del SDK de XR

Si usa OpenXR, elija "DefaultOpenXRConfigurationProfile" como perfil activo o clonarlo para crear personalizaciones.

Si usa otros tiempos de ejecución de XR en la configuración de administración de complementos de XR, como Windows Mixed Reality o Oculus, elija "DefaultXRSDKConfigurationProfile" como perfil activo o clonarlo para crear personalizaciones.

Estos perfiles se configuran con los sistemas y proveedores correctos, cuando sea necesario. Vea [los documentos de perfiles](../features/profiles/profiles.md#xr-sdk) para obtener más información sobre el perfil y la compatibilidad de ejemplo con el SDK de XR.

Para migrar un perfil existente a XR SDK, deben actualizarse los siguientes servicios y proveedores de datos:

### <a name="camera"></a>Cámara

De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configuración de cámara heredada](../features/images/xrsdk/CameraSystemLegacy.png)

en

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings)**y**[`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |

![Configuración de cámara del SDK de XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configuración de entrada heredada](../features/images/xrsdk/InputSystemWMRLegacy.png)

en

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR__:

![Configuración de entrada de OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configuración de entrada del SDK de XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Límite

De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configuración de límites heredados](../features/images/xrsdk/BoundarySystemLegacy.png)

en

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configuración de límites del SDK de XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Reconocimiento espacial

De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configuración de reconocimiento espacial heredada](../features/images/xrsdk/SpatialAwarenessLegacy.png)

en

| OpenXR | Windows Mixed Reality |
|--------|-----------------------|
| En curso | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |

![Configuración de reconocimiento espacial del SDK de XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Asignaciones de controlador

Si usa perfiles de asignación de controlador personalizados, abra uno de ellos y ejecute el elemento de menú de los perfiles de asignación del kit de herramientas de realidad mixta-> Utilities-> Update-> Controller para asegurarse de que se han definido los nuevos tipos de controlador del SDK de XR.

## <a name="see-also"></a>Consulte también

* [Introducción al desarrollo de AR en Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introducción al desarrollo de VR en Unity](https://docs.unity3d.com/Manual/VROverview.html)