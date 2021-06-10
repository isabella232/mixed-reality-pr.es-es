---
title: Moran
description: Interacción de permanencia
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, Mixed Reality, development, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647865"
---
# <a name="dwell"></a><span data-ttu-id="f8638-104">Moran</span><span class="sxs-lookup"><span data-stu-id="f8638-104">Dwell</span></span>

![Permanencia de hero](../images/dwell/MRTK_UX_Dwell.png)

<span data-ttu-id="f8638-106">La mirada con la cabeza y la permanencia son excelentes en escenarios en los que las manos de una persona están ocupadas con otras tareas.</span><span class="sxs-lookup"><span data-stu-id="f8638-106">Head-gaze and dwell are great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="f8638-107">La característica también es útil cuando la voz no es 100 % confiable o disponible debido a restricciones ambientales o sociales.</span><span class="sxs-lookup"><span data-stu-id="f8638-107">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span>
<span data-ttu-id="f8638-108">Los ejemplos de permanencia de MRTK muestran diferentes tipos de componentes de interfaz de usuario con tiempo de respuesta configurable y comentarios visuales.</span><span class="sxs-lookup"><span data-stu-id="f8638-108">MRTK's dwell examples demonstrate different types of UI components with configurable response time and visual feedback.</span></span>

<span data-ttu-id="f8638-109">Consulte la [página guía de mirada con](/windows/mixed-reality/design/gaze-and-dwell-head) la cabeza y permanencia para ver las recomendaciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="f8638-109">Please see [Head-gaze and dwell guideline](/windows/mixed-reality/design/gaze-and-dwell-head) page for the design recommendations.</span></span>

## <a name="dwell-scripts"></a><span data-ttu-id="f8638-110">Scripts de permanencia</span><span class="sxs-lookup"><span data-stu-id="f8638-110">Dwell scripts</span></span>

- <span data-ttu-id="f8638-111">**DwellHandler:** agrega una modalidad de permanencia al destino de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="f8638-111">**DwellHandler**: Adds a dwell modality to the UI target.</span></span>
- <span data-ttu-id="f8638-112">**DwellStateType:** los estados del controlador de permanencia.</span><span class="sxs-lookup"><span data-stu-id="f8638-112">**DwellStateType**: The states of the dwell handler.</span></span>
- <span data-ttu-id="f8638-113">**DwellUnityEvent:** evento de Unity para un evento de permanencia.</span><span class="sxs-lookup"><span data-stu-id="f8638-113">**DwellUnityEvent**: Unity event for a dwell event.</span></span> <span data-ttu-id="f8638-114">Contiene la referencia de puntero.</span><span class="sxs-lookup"><span data-stu-id="f8638-114">Contains the pointer reference.</span></span>
- <span data-ttu-id="f8638-115">**BaseDwellPressableButton.cs:** script que desencadena el evento OnClick() en los `Interactable` prefabs PressableButtonHoloLens2.</span><span class="sxs-lookup"><span data-stu-id="f8638-115">**BaseDwellPressableButton.cs** : A script that triggers OnClick() event in `Interactable` of PressableButtonHoloLens2 prefabs.</span></span>
- <span data-ttu-id="f8638-116">**ToggleDwellPressableButton.cs:** este script modifica la propiedad de que usa el sombreador `_BorderWidth` `dwellVisualImage` estándar de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f8638-116">**ToggleDwellPressableButton.cs** : This script modifies `_BorderWidth` property of the `dwellVisualImage` which is using MRTK Standard Shader.</span></span>

## <a name="dwell-profiles"></a><span data-ttu-id="f8638-117">Perfiles de permanencia</span><span class="sxs-lookup"><span data-stu-id="f8638-117">Dwell profiles</span></span>
<span data-ttu-id="f8638-118">El controlador de permanencia usa los perfiles **de** permanencia para configurar los distintos umbrales.</span><span class="sxs-lookup"><span data-stu-id="f8638-118">Dwell profiles are used by the **Dwell Handler** to configure the various thresholds.</span></span>
- <span data-ttu-id="f8638-119">**ButtonDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="f8638-119">**ButtonDwellProfile.asset**</span></span>
- <span data-ttu-id="f8638-120">**InstandDwellProfile.asset**</span><span class="sxs-lookup"><span data-stu-id="f8638-120">**InstandDwellProfile.asset**</span></span>
- <span data-ttu-id="f8638-121">**DwellProfileWithDecay.asset**</span><span class="sxs-lookup"><span data-stu-id="f8638-121">**DwellProfileWithDecay.asset**</span></span>

## <a name="prefabs"></a><span data-ttu-id="f8638-122">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="f8638-122">Prefabs</span></span>

<span data-ttu-id="f8638-123">Estos elementos prefabs son variantes de los elementos HoloLens 2 prefabs de botones presionables de estilo que tienen componentes adicionales para admitir las interacciones de permanencia.</span><span class="sxs-lookup"><span data-stu-id="f8638-123">These prefabs are variants of the HoloLens 2 style pressable button prefabs that have additional components to support dwell interactions.</span></span>

- <span data-ttu-id="f8638-124">**PressableButtonHoloLens2_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="f8638-124">**PressableButtonHoloLens2_Dwell.prefab**</span></span>
- <span data-ttu-id="f8638-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="f8638-125">**PressableButtonHoloLens2_32x96_Dwell.prefab**</span></span>
- <span data-ttu-id="f8638-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="f8638-126">**PressableButtonHoloLens2ToggleDwell.prefab**</span></span>
- <span data-ttu-id="f8638-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span><span class="sxs-lookup"><span data-stu-id="f8638-127">**PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**</span></span>

<span data-ttu-id="f8638-128">Estos elementos prefabs tienen un componente de placa posterior **QuadDwellVisual** adicional para visualizar el estado de entrada de permanencia.</span><span class="sxs-lookup"><span data-stu-id="f8638-128">These prefabs have an additional backplate component **QuadDwellVisual** to visualize the dwell input state.</span></span> <span data-ttu-id="f8638-129">Tiene asignado el material **HolographicBackPlateDwellVisual.mat.**</span><span class="sxs-lookup"><span data-stu-id="f8638-129">It has **HolographicBackPlateDwellVisual.mat** material assigned.</span></span> <span data-ttu-id="f8638-130">**ToggleDwellPressableButton.cs** actualiza la propiedad **_BorderWidth** del sombreador estándar de MRTK para visualizar la entrada de permanencia.</span><span class="sxs-lookup"><span data-stu-id="f8638-130">**ToggleDwellPressableButton.cs** updates the **_BorderWidth** property of MRTK Standard shader to visualize the dwell input.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a><span data-ttu-id="f8638-131">Escena de ejemplo</span><span class="sxs-lookup"><span data-stu-id="f8638-131">Example scene</span></span>

<span data-ttu-id="f8638-132">Puede encontrar ejemplos en la `DwellExample` escena.</span><span class="sxs-lookup"><span data-stu-id="f8638-132">You can find examples in the `DwellExample` scene.</span></span> <span data-ttu-id="f8638-133">En la escena de ejemplo se muestran ejemplos de interfaz de usuario volumétrica y ejemplos de interfaz de usuario de Unity.</span><span class="sxs-lookup"><span data-stu-id="f8638-133">The example scene shows both volumetric UI examples and Unity UI examples.</span></span>

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a><span data-ttu-id="f8638-134">Vea también</span><span class="sxs-lookup"><span data-stu-id="f8638-134">See also</span></span>

- [<span data-ttu-id="f8638-135">**Botones**</span><span class="sxs-lookup"><span data-stu-id="f8638-135">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="f8638-136">**Interactuable**</span><span class="sxs-lookup"><span data-stu-id="f8638-136">**Interactable**</span></span>](interactable.md)
