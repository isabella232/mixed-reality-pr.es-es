---
title: Autorización de cambios en el proyecto
description: Obtenga información sobre cómo autorizar los cambios en el proyecto en la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243974"
---
# <a name="authorizing-project-changes"></a><span data-ttu-id="7ed61-104">Autorización de cambios en el proyecto</span><span class="sxs-lookup"><span data-stu-id="7ed61-104">Authorizing project changes</span></span>

<span data-ttu-id="7ed61-105">Antes de modificar el proyecto de Unity, los cambios en el manifiesto y los archivos del proyecto deben revisarse y aprobarse:</span><span class="sxs-lookup"><span data-stu-id="7ed61-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![Solicitud de autorización](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="7ed61-107">Manifest</span><span class="sxs-lookup"><span data-stu-id="7ed61-107">Manifest</span></span>

<span data-ttu-id="7ed61-108">Los cambios en el manifiesto propuestos se pueden ver en la columna **Manifiesto** de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="7ed61-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="7ed61-109">Este contenido es exactamente el que se escribirá en el manifiesto del proyecto (**Packages/manifest.json**):</span><span class="sxs-lookup"><span data-stu-id="7ed61-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![Vista previa del manifiesto](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="7ed61-111">Archivos que se copiarán en el proyecto</span><span class="sxs-lookup"><span data-stu-id="7ed61-111">Files to be copied into the project</span></span>

<span data-ttu-id="7ed61-112">En la sección **Files to be copied into the project** (Archivos que se copiarán en el proyecto) de la derecha se muestra los archivos del paquete de características específicos que se copiarán en el proyecto de Unity:</span><span class="sxs-lookup"><span data-stu-id="7ed61-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![Vista previa del manifiesto con los archivos que se copiarán](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="7ed61-114">Comparación de manifiestos</span><span class="sxs-lookup"><span data-stu-id="7ed61-114">Compare manifests</span></span>

<span data-ttu-id="7ed61-115">Para ver una comparación en paralelo detallada de todos los cambios propuestos, seleccione **Comparar**:</span><span class="sxs-lookup"><span data-stu-id="7ed61-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![Comparación de manifiestos](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="7ed61-117">Aprobación de cambios</span><span class="sxs-lookup"><span data-stu-id="7ed61-117">Approving changes</span></span>

<span data-ttu-id="7ed61-118">Cuando se aprueben los cambios propuestos, los archivos de la lista se copiarán en el proyecto de Unity y el manifiesto se actualizará con las referencias a estos archivos.</span><span class="sxs-lookup"><span data-stu-id="7ed61-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="7ed61-119">Los archivos del paquete de características (\*.tgz) se deben agregar al control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="7ed61-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="7ed61-120">Se hace referencia a ellos mediante una ruta de acceso relativa para permitir que los equipos de desarrollo compartan fácilmente las características y los cambios del manifiesto.</span><span class="sxs-lookup"><span data-stu-id="7ed61-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="7ed61-121">Como parte de las modificaciones, se realizará una copia de seguridad del archivo **manifest.json** actual.</span><span class="sxs-lookup"><span data-stu-id="7ed61-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ed61-122">Al ver las copias de seguridad del manifiesto, la más antigua se denominará **manifest.json.backup**.</span><span class="sxs-lookup"><span data-stu-id="7ed61-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="7ed61-123">Las copias de seguridad más recientes se anotarán con un valor numérico, empezando por cero (0).</span><span class="sxs-lookup"><span data-stu-id="7ed61-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="7ed61-124">Vuelta al paso anterior</span><span class="sxs-lookup"><span data-stu-id="7ed61-124">Going back to the previous step</span></span>

<span data-ttu-id="7ed61-125">Si necesita realizar cambios en las selecciones de características, use **Volver** para regresar al paso de [importación](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="7ed61-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed61-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="7ed61-126">See also</span></span>

- [<span data-ttu-id="7ed61-127">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="7ed61-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="7ed61-128">Importación de paquetes seleccionados</span><span class="sxs-lookup"><span data-stu-id="7ed61-128">Importing selected packages</span></span>](importing-features.md)
