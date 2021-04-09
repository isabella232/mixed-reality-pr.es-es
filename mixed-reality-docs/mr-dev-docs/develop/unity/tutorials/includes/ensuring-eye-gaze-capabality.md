---
ms.openlocfilehash: 4b42b669e45181dec45cab2337d01488c77f77cb
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097083"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Garantía de la funcionalidad de entrada de mirada e incorporación del proveedor de datos de mirada

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.

En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):

* Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.

![Incorporación del proveedor de datos de mirada 1](../images/mr-learning-base/base-08-section1-step1-2.png)

Asigne **Microsoft.MixedReality.ToolKit.WindowsMixedReality.Input** > **WindowsMixedRealityEyeGazeProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.

![Incorporación del proveedor de datos de mirada 2](../images/mr-learning-base/base-08-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-eye-gaze-input-capability-and-adding-eye-gaze-data-provider"></a>Garantía de la funcionalidad de entrada de mirada e incorporación del proveedor de datos de mirada

En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):

* Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.

![Incorporación del proveedor de datos de mirada 1](../images/mr-learning-base/base-08-section1-step1-2openxr.png)

Asigne **Microsoft.MixedReality.ToolKit.XRSDK.OpenXR.Input** > **WindowsMixedRealityEyeGazeProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.

![Incorporación del proveedor de datos de mirada 2](../images/mr-learning-base/base-08-section1-step1-3openxr.png)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>Asegurarse de que está habilitada la funcionalidad de entrada de mirada

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Eye Gaze Input Capability** (Habilitar funcionalidad de entrada de mirada) esté atenuada:

![Ventana MRTK Project Configurator (Configurador del proyecto MRTK) de Unity](../images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> La funcionalidad de entrada de mirada con los ojos debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.
