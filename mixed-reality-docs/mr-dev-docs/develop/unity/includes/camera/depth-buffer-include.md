---
ms.openlocfilehash: 924190e10de100fc84795344a6cf676f318d04cec26793af96d03a3cb7cb5f78
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212330"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El cuadro de diálogo de configuración de [MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) intentará establecer la configuración del búfer de profundidad para el SDK de XR y WSA heredado, pero es bueno comprobar esas pestañas y comprobar la configuración en Unity.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación unity proporcionará un búfer de profundidad para Windows:

1. Vaya a **Editar Project Configuración** administración de complementos XR y asegúrese de que el elemento de  >    >   menú está expandido.
2. Haga clic en el elemento de menú correspondiente al entorno de ejecución de XR que ha elegido, ya sea Windows Mixed Reality o OpenXR. Además, asegúrese de que está seleccionada la plataforma de compilación correcta, ya que hay disponibles pestañas para Windows independiente y universal Windows platform.
3. Para habilitar y configurar:
    1. En OpenXR, seleccione un formato de profundidad o "Ninguno" en la lista **desplegable Modo de envío de profundidad.**
    2. Para Windows Mixed Reality, active o desactive la casilla **Búfer de profundidad** compartido . A continuación, seleccione un formato en la lista **desplegable Depth Buffer Format (Formato de búfer de profundidad).**

![Windows Configuración de profundidad del complemento XR ](../../images/xrsdk-winxr-depth.png)
 ![ Configuración de profundidad de OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si usa el formato de profundidad de 16 bits, los efectos necesarios del búfer de galería de símbolos (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) no crea un búfer de galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, se suele crear un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html) bits si procede en la plataforma de gráficos de punto de conexión.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación unity proporcionará un búfer de profundidad para Windows:

1. Vaya a **la**  >  **pestaña Project Configuración**  >  **Player** Universal Windows  >  **Platform**  >  **XR Configuración**.
2. Expanda el **Windows Mixed Reality SDK.**
3. Active o desactive la casilla **Habilitar uso compartido de búfer de** profundidad. Habilitar el uso compartido de búfer de profundidad está activado de forma predeterminada en los proyectos nuevos, pero es posible que se haya desactivado de forma predeterminada en los proyectos anteriores.

![Configuración de profundidad XR heredada](../../images/wmr-depth.png)

Un búfer de profundidad puede mejorar la calidad visual siempre que Windows pueda asignar con precisión los valores normalizados de profundidad por píxel del búfer de profundidad a distancias en metros, mediante los planos cercanos y lejanos que haya establecido en Unity en la cámara principal. Si la representación pasa los valores de profundidad de maneras típicas, debería estar bien aquí, aunque los pases de representación translúcidos que escriben en el búfer de profundidad mientras se muestran a los píxeles de color existentes pueden confundir la reproducción.  Si sabe que los pases de representación dejarán muchos de los píxeles de profundidad finales con valores de profundidad inexactos, es probable que obtenga una mejor calidad visual desactivando "Habilitar el uso compartido del búfer de profundidad".

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si usa el formato de profundidad de 16 bits, los efectos necesarios del búfer de galería de símbolos (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) no crea un búfer de galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, se suele crear un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html) bits si procede en la plataforma de gráficos de punto de conexión.