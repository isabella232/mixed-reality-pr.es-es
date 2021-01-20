---
title: Controladores de HP reverberación G2 en la realidad
description: Aprenda a usar los nuevos controladores de HP reverberación G2 en OpenXR y SteamVR para aplicaciones de realidad mixtas no reales.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, nonreal Engine 4, UE4, reverberation, reverberación G2, HP reverberación G2, realidad mixta, desarrollo, controladores de movimiento, entrada de usuario, características, nuevo proyecto, emulador, documentación, guías, características, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 006c70208ec0eaa45447caecf39f799c4be1bfeb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582683"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controladores de HP reverberación G2 en la realidad 

## <a name="getting-started"></a>Introducción

> [!IMPORTANT]
> Se necesita el motor 4,26 y OpenXR o SteamVR inreal para tener acceso al complemento de controlador de movimiento de HP. tendrá que trabajar con los controladores de la reverberación de HP G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Portabilidad de una aplicación existente de OpenXR 

Si no existe ningún enlace de controlador en el juego para el controlador HP Mixed Reality, el tiempo de ejecución de OpenXR intentará reasignar los enlaces existentes al controlador activo.  En este caso, el juego tiene enlaces de toque Oculus y ningún enlace de controlador de realidad de HP Mixed.

![Volver a asignar los enlaces existentes cuando no existe ningún enlace de controlador](images/reverb-g2-img-04.png)

Los eventos se seguirán activando, pero si el juego necesita hacer uso de enlaces específicos del controlador, como el botón derecho del menú, se debe usar el perfil de interacción de la realidad de HP Mixed.  Se pueden especificar varios enlaces de controlador por acción para admitir mejor los distintos dispositivos.
   
![Usar varios enlaces de controlador](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Agregar asignaciones de acción de entrada 

Definir una nueva acción y asignarla a una de las pulsaciones de teclas de la sección controlador HP Mixed Reality.

![Definir nuevas acciones y asignaciones](images/reverb-g2-img-02.png)

El controlador de HP reverberación G2 también tiene un control analógico, que se puede usar en las asignaciones de eje con el enlace "apriete de eje".  Hay un enlace de ajuste independiente que se debe usar para las asignaciones de acciones cuando el botón de control se presiona por completo. 

![Usar los enlaces de eje de apriete](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Agregar eventos de entrada

Haga clic con el botón derecho en un plano y busque los nuevos nombres de acción del sistema de entrada para agregar eventos para estas acciones.  Aquí el Blueprint responde a los eventos con una cadena de impresión que genera el estado actual del eje y el botón.

![Blueprint responder a eventos y salida del botón actual y el estado del eje](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Usar entrada 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Consulte también
* [Entrada SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Uso de SteamVR con Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Cámara del reproductor inreal](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)