---
title: Introducción a MRTK para Unity
description: Descubra todo lo que Mixed Reality Toolkit multiplataforma puede ofrecer a los nuevos desarrolladores de realidad mixta.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK version 2, MRTK, tools, SDK, HoloLens, HoloLens 2, mixed reality headset, windows mixed reality headset, virtual reality headset, cross-platform
ms.openlocfilehash: 6d9e43a3e5ef59226dc6396de46d1295181c07f950ab9255eaf8503f973a2f43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187655"
---
# <a name="introducing-mrtk-for-unity"></a>Introducción a MRTK para Unity

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>¿Qué es Mixed Reality Toolkit (MRTK)?

MRTK es un increíble kit de herramientas de código abierto que ha estado presente desde la primera vez que se lanzó HoloLens. El kit de herramientas no sería de la forma que es actualmente sin el trabajo que aporta nuestra comunidad de desarrolladores. Durante los últimos tres años, hemos tenido en cuenta los comentarios de nuestra comunidad de desarrolladores y hemos creado MRTK v2 para dar respuesta a las preocupaciones más importantes.  

MRTK para Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. La manera más fácil de instalar el kit de herramientas es con la nueva herramienta de características de Mixed Reality. Siga las [instrucciones de instalación y uso](welcome-to-mr-feature-tool.md) y seleccione el paquete **Mixed Reality Toolkit Foundation** en la categoría Mixed Reality Toolkit.

MRTK para Unity proporciona un sistema de entrada multiplataforma, componentes básicos y bloques de creación comunes para interacciones espaciales. La versión 2 de MRTK está diseñada para acelerar el desarrollo de aplicaciones de Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está pensado para reducir las barreras en la creación de aplicaciones de realidad mixta y para contribuir al crecimiento conjunto de la comunidad.

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [Pruebe nuestros tutoriales de MRTK](tutorials/mr-learning-base-01.md)

Eche un vistazo a la [documentación de MRTK](/windows/mixed-reality/mrtk-unity) para obtener más detalles sobre las características.

## <a name="new-with-mrtk-v2"></a>Novedades en MRTK v2

Queremos remarcar nuestro compromiso con estas herramientas de la plataforma.  De hecho, hemos usado MRTK, versión 2, para desarrollar nuestras experiencias de bandeja de entrada, como configuración rápida (OOBE) y nuestra aplicación de sugerencias de realidad mixta. Además, verás nuevas funcionalidades de HoloLens 2 expuestas por primera vez a través de MRTK porque creemos que es la mejor manera de llevar a cabo el desarrollo en nuestra plataforma.

### <a name="modular"></a>Modular

Lo hemos diseñado de una manera modular, por lo que no es necesario incluir cada una de las partes del kit de herramientas en el proyecto.  De hecho, esto supone varias ventajas.  Mantiene el tamaño del proyecto más pequeño y facilita su administración.  Además, dado que se ha creado con objetos que admiten scripts y está basado en una interfaz, también puedes reemplazar los componentes incluidos por los tuyos propios, a fin de agregar compatibilidad con otros servicios, sistemas y plataformas.

### <a name="cross-platform"></a>Multiplataforma

Hablando de otras plataformas, también ofrece compatibilidad multiplataforma.  Aunque esto no significa que todas las plataformas sean compatibles, nos hemos asegurado de que ninguna parte del código del kit de herramientas deje de funcionar al cambiar el destino de compilación a otras plataformas.  La solidez y la extensibilidad del diseño modular establecen las aplicaciones a fin de poder admitir varias plataformas, como ARCore, ARKit y OpenVR.

### <a name="performant"></a>Buen rendimiento

Dado que trabamos con plataformas móviles, lo hemos diseñado pensando en el rendimiento.  Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan en tu contra.

## <a name="see-also"></a>Consulta también

* [Instalación de las herramientas](../install-the-tools.md)
* [Herramienta de características de Mixed Reality](welcome-to-mr-feature-tool.md)
* [Desarrollo con MRTK para Unity](unity-development-overview.md)
* [Página principal de documentación de MRTK](/windows/mixed-reality/mrtk-unity/)
* [Migración de HoloToolkit/MRTK a MRTK, versión 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
