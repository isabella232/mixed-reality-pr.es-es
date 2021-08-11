---
title: Uso de la compatibilidad con XR integrada heredada
description: Aprenda a configurar los proyectos de Unity con y sin MRTK mediante la compatibilidad con XR integrada heredada.
author: hferrone
ms.author: alexturn
ms.date: 03/26/2021
ms.topic: article
keywords: Unity, realidad mixta, desarrollo, introducción, nuevo proyecto, Windows Mixed Reality, UWP, XR, rendimiento, heredado, mrtk
ms.openlocfilehash: 534df0b9c4efbe62b00af6cccb74f4203c1557e9479b2101320bab3bbdb5e565
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192064"
---
# <a name="using-legacy-built-in-xr-support"></a>Uso de la compatibilidad con XR integrada heredada

## <a name="setting-up-your-project-with-mrtk"></a>Configuración del proyecto con MRTK

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

> [!div class="nextstepaction"]
> [Pruebe nuestros tutoriales de MRTK](./tutorials/mr-learning-base-02.md?tabs=wsa)

Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Si tiene como destino Desktop VR, se recomienda usar la plataforma independiente de PC seleccionada de forma predeterminada en un nuevo proyecto de Unity:

![Captura de pantalla de la ventana Configuración compilación abierta en el editor de Unity con PC, Mac & independiente resaltado](images/wmr-config-img-3.png)

Si tiene como destino HoloLens 2, debe cambiar a la Plataforma de Windows universal:

1.  Seleccione **Archivo > compilación Configuración...**
2.  Seleccione **Universal Windows Platform en** la lista Platform (Plataforma) y seleccione Switch Platform **(Cambiar plataforma).**
3.  Establezca la **arquitectura** en **ARM 64**
4.  Establezca **Target Device** (Dispositivo de destino) en **HoloLens**.
5.  Establezca **Build Type** (Tipo de compilación) en **D3D**.
6.  Establezca el **SDK de UWP** en la **Latest installed** (última versión instalada)
7.  Establezca la **configuración de compilación** en **Release** (Publicación) porque hay problemas de rendimiento conocidos con Debug (Depuración).

![Captura de pantalla de la ventana Configuración compilación abierta en el editor de Unity con la plataforma Windows universal resaltada](images/wmr-config-img-4.png)

Después de configurar la plataforma, debe hacer [](../../design/app-views.md) que Unity sepa que debe crear una vista inmersiva en lugar de una vista 2D cuando se exporte.

> [!CAUTION]
> La XR heredada está en desuso en Unity 2019 y se ha quitado en Unity 2020.

1. Abra **player Configuración...** desde el **cuadro de diálogo Configuración... ventana** y expanda el **grupo de Configuración XR**
2. En la **sección XR Configuración,** seleccione **Virtual Reality Supported (Compatible con Virtual Reality)** para agregar la lista Dispositivos de realidad virtual.
3. Establezca **Formato de profundidad en** Profundidad de **16 bits y** habilite El uso compartido del búfer de **profundidad**
4. Establecer **el modo de representación estéreo en** Instancia de paso **único**
5. Seleccione **WSA Holographic Remoting Supported (Comunicación** remota holográfica de WSA compatible) si desea usar la comunicación remota holográfica. 

![Captura de pantalla Project ventana de configuración abierta en el editor de Unity con la sección Configuración del reproductor resaltada](images/wmr-config-img-9.png)