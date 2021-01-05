---
title: Controladores de manos y movimiento
description: Obtenga información acerca de los modelos de interacción de los controladores de manos y de movimiento, que pueden quitar el límite entre el virtual y el físico.
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: Realidad mixta, manos, controladores de movimiento, interacción, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847317"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="ce434-104">Controladores de manos y movimiento</span><span class="sxs-lookup"><span data-stu-id="ce434-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="ce434-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="ce434-105">Scenarios</span></span>

<span data-ttu-id="ce434-106">Después de leer la [información general](interaction-fundamentals.md)de la interacción, elija el modelo de interacción del controlador de movimiento y la mano.</span><span class="sxs-lookup"><span data-stu-id="ce434-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="ce434-107">Esto significa que está desarrollando una aplicación que requiere que los usuarios usen dos manos para interactuar con el mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="ce434-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="ce434-108">La aplicación va a lograr el objetivo de quitar el límite entre virtual y física.</span><span class="sxs-lookup"><span data-stu-id="ce434-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="ce434-109">Algunos escenarios específicos pueden ser:</span><span class="sxs-lookup"><span data-stu-id="ce434-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="ce434-110">Proporcionar a los trabajadores de la información pantallas virtuales 2D con prestaciones de la interfaz de usuario para mostrar y controlar el contenido.</span><span class="sxs-lookup"><span data-stu-id="ce434-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="ce434-111">Proporcionar tutoriales y guías de primera línea para las líneas de montaje de fábrica</span><span class="sxs-lookup"><span data-stu-id="ce434-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="ce434-112">Desarrollo de herramientas profesionales para ayudar y formar a los profesionales médicos.</span><span class="sxs-lookup"><span data-stu-id="ce434-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="ce434-113">Uso de objetos virtuales 3D para decorar el mundo real o crear un segundo mundo.</span><span class="sxs-lookup"><span data-stu-id="ce434-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="ce434-114">Crear servicios y juegos basados en la ubicación que usan el mundo real como fondo.</span><span class="sxs-lookup"><span data-stu-id="ce434-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="ce434-115">Modalidades de los controladores de manos y de movimiento</span><span class="sxs-lookup"><span data-stu-id="ce434-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ce434-116">[![Manipulación directa con las manos](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="ce434-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="ce434-117">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="ce434-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="ce434-118">Modalidad que aplica la potencia de las manos que los usuarios pueden usar para tocar y manipular los hologramas.</span><span class="sxs-lookup"><span data-stu-id="ce434-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="ce434-119">Mediante el uso de experiencias de vida diaria y la prestación de prestaciones visuales adecuadas, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con los virtuales.</span><span class="sxs-lookup"><span data-stu-id="ce434-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ce434-120">[![Apuntar y confirmar con las manos](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="ce434-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="ce434-121">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="ce434-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="ce434-122">Esta modalidad permite a los usuarios interactuar con los hologramas en una distancia.</span><span class="sxs-lookup"><span data-stu-id="ce434-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="ce434-123">Permite a los usuarios hacer el mejor uso de los entornos.</span><span class="sxs-lookup"><span data-stu-id="ce434-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="ce434-124">Los usuarios pueden colocar hologramas en cualquier lugar y seguir accediendo a ellos desde cualquier distancia.</span><span class="sxs-lookup"><span data-stu-id="ce434-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="ce434-125">Los modelos y gestos mentales para controlar y manipular los hologramas 2D y 3D están muy sincronizados con los de manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="ce434-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="ce434-126">[![Controladores de movimiento](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="ce434-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="ce434-127">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="ce434-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="ce434-128">Los controladores de movimiento amplían las capacidades físicas del usuario con interacciones precisas en un intervalo de distancias al usar una o ambas manos.</span><span class="sxs-lookup"><span data-stu-id="ce434-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="ce434-129">Estos accesorios de hardware proporcionan accesos directos a muchas de las interacciones usadas comúnmente y proporcionan comentarios de seguridad en el pie de página para realizar diversas acciones.</span><span class="sxs-lookup"><span data-stu-id="ce434-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="ce434-130">Actualmente, los controladores de movimiento solo están disponibles para escenarios de Windows Mixed Reality (WMR).</span><span class="sxs-lookup"><span data-stu-id="ce434-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="ce434-131">Consulta también</span><span class="sxs-lookup"><span data-stu-id="ce434-131">See also</span></span>
* [<span data-ttu-id="ce434-132">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="ce434-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="ce434-133">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="ce434-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="ce434-134">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="ce434-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="ce434-135">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="ce434-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="ce434-136">Manos libres</span><span class="sxs-lookup"><span data-stu-id="ce434-136">Hands-free</span></span>](hands-free.md)
