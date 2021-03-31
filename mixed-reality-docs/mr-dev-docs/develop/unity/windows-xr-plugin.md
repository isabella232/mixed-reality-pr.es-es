---
title: Usar el complemento de Windows XR
description: Aprenda a configurar los proyectos de Unity con y sin MRTK con la compatibilidad de Windows XR.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, MRTK, Windows
ms.openlocfilehash: 24da4b5116b926cfd5eda12db6eedee2f9e85621
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938153"
---
# <a name="using-windows-xr-plugin"></a>Uso del complemento de Windows XR

Para los desarrolladores que tienen como destino Unity 2020, el complemento de Windows XR permite el acceso a características de realidad mixta en auriculares de la realidad de HoloLens 2 y Windows Mixed Reality.  Este complemento también se admite en Unity 2019, aunque hay algunas incompatibilidades conocidas con los delimitadores espaciales de Azure al usar este complemento en esa versión.

Aunque Microsoft y la comunidad han creado herramientas de código abierto, como el kit de herramientas de la [realidad mixta (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) , que configurará automáticamente el entorno de WMR, muchos desarrolladores quieren crear sus experiencias desde cero.  En la siguiente documentación se muestra cómo configurar correctamente un proyecto para el desarrollo de realidad mixta, tanto si usa MRTK como si no.  La configuración que debe cambiar se divide en dos categorías: configuración por proyecto y configuración por escena.

## <a name="setting-up-your-project-with-mrtk"></a>Configurar el proyecto con MRTK

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

> [!div class="nextstepaction"]
> [Pruebe nuestros tutoriales de MRTK](tutorials/mr-learning-base-01.md)

Eche un vistazo a [la documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana de configuración de compilación abierta en el editor de Unity con PC, Mac & plataforma independiente resaltada](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar a la Plataforma universal de Windows:

1.  Seleccionar **archivo > configuración de compilación...**
2.  Seleccione **plataforma universal de Windows** en la lista plataforma y seleccione **Switch Platform (cambiar plataforma** ).
3.  Establecimiento de la **arquitectura** en **ARM 64**
4.  Establecimiento del **dispositivo de destino** en **HoloLens**
5.  Establecer el **tipo de compilación** en **D3D**
6.  Establecimiento del **SDK de UWP** en la **versión más reciente instalada**
7.  Establezca la **configuración de compilación** en **Release** porque hay problemas de rendimiento conocidos con debug

![Captura de pantalla de la ventana Configuración de compilación abierta en el editor de Unity con Plataforma universal de Windows resaltado](images/wmr-config-img-4.png)

Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte:

1. En el editor de Unity, navegue a **editar > configuración del proyecto** y seleccione **Administración de complementos de XR** .

2. Seleccione **instalar administración de complementos de XR**

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-5.png)

3. Seleccione **inicializar XR en el inicio** y **Windows Mixed Reality** .

![Captura de pantalla de la ventana Configuración del proyecto abierta en el editor de Unity con la administración de complementos de XR resalta](images/wmr-config-img-7.png)

4. Expanda la sección **Administración de complementos de XR** y seleccione la pestaña Configuración de la **plataforma de Windows universal** .
5. Si usa Unity 2020 o una versión posterior, verá las opciones para comprobar **OpenXR** o **Windows Mixed Reality**. 
    * Puede elegir en tiempo de ejecución.  Si está desarrollando específicamente para HoloLens 2 o la reverberación de HP G2 y decide probar el **OpenXR**, seleccione el cuadro OpenXR y revise nuestra guía para [usar el complemento Mixed Reality OpenXR para Unity](openxr-getting-started.md) con el fin de configurarlo correctamente para estos dispositivos antes de volver a este tutorial.

> [!NOTE]
> A partir de Unity 2020 LTS, Microsoft adopta el desarrollo con OpenXR.  Al migrar a esta ruta de acceso, en Unity 2021,1 el complemento de Windows XR dejará de usarse y se quitará en 2021,2, de modo que OpenXR la única ruta de acceso admitida. Puede encontrar más información en [uso del complemento OpenXR de realidad mixta](openxr-getting-started.md).

6. Si decide elegir el complemento de **Windows Mixed Reality** , active todas las casillas y establezca el **modo de envío de profundidad** en profundidad de **16 bits** .

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con Windows Mixed Reality sección resaltada](images/wmr-config-img-8.png)
