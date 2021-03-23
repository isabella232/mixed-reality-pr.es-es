---
title: Importación de características
description: Obtenga información sobre cómo importar e instalar características desde la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230835"
---
# <a name="importing-features"></a><span data-ttu-id="0b567-104">Importación de características</span><span class="sxs-lookup"><span data-stu-id="0b567-104">Importing features</span></span>

<span data-ttu-id="0b567-105">Una vez que se han descargado las características, se pueden revisar e importar en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="0b567-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="0b567-106">En este paso, la ventana de la aplicación debería tener un aspecto similar al de la siguiente imagen:</span><span class="sxs-lookup"><span data-stu-id="0b567-106">At this step, your application window should look like the following image:</span></span>

![Importación de características](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="0b567-108">Lista de características</span><span class="sxs-lookup"><span data-stu-id="0b567-108">Features list</span></span>

<span data-ttu-id="0b567-109">La lista **Características** contiene la colección de paquetes seleccionados durante la detección.</span><span class="sxs-lookup"><span data-stu-id="0b567-109">The **Features** list contains the collection of packages selected during discovery.</span></span> <span data-ttu-id="0b567-110">Las características se pueden seleccionar o deseleccionar antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="0b567-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="0b567-111">Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0b567-111">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de características](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="0b567-113">Lista de dependencias requeridas</span><span class="sxs-lookup"><span data-stu-id="0b567-113">Required dependencies list</span></span>

<span data-ttu-id="0b567-114">La lista **Dependencias requeridas** contiene los paquetes que una o varias de las características seleccionadas necesitan para funcionar.</span><span class="sxs-lookup"><span data-stu-id="0b567-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="0b567-115">Esta lista también contendrá las dependencias de las dependencias.</span><span class="sxs-lookup"><span data-stu-id="0b567-115">This list will also contain dependencies of dependencies.</span></span> <span data-ttu-id="0b567-116">Cada dependencia se puede seleccionar o deseleccionar antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="0b567-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="0b567-117">Los detalles del paquete se pueden ver mediante el vínculo **Detalles** que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="0b567-117">Package details can be viewed using the **Details** link shown below</span></span>

![Lista de dependencias](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="0b567-119">Si se anula la selección de las dependencias requeridas, se producirán uno o varios errores debidos a la ausencia de dichas dependencias al cargar el proyecto en Unity.</span><span class="sxs-lookup"><span data-stu-id="0b567-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="0b567-120">Estas características no se podrán usar en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="0b567-120">These features won't be usable in the project.</span></span>

## <a name="validating-selections"></a><span data-ttu-id="0b567-121">Validación de selecciones</span><span class="sxs-lookup"><span data-stu-id="0b567-121">Validating selections</span></span>

<span data-ttu-id="0b567-122">Se recomienda validar las selecciones de características antes de la importación.</span><span class="sxs-lookup"><span data-stu-id="0b567-122">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="0b567-123">Este paso presentará los problemas que es probable que impidan el desarrollo correcto del proyecto.</span><span class="sxs-lookup"><span data-stu-id="0b567-123">This step will raise any issues that are likely to impede successful project development.</span></span>

![Problemas de validación](images/ValidationIssues.png)

<span data-ttu-id="0b567-125">La herramienta de características de Mixed Reality ofrece dos resoluciones de problemas automáticas que se describen en las secciones siguientes, así como la opción de cancelar y resolver problemas manualmente.</span><span class="sxs-lookup"><span data-stu-id="0b567-125">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="0b567-126">Habilitación de dependencias</span><span class="sxs-lookup"><span data-stu-id="0b567-126">Enable dependencies</span></span>

<span data-ttu-id="0b567-127">El botón **Enable dependencies** (Habilitar dependencias) volverá a seleccionar automáticamente las dependencias que falten.</span><span class="sxs-lookup"><span data-stu-id="0b567-127">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="0b567-128">Esto se aplica a las dependencias que se seleccionaron explícitamente (aparecen en la lista de **Características**) y a las que se seleccionaron implícitamente en función de los requisitos de las características seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="0b567-128">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="0b567-129">Deshabilitación de características</span><span class="sxs-lookup"><span data-stu-id="0b567-129">Disable features</span></span>

<span data-ttu-id="0b567-130">Al seleccionar **Disable features** (Deshabilitar características), se anulará automáticamente la selección de cualquier característica que dependa de una o varias de las dependencias que se deseleccionaron.</span><span class="sxs-lookup"><span data-stu-id="0b567-130">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="0b567-131">Esto se aplica a los paquetes de dependencia seleccionados implícitamente y a las características seleccionadas explícitamente.</span><span class="sxs-lookup"><span data-stu-id="0b567-131">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="0b567-132">Importación</span><span class="sxs-lookup"><span data-stu-id="0b567-132">Importing</span></span>

<span data-ttu-id="0b567-133">Seleccione **Importar** para agregar las características seleccionadas y dé su [aprobación final](reviewing-changes.md) antes de actualizar el proyecto de destino.</span><span class="sxs-lookup"><span data-stu-id="0b567-133">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b567-134">Si sigue existiendo un problema de validación al realizar la importación, se mostrará un mensaje de advertencia.</span><span class="sxs-lookup"><span data-stu-id="0b567-134">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="0b567-135">Se recomienda seleccionar No, hacer clic en **Validar** y resolver los problemas que se presenten.</span><span class="sxs-lookup"><span data-stu-id="0b567-135">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![Continuar con problemas de validación](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="0b567-137">Vuelta al paso anterior</span><span class="sxs-lookup"><span data-stu-id="0b567-137">Going back to the previous step</span></span>

<span data-ttu-id="0b567-138">Desde **Import features** (Importar características), la herramienta de características de Mixed Reality permite volver a la pantalla de [detección](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="0b567-138">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="0b567-139">Seleccione **Volver** para descargar otros paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="0b567-139">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b567-140">Vea también</span><span class="sxs-lookup"><span data-stu-id="0b567-140">See also</span></span>

- [<span data-ttu-id="0b567-141">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0b567-141">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="0b567-142">Detección y adquisición</span><span class="sxs-lookup"><span data-stu-id="0b567-142">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="0b567-143">Visualización de los detalles del paquete de características</span><span class="sxs-lookup"><span data-stu-id="0b567-143">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="0b567-144">Revisión y aprobación de las modificaciones del proyecto</span><span class="sxs-lookup"><span data-stu-id="0b567-144">Reviewing and approving project modifications</span></span>](reviewing-changes.md)