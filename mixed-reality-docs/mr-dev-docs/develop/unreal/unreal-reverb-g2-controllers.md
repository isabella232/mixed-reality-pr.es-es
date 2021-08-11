---
title: Controladores de HP Reverb G2 en Unreal
description: Aprenda a usar los nuevos controladores HP Reverb G2 en openXR y SteamVR para aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, Reverb, Reverb G2, HP Reverb G2, mixed reality, development, motion controllers, user input, features, new project, emulator, documentation, guides, features, holograms, game development, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: b287a5c7de1ea086b76228d9109cc07a4e1569f5f926cb42dc3e37cc2a3bb916
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204213"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Controladores de HP Reverb G2 en Unreal 

## <a name="getting-started"></a>Introducción

> [!IMPORTANT]
> Se requiere Unreal Engine 4.26 y OpenXR o SteamVR para acceder al complemento hp Motion Controller que necesitará para trabajar con los controladores HP Reverb G2.

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>Porte de una aplicación OpenXR existente 

Si no existen enlaces de controlador en el juego para hp Mixed Reality Controller, el tiempo de ejecución de OpenXR intentará reasignar los enlaces existentes al controlador activo.  En este caso, el juego tiene enlaces táctiles de Oculus y ningún enlace hp Mixed Reality controller.

![Volver a la aplicación de enlaces existentes cuando no existe ningún enlace de controlador](images/reverb-g2-img-04.png)

Los eventos seguirán activo, pero si el juego necesita hacer uso de enlaces específicos del controlador, como el botón de menú derecho, se debe usar el perfil de interacción de hp Mixed Reality.  Se pueden especificar varios enlaces de controlador por acción para admitir mejor distintos dispositivos.
   
![Uso de varios enlaces de controlador](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>Adición de asignaciones de acciones de entrada 

Defina una nueva acción y asigne a una de las pulsaciones de tecla de la sección Hp Mixed Reality Controller.

![Definición de nuevas acciones y asignaciones](images/reverb-g2-img-02.png)

El controlador HP Reverb G2 también tiene un control análogo, que se puede usar en las asignaciones de ejes con el enlace "Eje de tracción".  Hay un enlace Desasoción independiente, que se debe usar para las asignaciones de acciones cuando el botón de control está totalmente presionado. 

![Usar los enlaces del eje Desasoyir](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>Agregar eventos de entrada

Haga clic con el botón derecho en un plano técnico y busque los nuevos nombres de acción del sistema de entrada para agregar eventos para estas acciones.  Aquí el plano técnico responde a los eventos con una cadena de impresión que genera el estado actual del botón y del eje.

![Plano técnico que responde a eventos y genera el estado actual del botón y del eje](images/reverb-g2-img-06.png)

### <a name="using-input"></a>Uso de la entrada 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>Consulte también
* [Entrada de SteamVR](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Uso de SteamVR con Windows Mixed Reality](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Cámara de Unreal Player](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)