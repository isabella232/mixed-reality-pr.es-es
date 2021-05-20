---
title: Ventana de compilación de MRTK
description: Documentación sobre el uso de la ventana de compilación en MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, compilación, ventana de compilación, herramientas
ms.openlocfilehash: 00ccbc5cfbb3b034771585a1263c624309b08465
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196872"
---
# <a name="build-window"></a>Ventana de compilación
![Compilación & flujo de implementación](images/MRTK_BuildWindow0.png)

La ventana de compilación de MRTK facilita la compilación & implementar MRTK-Unity proyectos. Con un solo clic, puede compilar un proyecto de Unity y generar Visual Studio solución(. SLN), paquete de aplicación para UWP(. APPX) e instale el paquete de aplicación en el dispositivo. 


## <a name="unity-build-options"></a>Opciones de compilación de Unity
![Ventana Compilación: Opciones de compilación de Unity 1](images/MRTK_BuildWindow1.png)

Estas escenas son de la configuración de compilación de Unity. Puede cambiar el tipo de dispositivo de destino mediante el menú desplegable.

## <a name="appx-build-options"></a>Opciones de compilación de Appx
![Ventana Compilación: Opciones de compilación de Appx 2](images/MRTK_BuildWindow2.png)

En esta pestaña se muestra la configuración de Visual Studio solución. Para habilitar HoloLens 2 entrada de seguimiento ocular, active la opción **Gaze Input Capability** (Funcionalidad de entrada de mirada). 

Puede asignar el archivo .glb en el campo Modelo del iniciador de aplicaciones **3D** para el icono personalizado del iniciador de aplicaciones 3D. Consulte la [guía de diseño del iniciador de aplicaciones 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obtener más información.

De forma predeterminada, **Incremento automático** está activado en Opciones de control de versiones. Las versiones de AppX se incrementarán automáticamente.


## <a name="deploy-options"></a>Opciones de implementación
![Ventana Compilación: Opciones de implementación 3](images/MRTK_BuildWindow3.png)

En esta pestaña, puede conectarse al dispositivo si escribe el nombre de usuario y la contraseña de la Portal de dispositivos. 

En la parte inferior de la página, puede encontrar una lista de los paquetes de aplicación que se han creado. 

