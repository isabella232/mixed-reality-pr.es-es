---
title: Configuración de la cámara ar de Unity
description: Documentación para usar la cámara ar en MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara ar,
ms.openlocfilehash: baa54f4a7c6238b136a108cf5adcbddd29c3ee1b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143461"
---
# <a name="unity-ar-camera-settings-provider"></a><span data-ttu-id="9fe2e-104">Proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="9fe2e-104">Unity AR camera settings provider</span></span>

<span data-ttu-id="9fe2e-105">El proveedor de configuración de la cámara AR de Unity es un componente experimental de MRTK que permite que las aplicaciones de realidad mixta se ejecuten en dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-105">The Unity AR camera settings provider is an experimental MRTK component that enables mixed reality applications to run on Android and iOS devices.</span></span>

## <a name="unity-ar-camera-settings-provider-options"></a><span data-ttu-id="9fe2e-106">Opciones del proveedor de configuración de la cámara ar de Unity</span><span class="sxs-lookup"><span data-stu-id="9fe2e-106">Unity AR camera settings provider options</span></span>

![Configuración de la cámara ar de Unity](../images/camera-system/UnityArSettingsConfiguration.png)

<span data-ttu-id="9fe2e-108">Para obtener una guía sobre cómo agregar el proveedor a la escena: [Configuración de MRTK para iOS y Android](../../supported-devices/using-ar-foundation.md)</span><span class="sxs-lookup"><span data-stu-id="9fe2e-108">For a guide on how to add the provider to your scene: [How to configure MRTK for iOS and Android](../../supported-devices/using-ar-foundation.md)</span></span>

### <a name="tracking-settings"></a><span data-ttu-id="9fe2e-109">Configuración de seguimiento</span><span class="sxs-lookup"><span data-stu-id="9fe2e-109">Tracking settings</span></span>

<span data-ttu-id="9fe2e-110">El proveedor de configuración de la cámara AR de Unity permite opciones de configuración sobre cómo se realiza el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-110">The Unity AR camera settings provider allows configuration options for how tracking is performed.</span></span> <span data-ttu-id="9fe2e-111">Esta configuración es específica de la implementación del proveedor de configuración de la cámara ar de Unity.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-111">These settings are specific to the Unity AR camera settings provider implementation.</span></span>

<span data-ttu-id="9fe2e-112">**Pos Source**</span><span class="sxs-lookup"><span data-stu-id="9fe2e-112">**Pose Source**</span></span>

<span data-ttu-id="9fe2e-113">El origen de la posición define los tipos disponibles de poses de seguimiento de realidad aumentada.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-113">The pose source defines the available types of augmented reality tracking poses.</span></span> <span data-ttu-id="9fe2e-114">En general, estos valores se asignan a un componente del dispositivo en el que se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-114">In general, these values map to a component of the device on which the application is running.</span></span>

<span data-ttu-id="9fe2e-115">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-115">The available options are described in the following table.</span></span>

| <span data-ttu-id="9fe2e-116">Opción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-116">Option</span></span> | <span data-ttu-id="9fe2e-117">Descripción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-117">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9fe2e-118">Center</span><span class="sxs-lookup"><span data-stu-id="9fe2e-118">Center</span></span> | <span data-ttu-id="9fe2e-119">El ojo central de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-119">The center eye of a head mounted device.</span></span> |
| <span data-ttu-id="9fe2e-120">Cámara de color</span><span class="sxs-lookup"><span data-stu-id="9fe2e-120">Color Camera</span></span> | <span data-ttu-id="9fe2e-121">Cámara de color de un dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-121">The color camera of a mobile device.</span></span> |
| <span data-ttu-id="9fe2e-122">Head</span><span class="sxs-lookup"><span data-stu-id="9fe2e-122">Head</span></span> | <span data-ttu-id="9fe2e-123">El ojo de la cabeza de un dispositivo montado en la cabeza, a menudo ligeramente por encima del ojo central.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-123">The head eye of a head mounted device, often slightly above the center eye.</span></span> |
| <span data-ttu-id="9fe2e-124">Ojo izquierdo</span><span class="sxs-lookup"><span data-stu-id="9fe2e-124">Left Eye</span></span> | <span data-ttu-id="9fe2e-125">El ojo izquierdo de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-125">The left eye of a head mounted device.</span></span> |
| <span data-ttu-id="9fe2e-126">Posición izquierda</span><span class="sxs-lookup"><span data-stu-id="9fe2e-126">Left Pose</span></span> | <span data-ttu-id="9fe2e-127">Posición del controlador izquierdo.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-127">The left hand controller pose.</span></span> |
| <span data-ttu-id="9fe2e-128">Ojo derecho</span><span class="sxs-lookup"><span data-stu-id="9fe2e-128">Right Eye</span></span> | <span data-ttu-id="9fe2e-129">El ojo derecho de un dispositivo montado en la cabeza.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-129">The right eye of a head mounted device.</span></span> |
| <span data-ttu-id="9fe2e-130">Posición derecha</span><span class="sxs-lookup"><span data-stu-id="9fe2e-130">Right Pose</span></span> | <span data-ttu-id="9fe2e-131">Posición del controlador derecho.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-131">The right hand controller pose.</span></span> |

<span data-ttu-id="9fe2e-132">El valor predeterminado para el origen de posición es **Color Camera**, para habilitar una pantalla transparente en dispositivos móviles, como un teléfono o una tableta.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-132">The default value for pose source is **Color Camera**, to enable a transparent display on mobile devices, such as a phone or tablet.</span></span>

<span data-ttu-id="9fe2e-133">**Tipo de seguimiento**</span><span class="sxs-lookup"><span data-stu-id="9fe2e-133">**Tracking Type**</span></span>

<span data-ttu-id="9fe2e-134">El tipo de seguimiento define las partes de la posición que se usarán para el seguimiento.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-134">The tracking type defines the portion(s) of the pose that will be used for tracking.</span></span>

<span data-ttu-id="9fe2e-135">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-135">The available options are described in the following table.</span></span>

| <span data-ttu-id="9fe2e-136">Opción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-136">Option</span></span> | <span data-ttu-id="9fe2e-137">Descripción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-137">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9fe2e-138">Posición</span><span class="sxs-lookup"><span data-stu-id="9fe2e-138">Position</span></span> | <span data-ttu-id="9fe2e-139">Posición del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-139">The position of the device.</span></span> |
| <span data-ttu-id="9fe2e-140">Rotación</span><span class="sxs-lookup"><span data-stu-id="9fe2e-140">Rotation</span></span> | <span data-ttu-id="9fe2e-141">Rotación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-141">The rotation of the device.</span></span> |
| <span data-ttu-id="9fe2e-142">Rotación y posición</span><span class="sxs-lookup"><span data-stu-id="9fe2e-142">Rotation And Position</span></span> | <span data-ttu-id="9fe2e-143">Posición y rotación del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-143">The position and rotation of the device.</span></span> |

<span data-ttu-id="9fe2e-144">El valor predeterminado para el tipo de seguimiento **es Rotación y posición** para habilitar la experiencia de seguimiento más completa.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-144">The default value for tracking type is **Rotation And Position**, to enable the richest tracking experience.</span></span>

<span data-ttu-id="9fe2e-145">**Tipo de actualización**</span><span class="sxs-lookup"><span data-stu-id="9fe2e-145">**Update Type**</span></span>

<span data-ttu-id="9fe2e-146">El tipo de actualización define en qué puntos, durante el procesamiento de fotogramas, se muestrearán los datos de posición.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-146">The update type defines at what points, during frame processing, the pose data will be sampled.</span></span>

<span data-ttu-id="9fe2e-147">Las opciones disponibles se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-147">The available options are described in the following table.</span></span>

| <span data-ttu-id="9fe2e-148">Opción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-148">Option</span></span> | <span data-ttu-id="9fe2e-149">Descripción</span><span class="sxs-lookup"><span data-stu-id="9fe2e-149">Description</span></span> |
| --- | --- |
| <span data-ttu-id="9fe2e-150">Antes de la representación</span><span class="sxs-lookup"><span data-stu-id="9fe2e-150">Before Render</span></span> | <span data-ttu-id="9fe2e-151">Justo antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-151">Just before rendering.</span></span> |
| <span data-ttu-id="9fe2e-152">Actualizar</span><span class="sxs-lookup"><span data-stu-id="9fe2e-152">Update</span></span> | <span data-ttu-id="9fe2e-153">Durante la fase de actualización del marco.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-153">During the update phase of the frame.</span></span> |
| <span data-ttu-id="9fe2e-154">Actualizar y antes de representar</span><span class="sxs-lookup"><span data-stu-id="9fe2e-154">Update And Before Render</span></span> | <span data-ttu-id="9fe2e-155">Durante la fase de actualización y justo antes de la representación.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-155">During the update phase and just before rendering.</span></span> |

<span data-ttu-id="9fe2e-156">El valor predeterminado para el tipo de seguimiento **es Update y Before Render**, para habilitar la latencia de seguimiento más baja.</span><span class="sxs-lookup"><span data-stu-id="9fe2e-156">The default value for tracking type is **Update And Before Render**, to enable the lowest tracking latency.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe2e-157">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9fe2e-157">See also</span></span>

- [<span data-ttu-id="9fe2e-158">Información general del sistema de cámara</span><span class="sxs-lookup"><span data-stu-id="9fe2e-158">Camera System Overview</span></span>](camera-system-overview.md)
- [<span data-ttu-id="9fe2e-159">Crear un proveedor de configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="9fe2e-159">Creating a Camera Settings Provider</span></span>](create-settings-provider.md)
