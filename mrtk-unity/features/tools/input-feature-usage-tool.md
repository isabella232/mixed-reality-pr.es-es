---
title: InputFeatureUsageTool
description: Herramienta InputFeatureUsage de documentación de MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 35b28557df37abee19a0c950b362117eb6a120b0
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300209"
---
# <a name="inputfeatureusage-tool"></a><span data-ttu-id="69a6d-104">Herramienta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="69a6d-104">InputFeatureUsage tool</span></span>

<span data-ttu-id="69a6d-105">La herramienta InputFeatureUsage es una herramienta de tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente el InputFeatureUsages de Unity disponible para un origen de entrada detectado (por ejemplo, un controlador de movimiento o una mano articulada).</span><span class="sxs-lookup"><span data-stu-id="69a6d-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="69a6d-106">Esta escena solo funciona en Unity 2019,3 o posterior.</span><span class="sxs-lookup"><span data-stu-id="69a6d-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="69a6d-107">Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware.</span><span class="sxs-lookup"><span data-stu-id="69a6d-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="69a6d-108">También puede ayudar a confirmar un problema de asignación de control sospechoso en la clase de soporte de un controlador existente.</span><span class="sxs-lookup"><span data-stu-id="69a6d-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Herramienta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="69a6d-110">Uso de la herramienta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="69a6d-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="69a6d-111">Para empezar a trabajar con la herramienta InputFeatureUsage, vaya a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** y abra la escena **InputFeatureUsageTool** .</span><span class="sxs-lookup"><span data-stu-id="69a6d-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="69a6d-112">Una vez cargada la escena, el proyecto puede ejecutarse en el editor, usar el modo de reproducción o compilarse y ejecutarse en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69a6d-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="69a6d-113">Para examinar las asignaciones de Unity para un controlador:</span><span class="sxs-lookup"><span data-stu-id="69a6d-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="69a6d-114">Conectar el controlador</span><span class="sxs-lookup"><span data-stu-id="69a6d-114">Connect the controller</span></span>
- <span data-ttu-id="69a6d-115">Presione cada botón y mueva cada eje</span><span class="sxs-lookup"><span data-stu-id="69a6d-115">Press each button and move each axis</span></span>
- <span data-ttu-id="69a6d-116">Tenga en cuenta los usos de las características en la pantalla</span><span class="sxs-lookup"><span data-stu-id="69a6d-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="69a6d-117">Actualizar las asignaciones de control en el proveedor de datos del sistema de entrada para el controlador</span><span class="sxs-lookup"><span data-stu-id="69a6d-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="69a6d-118">La herramienta InputFeatureUsage no hace uso de los componentes del kit de herramientas de la realidad mixta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="69a6d-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="69a6d-119">Se comunica directamente con Unity para determinar y mostrar los usos de las características.</span><span class="sxs-lookup"><span data-stu-id="69a6d-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="69a6d-120">Paneles</span><span class="sxs-lookup"><span data-stu-id="69a6d-120">Panels</span></span>

<span data-ttu-id="69a6d-121">Los paneles muestran el estado actual de todos los InputFeatureUsages indicados en todos los orígenes de entrada de Unity detectados.</span><span class="sxs-lookup"><span data-stu-id="69a6d-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="69a6d-122">El panel más pequeño de la parte superior muestra los nombres de todos los orígenes detectados.</span><span class="sxs-lookup"><span data-stu-id="69a6d-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="69a6d-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="69a6d-123">See also</span></span>

- [<span data-ttu-id="69a6d-124">Crear un proveedor de datos del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="69a6d-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="69a6d-125">Herramienta de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="69a6d-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
