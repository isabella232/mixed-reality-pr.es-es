---
ms.openlocfilehash: 7cd9400ddb83b95f145a9b962be51aaed30df47b
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224498"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, compruebe tener instalado **AR Foundation** > **4.1.7**.

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-OpenXR.png)

> [!NOTE]
> Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Agregue el SDK de Azure Spatial Anchors V2.10 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-OpenXR.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo  [Importación de Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="unity-2020--windows-xr-plugin"></a>[Complemento de XR para Unity 2020 y Windows](#tab/winxr)

En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation > 4.0.12** y haga clic en el botón **Install** (Instalar) para instalar el paquete:

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-XRSDK.png)

> [!NOTE]
> Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Agregue el SDK de Azure Spatial Anchors V2.10 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.XRPlugginManagement.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-XRSDK.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo  [Importación de Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .

# <a name="legacy-wsa"></a>[WSA heredado](#tab/wsa)

En el menú de Unity, seleccione **Window** > **Package Manager** (Ventana > Administrador de paquetes) para abrir la ventana Package Manager y, a continuación, seleccione **AR Foundation > 3.1.3** y haga clic en el botón **Install** (Instalar) para instalar el paquete:

![Unity Package Manager con AR Foundation seleccionado](../images/mr-learning-asa/asa-02-section3-step1-1-Legacy.png)

> [!NOTE]
> Se instalará el paquete de AR Foundation porque así lo requiere el SDK de Azure Spatial Anchors que se importará en la siguiente sección.

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Agregue el SDK de Azure Spatial Anchors V2.7.2 al proyecto. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [AzureStorageForUnity.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.LegacyWSA.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](../images/mr-learning-azure/tutorial1-section4-step1-1-Legacy.png)

> [!NOTE]
> Si ve alguna advertencia CS0618 que indica que los elementos “WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)” y “WorldAnchor.GetNativeSpatialAnchorPtr()” están obsoletos, puede ignorarlas.

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo  [Importación de Mixed Reality Toolkit](../mr-learning-base-04.md#importing-the-tutorial-assets) .
