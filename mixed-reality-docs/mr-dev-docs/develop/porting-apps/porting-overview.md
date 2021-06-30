---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de porte para llevar las aplicaciones existentes a Mixed Reality para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 167559d69cc4e65f971a8970b56e41e6e3ca8b22
ms.sourcegitcommit: 12ea3fb2df4664c5efd07dcbb9040c2ff173afb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2021
ms.locfileid: "113042276"
---
# <a name="porting-overview"></a>Introducción a la portabilidad

Cuando se trata de portear o actualizar los proyectos existentes para Mixed Reality, el recorrido de porte depende de si la aplicación se ha creado con Unity o Unreal Engine, y tiene como destino HoloLens (1.ª generación) o HoloLens 2, o SteamVR. Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo; asegúrese de volver a comprobarlo, ya que estos procesos siempre cambian.

En primer lugar, configure el destino del proyecto en función de nuestras recomendaciones de [Unity](#unity) y [Unreal](#unreal) y, a continuación, siga uno o varios de nuestros escenarios de porte:

- [HoloLens (1.ª generación) para HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Cascos envolventes de VR](#immersive-vr-headsets)
- [Aplicaciones para UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de proyecto recomendados

Es importante mantener los proyectos actualizados, tanto si se porte una aplicación a otro dispositivo de destino. Consulte los recursos basados en motor que se enumeran a continuación para ver nuestras recomendaciones actuales.

### <a name="unity"></a>Unity

Consulte la [página Elegir una versión de Unity](../unity/choosing-unity-version.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unity y MRTK.

### <a name="unreal"></a>Unreal

Consulte la página Configuración del proyecto [de Unreal](../unreal/unreal-project-setup.md) para obtener instrucciones actualizadas sobre las versiones recomendadas de Unreal y MRTK.

## <a name="porting-scenarios"></a>Escenarios de porte

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Aplicaciones de Unity de HoloLens (1.ª generación) para HoloLens 2

Si tiene una aplicación de Unity holoLens (1.ª generación) existente que le gustaría portabilidad a un HoloLens 2, siga las instrucciones de nuestro artículo de portabilidad de [HoloLens](./porting-hl1-hl2.md).

### <a name="immersive-vr-headsets"></a>Cascos envolventes de VR

Si ha creado contenido para otros dispositivos vr, deberá redestinar los SDK de REALIDAD virtual específicos del proveedor y las API de asignación de entrada potenciales. Puede encontrar información sobre los escenarios de porte de Unity y Unreal en nuestra guía de [porte de aplicaciones inmersivas.](porting-guides.md)

Para conocer las experiencias de SteamVR que desea actualizar para Windows Mixed Reality cascos, consulte nuestra guía [de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>Aplicaciones universales de Windows 2D

Si tienes una aplicación 2D para UWP existente que te gustaría portabilidad a un casco envolvente de Windows Mixed Reality o HoloLens, sigue nuestras instrucciones de portabilidad de aplicaciones [2D para UWP Windows Mixed Reality](building-2d-apps.md) usuario.