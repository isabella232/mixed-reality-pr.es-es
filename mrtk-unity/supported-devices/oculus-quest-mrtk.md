---
title: Oculus Quest MRTK
description: Documentación que se debe configurar para Oculus Quest en MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Oculus Unity,
ms.openlocfilehash: 0892e0d416cd07d1bedbeea0ddb316e3eb012b94
ms.sourcegitcommit: 4c1dd5c22af69eeb192425118c2bfb95344b8dd9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110441179"
---
# <a name="building-and-deploying-mrtk-to-oculus-quest-using-the-xr-sdk-pipeline"></a>Compilación e implementación de MRTK en Oculus Quest mediante la canalización del SDK de XR

Se [requiere una misión de Oculus.](https://www.oculus.com/quest/)

La compatibilidad de MRTK con Oculus Unity se realiza a través de dos orígenes diferentes, la canalización del SDK de XR de Unity y el paquete de Unity de integración de Oculus. El **proveedor de datos Oculus XRSDK** permite el uso de ambos orígenes y debe usarse para implementar MRTK en Oculus Quest.

La [canalización del SDK de XR](https://docs.unity3d.com/Manual/XR.html) de Unity permite el uso de controladores Oculus Touch y el seguimiento de la cabeza con Oculus Unity.
Esta canalización es el estándar para desarrollar aplicaciones XR en Unity 2019.3 y posteriores. Para usar esta canalización, asegúrese de usar **Unity 2019.3 o una versión más reciente.** Esto es **necesario para** implementar aplicaciones MRTK en Oculus Quest. 

El paquete de Unity de integración [de Oculus](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) permite el uso del **seguimiento manual** con Oculus Unity. Este proveedor de datos **NO usa** la canalización del SDK **de XR** de Unity **ni la canalización XR heredada.**

## <a name="setting-up-project-for-the-oculus-quest"></a>Configuración del proyecto para Oculus Quest

1. Siga [estos pasos](https://developer.oculus.com/documentation/unity/book-unity-gsg/) para asegurarse de que el proyecto está listo para implementarse en Oculus Quest.

1. Asegúrese de [que el modo de](https://developer.oculus.com/documentation/native/android/mobile-device-setup/) desarrollador está habilitado en el dispositivo. La instalación de los controladores de ADB de Oculus es opcional.

## <a name="setting-up-the-xr-sdk-pipeline-for-oculus-quest"></a>Configuración de la canalización del SDK de XR para Oculus Quest

1. Asegúrese de que **el complemento Oculus XR** está instalado en **La ventana --> Administrador de paquetes**

    ![Paquete del complemento XR de Oculus](../images/cross-platform/oculus-quest/OculusXRPluginPackage.png)

1. Asegúrese de que el proveedor de complementos de Oculus está incluido en el proyecto; para ello, vaya a Editar la configuración del proyecto **--> --> XR Plug-in Management --> Plug-in Providers** (Editar la configuración del proyecto de > --> XR Plug-in Management --> Plug-in Providers[Editar la configuración del proyecto --> XR Plug-in Management --> Plug-in Providers].

    ![Proveedor de complementos de Oculus](../images/cross-platform/oculus-quest/OculusPluginProvider.png)

## <a name="setting-up-the-oculus-integration-unity-package-to-enable-handtracking"></a>Configuración del paquete de Unity de integración de Oculus para habilitar el seguimiento a mano

1. Descargue e importe [Oculus Integration desde](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) el Almacén de recursos de Unity. La versión más reciente probada para funcionar es la 20.0.0. Las versiones anteriores se pueden encontrar en este [archivo](https://developer.oculus.com/downloads/package/unity-integration-archive/)

1. Vaya a Mixed Reality Toolkit > Utilities > Oculus > integrar módulos de Unity de integración de Oculus. Al hacerlo, se actualizarán las definiciones de asmdefs con las definiciones y las referencias necesarias para que el código de Oculus Quest pertinente funcione. También actualizará el archivo csc para filtrar las advertencias obsoletas producidas por los recursos de integración de Oculus. El repositorio MRTK contiene un archivo csc que convierte las advertencias en errores. Esta conversión detiene el proceso de MRTK-Quest configuración.

    ![Asmdef de integración de Oculus](../images/cross-platform/oculus-quest/OculusIntegrationAsmdef.png)

1. En la carpeta Oculus importada (debe encontrarse en Assets/Oculus), hay un objeto que puede incluirse en scripts denominado OculusProjectConfig. En ese archivo de configuración, debe establecer HandTrackingSupport en "Controladores y manos".

    ![Controlador de integración de Oculus y manos](../images/cross-platform/oculus-quest/OculusIntegrationControllerAndHands.png)

## <a name="setting-up-the-scene"></a>Configuración de la escena

1. Cree una nueva escena de Unity o abra una escena preexistida como HandInteractionExamples.
1. Para agregar MRTK a la escena, vaya a **Mixed Reality Toolkit** Add to Scene and Configure (Agregar a la escena y  >  **configurar)**

## <a name="using-the-oculus-xr-sdk-data-provider"></a>Uso del proveedor de datos del SDK de Oculus XR

1. Configuración del perfil para usar el proveedor **de datos del SDK de Oculus XR**
    - Si no pretende modificar los perfiles de configuración
        - Cambie el perfil a DefaultXRSDKConfigurationProfile y vaya a [Compilación e implementación del proyecto en Oculus Quest.](oculus-quest-mrtk.md#build-and-deploy-your-project-to-oculus-quest)

    - De lo contrario, siga estos pasos:
        - Seleccione el objeto de juego MixedRealityToolkit en la jerarquía y seleccione Copiar y **personalizar** para clonar el perfil de realidad mixta predeterminado.

        ![Clonar perfil](../images/cross-platform/CloneProfile.png)

        - Selección del perfil **de configuración** de entrada

        ![Perfil de configuración de entrada](../images/cross-platform/InputConfigurationProfile.png)

        - Seleccione **Clonar** en el perfil del sistema de entrada para habilitar la modificación.

        ![Clonar perfil del sistema de entrada](../images/cross-platform/CloneInputSystemProfile.png)

        - Abra la sección Proveedores  de datos **de** entrada, seleccione Agregar proveedor de datos en la parte superior y se agregará un nuevo proveedor de datos al final de la lista.  Abra el nuevo proveedor de datos y establezca **el** tipo en **Microsoft.MixedReality.Toolkit.XRSDK.Oculus > OculusXRSDKDeviceManager**

        ![Agregar proveedor de datos XRSDK de Oculus](../images/cross-platform/oculus-quest/OculusAddDataXRSDKProvider.png)

1. El proveedor de datos del SDK de Oculus XR incluye un prefab de cámara OVR que configura automáticamente el proyecto con un equipo de cámara OVR y las manos de OVR para enrutar correctamente la entrada. Agregar manualmente un equipo de cámara OVR a la escena requerirá la configuración manual de la configuración y la entrada.

## <a name="build-and-deploy-your-project-to-oculus-quest"></a>Compilación e implementación del proyecto en Oculus Quest

1. Conecte Oculus Quest a través de un cable USB 3.0 -> USB C
1. Vaya a **File > Build Settings (Configuración de compilación de archivos).**
1. Cambio de la implementación a **Android**
1. Asegúrese de que Oculus Quest está seleccionado como el dispositivo de ejecución aplicable.

    ![Oculus Run Device](../images/cross-platform/oculus-quest/OculusRunDevice.png)

1. Seleccione Build and Run (Compilar y ejecutar).
    - Es probable que encuentre el siguiente conjunto de errores de compilación al seleccionar *Compilar y ejecutar* la primera vez. Debería poder realizar la implementación correctamente al seleccionar Compilar *y ejecutar de* nuevo.

    ![Errores de compilación esperados de Oculus](../images/cross-platform/oculus-quest/OculusExpectedBuildErrors.png)

1. Acepte el _símbolo del sistema Permitir depuración USB_ desde dentro de la misión.
1. Ver la escena dentro de Oculus Scene

## <a name="removing-oculus-integration-from-the-project"></a>Quitar la integración de Oculus del proyecto

1. Vaya a Mixed Reality Toolkit > Oculus > Oculus Integration Unity Modules  ![ Oculus Separation Asmdef](../images/cross-platform/oculus-quest/OculusSeparationAsmdef.png)
1. Deje que Unity se actualice como referencias en Microsoft.MixedReality.Toolkit.Providers.Oculus.asmdef y se modifican otros archivos en este paso.
1. Cerrar Unity
1. Cierre Visual Studio, si está abierto
1. Abra Explorador de archivos y vaya a la raíz del proyecto de Unity de MRTK.
1. Eliminación del directorio UnityProjectName/Library
1. Eliminación del directorio UnityProjectName/Assets/Oculus
1. Eliminación del archivo UnityProjectName/Assets/Oculus.meta
1. Volver a abrir Unity

## <a name="common-errors"></a>Errores comunes

### <a name="quest-not-recognized-by-unity"></a>Misión no reconocida por Unity

Asegúrese de que las rutas de acceso de Android están configuradas correctamente. Si sigue teniendo problemas, siga esta [guía.](https://developer.oculus.com/documentation/unity/book-unity-gsg/#install-android-tools)

**Editar > preferencias > herramientas externas > Android**

![Configuración de herramientas de Android](../images/cross-platform/oculus-quest/AndroidToolsConfig.png)
