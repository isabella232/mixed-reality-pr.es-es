---
title: Configuración de la herramienta de características de Mixed Reality
description: Obtenga información sobre cómo descargar e instalar paquetes de Mixed Reality para Unity desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "99244015"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="32cfb-104">Configuración de la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="32cfb-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="32cfb-105">Cuando usa la herramienta de características de Mixed Reality, tiene acceso a tres categorías de configuración diferentes que puede personalizar como desee:</span><span class="sxs-lookup"><span data-stu-id="32cfb-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* [<span data-ttu-id="32cfb-106">Configuración de descarga</span><span class="sxs-lookup"><span data-stu-id="32cfb-106">Download settings</span></span>](#download-settings)
* [<span data-ttu-id="32cfb-107">Configuración de características</span><span class="sxs-lookup"><span data-stu-id="32cfb-107">Feature settings</span></span>](#feature-settings)
* [<span data-ttu-id="32cfb-108">Importar configuración</span><span class="sxs-lookup"><span data-stu-id="32cfb-108">Import settings</span></span>](#import-settings)

![Configuración](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="32cfb-110">Configuración de descarga</span><span class="sxs-lookup"><span data-stu-id="32cfb-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="32cfb-111">Sobrescribir archivos de paquete existentes</span><span class="sxs-lookup"><span data-stu-id="32cfb-111">Overwrite existing package files</span></span>

<span data-ttu-id="32cfb-112">Al habilitar esta opción, se descargan los archivos del paquete cada vez que se adquieren.</span><span class="sxs-lookup"><span data-stu-id="32cfb-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="32cfb-113">**Le recomendamos mantener esta opción deshabilitada para reducir el uso del ancho de banda de red**.</span><span class="sxs-lookup"><span data-stu-id="32cfb-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="32cfb-114">De manera predeterminada, los archivos de paquetes adquiridos previamente no se volverán a descargar.</span><span class="sxs-lookup"><span data-stu-id="32cfb-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="32cfb-115">Memoria caché de paquetes</span><span class="sxs-lookup"><span data-stu-id="32cfb-115">Package cache</span></span>

<span data-ttu-id="32cfb-116">Cambie esta configuración para actualizar la ubicación en la que se descargan los paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="32cfb-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="32cfb-117">Esta opción es de **solo lectura** en esta versión.</span><span class="sxs-lookup"><span data-stu-id="32cfb-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="32cfb-118">Es posible que en versiones futuras se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="32cfb-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="32cfb-119">Configuración de características</span><span class="sxs-lookup"><span data-stu-id="32cfb-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="32cfb-120">Inclusión de versiones preliminares</span><span class="sxs-lookup"><span data-stu-id="32cfb-120">Include preview releases</span></span>

<span data-ttu-id="32cfb-121">Habilite esta opción para adquirir versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="32cfb-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="32cfb-122">De manera predeterminada, las versiones preliminares no se muestran en la herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="32cfb-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="32cfb-123">Cuando se define una versión preliminar, esta indica que contiene la designación **"-preview"** en la versión del paquete.</span><span class="sxs-lookup"><span data-stu-id="32cfb-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="32cfb-124">Importar configuración</span><span class="sxs-lookup"><span data-stu-id="32cfb-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="32cfb-125">Reemplazo de los archivos de paquete existentes</span><span class="sxs-lookup"><span data-stu-id="32cfb-125">Replace existing package files</span></span>

<span data-ttu-id="32cfb-126">De manera predeterminada, la herramienta de características de Mixed Reality quita las copias anteriores de los paquetes que se van a importar para reducir el tamaño de archivo y los cálculos innecesarios.</span><span class="sxs-lookup"><span data-stu-id="32cfb-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="32cfb-127">Desactive esta opción para conservar todas las versiones.</span><span class="sxs-lookup"><span data-stu-id="32cfb-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="32cfb-128">Ruta de importación relativa del proyecto</span><span class="sxs-lookup"><span data-stu-id="32cfb-128">Project relative import path</span></span>

<span data-ttu-id="32cfb-129">Cambie esta configuración para actualizar la ruta de acceso de la carpeta del proyecto en la que se copian los paquetes de características durante la importación.</span><span class="sxs-lookup"><span data-stu-id="32cfb-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="32cfb-130">Por ejemplo, si la carpeta del proyecto es **C:\GalaxyExplorer**, la ruta de acceso de importación completa será **C:\GalaxyExplorer\Packages\MixedReality**.</span><span class="sxs-lookup"><span data-stu-id="32cfb-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="32cfb-131">Esta opción es de **solo lectura** en esta versión.</span><span class="sxs-lookup"><span data-stu-id="32cfb-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="32cfb-132">Es posible que en versiones futuras se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="32cfb-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="32cfb-133">Vea también</span><span class="sxs-lookup"><span data-stu-id="32cfb-133">See also</span></span>

- [<span data-ttu-id="32cfb-134">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="32cfb-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)