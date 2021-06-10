---
title: Configuración de MRTK de Android e iOS (ARFoundation)
description: Documentación para configurar MRTK para Android e iOS (ARFoundation) en Unity
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, AR Core, AR Kit, iOS, IOS, Android, AR Foundation
ms.openlocfilehash: 9f621008db76e3f8e443545b795db442d7c17dda
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345138"
---
# <a name="how-to-configure-mrtk-for-ios-and-android-experimental"></a>Configuración de MRTK para iOS y Android [Experimental]

## <a name="install-required-packages"></a>Instalación de los paquetes requeridos

1. Descargue e importe el **paquete Microsoft.MixedReality.Toolkit.Unity.Foundation,** [desde GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.3.0) o [el](../configuration/usingupm.md) Administrador de paquetes

1. En unity Administrador de paquetes (UPM), instale los siguientes paquetes:

    **Unity 2018.4.x**

    | **Android** | **iOS** | Comentarios |
    | --- | --- | --- |
    | AR Foundation  <br/> Versión: 1.5.0 - versión preliminar 6 | AR Foundation  <br/> Versión: 1.5.0 - versión preliminar 6 | Para Unity 2018.4, este paquete se incluye como versión preliminar. Para ver el paquete: `Window` > `Package Manager` > `Advanced` > `Show Preview Packages` |
    | Complemento ARCore XR <br/> Versión: 2.1.2 | Complemento ARKit XR <br/> Versión: 2.1.2 | |

    **Unity 2019.4.x**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versión: 2.1.8 |  AR Foundation  <br/> Versión: 2.1.8 |
    | Complemento ARCore XR <br/> Versión: 2.1.11 | Complemento ARKit XR <br/> Versión: 2.1.9 |

    **Unity 2020.1.x (actualmente no compatible formalmente, incluido solo con fines informativos)**

    | **Android** | **iOS** |
    | --- | --- |
    | AR Foundation  <br/> Versión: 3.1.3 |  AR Foundation  <br/> Versión: 3.1.3 |
    | Complemento ARCore XR <br/> Versión: 3.1.4 | Complemento ARKit XR <br/> Versión: 3.1.3 |

1. Actualice el scripting de UnityAR de MRTK invocando el elemento de menú: Mixed Reality > **Toolkit > Utilities > UnityAR > Update Scripting Defines**

    ![Actualizar scripting define](../features/images/UpdateScriptingDefineUnityAR.png)


## <a name="enabling-the-unity-ar-camera-settings-provider"></a>Habilitación del proveedor de configuración de la cámara ar de Unity

En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit. Los pasos necesarios para otros registradores de servicios pueden ser diferentes.

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.

    ![Jerarquía de escena configurada de MRTK](../features/images/MRTK_ConfiguredHierarchy.png)

1. Seleccione **Copiar y personalizar para** clonar el perfil de MRTK para habilitar la configuración personalizada.

    ![Clonación del perfil de MRTK](../features/images/camera-system/CloneProfileARFoundation.png)

1. Seleccione **Clonar** junto al perfil de cámara.

    ![Clonación del perfil de cámara de MRTK](../features/images/camera-system/CloneCameraProfileARFoundation.png)

1. Vaya al panel Inspector a la sección sistema de cámara y expanda la **sección Proveedores de configuración de** cámara.

    ![Expandir proveedores de configuración](../features/images/camera-system/ExpandProviders.png)

1. Haga **clic en Agregar proveedor de configuración de** cámara y expanda la entrada Nueva configuración de cámara **recién** agregada.

    ![Expansión del nuevo proveedor de configuración](../features/images/camera-system/ExpandNewProvider.png)

1. Selección del proveedor de configuración de la cámara ar de Unity

    ![Selección del proveedor de configuración de AR de Unity](../features/images/camera-system/SelectUnityArSettings.png)

    Para obtener más información sobre cómo configurar el proveedor de configuración de la cámara ar de Unity: [Proveedor de configuración de la cámara ar de Unity](../features/camera-system/unity-ar-camera-settings.md).

> [!NOTE]
> Esta instalación comprueba (cuando se inicia la aplicación) si los componentes de AR Foundation están en la escena. Si no es así, se agregan automáticamente para que funcione con ARCore y ARKit.
> Si necesita establecer un comportamiento específico, debe agregar los componentes que necesita por sí mismo.
> Para obtener más información sobre los componentes e instalación de AR Foundation, consulte esta [documentación.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/manual/index.html#samples)

## <a name="building-a-scene-for-android-and-ios-devices"></a>Creación de una escena para dispositivos Android e iOS

1. Asegúrese de que ha agregado el proveedor de configuración de cámara UnityAR a la escena.

1. Cambie la plataforma a Android o iOS en la configuración de compilación de Unity.

1. Asegúrese de que el proveedor de administración del complemento XR asociado está habilitado.

    Administración de complementos XR de iOS:  ![ Administración de complementos XR para iOS](../features/images/XRManagementiOS.png)

1. Compilación y ejecución de la escena

## <a name="see-also"></a>Vea también

- [Configuración de la cámara ar de Unity](../features/camera-system/unity-ar-camera-settings.md)
