---
ms.openlocfilehash: dbaace96246f28050ff6fb189d9b626be6b0ec9e
ms.sourcegitcommit: e380d56f5504be4e4f069394a58cf0147eb33b66
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2021
ms.locfileid: "113603722"
---
# <a name="openxr"></a>[OpenXR](#tab/openxr)

Para empezar a trabajar con un **nuevo proyecto de Unity** mediante MRTK, comience desde el paso 2 del tutorial de MRTK:

> [!div class="nextstepaction"]
> [Configuración de un nuevo proyecto de OpenXR con MRTK](../../tutorials/mr-learning-base-02.md?tabs=openxr)

Si va a actualizar un proyecto de MRTK existente a **OpenXR,** primero querrá actualizar MRTK-Unity a la versión más reciente (versión 2.7.2 o posterior) para obtener correcciones de claves para la compatibilidad con el complemento Mixed Reality OpenXR.  Use la [Mixed Reality de](../../welcome-to-mr-feature-tool.md) características para actualizar a la versión más reciente de MRTK y, a continuación, siga los pasos de instalación manual de [OpenXR a continuación.](#manual-setup-without-mrtk) Consulte la documentación de MRTK para obtener información más detallada sobre cómo migrar un proyecto [de MRTK existente a OpenXR.](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)

> [!NOTE]
> Al actualizar desde una versión anterior de MRTK anterior a **la 2.5.3,** asegúrese de que la línea siguiente está en el archivo **Assets/MixedRealityToolkit.Generated/link.xml:**
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> Esta línea se agregará de forma predeterminada si empezó con MRTK 2.5.4 o posterior.

# <a name="windows-xr"></a>[Windows Xr](#tab/windowsxr)

Para empezar a trabajar con un **nuevo proyecto de Unity** mediante MRTK, comience desde el paso 2 del tutorial de MRTK:

> [!div class="nextstepaction"]
> [Configuración de un nuevo Windows XR con MRTK](../../tutorials/mr-learning-base-02.md?tabs=winxr)

# <a name="legacy-xr"></a>[XR heredado](#tab/legacy)

Para empezar a trabajar con un **nuevo proyecto de Unity** mediante MRTK, comience desde el paso 2 del tutorial de MRTK:

> [!div class="nextstepaction"]
> [Configuración de un nuevo proyecto XR heredado con MRTK](../../tutorials/mr-learning-base-02.md?tabs=wsa)