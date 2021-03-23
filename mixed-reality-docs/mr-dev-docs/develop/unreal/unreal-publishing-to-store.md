---
title: Publicación en Microsoft Store
description: Obtenga información acerca de cómo empaquetar, certificar y publicar aplicaciones de Mixed Reality de Unreal en Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, documentación, guías, características, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, publicación, distribución, Microsoft Store
ms.openlocfilehash: 3a975d9c66e64f56919163e9d3aa65a3126d6379
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583598"
---
# <a name="publishing-to-the-microsoft-store"></a><span data-ttu-id="8c0ea-104">Publicación en Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="8c0ea-104">Publishing to the Microsoft Store</span></span>

<span data-ttu-id="8c0ea-105">Cuando esté listo para lanzar al mundo la aplicación Unreal, hay algunas opciones de configuración del proyecto que deben actualizarse antes de enviarla a Microsoft Store.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-105">When you're ready to get your Unreal app out to the world, there are a few project settings that need updating before you submit to the Microsoft Store.</span></span> <span data-ttu-id="8c0ea-106">Todos estas opciones tienen valores predeterminados, pero se deben cambiar para producción para que representen mejor la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-106">All of these settings have default values, but should be changed for production to best represent the application.</span></span>

## <a name="project-settings-for-the-store-packaging"></a><span data-ttu-id="8c0ea-107">Configuración del proyecto para el empaquetado del almacén</span><span class="sxs-lookup"><span data-stu-id="8c0ea-107">Project settings for the store packaging</span></span>

1. <span data-ttu-id="8c0ea-108">En primer lugar, seleccione **Configuración del proyecto > Descripción** y actualice la información del juego y del editor:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-108">First, select **Project Settings > Description** and update the game and publisher information:</span></span> 
    * <span data-ttu-id="8c0ea-109">El **nombre del juego** aparecerá en el icono de la aplicación en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-109">The **Game Name** will appear in the app tile on the HoloLens</span></span>
    * <span data-ttu-id="8c0ea-110">El **nombre distintivo de la empresa** se usa al generar el certificado del proyecto y debe tener el siguiente formato:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-110">The **Company Distinguished Name** is used when generating the project certificate and should be in the format:</span></span> 
        * <span data-ttu-id="8c0ea-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-111">**CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:</span></span>

![Captura de pantalla del editor de Unreal con la sección de descripción expandida en la configuración del proyecto](images/unreal-publishing-img-01.png)

2. <span data-ttu-id="8c0ea-113">Expanda la sección **HoloLens** de la configuración del proyecto y actualice los recursos de empaquetado.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-113">Expand the **HoloLens** section of the project settings and update the packaging resources.</span></span>  <span data-ttu-id="8c0ea-114">Estos nombres de recursos se mostrarán en la página de la tienda de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-114">These resource names will be shown on the application’s store page:</span></span>

![Captura de pantalla del editor de Unreal con la sección de empaquetado expandida en la configuración del proyecto](images/unreal-publishing-img-02.png)

3. <span data-ttu-id="8c0ea-116">Expanda la sección **Imágenes** y actualice las imágenes de almacenamiento predeterminadas con las texturas que representan la aplicación de la Tienda.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-116">Expand the **Images** section and update the default store images with textures that represent the store app.</span></span>  <span data-ttu-id="8c0ea-117">También puede activar la casilla **logotipo 3D** para cargar un archivo .glb para usarlo como un cubo dinámico 3D al iniciar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-117">Optionally, select the **3D Logo** checkbox to upload a glb file to use as a 3D live cube when launching the application:</span></span>

![Captura de pantalla del editor de Unreal con la sección de imágenes expandida en la configuración del proyecto](images/unreal-publishing-img-03.png)

4. <span data-ttu-id="8c0ea-119">Por último, seleccione **Generar nuevo** para generar un certificado de firma a partir del nombre del proyecto y el nombre distintivo de la empresa.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-119">Lastly, select **Generate New** to generate a signing certificate from the project name and company distinguished name</span></span>  
    * <span data-ttu-id="8c0ea-120">Establezca un **color de fondo de icono**, que aparecerá en lugar de los píxeles transparentes en las imágenes de la tienda.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-120">Set a **Tile Background Color**, which will appear in place of any transparent pixels in the store images.</span></span>
    * <span data-ttu-id="8c0ea-121">Expanda la lista desplegable y habilite la opción **Usar el entorno de Windows Store comercial** para ejecutarlo en dispositivos con bloqueo comercial y no desbloqueados para desarrollo.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-121">Expand the dropdown and enable **Use Retail Windows Store Environment** to run on retail-locked, not dev-unlocked, devices.</span></span>

![Captura de pantalla del editor de Unreal con la sección de generación de certificado expandida en la configuración del proyecto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a><span data-ttu-id="8c0ea-123">Instalador de aplicaciones opcionales</span><span class="sxs-lookup"><span data-stu-id="8c0ea-123">Optional App Installer</span></span>

<span data-ttu-id="8c0ea-124">Se puede crear un archivo instalador de aplicación desde **Configuración del proyecto > HoloLens**, que se puede usar para distribuir la aplicación fuera del almacén.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-124">An App Installer file can be created from **Project Settings > HoloLens**, which can be used to distribute the application outside of the store.</span></span>  <span data-ttu-id="8c0ea-125">Habilite la casilla **Debe crear el instalador de aplicación** y establezca una dirección URL o una ruta de acceso de red donde quiera que se almacene el appxbundle del juego.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-125">Enable the **Should Create App Installer** checkbox and set a URL or network path where you'd like the game’s appxbundle to be stored.</span></span>  

![Captura de pantalla del editor de Unreal con la sección de instalador de aplicación expandida en la configuración del proyecto](images/unreal-publishing-img-05.png)

<span data-ttu-id="8c0ea-127">Cuando se empaqueta la aplicación, se generan los tipos appxbundle y appinstaller.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-127">When the app is being packaged, both the appxbundle and appinstaller will be generated.</span></span>  <span data-ttu-id="8c0ea-128">Cargue el appxbundle en la dirección URL de instalación y, a continuación, inicie appinstaller para instalar la aplicación desde la ubicación de red.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-128">Upload the appxbundle to the installation URL, then launch the appinstaller to install the app from the network location.</span></span>

## <a name="windows-app-certification-kit"></a><span data-ttu-id="8c0ea-129">Kit para la certificación de aplicaciones en Windows</span><span class="sxs-lookup"><span data-stu-id="8c0ea-129">Windows App Certification Kit</span></span>

<span data-ttu-id="8c0ea-130">Windows 10 SDK se incluye con el kit para la certificación de aplicaciones en Windows (WACK) para validar problemas comunes que podrían afectar a la carga de un paquete en el almacén.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-130">The Windows 10 SDK ships with the Windows App Certification Kit (WACK) to validate common issues that could affect uploading a package to the store.</span></span>  <span data-ttu-id="8c0ea-131">Puede encontrar WACK en el directorio de kits de Windows, normalmente en la siguiente ruta de acceso:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-131">You can find the WACK in the Windows Kits directory, usually under the following path:</span></span> 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. <span data-ttu-id="8c0ea-132">Una vez que el archivo appx esté empaquetado para su publicación, ejecute **appcertui.exe** y siga las indicaciones para examinar el archivo appx:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-132">After your appx file is packaged for publication, run **appcertui.exe** and follow the prompts to scan the appx:</span></span>

![Captura de pantalla de la aplicación que se selecciona para la validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-06.png)

2. <span data-ttu-id="8c0ea-134">Seleccione **Validar aplicación de la Tienda**:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-134">Select **Validate Store App**:</span></span>

![Captura de pantalla de la selección de validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-07.png)

3. <span data-ttu-id="8c0ea-136">Examine el appx en la sección superior y seleccione **Siguiente**:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-136">Browse for the appx in the top section and select **Next**:</span></span>

![Captura de pantalla de la selección de prueba en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-08.png)

4. <span data-ttu-id="8c0ea-138">Seleccione **Siguiente** para ejecutar las pruebas y crear un informe:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-138">Select **Next** to run the tests and create a report:</span></span>
    * <span data-ttu-id="8c0ea-139">Todas las pruebas disponibles que se pueden ejecutar en el equipo host estarán habilitadas de manera predeterminada.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-139">All available tests that can be run on the host PC will be enabled by default</span></span>

![Captura de pantalla del progreso de la validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-09.png)

5. <span data-ttu-id="8c0ea-141">Espere a que finalicen las pruebas.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-141">Wait for the tests to finish.</span></span> <span data-ttu-id="8c0ea-142">Una vez que haya finalizado, la ventana final mostrará un resultado de superación o error, que se puede ver en el informe guardado.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-142">Once complete, the final window will show a pass or fail result, which can be viewed in the saved report.</span></span>

![Captura de pantalla de los resultados del informe final en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a><span data-ttu-id="8c0ea-144">Error conocido WACK con la versión 4.25</span><span class="sxs-lookup"><span data-stu-id="8c0ea-144">Known WACK failure with 4.25</span></span>

<span data-ttu-id="8c0ea-145">El complemento de Windows Mixed Reality en Unreal 4.25 producirá un error WACK porque algunos archivos binarios x64 se incluyen durante el empaquetado de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-145">The Windows Mixed Reality plugin in Unreal 4.25 will fail WACK because some x64 binaries are included while packaging for HoloLens.</span></span> <span data-ttu-id="8c0ea-146">El error tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-146">The failure will look like this:</span></span>

![Captura de pantalla de un resultado erróneo debido al analizador binario y a las API admitidas del kit para la certificación de aplicaciones de Windows](images/unreal-publishing-img-11.png)

<span data-ttu-id="8c0ea-148">Para solucionar el problema:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-148">To fix the issue:</span></span>
1. <span data-ttu-id="8c0ea-149">Para ir a la raíz del directorio de origen o instalación de Unreal, abra un proyecto de Unreal y haga clic con el botón derecho en el icono de Unreal de la barra de tareas.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-149">Browse to the Unreal installation or source directory root by opening an Unreal project and right-click on the Unreal icon in the taskbar.</span></span>
2. <span data-ttu-id="8c0ea-150">Haga clic con el botón derecho en UE4Editor, seleccione Propiedades y vaya a la ruta de acceso de la entrada de **Ubicación**:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-150">Right-click on UE4Editor, select properties, and browse to the path in the **Location** entry:</span></span>

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. <span data-ttu-id="8c0ea-151">En **WindowsMixedRealityHMD.Build.cs**, modifique la **línea 32** de:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-151">In **WindowsMixedRealityHMD.Build.cs**, modify **line 32** from:</span></span>

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

<span data-ttu-id="8c0ea-152">a:</span><span class="sxs-lookup"><span data-stu-id="8c0ea-152">to:</span></span>

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. <span data-ttu-id="8c0ea-153">Cierre Unreal, vuelva a abrir el proyecto y vuelva a empaquetarlo para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-153">Close Unreal, reopen the project, and repackage for HoloLens.</span></span>  <span data-ttu-id="8c0ea-154">Vuelva a ejecutar WACK y el error habrá desaparecido.</span><span class="sxs-lookup"><span data-stu-id="8c0ea-154">Rerun WACK and the error will be gone.</span></span> 

## <a name="see-also"></a><span data-ttu-id="8c0ea-155">Consulte también</span><span class="sxs-lookup"><span data-stu-id="8c0ea-155">See also</span></span>

* [<span data-ttu-id="8c0ea-156">Envío de aplicaciones a Microsoft Store</span><span class="sxs-lookup"><span data-stu-id="8c0ea-156">Submitting an app to the Microsoft Store</span></span>](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [<span data-ttu-id="8c0ea-157">Kit para la certificación de aplicaciones en Windows</span><span class="sxs-lookup"><span data-stu-id="8c0ea-157">Windows App Certification Kit</span></span>](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [<span data-ttu-id="8c0ea-158">Creación manual de un archivo Instalador de aplicación</span><span class="sxs-lookup"><span data-stu-id="8c0ea-158">Create an App Installer file manually</span></span>](/windows/msix/app-installer/how-to-create-appinstaller-file)