---
title: Uso del Mixed Reality openXR para Unity
description: Aprenda a habilitar el complemento Mixed Reality OpenXR para proyectos de Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, realidad aumentada, realidad virtual, cascos de realidad mixta, aprendizaje, tutorial, introducción
ms.openlocfilehash: 4c220deeca13c6807857375b71640207823b94ed
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944666"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a>Uso del Mixed Reality openXR para Unity

A partir de la versión 2020.2 de Unity, el paquete Mixed Reality complemento OpenXR de Microsoft está disponible con la herramienta Mixed Reality feature tool de [Microsoft.](welcome-to-mr-feature-tool.md)

## <a name="prerequisites"></a>Prerrequisitos

* Unity 2020.3 LTS o posterior
* Complemento OpenXR de Unity 1.1.1 o posterior
* Visual Studio 2019 o posterior
* Instalación de la compatibilidad con la plataforma **UWP** en Unity para HoloLens 2 aplicaciones

> [!NOTE]
> Si va a compilar aplicaciones de realidad virtual en equipos Windows, Mixed Reality complemento OpenXR no es necesariamente necesario. Sin embargo, querrá instalar el complemento si va a personalizar la asignación de controladores para controladores HP Reverb G2 o crear aplicaciones que funcionen en cascos de realidad virtual HoloLens 2 y de realidad virtual.

## <a name="setting-up-your-project-with-mrtk"></a>Configuración del proyecto con MRTK

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

> [!div class="nextstepaction"]
> [Configuración del proyecto mediante MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Instale el complemento OpenXR con la nueva Mixed Reality Feature Tool. Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el Mixed Reality complemento **OpenXR** en la categoría Mixed Reality Toolkit:

![Mixed Reality paquetes de feature tool con el complemento xr abierto resaltado](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a>Establecimiento del destino de compilación

Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & independiente resaltado](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

Después de configurar la plataforma, debe hacer [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.

## <a name="configuring-xr-plugin-management-for-openxr"></a>Configuración de la administración de complementos XR para OpenXR

Para establecer OpenXR como runtime en Unity:

1. En el Editor de Unity, vaya **a Editar > configuración del proyecto.**
2. En la lista de configuración, seleccione **Administración de complementos XR.**
3. Active los **cuadros Inicializar XR al inicio** y **OpenXR**
4. Si el destino HoloLens 2, asegúrese de que está en la plataforma para UWP y **seleccione Microsoft HoloLens conjunto de características.**

![Captura de pantalla del panel de configuración del proyecto abierto en el editor de Unity con la administración de complementos XR resaltada](images/openxr-img-05.png)

## <a name="optimization"></a>Optimization

Si va a desarrollar para HoloLens 2, vaya a Mixed Reality> **OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance (Aplicar la configuración de proyecto recomendada para HoloLens 2 obtener un mejor rendimiento de la aplicación).

![Captura de pantalla del elemento de menú de realidad mixta abierto con OpenXR seleccionado](images/openxr-img-08.png)

> [!IMPORTANT]
> Si ve un icono de advertencia rojo junto a **Complemento OpenXR,** haga clic en el icono y **seleccione Corregir todo** antes de continuar. Es posible que el editor de Unity tenga que reiniciarse para que los cambios surtan efecto.

![Captura de pantalla de la ventana de validación del proyecto de OpenXR](images/openxr-img-06.png)

Ya está listo para empezar a desarrollar con OpenXR en Unity.  Continúe con la sección siguiente para aprender a usar los ejemplos de OpenXR.

## <a name="try-out-the-unity-sample-scenes"></a>Prueba de las escenas de ejemplo de Unity

### <a name="hololens-2-samples"></a>HoloLens 2 ejemplos

1. En el Editor de Unity, vaya a **Ventana > Administrador de paquetes**
2. En la lista de paquetes, **seleccione Mixed Reality complemento OpenXR.**
3. Busque el ejemplo en la **lista Ejemplos** y seleccione **Importar.**

![Captura de pantalla de unity Administrador de paquetes en el editor de Unity con Mixed Reality complemento OpenXR seleccionado y el botón de importación de ejemplos resaltado](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> Cuando se actualiza un paquete, Unity proporciona la opción de actualizar los ejemplos importados.  Al actualizar un ejemplo importado, se sobrescribirán los cambios realizados en el ejemplo y los recursos asociados.

## <a name="using-mrtk-with-openxr-support"></a>Uso de MRTK con compatibilidad con OpenXR

MRTK-Unity admite Mixed Reality complemento OpenXR a partir de la versión 2.5.3.

1. Abra de [nuevo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho. La compatibilidad con OpenXR está en el **paquete de Foundation.**
2. Vaya al script del componente MixedReality Toolkit en el inspector y cambie al perfil **DefaultOpenXRConfigurationProfile:**

    ![Captura de pantalla de la conmutación de la configuración de MRTK en el componente Mixed Reality Toolkit del inspector](images/openxr-img-11.png)

    1. Consulte la documentación de MRTK para obtener información más [detallada sobre la migración a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Al actualizar desde una versión anterior de MRTK, asegúrese de que la línea siguiente está en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.

## <a name="next-steps"></a>Pasos siguientes

Ahora que tiene el proyecto configurado para OpenXR y [](openxr-supported-features.md) tiene acceso a ejemplos, consulte las características que se admiten actualmente en nuestro complemento OpenXR.

## <a name="have-feedback"></a>¿Tiene comentarios?

OpenXR sigue siendo experimental, por lo que agradecemos cualquier comentario que pueda proporcionarnos para mejorarlo. Para encontrarnos en los foros de [Unity,](https://aka.ms/unityforums) debe etiquetar la publicación del foro con **Microsoft**  +  **OpenXR** y HoloLens 2 **o Windows Mixed Reality**. 

## <a name="see-also"></a>Vea también

* [Configuración de un proyecto sin MRTK](configure-unity-project.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md#how-to-profile-with-unity)
