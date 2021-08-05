---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de porte para llevar las aplicaciones existentes a Mixed Reality para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 519dae088e689e0a6e617bf5e2b34f81cc2e265256c4844df7dd34e99172d536
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189425"
---
# <a name="porting-overview"></a>Introducción a la portabilidad

Cuando se trata de portear o actualizar los proyectos existentes para Mixed Reality, el recorrido de porte depende de si la aplicación se ha creado con Unity o Unreal Engine y tiene como destino HoloLens (1.ª generación) o HoloLens 2, o SteamVR. Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo; asegúrese de volver a comprobarlo, ya que estos procesos siempre cambian.

En primer lugar, configure el destino del proyecto en función de nuestras recomendaciones de [Unity](#unity) y [Unreal](#unreal) y, a continuación, siga uno o varios de nuestros escenarios de porte:

- [HoloLens (1.ª generación) a HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Cascos envolventes de VR](#immersive-vr-headsets)
- [Aplicaciones para UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de proyecto recomendados

Es importante mantener los proyectos actualizados, tanto si se porte una aplicación a otro dispositivo de destino. Consulte los recursos basados en motor que se enumeran a continuación para ver nuestras recomendaciones actuales.

### <a name="unity"></a>Unity

Consulte la [página Elegir una versión de Unity](../unity/choosing-unity-version.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unity y MRTK.

### <a name="unreal"></a>Unreal

Consulte la [página Configuración del proyecto de Unreal](../unreal/unreal-project-setup.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unreal y MRTK.

## <a name="porting-scenarios"></a>Escenarios de porte

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>HoloLens aplicaciones de Unity (1.ª generación) para HoloLens 2

Si tiene una aplicación de Unity HoloLens (1.ª generación) que le gustaría portabilidad a un HoloLens 2, siga las instrucciones de nuestro artículo de [HoloLens portabilidad](./porting-hl1-hl2.md).

### <a name="immersive-vr-headsets"></a>Cascos envolventes de VR

Si ha creado contenido para otros dispositivos vr, deberá redestinar los SDK de REALIDAD virtual específicos del proveedor y las API de asignación de entrada potenciales. Puede encontrar información sobre los escenarios de porte de Unity y Unreal en nuestra guía de [porte de aplicaciones inmersivas.](porting-guides.md)

Para conocer las experiencias de SteamVR que desea actualizar para los cascos Windows Mixed Reality, consulte nuestra guía [de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>Aplicaciones de Windows universales 2D

Si tienes una aplicación 2D para UWP existente que te gustaría portabilidad a un casco envolvente de Windows Mixed Reality o HoloLens, sigue nuestras instrucciones de portabilidad de aplicaciones [2D para UWP Windows Mixed Reality](building-2d-apps.md) usuario.