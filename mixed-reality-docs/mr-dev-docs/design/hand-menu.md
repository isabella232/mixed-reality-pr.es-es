---
title: Menú Mano
description: Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menú, botón, acceso rápido, diseño, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: e222d792d883ccacc71b177fbde21979c8dfcc77
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299920"
---
# <a name="hand-menu"></a><span data-ttu-id="9a9b0-104">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-104">Hand menu</span></span>

![Ubicación del lado de ulnar](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="9a9b0-106">El menú de la mano es uno de los patrones de experiencia de usuario más únicos de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="9a9b0-107">Permite abrir rápidamente la interfaz de usuario asociada a la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="9a9b0-108">Dado que es accesible en cualquier momento y se puede mostrar y ocultar fácilmente, es excelente para acciones rápidas.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="9a9b0-109">Encontrará las prácticas recomendadas para trabajar con menús de mano en la lista siguiente.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="9a9b0-110">También puede encontrar una escena de ejemplo en la que se muestra el menú de la mano en [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span><span class="sxs-lookup"><span data-stu-id="9a9b0-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="9a9b0-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="9a9b0-111">Best practices</span></span>

<span data-ttu-id="9a9b0-112">**Mantener el número de botones pequeños**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="9a9b0-113">Debido a la distancia de cierre entre un menú bloqueado a mano y los ojos, y la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), se recomienda mantener el número de botones reducidos.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="9a9b0-114">En función de la exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (campo de visualización) incluso cuando un usuario mueve sus manos al centro del campo de contenido.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="9a9b0-115">**Usar el menú mano para una acción rápida**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="9a9b0-116">La elevación de una ARM y el mantenimiento de la posición pueden provocar una fatiga ARM.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="9a9b0-117">Use un método bloqueado manualmente para el menú que requiera una breve interacción.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="9a9b0-118">Si el menú es complejo y requiere tiempos de interacción extendidos, considere la posibilidad de usar en su lugar el uso de bloqueos internacionales o del cuerpo.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="9a9b0-119">**Ángulo de botón/panel**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-119">**Button / Panel angle**</span></span>

<span data-ttu-id="9a9b0-120">Los menús deben encabezarse hacia el hombro opuesto y el centro del cabezal: Esto permite que un movimiento de mano normal interactúe con el menú con la mano opuesta y evite las posiciones de mano extrañas o inconvenientes al tocar botones.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="9a9b0-121">**Considere la posibilidad de admitir operaciones Monodireccionales o gratuitas**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="9a9b0-122">No asuma que las dos manos del usuario están siempre disponibles.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="9a9b0-123">Tenga en cuenta una amplia gama de contextos cuando una o ambas manecillas no estén disponibles y asegúrese de que su diseño tiene en cuenta esas situaciones.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="9a9b0-124">Para admitir un menú de una mano, puede intentar realizar la transición de la ubicación del menú desde el bloque bloqueado a un mundo bloqueado cuando la mano se voltee (se desplace hacia abajo).</span><span class="sxs-lookup"><span data-stu-id="9a9b0-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="9a9b0-125">En escenarios gratuitos, considere la posibilidad de usar un comando de voz para invocar el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="9a9b0-126">**Evitar agregar botones cerca de la muñeca (botón Inicio del sistema)**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="9a9b0-127">Si los botones de menú de la mano se colocan demasiado cerca del botón Inicio, se puede desencadenar accidentalmente durante la interacción con el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="9a9b0-128">Menú mano con controles de interfaz de usuario grandes y complejos</span><span class="sxs-lookup"><span data-stu-id="9a9b0-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="9a9b0-129">Se recomienda limitar el número de botones o controles de interfaz de usuario en los menús conectados a mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="9a9b0-130">Esto se debe a que la interacción extendida con un gran número de elementos de la interfaz de usuario puede causar fatiga ARM.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="9a9b0-131">Si su experiencia requiere un menú grande, proporcione un método sencillo para que el usuario bloquee el menú.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="9a9b0-132">Una técnica que se recomienda es usar el menú de bloqueo internacional cuando la mano se coloca o se mueve fuera del usuario.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="9a9b0-133">Una segunda técnica consiste en permitir que el usuario capte directamente el menú con la otra mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="9a9b0-134">Cuando el usuario suelta el menú, el menú debe ser un bloqueo universal.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="9a9b0-135">De este modo, un usuario puede interactuar con varios elementos de la interfaz de usuario de forma cómoda y confiable durante un período de tiempo prolongado.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="9a9b0-136">Cuando el menú esté bloqueado mundialmente, asegúrese de proporcionar una manera de desplace el menú y cierre el menú cuando ya no se necesite.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="9a9b0-137">Haga que el menú sea móvil proporcionando controladores en los lados o en la parte superior del menú.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="9a9b0-138">Agregue un botón Cerrar para permitir que el menú se cierre.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="9a9b0-139">Permite que el menú se vuelva a asociar a la mano cuando el usuario se enfrente al usuario.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="9a9b0-140">También se recomienda requerir que los usuarios se admiran a su mano para evitar activaciones falsas (consulte a continuación).</span><span class="sxs-lookup"><span data-stu-id="9a9b0-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="9a9b0-141">**Menú grande que muestra un problema de facilidad de uso**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="9a9b0-142">**Descartado de la mano del menú con bloqueo mundial**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="9a9b0-143">**Extracción manual & extraer del menú**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="9a9b0-144">Cómo evitar la activación falsa</span><span class="sxs-lookup"><span data-stu-id="9a9b0-144">How to prevent false activation</span></span>

<span data-ttu-id="9a9b0-145">Si usa solo Palm como un evento para desencadenar el menú de la mano, puede aparecer accidentalmente cuando no lo necesite (falsos positivos), ya que los usuarios mueven sus manos intencionadamente (para la comunicación y la manipulación de objetos) y de forma involuntaria.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="9a9b0-146">Para reducir las activaciones falsas, agregue un paso adicional además del evento de mano para invocar el menú de la mano (como los dedos totalmente abiertos o el usuario intencionadamente Gazing en su mano).</span><span class="sxs-lookup"><span data-stu-id="9a9b0-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="9a9b0-147">**Requerir Palm plana**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-147">**Require Flat Palm**</span></span>

<span data-ttu-id="9a9b0-148">Al requerir una mano abierta plana, puede evitar la activación falsa que se puede producir cuando el usuario manipula objetos o gestos mientras se comunica dentro de un entorno.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="9a9b0-149">**Requerir mira**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-149">**Require Gaze**</span></span>

<span data-ttu-id="9a9b0-150">Al solicitar al usuario que se ponga en mano (ya sea con miras hacia abajo o hacia abajo), se evitan las activaciones falsas debido a que el usuario tiene que dirigir su atención a la mano como un paso de activación secundario (con un umbral de distancia ajustable que se usa para permitir la comodidad del usuario).</span><span class="sxs-lookup"><span data-stu-id="9a9b0-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="9a9b0-151">Procedimientos recomendados de selección de ubicación de menús</span><span class="sxs-lookup"><span data-stu-id="9a9b0-151">Hand menu placement best practices</span></span>

<span data-ttu-id="9a9b0-152">En la anatomía humana, el ulnar Nerve es un Nerve que se ejecuta cerca del hueso de Ulna.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="9a9b0-153">Ulna es un hueso largo que se encuentra en el Forearm que se estira desde el codo hasta el dedo más pequeño.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="9a9b0-154">A continuación se muestran dos ubicaciones recomendadas basadas en nuestras exploraciones:</span><span class="sxs-lookup"><span data-stu-id="9a9b0-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9a9b0-155">![Ulnar ubicación lateral dentro de Palm](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="9a9b0-156">**A. ulnar en Palm**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="9a9b0-157">Esta posición es confiable porque las manos no se superponen entre sí.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="9a9b0-158">Esto es fundamental para la detección y el seguimiento precisos de la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9a9b0-159">![Ubicación del lado de ulnar por encima de la mano](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="9a9b0-160">**B. ulnar por encima de la mano**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="9a9b0-161">Esta ubicación es cómoda para los usuarios porque no necesitan aumentar demasiado el brazo para interactuar con el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="9a9b0-162">Se recomienda colocar los menús **13 cm** por encima de la palma y alinear los botones dentro de la palma de ulnar.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="9a9b0-163">Obtenga más información sobre el tamaño óptimo del botón</span><span class="sxs-lookup"><span data-stu-id="9a9b0-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="9a9b0-164">Por motivos técnicos, recomendamos esta ubicación con una implementación necesaria: el desarrollador deberá inmovilizar el menú cuando la mano del usuario se acerque a la interacción con él.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="9a9b0-165">Esto evitará la vibración de las manos superpuestas y también permite un destino más rápido de los botones.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="9a9b0-166">Las cámaras de HoloLens 2 identifican con precisión cuándo son independientes entre sí.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="9a9b0-167">Las manos superpuestas pueden provocar que los menús de la mano se alejen de la ubicación del delimitador.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="9a9b0-168">Posiciones de menú que no se recomiendan</span><span class="sxs-lookup"><span data-stu-id="9a9b0-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="9a9b0-169">Hemos realizado una investigación de usuario con distintos diseños y ubicaciones de menús; **no se recomiendan** las siguientes ubicaciones de menú:</span><span class="sxs-lookup"><span data-stu-id="9a9b0-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="9a9b0-170">![Anterior ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="9a9b0-171">**Por encima del brazo**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-171">**Above the arm**</span></span><br>
        <span data-ttu-id="9a9b0-172">1-difícil de mantener un buen seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="9a9b0-173">2-causa la fatiga del usuario debido a una posición no natural</span><span class="sxs-lookup"><span data-stu-id="9a9b0-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9a9b0-174">![Los dedos anteriores](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="9a9b0-175">**Los dedos anteriores**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-175">**Above fingers**</span></span><br>
        <span data-ttu-id="9a9b0-176">la fatiga de un lado a otro debido a la falta de mano durante mucho tiempo</span><span class="sxs-lookup"><span data-stu-id="9a9b0-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="9a9b0-177">2-problemas de seguimiento en el índice y los dedos del centro</span><span class="sxs-lookup"><span data-stu-id="9a9b0-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="9a9b0-178">![Por encima del centro Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="9a9b0-179">**Anterior: Palm del centro**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="9a9b0-180">1-problemas de seguimiento debido a las manos superpuestas</span><span class="sxs-lookup"><span data-stu-id="9a9b0-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="9a9b0-181">fatiga de 2 a mano debido a la retención de manos durante mucho tiempo para interactuar con los menús</span><span class="sxs-lookup"><span data-stu-id="9a9b0-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="9a9b0-182">![Primer dedo ](images/TopFingerTip.gif) **principal**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="9a9b0-183">1-problemas de seguimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="9a9b0-184">la fatiga de 2 manos desde la mano por encima de la postura normal</span><span class="sxs-lookup"><span data-stu-id="9a9b0-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="9a9b0-185">3-problemas al presionar botones con otros dedos por accidente debido al espacio limitado entre los dedos</span><span class="sxs-lookup"><span data-stu-id="9a9b0-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="9a9b0-186">![Parte posterior del brazo](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="9a9b0-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="9a9b0-187">**Parte posterior del brazo**</span><span class="sxs-lookup"><span data-stu-id="9a9b0-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="9a9b0-188">1-puede desencadenar el botón Inicio por accidente</span><span class="sxs-lookup"><span data-stu-id="9a9b0-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="9a9b0-189">2-no es una posición natural o cómoda</span><span class="sxs-lookup"><span data-stu-id="9a9b0-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="9a9b0-190">Menú de la mano en MRTK (kit de herramientas de realidad mixta) para Unity</span><span class="sxs-lookup"><span data-stu-id="9a9b0-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="9a9b0-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y escenas de ejemplo para el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="9a9b0-192">El script de Solver de HandConstraintPalmUp le permite adjuntar cualquier objeto a las manos con varias opciones configurables.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="9a9b0-193">Los ejemplos de los menús de MRTK incluyen opciones útiles como el requisito plano de Palm y fijamente para evitar la activación falsa.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="9a9b0-194">Documentación del menú de la mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-194">Hand Menu Documentations</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="9a9b0-195">Escenario de ejemplo de menú de mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="9a9b0-196">Puede probar ejemplos de menú de la mano en HoloLens 2 con la aplicación Hub de ejemplos de MRTK.</span><span class="sxs-lookup"><span data-stu-id="9a9b0-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="9a9b0-197">Escenario de menú de mano en el concentrador de ejemplos de MRTK</span><span class="sxs-lookup"><span data-stu-id="9a9b0-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="9a9b0-198">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9a9b0-198">See also</span></span>

* [<span data-ttu-id="9a9b0-199">Cursores</span><span class="sxs-lookup"><span data-stu-id="9a9b0-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="9a9b0-200">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="9a9b0-201">Botón</span><span class="sxs-lookup"><span data-stu-id="9a9b0-201">Button</span></span>](button.md)
* [<span data-ttu-id="9a9b0-202">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="9a9b0-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="9a9b0-203">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="9a9b0-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="9a9b0-204">Manipulación</span><span class="sxs-lookup"><span data-stu-id="9a9b0-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="9a9b0-205">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="9a9b0-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="9a9b0-206">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="9a9b0-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="9a9b0-207">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="9a9b0-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="9a9b0-208">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="9a9b0-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="9a9b0-209">Teclado</span><span class="sxs-lookup"><span data-stu-id="9a9b0-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="9a9b0-210">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="9a9b0-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="9a9b0-211">Claqueta</span><span class="sxs-lookup"><span data-stu-id="9a9b0-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="9a9b0-212">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="9a9b0-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="9a9b0-213">Sombreador</span><span class="sxs-lookup"><span data-stu-id="9a9b0-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="9a9b0-214">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="9a9b0-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="9a9b0-215">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="9a9b0-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="9a9b0-216">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="9a9b0-216">Surface magnetism</span></span>](surface-magnetism.md)
