---
title: Uso del administrador de paquetes de Unity
description: Uso de MRTK en Unity Administrador de paquetes
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, paquetes MRTK,
ms.openlocfilehash: e3e7a2d06cd38d7a9e8daf579f1a312904a86280
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345078"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="0cde7-104">Mixed Reality Toolkit y Unity Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="0cde7-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="0cde7-105">A partir de la versión 2.5.0, con la herramienta de características de [Mixed Reality,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)Microsoft Mixed Reality Toolkit se integra con Unity Administrador de paquetes (UPM) cuando se usa Unity 2019.4 y versiones más recientes.</span><span class="sxs-lookup"><span data-stu-id="0cde7-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="0cde7-106">Uso de la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0cde7-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="0cde7-107">Como se describe [en Le damos la bienvenida a Mixed Reality Feature Tool,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) puede descargar la herramienta mediante [este vínculo](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="0cde7-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cde7-108">Si el manifiesto del proyecto tiene una entrada en la sección , se `Microsoft Mixed Reality` `scopedRegistries` recomienda quitarlo.</span><span class="sxs-lookup"><span data-stu-id="0cde7-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="0cde7-109">Para quitar un registro con ámbito configurado, consulte `Edit`  >  `Project Settings`  >  `Package Manager` a .</span><span class="sxs-lookup"><span data-stu-id="0cde7-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Eliminación del registro con ámbito](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="0cde7-111">Los paquetes MRTK aparecen debajo `Mixed Reality Toolkit` del encabezado al detectar características.</span><span class="sxs-lookup"><span data-stu-id="0cde7-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Detectar características](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="0cde7-113">Al seleccionar características, no es necesario preocuparse por las dependencias necesarias; la herramienta las descargará e integrará automáticamente en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="0cde7-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dependencias requeridas](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="0cde7-115">Administración Mixed Reality características con unity Administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="0cde7-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="0cde7-116">Una vez que Mixed Reality Toolkit se ha agregado al manifiesto del paquete, se puede administrar mediante la interfaz de usuario Administrador de paquetes Unity.</span><span class="sxs-lookup"><span data-stu-id="0cde7-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Paquete UPM de MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="0cde7-118">Si se quita Mixed Reality Toolkit mediante el Administrador de paquetes Unity, tendrá que volver a agregarlo mediante los pasos descritos [anteriormente.](#using-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="0cde7-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="0cde7-119">Uso de Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="0cde7-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="0cde7-120">A diferencia de cuando se usan archivos de paquete de recursos (.unitypackage), y no importan automáticamente los recursos y las escenas `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="0cde7-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="0cde7-121">Para usar uno o varios de los ejemplos, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="0cde7-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="0cde7-122">En el Editor de Unity, vaya a `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="0cde7-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="0cde7-123">En la lista de paquetes, seleccione `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="0cde7-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="0cde7-124">Busque las muestras deseadas en la `Samples` lista.</span><span class="sxs-lookup"><span data-stu-id="0cde7-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="0cde7-125">Haga clic en `Import into Project`</span><span class="sxs-lookup"><span data-stu-id="0cde7-125">Click `Import into Project`</span></span>

![Importación de ejemplos](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="0cde7-127">Cuando se actualiza un paquete de ejemplo, Unity proporciona la opción de actualizar ejemplos importados.</span><span class="sxs-lookup"><span data-stu-id="0cde7-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="0cde7-128">La actualización de un ejemplo importado sobrescribirá los cambios realizados en esa muestra y en los recursos asociados.</span><span class="sxs-lookup"><span data-stu-id="0cde7-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="0cde7-129">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0cde7-129">See Also</span></span>

- [<span data-ttu-id="0cde7-130">paquetes Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="0cde7-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)