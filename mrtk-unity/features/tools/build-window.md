---
title: Ventana de compilación
description: Documentación sobre el uso de la ventana de compilación en MRTK para Unity.
author: cre8ivepark
ms.author: dongpark
ms.date: 04/06/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, compilación, ventana de compilación, herramientas
ms.openlocfilehash: b0b2bb1d06a561f5f647d01145fe88f562c53017
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176148"
---
# <a name="build-window"></a>Ventana de compilación
![Compilación & flujo de implementación](images/MRTK_BuildWindow0.png)

La ventana de compilación de MRTK facilita la compilación & implementar MRTK-Unity proyectos. Con un solo clic, puede compilar un proyecto de Unity y generar Visual Studio solución(. SLN), paquete de aplicación para UWP(. APPX) e instale el paquete de aplicación en el dispositivo. 


## <a name="unity-build-options"></a>Opciones de compilación de Unity
![Ventana De compilación: Opciones de compilación de Unity 1](images/MRTK_BuildWindow1.png)

Estas escenas son de la compilación de Unity Configuración. Puede cambiar el tipo de dispositivo de destino mediante el menú desplegable.

## <a name="appx-build-options"></a>Opciones de compilación de Appx
![Ventana De compilación: Opciones de compilación de Appx 2](images/MRTK_BuildWindow2.png)

En esta pestaña se muestra la configuración de Visual Studio solución. Para habilitar HoloLens 2 entrada de seguimiento de los ojos, active la opción **Capacidad de entrada de mirada.** 

Puede asignar el archivo .glb en el campo 3D App Selector Model (Modelo de aplicación **3D)** para el icono personalizado del iniciador de aplicaciones 3D. Consulte [la guía de diseño del iniciador de aplicaciones 3D](/windows/mixed-reality/distribute/3d-app-launcher-design-guidance) para obtener más información.

De forma predeterminada, **Incremento automático** está activado en Opciones de control de versiones. Las versiones de AppX se incrementarán automáticamente.


## <a name="deploy-options"></a>Opciones de implementación
![Ventana De compilación: Opciones de implementación 3](images/MRTK_BuildWindow3.png)

En esta pestaña, puede conectarse al dispositivo si escribe el nombre de usuario y la contraseña de la Portal de dispositivos. 

En la parte inferior de la página, puede encontrar una lista de los paquetes de aplicación que se han creado. 

