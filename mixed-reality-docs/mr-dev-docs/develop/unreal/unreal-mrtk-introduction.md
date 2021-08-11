---
title: Introducción de MRTK para Unreal
description: Descubra todo lo que Mixed Reality Toolkit for Unreal puede ofrecer a los nuevos desarrolladores de realidad mixta.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, tools, SDK, HoloLens, HoloLens 2, mixed reality headset, windows mixed reality headset, virtual reality headset, cross-platform
ms.openlocfilehash: 06eacac245c80f16ab48dbda4b5aca740ffdfd66a0266beafac5e46b39a9d109
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221835"
---
# <a name="introducing-mrtk-for-unreal"></a>Introducción de MRTK para Unreal

![Imagen del banner de MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>¿Qué es Mixed Reality Toolkit (MRTK)?

MRTK es un increíble kit de herramientas de código abierto que ha estado presente desde la primera vez que se lanzó HoloLens. El kit de herramientas no sería de la forma que es actualmente sin el trabajo que aporta nuestra comunidad de desarrolladores. 

Mixed Reality Toolkit para Unreal (MRTK-Unreal) es un conjunto de componentes, en forma de complementos, muestras y documentación, diseñado para facilitar el desarrollo de aplicaciones de realidad mixta con Unreal Engine. Actualmente, el kit de herramientas consta de:
* [UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), que proporciona código, planos técnicos y ejemplos para implementar características de experiencia de usuario para aplicaciones de Hololens 2.
* [Graphic Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), que ayuda a mejorar la fidelidad visual de las aplicaciones de realidad mixta sin salirse de los presupuestos de rendimiento.

Eche un vistazo a la [documentación de MRTK en GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) y empiece a trabajar con las guías de instalación de [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) o [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md).

### <a name="modular"></a>Modular

Hemos compilado MRTK Unreal de una manera modular, por lo que no es necesario incluir cada una de las partes del kit de herramientas en el proyecto. Puede elegir los complementos que necesite y agregarlos o quitarlos cuando lo considere oportuno. Este enfoque reduce el tamaño del proyecto y facilita su administración.  

### <a name="performant"></a>Buen rendimiento

Dado que trabamos con plataformas móviles, hemos diseñado MRTK Unreal pensando en el rendimiento. Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan en su contra.

## <a name="project-setup"></a>Configuración del proyecto

> [!div class="nextstepaction"]
> [Descargar Unreal Engine y MRTK](unreal-project-setup.md)

## <a name="see-also"></a>Consulta también

* [Instalación de las herramientas](../install-the-tools.md)
* [Desarrollo con MRTK para Unreal](unreal-development-overview.md)
* [UX Tools: guía de instalación (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [UX Tools: página principal de documentación (GitHub)](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [Graphics Tools: guía de instalación (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [Graphics Tools: página principal de documentación (GitHub)](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)