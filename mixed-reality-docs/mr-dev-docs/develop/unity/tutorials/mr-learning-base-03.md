---
title: 'Tutoriales de introducción: 3. Configuración de los perfiles de MRTK'
description: En este curso se muestra cómo configurar los perfiles Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, spatial awareness
ms.localizationpriority: high
ms.openlocfilehash: f6c17dc361846808ec10f1d94932e3089072e642
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300460"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="dbe79-105">3. Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="dbe79-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="dbe79-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="dbe79-106">Overview</span></span>

<span data-ttu-id="dbe79-107">En este tutorial, aprenderá a personalizar y configurar los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="dbe79-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="dbe79-108">Los <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">perfiles de MRTK</a> constituyen un árbol de perfiles anidados que componen la información de configuración sobre cómo se deben inicializar los sistemas y las características de MRTK.</span><span class="sxs-lookup"><span data-stu-id="dbe79-108">The <a href="/windows/mixed-reality/mrtk-unity/features/profiles/profiles" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="dbe79-109">El perfil de nivel superior, el perfil Configuration (Configuración), contiene perfiles anidados para cada uno de los sistemas básicos principales.</span><span class="sxs-lookup"><span data-stu-id="dbe79-109">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="dbe79-110">Cada perfil anidado está diseñado para configurar el comportamiento de su sistema correspondiente.</span><span class="sxs-lookup"><span data-stu-id="dbe79-110">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="dbe79-111">En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial.</span><span class="sxs-lookup"><span data-stu-id="dbe79-111">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="dbe79-112">Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.</span><span class="sxs-lookup"><span data-stu-id="dbe79-112">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="dbe79-113">Como lo visto al implementar el proyecto en HoloLens 2 durante el [tutorial anterior](mr-learning-base-02.md#congratulations), la malla <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> es una colección de mallas que representan la geometría del entorno.</span><span class="sxs-lookup"><span data-stu-id="dbe79-113">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="dbe79-114">Es una visualización útil para ver inicialmente, pero normalmente está desactivada para evitar la distracción visual y el impacto adicional en el rendimiento al tenerla activada.</span><span class="sxs-lookup"><span data-stu-id="dbe79-114">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="dbe79-115">Objetivos</span><span class="sxs-lookup"><span data-stu-id="dbe79-115">Objectives</span></span>

* <span data-ttu-id="dbe79-116">Obtener información sobre cómo personalizar y configurar los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="dbe79-116">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="dbe79-117">Ocultar la malla de reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="dbe79-117">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="dbe79-118">Cambio de la opción de visualización del reconocimiento espacial</span><span class="sxs-lookup"><span data-stu-id="dbe79-118">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="dbe79-119">Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="dbe79-119">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="dbe79-120">Clonar el perfil de configuración predeterminado</span><span class="sxs-lookup"><span data-stu-id="dbe79-120">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="dbe79-121">Habilitar el sistema de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="dbe79-121">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="dbe79-122">Clonar el perfil del sistema de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="dbe79-122">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="dbe79-123">Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.</span><span class="sxs-lookup"><span data-stu-id="dbe79-123">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="dbe79-124">Cambiar la visibilidad de la malla de reconocimiento espacial.</span><span class="sxs-lookup"><span data-stu-id="dbe79-124">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="dbe79-125">De forma predeterminada, los perfiles de MRTK no son editables.</span><span class="sxs-lookup"><span data-stu-id="dbe79-125">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="dbe79-126">Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse.</span><span class="sxs-lookup"><span data-stu-id="dbe79-126">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="dbe79-127">Hay varias capas anidadas de perfiles.</span><span class="sxs-lookup"><span data-stu-id="dbe79-127">There are several nested layers of profiles.</span></span> <span data-ttu-id="dbe79-128">Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.</span><span class="sxs-lookup"><span data-stu-id="dbe79-128">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

[!INCLUDE[](includes/configuring-profile.md)]

## <a name="congratulations"></a><span data-ttu-id="dbe79-129">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="dbe79-129">Congratulations</span></span>

<span data-ttu-id="dbe79-130">En este tutorial, aprendió a clonar, personalizar y configurar los perfiles de MRTK y sus opciones.</span><span class="sxs-lookup"><span data-stu-id="dbe79-130">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dbe79-131">Tutorial siguiente: 4. Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="dbe79-131">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)