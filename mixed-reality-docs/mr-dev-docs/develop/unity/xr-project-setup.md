---
title: Establecimiento de la configuración de XR
description: Manténgase al día de las recomendaciones de configuración más recientes de Unity XR para HoloLens desarrollo de aplicaciones.
author: hferrone
ms.author: v-hferrone
ms.date: 04/22/2021
ms.topic: article
keywords: mixedrealitytoolkit, mixedrealitytoolkit-unity, mixed reality headset, windows mixed reality headset, virtual reality headset, unity
ms.openlocfilehash: 72f17ec9fc74143a2ae6cc51e1ffed0c73d13ef04ef5c4004537be70d1daaaca
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202758"
---
# <a name="setting-up-your-xr-configuration"></a>Establecimiento de la configuración de XR

Una vez que haya elegido una versión de [Unity,](choosing-unity-version.md)el siguiente paso es seleccionar la configuración de XR que usará para compilar la aplicación de realidad mixta:

## <a name="choosing-an-xr-configuration"></a>Elección de una configuración de XR

Al iniciar un nuevo proyecto de Unity, tiene varias configuraciones XR entre las que puede seleccionar: el complemento **Mixed Reality OpenXR,** el complemento **XR** de Windows y el **XR integrado heredado.**

[!INCLUDE[](includes/xr/intro.md)]

## <a name="setting-up-your-project-with-mrtk"></a>Configuración del proyecto con MRTK

La manera más fácil de configurar el proyecto de Unity para la realidad mixta es con Mixed Reality Toolkit (MRTK).  MRTK para Unity es un kit de desarrollo multiplataforma de código abierto diseñado para facilitar la creación de sorprendentes aplicaciones de realidad mixta.

![MRTK](../../design/images/MRTK_UX_Hero.png)

MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales.  Con la versión 2 de MRTK, puede acelerar el desarrollo de aplicaciones para Microsoft HoloLens, Windows Mixed Reality cascos envolventes (VR) y muchos otros dispositivos VR/AR. El proyecto está destinado a reducir las barreras de entrada, lo que permite a todos crear aplicaciones de realidad mixta y contribuir de nuevo a la comunidad a medida que crecemos todos.

[!INCLUDE[](includes/xr/mrtk-next-step.md)]

Para obtener más información sobre la Mixed Reality Toolkit, consulte la [documentación de MRTK](/windows/mixed-reality/mrtk-unity).

## <a name="manual-setup-without-mrtk"></a>Configuración manual sin MRTK

Aunque Microsoft y la comunidad han creado herramientas de código abierto como [Mixed Reality Toolkit (MRTK)](/windows/mixed-reality/mrtk-unity) que configurarán automáticamente el entorno para la realidad mixta, es posible que algunos desarrolladores quieran crear sus experiencias desde el primer momento.

[!INCLUDE[](includes/xr/manual-setup.md)]