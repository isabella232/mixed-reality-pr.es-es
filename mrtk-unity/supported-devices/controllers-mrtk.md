---
title: Controladores en MRTK
description: Documentación sobre el uso de varios controladores con MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/13/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, controladores, HP Reverb, Oculus, HOLO Vive, Hands
ms.openlocfilehash: 953b1cd56dbf7d7a548a3aba8da07ce5875fec74
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145490"
---
# <a name="controllers-in-mrtk"></a><span data-ttu-id="f9876-104">Controladores en MRTK</span><span class="sxs-lookup"><span data-stu-id="f9876-104">Controllers in MRTK</span></span>

<span data-ttu-id="f9876-105">MRTK admite muchos controladores diferentes.</span><span class="sxs-lookup"><span data-stu-id="f9876-105">MRTK has support for many different controllers.</span></span> <span data-ttu-id="f9876-106">Muchos controladores, como VLAN Vive Knuckles y VLAN Vive Wands, funcionarán de forma nativa una vez que se inicia una aplicación creada con MRTK en el dispositivo compatible.</span><span class="sxs-lookup"><span data-stu-id="f9876-106">Many controllers, such as HTC Vive Knuckles and HTC Vive Wands, will work natively once an application built with MRTK is launched on the compatible device.</span></span> <span data-ttu-id="f9876-107">Otros controladores, como las manos articuladas de Oculus Packs y los controladores HP Reverb G2, requieren paquetes adicionales antes de que MRTK los reconozca.</span><span class="sxs-lookup"><span data-stu-id="f9876-107">Other controllers, such as articulated hands on the Oculus Quest and the HP Reverb G2 Controllers, require additional packages before they are recognized by MRTK.</span></span>

<span data-ttu-id="f9876-108">En este documento se describen los escenarios comunes en los que es necesario instalar paquetes adicionales.</span><span class="sxs-lookup"><span data-stu-id="f9876-108">This document will describe the common scenarios where extra packages need to be installed.</span></span> <span data-ttu-id="f9876-109">Para obtener información adicional sobre los controladores, visite la [**página de características**](../features/input/controllers.md).</span><span class="sxs-lookup"><span data-stu-id="f9876-109">For additional information about controllers, visit the [**features page**](../features/input/controllers.md).</span></span> <span data-ttu-id="f9876-110">Para depurar problemas con controladores, consulte la herramienta [ **de asignación de controladores.**](../features/tools/controller-mapping-tool.md)</span><span class="sxs-lookup"><span data-stu-id="f9876-110">To debug issues with controllers, see the [**Controller mapping tool**](../features/tools/controller-mapping-tool.md)</span></span>

## <a name="hp-reverb-g2-controllers"></a><span data-ttu-id="f9876-111">Controladores HP Reverb G2</span><span class="sxs-lookup"><span data-stu-id="f9876-111">HP Reverb G2 Controllers</span></span>

<span data-ttu-id="f9876-112">Para detectar y mostrar los controladores HP Reverb G2 al usar MRTK, siga estos pasos para instalar el [**paquete Microsoft.MixedReality.Input.**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="f9876-112">To detect and show the HP Reverb G2 controllers when using MRTK, follow these steps to install the [**Microsoft.MixedReality.Input**](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers#installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool) package.</span></span> <span data-ttu-id="f9876-113">Una vez instalado este paquete, no es necesario realizar ningún otro cambio en los perfiles predeterminados para que los controladores se muestren en HP Reverb.</span><span class="sxs-lookup"><span data-stu-id="f9876-113">Once this package is installed, no other changes to the default profiles need to be made to have the controllers show up on the HP Reverb.</span></span> 

<span data-ttu-id="f9876-114">Para mostrar los controladores en el editor, debe asegurarse de que usa el mediante el [**complemento OpenXR**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span><span class="sxs-lookup"><span data-stu-id="f9876-114">In order to display the controllers in editor, you need to ensure that you are using the using the [**OpenXR Plugin**](/windows/mixed-reality/develop/unity/openxr-getting-started).</span></span>

## <a name="oculus-controllers"></a><span data-ttu-id="f9876-115">Controladores de Oculus</span><span class="sxs-lookup"><span data-stu-id="f9876-115">Oculus Controllers</span></span> 

<span data-ttu-id="f9876-116">Para visualizar los modelos de controlador de Oculus, siga las instrucciones de implementación de Oculus Raid.</span><span class="sxs-lookup"><span data-stu-id="f9876-116">To visualize Oculus controller models, follow the Oculus Quest deployment instructions.</span></span> <span data-ttu-id="f9876-117">Si desea mostrar las manos virtuales al usar los controladores, asegúrese de que La opción Representar las manos **de avatar** en lugar de los controladores está activada en el sdk de XR Oculus Administrador de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="f9876-117">If you wish to show virtual hands when using the controllers, make sure that **Render Avatar Hands Instead Of Controllers** is checked under the XR SDK Oculus Device Manager.</span></span> <span data-ttu-id="f9876-118">De lo contrario, desactive esta opción.</span><span class="sxs-lookup"><span data-stu-id="f9876-118">Otherwise, uncheck this option.</span></span>

![OculusDeviceManagerVisualizationSettings](../images/cross-platform/oculus-quest/OculusDeviceManager.png)
