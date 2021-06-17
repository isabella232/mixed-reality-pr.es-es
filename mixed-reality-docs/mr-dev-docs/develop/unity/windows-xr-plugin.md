---
title: Uso del complemento XR de Windows
description: Obtenga información sobre cómo configurar los proyectos de Unity con y sin MRTK mediante la compatibilidad con Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, mrtk, windows
ms.openlocfilehash: c9733d58236d97db370ce4f58dc1760bdf4eda86
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110232"
---
# <a name="using-windows-xr-plugin"></a>Uso del complemento XR de Windows

Para los desarrolladores que tienen como destino Unity 2020, el complemento XR de Windows permite el acceso a características de realidad mixta en HoloLens 2 y Windows Mixed Reality cascos.  Este complemento también se admite en Unity 2019, aunque hay algunas incompatibilidades conocidas con Azure Spatial Anchors al usar este complemento en esa versión.

Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity/configuration/usingupm) que configurarán automáticamente el entorno WMR, muchos desarrolladores desean crear sus experiencias desde el primer momento.  En la siguiente documentación se muestra cómo configurar correctamente un proyecto para Mixed Reality desarrollo independientemente de si usa MRTK o no.  La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.

## <a name="setting-up-your-project-with-mrtk"></a>Configuración del proyecto con MRTK

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

> [!div class="nextstepaction"]
> [Pruebe nuestros tutoriales de MRTK](./tutorials/mr-learning-base-02.md?tabs=winxr)

Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Si tiene como destino vr de escritorio, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltado](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar al Plataforma universal de Windows:

1.  Seleccione File > Build Settings... (Configuración **de compilación de archivos).**
2.  Seleccione **Plataforma universal de Windows** en la lista Plataforma y seleccione **Cambiar plataforma.**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

Después de configurar la plataforma, debe dejar [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte:

1. En el Editor de Unity, vaya **a Editar > configuración del** proyecto y seleccione Administración de complementos **XR.**

2. Seleccione **Install XR Plugin Management (Instalar administración de complementos XR).**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](images/wmr-config-img-5.png)

3. Seleccione **Initialize XR on Startup (Inicializar XR)** **al iniciar Windows Mixed Reality**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración del complemento XR resaltada](images/wmr-config-img-7.png)

4. Expanda la **sección XR Plug-in Management (Administración** de complementos XR) y seleccione la pestaña **Univeral Windows Platform Settings (Configuración de plataforma de Windows univeral).**
5. Si usa Unity 2020 o posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**. 
    * Puede elegir cualquiera de los entornos de ejecución.  Si va a desarrollar específicamente para HoloLens 2 o HP Reverb G2 y decide probar **OpenXR,** active la casilla OpenXR y revise nuestra guía Uso del complemento [de OpenXR](openxr-getting-started.md) de Mixed Reality para Unity para configurarse correctamente para estos dispositivos antes de volver a este tutorial.

> [!NOTE]
> A partir de Unity 2020 LTS, Microsoft está adoptando el desarrollo con OpenXR.  A medida que migramos a esta ruta de acceso, en Unity 2021.1 el complemento XR de Windows estará en desuso y se quitará en 2021.2, lo que hace que OpenXR sea la única ruta de acceso admitida. Puede encontrar más información en [Uso del complemento Mixed Reality OpenXR.](openxr-getting-started.md)

6. Si decide elegir  el complemento de Windows Mixed Reality, active todas las casillas y establezca **Modo de envío de** profundidad en Profundidad **de 16 bits.**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)