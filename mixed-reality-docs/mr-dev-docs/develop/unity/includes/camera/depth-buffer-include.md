---
ms.openlocfilehash: 3306a9925c55c24c4d72ecb58d7c744dd64b283e
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636318"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

El [cuadro de diálogo de configuración de MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mrtk-configuration-dialog) intentará establecer una configuración de búfer de profundidad para el SDK de XR y el heredado WSA, pero es conveniente comprobar esas pestañas y comprobar la configuración en Unity.

# <a name="xr-sdk"></a>[SDK DE XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación de Unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **Editar**  >  **configuración de proyecto**  >  **XR administración de complementos** y asegúrese de que el elemento de menú está expandido.
2. Haga clic en el elemento de menú correspondiente al tiempo de ejecución de XR que ha elegido, ya sea Windows Mixed Reality o OpenXR. Además, asegúrese de que esté seleccionada la plataforma de compilación correcta, ya que las pestañas de Windows independiente y Plataforma universal de Windows están disponibles.
3. Para habilitar y configurar:
    1. En el caso de OpenXR, seleccione un formato de profundidad o "ninguno" en la lista desplegable **modo de envío de profundidad** .
    2. En Windows Mixed Reality, Active o desactive la casilla **búfer de profundidad compartido** . A continuación, seleccione un formato en la lista desplegable **formato de búfer de profundidad** .

![Configuración de profundidad del complemento de XR de Windows ](../../images/xrsdk-winxr-depth.png)
 ![ OpenXR configuración de profundidad](../../images/xrsdk-openxr-depth.png)

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si se usa el formato de profundidad de 16 bits, los efectos requeridos del búfer de estarcido (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity no crea un búfer de estarcido](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) en esta configuración. Si se selecciona el *formato de profundidad de 24 bits* a la inversa, se creará normalmente un [búfer de estarcido de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) si es aplicable en la plataforma de gráficos de punto de conexión.

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

Para establecer si la aplicación de Unity proporcionará un búfer de profundidad a Windows:

1. Vaya a **Editar**  >  **configuración de proyecto**  >  **reproductor**  >  **plataforma universal de Windows pestaña**  >  **XR configuración**.
2. Expanda el elemento **SDK de Windows Mixed Reality** .
3. Active o desactive la casilla **Habilitar uso compartido del búfer de profundidad** . Habilitar el uso compartido de búfer de profundidad está activado de forma predeterminada en los proyectos nuevos, pero puede que se haya desactivado de forma predeterminada en los proyectos anteriores.

![Configuración de profundidad de XR heredada](../../images/wmr-depth.png)

Un búfer de profundidad puede mejorar la calidad visual, siempre y cuando Windows pueda asignar con precisión los valores normalizados de profundidad por píxel en el búfer de profundidad a distancias en metros, con los planos cercanos y lejanos que haya establecido en Unity en la cámara principal. Si las pasadas de representación controlan los valores de profundidad de maneras típicas, generalmente debería estar bien aquí, aunque las pasadas de representación translúcidas que escriben en el búfer de profundidad mientras se muestran a los píxeles de color existentes pueden confundir la Reproyección.  Si sabe que las fases de representación van a dejar muchos de los píxeles de profundidad finales con valores de profundidad inexactos, es probable que obtenga una mejor calidad visual si desactiva "habilitar el uso compartido del búfer de profundidad".

> [!NOTE]
> Por lo general, se recomienda usar búferes de profundidad de 16 bits para mejorar el rendimiento. Sin embargo, si se usa el formato de profundidad de 16 bits, los efectos requeridos del búfer de estarcido (como algunos paneles de desplazamiento de la interfaz de usuario de Unity) no funcionarán porque [Unity no crea un búfer de estarcido](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) en esta configuración. Si se selecciona el *formato de profundidad de 24 bits* a la inversa, se creará normalmente un [búfer de estarcido de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html) si es aplicable en la plataforma de gráficos de punto de conexión.