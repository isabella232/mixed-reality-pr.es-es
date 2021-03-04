---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de portabilidad para llevar las aplicaciones existentes a la realidad mixta de HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: portabilidad, Unity, middleware, motor, UWP, Win32
ms.openlocfilehash: 693891d67ae26098f0810a539059da8d34f4731c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759116"
---
# <a name="porting-overview"></a>Introducción a la portabilidad

En lo que respecta a la migración o la actualización de los proyectos existentes para la realidad mixta, el recorrido de portabilidad depende de si la aplicación está compilada con Unity o un motor no real, y tiene como destino HoloLens (1º gen) o HoloLens 2 o SteamVR. Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo. Asegúrese de volver a comprobar que estos procesos siempre cambian.

En primer lugar, configure el destino del proyecto en función de las recomendaciones de [Unity](#unity) y no [reales](#unreal) y luego siga uno o varios de nuestros escenarios de migración:

- [HoloLens (1ª generación) a HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Cascos de Windows Mixed Reality](#windows-mixed-reality-headsets)
- [Aplicaciones SteamVR](#steamvr-applications)
- [aplicaciones para UWP en 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Objetivos de proyecto recomendados

Es importante mantener los proyectos actualizados, tanto si se traslada una aplicación a otro dispositivo de destino. Consulte los recursos basados en el motor que se enumeran a continuación para ver nuestras recomendaciones actuales.

### <a name="unity"></a>Unity

Nuestra recomendación actual para el desarrollo de Unity con realidad mixta es **Unity 2019 lts mediante el paquete de XR heredado**. Si el proyecto usa el kit de herramientas de realidad mixta, compruebe que se encuentra en la versión más reciente, que actualmente es **MRTK-Unity 2,5**.

> [!CAUTION]
> Aunque el SDK de XR está disponible con esta versión de Unity, los delimitadores espaciales de Azure no son compatibles actualmente con esta configuración. Esta recomendación se actualizará con una versión futura del paquete de anclajes espaciales de Azure para Unity. 
> 
> * Si no necesita anclajes espaciales de Azure, puede [configurar el proyecto de Unity para XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) y comenzar a usar el [SDK de MRTK y XR](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/configuration/getting-started-with-mrtk-and-xrsdk.md).
> 
> * Si actualmente está usando el SDK de XR en el proyecto y quiere usar delimitadores espaciales de Azure, desinstale el SDK de XR y reinstale el paquete de XR heredado para revertir la configuración del proyecto.


### <a name="unreal"></a>Unreal 

Nuestra recomendación actual para el desarrollo no real con realidad mixta es el **motor inreal 4,26**. Si el proyecto usa las herramientas de la experiencia del kit de herramientas de realidad mixta, asegúrese de que está usando la versión más reciente, que actualmente es **UXT 0,10**.

## <a name="porting-scenarios"></a>Escenarios de migración

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Aplicaciones de Unity de HoloLens (primera generación) a HoloLens 2

Si ya tiene una aplicación de Unity de HoloLens (primera generación) que le gustaría migrar a un HoloLens 2, siga las instrucciones que aparecen en nuestro artículo sobre la [migración de hololens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Cascos de Windows Mixed Reality

Si ha creado contenido para otros dispositivos, como Oculus Rift o HP reverberación G2, deberá redestinar los SDK de VR específicos del proveedor y las API de asignación de entrada posibles. Puede encontrar información sobre los escenarios de migración de Unity y no real en nuestra [Guía de migración de aplicaciones envolventes](porting-guides.md).

### <a name="steamvr-applications"></a>Aplicaciones SteamVR

En el caso de las experiencias de SteamVR que quiera actualizar para los auriculares con Windows Mixed Reality, consulte nuestra [Guía de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>aplicaciones Windows universales en 2D

Si tiene una aplicación de UWP en 2D existente que le gustaría trasladar a un auricular o a HoloLens de realidad mixta de Windows, siga las instrucciones [de migración de aplicaciones para UWP en 2D para Windows](building-2d-apps.md) .