---
title: Configuración de la configuración de XR
description: Manténgase al día con las recomendaciones de configuración XR de Unity más recientes para el desarrollo de aplicaciones holoLens.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, unity
ms.openlocfilehash: df7c5039c6cdcfa1e39dc96f0829611dd5209772
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394569"
---
# <a name="setting-up-your-xr-configuration"></a>Configuración de la configuración de XR

Al iniciar un nuevo proyecto de Unity, tiene tres opciones diferentes para controlar sus necesidades de XR: 
* Complemento OpenXR
* Complemento XR de Windows
* Complemento XR heredado

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configuración del proyecto con MRTK

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

> [!div class="nextstepaction"]
> [Pruebe nuestros tutoriales de MRTK](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=winxr)

Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

### <a name="using-mrtk-with-openxr-support"></a>Uso de MRTK con compatibilidad con OpenXR

MRTK-Unity versión 2.7 proporciona mejores compatibilidades para el complemento Mixed Reality OpenXR.

Abra de [nuevo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) para instalar Mixed Reality Toolkit, si aún no lo ha hecho. La compatibilidad con OpenXR está en el **paquete de Foundation.**

Consulte la documentación de MRTK para obtener información más [detallada sobre la migración a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Al actualizar desde una versión anterior de MRTK anterior a **la 2.5.3,** asegúrese de que la línea siguiente está en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) que configurarán automáticamente el entorno WMR, muchos desarrolladores desean crear sus experiencias desde cero.

[!INCLUDE[](includes/xr/manual-setup.md)]
