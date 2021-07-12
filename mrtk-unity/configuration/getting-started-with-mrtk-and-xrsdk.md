---
title: Introducción a MRTK y al SDK de XR
description: Página de aterrizaje de MRTK con el SDK de XR
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, XRSDK, SDK de XR
ms.openlocfilehash: bc2924f8e080b0c202f7c3e394a5382cf306431c
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603696"
---
# <a name="getting-started-with-mrtk-and-xr-sdk"></a>Introducción a MRTK y al SDK de XR

El SDK de XR es la nueva canalización [de XR de Unity en Unity 2019.3 y más allá de](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/). En Unity 2019, proporciona una alternativa a la canalización de XR existente. En Unity 2020, es la única canalización XR en Unity.

## <a name="prerequisites"></a>Requisitos previos

Para empezar a trabajar con Mixed Reality Toolkit, siga [los](../install-the-tools.md#importing-the-mixed-reality-toolkit) pasos proporcionados para agregar MRTK a un proyecto.

## <a name="configuring-unity-for-the-xr-sdk-pipeline"></a>Configuración de Unity para la canalización del SDK de XR

La canalización del SDK de XR admite actualmente tres plataformas: Windows Mixed Reality, Oculus y OpenXR. En las secciones siguientes se detendrán los pasos necesarios para configurar el SDK de XR para cada plataforma.

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

Vaya a **la aplicación de Unity Administrador de paquetes** instale el paquete Windows complemento XR, que agrega compatibilidad con Windows Mixed Reality sdk de XR. Esto también extraerá algunos paquetes de dependencia.

1. Asegúrese de que todo lo siguiente se ha instalado correctamente:
   * Administración de complementos XR
   * Windows Complemento XR
   * Asistentes de entrada heredados de XR

2. Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).
3. Haga clic en la pestaña XR Plug-in Management (Administración de complementos XR) en Project Configuración ventana.
4. Vaya a la configuración de la plataforma Windows universal y asegúrese de Windows Mixed Reality esté activada en Proveedores de complementos.
5. Asegúrese de que la opción Inicializar XR al iniciar está activada.
6. ( Obligatorio para la comunicación remota en HoloLens editor; de **_lo contrario, opcional)_** Vaya a la configuración independiente y asegúrese de que Windows Mixed Reality en Proveedores de complementos. Asegúrese también de que la opción Inicializar XR al iniciar está activada.

    ![Administración de complementos XR con la pestaña Independiente seleccionada](images/xr-management-img-02.png)

7. (**_Opcional)_** Haga clic en Windows Mixed Reality en Administración de complementos XR y cree un perfil de configuración personalizado para cambiar los valores predeterminados. Si la lista de configuraciones ya está ahí, no es necesario crear ningún perfil.

    ![Administración de complementos XR con Windows pestaña seleccionada](images/xr-management-img-01.png)

### <a name="oculus"></a>Oculus

1. Siga la [guía How to configure Oculus Quest in MRTK using the XR SDK pipeline](../supported-devices/oculus-quest-mrtk.md) guide to the end (Cómo configurar Oculus Quest en MRTK mediante la canalización del SDK de XR hasta el final). En la guía se describen los pasos necesarios para configurar Unity y MRTK para usar la canalización del SDK de XR para Oculus Unity.

### <a name="openxr"></a>OpenXR

> [!IMPORTANT]
> OpenXR en Unity solo se admite en Unity 2020.2 y versiones posteriores.
> También admite compilaciones x64, ARM y ARM64.

1. Siga la guía Using [the Mixed Reality OpenXR Plugin for Unity](/windows/mixed-reality/develop/unity/openxr-getting-started) (Uso del complemento OpenXR para Unity), incluidos los pasos para configurar la administración y optimización de complementos XR para instalar el complemento OpenXR en el proyecto. Asegúrese de que lo siguiente se ha instalado correctamente:
   1. Administración de complementos XR
   1. Complemento OpenXR
   1. Mixed Reality complemento OpenXR
1. Vaya a Editar > Project Configuración.
1. Haga clic en la pestaña XR Plug-in Management (Administración de complementos XR) en Project Configuración ventana.
1. Asegúrese de que la opción Inicializar XR al iniciar está activada.
1. (**_Opcional)_** Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y seleccione Microsoft HoloLens conjunto de características.

![Administración de complementos OpenXR](../features/images/xrsdk/PluginManagementOpenXR.png)

> [!NOTE]
> Si tiene un proyecto **preexistente** que usa MRTK de UPM, asegúrese de que la línea siguiente se encuentra en el archivolink.xmlubicado en la carpeta MixedRealityToolkit.Generated.

`<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>`

> [!NOTE]
> Para la versión inicial de MRTK y OpenXR, solo se admiten de forma nativa las HoloLens 2 y Windows Mixed Reality de movimiento. Se agregará compatibilidad con hardware adicional en las próximas versiones.

## <a name="configuring-mrtk-for-the-xr-sdk-pipeline"></a>Configuración de MRTK para la canalización del SDK de XR

::: moniker range=">= mrtkunity-2021-05"
Use cualquiera de los perfiles de MRTK predeterminados, que están configurados en las canalizaciones XR de Unity. Los valores anteriores "DefaultOpenXRConfigurationProfile" y "DefaultXRSDKConfigurationProfile" ahora están etiquetados como obsoletos.
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
Si usa OpenXR, elija "DefaultOpenXRConfigurationProfile" como perfil activo o clone para realizar personalizaciones.

Si usa otros entornos de ejecución de XR en la configuración de administración de complementos de XR, como Windows Mixed Reality u Oculus, elija "DefaultXRSDKConfigurationProfile" como perfil activo o clone para realizar personalizaciones.

Estos perfiles se establecen con los sistemas y proveedores correctos, cuando sea necesario. Consulte [los documentos de perfiles para](../features/profiles/profiles.md#xr-sdk) obtener más información sobre el perfil y la compatibilidad de ejemplo con el SDK de XR.
::: moniker-end

Para migrar un perfil existente al SDK de XR, se deben actualizar los siguientes servicios y proveedores de datos.
::: moniker range=">= mrtkunity-2021-05"
Podrá ver los nuevos proveedores de datos en la pestaña SDK de XR en Unity 2019 o en la vista principal o única de Unity 2020+, donde la XR heredada no existe.

![Pestaña SDK de XR](../features/images/xrsdk/XrsdkTabView.png)
::: moniker-end

### <a name="camera"></a>Cámara

::: moniker range=">= mrtkunity-2021-05"
Agregue los siguientes proveedores de datos
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.WindowsMixedRealityCameraSettings)

![Configuración de la cámara heredada](../features/images/xrsdk/CameraSystemLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRCameraSettings) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| | [`XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityCameraSettings) |
| [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) | [`GenericXRSDKCameraSettings`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKCameraSettings) |
::: moniker-end

![Configuración de la cámara del SDK de XR](../features/images/xrsdk/CameraSystemXRSDK.png)

### <a name="input"></a>Entrada

::: moniker range=">= mrtkunity-2021-05"
Agregue los siguientes proveedores de datos
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.Input.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)

![Configuración de entrada heredada](../features/images/xrsdk/InputSystemWMRLegacy.png)

to
::: moniker-end

| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| [`OpenXRDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRDeviceManager) | [`XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealityDeviceManager) |

__OpenXR:__

![Configuración de entrada de OpenXR](../features/images/xrsdk/InputSystemOpenXR.png)

__Windows Mixed Reality__:

![Configuración de entrada del SDK de XR](../features/images/xrsdk/InputSystemWMRXRSDK.png)

### <a name="boundary"></a>Límite

::: moniker range=">= mrtkunity-2021-05"
Agregue los siguientes proveedores de datos
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`MixedRealityBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.Boundary.MixedRealityBoundarySystem)

![Configuración de límites heredada](../features/images/xrsdk/BoundarySystemLegacy.png)

to
::: moniker-end

| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) | [`XRSDKBoundarySystem`](xref:Microsoft.MixedReality.Toolkit.XRSDK.XRSDKBoundarySystem) |

![Configuración de límites del SDK de XR](../features/images/xrsdk/BoundarySystemXRSDK.png)

### <a name="spatial-awareness"></a>Reconocimiento espacial

::: moniker range=">= mrtkunity-2021-05"
Agregue los siguientes proveedores de datos
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
De [`WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)

![Configuración de reconocimiento espacial heredado](../features/images/xrsdk/SpatialAwarenessLegacy.png)

to
::: moniker-end

::: moniker range=">= mrtkunity-2021-05"
| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| [`XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.OpenXR.OpenXRSpatialAwarenessMeshObserver) (para UWP) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) (para UWP) |
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) (para no UWP) | |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Complemento OpenXR | Windows Complemento XR |
|---------------|-------------------|
| [`XRSDK.GenericXRSDKSpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.GenericXRSDKSpatialMeshObserver) | [`XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.XRSDK.WindowsMixedReality.WindowsMixedRealitySpatialMeshObserver) |
::: moniker-end

![Configuración de reconocimiento espacial del SDK de XR](../features/images/xrsdk/SpatialAwarenessXRSDK.png)

### <a name="controller-mappings"></a>Asignaciones de controladores

Si usa perfiles de asignación de controladores personalizados, abra uno de ellos y ejecute el elemento de menú Mixed Reality Toolkit -> Utilities -> Update -> Controller Mapping Profiles para asegurarse de que se definen los nuevos tipos de controlador del SDK de XR.

## <a name="see-also"></a>Vea también

* [Introducción al desarrollo de AR en Unity](https://docs.unity3d.com/Manual/AROverview.html)
* [Introducción al desarrollo de realidad virtual en Unity](https://docs.unity3d.com/Manual/VROverview.html)
