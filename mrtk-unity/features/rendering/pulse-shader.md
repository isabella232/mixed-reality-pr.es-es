---
title: Sombreador de pulsos
description: descripción en sombreadores pulse en MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144944"
---
# <a name="pulse-shader"></a><span data-ttu-id="b42a5-104">Sombreador de pulsos</span><span class="sxs-lookup"><span data-stu-id="b42a5-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="b42a5-106">Use el sombreador de pulsos para animar un efecto de pulso visual sobre la reconstrucción de la superficie, la malla de mano articulada o cualquier otra malla.</span><span class="sxs-lookup"><span data-stu-id="b42a5-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="b42a5-107">Sombreador y material</span><span class="sxs-lookup"><span data-stu-id="b42a5-107">Shader and material</span></span>

<span data-ttu-id="b42a5-108">Los siguientes materiales usan **SR_Triangles** sombreador.</span><span class="sxs-lookup"><span data-stu-id="b42a5-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="b42a5-109">Puede configurar varias opciones, como el color de relleno, el color de línea y el color de pulso.</span><span class="sxs-lookup"><span data-stu-id="b42a5-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="b42a5-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="b42a5-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="b42a5-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="b42a5-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="b42a5-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="b42a5-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="b42a5-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="b42a5-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="b42a5-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="b42a5-114">Prerequisites</span></span>

<span data-ttu-id="b42a5-115">En el ejemplo de malla espacial, asegúrese de que MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat están asignados en Configuración de MRTK -> Spatial Awareness -> Display Settings -> Visible Material.</span><span class="sxs-lookup"><span data-stu-id="b42a5-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="b42a5-116">En el ejemplo de malla de mano, asegúrese de que MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat se asignan en ArticulatedHandMesh.prefab, que a su vez se debe asignar en configuración de MRTK -> Input -> Hand Tracking -> Hand Mesh Prefab.</span><span class="sxs-lookup"><span data-stu-id="b42a5-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="b42a5-117">Funcionamiento</span><span class="sxs-lookup"><span data-stu-id="b42a5-117">How it works</span></span>

<span data-ttu-id="b42a5-118">El sombreador de malla de mano usa UV para asignar el pulso a lo largo de la malla de mano y para atenuar la bolsa.</span><span class="sxs-lookup"><span data-stu-id="b42a5-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="b42a5-119">El sombreador de reconstrucción de superficie usa las posiciones de vértice para asignar el pulso.</span><span class="sxs-lookup"><span data-stu-id="b42a5-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="b42a5-120">Ejemplo de malla espacial: PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="b42a5-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="b42a5-121">De forma HoloLens 2 experiencia de shell, puede apuntar y pulsar el aire con el rayo de la mano para generar un efecto de pulsación en la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="b42a5-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="b42a5-122">La escena de ejemplo contiene el objeto ExampleSpatialMesh, que es un datos de malla espacial de prueba para el modo de juego de Unity.</span><span class="sxs-lookup"><span data-stu-id="b42a5-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="b42a5-123">Este objeto se deshabilitará y ocultará en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b42a5-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="b42a5-124">El script **PulseShaderSpatialMeshHandler.cs** genera el efecto de pulso en la malla espacial en la posición del punto de acceso `PulseOnSelect` si es true.</span><span class="sxs-lookup"><span data-stu-id="b42a5-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="b42a5-125">La  `Auto Pulse` propiedad también se puede establecer en true en el propio material para una animación repetida.</span><span class="sxs-lookup"><span data-stu-id="b42a5-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="b42a5-126">En la escena de ejemplo, este script se adjunta al prefab PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="b42a5-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="b42a5-127">Se hace referencia a este objeto prefab en la propiedad Prefab Spatial Awareness Profile through Runtime Spatial Mesh (Perfil de reconocimiento espacial mediante prefab de malla espacial en tiempo de ejecución).</span><span class="sxs-lookup"><span data-stu-id="b42a5-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="b42a5-128">Durante el tiempo de ejecución, se crea una instancia del objeto prefab PulseShaderSpatialMeshParent y se crea una instancia y se agrega a la jerarquía de malla espacial (solo en el dispositivo, este comportamiento no se puede observar en el editor).</span><span class="sxs-lookup"><span data-stu-id="b42a5-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="b42a5-129">Ejemplo de malla de mano: PulseShaderHandMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="b42a5-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="b42a5-130">En esta escena de ejemplo se muestra la visualización de malla de mano mediante el sombreador de pulsos.</span><span class="sxs-lookup"><span data-stu-id="b42a5-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="b42a5-131">Cuando el dispositivo HoloLens detecta una mano, la animación por pulsos se desencadena una vez.</span><span class="sxs-lookup"><span data-stu-id="b42a5-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="b42a5-132">Estos comentarios visuales pueden aumentar la confianza de interacción del usuario.</span><span class="sxs-lookup"><span data-stu-id="b42a5-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="b42a5-133">El script **PulseShaderHandMeshHandler.cs** genera el efecto pulse en el material asignado.</span><span class="sxs-lookup"><span data-stu-id="b42a5-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="b42a5-134">De forma predeterminada, se comprueba "Pulse On Hand Detected".</span><span class="sxs-lookup"><span data-stu-id="b42a5-134">By default, 'Pulse On Hand Detected' is checked.</span></span>
