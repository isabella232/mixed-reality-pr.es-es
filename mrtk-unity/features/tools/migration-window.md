---
title: El plazo de migración
description: Documentación sobre cómo migrar a una actualización en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 9d960d01e738736edd452a124db5c306b5d752ce
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176129"
---
# <a name="migration-window"></a><span data-ttu-id="5c568-104">El plazo de migración</span><span class="sxs-lookup"><span data-stu-id="5c568-104">Migration window</span></span>

<span data-ttu-id="5c568-105">A medida que MRTK se somete a cambios, algunos componentes podrían desusar y se introducirán reemplazos.</span><span class="sxs-lookup"><span data-stu-id="5c568-105">As the MRTK undergoes changes, some components might get deprecated and replacements will get introduced.</span></span>
<span data-ttu-id="5c568-106">La ventana de migración es una herramienta que ayuda a los usuarios a migrar automáticamente un subconjunto de esos componentes en desuso a los nuevos reemplazos.</span><span class="sxs-lookup"><span data-stu-id="5c568-106">The migration window is a tool that helps users to automatically migrate a subset of those deprecated components to the new replacements.</span></span>

![El plazo de migración](../images/migration-window/MRTK_Migration_Window.png)

## <a name="usage"></a><span data-ttu-id="5c568-108">Uso</span><span class="sxs-lookup"><span data-stu-id="5c568-108">Usage</span></span>

<span data-ttu-id="5c568-109">Para abrir la ventana, seleccione **Mixed Reality**  >  **Toolkit**  >  **migración de**  >  **utilidades.**</span><span class="sxs-lookup"><span data-stu-id="5c568-109">To open the window, select **Mixed Reality** > **Toolkit** > **Utilities** > **Migration Window**.</span></span> <span data-ttu-id="5c568-110">Una vez abierta la ventana de migración, las pestañas de navegación del modo de selección se pueden habilitar eligiendo la implementación específica del componente del controlador de migración.</span><span class="sxs-lookup"><span data-stu-id="5c568-110">Once the migration window is open, the selection mode navigation tabs can be enabled by choosing the component specific implementation of the migration handler.</span></span>  

![Modos de selección de migración](../images/migration-window/MRTK_Migration_Modes.png)

### <a name="object-mode"></a><span data-ttu-id="5c568-112">Modo de objeto</span><span class="sxs-lookup"><span data-stu-id="5c568-112">Object mode</span></span>

<span data-ttu-id="5c568-113">Al seleccionar la pestaña objects (Objetos), se habilita el campo de objeto al que el usuario puede arrastrar y colocar cualquier objeto Game de la escena o los objetos prefabs actualmente abiertos de la carpeta del proyecto que se va a migrar.</span><span class="sxs-lookup"><span data-stu-id="5c568-113">Selecting the objects tab enables the object Field to where the user can drag and drop any Game objects from the currently open scene or prefabs from the project folder to be migrated.</span></span>
<span data-ttu-id="5c568-114">Al presionar el *botón quitar (-)* que se muestra en el lado derecho del objeto enumerado, se quita el objeto de la lista de selección.</span><span class="sxs-lookup"><span data-stu-id="5c568-114">Pressing the remove *(-)* button displayed at the right side of the listed object removes the object from the selection list.</span></span>

<span data-ttu-id="5c568-115">Una vez que todos los objetos  deseados están en la lista, al presionar el botón Migrar se aplicarán los cambios necesarios para la implementación del controlador de migración elegido a todos los componentes de la selección que coincidan con la implementación.</span><span class="sxs-lookup"><span data-stu-id="5c568-115">Once all the desired objects are in the list, pressing the *Migrate* button will apply the changes required by the chosen migration handler implementation to all components in the selection that match the implementation.</span></span>

![Migración de selección](../images/migration-window/MRTK_Object_Migration.png)

### <a name="scene-mode"></a><span data-ttu-id="5c568-117">Modo de escena</span><span class="sxs-lookup"><span data-stu-id="5c568-117">Scene mode</span></span>

<span data-ttu-id="5c568-118">Permite al usuario arrastrar y colocar recursos de escena que contienen objetos que se van a migrar.</span><span class="sxs-lookup"><span data-stu-id="5c568-118">Allows user to drag and drop scene assets containing objects to be migrated.</span></span>

![Selección de escenas para la migración](../images/migration-window/MRTK_Scene_Selection.png)

### <a name="project-mode"></a><span data-ttu-id="5c568-120">Project modo de configuración</span><span class="sxs-lookup"><span data-stu-id="5c568-120">Project mode</span></span>

<span data-ttu-id="5c568-121">Al presionar *el botón* Migrar, se actualizará el componente de destino de la implementación del controlador de migración para todos los objetos prefabs y escenas del proyecto.</span><span class="sxs-lookup"><span data-stu-id="5c568-121">Pressing the *Migrate* button will update the component targeted by the migration handler implementation for all prefabs and scenes in the project.</span></span>

![Migración de un proyecto completo](../images/migration-window/MRTK_Project_Migration.png)

## <a name="see-also"></a><span data-ttu-id="5c568-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5c568-123">See also</span></span>

- [<span data-ttu-id="5c568-124">Actualización desde versiones anteriores</span><span class="sxs-lookup"><span data-stu-id="5c568-124">Updating from earlier versions</span></span>](../../updates-deployment/updating.md)
- [<span data-ttu-id="5c568-125">Versiones Mixed Reality Toolkit Microsoft</span><span class="sxs-lookup"><span data-stu-id="5c568-125">Microsoft Mixed Reality Toolkit releases</span></span>](../../release-notes/mrtk-26-release-notes.md)
- [<span data-ttu-id="5c568-126">Mapa de ruta de MRTK</span><span class="sxs-lookup"><span data-stu-id="5c568-126">MRTK roadmap</span></span>](../../roadmap.md)
