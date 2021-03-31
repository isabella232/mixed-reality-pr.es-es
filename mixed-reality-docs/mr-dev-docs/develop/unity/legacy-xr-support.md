---
title: Usar la compatibilidad integrada de XR heredada
description: Aprenda a configurar los proyectos de Unity con y sin MRTK con la compatibilidad integrada de XR heredada.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, MRTK
ms.openlocfilehash: 0860154034a63d5058da09a3b842e70bc3775dc5
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105938156"
---
# <a name="using-legacy-built-in-xr-support"></a>Usar la compatibilidad integrada de XR heredada

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

Después de establecer la plataforma, debe dejar que Unity sepa crear una [vista envolvente](../../design/app-views.md) en lugar de una vista 2D cuando se exporte.

> [!CAUTION]
> El XR heredado está en desuso en Unity 2019 y se quitó en Unity 2020.

1. Abra **configuración del reproductor...** en la **configuración de compilación... y** expanda el grupo de **configuración XR**
2. En la sección **configuración de XR** , seleccione **realidad virtual compatible** para agregar la lista de dispositivos de realidad virtual.
3. Establecer el **formato de profundidad** en profundidad de **16 bits** y habilitar el **uso compartido del búfer de profundidad**
4. Establecer el **modo de representación estéreo** en **una instancia de paso único**
5. Seleccione **WSA Holographic Remoting compatible** si desea usar Holographic Remoting 

![Captura de pantalla de la ventana de configuración del proyecto abierta en el editor de Unity con la sección configuración del reproductor resaltada](images/wmr-config-img-9.png)