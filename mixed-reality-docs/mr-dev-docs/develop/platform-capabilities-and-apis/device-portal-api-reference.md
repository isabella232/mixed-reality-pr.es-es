---
title: Referencia de la API del Portal de dispositivos
description: Referencia de API para Windows Device portal en HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portal de dispositivos de Windows, API, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: c705ce65971042ab41befed9c6813dc797b61fc0
ms.sourcegitcommit: 084b1da9d7b435394b38d6152a2f9aee7a74aa2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/29/2020
ms.locfileid: "97804427"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="99714-104">Referencia de la API del Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="99714-104">Device portal API reference</span></span>

<span data-ttu-id="99714-105">Todo lo que se encuentra en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para tener acceso a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="99714-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="99714-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="99714-106">App deloyment</span></span>

<span data-ttu-id="99714-107">**/API/App/packagemanager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="99714-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="99714-108">Uninstalls an app</span></span>

<span data-ttu-id="99714-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-109">Parameters</span></span>
* <span data-ttu-id="99714-110">paquete: nombre de archivo del paquete que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="99714-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="99714-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="99714-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="99714-112">Installs an App</span></span>

<span data-ttu-id="99714-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-113">Parameters</span></span>
* <span data-ttu-id="99714-114">paquete: nombre de archivo del paquete que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="99714-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="99714-115">Carga</span><span class="sxs-lookup"><span data-stu-id="99714-115">Payload</span></span>
* <span data-ttu-id="99714-116">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="99714-116">multi-part conforming http body</span></span>

<span data-ttu-id="99714-117">**/API/App/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="99714-118">Recupera la lista de aplicaciones instaladas en el sistema con detalles</span><span class="sxs-lookup"><span data-stu-id="99714-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="99714-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-119">Return data</span></span>
* <span data-ttu-id="99714-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="99714-120">List of installed packages with details</span></span>

<span data-ttu-id="99714-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="99714-122">Obtiene el estado de la instalación de la aplicación en curso</span><span class="sxs-lookup"><span data-stu-id="99714-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="99714-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="99714-123">Dump collection</span></span>

<span data-ttu-id="99714-124">**/API/Debug/dump/usermode/CrashControl (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="99714-125">Deshabilita la recopilación de volcados de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="99714-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="99714-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-126">Parameters</span></span>
* <span data-ttu-id="99714-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="99714-127">packageFullname : package name</span></span>

<span data-ttu-id="99714-128">**/API/Debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="99714-129">Obtiene la configuración de la colección de volcados de memoria de aplicaciones transferidas</span><span class="sxs-lookup"><span data-stu-id="99714-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="99714-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-130">Parameters</span></span>
* <span data-ttu-id="99714-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="99714-131">packageFullname : package name</span></span>

<span data-ttu-id="99714-132">**/API/Debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="99714-133">Habilita y establece la configuración de control de volcado para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="99714-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="99714-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-134">Parameters</span></span>
* <span data-ttu-id="99714-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="99714-135">packageFullname : package name</span></span>

<span data-ttu-id="99714-136">**/API/Debug/dump/usermode/crashdump (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="99714-137">Elimina un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="99714-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="99714-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-138">Parameters</span></span>
* <span data-ttu-id="99714-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="99714-139">packageFullname : package name</span></span>
* <span data-ttu-id="99714-140">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="99714-140">fileName : dump file name</span></span>

<span data-ttu-id="99714-141">**/API/Debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="99714-142">Recupera un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="99714-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="99714-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-143">Parameters</span></span>
* <span data-ttu-id="99714-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="99714-144">packageFullname : package name</span></span>
* <span data-ttu-id="99714-145">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="99714-145">fileName : dump file name</span></span>

<span data-ttu-id="99714-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-146">Return data</span></span>
* <span data-ttu-id="99714-147">Archivo de volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="99714-147">Dump file.</span></span> <span data-ttu-id="99714-148">Inspeccionar con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="99714-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="99714-149">**/API/Debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="99714-150">Devuelve la lista de todos los volcados de memoria de las aplicaciones transferidas localmente</span><span class="sxs-lookup"><span data-stu-id="99714-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="99714-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-151">Return data</span></span>
* <span data-ttu-id="99714-152">Lista de volcados de memoria por aplicación cargada</span><span class="sxs-lookup"><span data-stu-id="99714-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="99714-153">ETW</span><span class="sxs-lookup"><span data-stu-id="99714-153">ETW</span></span>

<span data-ttu-id="99714-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="99714-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="99714-155">Enumerates registered providers</span></span>

<span data-ttu-id="99714-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-156">Return data</span></span>
* <span data-ttu-id="99714-157">Lista de proveedores, nombre descriptivo y GUID</span><span class="sxs-lookup"><span data-stu-id="99714-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="99714-158">**/API/ETW/Session/Realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="99714-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="99714-159">Crea una sesión ETW en tiempo real; se administra a través de un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="99714-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="99714-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-160">Return data</span></span>
* <span data-ttu-id="99714-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="99714-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="99714-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="99714-162">Holographic OS</span></span>

<span data-ttu-id="99714-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="99714-164">Devuelve una lista de proveedores ETW específicos de HoloLens que no están registrados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="99714-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="99714-166">Devuelve los Estados de todos los servicios que se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="99714-166">Returns the states of all services running.</span></span>

<span data-ttu-id="99714-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="99714-168">Obtiene el IPD almacenado (distancia interpupillary) en milímetros.</span><span class="sxs-lookup"><span data-stu-id="99714-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="99714-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="99714-170">Establece la configuración de IPD</span><span class="sxs-lookup"><span data-stu-id="99714-170">Sets the IPD</span></span>

<span data-ttu-id="99714-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-171">Parameters</span></span>
* <span data-ttu-id="99714-172">IPD: nuevo valor de IPD que se establecerá en milímetros</span><span class="sxs-lookup"><span data-stu-id="99714-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="99714-173">**/API/Holographic/os/webmanagement/Settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="99714-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="99714-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="99714-175">**/API/Holographic/os/webmanagement/Settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="99714-176">Establece los requisitos de HTTPS para el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="99714-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="99714-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-177">Parameters</span></span>
* <span data-ttu-id="99714-178">requerido: sí, no o predeterminado</span><span class="sxs-lookup"><span data-stu-id="99714-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="99714-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="99714-179">Holographic Perception</span></span>

<span data-ttu-id="99714-180">**/API/Holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="99714-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="99714-181">Acepta actualizaciones de WebSocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="99714-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="99714-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-182">Parameters</span></span>
* <span data-ttu-id="99714-183">clientmode: "Active" fuerza el modo de seguimiento visual cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="99714-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="99714-184">Temperatura térmica holográfica</span><span class="sxs-lookup"><span data-stu-id="99714-184">Holographic Thermal</span></span>

<span data-ttu-id="99714-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="99714-186">Obtener la fase térmica del dispositivo (0 normal, 1 cálido, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="99714-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="99714-187">Map Manager (Administrador de mapas)</span><span class="sxs-lookup"><span data-stu-id="99714-187">Map Manager</span></span>

<span data-ttu-id="99714-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="99714-189">Obtiene la lista de archivos de asignación disponibles (. MAPX).</span><span class="sxs-lookup"><span data-stu-id="99714-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="99714-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="99714-191">Obtiene la lista de archivos de delimitador disponibles (. ancx).</span><span class="sxs-lookup"><span data-stu-id="99714-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="99714-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="99714-193">Obtiene la lista de archivos de base de datos de reconstrucción espacial disponibles (. srdb).</span><span class="sxs-lookup"><span data-stu-id="99714-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="99714-194">**/API/Holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="99714-195">Obtiene la lista de delimitadores persistentes para el usuario actual.</span><span class="sxs-lookup"><span data-stu-id="99714-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="99714-196">Descargar/cargar/eliminar archivos</span><span class="sxs-lookup"><span data-stu-id="99714-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="99714-197">**/API/Holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="99714-198">Descarga un mapa, un delimitador o un archivo de base de datos de reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="99714-199">El archivo se debe haber cargado o exportado previamente.</span><span class="sxs-lookup"><span data-stu-id="99714-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="99714-200">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-200">Parameters</span></span>
* <span data-ttu-id="99714-201">FileName: nombre del archivo que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="99714-202">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="99714-203">**/API/Holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="99714-204">Carga un archivo de base de datos de asignación, delimitador o reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="99714-205">Una vez que se carga un archivo, se puede importar posteriormente para que lo use el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="99714-206">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-206">Parameters</span></span>
* <span data-ttu-id="99714-207">archivo: nombre del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="99714-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="99714-208">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="99714-209">**/API/Holographic/mapmanager/Delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="99714-210">Elimina un mapa, un delimitador o un archivo de base de datos de reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="99714-211">El archivo se debe haber cargado o exportado previamente.</span><span class="sxs-lookup"><span data-stu-id="99714-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="99714-212">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-212">Parameters</span></span>
* <span data-ttu-id="99714-213">FileName: nombre del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="99714-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="99714-214">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="99714-215">Exportación</span><span class="sxs-lookup"><span data-stu-id="99714-215">Export</span></span>

<span data-ttu-id="99714-216">**/API/Holographic/mapmanager/Export (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="99714-217">Exporta el mapa actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="99714-218">Una vez exportado, se puede descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="99714-219">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="99714-220">**/API/Holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="99714-221">Exporta el mapa actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="99714-222">Una vez exportado, se puede descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="99714-223">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="99714-224">**/API/Holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="99714-225">Exporta el mapa y los delimitadores actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="99714-226">Una vez que se exporten, se pueden descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="99714-227">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="99714-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="99714-229">Exporta el mapa y la base de datos de reconstrucción espacial actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="99714-230">Una vez exportados, se pueden descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="99714-231">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="99714-232">Importar</span><span class="sxs-lookup"><span data-stu-id="99714-232">Import</span></span>

<span data-ttu-id="99714-233">**/API/Holographic/mapmanager/Import (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="99714-234">Indica al sistema qué asignación debe usarse actualmente.</span><span class="sxs-lookup"><span data-stu-id="99714-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="99714-235">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="99714-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="99714-236">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-236">Parameters</span></span>
* <span data-ttu-id="99714-237">Nombre de archivo: nombre del mapa que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="99714-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="99714-238">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="99714-239">**/API/Holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="99714-240">Indica al sistema qué delimitadores deben usarse actualmente.</span><span class="sxs-lookup"><span data-stu-id="99714-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="99714-241">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="99714-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="99714-242">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-242">Parameters</span></span>
* <span data-ttu-id="99714-243">Nombre de archivo: nombre de los delimitadores que se van a utilizar.</span><span class="sxs-lookup"><span data-stu-id="99714-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="99714-244">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="99714-245">**/API/Holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="99714-246">Indica al sistema qué base de datos de reconstrucción espacial se debe utilizar actualmente.</span><span class="sxs-lookup"><span data-stu-id="99714-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="99714-247">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="99714-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="99714-248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-248">Parameters</span></span>
* <span data-ttu-id="99714-249">Nombre de archivo: nombre de la base de de asignación espacial que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="99714-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="99714-250">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="99714-251">Otros</span><span class="sxs-lookup"><span data-stu-id="99714-251">Other</span></span>

<span data-ttu-id="99714-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="99714-253">Restablezca el sistema en la base de datos de asignaciones, delimitadores y reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="99714-254">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="99714-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="99714-255">**/API/Holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="99714-256">Obtiene el estado del sistema, incluidos los archivos de base de datos de asignación, delimitadores y reconstrucción espacial que se importaron por última vez.</span><span class="sxs-lookup"><span data-stu-id="99714-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="99714-257">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="99714-257">Mixed Reality Capture</span></span>

<span data-ttu-id="99714-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="99714-259">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99714-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="99714-260">Use OP = parámetro de consulta de transmisión por secuencias.</span><span class="sxs-lookup"><span data-stu-id="99714-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="99714-261">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-261">Parameters</span></span>
* <span data-ttu-id="99714-262">Filename: nombre, hex64 codificado, del archivo de vídeo que se va a obtener</span><span class="sxs-lookup"><span data-stu-id="99714-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="99714-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="99714-263">op : stream</span></span>

<span data-ttu-id="99714-264">**/API/Holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="99714-265">Elimina una grabación de realidad mixta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99714-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="99714-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-266">Parameters</span></span>
* <span data-ttu-id="99714-267">Filename: nombre, hex64 codificado, del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="99714-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="99714-268">**/API/Holographic/MRC/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="99714-269">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="99714-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="99714-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="99714-271">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99714-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="99714-272">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-272">Parameters</span></span>
* <span data-ttu-id="99714-273">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-274">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-275">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="99714-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="99714-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="99714-277">Obtiene la configuración de captura de realidad mixta predeterminada</span><span class="sxs-lookup"><span data-stu-id="99714-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="99714-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="99714-279">Establece la configuración de captura de realidad mixta predeterminada.</span><span class="sxs-lookup"><span data-stu-id="99714-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="99714-280">Algunos de estos valores se aplican a la captura de vídeo y fotos de MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="99714-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="99714-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="99714-282">Obtiene el estado de la captura de realidad mixta en el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="99714-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="99714-283">\**_Respuesta_* _</span><span class="sxs-lookup"><span data-stu-id="99714-283">\**_Response_* _</span></span>

<span data-ttu-id="99714-284">La respuesta contiene una propiedad JSON que indica si el portal de dispositivos de Windows está grabando vídeo o no.</span><span class="sxs-lookup"><span data-stu-id="99714-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="99714-285">_ */API/Holographic/MRC/Thumbnail (GET)*\*</span><span class="sxs-lookup"><span data-stu-id="99714-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="99714-286">Obtiene la imagen en miniatura del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="99714-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="99714-287">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-287">Parameters</span></span>
* <span data-ttu-id="99714-288">Filename: nombre, hex64 codificado, del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="99714-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="99714-289">**/API/Holographic/MRC/video/control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="99714-290">Inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="99714-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="99714-291">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-291">Parameters</span></span>
* <span data-ttu-id="99714-292">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-293">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-294">MIC: Capture Microphone: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-295">bucle invertido: captura de audio de la aplicación: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-296">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="99714-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="99714-297">Vstab: (solo HoloLens 2) habilitar estabilización de vídeo: true o false (el valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="99714-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="99714-298">vstabbuffer: (solo HoloLens 2) latencia de búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="99714-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="99714-299">**/API/Holographic/MRC/video/control/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="99714-300">Detiene la grabación de realidad mixta actual</span><span class="sxs-lookup"><span data-stu-id="99714-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="99714-301">Streaming de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="99714-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="99714-302">Debido al aislamiento de bucle invertido, no se puede conectar a un streaming de realidad mixta desde dentro de una aplicación en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="99714-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="99714-303">HoloLens admite la vista previa dinámica de la realidad mixta a través de la descarga fragmentada de un MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="99714-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="99714-304">Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:</span><span class="sxs-lookup"><span data-stu-id="99714-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="99714-305">hololens: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="99714-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="99714-306">PV: capturar la cámara PV: true o false</span><span class="sxs-lookup"><span data-stu-id="99714-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="99714-307">MIC: capturar micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="99714-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="99714-308">bucle invertido: captura de audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="99714-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="99714-309">Si no se especifica ninguno de estos: los hologramas, la cámara de foto/vídeo y el audio de la aplicación se capturarán</span><span class="sxs-lookup"><span data-stu-id="99714-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="99714-310">Si se especifica any: los parámetros no especificados tendrán como valor predeterminado False.</span><span class="sxs-lookup"><span data-stu-id="99714-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="99714-311">Parámetros opcionales (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="99714-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="99714-312">RenderFromCamera: representación de la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="99714-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="99714-313">Vstab: habilitar estabilización de vídeo: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="99714-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="99714-314">vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="99714-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="99714-315">**live.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="99714-316">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="99714-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="99714-317">**live_high.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="99714-318">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="99714-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="99714-319">**live_med.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="99714-320">Una secuencia de 854x480p 30 fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="99714-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="99714-321">**live_low.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="99714-322">Una secuencia de 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="99714-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="99714-323">Redes</span><span class="sxs-lookup"><span data-stu-id="99714-323">Networking</span></span>

<span data-ttu-id="99714-324">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="99714-325">Obtiene la configuración de IP actual.</span><span class="sxs-lookup"><span data-stu-id="99714-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="99714-326">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="99714-326">OS Information</span></span>

<span data-ttu-id="99714-327">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="99714-328">Obtiene información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="99714-328">Gets operating system information</span></span>

<span data-ttu-id="99714-329">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="99714-330">Obtiene el nombre de la máquina.</span><span class="sxs-lookup"><span data-stu-id="99714-330">Gets the machine name</span></span>

<span data-ttu-id="99714-331">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="99714-332">Establece el nombre de la máquina</span><span class="sxs-lookup"><span data-stu-id="99714-332">Sets the machine name</span></span>

<span data-ttu-id="99714-333">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-333">Parameters</span></span>
* <span data-ttu-id="99714-334">Nombre: nuevo nombre del equipo, hex64 codificado, para establecer en</span><span class="sxs-lookup"><span data-stu-id="99714-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="99714-335">Control de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="99714-335">Perception Simulation Control</span></span>

<span data-ttu-id="99714-336">**/API/Holographic/Simulation/control/MODE (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="99714-337">Obtención del modo de simulación</span><span class="sxs-lookup"><span data-stu-id="99714-337">Get the simulation mode</span></span>

<span data-ttu-id="99714-338">**/API/Holographic/Simulation/control/MODE (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="99714-339">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="99714-339">Set the simulation mode</span></span>

<span data-ttu-id="99714-340">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-340">Parameters</span></span>
* <span data-ttu-id="99714-341">modo de simulación: predeterminado, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="99714-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="99714-342">**/API/Holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="99714-343">Elimine un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="99714-343">Delete a control stream.</span></span>

<span data-ttu-id="99714-344">**/API/Holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="99714-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="99714-345">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="99714-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="99714-346">**/API/Holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="99714-347">Cree un flujo de control (se requiere prioridad) o publique los datos en un flujo creado (streamId obligatorio).</span><span class="sxs-lookup"><span data-stu-id="99714-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="99714-348">Se espera que los datos expuestos sean del tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="99714-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="99714-349">**/API/Holographic/Simulation/display/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="99714-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="99714-350">Solicitar una secuencia de vídeo de simulación que contenga el contenido representado en la pantalla del sistema cuando esté en modo de ' simulación '.</span><span class="sxs-lookup"><span data-stu-id="99714-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="99714-351">Inicialmente, se enviará un encabezado de descriptor de formato simple, seguido de las texturas codificadas en H. 264, cada una precedida por un encabezado que indica el índice ocular y el tamaño de la textura.</span><span class="sxs-lookup"><span data-stu-id="99714-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="99714-352">Reproducción de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="99714-352">Perception Simulation Playback</span></span>

<span data-ttu-id="99714-353">**/API/Holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="99714-354">Elimina una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-354">Delete a recording.</span></span>

<span data-ttu-id="99714-355">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-355">Parameters</span></span>
* <span data-ttu-id="99714-356">grabación: nombre de la grabación que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="99714-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="99714-357">**/API/Holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="99714-358">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-358">Upload a recording.</span></span>

<span data-ttu-id="99714-359">**/API/Holographic/Simulation/Playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="99714-360">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="99714-360">Get all recordings.</span></span>

<span data-ttu-id="99714-361">**/API/Holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="99714-362">Obtiene el estado de reproducción actual de una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="99714-363">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-363">Parameters</span></span>
* <span data-ttu-id="99714-364">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-364">recording : Name of recording.</span></span>

<span data-ttu-id="99714-365">**/API/Holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="99714-366">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-366">Unload a recording.</span></span>

<span data-ttu-id="99714-367">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-367">Parameters</span></span>
* <span data-ttu-id="99714-368">grabación: nombre de la grabación que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="99714-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="99714-369">**/API/Holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="99714-370">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-370">Load a recording.</span></span>

<span data-ttu-id="99714-371">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-371">Parameters</span></span>
* <span data-ttu-id="99714-372">grabación: nombre de la grabación que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="99714-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="99714-373">**/API/Holographic/Simulation/Playback/Session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="99714-374">Obtiene todas las grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="99714-374">Get all loaded recordings.</span></span>

<span data-ttu-id="99714-375">**/API/Holographic/Simulation/Playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="99714-376">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-376">Pause a recording.</span></span>

<span data-ttu-id="99714-377">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-377">Parameters</span></span>
* <span data-ttu-id="99714-378">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-378">recording : Name of recording.</span></span>

<span data-ttu-id="99714-379">**/API/Holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="99714-380">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-380">Play a recording.</span></span>

<span data-ttu-id="99714-381">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-381">Parameters</span></span>
* <span data-ttu-id="99714-382">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-382">recording : Name of recording.</span></span>

<span data-ttu-id="99714-383">**/API/Holographic/Simulation/Playback/Session/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="99714-384">Detener una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-384">Stop a recording.</span></span>

<span data-ttu-id="99714-385">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-385">Parameters</span></span>
* <span data-ttu-id="99714-386">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-386">recording : Name of recording.</span></span>

<span data-ttu-id="99714-387">**/API/Holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="99714-388">Obtiene los tipos de datos en una grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="99714-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="99714-389">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-389">Parameters</span></span>
* <span data-ttu-id="99714-390">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="99714-391">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="99714-391">Perception Simulation Recording</span></span>

<span data-ttu-id="99714-392">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="99714-393">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-393">Start a recording.</span></span> <span data-ttu-id="99714-394">Solo puede haber una grabación activa al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="99714-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="99714-395">Debe establecerse una de las clases Head, Hand, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="99714-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="99714-396">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-396">Parameters</span></span>
* <span data-ttu-id="99714-397">Head: establézcalo en 1 para registrar los datos principales.</span><span class="sxs-lookup"><span data-stu-id="99714-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="99714-398">manos: establézcalo en 1 para registrar los datos de la mano.</span><span class="sxs-lookup"><span data-stu-id="99714-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="99714-399">spatialMapping: establézcalo en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="99714-400">entorno: establézcalo en 1 para registrar los datos del entorno.</span><span class="sxs-lookup"><span data-stu-id="99714-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="99714-401">Nombre: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-401">name : Name of the recording.</span></span>
* <span data-ttu-id="99714-402">singleSpatialMappingFrame: establézcalo en 1 para registrar solo un marco de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="99714-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="99714-403">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="99714-404">Obtiene el estado de grabación.</span><span class="sxs-lookup"><span data-stu-id="99714-404">Get recording state.</span></span>

<span data-ttu-id="99714-405">**/API/Holographic/Simulation/Recording/STOP (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="99714-406">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="99714-406">Stop the current recording.</span></span> <span data-ttu-id="99714-407">La grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="99714-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="99714-408">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="99714-408">Performance data</span></span>

<span data-ttu-id="99714-409">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="99714-410">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="99714-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="99714-411">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-411">Return data</span></span>
* <span data-ttu-id="99714-412">JSON con la lista de procesos y detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="99714-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="99714-413">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="99714-414">Devuelve las estadísticas de rendimiento del sistema (e/s de lectura/escritura, estadísticas de memoria, etc.).</span><span class="sxs-lookup"><span data-stu-id="99714-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="99714-415">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-415">Return data</span></span>
* <span data-ttu-id="99714-416">JSON con información del sistema: CPU, GPU, memoria, red, e/s</span><span class="sxs-lookup"><span data-stu-id="99714-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="99714-417">Power</span><span class="sxs-lookup"><span data-stu-id="99714-417">Power</span></span>

<span data-ttu-id="99714-418">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="99714-419">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="99714-419">Gets the current battery state</span></span>

<span data-ttu-id="99714-420">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="99714-421">Comprueba si el sistema está en un estado de baja energía.</span><span class="sxs-lookup"><span data-stu-id="99714-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="99714-422">Control remoto</span><span class="sxs-lookup"><span data-stu-id="99714-422">Remote Control</span></span>

<span data-ttu-id="99714-423">**/API/control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="99714-424">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="99714-424">Restarts the target device</span></span>

<span data-ttu-id="99714-425">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="99714-426">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="99714-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="99714-427">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="99714-427">Task Manager</span></span>

<span data-ttu-id="99714-428">**/API/TaskManager/App (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="99714-429">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="99714-429">Stops a modern app</span></span>

<span data-ttu-id="99714-430">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-430">Parameters</span></span>
* <span data-ttu-id="99714-431">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="99714-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="99714-432">forcestop: forzar la detención de todos los procesos (= sí)</span><span class="sxs-lookup"><span data-stu-id="99714-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="99714-433">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="99714-434">Inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="99714-434">Starts a modern app</span></span>

<span data-ttu-id="99714-435">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-435">Parameters</span></span>
* <span data-ttu-id="99714-436">AppID: PRAID de la aplicación que se va a iniciar, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="99714-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="99714-437">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="99714-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="99714-438">Administración de WiFi</span><span class="sxs-lookup"><span data-stu-id="99714-438">WiFi Management</span></span>

<span data-ttu-id="99714-439">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="99714-440">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="99714-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="99714-441">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-441">Return data</span></span>
* <span data-ttu-id="99714-442">Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)</span><span class="sxs-lookup"><span data-stu-id="99714-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="99714-443">**/API/WiFi/Network (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="99714-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="99714-444">Elimina un perfil asociado a una red en una interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="99714-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="99714-445">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-445">Parameters</span></span>
* <span data-ttu-id="99714-446">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="99714-446">interface : network interface guid</span></span>
* <span data-ttu-id="99714-447">Perfil: nombre del perfil</span><span class="sxs-lookup"><span data-stu-id="99714-447">profile : profile name</span></span>

<span data-ttu-id="99714-448">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="99714-449">Enumera las redes inalámbricas de la interfaz de red especificada</span><span class="sxs-lookup"><span data-stu-id="99714-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="99714-450">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-450">Parameters</span></span>
* <span data-ttu-id="99714-451">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="99714-451">interface : network interface guid</span></span>

<span data-ttu-id="99714-452">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-452">Return data</span></span>
* <span data-ttu-id="99714-453">Lista de redes inalámbricas encontradas en la interfaz de red con detalles</span><span class="sxs-lookup"><span data-stu-id="99714-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="99714-454">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="99714-455">Conecta o desconecta una red de la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="99714-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="99714-456">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-456">Parameters</span></span>
* <span data-ttu-id="99714-457">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="99714-457">interface : network interface guid</span></span>
* <span data-ttu-id="99714-458">SSID: SSID, hex64 codificado, para conectarse</span><span class="sxs-lookup"><span data-stu-id="99714-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="99714-459">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="99714-459">op : connect or disconnect</span></span>
* <span data-ttu-id="99714-460">createprofile: sí o no</span><span class="sxs-lookup"><span data-stu-id="99714-460">createprofile : yes or no</span></span>
* <span data-ttu-id="99714-461">clave: clave compartida, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="99714-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="99714-462">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="99714-462">Windows Performance Recorder</span></span>

<span data-ttu-id="99714-463">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="99714-464">Carga un perfil de WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="99714-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="99714-465">Carga</span><span class="sxs-lookup"><span data-stu-id="99714-465">Payload</span></span>
* <span data-ttu-id="99714-466">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="99714-466">multi-part conforming http body</span></span>

<span data-ttu-id="99714-467">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-467">Return data</span></span>
* <span data-ttu-id="99714-468">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="99714-468">Returns the WPR session status.</span></span>

<span data-ttu-id="99714-469">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="99714-470">Recupera el estado de la sesión de WPR</span><span class="sxs-lookup"><span data-stu-id="99714-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="99714-471">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-471">Return data</span></span>
* <span data-ttu-id="99714-472">Estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="99714-472">WPR session status.</span></span>

<span data-ttu-id="99714-473">**/API/WPR/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="99714-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="99714-474">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="99714-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="99714-475">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-475">Return data</span></span>
* <span data-ttu-id="99714-476">Devuelve el archivo ETL de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="99714-476">Returns the trace ETL file</span></span>

<span data-ttu-id="99714-477">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="99714-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="99714-478">Inicia una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="99714-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="99714-479">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99714-479">Parameters</span></span>
* <span data-ttu-id="99714-480">Perfil: nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="99714-480">profile : Profile name.</span></span> <span data-ttu-id="99714-481">Los perfiles disponibles se almacenan en perfprofiles/profiles.jsen</span><span class="sxs-lookup"><span data-stu-id="99714-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="99714-482">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="99714-482">Return data</span></span>
* <span data-ttu-id="99714-483">Al iniciar, devuelve el estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="99714-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="99714-484">Consulte también</span><span class="sxs-lookup"><span data-stu-id="99714-484">See also</span></span>
* [<span data-ttu-id="99714-485">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="99714-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="99714-486">Referencia de API principal del portal de dispositivos (UWP)</span><span class="sxs-lookup"><span data-stu-id="99714-486">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
