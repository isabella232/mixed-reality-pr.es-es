---
title: Le damos la bienvenida a la herramienta de características de Mixed Reality
description: Conozca los aspectos básicos de la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244070"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="c0008-104">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c0008-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Imagen de banner de la herramienta de características de Mixed Reality](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="c0008-106">La herramienta de características de Mixed Reality solo está disponible para Unity en este momento.</span><span class="sxs-lookup"><span data-stu-id="c0008-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="c0008-107">Si usa el motor Unreal para el desarrollo, consulte la documentación de [instalación de herramientas](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c0008-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="c0008-108">La herramienta de características de Mixed Reality es una nueva manera de que los desarrolladores detecten, actualicen y agreguen paquetes de características de Mixed Reality en proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="c0008-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="c0008-109">Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="c0008-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="c0008-110">Si nunca antes ha trabajado con un archivo de manifiesto, se trata de un archivo JSON que contiene todos los paquetes de proyectos.</span><span class="sxs-lookup"><span data-stu-id="c0008-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="c0008-111">Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto que elija.</span><span class="sxs-lookup"><span data-stu-id="c0008-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="c0008-112">Requisitos del sistema</span><span class="sxs-lookup"><span data-stu-id="c0008-112">System requirements</span></span>

<span data-ttu-id="c0008-113">Para que pueda ejecutar la herramienta de característica de Mixed Reality, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c0008-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="c0008-114">Entorno de ejecución de .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="c0008-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="c0008-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="c0008-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="c0008-116">Actualmente, la herramienta de características de Mixed Reality solo se ejecuta en Windows, pero pronto estará disponible la compatibilidad con MacOS.</span><span class="sxs-lookup"><span data-stu-id="c0008-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="c0008-117">Una vez configurado el entorno, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c0008-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="c0008-118">Descargue la última versión de la herramienta de características de Mixed Reality del [Centro de descargas de Microsoft](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="c0008-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="c0008-119">Una vez finalizada la descarga, descomprima el archivo y guárdelo en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="c0008-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="c0008-120">Se recomienda crear un acceso directo al archivo ejecutable para obtener un acceso más rápido.</span><span class="sxs-lookup"><span data-stu-id="c0008-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="c0008-121">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="c0008-121">1. Getting started</span></span>

<span data-ttu-id="c0008-122">Inicie la herramienta de características de Mixed Reality desde el archivo ejecutable, que muestra la página de inicio en el primer inicio:</span><span class="sxs-lookup"><span data-stu-id="c0008-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Introducción](images/FeatureToolStart.png)

<span data-ttu-id="c0008-124">Desde la página de inicio, puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c0008-124">From the start page, you can:</span></span>

* <span data-ttu-id="c0008-125">[Configurar](configuring-feature-tool.md) las opciones de la herramienta mediante el botón con el **icono de engranaje**.</span><span class="sxs-lookup"><span data-stu-id="c0008-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="c0008-126">Usar el botón de **signo de interrogación** para iniciar el explorador web predeterminado y mostrar nuestra documentación</span><span class="sxs-lookup"><span data-stu-id="c0008-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="c0008-127">Seleccionar **Iniciar** para empezar a explorar paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="c0008-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="c0008-128">2. Detección y adquisición de paquetes de características</span><span class="sxs-lookup"><span data-stu-id="c0008-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="c0008-129">El catálogo de paquetes de características se muestra en cuanto se presiona Iniciar.</span><span class="sxs-lookup"><span data-stu-id="c0008-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="c0008-130">Las características se agrupan por categoría a fin de facilitar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="c0008-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="c0008-131">Por ejemplo, la categoría **Mixed Reality Toolkit** tiene varias características entre las que puede elegir:</span><span class="sxs-lookup"><span data-stu-id="c0008-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Detección y adquisición](images/FeatureToolDiscovery.png)

<span data-ttu-id="c0008-133">Una vez que haya elegido las opciones, seleccione **Get features** (Obtener características) para capturar todos los paquetes necesarios del catálogo.</span><span class="sxs-lookup"><span data-stu-id="c0008-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="c0008-134">Para obtener más información, consulte [Detección y adquisición de características](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="c0008-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="c0008-135">3. Importación de paquetes de características</span><span class="sxs-lookup"><span data-stu-id="c0008-135">3. Importing feature packages</span></span>

<span data-ttu-id="c0008-136">Después de adquirirlo, el conjunto completo de paquetes se muestra en pantalla, junto con una lista de las dependencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="c0008-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="c0008-137">Si necesita cambiar su selección de características o paquetes, este es el momento:</span><span class="sxs-lookup"><span data-stu-id="c0008-137">If you need to change any feature or package selections, this is the time:</span></span>

![Importación de paquetes](images/FeatureToolImport.png)

<span data-ttu-id="c0008-139">Le recomendamos usar el botón **Validar** para asegurarse de que el proyecto de Unity pueda importar correctamente las características seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="c0008-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="c0008-140">Después de la validación, verá un cuadro de diálogo emergente con un mensaje de operación correcta o una lista de los problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="c0008-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="c0008-141">También debe establecer la ubicación del proyecto de Unity de destino antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="c0008-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="c0008-142">Use el botón de **puntos suspensivos** que hay en la izquierda del campo de ruta de acceso del proyecto para examinar la ubicación.</span><span class="sxs-lookup"><span data-stu-id="c0008-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="c0008-143">Cuando haya terminado de desplazarse por el sistema de archivos, abra la carpeta que contiene el proyecto de Unity de destino.</span><span class="sxs-lookup"><span data-stu-id="c0008-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="c0008-144">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="c0008-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="c0008-145">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="c0008-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="c0008-146">Seleccione **Importar** para continuar.</span><span class="sxs-lookup"><span data-stu-id="c0008-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="c0008-147">Después de hacer clic en el botón **Importar**, si hay algún problema, se mostrará un mensaje simple.</span><span class="sxs-lookup"><span data-stu-id="c0008-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="c0008-148">Se recomienda hacer clic en No y usar el botón **Validar** para ver y resolver los problemas.</span><span class="sxs-lookup"><span data-stu-id="c0008-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="c0008-149">Para más información, consulte [Importación de características](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="c0008-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="c0008-150">4. Revisión y aprobación de los cambios del proyecto</span><span class="sxs-lookup"><span data-stu-id="c0008-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="c0008-151">El último paso consiste en revisar y aprobar los cambios propuestos en los archivos de manifiesto y proyecto:</span><span class="sxs-lookup"><span data-stu-id="c0008-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="c0008-152">Los cambios propuestos en el manifiesto se muestran a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="c0008-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="c0008-153">Los archivos que se van a agregar al proyecto se muestran a la derecha.</span><span class="sxs-lookup"><span data-stu-id="c0008-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="c0008-154">El botón **Comparar** permite ver el manifiesto actual y los cambios propuestos en paralelo.</span><span class="sxs-lookup"><span data-stu-id="c0008-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Authorization](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="c0008-156">Para obtener más información, consulte [Revisión y aprobación de las modificaciones del proyecto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="c0008-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="c0008-157">5. Proyecto actualizado</span><span class="sxs-lookup"><span data-stu-id="c0008-157">5. Project updated</span></span>

<span data-ttu-id="c0008-158">Cuando se aprueban los cambios propuestos, el proyecto de Unity de destino se actualiza para hacer referencia a las características de Mixed Reality seleccionadas:</span><span class="sxs-lookup"><span data-stu-id="c0008-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![Proyecto actualizado](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="c0008-160">La carpeta **Packages** del proyecto de Unity ahora tiene una subcarpeta **MixedReality** con los archivos del paquete de características, y el manifiesto contendrá las referencias correspondientes.</span><span class="sxs-lookup"><span data-stu-id="c0008-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="c0008-161">Vuelva a Unity, espere a que se carguen las nuevas características seleccionadas y empiece a crear contenido.</span><span class="sxs-lookup"><span data-stu-id="c0008-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="c0008-162">Vea también</span><span class="sxs-lookup"><span data-stu-id="c0008-162">See also</span></span>

- [<span data-ttu-id="c0008-163">Configuración de la herramienta de características</span><span class="sxs-lookup"><span data-stu-id="c0008-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="c0008-164">Detección y adquisición</span><span class="sxs-lookup"><span data-stu-id="c0008-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="c0008-165">Visualización de los detalles del paquete de características</span><span class="sxs-lookup"><span data-stu-id="c0008-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="c0008-166">Importación de paquetes seleccionados</span><span class="sxs-lookup"><span data-stu-id="c0008-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="c0008-167">Revisión y aprobación de las modificaciones del proyecto</span><span class="sxs-lookup"><span data-stu-id="c0008-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
