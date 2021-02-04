---
title: Importación de características
description: Obtenga información sobre cómo importar e instalar características desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243983"
---
# <a name="importing-features"></a><span data-ttu-id="e648f-104">Importación de características</span><span class="sxs-lookup"><span data-stu-id="e648f-104">Importing features</span></span>

<span data-ttu-id="e648f-105">Una vez que se han descargado las características, se pueden revisar e importar en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="e648f-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="e648f-106">En este paso, la ventana de la aplicación debería tener un aspecto similar al de la siguiente imagen:</span><span class="sxs-lookup"><span data-stu-id="e648f-106">At this step, your application window should look like the following image:</span></span>

![Importación de características](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="e648f-108">Lista de características</span><span class="sxs-lookup"><span data-stu-id="e648f-108">Features list</span></span>

<span data-ttu-id="e648f-109">La lista **Características** contiene la colección de paquetes seleccionados durante la detección.</span><span class="sxs-lookup"><span data-stu-id="e648f-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="e648f-110">Las características se pueden seleccionar o deseleccionar antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="e648f-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="e648f-111">Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="e648f-111">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de características](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="e648f-113">Lista de dependencias requeridas</span><span class="sxs-lookup"><span data-stu-id="e648f-113">Required dependencies list</span></span>

<span data-ttu-id="e648f-114">La lista **Dependencias requeridas** contiene los paquetes que una o varias de las características seleccionadas necesitan para funcionar.</span><span class="sxs-lookup"><span data-stu-id="e648f-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="e648f-115">Esta lista también contendrá las dependencias de las dependencias.</span><span class="sxs-lookup"><span data-stu-id="e648f-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="e648f-116">Cada dependencia se puede seleccionar o deseleccionar antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="e648f-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="e648f-117">Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="e648f-117">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de dependencias](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="e648f-119">Si se anula la selección de las dependencias requeridas, se producirán uno o varios errores debidos a la ausencia de dichas dependencias al cargar el proyecto en Unity.</span><span class="sxs-lookup"><span data-stu-id="e648f-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="e648f-120">Estas características no se podrán usar en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="e648f-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="e648f-121">Especificación de la ruta de acceso del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="e648f-121">Specifying the Unity project path</span></span>

<span data-ttu-id="e648f-122">Antes de que las características se puedan importar en el proyecto, debe registrar la ruta de acceso con la herramienta de características de Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="e648f-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![Configuración de la ruta de acceso del proyecto](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="e648f-124">Validación de selecciones</span><span class="sxs-lookup"><span data-stu-id="e648f-124">Validating selections</span></span>

<span data-ttu-id="e648f-125">Se recomienda validar las selecciones de características antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="e648f-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="e648f-126">Este paso presentará los problemas que es probable que impidan el desarrollo correcto del proyecto.</span><span class="sxs-lookup"><span data-stu-id="e648f-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemas de validación](images/ValidationIssues.png)

<span data-ttu-id="e648f-128">La herramienta de características de Mixed Reality ofrece dos resoluciones de problemas automáticas que se describen en las secciones siguientes, así como la opción de cancelar y resolver problemas manualmente.</span><span class="sxs-lookup"><span data-stu-id="e648f-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e648f-129">La herramienta de características de Mixed Reality no puede resolver automáticamente los problemas relacionados con las versiones de Unity requeridas.</span><span class="sxs-lookup"><span data-stu-id="e648f-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="e648f-130">Estos problemas deben solucionarse manualmente mediante la actualización de la versión de Unity que utiliza el proyecto o la deshabilitación de las características que requieren una versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="e648f-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="e648f-131">Una versión futura de la herramienta de características de Mixed Reality proporcionará un mejor filtrado de las características en función de la versión de Unity que use el proyecto.</span><span class="sxs-lookup"><span data-stu-id="e648f-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="e648f-132">Habilitación de dependencias</span><span class="sxs-lookup"><span data-stu-id="e648f-132">Enable dependencies</span></span>

<span data-ttu-id="e648f-133">El botón **Enable dependencies** (Habilitar dependencias) volverá a seleccionar automáticamente las dependencias que falten.</span><span class="sxs-lookup"><span data-stu-id="e648f-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="e648f-134">Esto se aplica a las dependencias que se seleccionaron explícitamente (aparecen en la lista de **Características**) y a las que se seleccionaron implícitamente en función de los requisitos de las características seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="e648f-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="e648f-135">Deshabilitación de características</span><span class="sxs-lookup"><span data-stu-id="e648f-135">Disable features</span></span>

<span data-ttu-id="e648f-136">Al seleccionar **Disable features** (Deshabilitar características), se anulará automáticamente la selección de cualquier característica que dependa de una o varias de las dependencias que se deseleccionaron.</span><span class="sxs-lookup"><span data-stu-id="e648f-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="e648f-137">Esto se aplica a los paquetes de dependencia seleccionados implícitamente y a las características seleccionadas explícitamente.</span><span class="sxs-lookup"><span data-stu-id="e648f-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="e648f-138">Importación</span><span class="sxs-lookup"><span data-stu-id="e648f-138">Importing</span></span>

<span data-ttu-id="e648f-139">Seleccione **Importar** para agregar las características seleccionadas y dé su [aprobación final](reviewing-changes.md) antes de actualizar el proyecto de destino.</span><span class="sxs-lookup"><span data-stu-id="e648f-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e648f-140">Si sigue existiendo un problema de validación al realizar la importación, se mostrará un mensaje de advertencia.</span><span class="sxs-lookup"><span data-stu-id="e648f-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="e648f-141">Se recomienda seleccionar No, hacer clic en **Validar** y resolver los problemas que se presenten.</span><span class="sxs-lookup"><span data-stu-id="e648f-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continuar con problemas de validación](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="e648f-143">Vuelta al paso anterior</span><span class="sxs-lookup"><span data-stu-id="e648f-143">Going back to the previous step</span></span>

<span data-ttu-id="e648f-144">Desde **Import features** (Importar características), la herramienta de características de Mixed Reality permite volver a la pantalla de [detección](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="e648f-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="e648f-145">Seleccione **Volver** para descargar otros paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="e648f-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="e648f-146">Vea también</span><span class="sxs-lookup"><span data-stu-id="e648f-146">See also</span></span>

- [<span data-ttu-id="e648f-147">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e648f-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="e648f-148">Detección y adquisición</span><span class="sxs-lookup"><span data-stu-id="e648f-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="e648f-149">Visualización de los detalles del paquete de características</span><span class="sxs-lookup"><span data-stu-id="e648f-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="e648f-150">Revisión y aprobación de las modificaciones del proyecto</span><span class="sxs-lookup"><span data-stu-id="e648f-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)