---
title: Documentación del Empaquetador de datos espaciales de realidad mixta
description: La herramienta de empaquetado de datos espaciales de realidad mixta ya está en desuso y ya no funciona en ninguna plataforma. En su lugar, se recomienda la herramienta de administración de mapas.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: LBE, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 93d598a6add8350850faadab241b254e9cb341aa
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583642"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="b8bdf-105">Documentación del Empaquetador de datos espaciales de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b8bdf-105">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="b8bdf-106">EN DESUSO</span><span class="sxs-lookup"><span data-stu-id="b8bdf-106">DEPRECATED</span></span> 
> 
> <span data-ttu-id="b8bdf-107">A partir de 8/1/2020, esta herramienta ya está en desuso y ya no funciona en ninguna plataforma.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-107">As of 8/1/2020 this tool is now deprecated and no longer functions on any platform.</span></span> <span data-ttu-id="b8bdf-108">En su lugar, se recomienda usar la herramienta [map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) en el portal de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-108">We recommend using the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool in the Device Portal instead.</span></span> 
> 
> <span data-ttu-id="b8bdf-109">Esta herramienta y su operación se ofrecen tal cual.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-109">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="b8bdf-110">Está sujeto a cambios sin previo aviso y es posible que no sea compatible con las futuras versiones de HMD de Windows o Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-110">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span> 


## <a name="download"></a><span data-ttu-id="b8bdf-111">Descargar</span><span class="sxs-lookup"><span data-stu-id="b8bdf-111">Download</span></span>
 <span data-ttu-id="b8bdf-112">Descargar [MixedRealitySpatialDataPackager aquí](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span><span class="sxs-lookup"><span data-stu-id="b8bdf-112">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="b8bdf-113">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="b8bdf-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b8bdf-114"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="b8bdf-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b8bdf-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8bdf-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b8bdf-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b8bdf-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b8bdf-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8bdf-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b8bdf-118">Empaquetador de datos espaciales de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="b8bdf-118">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="b8bdf-119">✔️</span><span class="sxs-lookup"><span data-stu-id="b8bdf-119">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="b8bdf-120">Guía de inicio rápido</span><span class="sxs-lookup"><span data-stu-id="b8bdf-120">Quickstart</span></span>

<span data-ttu-id="b8bdf-121">La herramienta de empaquetado de datos espaciales de realidad mixta copia los datos espaciales de una aplicación de destino de un equipo a otro a través de un proceso de exportación e importación de dos pasos.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-121">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="b8bdf-122">La herramienta debe ejecutarse con privilegios de administrador y elimina los datos espaciales existentes al importar.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-122">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="b8bdf-123">La exportación deja intactos los datos espaciales existentes.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-123">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="b8bdf-124">Requisitos y limitaciones clave:</span><span class="sxs-lookup"><span data-stu-id="b8bdf-124">Key requirements and limitations:</span></span>

1. <span data-ttu-id="b8bdf-125">La herramienta debe ejecutarse con privilegios de administrador</span><span class="sxs-lookup"><span data-stu-id="b8bdf-125">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="b8bdf-126">Es posible que tenga que reiniciar el equipo si el portal de realidad mixta es inestable después de ejecutar la herramienta</span><span class="sxs-lookup"><span data-stu-id="b8bdf-126">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="b8bdf-127">La herramienta no se ejecutará al encontrar incompatibilidades o incompatibilidades de la versión de datos espaciales</span><span class="sxs-lookup"><span data-stu-id="b8bdf-127">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="b8bdf-128">La herramienta borrará los datos espaciales existentes al importar</span><span class="sxs-lookup"><span data-stu-id="b8bdf-128">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="b8bdf-129">Si se produce un error en el proceso de importación, los datos anteriores no se pueden restaurar a menos que se haya realizado la copia de seguridad mediante la exportación anterior</span><span class="sxs-lookup"><span data-stu-id="b8bdf-129">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="b8bdf-130">Calidad de la funcionalidad de importación condicionada en el modo de "solo lectura" para los datos de mapa espacial</span><span class="sxs-lookup"><span data-stu-id="b8bdf-130">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="b8bdf-131">Procedimientos recomendados de asignación</span><span class="sxs-lookup"><span data-stu-id="b8bdf-131">Mapping Best Practices</span></span>

1. <span data-ttu-id="b8bdf-132">Borrar asignaciones existentes en el panel de control (configuración-> entorno mixto de realidad >-> borrar datos de entorno)</span><span class="sxs-lookup"><span data-stu-id="b8bdf-132">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="b8bdf-133">Asegúrese de que haya suficiente iluminación para un buen seguimiento y si la ejecución del modo de mapa bloqueado intente mantener la misma iluminación</span><span class="sxs-lookup"><span data-stu-id="b8bdf-133">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="b8bdf-134">Cuando sea posible, mantenga el intervalo dinámico de iluminación bajo evitando áreas de iluminación alta junto a áreas oscuras y sombreadas.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-134">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="b8bdf-135">Minimizar las superficies en blanco y sin texturas, por ejemplo, colocar un intervalo de pósters distintos en las paredes blancas</span><span class="sxs-lookup"><span data-stu-id="b8bdf-135">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="b8bdf-136">Asignar el espacio sin objetos dinámicos en la escena, como mover personas</span><span class="sxs-lookup"><span data-stu-id="b8bdf-136">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="b8bdf-137">Bloquear el mapa al importar (disponible a través de Insider Preview)</span><span class="sxs-lookup"><span data-stu-id="b8bdf-137">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="b8bdf-138">Desbloquee el mapa y vuelva a examinar el entorno cuando se realice un seguimiento de la calidad y/o cuando haya cambios en el entorno (iluminación o cambios en el diseño de objetos) \* \* _</span><span class="sxs-lookup"><span data-stu-id="b8bdf-138">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout) \*\*_</span></span>

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="b8bdf-139">Ejecución de un empaquetador de datos espaciales de realidad mixta con un script complementario</span><span class="sxs-lookup"><span data-stu-id="b8bdf-139">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="b8bdf-140">Hemos proporcionado MRSpatialPackagerHelperScript.ps1 que ejecutan las herramientas del Empaquetador de mapas.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-140">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="b8bdf-141">Los parámetros de script se definen a continuación:</span><span class="sxs-lookup"><span data-stu-id="b8bdf-141">The script parameters are defined below:</span></span>

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="b8bdf-142">Ejemplo de script de PowerShell uso y salida</span><span class="sxs-lookup"><span data-stu-id="b8bdf-142">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="b8bdf-143">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-nombredeusuario administrador-Mode Export-MapxPath D:\temp\-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="b8bdf-143">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="b8bdf-144">Cómo exportar con MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="b8bdf-144">How to Export using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="b8bdf-145">La exportación de mapas fuera del dispositivo genera dos archivos MAPX, Het. MAPX y SA. MAPX.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-145">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="b8bdf-146">Durante el proceso de exportación, se quitan todos los delimitadores espaciales, a excepción de la aplicación especificada y el límite creado por el usuario (si existe).</span><span class="sxs-lookup"><span data-stu-id="b8bdf-146">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="b8bdf-147">El nombre de familia del paquete de origen debe coincidir con una aplicación instalada existente o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-147">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="b8bdf-148">Cómo importar mediante MixedRealitySpatialDataPackager.exe</span><span class="sxs-lookup"><span data-stu-id="b8bdf-148">How to Import using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="b8bdf-149">La importación elimina los datos espaciales existentes y los reemplaza con los datos del directorio especificado.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-149">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="b8bdf-150">La entrada del nombre de la aplicación especifica el nombre del paquete de la aplicación de destino que se debe importar para y el SID del usuario de destino especifica el usuario que debe tener acceso a los delimitadores espaciales importados.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-150">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="b8bdf-151">El nombre de familia y los SID de usuario del paquete de destino deben coincidir con los valores existentes en el equipo o se producirá un error en el archivo exe.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-151">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


<span data-ttu-id="b8bdf-152">_\*\*</span><span class="sxs-lookup"><span data-stu-id="b8bdf-152">_\*\*</span></span>
## <a name="error-messages"></a><span data-ttu-id="b8bdf-153">mensajes de error</span><span class="sxs-lookup"><span data-stu-id="b8bdf-153">Error Messages</span></span>
<span data-ttu-id="b8bdf-154">Además, los mensajes de error siguientes también irán acompañados de un valor HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b8bdf-154">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="b8bdf-155">Si se produjo un error argumentos no válidos</span><span class="sxs-lookup"><span data-stu-id="b8bdf-155">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="b8bdf-156">Si el ejecutable no se ejecutó en modo de administrador</span><span class="sxs-lookup"><span data-stu-id="b8bdf-156">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="b8bdf-157">Si se produjo un error al habilitar o deshabilitar el controlador</span><span class="sxs-lookup"><span data-stu-id="b8bdf-157">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="b8bdf-158">Si se produjo un error al validar la versión de la base de datos espacial</span><span class="sxs-lookup"><span data-stu-id="b8bdf-158">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="b8bdf-159">Si se produjo un error al validar el nombre de familia del paquete proporcionado para la aplicación de importación y exportación de destino</span><span class="sxs-lookup"><span data-stu-id="b8bdf-159">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="b8bdf-160">Si se produjo un error al validar el SID del usuario</span><span class="sxs-lookup"><span data-stu-id="b8bdf-160">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="b8bdf-161">Si se produjo un error relacionado con los archivos de datos espaciales de origen o de destino</span><span class="sxs-lookup"><span data-stu-id="b8bdf-161">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="b8bdf-162">Si se produjo un error relacionado con el inicio y la detención del espectro/SharedRealitySvc</span><span class="sxs-lookup"><span data-stu-id="b8bdf-162">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```