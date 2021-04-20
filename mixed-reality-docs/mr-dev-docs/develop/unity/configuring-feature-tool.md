---
title: Configuración de la herramienta de características de Mixed Reality
description: Obtenga información sobre cómo descargar e instalar paquetes de Mixed Reality para Unity desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 04/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 5b61924ccf4d3eb5f5433c9042582ff2a850bb04
ms.sourcegitcommit: 286384e6e255135939bce2ab0267a62558837562
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2021
ms.locfileid: "107731954"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="8f6df-104">Configuración de la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f6df-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="8f6df-105">Cuando usa la herramienta de características de Mixed Reality, tiene acceso a tres categorías de configuración diferentes que puede personalizar como desee:</span><span class="sxs-lookup"><span data-stu-id="8f6df-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="8f6df-106">Configuración de descarga</span><span class="sxs-lookup"><span data-stu-id="8f6df-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="8f6df-107">Configuración de características</span><span class="sxs-lookup"><span data-stu-id="8f6df-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="8f6df-108">Importar configuración</span><span class="sxs-lookup"><span data-stu-id="8f6df-108">Import settings</span></span>](#import-settings)

## <a name="download-settings"></a><span data-ttu-id="8f6df-109">Configuración de descarga</span><span class="sxs-lookup"><span data-stu-id="8f6df-109">Download settings</span></span>

![Configuración de descarga](images/FeatureToolSettings-Download.png)

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="8f6df-111">Sobrescribir archivos de paquete existentes</span><span class="sxs-lookup"><span data-stu-id="8f6df-111">Overwrite existing package files</span></span>

<span data-ttu-id="8f6df-112">Al habilitar esta opción, se descargan los archivos del paquete cada vez que se adquieren.</span><span class="sxs-lookup"><span data-stu-id="8f6df-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 

* <span data-ttu-id="8f6df-113">**Le recomendamos mantener esta opción deshabilitada para reducir el uso del ancho de banda de red**.</span><span class="sxs-lookup"><span data-stu-id="8f6df-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="8f6df-114">De manera predeterminada, los archivos de paquetes adquiridos previamente no se volverán a descargar.</span><span class="sxs-lookup"><span data-stu-id="8f6df-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="8f6df-115">Memoria caché de paquetes</span><span class="sxs-lookup"><span data-stu-id="8f6df-115">Package cache</span></span>

<span data-ttu-id="8f6df-116">Cambie esta configuración para actualizar la ubicación en la que se descargan los paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="8f6df-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="8f6df-117">Esta opción es de **solo lectura** en esta versión.</span><span class="sxs-lookup"><span data-stu-id="8f6df-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="8f6df-118">Es posible que en versiones futuras se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="8f6df-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="8f6df-119">Configuración de características</span><span class="sxs-lookup"><span data-stu-id="8f6df-119">Feature settings</span></span>

![Configuración de características](images/FeatureToolSettings-Feature.png)

### <a name="show-preview-releases"></a><span data-ttu-id="8f6df-121">Visualización de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="8f6df-121">Show preview releases</span></span>

<span data-ttu-id="8f6df-122">Habilite esta opción para adquirir versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="8f6df-122">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="8f6df-123">De manera predeterminada, las versiones preliminares no se muestran en la herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8f6df-123">By default, preview releases are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="8f6df-124">Cuando se define una versión preliminar, esta indica que contiene la designación **"-preview"** en la versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="8f6df-124">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

### <a name="show-early-access-program-features"></a><span data-ttu-id="8f6df-125">Visualización de características del programa de acceso anticipado</span><span class="sxs-lookup"><span data-stu-id="8f6df-125">Show early access program features</span></span>

<span data-ttu-id="8f6df-126">Habilite esta opción para adquirir características de las versiones de los programas de acceso anticipado registrados.</span><span class="sxs-lookup"><span data-stu-id="8f6df-126">Enable this setting to acquire features from registered early access programs releases.</span></span>

* <span data-ttu-id="8f6df-127">De manera predeterminada, las características de acceso anticipado no se muestran en la herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="8f6df-127">By default, early access features are not shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="8f6df-128">La habilitación de `Show early access program features` sin `Show preview releases` puede dar lugar a que los paquetes de acceso anticipado no aparezcan en la detección.</span><span class="sxs-lookup"><span data-stu-id="8f6df-128">Enabling `Show early access program features` without `Show preview releases` may result in eary access packages not appearing in Discovery.</span></span>

## <a name="import-settings"></a><span data-ttu-id="8f6df-129">Importar configuración</span><span class="sxs-lookup"><span data-stu-id="8f6df-129">Import settings</span></span>

![Importar configuración](images/FeatureToolSettings-Import.png)

### <a name="replace-existing-package-files"></a><span data-ttu-id="8f6df-131">Reemplazo de los archivos de paquete existentes</span><span class="sxs-lookup"><span data-stu-id="8f6df-131">Replace existing package files</span></span>

<span data-ttu-id="8f6df-132">De manera predeterminada, la herramienta de características de Mixed Reality quita las copias anteriores de los paquetes que se van a importar para reducir el tamaño de archivo y los cálculos innecesarios.</span><span class="sxs-lookup"><span data-stu-id="8f6df-132">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 

* <span data-ttu-id="8f6df-133">Desactive esta opción para conservar todas las versiones.</span><span class="sxs-lookup"><span data-stu-id="8f6df-133">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="8f6df-134">Ruta de importación relativa del proyecto</span><span class="sxs-lookup"><span data-stu-id="8f6df-134">Project relative import path</span></span>

<span data-ttu-id="8f6df-135">Cambie esta configuración para actualizar la ruta de acceso de la carpeta del proyecto en la que se copian los paquetes de características durante la importación.</span><span class="sxs-lookup"><span data-stu-id="8f6df-135">Change this setting to update project folder path where feature packages are copied on import.</span></span> 

* <span data-ttu-id="8f6df-136">Por ejemplo, si la carpeta del proyecto es **C:\GalaxyExplorer**, la ruta de acceso de importación completa será **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="8f6df-136">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="8f6df-137">Esta opción es de **solo lectura** en esta versión.</span><span class="sxs-lookup"><span data-stu-id="8f6df-137">This setting is **read-only** in this release.</span></span> <span data-ttu-id="8f6df-138">Es posible que en versiones futuras se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="8f6df-138">Future releases may make this setting configurable.</span></span>

## <a name="early-access-settings"></a><span data-ttu-id="8f6df-139">Configuración de acceso anticipado</span><span class="sxs-lookup"><span data-stu-id="8f6df-139">Early Access settings</span></span>

![Configuración de acceso anticipado](images/FeatureToolSettings-EarlyAccess.png)
 
### <a name="ask-for-confirmation-before-removing-an-early-access-program"></a><span data-ttu-id="8f6df-141">Pedido de confirmación antes de quitar un programa de acceso anticipado</span><span class="sxs-lookup"><span data-stu-id="8f6df-141">Ask for confirmation before removing an early access program</span></span>

<span data-ttu-id="8f6df-142">Esta opción determina si se mostrará un aviso cada vez que se quite un programa de acceso anticipado.</span><span class="sxs-lookup"><span data-stu-id="8f6df-142">This setting determines if a prompt will be displayed each time an early access program is removed.</span></span>

### <a name="my-previews"></a><span data-ttu-id="8f6df-143">Mis versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="8f6df-143">My previews</span></span>

<span data-ttu-id="8f6df-144">Lista de programas de acceso anticipado registrados.</span><span class="sxs-lookup"><span data-stu-id="8f6df-144">The list of registered early access programs.</span></span> <span data-ttu-id="8f6df-145">Use `Add`, `Edit` y `Remove` para administrar la colección de programas registrados.</span><span class="sxs-lookup"><span data-stu-id="8f6df-145">Use the `Add`, `Edit` and `Remove` to manage the collection of registered programs.</span></span>

## <a name="diagnostic-settings"></a><span data-ttu-id="8f6df-146">Configuración de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="8f6df-146">Diagnostic settings</span></span>

![Configuración de diagnóstico](images/FeatureToolSettings-Diagnostics.png)

### <a name="log-file"></a><span data-ttu-id="8f6df-148">Archivo de registro</span><span class="sxs-lookup"><span data-stu-id="8f6df-148">Log file</span></span>

<span data-ttu-id="8f6df-149">Muestra la ruta del archivo de registro de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="8f6df-149">Displays the path to the diagnostic log file.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f6df-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="8f6df-150">See also</span></span>

- [<span data-ttu-id="8f6df-151">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f6df-151">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)