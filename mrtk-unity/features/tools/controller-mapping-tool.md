---
title: Herramienta de asignación de controladores
description: Documentación sobre la herramienta de asignación de controladores en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: f00dc01555ef158dab21334761bd23ef6a70dba4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144084"
---
# <a name="controller-mapping-tool"></a><span data-ttu-id="7e37b-104">Herramienta de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="7e37b-104">Controller mapping tool</span></span>

<span data-ttu-id="7e37b-105">La herramienta de asignación de controladores es una herramienta en tiempo de ejecución (en el dispositivo o en el editor) que permite a los desarrolladores determinar rápidamente las asignaciones de botón y eje de entrada de Unity para un controlador de hardware (por ejemplo, controlador de movimiento).</span><span class="sxs-lookup"><span data-stu-id="7e37b-105">The controller mapping tool is a runtime (on device or in the editor) tool that enables developers to quickly determine the Unity input axis and button mappings for a hardware controller (ex: motion controller).</span></span>

<span data-ttu-id="7e37b-106">Esta herramienta es muy útil al desarrollar compatibilidad con un nuevo controlador de hardware.</span><span class="sxs-lookup"><span data-stu-id="7e37b-106">This tool is very useful when developing support for a new hardware controller.</span></span> <span data-ttu-id="7e37b-107">También puede ayudar a confirmar un problema sospechoso de asignación de controles en la clase de soporte técnico para un controlador existente.</span><span class="sxs-lookup"><span data-stu-id="7e37b-107">It can also help to confirm a suspected control mapping issue in the support class for an existing controller.</span></span>

![Herramienta de asignación de controladores](../images/controller-mapping-tool/ControllerMappingTool.png)

## <a name="using-the-controller-mapping-tool"></a><span data-ttu-id="7e37b-109">Uso de la herramienta de asignación de controladores</span><span class="sxs-lookup"><span data-stu-id="7e37b-109">Using the controller mapping tool</span></span>

<span data-ttu-id="7e37b-110">Para empezar a trabajar con la herramienta de asignación de controladores, vaya a **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** y abra la **escena ControllerMappingTool.**</span><span class="sxs-lookup"><span data-stu-id="7e37b-110">To get started with the controller mapping tool, navigate to **MRTK/Tools/RuntimeTools/Tools/ControllerMappingTool** and open the **ControllerMappingTool** scene.</span></span> <span data-ttu-id="7e37b-111">Una vez cargada la escena, el proyecto se puede ejecutar en el editor, mediante el modo de reproducción, o bien se puede crear y ejecutar en un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e37b-111">Once the scene has been loaded, the project can either be run in the editor, using play mode, or built and run on a device.</span></span>

<span data-ttu-id="7e37b-112">Para examinar las asignaciones de Unity para un controlador:</span><span class="sxs-lookup"><span data-stu-id="7e37b-112">To examine Unity's mappings for a controller:</span></span>

- <span data-ttu-id="7e37b-113">Conexión del controlador</span><span class="sxs-lookup"><span data-stu-id="7e37b-113">Connect the controller</span></span>
- <span data-ttu-id="7e37b-114">Presione cada botón y mueva cada eje.</span><span class="sxs-lookup"><span data-stu-id="7e37b-114">Press each button and move each axis</span></span>
- <span data-ttu-id="7e37b-115">Anote las asignaciones en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="7e37b-115">Note the mappings in the display</span></span>
- <span data-ttu-id="7e37b-116">Actualización de las asignaciones de controles en el proveedor de datos del sistema de entrada para el controlador</span><span class="sxs-lookup"><span data-stu-id="7e37b-116">Update the control mappings in the input system data provider for the controller</span></span>

> [!NOTE]
> <span data-ttu-id="7e37b-117">La herramienta de asignación de controladores no usa componentes de Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="7e37b-117">The controller mapping tool does not make use of Microsoft Mixed Reality Toolkit components.</span></span> <span data-ttu-id="7e37b-118">Se comunica directamente con Unity para determinar y mostrar las asignaciones de control.</span><span class="sxs-lookup"><span data-stu-id="7e37b-118">It directly communicates with Unity to determine and display the control mappings.</span></span>

### <a name="all-controls-display"></a><span data-ttu-id="7e37b-119">Se muestran todos los controles</span><span class="sxs-lookup"><span data-stu-id="7e37b-119">All controls display</span></span>

<span data-ttu-id="7e37b-120">El panel de pantalla grande informa del estado de todos los ejes y botones de entrada de Unity definidos (por ejemplo: Eje 10, Botón 3).</span><span class="sxs-lookup"><span data-stu-id="7e37b-120">The large display panel reports the state of all defined Unity input axes and buttons (ex: Axis 10, Button 3).</span></span> <span data-ttu-id="7e37b-121">Este panel proporciona una vista completa del estado del controlador.</span><span class="sxs-lookup"><span data-stu-id="7e37b-121">This panel provides a complete view of the state of the controller.</span></span>

![Se muestran todos los controles](../images/controller-mapping-tool/AllControls.png)

### <a name="active-controls-display"></a><span data-ttu-id="7e37b-123">Presentación de controles activos</span><span class="sxs-lookup"><span data-stu-id="7e37b-123">Active controls display</span></span>

<span data-ttu-id="7e37b-124">En el panel de pantalla más pequeño y estrecho se muestran los botones y los ejes de entrada de Unity que están en estado activo (por ejemplo, se presiona un botón).</span><span class="sxs-lookup"><span data-stu-id="7e37b-124">The smaller, narrow display panel shows the Unity input axed and buttons which are in an active state (ex: a button is pressed).</span></span> <span data-ttu-id="7e37b-125">La presentación de controles activos proporciona una vista de resumen fácil de leer del estado del controlador.</span><span class="sxs-lookup"><span data-stu-id="7e37b-125">The active controls display provides an easy to read summary view of the state of the controller.</span></span>

![Presentación de controles activos](../images/controller-mapping-tool/ActiveControls.png)

## <a name="see-also"></a><span data-ttu-id="7e37b-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7e37b-127">See also</span></span>

- [<span data-ttu-id="7e37b-128">Creación de un proveedor de datos del sistema de entrada</span><span class="sxs-lookup"><span data-stu-id="7e37b-128">Creating an input system data provider</span></span>](../input/create-data-provider.md)
- [<span data-ttu-id="7e37b-129">Herramienta InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="7e37b-129">InputFeatureUsage tool</span></span>](input-feature-usage-tool.md)
