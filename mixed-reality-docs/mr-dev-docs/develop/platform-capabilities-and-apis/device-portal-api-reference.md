---
title: Referencia de la API del Portal de dispositivos
description: Referencia de API para Windows Device portal en HoloLens
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portal de dispositivos de Windows, API, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677974"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="4e8a2-104">Referencia de la API del Portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-104">Device portal API reference</span></span>

<span data-ttu-id="4e8a2-105">Todo lo que se encuentra en el [portal de dispositivos de Windows](using-the-windows-device-portal.md) se basa en la API de REST que puede usar para tener acceso a los datos y controlar el dispositivo mediante programación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="4e8a2-106">Implementación de aplicación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-106">App deloyment</span></span>

<span data-ttu-id="4e8a2-107">**/API/App/packagemanager/Package (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="4e8a2-108">Desinstala una aplicación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-108">Uninstalls an app</span></span>

<span data-ttu-id="4e8a2-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-109">Parameters</span></span>
* <span data-ttu-id="4e8a2-110">paquete: nombre de archivo del paquete que se va a desinstalar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="4e8a2-111">**/API/App/packagemanager/Package (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="4e8a2-112">Instala una aplicación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-112">Installs an App</span></span>

<span data-ttu-id="4e8a2-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-113">Parameters</span></span>
* <span data-ttu-id="4e8a2-114">paquete: nombre de archivo del paquete que se va a instalar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="4e8a2-115">Carga</span><span class="sxs-lookup"><span data-stu-id="4e8a2-115">Payload</span></span>
* <span data-ttu-id="4e8a2-116">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="4e8a2-116">multi-part conforming http body</span></span>

<span data-ttu-id="4e8a2-117">**/API/App/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="4e8a2-118">Recupera la lista de aplicaciones instaladas en el sistema con detalles</span><span class="sxs-lookup"><span data-stu-id="4e8a2-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="4e8a2-119">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-119">Return data</span></span>
* <span data-ttu-id="4e8a2-120">Lista de paquetes instalados con detalles</span><span class="sxs-lookup"><span data-stu-id="4e8a2-120">List of installed packages with details</span></span>

<span data-ttu-id="4e8a2-121">**/API/App/packagemanager/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="4e8a2-122">Obtiene el estado de la instalación de la aplicación en curso</span><span class="sxs-lookup"><span data-stu-id="4e8a2-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="4e8a2-123">Colección de volcados de memoria</span><span class="sxs-lookup"><span data-stu-id="4e8a2-123">Dump collection</span></span>

<span data-ttu-id="4e8a2-124">**/API/Debug/dump/usermode/CrashControl (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="4e8a2-125">Deshabilita la recopilación de volcados de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="4e8a2-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="4e8a2-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-126">Parameters</span></span>
* <span data-ttu-id="4e8a2-127">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="4e8a2-127">packageFullname : package name</span></span>

<span data-ttu-id="4e8a2-128">**/API/Debug/dump/usermode/CrashControl (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="4e8a2-129">Obtiene la configuración de la colección de volcados de memoria de aplicaciones transferidas</span><span class="sxs-lookup"><span data-stu-id="4e8a2-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="4e8a2-130">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-130">Parameters</span></span>
* <span data-ttu-id="4e8a2-131">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="4e8a2-131">packageFullname : package name</span></span>

<span data-ttu-id="4e8a2-132">**/API/Debug/dump/usermode/CrashControl (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="4e8a2-133">Habilita y establece la configuración de control de volcado para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="4e8a2-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="4e8a2-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-134">Parameters</span></span>
* <span data-ttu-id="4e8a2-135">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="4e8a2-135">packageFullname : package name</span></span>

<span data-ttu-id="4e8a2-136">**/API/Debug/dump/usermode/crashdump (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="4e8a2-137">Elimina un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="4e8a2-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="4e8a2-138">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-138">Parameters</span></span>
* <span data-ttu-id="4e8a2-139">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="4e8a2-139">packageFullname : package name</span></span>
* <span data-ttu-id="4e8a2-140">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-140">fileName : dump file name</span></span>

<span data-ttu-id="4e8a2-141">**/API/Debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="4e8a2-142">Recupera un volcado de memoria para una aplicación transferida localmente</span><span class="sxs-lookup"><span data-stu-id="4e8a2-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="4e8a2-143">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-143">Parameters</span></span>
* <span data-ttu-id="4e8a2-144">packageFullname: nombre del paquete</span><span class="sxs-lookup"><span data-stu-id="4e8a2-144">packageFullname : package name</span></span>
* <span data-ttu-id="4e8a2-145">fileName: nombre de archivo de volcado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-145">fileName : dump file name</span></span>

<span data-ttu-id="4e8a2-146">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-146">Return data</span></span>
* <span data-ttu-id="4e8a2-147">Archivo de volcado de memoria.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-147">Dump file.</span></span> <span data-ttu-id="4e8a2-148">Inspeccionar con WinDbg o Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e8a2-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="4e8a2-149">**/API/Debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="4e8a2-150">Devuelve la lista de todos los volcados de memoria de las aplicaciones transferidas localmente</span><span class="sxs-lookup"><span data-stu-id="4e8a2-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="4e8a2-151">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-151">Return data</span></span>
* <span data-ttu-id="4e8a2-152">Lista de volcados de memoria por aplicación cargada</span><span class="sxs-lookup"><span data-stu-id="4e8a2-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="4e8a2-153">ETW</span><span class="sxs-lookup"><span data-stu-id="4e8a2-153">ETW</span></span>

<span data-ttu-id="4e8a2-154">**/API/ETW/Providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="4e8a2-155">Enumera los proveedores registrados</span><span class="sxs-lookup"><span data-stu-id="4e8a2-155">Enumerates registered providers</span></span>

<span data-ttu-id="4e8a2-156">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-156">Return data</span></span>
* <span data-ttu-id="4e8a2-157">Lista de proveedores, nombre descriptivo y GUID</span><span class="sxs-lookup"><span data-stu-id="4e8a2-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="4e8a2-158">**/API/ETW/Session/Realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="4e8a2-159">Crea una sesión ETW en tiempo real; se administra a través de un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="4e8a2-160">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-160">Return data</span></span>
* <span data-ttu-id="4e8a2-161">Eventos ETW de los proveedores habilitados</span><span class="sxs-lookup"><span data-stu-id="4e8a2-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="4e8a2-162">SO Holographic</span><span class="sxs-lookup"><span data-stu-id="4e8a2-162">Holographic OS</span></span>

<span data-ttu-id="4e8a2-163">**/API/Holographic/os/ETW/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="4e8a2-164">Devuelve una lista de proveedores ETW específicos de HoloLens que no están registrados en el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="4e8a2-165">**/API/Holographic/os/Services (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="4e8a2-166">Devuelve los Estados de todos los servicios que se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-166">Returns the states of all services running.</span></span>

<span data-ttu-id="4e8a2-167">**/API/Holographic/os/Settings/IPD (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="4e8a2-168">Obtiene el IPD almacenado (distancia interpupillary) en milímetros.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="4e8a2-169">**/API/Holographic/os/Settings/IPD (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="4e8a2-170">Establece la configuración de IPD</span><span class="sxs-lookup"><span data-stu-id="4e8a2-170">Sets the IPD</span></span>

<span data-ttu-id="4e8a2-171">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-171">Parameters</span></span>
* <span data-ttu-id="4e8a2-172">IPD: nuevo valor de IPD que se establecerá en milímetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="4e8a2-173">**/API/Holographic/os/webmanagement/Settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="4e8a2-174">Obtener los requisitos de HTTPS para Device Portal</span><span class="sxs-lookup"><span data-stu-id="4e8a2-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="4e8a2-175">**/API/Holographic/os/webmanagement/Settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="4e8a2-176">Establece los requisitos de HTTPS para el portal de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="4e8a2-177">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-177">Parameters</span></span>
* <span data-ttu-id="4e8a2-178">requerido: sí, no o predeterminado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="4e8a2-179">Percepción holográfica</span><span class="sxs-lookup"><span data-stu-id="4e8a2-179">Holographic Perception</span></span>

<span data-ttu-id="4e8a2-180">**/API/Holographic/Perception/Client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="4e8a2-181">Acepta actualizaciones de WebSocket y ejecuta un cliente de percepción que envía actualizaciones a 30 fps.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="4e8a2-182">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-182">Parameters</span></span>
* <span data-ttu-id="4e8a2-183">clientmode: "Active" fuerza el modo de seguimiento visual cuando no se puede establecer de forma pasiva</span><span class="sxs-lookup"><span data-stu-id="4e8a2-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="4e8a2-184">Temperatura térmica holográfica</span><span class="sxs-lookup"><span data-stu-id="4e8a2-184">Holographic Thermal</span></span>

<span data-ttu-id="4e8a2-185">**/API/Holographic/Thermal/Stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="4e8a2-186">Obtener la fase térmica del dispositivo (0 normal, 1 cálido, 2 crítico)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="4e8a2-187">Map Manager (Administrador de mapas)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-187">Map Manager</span></span>

<span data-ttu-id="4e8a2-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="4e8a2-189">Obtiene la lista de archivos de asignación disponibles (. MAPX).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="4e8a2-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="4e8a2-191">Obtiene la lista de archivos de delimitador disponibles (. ancx).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="4e8a2-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="4e8a2-193">Obtiene la lista de archivos de base de datos de reconstrucción espacial disponibles (. srdb).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="4e8a2-194">**/API/Holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="4e8a2-195">Obtiene la lista de delimitadores persistentes para el usuario actual.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="4e8a2-196">Descargar/cargar/eliminar archivos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="4e8a2-197">**/API/Holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="4e8a2-198">Descarga un mapa, un delimitador o un archivo de base de datos de reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="4e8a2-199">El archivo se debe haber cargado o exportado previamente.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="4e8a2-200">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-200">Parameters</span></span>
* <span data-ttu-id="4e8a2-201">FileName: nombre del archivo que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="4e8a2-202">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="4e8a2-203">**/API/Holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="4e8a2-204">Carga un archivo de base de datos de asignación, delimitador o reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="4e8a2-205">Una vez que se carga un archivo, se puede importar posteriormente para que lo use el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="4e8a2-206">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-206">Parameters</span></span>
* <span data-ttu-id="4e8a2-207">archivo: nombre del archivo que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="4e8a2-208">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-208">Example:</span></span>
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

<span data-ttu-id="4e8a2-209">**/API/Holographic/mapmanager/Delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="4e8a2-210">Elimina un mapa, un delimitador o un archivo de base de datos de reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="4e8a2-211">El archivo se debe haber cargado o exportado previamente.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="4e8a2-212">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-212">Parameters</span></span>
* <span data-ttu-id="4e8a2-213">FileName: nombre del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="4e8a2-214">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="4e8a2-215">Exportación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-215">Export</span></span>

<span data-ttu-id="4e8a2-216">**/API/Holographic/mapmanager/Export (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="4e8a2-217">Exporta el mapa actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="4e8a2-218">Una vez exportado, se puede descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="4e8a2-219">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="4e8a2-220">**/API/Holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="4e8a2-221">Exporta el mapa actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="4e8a2-222">Una vez exportado, se puede descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="4e8a2-223">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="4e8a2-224">**/API/Holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="4e8a2-225">Exporta el mapa y los delimitadores actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="4e8a2-226">Una vez que se exporten, se pueden descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="4e8a2-227">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="4e8a2-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="4e8a2-229">Exporta el mapa y la base de datos de reconstrucción espacial actualmente en uso por el sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="4e8a2-230">Una vez exportados, se pueden descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="4e8a2-231">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="4e8a2-232">Importar</span><span class="sxs-lookup"><span data-stu-id="4e8a2-232">Import</span></span>

<span data-ttu-id="4e8a2-233">**/API/Holographic/mapmanager/Import (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="4e8a2-234">Indica al sistema qué asignación debe usarse actualmente.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="4e8a2-235">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="4e8a2-236">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-236">Parameters</span></span>
* <span data-ttu-id="4e8a2-237">Nombre de archivo: nombre del mapa que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="4e8a2-238">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="4e8a2-239">**/API/Holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="4e8a2-240">Indica al sistema qué delimitadores deben usarse actualmente.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="4e8a2-241">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="4e8a2-242">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-242">Parameters</span></span>
* <span data-ttu-id="4e8a2-243">Nombre de archivo: nombre de los delimitadores que se van a utilizar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="4e8a2-244">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="4e8a2-245">**/API/Holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="4e8a2-246">Indica al sistema qué base de datos de reconstrucción espacial se debe utilizar actualmente.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="4e8a2-247">Se puede llamar en los archivos que se han exportado o cargado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="4e8a2-248">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-248">Parameters</span></span>
* <span data-ttu-id="4e8a2-249">Nombre de archivo: nombre de la base de de asignación espacial que se va a usar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="4e8a2-250">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="4e8a2-251">Otros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-251">Other</span></span>

<span data-ttu-id="4e8a2-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="4e8a2-253">Restablezca el sistema en la base de datos de asignaciones, delimitadores y reconstrucción espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="4e8a2-254">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="4e8a2-255">**/API/Holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="4e8a2-256">Obtiene el estado del sistema, incluidos los archivos de base de datos de asignación, delimitadores y reconstrucción espacial que se importaron por última vez.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="4e8a2-257">Captura de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4e8a2-257">Mixed Reality Capture</span></span>

<span data-ttu-id="4e8a2-258">**/API/Holographic/MRC/File (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="4e8a2-259">Descarga un archivo de realidad mixta desde el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="4e8a2-260">Use OP = parámetro de consulta de transmisión por secuencias.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="4e8a2-261">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-261">Parameters</span></span>
* <span data-ttu-id="4e8a2-262">Filename: nombre, hex64 codificado, del archivo de vídeo que se va a obtener</span><span class="sxs-lookup"><span data-stu-id="4e8a2-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="4e8a2-263">OP: Stream</span><span class="sxs-lookup"><span data-stu-id="4e8a2-263">op : stream</span></span>

<span data-ttu-id="4e8a2-264">**/API/Holographic/MRC/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="4e8a2-265">Elimina una grabación de realidad mixta del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="4e8a2-266">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-266">Parameters</span></span>
* <span data-ttu-id="4e8a2-267">Filename: nombre, hex64 codificado, del archivo que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="4e8a2-268">**/API/Holographic/MRC/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="4e8a2-269">Devuelve la lista de archivos de realidad mixta almacenados en el dispositivo</span><span class="sxs-lookup"><span data-stu-id="4e8a2-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="4e8a2-270">**/API/Holographic/MRC/Photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="4e8a2-271">Toma una fotografía de realidad mixta y crea un archivo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="4e8a2-272">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-272">Parameters</span></span>
* <span data-ttu-id="4e8a2-273">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-274">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-275">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="4e8a2-276">**/API/Holographic/MRC/Settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="4e8a2-277">Obtiene la configuración de captura de realidad mixta predeterminada</span><span class="sxs-lookup"><span data-stu-id="4e8a2-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="4e8a2-278">**/API/Holographic/MRC/Settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="4e8a2-279">Establece la configuración de captura de realidad mixta predeterminada.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="4e8a2-280">Algunos de estos valores se aplican a la captura de vídeo y fotos de MRC del sistema.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="4e8a2-281">**/API/Holographic/MRC/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="4e8a2-282">Obtiene el estado de la captura de realidad mixta en el portal de dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="4e8a2-283">\**_Respuesta_* _</span><span class="sxs-lookup"><span data-stu-id="4e8a2-283">\**_Response_* _</span></span>

<span data-ttu-id="4e8a2-284">La respuesta contiene una propiedad JSON que indica si el portal de dispositivos de Windows está grabando vídeo o no.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="4e8a2-285">_ */API/Holographic/MRC/Thumbnail (GET)*\*</span><span class="sxs-lookup"><span data-stu-id="4e8a2-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="4e8a2-286">Obtiene la imagen en miniatura del archivo especificado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="4e8a2-287">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-287">Parameters</span></span>
* <span data-ttu-id="4e8a2-288">Filename: nombre, hex64 codificado, del archivo para el que se solicita la miniatura</span><span class="sxs-lookup"><span data-stu-id="4e8a2-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="4e8a2-289">**/API/Holographic/MRC/video/control/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="4e8a2-290">Inicia una grabación de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4e8a2-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="4e8a2-291">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-291">Parameters</span></span>
* <span data-ttu-id="4e8a2-292">hololens: Capture hologramas: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-293">PV: capturar la cámara PV: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-294">MIC: Capture Microphone: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-295">bucle invertido: captura de audio de la aplicación: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-296">RenderFromCamera: (solo HoloLens 2) presentación desde la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="4e8a2-297">Vstab: (solo HoloLens 2) habilitar estabilización de vídeo: true o false (el valor predeterminado es true)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="4e8a2-298">vstabbuffer: (solo HoloLens 2) latencia de búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="4e8a2-299">**/API/Holographic/MRC/video/control/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="4e8a2-300">Detiene la grabación de realidad mixta actual</span><span class="sxs-lookup"><span data-stu-id="4e8a2-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="4e8a2-301">Streaming de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4e8a2-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="4e8a2-302">HoloLens admite la vista previa dinámica de la realidad mixta a través de la descarga fragmentada de un MP4 fragmentado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="4e8a2-303">Los flujos de realidad mixta comparten el mismo conjunto de parámetros para controlar lo que se captura:</span><span class="sxs-lookup"><span data-stu-id="4e8a2-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="4e8a2-304">hololens: capturar hologramas: true o false</span><span class="sxs-lookup"><span data-stu-id="4e8a2-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="4e8a2-305">PV: capturar la cámara PV: true o false</span><span class="sxs-lookup"><span data-stu-id="4e8a2-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="4e8a2-306">MIC: capturar micrófono: true o false</span><span class="sxs-lookup"><span data-stu-id="4e8a2-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="4e8a2-307">bucle invertido: captura de audio de la aplicación: true o false</span><span class="sxs-lookup"><span data-stu-id="4e8a2-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="4e8a2-308">Si no se especifica ninguno de estos: los hologramas, la cámara de foto/vídeo y el audio de la aplicación se capturarán</span><span class="sxs-lookup"><span data-stu-id="4e8a2-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="4e8a2-309">Si se especifica any: los parámetros no especificados tendrán como valor predeterminado False.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="4e8a2-310">Parámetros opcionales (solo HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="4e8a2-311">RenderFromCamera: representación de la perspectiva de la cámara de foto/vídeo: true o false (el valor predeterminado es true).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="4e8a2-312">Vstab: habilitar estabilización de vídeo: true o false (el valor predeterminado es false)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="4e8a2-313">vstabbuffer: latencia del búfer de estabilización de vídeo: de 0 a 30 fotogramas (el valor predeterminado es 15 fotogramas)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="4e8a2-314">**live.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="4e8a2-315">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="4e8a2-316">**live_high.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="4e8a2-317">1280x720p 30 fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="4e8a2-318">**live_med.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="4e8a2-319">Una secuencia de 854x480p 30 fps 2.5 Mbit.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="4e8a2-320">**live_low.mp4/API/Holographic/Stream/(GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="4e8a2-321">Una secuencia de 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="4e8a2-322">Redes</span><span class="sxs-lookup"><span data-stu-id="4e8a2-322">Networking</span></span>

<span data-ttu-id="4e8a2-323">**/API/Networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="4e8a2-324">Obtiene la configuración de IP actual.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="4e8a2-325">Información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="4e8a2-325">OS Information</span></span>

<span data-ttu-id="4e8a2-326">**/API/os/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="4e8a2-327">Obtiene información del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="4e8a2-327">Gets operating system information</span></span>

<span data-ttu-id="4e8a2-328">**/API/os/MachineName (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="4e8a2-329">Obtiene el nombre de la máquina.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-329">Gets the machine name</span></span>

<span data-ttu-id="4e8a2-330">**/API/os/MachineName (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="4e8a2-331">Establece el nombre de la máquina</span><span class="sxs-lookup"><span data-stu-id="4e8a2-331">Sets the machine name</span></span>

<span data-ttu-id="4e8a2-332">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-332">Parameters</span></span>
* <span data-ttu-id="4e8a2-333">Nombre: nuevo nombre del equipo, hex64 codificado, para establecer en</span><span class="sxs-lookup"><span data-stu-id="4e8a2-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="4e8a2-334">Control de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="4e8a2-334">Perception Simulation Control</span></span>

<span data-ttu-id="4e8a2-335">**/API/Holographic/Simulation/control/MODE (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="4e8a2-336">Obtención del modo de simulación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-336">Get the simulation mode</span></span>

<span data-ttu-id="4e8a2-337">**/API/Holographic/Simulation/control/MODE (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="4e8a2-338">Establecer el modo de simulación</span><span class="sxs-lookup"><span data-stu-id="4e8a2-338">Set the simulation mode</span></span>

<span data-ttu-id="4e8a2-339">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-339">Parameters</span></span>
* <span data-ttu-id="4e8a2-340">modo de simulación: predeterminado, simulación, remoto, heredado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="4e8a2-341">**/API/Holographic/Simulation/control/Stream (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="4e8a2-342">Elimine un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-342">Delete a control stream.</span></span>

<span data-ttu-id="4e8a2-343">**/API/Holographic/Simulation/control/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="4e8a2-344">Abra una conexión de socket web para un flujo de control.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="4e8a2-345">**/API/Holographic/Simulation/control/Stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="4e8a2-346">Cree un flujo de control (se requiere prioridad) o publique los datos en un flujo creado (streamId obligatorio).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="4e8a2-347">Se espera que los datos expuestos sean del tipo "application/octet-stream".</span><span class="sxs-lookup"><span data-stu-id="4e8a2-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="4e8a2-348">**/API/Holographic/Simulation/display/Stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="4e8a2-349">Solicitar una secuencia de vídeo de simulación que contenga el contenido representado en la pantalla del sistema cuando esté en modo de ' simulación '.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="4e8a2-350">Inicialmente, se enviará un encabezado de descriptor de formato simple, seguido de las texturas codificadas en H. 264, cada una precedida por un encabezado que indica el índice ocular y el tamaño de la textura.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="4e8a2-351">Reproducción de la simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="4e8a2-351">Perception Simulation Playback</span></span>

<span data-ttu-id="4e8a2-352">**/API/Holographic/Simulation/Playback/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="4e8a2-353">Elimina una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-353">Delete a recording.</span></span>

<span data-ttu-id="4e8a2-354">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-354">Parameters</span></span>
* <span data-ttu-id="4e8a2-355">grabación: nombre de la grabación que se va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="4e8a2-356">**/API/Holographic/Simulation/Playback/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="4e8a2-357">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-357">Upload a recording.</span></span>

<span data-ttu-id="4e8a2-358">**/API/Holographic/Simulation/Playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="4e8a2-359">Obtener todas las grabaciones.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-359">Get all recordings.</span></span>

<span data-ttu-id="4e8a2-360">**/API/Holographic/Simulation/Playback/Session (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="4e8a2-361">Obtiene el estado de reproducción actual de una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="4e8a2-362">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-362">Parameters</span></span>
* <span data-ttu-id="4e8a2-363">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-363">recording : Name of recording.</span></span>

<span data-ttu-id="4e8a2-364">**/API/Holographic/Simulation/Playback/Session/File (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="4e8a2-365">Descargar una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-365">Unload a recording.</span></span>

<span data-ttu-id="4e8a2-366">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-366">Parameters</span></span>
* <span data-ttu-id="4e8a2-367">grabación: nombre de la grabación que se va a descargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="4e8a2-368">**/API/Holographic/Simulation/Playback/Session/File (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="4e8a2-369">Carga de una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-369">Load a recording.</span></span>

<span data-ttu-id="4e8a2-370">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-370">Parameters</span></span>
* <span data-ttu-id="4e8a2-371">grabación: nombre de la grabación que se va a cargar.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="4e8a2-372">**/API/Holographic/Simulation/Playback/Session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="4e8a2-373">Obtiene todas las grabaciones cargadas.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-373">Get all loaded recordings.</span></span>

<span data-ttu-id="4e8a2-374">**/API/Holographic/Simulation/Playback/Session/PAUSE (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="4e8a2-375">Pausar una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-375">Pause a recording.</span></span>

<span data-ttu-id="4e8a2-376">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-376">Parameters</span></span>
* <span data-ttu-id="4e8a2-377">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-377">recording : Name of recording.</span></span>

<span data-ttu-id="4e8a2-378">**/API/Holographic/Simulation/Playback/Session/Play (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="4e8a2-379">Reproducir una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-379">Play a recording.</span></span>

<span data-ttu-id="4e8a2-380">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-380">Parameters</span></span>
* <span data-ttu-id="4e8a2-381">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-381">recording : Name of recording.</span></span>

<span data-ttu-id="4e8a2-382">**/API/Holographic/Simulation/Playback/Session/STOP (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="4e8a2-383">Detener una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-383">Stop a recording.</span></span>

<span data-ttu-id="4e8a2-384">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-384">Parameters</span></span>
* <span data-ttu-id="4e8a2-385">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-385">recording : Name of recording.</span></span>

<span data-ttu-id="4e8a2-386">**/API/Holographic/Simulation/Playback/Session/Types (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="4e8a2-387">Obtiene los tipos de datos en una grabación cargada.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="4e8a2-388">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-388">Parameters</span></span>
* <span data-ttu-id="4e8a2-389">grabación: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="4e8a2-390">Grabación de simulación de percepción</span><span class="sxs-lookup"><span data-stu-id="4e8a2-390">Perception Simulation Recording</span></span>

<span data-ttu-id="4e8a2-391">**/API/Holographic/Simulation/Recording/Start (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="4e8a2-392">Iniciar una grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-392">Start a recording.</span></span> <span data-ttu-id="4e8a2-393">Solo puede haber una grabación activa al mismo tiempo.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="4e8a2-394">Debe establecerse una de las clases Head, Hand, spatialMapping o Environment.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="4e8a2-395">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-395">Parameters</span></span>
* <span data-ttu-id="4e8a2-396">Head: establézcalo en 1 para registrar los datos principales.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="4e8a2-397">manos: establézcalo en 1 para registrar los datos de la mano.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="4e8a2-398">spatialMapping: establézcalo en 1 para registrar la asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="4e8a2-399">entorno: establézcalo en 1 para registrar los datos del entorno.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="4e8a2-400">Nombre: nombre de la grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-400">name : Name of the recording.</span></span>
* <span data-ttu-id="4e8a2-401">singleSpatialMappingFrame: establézcalo en 1 para registrar solo un marco de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="4e8a2-402">**/API/Holographic/Simulation/Recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="4e8a2-403">Obtiene el estado de grabación.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-403">Get recording state.</span></span>

<span data-ttu-id="4e8a2-404">**/API/Holographic/Simulation/Recording/STOP (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="4e8a2-405">Detener la grabación actual.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-405">Stop the current recording.</span></span> <span data-ttu-id="4e8a2-406">La grabación se devolverá como un archivo.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="4e8a2-407">Datos de rendimiento</span><span class="sxs-lookup"><span data-stu-id="4e8a2-407">Performance data</span></span>

<span data-ttu-id="4e8a2-408">**/API/ResourceManager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="4e8a2-409">Devuelve la lista de procesos en ejecución con detalles</span><span class="sxs-lookup"><span data-stu-id="4e8a2-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="4e8a2-410">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-410">Return data</span></span>
* <span data-ttu-id="4e8a2-411">JSON con la lista de procesos y detalles de cada proceso</span><span class="sxs-lookup"><span data-stu-id="4e8a2-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="4e8a2-412">**/API/ResourceManager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="4e8a2-413">Devuelve las estadísticas de rendimiento del sistema (e/s de lectura/escritura, estadísticas de memoria, etc.).</span><span class="sxs-lookup"><span data-stu-id="4e8a2-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="4e8a2-414">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-414">Return data</span></span>
* <span data-ttu-id="4e8a2-415">JSON con información del sistema: CPU, GPU, memoria, red, e/s</span><span class="sxs-lookup"><span data-stu-id="4e8a2-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="4e8a2-416">Power</span><span class="sxs-lookup"><span data-stu-id="4e8a2-416">Power</span></span>

<span data-ttu-id="4e8a2-417">**/API/Power/Battery (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="4e8a2-418">Obtiene el estado actual de la batería</span><span class="sxs-lookup"><span data-stu-id="4e8a2-418">Gets the current battery state</span></span>

<span data-ttu-id="4e8a2-419">**/API/Power/State (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="4e8a2-420">Comprueba si el sistema está en un estado de baja energía.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="4e8a2-421">Control remoto</span><span class="sxs-lookup"><span data-stu-id="4e8a2-421">Remote Control</span></span>

<span data-ttu-id="4e8a2-422">**/API/control/Restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="4e8a2-423">Reinicia el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="4e8a2-423">Restarts the target device</span></span>

<span data-ttu-id="4e8a2-424">**/API/control/Shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="4e8a2-425">Apaga el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="4e8a2-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="4e8a2-426">Administrador de tareas</span><span class="sxs-lookup"><span data-stu-id="4e8a2-426">Task Manager</span></span>

<span data-ttu-id="4e8a2-427">**/API/TaskManager/App (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="4e8a2-428">Detiene una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="4e8a2-428">Stops a modern app</span></span>

<span data-ttu-id="4e8a2-429">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-429">Parameters</span></span>
* <span data-ttu-id="4e8a2-430">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="4e8a2-431">forcestop: forzar la detención de todos los procesos (= sí)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="4e8a2-432">**/API/TaskManager/App (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="4e8a2-433">Inicia una aplicación moderna</span><span class="sxs-lookup"><span data-stu-id="4e8a2-433">Starts a modern app</span></span>

<span data-ttu-id="4e8a2-434">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-434">Parameters</span></span>
* <span data-ttu-id="4e8a2-435">AppID: PRAID de la aplicación que se va a iniciar, hex64 codificada</span><span class="sxs-lookup"><span data-stu-id="4e8a2-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="4e8a2-436">paquete: nombre completo del paquete de la aplicación, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="4e8a2-437">Administración de WiFi</span><span class="sxs-lookup"><span data-stu-id="4e8a2-437">WiFi Management</span></span>

<span data-ttu-id="4e8a2-438">**/API/WiFi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="4e8a2-439">Enumera las interfaces de red inalámbrica</span><span class="sxs-lookup"><span data-stu-id="4e8a2-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="4e8a2-440">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-440">Return data</span></span>
* <span data-ttu-id="4e8a2-441">Lista de interfaces inalámbricas con detalles (GUID, descripción, etc.)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="4e8a2-442">**/API/WiFi/Network (eliminar)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="4e8a2-443">Elimina un perfil asociado a una red en una interfaz especificada.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="4e8a2-444">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-444">Parameters</span></span>
* <span data-ttu-id="4e8a2-445">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="4e8a2-445">interface : network interface guid</span></span>
* <span data-ttu-id="4e8a2-446">Perfil: nombre del perfil</span><span class="sxs-lookup"><span data-stu-id="4e8a2-446">profile : profile name</span></span>

<span data-ttu-id="4e8a2-447">**/API/WiFi/Networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="4e8a2-448">Enumera las redes inalámbricas de la interfaz de red especificada</span><span class="sxs-lookup"><span data-stu-id="4e8a2-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="4e8a2-449">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-449">Parameters</span></span>
* <span data-ttu-id="4e8a2-450">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="4e8a2-450">interface : network interface guid</span></span>

<span data-ttu-id="4e8a2-451">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-451">Return data</span></span>
* <span data-ttu-id="4e8a2-452">Lista de redes inalámbricas encontradas en la interfaz de red con detalles</span><span class="sxs-lookup"><span data-stu-id="4e8a2-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="4e8a2-453">**/API/WiFi/Network (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="4e8a2-454">Conecta o desconecta una red de la interfaz especificada</span><span class="sxs-lookup"><span data-stu-id="4e8a2-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="4e8a2-455">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-455">Parameters</span></span>
* <span data-ttu-id="4e8a2-456">interfaz: GUID de la interfaz de red</span><span class="sxs-lookup"><span data-stu-id="4e8a2-456">interface : network interface guid</span></span>
* <span data-ttu-id="4e8a2-457">SSID: SSID, hex64 codificado, para conectarse</span><span class="sxs-lookup"><span data-stu-id="4e8a2-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="4e8a2-458">OP: conectar o desconectar</span><span class="sxs-lookup"><span data-stu-id="4e8a2-458">op : connect or disconnect</span></span>
* <span data-ttu-id="4e8a2-459">createprofile: sí o no</span><span class="sxs-lookup"><span data-stu-id="4e8a2-459">createprofile : yes or no</span></span>
* <span data-ttu-id="4e8a2-460">clave: clave compartida, hex64 codificado</span><span class="sxs-lookup"><span data-stu-id="4e8a2-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="4e8a2-461">Grabadora de rendimiento de Windows</span><span class="sxs-lookup"><span data-stu-id="4e8a2-461">Windows Performance Recorder</span></span>

<span data-ttu-id="4e8a2-462">**/API/WPR/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="4e8a2-463">Carga un perfil de WPR e inicia el seguimiento con el perfil cargado.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="4e8a2-464">Carga</span><span class="sxs-lookup"><span data-stu-id="4e8a2-464">Payload</span></span>
* <span data-ttu-id="4e8a2-465">cuerpo http compatible con varias partes</span><span class="sxs-lookup"><span data-stu-id="4e8a2-465">multi-part conforming http body</span></span>

<span data-ttu-id="4e8a2-466">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-466">Return data</span></span>
* <span data-ttu-id="4e8a2-467">Devuelve el estado de sesión WPR.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-467">Returns the WPR session status.</span></span>

<span data-ttu-id="4e8a2-468">**/API/WPR/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="4e8a2-469">Recupera el estado de la sesión de WPR</span><span class="sxs-lookup"><span data-stu-id="4e8a2-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="4e8a2-470">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-470">Return data</span></span>
* <span data-ttu-id="4e8a2-471">Estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-471">WPR session status.</span></span>

<span data-ttu-id="4e8a2-472">**/API/WPR/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="4e8a2-473">Detiene una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="4e8a2-474">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-474">Return data</span></span>
* <span data-ttu-id="4e8a2-475">Devuelve el archivo ETL de seguimiento.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-475">Returns the trace ETL file</span></span>

<span data-ttu-id="4e8a2-476">**/API/WPR/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="4e8a2-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="4e8a2-477">Inicia una sesión de seguimiento de WPR (rendimiento)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="4e8a2-478">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4e8a2-478">Parameters</span></span>
* <span data-ttu-id="4e8a2-479">Perfil: nombre del perfil.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-479">profile : Profile name.</span></span> <span data-ttu-id="4e8a2-480">Los perfiles disponibles se almacenan en perfprofiles/profiles.jsen</span><span class="sxs-lookup"><span data-stu-id="4e8a2-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="4e8a2-481">Devolver datos</span><span class="sxs-lookup"><span data-stu-id="4e8a2-481">Return data</span></span>
* <span data-ttu-id="4e8a2-482">Al iniciar, devuelve el estado de la sesión de WPR.</span><span class="sxs-lookup"><span data-stu-id="4e8a2-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e8a2-483">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4e8a2-483">See also</span></span>
* [<span data-ttu-id="4e8a2-484">Uso del Portal de dispositivos Windows</span><span class="sxs-lookup"><span data-stu-id="4e8a2-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="4e8a2-485">Referencia de API principal del portal de dispositivos (UWP)</span><span class="sxs-lookup"><span data-stu-id="4e8a2-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
