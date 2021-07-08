---
title: Notas de la versión del complemento Mixed Reality OpenXR
description: Manténgase al día con las notas de la versión y las actualizaciones más recientes del complemento Mixed Reality OpenXR.
author: hferrone
ms.author: v-hferrone
ms.date: 06/18/2021
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit, mixed reality headset, windows mixed reality headset, virtual reality headset, installation, Windows, HoloLens, emulator, unreal, openxr
ms.openlocfilehash: c926fbb758d7cfaa2e73b5357cacdab7a5d15e27
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394633"
---
# <a name="mixed-reality-openxr-plugin-release-notes"></a><span data-ttu-id="997c1-104">Notas de la versión del complemento Mixed Reality OpenXR</span><span class="sxs-lookup"><span data-stu-id="997c1-104">Mixed Reality OpenXR plugin release notes</span></span>

## <a name="100---current-release"></a><span data-ttu-id="997c1-105">1.0.0: Versión actual</span><span class="sxs-lookup"><span data-stu-id="997c1-105">1.0.0 - Current release</span></span>

* <span data-ttu-id="997c1-106">Se ha corregido un error por el que XRAnchorSubsystem siempre se iniciaba al iniciar la aplicación, independientemente de la presencia de ARAnchorManager.</span><span class="sxs-lookup"><span data-stu-id="997c1-106">Fixed a bug where a the XRAnchorSubsystem was always started on app start regardless ARAnchorManager’s present.</span></span>
* <span data-ttu-id="997c1-107">Se ha corregido un error por el que el modo de reproyección no funcionaba correctamente.</span><span class="sxs-lookup"><span data-stu-id="997c1-107">Fixed a bug where the reprojection mode didn’t work properly.</span></span>

## <a name="100-preview2---2021-06-14"></a><span data-ttu-id="997c1-108">1.0.0-preview.2: 14/06/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-108">1.0.0-preview.2 - 2021-06-14</span></span>

* <span data-ttu-id="997c1-109">Depende del complemento OpenXR 1.2.2 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-109">Depends on Unity’s 1.2.2 OpenXR plugin.</span></span>
* <span data-ttu-id="997c1-110">Se han cambiado las características de Holographic Remoting (Comunicación remota holográfica) en grupos de características individuales.</span><span class="sxs-lookup"><span data-stu-id="997c1-110">Changed Holographic Remoting features in to individual feature groups.</span></span>
* <span data-ttu-id="997c1-111">Se ha corregido un error por el que "Apply HoloLens 2 project settings" (Aplicar configuración del proyecto de HoloLens 2) cambiaba el espacio de color del proyecto.</span><span class="sxs-lookup"><span data-stu-id="997c1-111">Fixed a bug where “Apply HoloLens 2 project settings” changes project color space.</span></span> <span data-ttu-id="997c1-112">Esto ya no es necesario después del complemento OpenXR 1.2.0 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-112">This is no longer needed after Unity OpenXR 1.2.0 plugin.</span></span>
* <span data-ttu-id="997c1-113">Se ha corregido un error por el que un dispositivo de entrada se conectaba sin desconectarse después de que la aplicación se suspendiera y reanudara.</span><span class="sxs-lookup"><span data-stu-id="997c1-113">Fixed a bug where a input device get connected without disconnect after application suspended and resumed.</span></span>
* <span data-ttu-id="997c1-114">Se ha agregado compatibilidad para detectar el complemento y los estados de seguimiento actuales a través de ARSession.</span><span class="sxs-lookup"><span data-stu-id="997c1-114">Added support for detecting plugin and current tracking states via ARSession.</span></span>
* <span data-ttu-id="997c1-115">Se ha corregido un error por el que el objeto prefababricado "AR Default Plane" (plano predeterminado de AR) de ARFoundation no era visible.</span><span class="sxs-lookup"><span data-stu-id="997c1-115">Fixed a bug where the “AR Default Plane” ARFoundation prefab wouldn’t be visible.</span></span>

## <a name="100-preview1---2021-06-02"></a><span data-ttu-id="997c1-116">1.0.0-preview.1: 02/06/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-116">1.0.0-preview.1 - 2021-06-02</span></span>

* <span data-ttu-id="997c1-117">Admite las extensiones MSFT de descripción de escenas de OpenXR en lugar de las extensiones de la versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="997c1-117">Supports OpenXR scene understanding MSFT extensions instead of preview extensions.</span></span>
* <span data-ttu-id="997c1-118">La detección de plano en HoloLens 2 ya no requiere versiones preliminares de los entornos en tiempo de ejecución de Mixed Reality OpenXR.</span><span class="sxs-lookup"><span data-stu-id="997c1-118">Plane detection on HoloLens 2 no longer requires preview versions of the Mixed Reality OpenXR runtimes.</span></span>

## <a name="095---2021-05-21"></a><span data-ttu-id="997c1-119">0.9.5: 21/05/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-119">0.9.5 - 2021-05-21</span></span>

* <span data-ttu-id="997c1-120">Depende del complemento OpenXR 1.2.0 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-120">Depends on Unity’s 1.2.0 OpenXR Plugin</span></span>
* <span data-ttu-id="997c1-121">Se ha adaptado a la nueva interfaz de usuario de características (en el complemento de OpenXR 1.2.0) para la configuración.</span><span class="sxs-lookup"><span data-stu-id="997c1-121">Adapted to the new feature UI (in OpenXR Plugin 1.2.0) for configuration.</span></span>
* <span data-ttu-id="997c1-122">Se ha corregido un error por el que el proveedor de cámaras localizables no anulaba el registro correctamente.</span><span class="sxs-lookup"><span data-stu-id="997c1-122">Fixed a bug where the locatable camera provider wasn’t properly unregistering.</span></span>
* <span data-ttu-id="997c1-123">Se han limpiado algunos usos adicionales de [Preserve].</span><span class="sxs-lookup"><span data-stu-id="997c1-123">Cleaned up some extra usages of [Preserve].</span></span>
* <span data-ttu-id="997c1-124">Se ha actualizado el nombre "HP Reverb G2 Controller (OpenXR)" en la interfaz de usuario del sistema de entrada.</span><span class="sxs-lookup"><span data-stu-id="997c1-124">Update “HP Reverb G2 Controller (OpenXR)” name in the input system UI.</span></span>

## <a name="094---2021-05-20"></a><span data-ttu-id="997c1-125">0.9.4: 20/05/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-125">0.9.4 - 2021-05-20</span></span>

* <span data-ttu-id="997c1-126">Depende del complemento OpenXR 1.2.0 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-126">Depends on Unity’s 1.2.0 OpenXR Plugin.</span></span>
* <span data-ttu-id="997c1-127">Se ha agregado una nueva API de C# para obtener el modelo glTF del controlador de movimiento.</span><span class="sxs-lookup"><span data-stu-id="997c1-127">Added new C# API to get motion controller glTF model.</span></span>
* <span data-ttu-id="997c1-128">Se ha agregado una nueva API de C# para habilitar las configuraciones de vista y establecer la configuración de reproyección.</span><span class="sxs-lookup"><span data-stu-id="997c1-128">Added new C# API to get enabled view configurations and set reprojection settings.</span></span>
* <span data-ttu-id="997c1-129">Se ha agregado una nueva API de C# para establecer configuraciones adicionales para calcular mallas con XRMeshSubsystem.</span><span class="sxs-lookup"><span data-stu-id="997c1-129">Added new C# API to set additional settings for computing meshes with XRMeshSubsystem.</span></span>
* <span data-ttu-id="997c1-130">Se ha agregado una nueva API de C# para configurar y suscribirse a eventos de reconocimiento de gestos.</span><span class="sxs-lookup"><span data-stu-id="997c1-130">Added new C# API to configure and subscribe to gesture recognition events.</span></span>
* <span data-ttu-id="997c1-131">Se ha agregado el cuadro de diálogo de configuración Windows->XR->Editor Remoting (Comunicación remota del editor).</span><span class="sxs-lookup"><span data-stu-id="997c1-131">Added Windows->XR->Editor Remoting settings dialog.</span></span>
* <span data-ttu-id="997c1-132">Se ha agregado compatibilidad con ARM para aplicaciones para UWP en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="997c1-132">Added ARM support for HoloLens UWP applications.</span></span>

## <a name="093---2021-04-29"></a><span data-ttu-id="997c1-133">0.9.3: 29/04/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-133">0.9.3 - 2021-04-29</span></span>

* <span data-ttu-id="997c1-134">Se ha corregido un error por el que la conexión de conexión remota holográfica no era confiable.</span><span class="sxs-lookup"><span data-stu-id="997c1-134">Fixed a bug where Holographic remoting connection is not reliable</span></span>
* <span data-ttu-id="997c1-135">Se ha corregido un error por el que el rendimiento de la representación de VR era poco óptimo después de actualizar al complemento OpenXR 1.1.1 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-135">Fixed a bug where the VR rendering performance is sub-optimum after upgrade to Unity’s 1.1.1 OpenXR plugin.</span></span>

## <a name="092---2021-04-21"></a><span data-ttu-id="997c1-136">0.9.2: 21/04/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-136">0.9.2 - 2021-04-21</span></span>

* <span data-ttu-id="997c1-137">La detección de plano en HoloLens 2 en la versión 0.9.1 del complemento funcionará con la versión 105 del entorno en tiempo de ejecución de Mixed Reality OpenXR en versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="997c1-137">Plane detection on HoloLens 2 in plugin version 0.9.1 will work with version 105 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="997c1-138">La detección de plano en HoloLens 2 en la versión 0.9.2 del complemento funcionará con la versión 106 del entorno en tiempo de ejecución de Mixed Reality OpenXR en versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="997c1-138">Plane detection on HoloLens 2 in plugin version 0.9.2 will work with version 106 of the Mixed Reality OpenXR preview runtime.</span></span>
* <span data-ttu-id="997c1-139">Se han quitado algunas devoluciones de llamada no utilizadas de InputProvider para evitar que llamadas como XRInputSubsystem.\* GetTrackingOriginMode (que nuestro sistema de entrada no administra) devuelvan resultados correctos con valores engañosos.</span><span class="sxs-lookup"><span data-stu-id="997c1-139">Removed some unused callbacks from InputProvider to prevent calls like XRInputSubsystem.\* GetTrackingOriginMode (which aren’t managed by our input system) from returning success with misleading values.</span></span>
* <span data-ttu-id="997c1-140">Se ha dividido la versión en desuso de XRAnchorStore en su propio archivo para evitar la advertencia de la consola de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-140">Split out deprecated version of XRAnchorStore into its own file to prevent Unity console warning.</span></span>

## <a name="091---2021-04-20"></a><span data-ttu-id="997c1-141">0.9.1: 20/04/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-141">0.9.1 - 2021-04-20</span></span>

* <span data-ttu-id="997c1-142">Depende del complemento OpenXR 1.1.1 de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-142">Depends on Unity’s 1.1.1 OpenXR Plugin.</span></span>
* <span data-ttu-id="997c1-143">Se ha agregado compatibilidad con la aplicación Holographic Remoting (Comunicación remota holográfica) para la plataforma UWP.</span><span class="sxs-lookup"><span data-stu-id="997c1-143">Added support for Holographic Remoting application for UWP platform.</span></span>
* <span data-ttu-id="997c1-144">Se ha corregido UnityException en la que XRAnchorStore intentaba obtener una instancia de configuración fuera del subproceso principal.</span><span class="sxs-lookup"><span data-stu-id="997c1-144">Fix UnityException where XRAnchorStore was trying to get a settings instance outside the main thread.</span></span>

## <a name="090---2021-03-29"></a><span data-ttu-id="997c1-145">0.9.0: 29/03/2021</span><span class="sxs-lookup"><span data-stu-id="997c1-145">0.9.0 - 2021-03-29</span></span>

* <span data-ttu-id="997c1-146">Se ha agregado compatibilidad con la asignación espacial a través de XRMeshSubsystem y ARMeshManager.</span><span class="sxs-lookup"><span data-stu-id="997c1-146">Added support for spatial mapping via XRMeshSubsystem and ARMeshManager.</span></span>
* <span data-ttu-id="997c1-147">Se ha agregado una nueva API de C# para que los identificadores de OpenXR admitan otras extensiones de OpenXR de consumo de paquetes de Unity.</span><span class="sxs-lookup"><span data-stu-id="997c1-147">Added new C# API to get OpenXR handles to support other Unity packages consumes OpenXR extensions.</span></span>
* <span data-ttu-id="997c1-148">Se ha agregado una nueva API de C# para la interoperabilidad con las API Windows.Perception para admitir otros paquetes de Unity que consumen las API Perception de WinRT.</span><span class="sxs-lookup"><span data-stu-id="997c1-148">Added new C# API to interop with Windows.Perception APIs to support other Unity packages consuming Perception WinRT APIs.</span></span>
* <span data-ttu-id="997c1-149">Se han quitado perfiles de interacción de las características necesarias en el conjunto de características de Windows Mixed Reality, por lo que los desarrolladores pueden elegir los controladores de movimiento con los que han probado.</span><span class="sxs-lookup"><span data-stu-id="997c1-149">Removed interaction profiles from required features in Windows Mixed Reality feature set, so developers can choose the motion controllers they tested with.</span></span>
* <span data-ttu-id="997c1-150">Se ha agregado el validador de características de comunicación remota del editor holográfico para ayudar a los usuarios a configurar correctamente la comunicación remota del editor.</span><span class="sxs-lookup"><span data-stu-id="997c1-150">Added Holographic editor remoting feature validator to help users to setup editor remoting properly.</span></span>
* <span data-ttu-id="997c1-151">Se ha corregido un error por el que el editor de Unity se bloqueaba al salir del modo de comunicación remota del editor holográfico después de un error de conexión.</span><span class="sxs-lookup"><span data-stu-id="997c1-151">Fixed a bug where Unity editor crashes when exiting Holographic editor remoting mode after connection failure.</span></span>
* <span data-ttu-id="997c1-152">Se ha corregido un error por el que las texturas no premultiplicadas en el canal alfa provocaban un rendimiento poco óptimo en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="997c1-152">Fixed a bug where unpremultipled alpha textures leads to sub-optimum performance on HoloLens 2.</span></span>
* <span data-ttu-id="997c1-153">Se ha corregido un error por el que el seguimiento de manos no se encontraba correctamente cuando el origen de la escena estaba a nivel del suelo.</span><span class="sxs-lookup"><span data-stu-id="997c1-153">Fixed a bug where hand tracking was not located correctly when the scene origin was at floor level.</span></span>
* <span data-ttu-id="997c1-154">Se ha corregido un error por el que el seguimiento de la malla de mano desaparecía después de salir y cargar una nueva escena.</span><span class="sxs-lookup"><span data-stu-id="997c1-154">Fixed a bug where hand mesh tracking disappear after leaving and loading a new scene.</span></span>
* <span data-ttu-id="997c1-155">Se ha corregido un error por el que el proveedor de cámaras localizables no se limpiaba correctamente.</span><span class="sxs-lookup"><span data-stu-id="997c1-155">Fixed a bug where locatable camera provider didn’t properly clean up.</span></span>
* <span data-ttu-id="997c1-156">Se ha revisado el espacio de nombres de la API XRAnchorStore en Microsoft.MixedReality.OpenXR.</span><span class="sxs-lookup"><span data-stu-id="997c1-156">Revised the namespace of XRAnchorStore API into Microsoft.MixedReality.OpenXR.</span></span>