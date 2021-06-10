---
title: Menú Mano
description: Los menús de mano permiten a los usuarios abrir rápidamente la interfaz de usuario adjunta a mano para las funciones usadas con frecuencia.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600334"
---
# <a name="hand-menu"></a><span data-ttu-id="f06a9-104">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-104">Hand menu</span></span>

![Ubicación de la mano de Ulnar](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="f06a9-106">El menú de mano es uno de los patrones de experiencia de usuario más únicos HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f06a9-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="f06a9-107">Permite abrir rápidamente la interfaz de usuario adjunta a mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="f06a9-108">Puesto que es accesible en cualquier momento y se puede mostrar y ocultar fácilmente, es ideal para acciones rápidas.</span><span class="sxs-lookup"><span data-stu-id="f06a9-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="f06a9-109">Encontrará nuestros procedimientos recomendados para trabajar con menús de mano en la lista siguiente.</span><span class="sxs-lookup"><span data-stu-id="f06a9-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="f06a9-110">También puede encontrar una escena de ejemplo que muestra el menú de mano [en MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span><span class="sxs-lookup"><span data-stu-id="f06a9-110">You can also find an example scene demonstrating the hand menu in [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="f06a9-111">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="f06a9-111">Best practices</span></span>

<span data-ttu-id="f06a9-112">**Mantener pequeño el número de botones**</span><span class="sxs-lookup"><span data-stu-id="f06a9-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="f06a9-113">Debido a la distancia cercana entre un menú con la mano bloqueada y los ojos, y la tendencia de los usuarios a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de atención de la visión es aproximadamente de 10 grados), se recomienda mantener el número de botones pequeño.</span><span class="sxs-lookup"><span data-stu-id="f06a9-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="f06a9-114">En función de nuestra exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (FOV) incluso cuando un usuario mueve las manos al centro de la FOV.</span><span class="sxs-lookup"><span data-stu-id="f06a9-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="f06a9-115">**Uso del menú de mano para una acción rápida**</span><span class="sxs-lookup"><span data-stu-id="f06a9-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="f06a9-116">Elevar un arm y mantener la posición podría provocar fácilmente la agotamiento del arm.</span><span class="sxs-lookup"><span data-stu-id="f06a9-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="f06a9-117">Use un método bloqueado a mano para el menú que requiera una interacción corta.</span><span class="sxs-lookup"><span data-stu-id="f06a9-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="f06a9-118">Si el menú es complejo y requiere tiempos de interacción prolongados, considere la posibilidad de usar bloqueados por el mundo o bloqueados por el cuerpo en su lugar.</span><span class="sxs-lookup"><span data-stu-id="f06a9-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="f06a9-119">**Ángulo de botón o panel**</span><span class="sxs-lookup"><span data-stu-id="f06a9-119">**Button / Panel angle**</span></span>

<span data-ttu-id="f06a9-120">Los menús deben avanzar hacia el cuello opuesto y el centro de la cabeza: esto permite que un movimiento natural de la mano interactúe con el menú con la mano opuesta y evita cualquier posición de mano difícil o poco cómoda al tocar botones.</span><span class="sxs-lookup"><span data-stu-id="f06a9-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="f06a9-121">**Considere la posibilidad de admitir una operación con una mano o con manos libres**</span><span class="sxs-lookup"><span data-stu-id="f06a9-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="f06a9-122">No suponga que las dos manos del usuario siempre están disponibles.</span><span class="sxs-lookup"><span data-stu-id="f06a9-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="f06a9-123">Tenga en cuenta una amplia gama de contextos cuando una o ambas manos no estén disponibles y asegúrese de que el diseño tenga en cuenta esas situaciones.</span><span class="sxs-lookup"><span data-stu-id="f06a9-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="f06a9-124">Para admitir un menú con una mano, puede intentar cambiar la ubicación del menú de bloqueado a bloqueado al mundo cuando la mano se voltea (se queda abajo).</span><span class="sxs-lookup"><span data-stu-id="f06a9-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="f06a9-125">Para escenarios con manos libres, considere la posibilidad de usar un comando de voz para invocar el menú de mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="f06a9-126">**Evite agregar botones cerca de la ruedas (botón inicio del sistema)**</span><span class="sxs-lookup"><span data-stu-id="f06a9-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="f06a9-127">Si los botones del menú de la mano se colocan demasiado cerca del botón inicio, puede desencadenarse accidentalmente al interactuar con el menú de mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="f06a9-128">Menú de mano con controles de interfaz de usuario grandes y complejos</span><span class="sxs-lookup"><span data-stu-id="f06a9-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="f06a9-129">Se recomienda limitar el número de botones o controles de interfaz de usuario en los menús adjuntos a mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="f06a9-130">Esto se debe a que la interacción extendida con un gran número de elementos de la interfaz de usuario puede provocar la agotamiento del arm.</span><span class="sxs-lookup"><span data-stu-id="f06a9-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="f06a9-131">Si su experiencia requiere un menú grande, proporcione una manera fácil para que el usuario bloquee el menú.</span><span class="sxs-lookup"><span data-stu-id="f06a9-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="f06a9-132">Una técnica que se recomienda es bloquear el menú world-lock y, después, cuando la mano se desasocie o se desasocie del usuario.</span><span class="sxs-lookup"><span data-stu-id="f06a9-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="f06a9-133">Una segunda técnica consiste en permitir al usuario tomar directamente el menú con la otra mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="f06a9-134">Cuando el usuario suelta el menú, el menú debería bloquearse.</span><span class="sxs-lookup"><span data-stu-id="f06a9-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="f06a9-135">De este modo, un usuario puede interactuar con varios elementos de la interfaz de usuario de forma cómoda y segura durante un largo período de tiempo.</span><span class="sxs-lookup"><span data-stu-id="f06a9-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="f06a9-136">Cuando el menú esté bloqueado por el mundo, asegúrese de proporcionar una manera de mover el menú y cierre el menú cuando ya no sea necesario.</span><span class="sxs-lookup"><span data-stu-id="f06a9-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="f06a9-137">Para que el menú sea móvil, proporcione identificadores en los lados o en la parte superior del menú.</span><span class="sxs-lookup"><span data-stu-id="f06a9-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="f06a9-138">Agregue un botón Cerrar para permitir que se cierre el menú.</span><span class="sxs-lookup"><span data-stu-id="f06a9-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="f06a9-139">Permita que el menú se vuelva a asociar a la mano cuando el usuario se enfrenta al usuario.</span><span class="sxs-lookup"><span data-stu-id="f06a9-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="f06a9-140">También se recomienda exigir que los usuarios mire a su mano para evitar activaciones falsas (consulte a continuación).</span><span class="sxs-lookup"><span data-stu-id="f06a9-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="f06a9-141">**Menú grande que muestra un problema de facilidad de uso**</span><span class="sxs-lookup"><span data-stu-id="f06a9-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="f06a9-142">**Menú world-locked en la lista desplegable**</span><span class="sxs-lookup"><span data-stu-id="f06a9-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="f06a9-143">**Extracción manual & para bloquear el menú**</span><span class="sxs-lookup"><span data-stu-id="f06a9-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="f06a9-144">Cómo evitar la activación falsa</span><span class="sxs-lookup"><span data-stu-id="f06a9-144">How to prevent false activation</span></span>

<span data-ttu-id="f06a9-145">Si solo usas la forma de un evento para desencadenar el menú de la mano, es posible que aparezca accidentalmente cuando no lo necesites (falso positivo), ya que las personas mueven las manos de forma intencionada (para la comunicación y la manipulación de objetos) y sin querer.</span><span class="sxs-lookup"><span data-stu-id="f06a9-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="f06a9-146">Para reducir las activaciones falsas, agregue un paso adicional además del evento de pie arriba para invocar el menú de la mano (por ejemplo, los dedos completamente abiertos o el usuario que mira intencionadamente a su mano).</span><span class="sxs-lookup"><span data-stu-id="f06a9-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="f06a9-147">**Requerir una mano plana**</span><span class="sxs-lookup"><span data-stu-id="f06a9-147">**Require Flat Palm**</span></span>

<span data-ttu-id="f06a9-148">Al requerir una mano abierta sin formato, puede evitar la activación falsa que podría producirse cuando el usuario manipula objetos o gestos mientras se comunica dentro de un entorno.</span><span class="sxs-lookup"><span data-stu-id="f06a9-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="f06a9-149">**Requerir mirada**</span><span class="sxs-lookup"><span data-stu-id="f06a9-149">**Require Gaze**</span></span>

<span data-ttu-id="f06a9-150">Al exigir al usuario que mire con la mano (ya sea con la mirada con los ojos o la mirada con la cabeza), evita las falsas activaciones porque el usuario tiene que dirigir su atención a la mano como un paso de activación secundario (con un umbral de distancia ajustable que se usa para permitir la comodidad del usuario).</span><span class="sxs-lookup"><span data-stu-id="f06a9-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="f06a9-151">Prácticas recomendadas de selección de ubicación del menú de mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-151">Hand menu placement best practices</span></span>

<span data-ttu-id="f06a9-152">En la anatomía humana, la estructura ulnar es una estructura que se ejecuta cerca del ulna.</span><span class="sxs-lookup"><span data-stu-id="f06a9-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="f06a9-153">El ulna es un fragmento largo que se encuentra en el antebrazo que se extiende desde el dedo más pequeño hasta el más pequeño.</span><span class="sxs-lookup"><span data-stu-id="f06a9-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="f06a9-154">A continuación se muestran dos ubicaciones recomendadas en función de nuestras exploraciones:</span><span class="sxs-lookup"><span data-stu-id="f06a9-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f06a9-155">![Ubicación de la mano lateral de Ulnar dentro de la mano](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="f06a9-156">**A. Ulnar dentro de la mano**</span><span class="sxs-lookup"><span data-stu-id="f06a9-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="f06a9-157">Esta posición es confiable porque las manos no se superponen entre sí.</span><span class="sxs-lookup"><span data-stu-id="f06a9-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="f06a9-158">Esto es fundamental para la detección y el seguimiento precisos de las manos.</span><span class="sxs-lookup"><span data-stu-id="f06a9-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f06a9-159">![Ubicación de la mano lateral de Ulnar por encima de la mano](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="f06a9-160">**B. Ulnar sobre la mano**</span><span class="sxs-lookup"><span data-stu-id="f06a9-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="f06a9-161">Esta ubicación es cómoda para los usuarios porque no necesitan subir demasiado el mano para interactuar con el menú de la mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="f06a9-162">Se recomienda colocar menús **13 cm** por encima de la mano y alinear los botones dentro de la mano de ulnar.</span><span class="sxs-lookup"><span data-stu-id="f06a9-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="f06a9-163">Más información sobre el tamaño óptimo del botón</span><span class="sxs-lookup"><span data-stu-id="f06a9-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="f06a9-164">Por motivos técnicos, se recomienda esta ubicación con una implementación necesaria: el desarrollador tendrá que inmovilizar el menú una vez que la mano opuesta del usuario se acerca a interactuar con él.</span><span class="sxs-lookup"><span data-stu-id="f06a9-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="f06a9-165">Esto evitará la vibración de las manos superpuestas y también permite una selección de destino más rápida de los botones.</span><span class="sxs-lookup"><span data-stu-id="f06a9-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="f06a9-166">HoloLens 2 cámaras identifican las manos con precisión cuando están separadas entre sí.</span><span class="sxs-lookup"><span data-stu-id="f06a9-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="f06a9-167">Las manos superpuestas pueden hacer que los menús de las manos se muevan de la ubicación del anclaje.</span><span class="sxs-lookup"><span data-stu-id="f06a9-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="f06a9-168">Posiciones de menú que no se recomiendan</span><span class="sxs-lookup"><span data-stu-id="f06a9-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="f06a9-169">Hemos realizado una investigación del usuario con diferentes diseños y ubicaciones de menús, no se recomiendan las siguientes ubicaciones de menú; busque las desventajas de cada estudio a continuación:</span><span class="sxs-lookup"><span data-stu-id="f06a9-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="f06a9-170">![Arm superior](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="f06a9-171">**Encima del arm**</span><span class="sxs-lookup"><span data-stu-id="f06a9-171">**Above the arm**</span></span><br>
        <span data-ttu-id="f06a9-172">1 - Difícil de mantener un buen seguimiento de las manos</span><span class="sxs-lookup"><span data-stu-id="f06a9-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="f06a9-173">2 - Provoca la agotamiento del usuario debido a una posición no natural</span><span class="sxs-lookup"><span data-stu-id="f06a9-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f06a9-174">![Dedos superiores](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="f06a9-175">**Dedos superiores**</span><span class="sxs-lookup"><span data-stu-id="f06a9-175">**Above fingers**</span></span><br>
        <span data-ttu-id="f06a9-176">1 - Agotamiento de la mano debido a la mano durante mucho tiempo</span><span class="sxs-lookup"><span data-stu-id="f06a9-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="f06a9-177">2 - Problemas de seguimiento de las manos en el índice y los dedos centrales</span><span class="sxs-lookup"><span data-stu-id="f06a9-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="f06a9-178">![Manola central anterior](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="f06a9-179">**Manola de centro superior**</span><span class="sxs-lookup"><span data-stu-id="f06a9-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="f06a9-180">1 - Problemas de seguimiento de las manos debido a la superposición de las manos</span><span class="sxs-lookup"><span data-stu-id="f06a9-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="f06a9-181">2 - Agotamiento de las manos debido a la mano durante mucho tiempo para interactuar con los menús</span><span class="sxs-lookup"><span data-stu-id="f06a9-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="f06a9-182">![Dedo superior del ](images/TopFingerTip.gif) **dedo**</span><span class="sxs-lookup"><span data-stu-id="f06a9-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="f06a9-183">1 - Problemas de seguimiento de manos</span><span class="sxs-lookup"><span data-stu-id="f06a9-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="f06a9-184">2 - Agotamiento de la mano al mantener la mano por encima de la posición normal</span><span class="sxs-lookup"><span data-stu-id="f06a9-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="f06a9-185">3 - Problemas al presionar botones con otros dedos por accidente debido a un espacio limitado entre los dedos</span><span class="sxs-lookup"><span data-stu-id="f06a9-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="f06a9-186">![Parte posterior del arm](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="f06a9-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="f06a9-187">**Parte posterior del arm**</span><span class="sxs-lookup"><span data-stu-id="f06a9-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="f06a9-188">1 - Puede desencadenar el botón inicio por accidente</span><span class="sxs-lookup"><span data-stu-id="f06a9-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="f06a9-189">2 - No es una posición natural o cómoda</span><span class="sxs-lookup"><span data-stu-id="f06a9-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f06a9-190">Menú de mano en MRTK (Mixed Reality Toolkit) para Unity</span><span class="sxs-lookup"><span data-stu-id="f06a9-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="f06a9-191">**[MRTK proporciona](https://github.com/Microsoft/MixedRealityToolkit-Unity)** scripts y escenas de ejemplo para el menú de mano.</span><span class="sxs-lookup"><span data-stu-id="f06a9-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="f06a9-192">El script del solucionador HandConstraintPalmUp permite adjuntar objetos a las manos con varias opciones configurables.</span><span class="sxs-lookup"><span data-stu-id="f06a9-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="f06a9-193">Los ejemplos de menú de mano de MRTK incluyen opciones útiles, como el requisito de mano plana y mirada para evitar la activación falsa.</span><span class="sxs-lookup"><span data-stu-id="f06a9-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="f06a9-194">Documentación del menú de mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-194">Hand Menu Documentations</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="f06a9-195">Escena de ejemplo de menú de mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="f06a9-196">Puede probar ejemplos de menú de mano en HoloLens 2 con la aplicación Centro de ejemplos de MRTK.</span><span class="sxs-lookup"><span data-stu-id="f06a9-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="f06a9-197">Escena del menú de mano en el centro de ejemplos de MRTK</span><span class="sxs-lookup"><span data-stu-id="f06a9-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="f06a9-198">Vea también</span><span class="sxs-lookup"><span data-stu-id="f06a9-198">See also</span></span>

* [<span data-ttu-id="f06a9-199">Cursores</span><span class="sxs-lookup"><span data-stu-id="f06a9-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f06a9-200">Haces de mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f06a9-201">Botón</span><span class="sxs-lookup"><span data-stu-id="f06a9-201">Button</span></span>](button.md)
* [<span data-ttu-id="f06a9-202">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="f06a9-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f06a9-203">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="f06a9-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f06a9-204">Manipulación</span><span class="sxs-lookup"><span data-stu-id="f06a9-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f06a9-205">Menú Mano</span><span class="sxs-lookup"><span data-stu-id="f06a9-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f06a9-206">Menú Cerca</span><span class="sxs-lookup"><span data-stu-id="f06a9-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f06a9-207">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="f06a9-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f06a9-208">Comando de voz</span><span class="sxs-lookup"><span data-stu-id="f06a9-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f06a9-209">Teclado</span><span class="sxs-lookup"><span data-stu-id="f06a9-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f06a9-210">Información sobre herramientas</span><span class="sxs-lookup"><span data-stu-id="f06a9-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f06a9-211">Claqueta</span><span class="sxs-lookup"><span data-stu-id="f06a9-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="f06a9-212">Control deslizante</span><span class="sxs-lookup"><span data-stu-id="f06a9-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="f06a9-213">Sombreador</span><span class="sxs-lookup"><span data-stu-id="f06a9-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="f06a9-214">Etiquetado y vista frontal continua</span><span class="sxs-lookup"><span data-stu-id="f06a9-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f06a9-215">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="f06a9-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f06a9-216">Magnetismo de superficie</span><span class="sxs-lookup"><span data-stu-id="f06a9-216">Surface magnetism</span></span>](surface-magnetism.md)