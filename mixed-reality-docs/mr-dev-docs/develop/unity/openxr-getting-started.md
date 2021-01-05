---
title: Uso del complemento OpenXR de realidad mixta para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 9e7f59c57d409d61df73e6d07659bf6c7242202c
ms.sourcegitcommit: 5784336a780486d05db6a627839efe47f08fac36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97880609"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Uso del complemento OpenXR de realidad mixta para Unity

A partir de la versión 2020,2 de Unity, el paquete de complementos de OpenXR mixed reality de Microsoft está disponible mediante el administrador de paquetes de Unity (UPM).

## <a name="prerequisites"></a>Prerrequisitos

* Unity 2020,2 o posterior
* Complemento de Unity OpenXR 0.1.1 o posterior
* Visual Studio 2019 o posterior
* Instalación de la compatibilidad con la plataforma **UWP** en Unity para aplicaciones de HoloLens 2

> [!NOTE]
> Si va a compilar aplicaciones de VR en el equipo con Windows, el complemento OpenXR de realidad mixta no es necesariamente necesario. Sin embargo, querrá instalar el complemento si está personalizando la asignación de controladores para los controladores de HP reverberación G2 o la creación de aplicaciones que funcionan en los auriculares de HoloLens 2 y VR.

## <a name="installing-the-mixed-reality-openxr-plugin"></a>Instalación del complemento OpenXR de realidad mixta

El proyecto debe instalar los paquetes de administración de **Complementos** de **OpenXR** y XR antes de usar el complemento Mixed Reality OpenXR. Si ya las ha instalado, ¡ genial! Si no es así, al instalar el complemento OpenXR de realidad mixta se instalarán automáticamente como dependencias:

1. En el editor de Unity, vaya a **editar > configuración del proyecto > administrador de paquetes** .
2. Expanda la sección **registros de ámbito** , escriba la información siguiente y seleccione **Guardar**:
    * Establecer **nombre** en **Microsoft Mixed Reality**
    * Establecer **dirección URL** en **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**
    * Establezca **ámbitos** en **com. Microsoft. mixedreality**

3. En **Configuración avanzada**, seleccione **Habilitar paquetes de vista previa** .

![Captura de pantalla de la ventana Administrador de paquetes de Unity abierta en configuración del proyecto](images/openxr-img-01.png)

El administrador de paquetes de Unity usa un archivo *de manifiesto denominadomanifest.jsen* para determinar qué paquetes se deben instalar y los registros desde los que se pueden instalar.

> [!IMPORTANT]
> OpenXR sigue siendo experimental en Unity y este proceso puede cambiar con el tiempo a medida que trabajamos para optimizar la experiencia del desarrollador.

### <a name="registering-the-mixed-reality-dependency"></a>Registrar la dependencia de realidad mixta

Una vez que se ha agregado el registro de ámbito de Microsoft Mixed Reality al manifiesto, se puede especificar el paquete OpenXR.

Para agregar el paquete OpenXR:

1. Abra **[projectRoot]/Packages/manifest.js** en un editor de texto como Visual Studio Code
    1. Para obtener aquí, haga clic con el botón derecho en **paquetes** en el panel izquierdo de la ventana de proyecto. A continuación, haga clic en **Mostrar en el explorador**.
    ![Captura de pantalla de la lista de paquetes en la ventana proyecto](images/packages.png)
1. Modifique la sección de dependencias de los *paquetes/manifest.jsen* el archivo como se indica a continuación:

    > [!IMPORTANT]
    > Puede haber más dependencias en el archivo de manifiesto de las que se muestran aquí. No elimine ninguno de ellos, simplemente agregue la dependencia OpenXR a la lista.

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.1",
      }
    ```

1. Guarde el archivo, vuelva al editor de Unity y abra el administrador de **paquetes** para confirmar que el complemento está instalado:

    ![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta resaltado](images/openxr-img-03.png)

    > [!Note]
    > Si se quita el paquete OpenXR mediante el administrador de paquetes de Unity, tendrá que volver a agregarlo mediante los pasos descritos anteriormente.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configuración de administración de complementos de XR para OpenXR

Para establecer OpenXR como el tiempo de ejecución en Unity:

1. En el editor de Unity, vaya a **editar > configuración del proyecto** .
2. En la lista de opciones, seleccione **Administración de complementos de XR**
3. Active las casillas **inicializar XR en el inicio** y **OpenXR (versión preliminar)**
4. Si el destino es HoloLens 2, asegúrese de que está en la plataforma UWP y seleccione **conjunto de características de Microsoft HoloLens** .

![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-img-05.png)

> [!IMPORTANT]
> Si ve un icono de advertencia rojo junto al **complemento OpenXR (versión preliminar)**, haga clic en el icono y seleccione **corregir todo** antes de continuar. Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.

![Captura de pantalla de la ventana de validación del proyecto OpenXR](images/openxr-img-06.png)

Ahora está listo para empezar a desarrollar con OpenXR en Unity.  Continúe con la siguiente sección para aprender a usar los ejemplos de OpenXR.

## <a name="optimization"></a>Optimization

Si está desarrollando para HoloLens 2, vaya a **Mixed Reality> OpenXR > aplicar la configuración de proyecto recomendada para hololens 2** para obtener un mejor rendimiento de la aplicación.

![Captura de pantalla del elemento de menú de realidad mixta abrir con OpenXR seleccionado](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a>Pruebe las escenas de ejemplo de Unity

Para el uso de uno o varios de los ejemplos, instale [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) desde el **Administrador de paquetes**:

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con AR Foundation resaltado](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a>Ejemplos de HoloLens 2

1. En el editor de Unity, navegue a la **ventana > administrador de paquetes**
2. En la lista de paquetes, seleccione **Mixed Reality OpenXR plugin** .
3. Busque el ejemplo en la lista de **ejemplos** y seleccione **importar** .

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-10.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Cuando se actualiza un paquete, Unity ofrece la opción de actualizar los ejemplos importados.  Al actualizar un ejemplo importado se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado el proyecto para OpenXR y tiene acceso a los ejemplos, consulte [las características](openxr-supported-features.md) que se admiten actualmente en nuestro complemento OpenXR.

## <a name="see-also"></a>Consulte también

* [Configuración de un proyecto sin MRTK](configure-unity-project.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
