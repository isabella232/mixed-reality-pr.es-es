---
title: Actualización
description: Documentación para migrar desde una versión inferior de MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 04/19/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 97f45328bc8f9b811e815da0240138790db699c6
ms.sourcegitcommit: 0b09536c16f6802acc120a973d720aec7e30f617
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2021
ms.locfileid: "107742241"
---
# <a name="updating-the-microsoft-mixed-reality-toolkit"></a><span data-ttu-id="daa05-104">Actualización de Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="daa05-104">Updating the Microsoft Mixed Reality Toolkit</span></span>

- [<span data-ttu-id="daa05-105">Actualización a una nueva versión de MRTK</span><span class="sxs-lookup"><span data-stu-id="daa05-105">Upgrading to a new version of MRTK</span></span>](#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="daa05-106">De 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-106">2.3.0 to 2.4.0</span></span>](#updating-230-to-240)
- [<span data-ttu-id="daa05-107">De 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="daa05-107">2.2.0 to 2.3.0</span></span>](#updating-220-to-230)
- [<span data-ttu-id="daa05-108">De 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="daa05-108">2.1.0 to 2.2.0</span></span>](#updating-210-to-220)
- [<span data-ttu-id="daa05-109">De 2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="daa05-109">2.0.0 to 2.1.0</span></span>](#updating-200-to-210)
- [<span data-ttu-id="daa05-110">RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-110">RC2 to 2.0.0</span></span>](#updating-rc2-to-200)

## <a name="finding-the-current-version"></a><span data-ttu-id="daa05-111">Búsqueda de la versión actual</span><span class="sxs-lookup"><span data-stu-id="daa05-111">Finding the current version</span></span> 

<span data-ttu-id="daa05-112">Siga estas instrucciones para averiguar qué versión de MRTK está usando actualmente:</span><span class="sxs-lookup"><span data-stu-id="daa05-112">Follow these instructions to figure out which version of the MRTK you're currently using:</span></span>

1. <span data-ttu-id="daa05-113">Apertura del proyecto de MRTK en Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-113">Open your MRTK project in Unity</span></span>
2. <span data-ttu-id="daa05-114">Vaya a la carpeta "MixedRealityToolkit" en la ventana del proyecto.</span><span class="sxs-lookup"><span data-stu-id="daa05-114">Navigate to the "MixedRealityToolkit" folder in your Project window</span></span>
3. <span data-ttu-id="daa05-115">Abra el archivo denominado "Version"</span><span class="sxs-lookup"><span data-stu-id="daa05-115">Open the file called "Version"</span></span>

<span data-ttu-id="daa05-116">Si el archivo y la carpeta anteriores no existen, se encuentra en una versión más reciente de MRTK.</span><span class="sxs-lookup"><span data-stu-id="daa05-116">If the file and folder above doesn't exist, you're on a newer version of the MRTK.</span></span> <span data-ttu-id="daa05-117">En ese caso, pruebe lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="daa05-117">In that case, try the following:</span></span>

1. <span data-ttu-id="daa05-118">Vaya a la carpeta "Mixed Reality Toolkit Foundation".</span><span class="sxs-lookup"><span data-stu-id="daa05-118">Navigate to the "Mixed Reality Toolkit Foundation" folder</span></span>
2. <span data-ttu-id="daa05-119">Haga clic en "package.js" para ver una vista previa en Unity o ábrala con un editor de texto.</span><span class="sxs-lookup"><span data-stu-id="daa05-119">Click on the "package.json" to see a preview in Unity or open it with a text editor</span></span>
3. <span data-ttu-id="daa05-120">Busque la línea con la palabra "version:"</span><span class="sxs-lookup"><span data-stu-id="daa05-120">Look for the line with the word "version:"</span></span> 

## <a name="upgrading-to-a-new-version-of-mrtk"></a><span data-ttu-id="daa05-121">Actualización a una nueva versión de MRTK</span><span class="sxs-lookup"><span data-stu-id="daa05-121">Upgrading to a new version of MRTK</span></span>

<span data-ttu-id="daa05-122">*Se recomienda encarecidamente ejecutar [](../features/tools/migration-window.md)* la herramienta de migración después de obtener la actualización de MRTK para corregir y actualizar automáticamente los componentes en desuso y ajustarse a los cambios importantes.</span><span class="sxs-lookup"><span data-stu-id="daa05-122">*It is strongly recommended to run the [migration tool](../features/tools/migration-window.md) after getting the MRTK update* to auto-fix and upgrade from deprecated components and adjust to breaking changes.</span></span> <span data-ttu-id="daa05-123">La herramienta de migración forma parte del **paquete Herramientas.**</span><span class="sxs-lookup"><span data-stu-id="daa05-123">The migration tool is part of the **Tools** package.</span></span>

<span data-ttu-id="daa05-124">Las instrucciones siguientes describen la ruta de actualización de 2.4.0 a 2.5.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-124">The instructions below describe the 2.4.0 to 2.5.0 upgrade path.</span></span> <span data-ttu-id="daa05-125">Si el proyecto está en la versión 2.3.0 o anterior, siga leyendo los [](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) cambios entre versiones para comprender la ruta de actualización o lea las instrucciones de la versión anterior para realizar una actualización versión por versión. [](#updating-230-to-240)</span><span class="sxs-lookup"><span data-stu-id="daa05-125">If your project is on 2.3.0 or earlier, read on to the changes [between versions](#updating-230-to-240) to understand the upgrade path, or read the previous [release's instructions](https://microsoft.github.io/MixedRealityToolkit-Unity/version/releases/2.4.0/Documentation/Updating.html) to do a version-by-version upgrade.</span></span>

### <a name="mixed-reality-feature-tool"></a><span data-ttu-id="daa05-126">Herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="daa05-126">Mixed Reality Feature Tool</span></span>
<span data-ttu-id="daa05-127">La manera más fácil de actualizar MRTK a una versión más reciente de MRTK es usar la herramienta de características de [Mixed Reality](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) para descargar los paquetes más recientes y cargarlos directamente en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-127">The easiest way to upgrade MRTK to a newer version MRTK is by using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) to download the latest packages and load them directly to your Unity project.</span></span>

<span data-ttu-id="daa05-128">Si el proyecto usó previamente archivos de recursos de Unity (.unitypackage), consulte [estas instrucciones.](#switching-from-unity-asset-files-to-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="daa05-128">If the project previously used Unity asset (.unitypackage) files, please see [these instructions](#switching-from-unity-asset-files-to-mixed-reality-feature-tool).</span></span> 

### <a name="unity-asset-unitypackage-files"></a><span data-ttu-id="daa05-129">Archivos de recursos de Unity (.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="daa05-129">Unity asset (.unitypackage) files</span></span>

<span data-ttu-id="daa05-130">Otra ruta de actualización consiste en descargar manualmente los paquetes de Unity de MRTK y aplicarlos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="daa05-130">Another upgrade path is to manually download MRTK Unity packages and apply them to your project.</span></span> <span data-ttu-id="daa05-131">Consulte los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="daa05-131">See the steps below,</span></span>

1. <span data-ttu-id="daa05-132">Guarde una copia del proyecto actual, en caso de que se presione algún grupo de seguridad en cualquier punto de los pasos de actualización.</span><span class="sxs-lookup"><span data-stu-id="daa05-132">Save a copy of your current project, in case you hit any snags at any point in the upgrade steps.</span></span>
1. <span data-ttu-id="daa05-133">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-133">Close Unity</span></span>
1. <span data-ttu-id="daa05-134">Dentro de *la carpeta Activos,* elimine las siguientes carpetas **MRTK,** junto con sus archivos .meta (es posible que el proyecto no tenga todas las carpetas enumeradas)</span><span class="sxs-lookup"><span data-stu-id="daa05-134">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="daa05-135">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="daa05-135">MRTK/Core</span></span>
    - <span data-ttu-id="daa05-136">MRTK/Examples</span><span class="sxs-lookup"><span data-stu-id="daa05-136">MRTK/Examples</span></span>
    - <span data-ttu-id="daa05-137">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="daa05-137">MRTK/Extensions</span></span>
    - <span data-ttu-id="daa05-138">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="daa05-138">MRTK/Providers</span></span>
    - <span data-ttu-id="daa05-139">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="daa05-139">MRTK/SDK</span></span>
    - <span data-ttu-id="daa05-140">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="daa05-140">MRTK/Services</span></span>
    - <span data-ttu-id="daa05-141">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="daa05-141">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-142">Si se realizaron modificaciones en los sombreadores MRTK, cree una copia de seguridad local antes de eliminar la carpeta MRTK/StandardAssets.</span><span class="sxs-lookup"><span data-stu-id="daa05-142">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="daa05-143">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="daa05-143">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-144">NO elimine la **carpeta MixedRealityToolkit.Generated** ni su archivo .meta.</span><span class="sxs-lookup"><span data-stu-id="daa05-144">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="daa05-145">Eliminación de la **carpeta Biblioteca**</span><span class="sxs-lookup"><span data-stu-id="daa05-145">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-146">Algunas herramientas de Unity, como Unity Collab, guarda la información de configuración en la carpeta Biblioteca.</span><span class="sxs-lookup"><span data-stu-id="daa05-146">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="daa05-147">Si usa una herramienta que lo hace, copie primero la carpeta de datos de la herramienta de La biblioteca antes de eliminarla y, después, restáurela después de volver a generar la biblioteca.</span><span class="sxs-lookup"><span data-stu-id="daa05-147">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="daa05-148">Volver a abrir el proyecto en Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-148">Re-open the project in Unity</span></span>
1. <span data-ttu-id="daa05-149">Importación de los nuevos paquetes de Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-149">Import the new unity packages</span></span>
    - <span data-ttu-id="daa05-150">Foundation: _importe primero este paquete._</span><span class="sxs-lookup"><span data-stu-id="daa05-150">Foundation - _Import this package first_</span></span>
    - <span data-ttu-id="daa05-151">Herramientas</span><span class="sxs-lookup"><span data-stu-id="daa05-151">Tools</span></span>
    - <span data-ttu-id="daa05-152">(Opcional) Extensiones</span><span class="sxs-lookup"><span data-stu-id="daa05-152">(Optional) Extensions</span></span>
    > [!NOTE]
    > <span data-ttu-id="daa05-153">Si se hubieran instalado extensiones adicionales, es posible que deban volver a importarse.</span><span class="sxs-lookup"><span data-stu-id="daa05-153">If additional extensions had been installed, they may need to be re-imported.</span></span>
    - <span data-ttu-id="daa05-154">(Opcional) Ejemplos</span><span class="sxs-lookup"><span data-stu-id="daa05-154">(Optional) Examples</span></span>
1. <span data-ttu-id="daa05-155">Cierre Unity y elimine la **carpeta Biblioteca** (lea primero la nota siguiente).</span><span class="sxs-lookup"><span data-stu-id="daa05-155">Close Unity and delete the **Library** folder (read the note below first!).</span></span> <span data-ttu-id="daa05-156">Este paso es necesario para forzar a Unity a actualizar su base de datos de recursos y conciliar los perfiles personalizados existentes.</span><span class="sxs-lookup"><span data-stu-id="daa05-156">This step is necessary to force Unity to refresh its asset database and reconcile existing custom profiles.</span></span>
1. <span data-ttu-id="daa05-157">Inicie Unity y para cada escena del proyecto.</span><span class="sxs-lookup"><span data-stu-id="daa05-157">Launch Unity, and for each scene in the project</span></span>
    - <span data-ttu-id="daa05-158">Elimine **MixedRealityToolkit** y **MixedRealityPlayspace,** si está presente, de la jerarquía.</span><span class="sxs-lookup"><span data-stu-id="daa05-158">Delete **MixedRealityToolkit** and **MixedRealityPlayspace**, if present, from the hierarchy.</span></span> <span data-ttu-id="daa05-159">Esto eliminará la cámara principal, pero se volverá a crear en el paso siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa05-159">This will delete the main camera, but it will be re-created in the next step.</span></span> <span data-ttu-id="daa05-160">Si alguna de las propiedades de la cámara principal se ha cambiado manualmente, estas se tendrán que volver a aplicar manualmente una vez creada la nueva cámara.</span><span class="sxs-lookup"><span data-stu-id="daa05-160">If any properties of the main camera have been manually changed, these will have to be re-applied manually once the new camera is created.</span></span>
    - <span data-ttu-id="daa05-161">Seleccione **MixedRealityToolkit -> Agregar a la escena y configurar**</span><span class="sxs-lookup"><span data-stu-id="daa05-161">Select **MixedRealityToolkit -> Add to Scene and Configure**</span></span>
    - <span data-ttu-id="daa05-162">Seleccione **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (solo debe realizarse una vez): se actualizarán todos los perfiles de asignación de controladores personalizados con ejes y datos actualizados, a la vez que se mantienen intactas las acciones de entrada asignadas de forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="daa05-162">Select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** (only needs to be done once)       - This will update any custom controller mapping profiles with updated axes and data, while leaving your custom-assigned input actions intact</span></span>
1. <span data-ttu-id="daa05-163">Ejecute la [herramienta de migración](../features/tools/migration-window.md) y ejecute la herramienta en el proyecto *completo* para asegurarse de que todo el código se actualiza a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="daa05-163">Run the [migration tool](../features/tools/migration-window.md) and run the tool on the *Full Project* to ensure that all of your code is updated to the latest.</span></span>
   <span data-ttu-id="daa05-164">La ventana de migración contiene una serie de controladores de migración diferentes, que se deben ejecutar cada uno por su cuenta.</span><span class="sxs-lookup"><span data-stu-id="daa05-164">The migration window contains a number of different migration handlers, which must each be run on their own.</span></span> <span data-ttu-id="daa05-165">Este paso implica lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="daa05-165">This step involves:</span></span>
   - <span data-ttu-id="daa05-166">Seleccione el primer controlador de migración en la lista **desplegable Selección del controlador de** migración.</span><span class="sxs-lookup"><span data-stu-id="daa05-166">Select the first migration handler from the **Migration Handler Selection** dropdown.</span></span>
   - <span data-ttu-id="daa05-167">Haga clic en el botón "Proyecto completo".</span><span class="sxs-lookup"><span data-stu-id="daa05-167">Click the "Full Project" button.</span></span>
   - <span data-ttu-id="daa05-168">Haga clic en el botón "Add full project for migration" (Agregar proyecto completo para la migración) (examinará todo el proyecto en busca de objetos que se van a migrar).</span><span class="sxs-lookup"><span data-stu-id="daa05-168">Click the "Add full project for migration" button (this will scan the entire project for objects to migrate).</span></span>
   - <span data-ttu-id="daa05-169">Haga clic en el botón "Migrar", que debe habilitarse si se han encontrado objetos migrables.</span><span class="sxs-lookup"><span data-stu-id="daa05-169">Click the "Migrate" button which should be enabled if any migrateable objects were found.</span></span>
   - <span data-ttu-id="daa05-170">Repita los tres pasos anteriores para cada uno de los controladores de migración de la lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="daa05-170">Repeat the previous three steps for each of the migration handlers within the dropdown.</span></span>
     <span data-ttu-id="daa05-171">(Vea [este problema que](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) trata el trabajo que se puede realizar para simplificar este proceso de migración en una versión futura).</span><span class="sxs-lookup"><span data-stu-id="daa05-171">(See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8552) which covers work that can be done to simplify this migration process in a future release)</span></span>

### <a name="switching-from-unity-asset-files-to-mixed-reality-feature-tool"></a><span data-ttu-id="daa05-172">Cambio de archivos de recursos de Unity a Mixed Reality Feature Tool</span><span class="sxs-lookup"><span data-stu-id="daa05-172">Switching from Unity asset files to Mixed Reality Feature Tool</span></span>

<span data-ttu-id="daa05-173">El cambio de archivos de recursos de Unity Mixed Reality paquetes de Feature Tool aporta una serie de ventajas:</span><span class="sxs-lookup"><span data-stu-id="daa05-173">Switching from Unity asset files to Mixed Reality Feature Tool packages brings a number of benefits:</span></span>

- <span data-ttu-id="daa05-174">Actualización más sencilla</span><span class="sxs-lookup"><span data-stu-id="daa05-174">Easier updating</span></span>
- <span data-ttu-id="daa05-175">Tiempos de compilación más rápidos</span><span class="sxs-lookup"><span data-stu-id="daa05-175">Faster compile times</span></span>
- <span data-ttu-id="daa05-176">Menos proyectos en la solución Visual Studio proyecto</span><span class="sxs-lookup"><span data-stu-id="daa05-176">Fewer projects in the Visual Studio solution</span></span>

<span data-ttu-id="daa05-177">Cambiar al uso de Mixed Reality Feature Tool requiere un conjunto único de pasos manuales.</span><span class="sxs-lookup"><span data-stu-id="daa05-177">Changing to using the Mixed Reality Feature Tool requires a one-time set of manual steps.</span></span>

1. <span data-ttu-id="daa05-178">Guarde una copia del proyecto actual.</span><span class="sxs-lookup"><span data-stu-id="daa05-178">Save a copy of your current project.</span></span>
1. <span data-ttu-id="daa05-179">Cerrar Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-179">Close Unity</span></span>
1. <span data-ttu-id="daa05-180">Dentro de *la carpeta Activos,* elimine las siguientes carpetas **MRTK,** junto con sus archivos .meta (es posible que el proyecto no tenga todas las carpetas enumeradas)</span><span class="sxs-lookup"><span data-stu-id="daa05-180">Inside the *Assets* folder, delete the following **MRTK** folders, along with their .meta files (the project may not have all listed folders)</span></span>
    - <span data-ttu-id="daa05-181">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="daa05-181">MRTK/Core</span></span>
    - <span data-ttu-id="daa05-182">MRTK/Examples</span><span class="sxs-lookup"><span data-stu-id="daa05-182">MRTK/Examples</span></span>
    - <span data-ttu-id="daa05-183">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="daa05-183">MRTK/Extensions</span></span>
    - <span data-ttu-id="daa05-184">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="daa05-184">MRTK/Providers</span></span>
    - <span data-ttu-id="daa05-185">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="daa05-185">MRTK/SDK</span></span>
    - <span data-ttu-id="daa05-186">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="daa05-186">MRTK/Services</span></span>
    - <span data-ttu-id="daa05-187">MRTK/StandardAssets</span><span class="sxs-lookup"><span data-stu-id="daa05-187">MRTK/StandardAssets</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-188">Si se realizaron modificaciones en los sombreadores MRTK, cree una copia de seguridad local antes de eliminar la carpeta MRTK/StandardAssets.</span><span class="sxs-lookup"><span data-stu-id="daa05-188">If modifications were made to the MRTK shaders, create a local backup before deleteing the MRTK/StandardAssets folder</span></span>
    - <span data-ttu-id="daa05-189">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="daa05-189">MRTK/Tools</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-190">NO elimine la **carpeta MixedRealityToolkit.Generated** ni su archivo .meta.</span><span class="sxs-lookup"><span data-stu-id="daa05-190">Do NOT delete the **MixedRealityToolkit.Generated** folder, or its .meta file.</span></span>
1. <span data-ttu-id="daa05-191">Eliminación de la **carpeta Biblioteca**</span><span class="sxs-lookup"><span data-stu-id="daa05-191">Delete the **Library** folder</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="daa05-192">Algunas herramientas de Unity, como Unity Collab, guarda la información de configuración en la carpeta Biblioteca.</span><span class="sxs-lookup"><span data-stu-id="daa05-192">Some Unity tools, like Unity Collab, save configuration info to the Library folder.</span></span> <span data-ttu-id="daa05-193">Si usa una herramienta que lo hace, copie primero la carpeta de datos de la herramienta de La biblioteca antes de eliminarla y, después, restáurela después de volver a generar la biblioteca.</span><span class="sxs-lookup"><span data-stu-id="daa05-193">If using a tool that does this, first copy the tool's data folder from Library before deleting, then restore it after Library is regenerated.</span></span>
1. <span data-ttu-id="daa05-194">Volver a abrir el proyecto en Unity</span><span class="sxs-lookup"><span data-stu-id="daa05-194">Re-open the project in Unity</span></span>

<span data-ttu-id="daa05-195">Una vez que se hayan realizado los pasos anteriores, ejecute [Mixed Reality Feature Tool](#mixed-reality-feature-tool) e importe la versión deseada de Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="daa05-195">Once the previous steps have been performed, run the [Mixed Reality Feature Tool](#mixed-reality-feature-tool) and import the desired version of the Mixed Reality Toolkit.</span></span>

## <a name="updating-230-to-240"></a><span data-ttu-id="daa05-196">Actualización de 2.3.0 a 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-196">Updating 2.3.0 to 2.4.0</span></span>

<span data-ttu-id="daa05-197">[Cambio de nombre de carpeta](#folder-renames-in-240) 
 [Cambios de API](#api-changes-in-240)</span><span class="sxs-lookup"><span data-stu-id="daa05-197">[Folder renames](#folder-renames-in-240)
[API changes](#api-changes-in-240)</span></span>

### <a name="folder-renames-in-240"></a><span data-ttu-id="daa05-198">Cambio de nombre de carpeta en la versión 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-198">Folder renames in 2.4.0</span></span>

<span data-ttu-id="daa05-199">Se ha cambiado el nombre de las carpetas de MixedRealityToolkit y se han movido a una jerarquía común en la versión 2.4.</span><span class="sxs-lookup"><span data-stu-id="daa05-199">The MixedRealityToolkit folders have been renamed and moved into a common hierarchy in version 2.4.</span></span> <span data-ttu-id="daa05-200">Si una aplicación usa rutas de acceso codificadas de forma fuerte a los recursos de MRTK, deberá actualizarse según la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="daa05-200">If an application uses hard coded paths to MRTK resources, they will need to be updated per the following table.</span></span>

| <span data-ttu-id="daa05-201">Carpeta anterior</span><span class="sxs-lookup"><span data-stu-id="daa05-201">Previous Folder</span></span> | <span data-ttu-id="daa05-202">Nueva carpeta</span><span class="sxs-lookup"><span data-stu-id="daa05-202">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-203">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="daa05-203">MixedRealityToolkit</span></span> | <span data-ttu-id="daa05-204">MRTK/Core</span><span class="sxs-lookup"><span data-stu-id="daa05-204">MRTK/Core</span></span> |
| <span data-ttu-id="daa05-205">MixedRealityToolkit.Examples</span><span class="sxs-lookup"><span data-stu-id="daa05-205">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="daa05-206">MRTK/Examples</span><span class="sxs-lookup"><span data-stu-id="daa05-206">MRTK/Examples</span></span> |
| <span data-ttu-id="daa05-207">MixedRealityToolkit.Extensions</span><span class="sxs-lookup"><span data-stu-id="daa05-207">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="daa05-208">MRTK/Extensions</span><span class="sxs-lookup"><span data-stu-id="daa05-208">MRTK/Extensions</span></span> |
| <span data-ttu-id="daa05-209">MixedRealityToolkit.Providers</span><span class="sxs-lookup"><span data-stu-id="daa05-209">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="daa05-210">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="daa05-210">MRTK/Providers</span></span> |
| <span data-ttu-id="daa05-211">MixedRealityToolkit.SDK</span><span class="sxs-lookup"><span data-stu-id="daa05-211">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="daa05-212">MRTK/SDK</span><span class="sxs-lookup"><span data-stu-id="daa05-212">MRTK/SDK</span></span> |
| <span data-ttu-id="daa05-213">MixedRealityToolkit.Services</span><span class="sxs-lookup"><span data-stu-id="daa05-213">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="daa05-214">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="daa05-214">MRTK/Services</span></span> |
| <span data-ttu-id="daa05-215">MixedRealityToolkit.Tests</span><span class="sxs-lookup"><span data-stu-id="daa05-215">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="daa05-216">MRTK/Tests</span><span class="sxs-lookup"><span data-stu-id="daa05-216">MRTK/Tests</span></span> |
| <span data-ttu-id="daa05-217">MixedRealityToolkit.Tools</span><span class="sxs-lookup"><span data-stu-id="daa05-217">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="daa05-218">MRTK/Tools</span><span class="sxs-lookup"><span data-stu-id="daa05-218">MRTK/Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="daa05-219">contiene `MixedRealityToolkit.Generated` archivos generados por el cliente y permanece sin cambios.</span><span class="sxs-lookup"><span data-stu-id="daa05-219">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

### <a name="eye-gaze-setup-in-240"></a><span data-ttu-id="daa05-220">Configuración de la mirada con los ojos en la versión 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-220">Eye gaze setup in 2.4.0</span></span>

<span data-ttu-id="daa05-221">Esta versión de MRTK modifica los pasos necesarios para la configuración de la mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="daa05-221">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="daa05-222">La _casilla "IsEyeTrackingEnabled"_ se puede encontrar en la configuración de mirada del perfil de puntero de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-222">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="daa05-223">Al activar esta casilla, se habilitará la mirada con los ojos, en lugar de la mirada basada en la cabeza predeterminada.</span><span class="sxs-lookup"><span data-stu-id="daa05-223">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="daa05-224">Para obtener más información sobre estos cambios e instrucciones completas para la configuración del seguimiento ocular, consulte el artículo [seguimiento ocular.](../features/input/eye-tracking/eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="daa05-224">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/input/eye-tracking/eye-tracking-basic-setup.md) article.</span></span>

### <a name="eye-gaze-pointer-behavior-in-240"></a><span data-ttu-id="daa05-225">Comportamiento del puntero de mirada con los ojos en 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-225">Eye gaze pointer behavior in 2.4.0</span></span>

<span data-ttu-id="daa05-226">El comportamiento del puntero predeterminado de la mirada con los ojos se ha modificado para que coincida con el comportamiento predeterminado del puntero de mirada con la cabeza.</span><span class="sxs-lookup"><span data-stu-id="daa05-226">The eye gaze default pointer behavior have been modified to match the head gaze default pointer behavior.</span></span> <span data-ttu-id="daa05-227">Un puntero de mirada con los ojos se suprimirá automáticamente una vez que se detecte una mano.</span><span class="sxs-lookup"><span data-stu-id="daa05-227">An eye gaze pointer will automatically be suppressed once a hand is detected.</span></span> <span data-ttu-id="daa05-228">El puntero de mirada con los ojos volverá a estar visible después de decir "Seleccionar".</span><span class="sxs-lookup"><span data-stu-id="daa05-228">The eye gaze pointer will become visible again after saying "Select".</span></span>

<span data-ttu-id="daa05-229">Puede encontrar detalles sobre las configuraciones de mirada y mano en el [artículo sobre los ojos y las](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) manos.</span><span class="sxs-lookup"><span data-stu-id="daa05-229">Details about gaze and hand setups can be found in the [eyes and hands](../features/input/eye-tracking/eye-tracking-eyes-and-hands.md#how-to-keep-gaze-pointer-always-on) article.</span></span>

### <a name="api-changes-in-240"></a><span data-ttu-id="daa05-230">Cambios de API en la versión 2.4.0</span><span class="sxs-lookup"><span data-stu-id="daa05-230">API changes in 2.4.0</span></span>

<span data-ttu-id="daa05-231">**Clases de controlador personalizadas**</span><span class="sxs-lookup"><span data-stu-id="daa05-231">**Custom controller classes**</span></span>

<span data-ttu-id="daa05-232">Anteriormente, las clases de controlador personalizadas tenían que definir `SetupDefaultInteractions(Handedness)` .</span><span class="sxs-lookup"><span data-stu-id="daa05-232">Custom controller classes previously had to define `SetupDefaultInteractions(Handedness)`.</span></span> <span data-ttu-id="daa05-233">Este método se ha quedado obsoleto en la versión 2.4, ya que el parámetro handedness era redundante con la propia entrega de la clase del controlador.</span><span class="sxs-lookup"><span data-stu-id="daa05-233">This method has been made obsolete in 2.4, as the handedness parameter was redundant with the controller class' own handedness.</span></span> <span data-ttu-id="daa05-234">El nuevo método no tiene parámetros.</span><span class="sxs-lookup"><span data-stu-id="daa05-234">The new method has no parameters.</span></span> <span data-ttu-id="daa05-235">Además, muchas clases de controlador definieron esto de la misma manera ( ), por lo que la llamada completa se ha refactorizado en y se ha convertido en una invalidación opcional en lugar `AssignControllerMappings(DefaultInteractions);` `BaseController` de obligatoria.</span><span class="sxs-lookup"><span data-stu-id="daa05-235">Additionally, many controller classes defined this the same way (`AssignControllerMappings(DefaultInteractions);`), so the full call has been refactored down into `BaseController` and made an optional override instead of required.</span></span>

<span data-ttu-id="daa05-236">**Propiedades de mirada con los ojos**</span><span class="sxs-lookup"><span data-stu-id="daa05-236">**Eye Gaze properties**</span></span>

<span data-ttu-id="daa05-237">El `UseEyeTracking` nombre de la propiedad de la implementación de se ha cambiado a `GazeProvider` `IMixedRealityEyeGazeProvider` `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="daa05-237">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="daa05-238">Si lo hizo anteriormente...</span><span class="sxs-lookup"><span data-stu-id="daa05-238">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="daa05-239">Haga esto ahora...</span><span class="sxs-lookup"><span data-stu-id="daa05-239">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="daa05-240">**Propiedades de WindowsApiChecker**</span><span class="sxs-lookup"><span data-stu-id="daa05-240">**WindowsApiChecker properties**</span></span>

<span data-ttu-id="daa05-241">Las siguientes propiedades de WindowsApiChecker se han marcado como obsoletas.</span><span class="sxs-lookup"><span data-stu-id="daa05-241">The following WindowsApiChecker properties have been marked as obsolete.</span></span> <span data-ttu-id="daa05-242">Use `IsMethodAvailable` o `IsPropertyAvailable` `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="daa05-242">Please use `IsMethodAvailable`, `IsPropertyAvailable` or `IsTypeAvailable`.</span></span>

- <span data-ttu-id="daa05-243">UniversalApiContractV8_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-243">UniversalApiContractV8_IsAvailable</span></span>
- <span data-ttu-id="daa05-244">UniversalApiContractV7_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-244">UniversalApiContractV7_IsAvailable</span></span>
- <span data-ttu-id="daa05-245">UniversalApiContractV6_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-245">UniversalApiContractV6_IsAvailable</span></span>
- <span data-ttu-id="daa05-246">UniversalApiContractV5_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-246">UniversalApiContractV5_IsAvailable</span></span>
- <span data-ttu-id="daa05-247">UniversalApiContractV4_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-247">UniversalApiContractV4_IsAvailable</span></span>
- <span data-ttu-id="daa05-248">UniversalApiContractV3_IsAvailable</span><span class="sxs-lookup"><span data-stu-id="daa05-248">UniversalApiContractV3_IsAvailable</span></span>

<span data-ttu-id="daa05-249">No hay ningún plan para agregar propiedades a WindowsApiChecker para futuras versiones de contrato de API.</span><span class="sxs-lookup"><span data-stu-id="daa05-249">There are no plans to add properties to WindowsApiChecker for future API contract versions.</span></span>

<span data-ttu-id="daa05-250">**GltfMeshPrimitiveAttributes de solo lectura**</span><span class="sxs-lookup"><span data-stu-id="daa05-250">**GltfMeshPrimitiveAttributes read-only**</span></span>

<span data-ttu-id="daa05-251">Los atributos primitivos de la malla gltf que se solían establecer, ahora son de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="daa05-251">The gltf mesh primitive attributes used to be settable, they are now read-only.</span></span> <span data-ttu-id="daa05-252">Sus valores se establecerán una vez cuando se deserialice.</span><span class="sxs-lookup"><span data-stu-id="daa05-252">Their values will be set once when deserialized.</span></span>

### <a name="custom-button-icon-migration"></a><span data-ttu-id="daa05-253">Migración de icono de botón personalizado</span><span class="sxs-lookup"><span data-stu-id="daa05-253">Custom Button Icon Migration</span></span>

<span data-ttu-id="daa05-254">Anteriormente, los iconos de botón personalizados requerían asignar un nuevo material al representador de cuatro botones.</span><span class="sxs-lookup"><span data-stu-id="daa05-254">Previously custom button icons required assigning a new material to the button's quad renderer.</span></span> <span data-ttu-id="daa05-255">Esto ya no es necesario y se recomienda mover texturas de icono personalizadas a iconSet.</span><span class="sxs-lookup"><span data-stu-id="daa05-255">This is no longer necessary and we recommend moving custom icon textures into an IconSet.</span></span> <span data-ttu-id="daa05-256">Se conservan los iconos y materiales personalizados existentes.</span><span class="sxs-lookup"><span data-stu-id="daa05-256">Existing custom materials and icons are preserved.</span></span> <span data-ttu-id="daa05-257">Sin embargo, serán menos óptimos hasta que se actualicen.</span><span class="sxs-lookup"><span data-stu-id="daa05-257">However they will be less optimal until upgraded.</span></span>
<span data-ttu-id="daa05-258">Para actualizar los recursos de todos los botones del proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="daa05-258">To upgrade the assets on all buttons in the project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="daa05-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="daa05-259">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

![Cuadro de diálogo actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="daa05-261">Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit.Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="daa05-261">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="daa05-262">Un cuadro de diálogo indicará que esto ha tenido lugar.</span><span class="sxs-lookup"><span data-stu-id="daa05-262">A dialog will indicate that this has taken place.</span></span>

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

## <a name="updating-220-to-230"></a><span data-ttu-id="daa05-264">Actualización de 2.2.0 a 2.3.0</span><span class="sxs-lookup"><span data-stu-id="daa05-264">Updating 2.2.0 to 2.3.0</span></span>

- [<span data-ttu-id="daa05-265">Cambios en la API</span><span class="sxs-lookup"><span data-stu-id="daa05-265">API changes</span></span>](#api-changes-in-230)

### <a name="api-changes-in-230"></a><span data-ttu-id="daa05-266">Cambios de API en la versión 2.3.0</span><span class="sxs-lookup"><span data-stu-id="daa05-266">API changes in 2.3.0</span></span>

<span data-ttu-id="daa05-267">**ControllerPoseSynchronizer**</span><span class="sxs-lookup"><span data-stu-id="daa05-267">**ControllerPoseSynchronizer**</span></span>

<span data-ttu-id="daa05-268">El campo privado ControllerPoseSynchronizer.handedness se ha marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="daa05-268">The private ControllerPoseSynchronizer.handedness field has been marked as obsolete.</span></span> <span data-ttu-id="daa05-269">Esto debería tener un impacto mínimo en las aplicaciones, ya que el campo no es visible fuera de su clase.</span><span class="sxs-lookup"><span data-stu-id="daa05-269">This should have minimal impact on applications as the field is not visible outside of its class.</span></span>

<span data-ttu-id="daa05-270">Se ha quitado el setter de la propiedad ControllerPoseSynchronizer.Handedness pública ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span><span class="sxs-lookup"><span data-stu-id="daa05-270">The public ControllerPoseSynchronizer.Handedness property's setter has been removed ([#7012](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7012)).</span></span>

<span data-ttu-id="daa05-271">**MSBuild para Unity**</span><span class="sxs-lookup"><span data-stu-id="daa05-271">**MSBuild for Unity**</span></span>

<span data-ttu-id="daa05-272">Esta versión de MRTK usa una versión más reciente de MSBuild para Unity que las versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="daa05-272">This version of MRTK uses a newer version of MSBuild for Unity than previous releases.</span></span> <span data-ttu-id="daa05-273">Durante la carga del proyecto, si la versión anterior aparece en el manifiesto del administrador de paquetes de Unity, aparecerá el cuadro de diálogo de configuración, con la opción Habilitar MSBuild para Unity activada.</span><span class="sxs-lookup"><span data-stu-id="daa05-273">During project load, if the older version is listed in the Unity Package Manger manifest, the configuration dialog will appear, with the Enable MSBuild for Unity option checked.</span></span> <span data-ttu-id="daa05-274">La aplicación realizará una actualización.</span><span class="sxs-lookup"><span data-stu-id="daa05-274">Applying will perform an upgrade.</span></span>

<span data-ttu-id="daa05-275">**ScriptingUtilities**</span><span class="sxs-lookup"><span data-stu-id="daa05-275">**ScriptingUtilities**</span></span>

<span data-ttu-id="daa05-276">La clase ScriptingUtilities se ha marcado como obsoleta y se ha reemplazado por ScriptUtilities, en el ensamblado Microsoft.MixedReality.Toolkit.Editor.Utilities.</span><span class="sxs-lookup"><span data-stu-id="daa05-276">The ScriptingUtilities class has been marked as obsolete and has been replaced by ScriptUtilities, in the Microsoft.MixedReality.Toolkit.Editor.Utilities assembly.</span></span> <span data-ttu-id="daa05-277">La nueva clase refina el comportamiento anterior y agrega compatibilidad para quitar definiciones de scripting.</span><span class="sxs-lookup"><span data-stu-id="daa05-277">The new class refines previous behavior and adds support for removing scripting definitions.</span></span>

<span data-ttu-id="daa05-278">Aunque el código existente seguirá funcionando en la versión 2.3.0, se recomienda actualizar a la nueva clase.</span><span class="sxs-lookup"><span data-stu-id="daa05-278">While existing code will continue to function in version 2.3.0, it is recommended to update to the new class.</span></span>

<span data-ttu-id="daa05-279">**ShellHandRayPointer**</span><span class="sxs-lookup"><span data-stu-id="daa05-279">**ShellHandRayPointer**</span></span>

<span data-ttu-id="daa05-280">Los miembros lineRendererSelected y lineRendererNoTarget de la clase ShellHandRayPointer se han reemplazado por lineMaterialSelected y lineMaterialNoTarget, respectivamente ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span><span class="sxs-lookup"><span data-stu-id="daa05-280">The lineRendererSelected and lineRendererNoTarget members of the ShellHandRayPointer class have been replaced by lineMaterialSelected and lineMaterialNoTarget, respectively ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6863)).</span></span>

<span data-ttu-id="daa05-281">Reemplace lineRendererSelected por lineMaterialSelected o lineRendererNoTarget por lineMaterialNoTarget para resolver errores de compilación.</span><span class="sxs-lookup"><span data-stu-id="daa05-281">Please replace lineRendererSelected with lineMaterialSelected and/or lineRendererNoTarget with lineMaterialNoTarget to resolve compile errors.</span></span>

<span data-ttu-id="daa05-282">**StartupBehavior del observador espacial**</span><span class="sxs-lookup"><span data-stu-id="daa05-282">**Spatial observer StartupBehavior**</span></span>

<span data-ttu-id="daa05-283">Los observadores espaciales basados en la clase ahora respetan el valor de StartupBehavior cuando se vuelve a habilitar `BaseSpatialObserver` ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span><span class="sxs-lookup"><span data-stu-id="daa05-283">Spatial observers built upon the `BaseSpatialObserver` class now honor the value of StartupBehavior when re-enabled ([#6919](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6919)).</span></span>

<span data-ttu-id="daa05-284">No se requiere ningún cambio para aprovechar esta corrección.</span><span class="sxs-lookup"><span data-stu-id="daa05-284">No changes are required to take advantage of this fix.</span></span>

<span data-ttu-id="daa05-285">**Se han actualizado los requisitos previos del control de la experiencia de usuario para usar PressableButton.**</span><span class="sxs-lookup"><span data-stu-id="daa05-285">**UX control prefabs updated to use PressableButton**</span></span>

<span data-ttu-id="daa05-286">Los siguientes elementos prefab ahora usan el componente PressableButton en lugar de TouchHandler para la interacción cercana ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span><span class="sxs-lookup"><span data-stu-id="daa05-286">The following prefabs are now using the PressableButton component instead of TouchHandler for near interaction ([7070](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/7070))</span></span>

- <span data-ttu-id="daa05-287">AnimationButton</span><span class="sxs-lookup"><span data-stu-id="daa05-287">AnimationButton</span></span>
- <span data-ttu-id="daa05-288">Botón</span><span class="sxs-lookup"><span data-stu-id="daa05-288">Button</span></span>
- <span data-ttu-id="daa05-289">ButtonHoloLens1</span><span class="sxs-lookup"><span data-stu-id="daa05-289">ButtonHoloLens1</span></span>
- <span data-ttu-id="daa05-290">ButtonHoloLens1Toggle</span><span class="sxs-lookup"><span data-stu-id="daa05-290">ButtonHoloLens1Toggle</span></span>
- <span data-ttu-id="daa05-291">CheckBox</span><span class="sxs-lookup"><span data-stu-id="daa05-291">CheckBox</span></span>
- <span data-ttu-id="daa05-292">RadialSet</span><span class="sxs-lookup"><span data-stu-id="daa05-292">RadialSet</span></span>
- <span data-ttu-id="daa05-293">ToggleButton</span><span class="sxs-lookup"><span data-stu-id="daa05-293">ToggleButton</span></span>
- <span data-ttu-id="daa05-294">ToggleSwitch</span><span class="sxs-lookup"><span data-stu-id="daa05-294">ToggleSwitch</span></span>
- <span data-ttu-id="daa05-295">UnityUIButton</span><span class="sxs-lookup"><span data-stu-id="daa05-295">UnityUIButton</span></span>
- <span data-ttu-id="daa05-296">UnityUICheckboxButton</span><span class="sxs-lookup"><span data-stu-id="daa05-296">UnityUICheckboxButton</span></span>
- <span data-ttu-id="daa05-297">UnityUIRadialButton</span><span class="sxs-lookup"><span data-stu-id="daa05-297">UnityUIRadialButton</span></span>
- <span data-ttu-id="daa05-298">UnityUIToggleButton</span><span class="sxs-lookup"><span data-stu-id="daa05-298">UnityUIToggleButton</span></span>

<span data-ttu-id="daa05-299">El código de la aplicación puede requerir la actualización debido a este cambio.</span><span class="sxs-lookup"><span data-stu-id="daa05-299">Application code may require updating due to this change.</span></span>

<span data-ttu-id="daa05-300">**Espacio de nombres WindowsMixedRealityUtilities**</span><span class="sxs-lookup"><span data-stu-id="daa05-300">**WindowsMixedRealityUtilities namespace**</span></span>

<span data-ttu-id="daa05-301">El espacio de nombres de WindowsMixedRealityUtilities ha cambiado de Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input a Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span><span class="sxs-lookup"><span data-stu-id="daa05-301">The namespace of WindowsMixedRealityUtilities changed from Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input to Microsoft.MixedReality.Toolkit.WindowsMixedReality ([#6863](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/6989)).</span></span>

<span data-ttu-id="daa05-302">Actualice las #using para resolver errores de compilación.</span><span class="sxs-lookup"><span data-stu-id="daa05-302">Please update #using statements to resolve compile errors.</span></span>

## <a name="updating-210-to-220"></a><span data-ttu-id="daa05-303">Actualización de 2.1.0 a 2.2.0</span><span class="sxs-lookup"><span data-stu-id="daa05-303">Updating 2.1.0 to 2.2.0</span></span>

- [<span data-ttu-id="daa05-304">Cambios en la API</span><span class="sxs-lookup"><span data-stu-id="daa05-304">API changes</span></span>](#api-changes-in-220)

### <a name="api-changes-in-220"></a><span data-ttu-id="daa05-305">Cambios de API en la versión 2.2.0</span><span class="sxs-lookup"><span data-stu-id="daa05-305">API changes in 2.2.0</span></span>

<span data-ttu-id="daa05-306">**IMixedRealityBoundarySystem.Contains**</span><span class="sxs-lookup"><span data-stu-id="daa05-306">**IMixedRealityBoundarySystem.Contains**</span></span>

<span data-ttu-id="daa05-307">Anteriormente, este método tomaba una enumeración experimental específica definida por Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-307">This method previously took in a specific, Unity-defined experimental enum.</span></span> <span data-ttu-id="daa05-308">Ahora toma una enumeración definida por MRTK que es idéntica a la enumeración de Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-308">It now takes in an MRTK-defined enum that's identical to the Unity enum.</span></span> <span data-ttu-id="daa05-309">Este cambio ayuda a preparar MRTK para las FUTURAS API de límites de Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-309">This change helps prepare the MRTK for Unity's future boundary APIs.</span></span>

<span data-ttu-id="daa05-310">**MixedRealityServiceProfileAttribute**</span><span class="sxs-lookup"><span data-stu-id="daa05-310">**MixedRealityServiceProfileAttribute**</span></span>

<span data-ttu-id="daa05-311">Para describir mejor los requisitos para admitir un perfil, MixedRealityServiceProfileAttribute se ha actualizado para agregar una colección opcional de tipos excluidos.</span><span class="sxs-lookup"><span data-stu-id="daa05-311">To better describe the requirements for supporting a profile, the MixedRealityServiceProfileAttribute has been updated to add an optional collection of excluded types.</span></span> <span data-ttu-id="daa05-312">Como parte de este cambio, se ha cambiado la propiedad ServiceType de Type a Type[] y se ha cambiado el nombre a RequiredTypes.</span><span class="sxs-lookup"><span data-stu-id="daa05-312">As part of this change, the ServiceType property has been changed from Type to Type[] and been renamed to RequiredTypes.</span></span>

<span data-ttu-id="daa05-313">También se ha agregado una segunda propiedad, ExcludedTypes.</span><span class="sxs-lookup"><span data-stu-id="daa05-313">A second property, ExcludedTypes has also been added.</span></span>

## <a name="updating-200-to-210"></a><span data-ttu-id="daa05-314">Actualización de 2.0.0 a 2.1.0</span><span class="sxs-lookup"><span data-stu-id="daa05-314">Updating 2.0.0 to 2.1.0</span></span>

- [<span data-ttu-id="daa05-315">Cambios en la API</span><span class="sxs-lookup"><span data-stu-id="daa05-315">API changes</span></span>](#api-changes-in-210)
- [<span data-ttu-id="daa05-316">Cambios de perfil</span><span class="sxs-lookup"><span data-stu-id="daa05-316">Profile changes</span></span>](#profile-changes-in-210)

### <a name="api-changes-in-210"></a><span data-ttu-id="daa05-317">Cambios de API en la versión 2.1.0</span><span class="sxs-lookup"><span data-stu-id="daa05-317">API changes in 2.1.0</span></span>

<span data-ttu-id="daa05-318">**BaseNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="daa05-318">**BaseNearInteractionTouchable**</span></span>

<span data-ttu-id="daa05-319">se `BaseNearInteractionTouchable` ha modificado para marcar el método como `OnValidate` virtual.</span><span class="sxs-lookup"><span data-stu-id="daa05-319">The `BaseNearInteractionTouchable` has been modified to mark the `OnValidate` method as virtual.</span></span> <span data-ttu-id="daa05-320">Las clases que `BaseNearInteractionTouchable` extienden (por ejemplo: `NearInteractionTouchableUnityUI` ) se han actualizado para reflejar este cambio.</span><span class="sxs-lookup"><span data-stu-id="daa05-320">Classes that extend `BaseNearInteractionTouchable` (ex: `NearInteractionTouchableUnityUI`) have been updated to reflect this change.</span></span>

<span data-ttu-id="daa05-321">**ColliderNearInteractionTouchable**</span><span class="sxs-lookup"><span data-stu-id="daa05-321">**ColliderNearInteractionTouchable**</span></span>

<span data-ttu-id="daa05-322">La clase `ColliderNearInteractionTouchable` está desusada.</span><span class="sxs-lookup"><span data-stu-id="daa05-322">The `ColliderNearInteractionTouchable` class has been deprecated.</span></span> <span data-ttu-id="daa05-323">Actualice las referencias de código para usar `BaseNearInteractionTouchable` .</span><span class="sxs-lookup"><span data-stu-id="daa05-323">Please update code references to use `BaseNearInteractionTouchable`.</span></span>

<span data-ttu-id="daa05-324">**IMixedRealityMouseDeviceManager**</span><span class="sxs-lookup"><span data-stu-id="daa05-324">**IMixedRealityMouseDeviceManager**</span></span>

<span data-ttu-id="daa05-325">**_Añadido_**</span><span class="sxs-lookup"><span data-stu-id="daa05-325">**_Added_**</span></span>

<span data-ttu-id="daa05-326">`IMixedRealityMouseDeviceManager` se han agregado las `CursorSpeed` propiedades `WheelSpeed` y .</span><span class="sxs-lookup"><span data-stu-id="daa05-326">`IMixedRealityMouseDeviceManager` has been added `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="daa05-327">Estas propiedades permiten a las aplicaciones especificar un valor multiplicador por el que se escalará la velocidad del cursor y la rueda, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="daa05-327">These properties allow applications to specify a multiplier value by which the speed of the cursor and wheel, respectively will be scaled.</span></span>

<span data-ttu-id="daa05-328">Se trata de un cambio importante y requiere que se modifiquen las implementaciones existentes del administrador de dispositivos del mouse.</span><span class="sxs-lookup"><span data-stu-id="daa05-328">This is a breaking change and requires existing mouse device manager implementations to be modified .</span></span>

>[!NOTE]
><span data-ttu-id="daa05-329">Este cambio no es compatible con versiones anteriores de la versión 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-329">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="daa05-330">**_Obsoleto_**</span><span class="sxs-lookup"><span data-stu-id="daa05-330">**_Deprecated_**</span></span>

<span data-ttu-id="daa05-331">La `MouseInputProfile` propiedad se ha marcado como obsoleta y se quitará de una versión futura de Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="daa05-331">The `MouseInputProfile` property has been marked as obsolete and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="daa05-332">Se recomienda que el código de aplicación ya no use esta propiedad.</span><span class="sxs-lookup"><span data-stu-id="daa05-332">It is recommended that application code no longer use this property.</span></span>

<span data-ttu-id="daa05-333">**Interactuable**</span><span class="sxs-lookup"><span data-stu-id="daa05-333">**Interactable**</span></span>

<span data-ttu-id="daa05-334">Los siguientes métodos y propiedades han quedado en desuso y se quitarán de una versión futura de Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="daa05-334">The following methods and properties have been deprecated and will be removed from a future version of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="daa05-335">La recomendación es actualizar el código de la aplicación según las instrucciones contenidas en el atributo Obsoleto y que se muestran en la consola.</span><span class="sxs-lookup"><span data-stu-id="daa05-335">The recommendation is to update application code per the guidance contained in the Obsolete attribute and displayed in the console.</span></span>

- `public bool Enabled`
- `public bool FocusEnabled`
- `public void ForceUpdateThemes()`
- `public bool IsDisabled`
- `public bool IsToggleButton`
- `public int GetDimensionIndex()`
- `public State[] GetStates()`
- `public bool RequiresFocus`
- `public void ResetBaseStates()`
- `public virtual void SetCollision(bool collision)`
- `public virtual void SetCustom(bool custom)`
- `public void SetDimensionIndex(int index)`
- `public virtual void SetDisabled(bool disabled)`
- `public virtual void SetFocus(bool focus)`
- `public virtual void SetGesture(bool gesture)`
- `public virtual void SetGestureMax(bool gesture)`
- `public virtual void SetGrab(bool grab)`
- `public virtual void SetInteractive(bool interactive)`
- `public virtual void SetObservation(bool observation)`
- `public virtual void SetObservationTargeted(bool targeted)`
- `public virtual void SetPhysicalTouch(bool touch)`
- `public virtual void SetPress(bool press)`
- `public virtual void SetTargeted(bool targeted)`
- `public virtual void SetToggled(bool toggled)`
- `public virtual void SetVisited(bool visited)`
- `public virtual void SetVoiceCommand(bool voice)`

<span data-ttu-id="daa05-336">**NearInteractionTouchableSurface**</span><span class="sxs-lookup"><span data-stu-id="daa05-336">**NearInteractionTouchableSurface**</span></span>

<span data-ttu-id="daa05-337">La `NearInteractionTouchableSurface` clase se ha agregado y ahora actúa como clase base para y `NearInteractionTouchable` `NearInteractionTouchableUnityUI` .</span><span class="sxs-lookup"><span data-stu-id="daa05-337">The `NearInteractionTouchableSurface` class has been added and now serves as the base class for `NearInteractionTouchable` and `NearInteractionTouchableUnityUI`.</span></span>

### <a name="profile-changes-in-210"></a><span data-ttu-id="daa05-338">Cambios de perfil en la versión 2.1.0</span><span class="sxs-lookup"><span data-stu-id="daa05-338">Profile changes in 2.1.0</span></span>

<span data-ttu-id="daa05-339">**Perfil de seguimiento de manos**</span><span class="sxs-lookup"><span data-stu-id="daa05-339">**Hand tracking profile**</span></span>

<span data-ttu-id="daa05-340">La malla de mano y las visualizaciones conjuntas ahora tienen un editor y una configuración de reproductor independientes.</span><span class="sxs-lookup"><span data-stu-id="daa05-340">The hand mesh and joint visualizations now have a separate editor and player settings.</span></span> <span data-ttu-id="daa05-341">El perfil de seguimiento de manos se ha actualizado para permitir establecer estas visualizaciones en . Nothing, Everything, Editor o Player.</span><span class="sxs-lookup"><span data-stu-id="daa05-341">The hand tracking profile has been updated to allow for setting these visualizations to; Nothing, Everything, Editor or Player.</span></span>

![Modos de visualización con la mano](../release-notes/images/HandTrackingVisualizationModes.png)

<span data-ttu-id="daa05-343">Es posible que sea necesario actualizar los perfiles de seguimiento de mano personalizados para que funcionen correctamente con la versión 2.1.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-343">Custom hand tracking profiles may need to be updated to work correctly with version 2.1.0.</span></span>

>[!NOTE]
><span data-ttu-id="daa05-344">Este cambio no es compatible con versiones anteriores de la versión 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-344">This change is not backwards compatible with version 2.0.0.</span></span>

<span data-ttu-id="daa05-345">**Perfil de simulación de entrada**</span><span class="sxs-lookup"><span data-stu-id="daa05-345">**Input simulation profile**</span></span>

<span data-ttu-id="daa05-346">Se ha actualizado el sistema de simulación de entrada, que cambia algunos valores en el perfil de simulación de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-346">The input simulation system has been upgraded, which changes a few settings in the input simulation profile.</span></span> <span data-ttu-id="daa05-347">Algunos cambios no se pueden migrar automáticamente y los usuarios pueden encontrar que los perfiles usan valores predeterminados.</span><span class="sxs-lookup"><span data-stu-id="daa05-347">Some changes can not be migrated automatically and users may find that profiles are using default values.</span></span>

1. <span data-ttu-id="daa05-348">Todos los enlaces keycode y de botón del mouse del perfil se han reemplazado por una estructura genérica, que almacena el tipo de enlace (clave o mouse), así como el código de enlace real (KeyCode o número de botón del `KeyBinding` mouse respectivamente).</span><span class="sxs-lookup"><span data-stu-id="daa05-348">All KeyCode and mouse button bindings in the profile have been replaced with a generic `KeyBinding` struct, which stores the type of binding (key or mouse) as well as the actual binding code (KeyCode or mouse button number respectively).</span></span> <span data-ttu-id="daa05-349">La estructura tiene su propio inspector, que permite la visualización unificada y ofrece una herramienta de "enlace automático" para establecer rápidamente los enlaces de teclado presionando la clave correspondiente en lugar de seleccionarla en una lista desplegable enorme.</span><span class="sxs-lookup"><span data-stu-id="daa05-349">The struct has its own inspector, which allows unified display and offers an "auto-bind" tool to quickly set key bindings by pressing the respective key instead of selecting from a huge dropdown list.</span></span>

    - <span data-ttu-id="daa05-350">FastControlKey</span><span class="sxs-lookup"><span data-stu-id="daa05-350">FastControlKey</span></span>
    - <span data-ttu-id="daa05-351">ToggleLeftHandKey</span><span class="sxs-lookup"><span data-stu-id="daa05-351">ToggleLeftHandKey</span></span>
    - <span data-ttu-id="daa05-352">ToggleRightHandKey</span><span class="sxs-lookup"><span data-stu-id="daa05-352">ToggleRightHandKey</span></span>
    - <span data-ttu-id="daa05-353">LeftHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="daa05-353">LeftHandManipulationKey</span></span>
    - <span data-ttu-id="daa05-354">RightHandManipulationKey</span><span class="sxs-lookup"><span data-stu-id="daa05-354">RightHandManipulationKey</span></span>

1. <span data-ttu-id="daa05-355">`MouseLookToggle` anteriormente se incluía en la `MouseLookButton` enumeración como `InputSimulationMouseButton.Focused` , ahora es una opción independiente.</span><span class="sxs-lookup"><span data-stu-id="daa05-355">`MouseLookToggle` was previously included in the `MouseLookButton` enum as `InputSimulationMouseButton.Focused`, it is now a separate option.</span></span> <span data-ttu-id="daa05-356">Cuando esté habilitada, la cámara seguirá girando con el mouse después de soltar el botón hasta que se presione la tecla de escape.</span><span class="sxs-lookup"><span data-stu-id="daa05-356">When enabled, the camera will keep rotating with the mouse after releasing the button, until the escape key is pressed.</span></span>
1. <span data-ttu-id="daa05-357">`HandDepthMultiplier` El valor predeterminado se ha reducido de 0,1 a 0,03 para dar cabida a algunos cambios en la simulación de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-357">`HandDepthMultiplier` default value has been lowered from 0.1 to 0.03 to accommodate some changes to the input simulation.</span></span> <span data-ttu-id="daa05-358">Si la cámara se mueve demasiado rápido al desplazarse, intente reducir este valor.</span><span class="sxs-lookup"><span data-stu-id="daa05-358">If the camera moves too fast when scrolling, try lowering this value.</span></span>
1. <span data-ttu-id="daa05-359">Se han quitado las teclas para girar las manos, la rotación de las manos ahora también se controla mediante el mouse.</span><span class="sxs-lookup"><span data-stu-id="daa05-359">Keys for rotating hands have been removed, hand rotation is now controlled by the mouse as well.</span></span> <span data-ttu-id="daa05-360">Mantener presionado (Ctrl) junto con la tecla de manipulación de la mano `HandRotateButton` izquierda/derecha (LShift/Espacio) habilitará la rotación de la mano.</span><span class="sxs-lookup"><span data-stu-id="daa05-360">Holding `HandRotateButton` (Ctrl) together with the left/right hand manipulation key (LShift/Space) will enable hand rotation.</span></span>
1. <span data-ttu-id="daa05-361">Se ha introducido un nuevo eje "UpDown" en la lista de ejes de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-361">A new axis "UpDown" has been introduced to the input axis list.</span></span> <span data-ttu-id="daa05-362">Esto controla el movimiento de la cámara en vertical y tiene como valor predeterminado las teclas Q/E, así como los botones del desencadenador del controlador.</span><span class="sxs-lookup"><span data-stu-id="daa05-362">This controls camera movement in the vertical and defaults to Q/E keys as well as the controller trigger buttons.</span></span>

<span data-ttu-id="daa05-363">Para obtener más información sobre estos cambios, consulte el artículo sobre [el servicio de simulación de](../features/input-simulation/input-simulation-service.md) entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-363">For more information on these changes, please see the [input simulation service](../features/input-simulation/input-simulation-service.md) article.</span></span>

<span data-ttu-id="daa05-364">**Perfil del proveedor de datos del mouse**</span><span class="sxs-lookup"><span data-stu-id="daa05-364">**Mouse data provider profile**</span></span>

<span data-ttu-id="daa05-365">El perfil del proveedor de datos del mouse se ha actualizado para exponer las propiedades `CursorSpeed` y `WheelSpeed` nuevas.</span><span class="sxs-lookup"><span data-stu-id="daa05-365">The mouse data provider profile has been updated to expose the new `CursorSpeed` and `WheelSpeed` properties.</span></span> <span data-ttu-id="daa05-366">Los perfiles personalizados existentes tendrán automáticamente valores predeterminados proporcionados.</span><span class="sxs-lookup"><span data-stu-id="daa05-366">Existing custom profiles will automatically have default values provided.</span></span> <span data-ttu-id="daa05-367">Cuando se guarde el perfil, estos nuevos valores se conservarán.</span><span class="sxs-lookup"><span data-stu-id="daa05-367">When the profile is saved, these new values will be persisted.</span></span>

<span data-ttu-id="daa05-368">**Perfil de asignación de controlador**</span><span class="sxs-lookup"><span data-stu-id="daa05-368">**Controller mapping profile**</span></span>

<span data-ttu-id="daa05-369">Algunos ejes y tipos de entrada se han actualizado en la versión 2.1.0, especialmente en torno a la plataforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="daa05-369">Some axes and input types have been updated in 2.1.0, especially around the OpenVR platform.</span></span> <span data-ttu-id="daa05-370">Asegúrese de seleccionar **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** al actualizar.</span><span class="sxs-lookup"><span data-stu-id="daa05-370">Please be sure to select **MixedRealityToolkit -> Utilities -> Update -> Controller Mapping Profiles** when upgrading.</span></span> <span data-ttu-id="daa05-371">Esto actualizará los perfiles de asignación de controladores personalizados con los ejes y los datos actualizados, al tiempo que deja intactas las acciones de entrada asignadas de forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="daa05-371">This will update any custom Controller Mapping Profiles with the updated axes and data, while leaving your custom-assigned input actions intact.</span></span>

## <a name="updating-rc2-to-200"></a><span data-ttu-id="daa05-372">Actualización de RC2 a 2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-372">Updating RC2 to 2.0.0</span></span>

<span data-ttu-id="daa05-373">Entre las versiones RC2 y 2.0.0 del kit de herramientas de Microsoft Mixed Reality, se realizaron cambios que pueden afectar a los proyectos existentes.</span><span class="sxs-lookup"><span data-stu-id="daa05-373">Between the RC2 and 2.0.0 releases of the Microsoft Mixed Reality Toolkit, changes were made that may impact existing projects.</span></span> <span data-ttu-id="daa05-374">En este documento se describen esos cambios y cómo actualizar los proyectos a la versión 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-374">This document describes those changes and how to update projects to the 2.0.0 release.</span></span>

- [<span data-ttu-id="daa05-375">Cambios en la API</span><span class="sxs-lookup"><span data-stu-id="daa05-375">API changes</span></span>](#api-changes-in-200)
- [<span data-ttu-id="daa05-376">Cambios en el nombre del ensamblado</span><span class="sxs-lookup"><span data-stu-id="daa05-376">Assembly name changes</span></span>](#assembly-name-changes-in-200)

### <a name="api-changes-in-200"></a><span data-ttu-id="daa05-377">Cambios de API en la versión 2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-377">API changes in 2.0.0</span></span>

<span data-ttu-id="daa05-378">Desde el lanzamiento de RC2, ha habido una serie de cambios en la API, incluidos algunos que pueden interrumpir los proyectos existentes.</span><span class="sxs-lookup"><span data-stu-id="daa05-378">Since the release of RC2, there have been a number of API changes including some that may break existing projects.</span></span> <span data-ttu-id="daa05-379">En las secciones siguientes se describen los cambios que se han producido entre las versiones RC2 y 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-379">The following sections describe the changes that have occurred between the RC2 and 2.0.0 releases.</span></span>

<span data-ttu-id="daa05-380">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="daa05-380">**MixedRealityToolkit**</span></span>

<span data-ttu-id="daa05-381">Las siguientes propiedades públicas del objeto MixedRealityToolkit han quedado en desuso.</span><span class="sxs-lookup"><span data-stu-id="daa05-381">The following public properties on the MixedRealityToolkit object have been deprecated.</span></span>

- <span data-ttu-id="daa05-382">`RegisteredMixedRealityServices` ya no contiene la colección de servicios de extensiones registrados y proveedores de datos.</span><span class="sxs-lookup"><span data-stu-id="daa05-382">`RegisteredMixedRealityServices` no longer contains the collection of registered extensions services and data providers.</span></span>

<span data-ttu-id="daa05-383">Para acceder a los servicios de extensión, use `MixedRealityServiceRegistry.TryGetService<T>` .</span><span class="sxs-lookup"><span data-stu-id="daa05-383">To access extension services, use `MixedRealityServiceRegistry.TryGetService<T>`.</span></span> <span data-ttu-id="daa05-384">Para acceder a los proveedores de datos, convierte la instancia de servicio en [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) y usa `GetDataProvider<T>` .</span><span class="sxs-lookup"><span data-stu-id="daa05-384">To access data providers, cast the service instance to [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) and use `GetDataProvider<T>`.</span></span>

<span data-ttu-id="daa05-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) o en su lugar para las siguientes propiedades en [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) desuso</span><span class="sxs-lookup"><span data-stu-id="daa05-385">Use [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) or [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) instead for the following deprecated properties</span></span>

- `ActiveSystems`
- `InputSystem`
- `BoundarySystem`
- `CameraSystem`
- `SpatialAwarenessSystem`
- `TeleportSystem`
- `DiagnosticsSystem`
- `SceneSystem`

<span data-ttu-id="daa05-386">**CoreServices**</span><span class="sxs-lookup"><span data-stu-id="daa05-386">**CoreServices**</span></span>

<span data-ttu-id="daa05-387">La [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) clase es el reemplazo de los accessors del sistema estático (por ejemplo, BoundarySystem) que se encuentran en el objeto `MixedRealityToolkit` .</span><span class="sxs-lookup"><span data-stu-id="daa05-387">The [`CoreServices`](xref:Microsoft.MixedReality.Toolkit.CoreServices) class is the replacement for the static system accessors (ex: BoundarySystem) found in the `MixedRealityToolkit` object.</span></span>

>[!IMPORTANT]
><span data-ttu-id="daa05-388">Los accessors del sistema han quedado en desuso en la versión 2.0.0 y se quitarán en una versión futura `MixedRealityToolkit` de MRTK.</span><span class="sxs-lookup"><span data-stu-id="daa05-388">The `MixedRealityToolkit` system accessors have been deprecated in version 2.0.0 and will be removed in a future release of the MRTK.</span></span>

<span data-ttu-id="daa05-389">En el ejemplo de código siguiente se muestra el patrón antiguo y el nuevo.</span><span class="sxs-lookup"><span data-stu-id="daa05-389">The following code example illustrates the old and the new pattern.</span></span>

``` c#
// Old
GameObject playAreaVisualization = MixedRealityToolkit.BoundarySystem?.GetPlayAreaVisualization();

// New
GameObject playAreaVisualization = CoreServices.BoundarySystem?.GetPlayAreaVisualization();
```

<span data-ttu-id="daa05-390">El uso de la nueva clase CoreSystem garantizará que el código de la aplicación no necesite actualizarse si cambia la aplicación para usar un registrador de servicios diferente (por ejemplo, uno de los administradores de servicios experimentales).</span><span class="sxs-lookup"><span data-stu-id="daa05-390">Using the new CoreSystem class will ensure that your application code will not need updating if you change the application to use a different service registrar (ex: one of the experimental service managers).</span></span>

<span data-ttu-id="daa05-391">**IMixedRealityRaycastProvider**</span><span class="sxs-lookup"><span data-stu-id="daa05-391">**IMixedRealityRaycastProvider**</span></span>

<span data-ttu-id="daa05-392">Con la adición de IMixedRealityRaycastProvider, se cambió el perfil de configuración del sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-392">With the addition of the IMixedRealityRaycastProvider, the input system configuration profile was changed.</span></span> <span data-ttu-id="daa05-393">Si tiene un perfil personalizado, puede recibir los errores de la siguiente imagen al ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="daa05-393">If you have a custom profile, you may receive the errors in the following image when you run your application.</span></span>

![Selección del proveedor de Raycast 1](../release-notes/images/UnableToRegisterRaycastProvider.png)

<span data-ttu-id="daa05-395">Para corregirlos, agregue una instancia de IMixedRealityRaycastProvider al perfil del sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-395">To fix these, please add an IMixedRealityRaycastProvider instance to your input system profile.</span></span>

![Selección del proveedor de Raycast 2](../release-notes/images/SelectRaycastProvider.png)

<span data-ttu-id="daa05-397">**Sistema de eventos**</span><span class="sxs-lookup"><span data-stu-id="daa05-397">**Event System**</span></span>

- <span data-ttu-id="daa05-398">Los `IMixedRealityEventSystem` métodos de API `Register` `Unregister` antiguos y se han marcado como obsoletos.</span><span class="sxs-lookup"><span data-stu-id="daa05-398">The `IMixedRealityEventSystem` old API methods `Register` and `Unregister` have been marked as obsolete.</span></span> <span data-ttu-id="daa05-399">Se conservan por compatibilidad con versiones anteriores.</span><span class="sxs-lookup"><span data-stu-id="daa05-399">They are preserved for backwards compatibility.</span></span>
- <span data-ttu-id="daa05-400">`InputSystemGlobalListener` se ha marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="daa05-400">`InputSystemGlobalListener` has been marked as obsolete.</span></span> <span data-ttu-id="daa05-401">Su funcionalidad no ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="daa05-401">Its functionality has not changed.</span></span>
- <span data-ttu-id="daa05-402">`BaseInputHandler` La clase base se ha cambiado de `InputSystemGlobalListener` a `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="daa05-402">`BaseInputHandler` base class has been changed from `InputSystemGlobalListener` to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="daa05-403">Se trata de un cambio importante para cualquier descendiente de `BaseInputHandler` .</span><span class="sxs-lookup"><span data-stu-id="daa05-403">This is a breaking change for any descendants of `BaseInputHandler`.</span></span>

<span data-ttu-id="daa05-404">**_Motivación detrás del cambio_**</span><span class="sxs-lookup"><span data-stu-id="daa05-404">**_Motivation behind the change_**</span></span>

<span data-ttu-id="daa05-405">La API anterior del sistema de eventos y podría causar varios problemas en tiempo de `Register` `Unregister` ejecución, siendo principalmente:</span><span class="sxs-lookup"><span data-stu-id="daa05-405">The old event system API `Register` and `Unregister` could potentially cause multiple issues in runtime, main being:</span></span>

- <span data-ttu-id="daa05-406">Si un componente se registra para eventos globales, recibiría eventos de entrada globales de *todos los* tipos.</span><span class="sxs-lookup"><span data-stu-id="daa05-406">If a component registers for global events, it would receive global input events of *all* types.</span></span>
- <span data-ttu-id="daa05-407">Si uno de los componentes de un objeto se registra para eventos de entrada globales, todos los componentes de este objeto recibirán eventos de entrada globales de *todos los* tipos.</span><span class="sxs-lookup"><span data-stu-id="daa05-407">If one of the components on an object registers for global input events, all components on this object will receive global input events of *all* types.</span></span>
- <span data-ttu-id="daa05-408">Si dos componentes del mismo objeto se registran en eventos globales y, a continuación, uno está deshabilitado en tiempo de ejecución, el segundo deja de recibir eventos globales.</span><span class="sxs-lookup"><span data-stu-id="daa05-408">If two components on the same object register to global events, and then one is disabled in runtime, the second one stops receiving global events.</span></span>

<span data-ttu-id="daa05-409">Nueva API `RegisterHandler` y `UnregisterHandler` :</span><span class="sxs-lookup"><span data-stu-id="daa05-409">New API `RegisterHandler` and `UnregisterHandler`:</span></span>

- <span data-ttu-id="daa05-410">Proporciona un control explícito y granular sobre qué eventos de entrada se deben escuchar globalmente y cuáles deben centrarse.</span><span class="sxs-lookup"><span data-stu-id="daa05-410">Provides an explicit and granular control over which input events should be listened to globally and which should be focused-based.</span></span>
- <span data-ttu-id="daa05-411">Permite que varios componentes del mismo objeto escuche eventos globales de forma independiente entre sí.</span><span class="sxs-lookup"><span data-stu-id="daa05-411">Allows multiple components on the same object to listen to global events independently on each other.</span></span>

<span data-ttu-id="daa05-412">**_Migración_**</span><span class="sxs-lookup"><span data-stu-id="daa05-412">**_How to migrate_**</span></span>

- <span data-ttu-id="daa05-413">Si ha llamado a `Register` / `Unregister` la API directamente antes, reemplace estas llamadas por llamadas a `RegisterHandler` / `UnregisterHandler` .</span><span class="sxs-lookup"><span data-stu-id="daa05-413">If you have been calling `Register`/`Unregister` API directly before, replace these calls with calls to `RegisterHandler`/`UnregisterHandler`.</span></span> <span data-ttu-id="daa05-414">Use interfaces de controlador que implemente como parámetros genéricos.</span><span class="sxs-lookup"><span data-stu-id="daa05-414">Use handler interfaces you implement as generic parameters.</span></span> <span data-ttu-id="daa05-415">Si implementa varias interfaces y varias de ellas escuchan eventos de entrada globales, llame `RegisterHandler` a varias veces.</span><span class="sxs-lookup"><span data-stu-id="daa05-415">If you implement multiple interfaces, and several of them listen to global input events, call `RegisterHandler` multiple times.</span></span>
- <span data-ttu-id="daa05-416">Si ha heredado de , cambie `InputSystemGlobalListener` la herencia a `InputSystemGlobalHandlerListener` .</span><span class="sxs-lookup"><span data-stu-id="daa05-416">If you have been inheriting from `InputSystemGlobalListener`, change inheritance to `InputSystemGlobalHandlerListener`.</span></span> <span data-ttu-id="daa05-417">Implemente `RegisterHandlers` `UnregisterHandlers` métodos abstractos y .</span><span class="sxs-lookup"><span data-stu-id="daa05-417">Implement `RegisterHandlers` and `UnregisterHandlers` abstract methods.</span></span> <span data-ttu-id="daa05-418">En la llamada de implementación ( ) para registrarse en todas las interfaces de controlador para las `inputSystem.RegisterHandler` que desea escuchar eventos `inputSystem.UnregisterHandler` globales.</span><span class="sxs-lookup"><span data-stu-id="daa05-418">In the implementation call `inputSystem.RegisterHandler` (`inputSystem.UnregisterHandler`) to register on all handler interfaces you want to listen global events for.</span></span>
- <span data-ttu-id="daa05-419">Si ha heredado de `BaseInputHandler` , implemente los `RegisterHandlers` métodos `UnregisterHandlers` abstractos y (igual que para `InputSystemGlobalListener` ).</span><span class="sxs-lookup"><span data-stu-id="daa05-419">If you have been inheriting from `BaseInputHandler`, implement `RegisterHandlers` and `UnregisterHandlers` abstract methods (same as for `InputSystemGlobalListener`).</span></span>

<span data-ttu-id="daa05-420">**_Ejemplos de migración_**</span><span class="sxs-lookup"><span data-stu-id="daa05-420">**_Examples of migration_**</span></span>

```c#
// Old
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.Register(gameObject);
    }

    private void OnDisable()
    {
        InputSystem?.Unregister(gameObject);
    }
}

// Migrated
class SampleHandler : MonoBehaviour, IMixedRealitySourceStateHandler, IMixedRealityHandJointHandler
{
    private void OnEnable()
    {
        InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }
}
```

```c#
// Old
class SampleHandler2 : InputSystemGlobalListener, IMixedRealitySpeechHandler
{
}

// Migrated
class SampleHandler2 : InputSystemGlobalHandlerListener, IMixedRealitySpeechHandler
{
    private void RegisterHandlers()
    {
        InputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
    }

    private void UnregisterHandlers()
    {
        InputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
    }
}

// Alternative migration
class SampleHandler2 : MonoBehaviour, IMixedRealitySpeechHandler
{
    private void OnEnable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.RegisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }

    private void OnDisable()
    {
        IMixedRealityInputSystem inputSystem;
        if (MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
        {
            inputSystem?.UnregisterHandler<IMixedRealitySpeechHandler>(this);
        }
    }
}
```

<span data-ttu-id="daa05-421">**Reconocimiento espacial**</span><span class="sxs-lookup"><span data-stu-id="daa05-421">**Spatial Awareness**</span></span>

<span data-ttu-id="daa05-422">Las interfaces IMixedRealitySpatialAwarenessSystem e IMixedRealitySpatialAwarenessObserver han realizado varios cambios importantes, como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="daa05-422">The IMixedRealitySpatialAwarenessSystem and IMixedRealitySpatialAwarenessObserver interfaces have taken multiple breaking changes as described below.</span></span>

<span data-ttu-id="daa05-423">**_Cambios_**</span><span class="sxs-lookup"><span data-stu-id="daa05-423">**_Changes_**</span></span>

<span data-ttu-id="daa05-424">Se ha cambiado el nombre de los métodos siguientes para describir mejor su uso.</span><span class="sxs-lookup"><span data-stu-id="daa05-424">The following method(s) have been renamed to better describe their usage.</span></span>

- <span data-ttu-id="daa05-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` se ha cambiado el nombre a `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` para aclarar su uso.</span><span class="sxs-lookup"><span data-stu-id="daa05-425">`IMixedRealitySpatialAwarenessSystem.CreateSpatialObjectParent` has been renamed to `IMixedRealitySpatialAwarenessSystem.CreateSpatialAwarenessObservationParent` to clarify its usage.</span></span>

<span data-ttu-id="daa05-426">**_Adiciones_**</span><span class="sxs-lookup"><span data-stu-id="daa05-426">**_Additions_**</span></span>

<span data-ttu-id="daa05-427">En función de los comentarios de los clientes, se ha agregado soporte técnico para la eliminación sencilla de los datos de reconocimiento espacial observados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="daa05-427">Based on customer feedback, support for easy removal of previously observed spatial awareness data has been added.</span></span>

- `IMixedRealitySpatialAwarenessSystem.ClearObservations()`
- `IMixedRealitySpatialAwarenessSystem.ClearObservations<T>(string name)`
- `IMixedRealitySpatialAwarenessObserver.ClearObservations()`

<span data-ttu-id="daa05-428">**Solucionadores**</span><span class="sxs-lookup"><span data-stu-id="daa05-428">**Solvers**</span></span>

<span data-ttu-id="daa05-429">Algunos componentes del solucionador y la clase de administrador SolverHandler han cambiado para corregir varios errores y para un uso más intuitivo.</span><span class="sxs-lookup"><span data-stu-id="daa05-429">Some solver components and the SolverHandler manager class has changed to fix various bugs and for more intuitive usage.</span></span>

<span data-ttu-id="daa05-430">**_SolverHandler_**</span><span class="sxs-lookup"><span data-stu-id="daa05-430">**_SolverHandler_**</span></span>

- <span data-ttu-id="daa05-431">La clase ya no se extiende desde `ControllerFinder`</span><span class="sxs-lookup"><span data-stu-id="daa05-431">Class no longer extends from `ControllerFinder`</span></span>
- <span data-ttu-id="daa05-432">`TrackedObjectToReference` propiedad pública en desuso y se ha cambiado el nombre a `TrackedTargetType`</span><span class="sxs-lookup"><span data-stu-id="daa05-432">`TrackedObjectToReference` public property deprecated and has been renamed to `TrackedTargetType`</span></span>
- <span data-ttu-id="daa05-433">`TrackedObjectType` en desuso a & de controlador derecho.</span><span class="sxs-lookup"><span data-stu-id="daa05-433">`TrackedObjectType` deprecates left & right controller values.</span></span> <span data-ttu-id="daa05-434">En su lugar, use los valores o y actualice la nueva propiedad para limitar el seguimiento al controlador izquierdo `MotionController` o `HandJoint` `TrackedHandedness` derecho.</span><span class="sxs-lookup"><span data-stu-id="daa05-434">Instead use `MotionController` or `HandJoint` values and update new `TrackedHandedness` property to limit tracking to left or right controller</span></span>

<span data-ttu-id="daa05-435">**_InBetween_**</span><span class="sxs-lookup"><span data-stu-id="daa05-435">**_InBetween_**</span></span>

- <span data-ttu-id="daa05-436">`TrackedObjectForSecondTransform` propiedad pública en desuso y se ha cambiado el nombre a `SecondTrackedObjectType`</span><span class="sxs-lookup"><span data-stu-id="daa05-436">`TrackedObjectForSecondTransform` public property deprecated and has been renamed to `SecondTrackedObjectType`</span></span>
- <span data-ttu-id="daa05-437">`AttachSecondTransformToNewTrackedObject()` se ha quitado.</span><span class="sxs-lookup"><span data-stu-id="daa05-437">`AttachSecondTransformToNewTrackedObject()` has been removed.</span></span> <span data-ttu-id="daa05-438">Para actualizar el solucionador, modifique las propiedades públicas (es decir,</span><span class="sxs-lookup"><span data-stu-id="daa05-438">To update the solver, modify the public properties (i.e</span></span> <span data-ttu-id="daa05-439">`SecondTrackedObjectType`)</span><span class="sxs-lookup"><span data-stu-id="daa05-439">`SecondTrackedObjectType`)</span></span>

<span data-ttu-id="daa05-440">**_Surface Surface (Surface )Surface (Surface )Surface (Surface_**</span><span class="sxs-lookup"><span data-stu-id="daa05-440">**_SurfaceMagnetism_**</span></span>

- <span data-ttu-id="daa05-441">`MaxDistance` propiedad pública en desuso y se ha cambiado el nombre a `MaxRaycastDistance`</span><span class="sxs-lookup"><span data-stu-id="daa05-441">`MaxDistance` public property deprecated and has been renamed to `MaxRaycastDistance`</span></span>
- <span data-ttu-id="daa05-442">`CloseDistance` propiedad pública en desuso y se ha cambiado el nombre a `ClosestDistance`</span><span class="sxs-lookup"><span data-stu-id="daa05-442">`CloseDistance` public property deprecated and has been renamed to `ClosestDistance`</span></span>
- <span data-ttu-id="daa05-443">El valor predeterminado `RaycastDirectionMode` de es ahora qué raycasts en la dirección de la transformación de destino con seguimiento `TrackedTargetForward` hacia delante</span><span class="sxs-lookup"><span data-stu-id="daa05-443">Default value for `RaycastDirectionMode` is now `TrackedTargetForward` which raycasts in the direction of the tracked target transform forward</span></span>
- <span data-ttu-id="daa05-444">`OrientationMode` Se ha cambiado el nombre de los valores de enumeración y , `Vertical` `Full` a y `TrackedTarget` `SurfaceNormal` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="daa05-444">`OrientationMode` enum values, `Vertical` and `Full`, have been renamed to `TrackedTarget` and `SurfaceNormal` respectively</span></span>
- <span data-ttu-id="daa05-445">`KeepOrientationVertical` se ha agregado la propiedad public para controlar si la orientación de GameObject asociada sigue siendo vertical.</span><span class="sxs-lookup"><span data-stu-id="daa05-445">`KeepOrientationVertical` public property has been added to control whether orientation of associated GameObject remains vertical</span></span>

<span data-ttu-id="daa05-446">**Botones**</span><span class="sxs-lookup"><span data-stu-id="daa05-446">**Buttons**</span></span>

- <span data-ttu-id="daa05-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) ahora tiene `DistanceSpaceMode` la propiedad establecida en como valor `Local` predeterminado.</span><span class="sxs-lookup"><span data-stu-id="daa05-447">[`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) now has `DistanceSpaceMode` property set to `Local` as default.</span></span> <span data-ttu-id="daa05-448">Esto permite escalar los botones mientras se pueden presionar.</span><span class="sxs-lookup"><span data-stu-id="daa05-448">This allows buttons to be scaled while still be pressable</span></span>

<span data-ttu-id="daa05-449">**Esfera de recorte**</span><span class="sxs-lookup"><span data-stu-id="daa05-449">**Clipping Sphere**</span></span>

<span data-ttu-id="daa05-450">La interfaz ClippingSphere ha cambiado para reflejar las API que se encuentran en ClippingBox y ClippingPlane.</span><span class="sxs-lookup"><span data-stu-id="daa05-450">The ClippingSphere interface has changed to mirror the APIs found in the ClippingBox and ClippingPlane.</span></span>

<span data-ttu-id="daa05-451">La propiedad Radius de ClippingSphere ahora se calcula implícitamente en función de la escala de transformación.</span><span class="sxs-lookup"><span data-stu-id="daa05-451">The ClippingSphere's Radius property is now implicitly calculated based on the transform scale.</span></span> <span data-ttu-id="daa05-452">Antes de que los desarrolladores tengan que especificar el radio de ClippingSphere en el inspector.</span><span class="sxs-lookup"><span data-stu-id="daa05-452">Before developers would have to specify the radius of the ClippingSphere in the inspector.</span></span> <span data-ttu-id="daa05-453">Si desea cambiar el radio, solo tiene que actualizar la escala de transformación de la transformación como lo haría normalmente.</span><span class="sxs-lookup"><span data-stu-id="daa05-453">If you want to change the radius, just update the transform scale of the transform as you normally would.</span></span>

<span data-ttu-id="daa05-454">**NearInteractionTouchable y PokePointer**</span><span class="sxs-lookup"><span data-stu-id="daa05-454">**NearInteractionTouchable and PokePointer**</span></span>

- <span data-ttu-id="daa05-455">NearInteractionTouchable ya no controla el lienzo de la interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-455">NearInteractionTouchable does not handle Unity UI canvas touching any longer.</span></span> <span data-ttu-id="daa05-456">La clase NearInteractionTouchableUnityUI debe usarse ahora para los elementos táctiles de la interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="daa05-456">The NearInteractionTouchableUnityUI class must be used for Unity UI touchables now.</span></span>
- <span data-ttu-id="daa05-457">ColliderNearInteractionTouchable es la nueva clase base para los dispositivos táctiles basados en colisiondores, es decir, todos los que se pueden tocar excepto NearInteractionTouchableUnityUI.</span><span class="sxs-lookup"><span data-stu-id="daa05-457">ColliderNearInteractionTouchable is the new base class for touchables based on colliders, i.e. every touchable except NearInteractionTouchableUnityUI.</span></span>
- <span data-ttu-id="daa05-458">BaseNearInteractionTouchable.DistFront se ha movido y se ha cambiado el nombre a Contrapunto.TouchableDistance Esta es la distancia y con la que el usuario puede interactuar con los objetos táctiles.</span><span class="sxs-lookup"><span data-stu-id="daa05-458">BaseNearInteractionTouchable.DistFront has been moved and renamed to PokePointer.TouchableDistance This is the distance and which the PokePointer can interact with touchables.</span></span> <span data-ttu-id="daa05-459">Anteriormente, cada elemento táctil tenía su propia distancia máxima de interacción, pero ahora se define en el elemento Depointer, lo que permite una mejor optimización.</span><span class="sxs-lookup"><span data-stu-id="daa05-459">Previously each touchable had its own maximum interaction distance, but now this is defined in the PokePointer which allows better optimization.</span></span>
- <span data-ttu-id="daa05-460">Se ha cambiado el nombre de BaseNearInteractionTouchable.DistBack aThreshold. Esto deja claro que La propiedad DebounceThreshold es el homólogo de DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="daa05-460">BaseNearInteractionTouchable.DistBack has been renamed to PokeThreshold This makes it clear that PokeThreshold is the counterpart to DebounceThreshold.</span></span> <span data-ttu-id="daa05-461">Se activa un control táctil cuando se cruza el control DebounceThreshold y se libera cuando se cruza DebounceThreshold.</span><span class="sxs-lookup"><span data-stu-id="daa05-461">A touchable is activated when the PokeThreshold is crossed, and released when DebounceThreshold is crossed.</span></span>

<span data-ttu-id="daa05-462">**ReadOnlyAttribute**</span><span class="sxs-lookup"><span data-stu-id="daa05-462">**ReadOnlyAttribute**</span></span>

<span data-ttu-id="daa05-463">El `Microsoft.MixedReality.Toolkit` espacio de nombres se ha agregado a , y `ReadOnlyAttribute` `BeginReadOnlyGroupAttribute` `EndReadOnlyGroupAttribute` .</span><span class="sxs-lookup"><span data-stu-id="daa05-463">The `Microsoft.MixedReality.Toolkit` namespace has been added to `ReadOnlyAttribute`, `BeginReadOnlyGroupAttribute`, and `EndReadOnlyGroupAttribute`.</span></span>

<span data-ttu-id="daa05-464">**PointerClickHandler**</span><span class="sxs-lookup"><span data-stu-id="daa05-464">**PointerClickHandler**</span></span>

<span data-ttu-id="daa05-465">La clase `PointerClickHandler` está desusada.</span><span class="sxs-lookup"><span data-stu-id="daa05-465">The `PointerClickHandler` class has been deprecated.</span></span> <span data-ttu-id="daa05-466">Debe `PointerHandler` usarse en su lugar, proporciona la misma funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="daa05-466">The `PointerHandler` should be used instead, it provides the same functionality.</span></span>

<span data-ttu-id="daa05-467">**Compatibilidad con el clicker de HoloLens**</span><span class="sxs-lookup"><span data-stu-id="daa05-467">**HoloLens clicker support**</span></span>

<span data-ttu-id="daa05-468">Las asignaciones del controlador del clicker de HoloLens han cambiado de ser sin control [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) a ser un control sin [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand) control.</span><span class="sxs-lookup"><span data-stu-id="daa05-468">The HoloLens clicker's controller mappings have changed from being an unhanded [`WindowsMixedRealityController`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityController) to being an unhanded [`WindowsMixedRealityGGVHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityGGVHand).</span></span> <span data-ttu-id="daa05-469">Para tener esto en cuenta, se ejecutará un actualizador automático la primera vez que abra el perfil de ControllerMapping.</span><span class="sxs-lookup"><span data-stu-id="daa05-469">To account for this, an automatic updater will run the first time you open your ControllerMapping profile.</span></span> <span data-ttu-id="daa05-470">Abra los perfiles personalizados al menos una vez después de actualizar a 2.0.0 para desencadenar este paso de migración único.</span><span class="sxs-lookup"><span data-stu-id="daa05-470">Please open any custom profiles at least once after upgrading to 2.0.0 in order to trigger this one-time migration step.</span></span>

<span data-ttu-id="daa05-471">**InteractableHighlight**</span><span class="sxs-lookup"><span data-stu-id="daa05-471">**InteractableHighlight**</span></span>

<span data-ttu-id="daa05-472">La clase `InteractableHighlight` está desusada.</span><span class="sxs-lookup"><span data-stu-id="daa05-472">The `InteractableHighlight` class has been deprecated.</span></span> <span data-ttu-id="daa05-473">En `InteractableOnFocus` su `FocusInteractableStates` lugar, se deben usar la clase y el recurso.</span><span class="sxs-lookup"><span data-stu-id="daa05-473">The `InteractableOnFocus` class and `FocusInteractableStates` asset should be used instead.</span></span> <span data-ttu-id="daa05-474">Para crear un nuevo recurso para , haga clic con el botón derecho en la ventana del proyecto y seleccione Create Mixed Reality Toolkit Interactable Theme (Crear un tema `Theme` `InteractableOnFocus`   >    >  *interactuable*  >  del kit de herramientas).</span><span class="sxs-lookup"><span data-stu-id="daa05-474">To create a new `Theme` asset for the `InteractableOnFocus`, right click in the project window and select *Create* > *Mixed Reality Toolkit* > *Interactable* > *Theme*.</span></span>

<span data-ttu-id="daa05-475">**HandInteractionPanZoom**</span><span class="sxs-lookup"><span data-stu-id="daa05-475">**HandInteractionPanZoom**</span></span>

<span data-ttu-id="daa05-476">`HandInteractionPanZoom` se ha movido al espacio de nombres de la interfaz de usuario, ya que no era un componente de entrada.</span><span class="sxs-lookup"><span data-stu-id="daa05-476">`HandInteractionPanZoom` has been moved to the UI namespace as it was not an input component.</span></span> <span data-ttu-id="daa05-477">`HandPanEventData` también se ha movido a este espacio de nombres y se ha simplificado para que se corresponda con otros datos de eventos de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="daa05-477">`HandPanEventData` has also been moved into this namespace, and simplified to correspond with other UI event data.</span></span>

### <a name="assembly-name-changes-in-200"></a><span data-ttu-id="daa05-478">Cambios en el nombre del ensamblado en la versión 2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-478">Assembly name changes in 2.0.0</span></span>

<span data-ttu-id="daa05-479">En la versión 2.0.0, todos los nombres de ensamblado oficial de Mixed Reality Toolkit y sus archivos de definición de ensamblado asociados (.asmdef) se han actualizado para ajustarse al siguiente patrón.</span><span class="sxs-lookup"><span data-stu-id="daa05-479">In The 2.0.0 release, all of the official Mixed Reality Toolkit assembly names and their associated assembly definition (.asmdef) files have been updated to fit the following pattern.</span></span>

```c#
Microsoft.MixedReality.Toolkit[.<name>]
```

<span data-ttu-id="daa05-480">En algunos casos, se han combinado varios ensamblados para crear una mejor unidad de su contenido.</span><span class="sxs-lookup"><span data-stu-id="daa05-480">In some instances, multiple assemblies have been merged to create better unity of their contents.</span></span> <span data-ttu-id="daa05-481">Si el proyecto usa archivos .asmdef personalizados, es posible que deba actualizarse.</span><span class="sxs-lookup"><span data-stu-id="daa05-481">If your project uses custom .asmdef files, they may require updating.</span></span>

<span data-ttu-id="daa05-482">En las tablas siguientes se describe cómo se asignan los nombres de archivo RC2 .asmdef a la versión 2.0.0.</span><span class="sxs-lookup"><span data-stu-id="daa05-482">The following tables describe how the RC2 .asmdef file names map to the 2.0.0 release.</span></span> <span data-ttu-id="daa05-483">Todos los nombres de ensamblado coinciden con el nombre de archivo .asmdef.</span><span class="sxs-lookup"><span data-stu-id="daa05-483">All assembly names match the .asmdef file name.</span></span>

<span data-ttu-id="daa05-484">**MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="daa05-484">**MixedRealityToolkit**</span></span>

| <span data-ttu-id="daa05-485">RC2</span><span class="sxs-lookup"><span data-stu-id="daa05-485">RC2</span></span> | <span data-ttu-id="daa05-486">2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-486">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-487">MixedRealityToolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-487">MixedRealityToolkit.asmdef</span></span> | <span data-ttu-id="daa05-488">Microsoft.MixedReality.Toolkit.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-488">Microsoft.MixedReality.Toolkit.asmdef</span></span> |
| <span data-ttu-id="daa05-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-489">MixedRealityToolkit.Core.BuildAndDeploy.asmdef</span></span> | <span data-ttu-id="daa05-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-490">Microsoft.MixedReality.Toolkit.Editor.BuildAndDeploy.asmdef</span></span> |
| <span data-ttu-id="daa05-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-491">MixedRealityToolkit.Core.Definitions.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="daa05-492">Quitado, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-492">Removed, use Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="daa05-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-493">MixedRealityToolkit.Core.Extensions.EditorClassExtensions.asmdef</span></span> | <span data-ttu-id="daa05-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-494">Microsoft.MixedReality.Toolkit.Editor.ClassExtensions.asmdef</span></span>
| <span data-ttu-id="daa05-495">MixedRealityToolkit.Core.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-495">MixedRealityToolkit.Core.Inspectors.asmdef</span></span> | <span data-ttu-id="daa05-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-496">Microsoft.MixedReality.Toolkit.Editor.Inspectors.asmdef</span></span> |
| <span data-ttu-id="daa05-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-497">MixedRealityToolkit.Core.Inspectors.ServiceInspectors.asmdef</span></span> | <span data-ttu-id="daa05-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-498">Microsoft.MixedReality.Toolkit.Editor.ServiceInspectors.asmdef</span></span> |
| <span data-ttu-id="daa05-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-499">MixedRealityToolkit.Core.UtilitiesAsync.asmdef</span></span> | <span data-ttu-id="daa05-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-500">Microsoft.MixedReality.Toolkit.Async.asmdef</span></span> |
| <span data-ttu-id="daa05-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-501">MixedRealityToolkit.Core.Utilities.Editor.asmdef</span></span> | <span data-ttu-id="daa05-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-502">Microsoft.MixedReality.Toolkit.Editor.Utilities.asmdef</span></span> |
| <span data-ttu-id="daa05-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-503">MixedRealityToolkit.Utilities.Gltf.asmdef</span></span> | <span data-ttu-id="daa05-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-504">Microsoft.MixedReality.Toolkit.Gltf.asmdef</span></span> |
| <span data-ttu-id="daa05-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-505">MixedRealityToolkit.Utilities.Gltf.Importers.asmdef</span></span> | <span data-ttu-id="daa05-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-506">Microsoft.MixedReality.Toolkit.Gltf.Importers.asmdef</span></span> |

<span data-ttu-id="daa05-507">**MixedRealityToolkit.Providers**</span><span class="sxs-lookup"><span data-stu-id="daa05-507">**MixedRealityToolkit.Providers**</span></span>

| <span data-ttu-id="daa05-508">RC2</span><span class="sxs-lookup"><span data-stu-id="daa05-508">RC2</span></span> | <span data-ttu-id="daa05-509">2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-509">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-510">MixedRealityToolkit.Providers.OpenVR.asmdef</span></span> | <span data-ttu-id="daa05-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-511">Microsoft.MixedReality.Toolkit.Providers.OpenVR.asmdef</span></span> |
| <span data-ttu-id="daa05-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-512">MixedRealityToolkit.Providers.WindowsMixedReality.asmdef</span></span> | <span data-ttu-id="daa05-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-513">Microsoft.MixedReality.Toolkit.Providers.WindowsMixedReality.asmdef</span></span> |
| <span data-ttu-id="daa05-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-514">MixedRealityToolkit.Providers.WindowsVoiceInput.asmdef</span></span> | <span data-ttu-id="daa05-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-515">Microsoft.MixedReality.Toolkit.Providers.WindowsVoiceInput.asmdef</span></span> |

<span data-ttu-id="daa05-516">**MixedRealityToolkit.Services**</span><span class="sxs-lookup"><span data-stu-id="daa05-516">**MixedRealityToolkit.Services**</span></span>

| <span data-ttu-id="daa05-517">RC2</span><span class="sxs-lookup"><span data-stu-id="daa05-517">RC2</span></span> | <span data-ttu-id="daa05-518">2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-518">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-519">MixedRealityToolkit.Services.BoundarySystem.asmdef</span></span> | <span data-ttu-id="daa05-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-520">Microsoft.MixedReality.Toolkit.Services.BoundarySystem.asmdef</span></span> |
| <span data-ttu-id="daa05-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-521">MixedRealityToolkit.Services.CameraSystem.asmdef</span></span> | <span data-ttu-id="daa05-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-522">Microsoft.MixedReality.Toolkit.Services.CameraSystem.asmdef</span></span> |
| <span data-ttu-id="daa05-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-523">MixedRealityToolkit.Services.DiagnosticsSystem.asmdef</span></span> | <span data-ttu-id="daa05-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-524">Microsoft.MixedReality.Toolkit.Services.DiagnosticsSystem.asmdef</span></span> |
| <span data-ttu-id="daa05-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-525">MixedRealityToolkit.Services.InputSimulation.asmdef</span></span> | <span data-ttu-id="daa05-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-526">Microsoft.MixedReality.Toolkit.Services.InputSimulation.asmdef</span></span> |
| <span data-ttu-id="daa05-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-527">MixedRealityToolkit.Services.InputSimulation.Editor.asmdef</span></span> | <span data-ttu-id="daa05-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-528">Microsoft.MixedReality.Toolkit.Services.InputSimulation.Editor.asmdef</span></span> |
| <span data-ttu-id="daa05-529">MixedRealityToolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-529">MixedRealityToolkit.Services.InputSystem.asmdef</span></span> | <span data-ttu-id="daa05-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-530">Microsoft.MixedReality.Toolkit.Services.InputSystem.asmdef</span></span> |
| <span data-ttu-id="daa05-531">MixedRealityToolkit.Services.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-531">MixedRealityToolkit.Services.Inspectors.asmdef</span></span> | <span data-ttu-id="daa05-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-532">Microsoft.MixedReality.Toolkit.Services.InputSystem.Editor.asmdef</span></span> |
| <span data-ttu-id="daa05-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-533">MixedRealityToolkit.Services.SceneSystem.asmdef</span></span> | <span data-ttu-id="daa05-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-534">Microsoft.MixedReality.Toolkit.Services.SceneSystem.asmdef</span></span> |
| <span data-ttu-id="daa05-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-535">MixedRealityToolkit.Services.SpatialAwarenessSystem.asmdef</span></span> | <span data-ttu-id="daa05-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-536">Microsoft.MixedReality.Toolkit.Services.SpatialAwarenessSystem.asmdef</span></span> |
| <span data-ttu-id="daa05-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-537">MixedRealityToolkit.Services.TeleportSystem.asmdef</span></span> | <span data-ttu-id="daa05-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-538">Microsoft.MixedReality.Toolkit.Services.TeleportSystem.asmdef</span></span> |

<span data-ttu-id="daa05-539">**MixedRealityToolkit.SDK**</span><span class="sxs-lookup"><span data-stu-id="daa05-539">**MixedRealityToolkit.SDK**</span></span>

| <span data-ttu-id="daa05-540">RC2</span><span class="sxs-lookup"><span data-stu-id="daa05-540">RC2</span></span> | <span data-ttu-id="daa05-541">2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-541">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-542">MixedRealityToolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-542">MixedRealityToolkit.SDK.asmdef</span></span> | <span data-ttu-id="daa05-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-543">Microsoft.MixedReality.Toolkit.SDK.asmdef</span></span> |
| <span data-ttu-id="daa05-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-544">MixedRealityToolkit.SDK.Inspectors.asmdef</span></span> | <span data-ttu-id="daa05-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-545">Microsoft.MixedReality.Toolkit.SDK.Inspectors.asmdef</span></span> |

<span data-ttu-id="daa05-546">**MixedRealityToolkit.Examples**</span><span class="sxs-lookup"><span data-stu-id="daa05-546">**MixedRealityToolkit.Examples**</span></span>

| <span data-ttu-id="daa05-547">RC2</span><span class="sxs-lookup"><span data-stu-id="daa05-547">RC2</span></span> | <span data-ttu-id="daa05-548">2.0.0</span><span class="sxs-lookup"><span data-stu-id="daa05-548">2.0.0</span></span> |
| --- | --- |
| <span data-ttu-id="daa05-549">MixedRealityToolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-549">MixedRealityToolkit.Examples.asmdef</span></span> | <span data-ttu-id="daa05-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-550">Microsoft.MixedReality.Toolkit.Examples.asmdef</span></span> |
| <span data-ttu-id="daa05-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-551">MixedRealityToolkit.Examples.Demos.Gltf.asmdef</span></span> | <span data-ttu-id="daa05-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-552">Microsoft.MixedReality.Toolkit.Demos.Gltf.asmdef</span></span> |
| <span data-ttu-id="daa05-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-553">MixedRealityToolkit.Examples.Demos.StandardShader.Inspectors.asmdef</span></span> | <span data-ttu-id="daa05-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-554">Microsoft.MixedReality.Toolkit.Demos.StandardShader.Inspectors.asmdef</span></span> |
| <span data-ttu-id="daa05-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-555">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.asmdef</span></span> | <span data-ttu-id="daa05-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-556">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.asmdef</span></span> |
| <span data-ttu-id="daa05-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-557">MixedRealityToolkit.Examples.Demos.Utilities.InspectorFields.Inspectors.asmdef</span></span> | <span data-ttu-id="daa05-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-558">Microsoft.MixedReality.Toolkit.Demos.InspectorFields.Inspectors.asmdef</span></span> |
| <span data-ttu-id="daa05-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-559">MixedRealityToolkit.Examples.Demos.UX.Interactables.asmdef</span></span> | <span data-ttu-id="daa05-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span><span class="sxs-lookup"><span data-stu-id="daa05-560">Microsoft.MixedReality.Toolkit.Demos.UX.Interactables.asmdef</span></span> |