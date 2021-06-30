---
title: Configuración de la cámara ar de Unity
description: Documentación para usar la cámara ar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara ar,
ms.openlocfilehash: e1c032805bc4b733cfcc51e1ceac5096c73715cf
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121203"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="11d7c-104">Proveedor de configuración de cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="11d7c-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="11d7c-105">El proveedor de configuración de la cámara AR de Unity es un componente experimental de MRTK que permite que las aplicaciones de realidad mixta se ejecuten en dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="11d7c-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="11d7c-106">Opciones del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="11d7c-106">Unity AR camera settings provider options</span></span>

![Configuración de la cámara ar de Unity](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="11d7c-108">Para obtener una guía sobre cómo agregar el proveedor a la escena: [Configuración de MRTK para iOS y Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="11d7c-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="11d7c-109">Configuración de seguimiento</span><span class="sxs-lookup"><span data-stu-id="11d7c-109">Tracking settings</span></span>

<span data-ttu-id="11d7c-110">El proveedor de configuración de la cámara ar de Unity permite opciones de configuración para cómo se realiza el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="11d7c-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="11d7c-111">Esta configuración es específica de la implementación del proveedor de configuración de cámara ar de Unity.</span><span class="sxs-lookup"><span data-stu-id="11d7c-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="11d7c-112">**Pos Source**</span><span class="sxs-lookup"><span data-stu-id="11d7c-112">**Pose Source**</span></span>

<span data-ttu-id="11d7c-113">El origen de la posición define los tipos disponibles de poses de seguimiento de realidad aumentada.</span><span class="sxs-lookup"><span data-stu-id="11d7c-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="11d7c-114">En general, estos valores se asignan a un componente del dispositivo en el que se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="11d7c-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="11d7c-115">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="11d7c-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="11d7c-116">Opción</span><span class="sxs-lookup"><span data-stu-id="11d7c-116">Option</span></span> | <span data-ttu-id="11d7c-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="11d7c-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="11d7c-118">Center</span><span class="sxs-lookup"><span data-stu-id="11d7c-118">Center</span></span> | <span data-ttu-id="11d7c-119">El ojo central de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="11d7c-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="11d7c-120">Cámara de color</span><span class="sxs-lookup"><span data-stu-id="11d7c-120">Color Camera</span></span> | <span data-ttu-id="11d7c-121">Cámara de color de un dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="11d7c-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="11d7c-122">Head</span><span class="sxs-lookup"><span data-stu-id="11d7c-122">Head</span></span> | <span data-ttu-id="11d7c-123">El ojo de la cabeza de un dispositivo montado en la cabeza, a menudo ligeramente por encima del ojo central.</span><span class="sxs-lookup"><span data-stu-id="11d7c-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="11d7c-124">Ojo izquierdo</span><span class="sxs-lookup"><span data-stu-id="11d7c-124">Left Eye</span></span> | <span data-ttu-id="11d7c-125">El ojo izquierdo de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="11d7c-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="11d7c-126">Posición izquierda</span><span class="sxs-lookup"><span data-stu-id="11d7c-126">Left Pose</span></span> | <span data-ttu-id="11d7c-127">Posición del controlador izquierdo.</span><span class="sxs-lookup"><span data-stu-id="11d7c-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="11d7c-128">Ojo derecho</span><span class="sxs-lookup"><span data-stu-id="11d7c-128">Right Eye</span></span> | <span data-ttu-id="11d7c-129">El ojo derecho de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="11d7c-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="11d7c-130">Posición derecha</span><span class="sxs-lookup"><span data-stu-id="11d7c-130">Right Pose</span></span> | <span data-ttu-id="11d7c-131">Posición del controlador derecho.</span><span class="sxs-lookup"><span data-stu-id="11d7c-131">The right hand controller pose.</span></span> |

<span data-ttu-id="11d7c-132">El valor predeterminado para el origen de la posición es **Color Camera**, para habilitar una pantalla transparente en dispositivos móviles, como un teléfono o una tableta.</span><span class="sxs-lookup"><span data-stu-id="11d7c-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="11d7c-133">**Tipo de seguimiento**</span><span class="sxs-lookup"><span data-stu-id="11d7c-133">**Tracking Type**</span></span>

<span data-ttu-id="11d7c-134">El tipo de seguimiento define las partes de la posición que se usarán para el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="11d7c-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="11d7c-135">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="11d7c-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="11d7c-136">Opción</span><span class="sxs-lookup"><span data-stu-id="11d7c-136">Option</span></span> | <span data-ttu-id="11d7c-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="11d7c-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="11d7c-138">Posición</span><span class="sxs-lookup"><span data-stu-id="11d7c-138">Position</span></span> | <span data-ttu-id="11d7c-139">Posición del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11d7c-139">The position of the device.</span></span> |
| <span data-ttu-id="11d7c-140">Rotación</span><span class="sxs-lookup"><span data-stu-id="11d7c-140">Rotation</span></span> | <span data-ttu-id="11d7c-141">Rotación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11d7c-141">The rotation of the device.</span></span> |
| <span data-ttu-id="11d7c-142">Rotación y posición</span><span class="sxs-lookup"><span data-stu-id="11d7c-142">Rotation And Position</span></span> | <span data-ttu-id="11d7c-143">Posición y rotación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11d7c-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="11d7c-144">El valor predeterminado para el tipo de seguimiento **es Rotación y posición** para habilitar la experiencia de seguimiento más completa.</span><span class="sxs-lookup"><span data-stu-id="11d7c-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="11d7c-145">**Tipo de actualización**</span><span class="sxs-lookup"><span data-stu-id="11d7c-145">**Update Type**</span></span>

<span data-ttu-id="11d7c-146">El tipo de actualización define en qué puntos, durante el procesamiento de fotogramas, se muestrearán los datos de posición.</span><span class="sxs-lookup"><span data-stu-id="11d7c-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="11d7c-147">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="11d7c-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="11d7c-148">Opción</span><span class="sxs-lookup"><span data-stu-id="11d7c-148">Option</span></span> | <span data-ttu-id="11d7c-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="11d7c-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="11d7c-150">Antes de representar</span><span class="sxs-lookup"><span data-stu-id="11d7c-150">Before Render</span></span> | <span data-ttu-id="11d7c-151">Justo antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="11d7c-151">Just before rendering.</span></span> |
| <span data-ttu-id="11d7c-152">Actualizar</span><span class="sxs-lookup"><span data-stu-id="11d7c-152">Update</span></span> | <span data-ttu-id="11d7c-153">Durante la fase de actualización del marco.</span><span class="sxs-lookup"><span data-stu-id="11d7c-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="11d7c-154">Actualizar y antes de representar</span><span class="sxs-lookup"><span data-stu-id="11d7c-154">Update And Before Render</span></span> | <span data-ttu-id="11d7c-155">Durante la fase de actualización y justo antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="11d7c-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="11d7c-156">El valor predeterminado para el tipo de seguimiento **es Update y Before Render** para habilitar la latencia de seguimiento más baja.</span><span class="sxs-lookup"><span data-stu-id="11d7c-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="11d7c-157">Consulte también</span><span class="sxs-lookup"><span data-stu-id="11d7c-157">See also</span></span>

- [<span data-ttu-id="11d7c-158">Información general del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="11d7c-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="11d7c-159">Creación de un proveedor de configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="11d7c-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
