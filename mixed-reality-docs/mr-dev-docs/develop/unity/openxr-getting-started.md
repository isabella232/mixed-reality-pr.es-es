---
title: Uso del complemento OpenXR de realidad mixta para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 9b95a0978522fb9fefaca3c4b96189131b88d0ec
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230873"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Uso del complemento OpenXR de realidad mixta para Unity

A partir de la versión 2020,2 de Unity, el paquete de complementos de OpenXR mixed reality de Microsoft está disponible mediante el administrador de paquetes de Unity (UPM).

## <a name="prerequisites"></a>Requisitos previos

* Unity 2020,2 o posterior
* Complemento de Unity OpenXR 0.1.4 o posterior
* Visual Studio 2019 o posterior
* Instalación de la compatibilidad con la plataforma **UWP** en Unity para aplicaciones de HoloLens 2

> [!NOTE]
> Si va a compilar aplicaciones de VR en el equipo con Windows, el complemento OpenXR de realidad mixta no es necesariamente necesario. Sin embargo, querrá instalar el complemento si está personalizando la asignación de controladores para los controladores de HP reverberación G2 o la creación de aplicaciones que funcionan en los auriculares de HoloLens 2 y VR.

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a>Instalación de OpenXR con la herramienta de característica de realidad mixta

Instale el complemento OpenXR con la nueva aplicación de herramienta de características de realidad mixta. Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el paquete de **Complementos Mixed Reality OpenXR** en la categoría del kit de herramientas de realidad mixta:

![Ventana paquetes de herramientas de característica de realidad mixta con el complemento Open XR resaltado](images/feature-tool-openxr.png)

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

![Captura de pantalla del administrador de paquetes de Unity abierto en el editor de Unity con el complemento OpenXR de realidad mixta seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Cuando se actualiza un paquete, Unity ofrece la opción de actualizar los ejemplos importados.  Al actualizar un ejemplo importado se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.

## <a name="using-mrtk-with-openxr-support"></a>Uso de MRTK con compatibilidad con OpenXR

MRTK-Unity admite el complemento OpenXR de realidad mixta a partir de la versión 2.5.3.

1. Vuelva a abrir la [herramienta de característica de realidad mixta](welcome-to-mr-feature-tool.md) para instalar el kit de herramientas de realidad mixta, si no lo ha hecho ya. La compatibilidad con OpenXR se encuentra en el paquete **Foundation** .
2. Vaya al script del componente MixedReality Toolkit en el inspector y cambie al perfil **DefaultOpenXRConfigurationProfile** :

    ![Captura de pantalla de cambio de la configuración de MRTK en el componente del kit de herramientas de realidad mixta en el inspector](images/openxr-img-11.png)

    1. Consulte la documentación de MRTK para obtener [información más detallada sobre cómo migrar a OpenXR](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).

> [!NOTE]
> Al actualizar desde una versión anterior de MRTK, asegúrese de que la línea siguiente se encuentra en el archivo **assets/MixedRealityToolkit. generated/link.xml** :
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o una versión más reciente.

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado el proyecto para OpenXR y tiene acceso a los ejemplos, consulte [las características](openxr-supported-features.md) que se admiten actualmente en nuestro complemento OpenXR.

## <a name="have-feedback"></a>¿Tiene comentarios?

OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que nos proporcione para ayudarlo a mejorar. Nos encontrarás en los [foros de Unity](https://aka.ms/unityforums) mediante el etiquetado de tu entrada de foro con **Microsoft**  +  **OpenXRs** y **HoloLens 2** o **Windows Mixed Reality**.

## <a name="see-also"></a>Consulte también

* [Configuración de un proyecto sin MRTK](configure-unity-project.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
