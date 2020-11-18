---
title: Controladores de manos y movimiento
description: Obtenga información acerca de los modelos de interacción de los controladores de manos y de movimiento, que pueden quitar el límite entre el virtual y el físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realidad mixta, manos, controladores de movimiento, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: e931e5ec11548d9aab0d1dd7f8921dbc7554abab
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702161"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="a1d82-104">Controladores de manos y movimiento</span><span class="sxs-lookup"><span data-stu-id="a1d82-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="a1d82-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="a1d82-105">Scenarios</span></span>
<span data-ttu-id="a1d82-106">Si decide adoptar este modelo de interacción después de leer la [información general](interaction-fundamentals.md)de la interacción, significa que está desarrollando una aplicación que requiere que los usuarios usen dos manos para interactuar con el mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="a1d82-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="a1d82-107">La aplicación va a lograr el objetivo de quitar el límite entre virtual y física.</span><span class="sxs-lookup"><span data-stu-id="a1d82-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="a1d82-108">Algunos escenarios específicos pueden ser:</span><span class="sxs-lookup"><span data-stu-id="a1d82-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="a1d82-109">Proporcionar a los trabajadores de la información pantallas virtuales 2D con prestaciones de la interfaz de usuario para mostrar y controlar el contenido.</span><span class="sxs-lookup"><span data-stu-id="a1d82-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="a1d82-110">Proporcionar tutoriales y guías de primera línea para las líneas de montaje de fábrica</span><span class="sxs-lookup"><span data-stu-id="a1d82-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="a1d82-111">Desarrollo de herramientas profesionales para ayudar y formar a los profesionales médicos.</span><span class="sxs-lookup"><span data-stu-id="a1d82-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="a1d82-112">Uso de objetos virtuales 3D para decorar el mundo real o crear un segundo mundo.</span><span class="sxs-lookup"><span data-stu-id="a1d82-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="a1d82-113">Crear servicios y juegos basados en la ubicación que usan el mundo real como fondo.</span><span class="sxs-lookup"><span data-stu-id="a1d82-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="a1d82-114">Modalidades de los controladores de manos y de movimiento</span><span class="sxs-lookup"><span data-stu-id="a1d82-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="a1d82-115">[![Manipulación directa con las manos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="a1d82-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="a1d82-116">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="a1d82-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="a1d82-117">Se trata de una moda que aprovecha la eficacia de las manos, con las que los usuarios pueden tocar y manipular directamente los hologramas.</span><span class="sxs-lookup"><span data-stu-id="a1d82-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="a1d82-118">Al aprovechar las experiencias diarias de la vida y proporcionar prestaciones visuales adecuadas, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con los virtuales.</span><span class="sxs-lookup"><span data-stu-id="a1d82-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a1d82-119">[![Apuntar y confirmar con las manos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="a1d82-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="a1d82-120">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="a1d82-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="a1d82-121">Esta modalidad permite a los usuarios interactuar con los hologramas en una distancia.</span><span class="sxs-lookup"><span data-stu-id="a1d82-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="a1d82-122">Permite a los usuarios hacer el mejor uso de los entornos.</span><span class="sxs-lookup"><span data-stu-id="a1d82-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="a1d82-123">Los usuarios pueden colocar hologramas en cualquier lugar y seguir accediendo a ellos desde cualquier distancia.</span><span class="sxs-lookup"><span data-stu-id="a1d82-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="a1d82-124">Los modelos y gestos mentales para controlar y manipular los hologramas 2D y 3D están muy sincronizados con los de manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="a1d82-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a1d82-125">[![Controladores de movimiento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="a1d82-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="a1d82-126">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="a1d82-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="a1d82-127">Los controladores de movimiento son herramientas que amplían las capacidades físicas del usuario al proporcionar interacciones precisas en una gran variedad de distancias al usar una o ambas manos.</span><span class="sxs-lookup"><span data-stu-id="a1d82-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="a1d82-128">Estos accesorios de hardware proporcionan accesos directos a muchas interacciones usadas con frecuencia y proporcionan comentarios Surefooted y táctiles para una variedad de acciones.</span><span class="sxs-lookup"><span data-stu-id="a1d82-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="a1d82-129">Actualmente, los controladores de movimiento solo están disponibles para escenarios de Windows Mixed Reality (WMR).</span><span class="sxs-lookup"><span data-stu-id="a1d82-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="a1d82-130">Consulta también</span><span class="sxs-lookup"><span data-stu-id="a1d82-130">See also</span></span>
* [<span data-ttu-id="a1d82-131">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="a1d82-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="a1d82-132">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="a1d82-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="a1d82-133">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="a1d82-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a1d82-134">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="a1d82-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="a1d82-135">Manos libres</span><span class="sxs-lookup"><span data-stu-id="a1d82-135">Hands-free</span></span>](hands-free.md)
