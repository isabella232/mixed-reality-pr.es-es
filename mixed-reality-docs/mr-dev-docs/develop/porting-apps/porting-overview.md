---
title: Introducción a la portabilidad
description: Información general de las distintas opciones de porteo para llevar las aplicaciones existentes a Mixed Reality para HoloLens y VR.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
keywords: porting, unity, middleware, engine, UWP, Win32
ms.openlocfilehash: 9b056bd81a725fea23c1e7f3bfcd9844680086c6
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600504"
---
# <a name="porting-overview"></a>Introducción a la portabilidad

Cuando se trata de porte o actualización de los proyectos existentes para Mixed Reality, el recorrido de porte depende de si la aplicación se ha creado con Unity o Unreal Engine, y tiene como destino HoloLens (1ª generación) o HoloLens 2, o SteamVR. Esta página de información general contiene nuestras recomendaciones actuales para cada plataforma y dispositivo; asegúrese de comprobarlo, ya que estos procesos siempre cambian.

En primer lugar, configure el destino del proyecto en función de nuestras recomendaciones de [Unity](#unity) y [Unreal](#unreal) y, a continuación, siga uno o varios de nuestros escenarios de porte:

- [HoloLens (1ª generación) para HoloLens 2](#hololens-1st-gen-unity-apps-to-hololens-2)
- [Cascos de Windows Mixed Reality](#windows-mixed-reality-headsets)
- [Aplicaciones de SteamVR](#steamvr-applications)
- [Aplicaciones para UWP 2D](#2d-universal-windows-applications)

## <a name="recommended-project-targets"></a>Destinos de proyecto recomendados

Es importante mantener actualizados los proyectos, independientemente de si se porte una aplicación a otro dispositivo de destino. Consulte los recursos basados en motor que se enumeran a continuación para ver nuestras recomendaciones actuales.

### <a name="unity"></a>Unity

Nuestra recomendación actual para el desarrollo de Unity con Mixed Reality es **Unity 2019 LTS** mediante el paquete XR heredado . Si el proyecto usa Mixed Reality Toolkit, compruebe que se encuentra en la versión más reciente, que actualmente es **MRTK-Unity 2.5.**

> [!CAUTION]
> Aunque el SDK de XR está disponible con esta versión de Unity, Azure Spatial Anchors no es compatible actualmente con esta configuración. Esta recomendación se actualizará con una versión futura del paquete Spatial Anchors Azure para Unity.
> 
> * Si no necesita Azure Spatial Anchors, puede configurar el proyecto de Unity para [XR](https://docs.unity3d.com/Manual/configuring-project-for-xr.html) y empezar a trabajar con [MRTK y el SDK de XR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk)
> 
> * Si actualmente usa el SDK de XR en el proyecto y desea usar Azure Spatial Anchors, desinstale el SDK de XR y vuelva a instalar el paquete XR heredado para revertir la configuración del proyecto.

### <a name="unreal"></a>Unreal

Nuestra recomendación actual para el desarrollo de Unreal Mixed Reality **es Unreal Engine 4.26**. Si el proyecto usa Mixed Reality Toolkit UX Tools, asegúrese de que usa la versión más reciente, que actualmente es **UXT 0.10**.

## <a name="porting-scenarios"></a>Escenarios de porte

### <a name="hololens-1st-gen-unity-apps-to-hololens-2"></a>Aplicaciones de Unity de HoloLens (1ª generación) para HoloLens 2

Si tiene una aplicación de Unity de HoloLens (1.ª generación) que le gustaría portabilidad a un HoloLens 2, siga las instrucciones de nuestro artículo de portabilidad de [HoloLens](./porting-hl1-hl2.md).

### <a name="windows-mixed-reality-headsets"></a>Cascos de Windows Mixed Reality

Si ha creado contenido para otros dispositivos, como Oculus Dimensional o HP Reverb G2, deberá redestinar los SDK de REALIDAD virtual específicos del proveedor y las API de asignación de entrada potenciales. Puede encontrar información sobre los escenarios de porte de Unity y Unreal en nuestra guía de [porte de aplicaciones inmersivas](porting-guides.md).

### <a name="steamvr-applications"></a>Aplicaciones de SteamVR

Para conocer las experiencias de SteamVR que quiera actualizar para los cascos Windows Mixed Reality, consulte nuestra guía [de actualización de SteamVR](updating-your-steamvr-application-for-windows-mixed-reality.md).

### <a name="2d-universal-windows-applications"></a>Aplicaciones universales de Windows 2D

Si tienes una aplicación para UWP 2D existente que te gustaría portabilidad a un casco envolvente de Windows Mixed Reality o HoloLens, sigue nuestras instrucciones de portabilidad de aplicaciones [2D](building-2d-apps.md) para UWP Windows Mixed Reality aplicaciones.