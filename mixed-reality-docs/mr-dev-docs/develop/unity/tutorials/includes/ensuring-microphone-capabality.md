---
ms.openlocfilehash: 202d96435c437bc7630e82ea99a61f3c2a91c826
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/31/2021
ms.locfileid: "106097757"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Complemento XR para Unity 2019/2020 y Windows](#tab/winxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Garantía de la funcionalidad del micrófono e incorporación del proveedor de datos de entrada de voz

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:

![Enable microphone capability (Habilitar la funcionalidad del micrófono)](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.

En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):

* Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.

![Proveedor de datos para agregar nuevos comandos de voz](../images/mr-learning-base/base-09-section1-step1-2.png)

Asigne **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.

![Adición de la configuración de los nuevos comandos de voz](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

## <a name="ensuring-microphone-capability-and-adding-speech-input-data-provider"></a>Garantía de la funcionalidad del micrófono e incorporación del proveedor de datos de entrada de voz

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:

![Habilitar la funcionalidad del micrófono para OpenXR](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#configuring-the-unity-project) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.

En la ventana Hierarchy (Jerarquía), seleccione el objeto MixedRealityToolkit y, a continuación, en la ventana Inspector, navegue hasta la pestaña Input (Entrada):

* Expanda la sección **Input Data Providers** (Proveedores de datos de entrada) y haga clic en el botón **+ Add Data Provider** (+ Agregar proveedor de datos) para agregar un nuevo proveedor de datos.

![Adición de nuevos comandos de voz para OpenXR](../images/mr-learning-base/base-09-section1-step1-2.png)

Asigne **Microsoft.MixedReality.ToolKit.Windows.Input** > **WindowsSpeechInputProvider** al campo **Type** (Tipo) del nuevo proveedor de datos.

![Adición de la configuración de los nuevos comandos de voz para OpenXR](../images/mr-learning-base/base-09-section1-step1-3.png)

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

## <a name="ensuring-the-microphone-capability-is-enabled"></a>Asegurarse de que la funcionalidad del micrófono está habilitada

En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador de proyecto de MRTK) y, a continuación, en la sección **UWP Capabilities** (Funcionalidades para UWP), verifique que la opción **Enable Microphone Capability** (Habilitar funcionalidad del micrófono) esté atenuada:

![Enable microphone capability (Habilitar la funcionalidad del micrófono)](../images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> La funcionalidad del micrófono debe haberse habilitado durante las instrucciones de [Aplicación de la configuración de MRTK Project Configurator](../mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) al configurar el proyecto de Unity al principio de esta serie de tutoriales. Sin embargo, si no está habilitada, asegúrese de habilitarla ahora.
