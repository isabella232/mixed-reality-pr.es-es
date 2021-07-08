---
title: Le damos la bienvenida a la herramienta de características de Mixed Reality
description: Conozca los aspectos básicos de la herramienta de características de MR para el desarrollo de HoloLens y VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: 4e822f2dda2a314ce06bc394a4d92b1aa6953af3
ms.sourcegitcommit: 943489923c69c3a28bc152f1cb516dcdcea2880a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2021
ms.locfileid: "111772418"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="047b8-104">Le damos la bienvenida a la herramienta de características de Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="047b8-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Imagen de banner de la herramienta de características de Mixed Reality](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="047b8-106">La herramienta de características de Mixed Reality solo está disponible para Unity en este momento.</span><span class="sxs-lookup"><span data-stu-id="047b8-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="047b8-107">Si usa el motor Unreal para el desarrollo, consulte la documentación de [instalación de herramientas](../install-the-tools.md).</span><span class="sxs-lookup"><span data-stu-id="047b8-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="047b8-108">La herramienta de características de Mixed Reality es una nueva manera de que los desarrolladores detecten, actualicen y agreguen paquetes de características de Mixed Reality en proyectos de Unity.</span><span class="sxs-lookup"><span data-stu-id="047b8-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="047b8-109">Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación.</span><span class="sxs-lookup"><span data-stu-id="047b8-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="047b8-110">Si nunca antes ha trabajado con un archivo de manifiesto, se trata de un archivo JSON que contiene todos los paquetes de proyectos.</span><span class="sxs-lookup"><span data-stu-id="047b8-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="047b8-111">Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto que elija.</span><span class="sxs-lookup"><span data-stu-id="047b8-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="047b8-112">Requisitos del sistema</span><span class="sxs-lookup"><span data-stu-id="047b8-112">System requirements</span></span>

<span data-ttu-id="047b8-113">Para que pueda ejecutar la herramienta de característica de Mixed Reality, necesitará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="047b8-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="047b8-114">Entorno de ejecución de .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="047b8-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="047b8-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="047b8-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="047b8-116">Actualmente, la herramienta de características de Mixed Reality solo se ejecuta en Windows, pero pronto estará disponible la compatibilidad con MacOS.</span><span class="sxs-lookup"><span data-stu-id="047b8-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

## <a name="download"></a><span data-ttu-id="047b8-117">Descargar</span><span class="sxs-lookup"><span data-stu-id="047b8-117">Download</span></span>

<span data-ttu-id="047b8-118">Una vez configurado el entorno, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="047b8-118">Once you have your environment set up:</span></span>

* <span data-ttu-id="047b8-119">[Descargue la última versión de la herramienta Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) del Centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="047b8-119">[Download the latest version of the Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool) from the Microsoft Download Center.</span></span>
* <span data-ttu-id="047b8-120">Una vez finalizada la descarga, descomprima el archivo y guárdelo en el escritorio.</span><span class="sxs-lookup"><span data-stu-id="047b8-120">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="047b8-121">Se recomienda crear un acceso directo al archivo ejecutable para obtener un acceso más rápido.</span><span class="sxs-lookup"><span data-stu-id="047b8-121">We recommend creating a shortcut to the executable file for faster access</span></span>

> [!NOTE]
> <span data-ttu-id="047b8-122">Si no está familiarizado con el uso de Package Manager (Administrador de paquetes) de Unity, siga las [instrucciones de UPM](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span><span class="sxs-lookup"><span data-stu-id="047b8-122">If you're new to using the Unity Package Manager, follow our [UPM instructions](/windows/mixed-reality/mrtk-unity/configuration/usingupm#managing-mixed-reality-features-with-the-unity-package-manager).</span></span>

## <a name="changes-in-this-release"></a><span data-ttu-id="047b8-123">Cambios de esta versión</span><span class="sxs-lookup"><span data-stu-id="047b8-123">Changes in this release</span></span>

<span data-ttu-id="047b8-124">La versión 1.0.2103 beta incluye las siguientes correcciones:</span><span class="sxs-lookup"><span data-stu-id="047b8-124">Version 1.0.2103 Beta includes the following fixes:</span></span>

* <span data-ttu-id="047b8-125">Mejoras para la detección de errores de descarga.</span><span class="sxs-lookup"><span data-stu-id="047b8-125">Improvements to download error detection.</span></span>
* <span data-ttu-id="047b8-126">Actualizaciones sobre cómo se escriben los manifiestos para evitar errores en las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="047b8-126">Updates on how manifests are written to avoid failure to update correctly.</span></span>
* <span data-ttu-id="047b8-127">Se han quitado los escapes de las rutas de acceso de archivo en el manifiesto del proyecto.</span><span class="sxs-lookup"><span data-stu-id="047b8-127">Escpaing has been removed from file paths in the project manifest.</span></span>

<span data-ttu-id="047b8-128">A continuación se describen las características que se han agregado a esta versión:</span><span class="sxs-lookup"><span data-stu-id="047b8-128">The following features have been added in this release:</span></span>

* <span data-ttu-id="047b8-129">El catálogo de características ahora se almacena en caché.</span><span class="sxs-lookup"><span data-stu-id="047b8-129">The feature catalog is now cached.</span></span> <span data-ttu-id="047b8-130">Para comprobar si hay nuevas características y actualizaciones, use el botón Refresh (Actualizar) de Discovery (Detección).</span><span class="sxs-lookup"><span data-stu-id="047b8-130">To check for new features and updates, please use the refresh button in Discovery.</span></span>
* <span data-ttu-id="047b8-131">Se ha movido la selección del proyecto del paso de importación a antes de la detección.</span><span class="sxs-lookup"><span data-stu-id="047b8-131">Move project selection from the Import step to before Discovery.</span></span>
* <span data-ttu-id="047b8-132">Los paquetes disponibles se filtran por la versión de Unity especificada del proyecto.</span><span class="sxs-lookup"><span data-stu-id="047b8-132">Available packages are filtered by the project's specified Unity version.</span></span>
* <span data-ttu-id="047b8-133">La vista de detección ahora muestra los paquetes instalados actualmente.</span><span class="sxs-lookup"><span data-stu-id="047b8-133">The discovery view now displays currently installed packages.</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="047b8-134">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="047b8-134">1. Getting started</span></span>

<span data-ttu-id="047b8-135">Inicie la herramienta de características de Mixed Reality desde el archivo ejecutable, que muestra la página de inicio en el primer inicio:</span><span class="sxs-lookup"><span data-stu-id="047b8-135">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![Introducción](images/FeatureToolStart.png)

<span data-ttu-id="047b8-137">Desde la página de inicio, puede hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="047b8-137">From the start page, you can:</span></span>

* <span data-ttu-id="047b8-138">[Configurar](configuring-feature-tool.md) las opciones de la herramienta mediante el botón con el **icono de engranaje**.</span><span class="sxs-lookup"><span data-stu-id="047b8-138">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="047b8-139">Usar el botón de **signo de interrogación** para iniciar el explorador web predeterminado y mostrar nuestra documentación</span><span class="sxs-lookup"><span data-stu-id="047b8-139">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="047b8-140">Seleccionar **Iniciar** para empezar a explorar paquetes de características.</span><span class="sxs-lookup"><span data-stu-id="047b8-140">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-selecting-your-unity-project"></a><span data-ttu-id="047b8-141">2. Selección del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="047b8-141">2. Selecting your Unity project</span></span>

<span data-ttu-id="047b8-142">Para asegurarse de que todas las características detectadas se admiten en la versión de Unity del proyecto, el primer paso consiste en apuntar la herramienta de características de Mixed Reality al proyecto mediante el botón de **puntos suspensivos** (a la derecha del campo ruta de acceso del proyecto).</span><span class="sxs-lookup"><span data-stu-id="047b8-142">To ensure that all discovered features are supported on your project's version of Unity, the fist step is to point the Mixed Reality Feature Tool to your project using the **ellipsis** button (to the right of the project path field).</span></span>

![Selección del proyecto de Unity](images/FeatureToolSelectUnityProject.png)

> [!NOTE]
> <span data-ttu-id="047b8-144">El cuadro de diálogo que se muestra al buscar la carpeta del proyecto de Unity contiene "_" como nombre de archivo.</span><span class="sxs-lookup"><span data-stu-id="047b8-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="047b8-145">Debe escribir un valor en el nombre de archivo para que pueda seleccionarse la carpeta.</span><span class="sxs-lookup"><span data-stu-id="047b8-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="047b8-146">Cuando haya ubicado la carpeta del proyecto, haga clic en el botón Open (Abrir) para volver a Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="047b8-146">When you have located your project's folder, click the Open button to return to the Mixed Reality Feature Tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="047b8-147">Mixed Reality Feature Tool realiza la validación para asegurarse de que se ha dirigido a una carpeta de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="047b8-147">The Mixed Reality Feature Tool performs validation to ensure that it has been directed to a Unity project folder.</span></span> <span data-ttu-id="047b8-148">La carpeta debe contener las carpetas `Assets`, `Packages` y `Project Settings`.</span><span class="sxs-lookup"><span data-stu-id="047b8-148">The folder must contain `Assets`, `Packages` and `Project Settings` folders.</span></span>

## <a name="3-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="047b8-149">3. Detección y adquisición de paquetes de características</span><span class="sxs-lookup"><span data-stu-id="047b8-149">3. Discovering and acquiring feature packages</span></span>

> [!NOTE]
> <span data-ttu-id="047b8-150">La versión 1.0.2103 beta ahora almacena en caché el contenido del catálogo de características cada vez que se accede al servidor.</span><span class="sxs-lookup"><span data-stu-id="047b8-150">Version 1.0.2103 Beta now caches the feature catalog contents whenever the server is accessed.</span></span> <span data-ttu-id="047b8-151">Este cambio permite un acceso rápido a las características disponibles, a costa de mostrar los datos absolutos más recientes.</span><span class="sxs-lookup"><span data-stu-id="047b8-151">This change enables fast access to available features, at the expense of displaying the absolute latest data.</span></span> <span data-ttu-id="047b8-152">Para actualizar el catálogo, use el botón **Refresh** (Actualizar).</span><span class="sxs-lookup"><span data-stu-id="047b8-152">To update the catalog, please use the **Refresh** button.</span></span>

<span data-ttu-id="047b8-153">Las características se agrupan por categoría a fin de facilitar la búsqueda.</span><span class="sxs-lookup"><span data-stu-id="047b8-153">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="047b8-154">Por ejemplo, la categoría **Mixed Reality Toolkit** tiene varias características entre las que puede elegir:</span><span class="sxs-lookup"><span data-stu-id="047b8-154">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![Detección y adquisición](images/FeatureToolDiscovery.png)

<span data-ttu-id="047b8-156">Cuando la herramienta de características de Mixed Reality reconoce características importadas previamente, muestra un mensaje de notificación para cada una.</span><span class="sxs-lookup"><span data-stu-id="047b8-156">When the Mixed Reality Feature Tool recognizes previously imported feature(s), it displays a notification message by each.</span></span>

![Notificación de la característica importada](images/feature-tool-imported-note.png)


<span data-ttu-id="047b8-158">Una vez que haya elegido las opciones, seleccione **Get features** (Obtener características) para capturar todos los paquetes necesarios del catálogo.</span><span class="sxs-lookup"><span data-stu-id="047b8-158">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="047b8-159">Para obtener más información, consulte [Detección y adquisición de características](discovering-features.md).</span><span class="sxs-lookup"><span data-stu-id="047b8-159">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="4-importing-feature-packages"></a><span data-ttu-id="047b8-160">4. Importación de paquetes de características</span><span class="sxs-lookup"><span data-stu-id="047b8-160">4. Importing feature packages</span></span>

<span data-ttu-id="047b8-161">Después de adquirirlo, el conjunto completo de paquetes se muestra en pantalla, junto con una lista de las dependencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="047b8-161">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="047b8-162">Si necesita cambiar su selección de características o paquetes, este es el momento:</span><span class="sxs-lookup"><span data-stu-id="047b8-162">If you need to change any feature or package selections, this is the time:</span></span>

![Importación de paquetes](images/FeatureToolImport.png)

<span data-ttu-id="047b8-164">Le recomendamos usar el botón **Validar** para asegurarse de que el proyecto de Unity pueda importar correctamente las características seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="047b8-164">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="047b8-165">Después de la validación, verá un cuadro de diálogo emergente con un mensaje de operación correcta o una lista de los problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="047b8-165">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="047b8-166">Seleccione **Importar** para continuar.</span><span class="sxs-lookup"><span data-stu-id="047b8-166">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="047b8-167">Después de hacer clic en el botón **Importar**, si hay algún problema, se mostrará un mensaje simple.</span><span class="sxs-lookup"><span data-stu-id="047b8-167">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="047b8-168">Se recomienda hacer clic en No y usar el botón **Validar** para ver y resolver los problemas.</span><span class="sxs-lookup"><span data-stu-id="047b8-168">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="047b8-169">Para más información, consulte [Importación de características](importing-features.md).</span><span class="sxs-lookup"><span data-stu-id="047b8-169">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="5-reviewing-and-approving-project-changes"></a><span data-ttu-id="047b8-170">5. Revisión y aprobación de los cambios del proyecto</span><span class="sxs-lookup"><span data-stu-id="047b8-170">5. Reviewing and approving project changes</span></span>

<span data-ttu-id="047b8-171">El último paso consiste en revisar y aprobar los cambios propuestos en los archivos de manifiesto y proyecto:</span><span class="sxs-lookup"><span data-stu-id="047b8-171">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="047b8-172">Los cambios propuestos en el manifiesto se muestran a la izquierda.</span><span class="sxs-lookup"><span data-stu-id="047b8-172">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="047b8-173">Los archivos que se van a agregar al proyecto se muestran a la derecha.</span><span class="sxs-lookup"><span data-stu-id="047b8-173">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="047b8-174">El botón **Comparar** permite ver el manifiesto actual y los cambios propuestos en paralelo.</span><span class="sxs-lookup"><span data-stu-id="047b8-174">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![Authorization](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="047b8-176">Para obtener más información, consulte [Revisión y aprobación de las modificaciones del proyecto](reviewing-changes.md).</span><span class="sxs-lookup"><span data-stu-id="047b8-176">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="6-project-updated"></a><span data-ttu-id="047b8-177">6. Proyecto actualizado</span><span class="sxs-lookup"><span data-stu-id="047b8-177">6. Project updated</span></span>

<span data-ttu-id="047b8-178">Cuando se aprueban los cambios propuestos, el proyecto de Unity de destino se actualiza para hacer referencia a las características de Mixed Reality seleccionadas.</span><span class="sxs-lookup"><span data-stu-id="047b8-178">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features.</span></span>

![Proyecto actualizado](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="047b8-180">La carpeta **Packages** del proyecto de Unity ahora tiene una subcarpeta **MixedReality** con los archivos del paquete de características, y el manifiesto contendrá las referencias correspondientes.</span><span class="sxs-lookup"><span data-stu-id="047b8-180">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="047b8-181">Vuelva a Unity, espere a que se carguen las nuevas características seleccionadas y empiece a crear contenido.</span><span class="sxs-lookup"><span data-stu-id="047b8-181">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="047b8-182">Vea también</span><span class="sxs-lookup"><span data-stu-id="047b8-182">See also</span></span>

- [<span data-ttu-id="047b8-183">Configuración de la herramienta de características</span><span class="sxs-lookup"><span data-stu-id="047b8-183">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="047b8-184">Detección y adquisición</span><span class="sxs-lookup"><span data-stu-id="047b8-184">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="047b8-185">Visualización de los detalles del paquete de características</span><span class="sxs-lookup"><span data-stu-id="047b8-185">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="047b8-186">Importación de paquetes seleccionados</span><span class="sxs-lookup"><span data-stu-id="047b8-186">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="047b8-187">Revisión y aprobación de las modificaciones del proyecto</span><span class="sxs-lookup"><span data-stu-id="047b8-187">Reviewing and approving project modifications</span></span>](reviewing-changes.md)