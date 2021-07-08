---
title: Azure Spatial Anchors para iOS y Android
description: Complete este curso para aprender a implementar un proyecto de Unity con Mixed Reality Toolkit (MRTK) y Azure Spatial Anchors en Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, android, ios, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, AR Foundation, ARCore, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 67bda33f8d2d0711c83791be2e76d91b53ff934f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403434"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Azure Spatial Anchors para iOS y Android

En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.

## <a name="objectives"></a>Objetivos

* Aprender a compilar el proyecto en el dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity
* Aprender a compilar el proyecto en su dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity

## <a name="installing-inbuilt-unity-packages"></a>Instalación de paquetes de Unity integrados

[!INCLUDE[](includes/installing-inbuilt-unity-packages-for-asa-android-and-ios.md)]

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configuración de MRTK para la cámara de AR Foundation

En esta sección, obtendrá información sobre cómo configurar MRTK para realizar la implementación en un dispositivo móvil.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, seleccione la pestaña **Camera** (Cámara), clone el perfil de la cámara y asígnele un nombre adecuado, por ejemplo, **AzureSpatialAnchors_ARCameraProfile**:

![Unity con ARCameraProfile recién creado seleccionado](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones del artículo [Configuración de los perfiles de Mixed Reality Toolkit](mr-learning-base-03.md).

Con la pestaña **Camera** (Cámara) aún seleccionada en la ventana Inspector, expanda **Camera Setting Providers** (Proveedores de configuración de la cámara) y haga clic en "-" para quitar **Windows Mixed Reality Camera Setting** (Configuración de la cámara de Windows Mixed Reality) o **XR SDK Windows Mixed Reality Camera Setting** (Configuración de la cámara de Windows Mixed Reality para el SDK de XR):

![ARCameraProfile de Unity con un nuevo proveedor de datos agregado ](images/mr-learning-asa/asa-05-section2-step1-2.png)

y haga clic en el botón **+ Add Camera Setting Provider** (+ Agregar proveedor de configuración de la cámara) y, a continuación, expanda **New data provider** (Nuevo proveedor de datos):

![Cámara de AR agregada para Android](images/mr-learning-asa/asa-05-section2-step1-3.png)

Con la lista desplegable **Typo** (Tipo), cambie el tipo a **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![ARCameraProfile de Unity con la ruta de acceso a la selección del tipo de proveedor de datos](images/mr-learning-asa/asa-05-section2-step1-4.png)

Invoque el siguiente elemento de menú para actualizar las definiciones del scripting de MRTK UnityAR: **Mixed Reality** > **Toolkit** > **Utilities** > **UnityAR > Update Scripting Defines** (Realidad mixta > Kit de herramientas > Utilidades > UnityAR > Actualizar definiciones del scripting).

## <a name="building-your-application-to-your-android-device"></a>Compilación de la aplicación en el dispositivo Android

En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en un dispositivo Android.

En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a Android.

![Ventana Build Settings (Configuración de compilación) de Unity con la plataforma Android seleccionada](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).

Cierre la ventana Build Settings (Configuración de compilación).

En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar el proyecto para MRTK) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Configurador del proyecto MRTK de Unity 1](images/mr-learning-asa/asa-05-section3-step1-2.png)

En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración), seleccione **Vulkan** y quítelo haciendo clic en el símbolo **"-"** .

![Other Settings (Otra configuración) de Unity con Vulkan seleccionado](images/mr-learning-asa/asa-05-section3-step1-3.png)

[!INCLUDE[](includes/project-setting-for-asa-android.md)]

En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación). A continuación, use un cable USB, conecte el dispositivo Android al equipo y selecciónelo en la lista desplegable **Run Device** (Ejecutar dispositivo):

![Ventana Build Settings (Configuración de compilación) de Unity con escena agregada y Run Device (Ejecutar dispositivo) seleccionado](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Si el dispositivo no aparece en la lista desplegable Run Device (Ejecutar dispositivo), puede que tenga que presionar el botón Refresh (Actualizar) situado junto a dicha lista.

En la ventana Configuración de compilación, haga clic en el botón **Build and Run** (Compilar y ejecutar) para abrir la ventana Build Android (Compilar Android).

Elija una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, asigne a apk un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y haga clic en el botón **Save** (Guardar) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Save (Guardar) para Android](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
> Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos asociados de compatibilidad con la compilación de Android.

Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilación de la aplicación en el dispositivo iOS

En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en su dispositivo iOS.

En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a iOS.

![Ventana Build Settings (Configuración de compilación) de Unity con iOS seleccionado](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).

Cierre la ventana Build Settings (Configuración de compilación).

En el menú de Unity, seleccione **Mixed Reality** > **Toolkit** > **Utilities** > **Configure Project for MRTK** (Realidad mixta > Kit de herramientas > Utilidades > Configurar el proyecto para MRTK) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity para iOS](images/mr-learning-asa/asa-05-section4-step1-2.png)

[!INCLUDE[](includes/project-setting-for-asa-ios.md)]

En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración) y desactive la casilla **Strip Engine Code** (Código del motor de franja).

![Other Settings (Otra configuración) de Unity con Strip Engine Code (Código del motor de franja) deshabilitado](images/mr-learning-asa/asa-05-section4-step1-3.png)

Cierre la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana **Build Settings** (Configuración de compilación).

En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación):

![Ventana Build Settings (Configuración de compilación) de Unity con la escena agregada](images/mr-learning-asa/asa-05-section4-step1-4.png)

En la ventana Configuración de compilación, haga clic en el botón **Build** (Compilar) para abrir la ventana Build iOS (Compilar iOS).

Elija una ubicación adecuada para almacenar el proyecto Xcode, por ejemplo, _D:\MixedRealityLearning\Builds_, cree una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y, luego, haga clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![Ventana Build Settings (Configuración de compilación) de Unity con la ventana de solicitud Save (Guardar) para iOS](images/mr-learning-asa/asa-05-section4-step1-5.png)

Una vez completado el proceso de compilación, siga las instrucciones del artículo [Exportación del proyecto de Xcode](/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar el proyecto de Xcode en el dispositivo iOS.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.
