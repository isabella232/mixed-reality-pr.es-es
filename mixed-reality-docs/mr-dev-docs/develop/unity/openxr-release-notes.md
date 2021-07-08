---
title: Notas de la versión del complemento Mixed Reality OpenXR
description: Manténgase al día con las notas de la versión y las actualizaciones más recientes del complemento Mixed Reality OpenXR.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394633"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a>Notas de la versión del complemento Mixed Reality OpenXR

## <a name="100---current-release"></a>1.0.0: Versión actual

* Se ha corregido un error por el que XRAnchorSubsystem siempre se iniciaba al iniciar la aplicación, independientemente de la presencia de ARAnchorManager.
* Se ha corregido un error por el que el modo de reproyección no funcionaba correctamente.

## <a name="100-preview2---2021-06-14"></a>1.0.0-preview.2: 14/06/2021

* Depende del complemento OpenXR 1.2.2 de Unity.
* Se han cambiado las características de Holographic Remoting (Comunicación remota holográfica) en grupos de características individuales.
* Se ha corregido un error por el que "Apply HoloLens 2 project settings" (Aplicar configuración del proyecto de HoloLens 2) cambiaba el espacio de color del proyecto. Esto ya no es necesario después del complemento OpenXR 1.2.0 de Unity.
* Se ha corregido un error por el que un dispositivo de entrada se conectaba sin desconectarse después de que la aplicación se suspendiera y reanudara.
* Se ha agregado compatibilidad para detectar el complemento y los estados de seguimiento actuales a través de ARSession.
* Se ha corregido un error por el que el objeto prefababricado "AR Default Plane" (plano predeterminado de AR) de ARFoundation no era visible.

## <a name="100-preview1---2021-06-02"></a>1.0.0-preview.1: 02/06/2021

* Admite las extensiones MSFT de descripción de escenas de OpenXR en lugar de las extensiones de la versión preliminar.
* La detección de plano en HoloLens 2 ya no requiere versiones preliminares de los entornos en tiempo de ejecución de Mixed Reality OpenXR.

## <a name="095---2021-05-21"></a>0.9.5: 21/05/2021

* Depende del complemento OpenXR 1.2.0 de Unity.
* Se ha adaptado a la nueva interfaz de usuario de características (en el complemento de OpenXR 1.2.0) para la configuración.
* Se ha corregido un error por el que el proveedor de cámaras localizables no anulaba el registro correctamente.
* Se han limpiado algunos usos adicionales de [Preserve].
* Se ha actualizado el nombre "HP Reverb G2 Controller (OpenXR)" en la interfaz de usuario del sistema de entrada.

## <a name="094---2021-05-20"></a>0.9.4: 20/05/2021

* Depende del complemento OpenXR 1.2.0 de Unity.
* Se ha agregado una nueva API de C# para obtener el modelo glTF del controlador de movimiento.
* Se ha agregado una nueva API de C# para habilitar las configuraciones de vista y establecer la configuración de reproyección.
* Se ha agregado una nueva API de C# para establecer configuraciones adicionales para calcular mallas con XRMeshSubsystem.
* Se ha agregado una nueva API de C# para configurar y suscribirse a eventos de reconocimiento de gestos.
* Se ha agregado el cuadro de diálogo de configuración Windows->XR->Editor Remoting (Comunicación remota del editor).
* Se ha agregado compatibilidad con ARM para aplicaciones para UWP en HoloLens.

## <a name="093---2021-04-29"></a>0.9.3: 29/04/2021

* Se ha corregido un error por el que la conexión de conexión remota holográfica no era confiable.
* Se ha corregido un error por el que el rendimiento de la representación de VR era poco óptimo después de actualizar al complemento OpenXR 1.1.1 de Unity.

## <a name="092---2021-04-21"></a>0.9.2: 21/04/2021

* La detección de plano en HoloLens 2 en la versión 0.9.1 del complemento funcionará con la versión 105 del entorno en tiempo de ejecución de Mixed Reality OpenXR en versión preliminar.
* La detección de plano en HoloLens 2 en la versión 0.9.2 del complemento funcionará con la versión 106 del entorno en tiempo de ejecución de Mixed Reality OpenXR en versión preliminar.
* Se han quitado algunas devoluciones de llamada no utilizadas de InputProvider para evitar que llamadas como XRInputSubsystem.* GetTrackingOriginMode (que nuestro sistema de entrada no administra) devuelvan resultados correctos con valores engañosos.
* Se ha dividido la versión en desuso de XRAnchorStore en su propio archivo para evitar la advertencia de la consola de Unity.

## <a name="091---2021-04-20"></a>0.9.1: 20/04/2021

* Depende del complemento OpenXR 1.1.1 de Unity.
* Se ha agregado compatibilidad con la aplicación Holographic Remoting (Comunicación remota holográfica) para la plataforma UWP.
* Se ha corregido UnityException en la que XRAnchorStore intentaba obtener una instancia de configuración fuera del subproceso principal.

## <a name="090---2021-03-29"></a>0.9.0: 29/03/2021

* Se ha agregado compatibilidad con la asignación espacial a través de XRMeshSubsystem y ARMeshManager.
* Se ha agregado una nueva API de C# para que los identificadores de OpenXR admitan otras extensiones de OpenXR de consumo de paquetes de Unity.
* Se ha agregado una nueva API de C# para la interoperabilidad con las API Windows.Perception para admitir otros paquetes de Unity que consumen las API Perception de WinRT.
* Se han quitado perfiles de interacción de las características necesarias en el conjunto de características de Windows Mixed Reality, por lo que los desarrolladores pueden elegir los controladores de movimiento con los que han probado.
* Se ha agregado el validador de características de comunicación remota del editor holográfico para ayudar a los usuarios a configurar correctamente la comunicación remota del editor.
* Se ha corregido un error por el que el editor de Unity se bloqueaba al salir del modo de comunicación remota del editor holográfico después de un error de conexión.
* Se ha corregido un error por el que las texturas no premultiplicadas en el canal alfa provocaban un rendimiento poco óptimo en HoloLens 2.
* Se ha corregido un error por el que el seguimiento de manos no se encontraba correctamente cuando el origen de la escena estaba a nivel del suelo.
* Se ha corregido un error por el que el seguimiento de la malla de mano desaparecía después de salir y cargar una nueva escena.
* Se ha corregido un error por el que el proveedor de cámaras localizables no se limpiaba correctamente.
* Se ha revisado el espacio de nombres de la API XRAnchorStore en Microsoft.MixedReality.OpenXR.