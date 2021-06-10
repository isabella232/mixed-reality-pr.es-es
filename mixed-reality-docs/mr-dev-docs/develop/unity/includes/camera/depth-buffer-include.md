---
ms.openlocfilehash: 481a063cac3cb4d7e5ef7521ad19af43cb68e2cf
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110631161"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El cuadro de diálogo de configuración de [MRTK](/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) intentará establecer la configuración del búfer de profundidad para el SDK de XR y WSA heredado, pero es bueno comprobar esas pestañas y comprobar la configuración en Unity.

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **Editar configuración** del proyecto Administración del complemento  >    >  **XR** y asegúrese de que el elemento de menú está expandido.
2. Haga clic en el elemento de menú correspondiente al entorno de ejecución de XR que ha elegido, ya sea Windows Mixed Reality o OpenXR. Además, asegúrese de que está seleccionada la plataforma de compilación correcta, ya que las pestañas para Windows independiente Plataforma universal de Windows están disponibles.
3. Para habilitar y configurar:
    1. En OpenXR, seleccione un formato de profundidad o "Ninguno" en la lista **desplegable Modo de envío de profundidad.**
    2. Para Windows Mixed Reality, active o desactive la casilla **Búfer de profundidad** compartido . A continuación, seleccione un formato en la lista **desplegable Depth Buffer Format (Formato de búfer de profundidad).**

![Configuración de profundidad del complemento XR de Windows ](../../images/xrsdk-winxr-depth.png)
 ![ Configuración de profundidad de OpenXR](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si usa el formato de profundidad de 16 bits, los efectos necesarios del búfer de galería de símbolos (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) no crea un búfer de galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, se suele crear un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html) bits si procede en la plataforma de gráficos de punto de conexión.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **Edit** Project Settings Player (Editar configuración  >  **del**  >    >  **proyecto) Plataforma universal de Windows pestaña**  >  **XR Settings (Configuración de XR).**
2. Expanda el **Windows Mixed Reality SDK.**
3. Active o desactive la casilla **Habilitar uso compartido de búfer de** profundidad. Habilitar el uso compartido de búfer de profundidad está activado de forma predeterminada en los proyectos nuevos, pero es posible que se haya desactivado de forma predeterminada en los proyectos anteriores.

![Configuración de profundidad XR heredada](../../images/wmr-depth.png)

Un búfer de profundidad puede mejorar la calidad visual siempre que Windows pueda asignar con precisión los valores de profundidad normalizados por píxel del búfer de profundidad a distancias en metros, mediante los planos cercanos y lejanos que haya establecido en Unity en la cámara principal. Si la representación pasa los valores de profundidad de maneras típicas, debería estar bien aquí, aunque los pases de representación translúcidos que escriben en el búfer de profundidad mientras se muestran a los píxeles de color existentes pueden confundir la reproducción.  Si sabe que los pases de representación dejarán muchos de los píxeles de profundidad finales con valores de profundidad inexactos, es probable que obtenga una mejor calidad visual desactivando "Habilitar el uso compartido del búfer de profundidad".

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si usa el formato de profundidad de 16 bits, los efectos necesarios del búfer de galería de símbolos (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) no crea un búfer de galería de símbolos en esta configuración. Al seleccionar el formato de profundidad de *24* bits por el contrario, se suele crear un búfer de galería de símbolos de [8](https://docs.unity3d.com/Manual/SL-Stencil.html) bits si procede en la plataforma de gráficos de punto de conexión.