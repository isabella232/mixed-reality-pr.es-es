---
title: Herramienta de uso de características de entrada
description: Herramienta InputFeatureUsage de documentación en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 413d2a3105294411f9c08f4a2add9365389ea783
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176127"
---
# <a name="input-feature-usage-tool"></a><span data-ttu-id="817d7-104">Herramienta de uso de características de entrada</span><span class="sxs-lookup"><span data-stu-id="817d7-104">Input feature usage tool</span></span>

<span data-ttu-id="817d7-105">La herramienta InputFeatureUsage es una herramienta en tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente las entradas disponibles de UnityFeatureUsages para un origen de entrada detectado (por ejemplo, controlador de movimiento o mano articulada).</span><span class="sxs-lookup"><span data-stu-id="817d7-105">The InputFeatureUsage tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the available Unity InputFeatureUsages for a detected input source (ex: motion controller or articulated hand).</span></span>

> [!NOTE]
> <span data-ttu-id="817d7-106">Esta escena solo funciona en Unity 2019.3 o posterior.</span><span class="sxs-lookup"><span data-stu-id="817d7-106">This scene only works on Unity 2019.3 or later.</span></span>

<span data-ttu-id="817d7-107">Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware.</span><span class="sxs-lookup"><span data-stu-id="817d7-107">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="817d7-108">También puede ayudar a confirmar un problema sospechoso de asignación de controles en la clase de soporte técnico para un controlador existente.</span><span class="sxs-lookup"><span data-stu-id="817d7-108">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Herramienta InputFeatureUsage](../images/controller-mapping-tool/InputFeatureUsages.png)

## <a name="using-the-inputfeatureusage-tool"></a><span data-ttu-id="817d7-110">Uso de la herramienta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="817d7-110">Using the InputFeatureUsage tool</span></span>

<span data-ttu-id="817d7-111">Para empezar a trabajar con la herramienta InputFeatureUsage, vaya a **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** y abra la **escena InputFeatureUsageTool.**</span><span class="sxs-lookup"><span data-stu-id="817d7-111">To get started with the InputFeatureUsage tool, navigate to **MRTK/Tools/RuntimeTools/Tools/InputFeatureUsageTool** and open the **InputFeatureUsageTool** scene.</span></span> <span data-ttu-id="817d7-112">Una vez cargada la escena, el proyecto se puede ejecutar en el editor, mediante el modo de reproducción, o bien se puede crear y ejecutar en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="817d7-112">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="817d7-113">Para examinar las asignaciones de Unity para un controlador:</span><span class="sxs-lookup"><span data-stu-id="817d7-113">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="817d7-114">Conectar el controlador</span><span class="sxs-lookup"><span data-stu-id="817d7-114">Connect the controller</span></span>
- <span data-ttu-id="817d7-115">Presione cada botón y mueva cada eje.</span><span class="sxs-lookup"><span data-stu-id="817d7-115">Press each button and move each axis</span></span>
- <span data-ttu-id="817d7-116">Tenga en cuenta los usos de características en la pantalla</span><span class="sxs-lookup"><span data-stu-id="817d7-116">Note the feature usages in the display</span></span>
- <span data-ttu-id="817d7-117">Actualización de las asignaciones de control en el proveedor de datos del sistema de entrada para el controlador</span><span class="sxs-lookup"><span data-stu-id="817d7-117">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="817d7-118">La herramienta InputFeatureUsage no hace uso de los componentes Mixed Reality Toolkit Microsoft.</span><span class="sxs-lookup"><span data-stu-id="817d7-118">The InputFeatureUsage tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="817d7-119">Se comunica directamente con Unity para determinar y mostrar los usos de características.</span><span class="sxs-lookup"><span data-stu-id="817d7-119">It directly communicates with Unity to determine and display the feature usages.</span></span>

### <a name="panels"></a><span data-ttu-id="817d7-120">Paneles</span><span class="sxs-lookup"><span data-stu-id="817d7-120">Panels</span></span>

<span data-ttu-id="817d7-121">Los paneles muestran el estado actual de todos los inputFeatureUsages notificados en todos los orígenes de entrada de Unity detectados.</span><span class="sxs-lookup"><span data-stu-id="817d7-121">The panels display the current state of all reported InputFeatureUsages on all detected Unity input sources.</span></span>

<span data-ttu-id="817d7-122">En el panel más pequeño de la parte superior se enumeran los nombres de todos los orígenes detectados.</span><span class="sxs-lookup"><span data-stu-id="817d7-122">The smaller panel along the top lists the names of all detected sources.</span></span>

## <a name="see-also"></a><span data-ttu-id="817d7-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="817d7-123">See also</span></span>

- [<span data-ttu-id="817d7-124">Creación de un proveedor de datos del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="817d7-124">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="817d7-125">Herramienta de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="817d7-125">Controller mapping tool</span></span>](controller-mapping-tool.md)
