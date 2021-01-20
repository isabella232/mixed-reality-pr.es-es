---
title: Mirada y confirmación
description: Obtenga información sobre el modelo de entrada de la vista y la confirmación, incluidos dos tipos de mirados (mirados y mirados) y varios tipos de confirmación.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidad mixta, miración de miración, interacción, diseño, seguimiento ocular, seguimiento de cabezales, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, HoloLens, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: bfbf58ad065f91b27208d36ba63672ee5c28dfdd
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582338"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="b4dc2-104">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="b4dc2-104">Gaze and commit</span></span>

<span data-ttu-id="b4dc2-105">La acción de _mirar y confirmar_ es un modelo de entrada fundamental estrechamente relacionado con la forma en que interactuamos con nuestros equipos mediante el mouse: _punto & clic_.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="b4dc2-106">En esta página, se presentan dos tipos de entradas de miradas (de encabezado y ojo) y distintos tipos de acciones de confirmación.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="b4dc2-107">La acción de _mirar y confirmar_ se considera un modelo de entrada lejano con manipulación indirecta.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="b4dc2-108">Se usa mejor para interactuar con el contenido holográfica que no está disponible.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="b4dc2-109">Los auriculares de realidad mixta pueden usar la posición y la orientación del encabezado del usuario para determinar su vector de dirección principal.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="b4dc2-110">Piense en un láser que apunta directamente desde el principio del usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="b4dc2-111">Esto es una aproximación bastante general de dónde mira el usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="b4dc2-112">La aplicación puede formar una intersección con este rayo con objetos virtuales o del mundo real y dibujar un cursor en esa ubicación para que el usuario sepa de qué se dirige.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="b4dc2-113">Además de los cabezales, algunos auriculares de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento ocular que producen un vector de mirada ocular.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="b4dc2-114">Esto proporciona una medida específica de adónde mira el usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="b4dc2-115">En ambos casos, la mirada representa una señal importante para la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="b4dc2-116">Cuanto mejor sea el sistema para interpretar y predecir las acciones deseadas del usuario, mayor será la satisfacción y el rendimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="b4dc2-117">A continuación se muestran algunos ejemplos de cómo puede beneficiarse de un desarrollador de realidad mixta con miras a la mirada:</span><span class="sxs-lookup"><span data-stu-id="b4dc2-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="b4dc2-118">La aplicación puede intersectar con los hologramas de la escena para determinar dónde se encuentra la atención del usuario (con más precisión con miras).</span><span class="sxs-lookup"><span data-stu-id="b4dc2-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="b4dc2-119">La aplicación puede realizar gestos de canal y pulsaciones del controlador en función de la mirada del usuario, lo que permite al usuario seleccionar, activar, capturar, desplazarse o interactuar de otro modo con sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="b4dc2-120">La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real intersectando su rayo con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="b4dc2-121">La aplicación puede saber si el usuario no está buscando la dirección de un objeto importante, lo que puede conducir a que la aplicación proporcione indicaciones visuales y de audio para que se conviertan en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="b4dc2-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b4dc2-123"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="b4dc2-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="b4dc2-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4dc2-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b4dc2-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b4dc2-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b4dc2-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="b4dc2-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b4dc2-127">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="b4dc2-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="b4dc2-128">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="b4dc2-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="b4dc2-129">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="b4dc2-130">➕ Opción alternativa</span><span class="sxs-lookup"><span data-stu-id="b4dc2-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="b4dc2-131">Mirada con los ojos y confirmación</span><span class="sxs-lookup"><span data-stu-id="b4dc2-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="b4dc2-132">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="b4dc2-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="b4dc2-133">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="b4dc2-134">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="b4dc2-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="b4dc2-135">Mirar</span><span class="sxs-lookup"><span data-stu-id="b4dc2-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="b4dc2-136">¿Está atento o mira la cabeza?</span><span class="sxs-lookup"><span data-stu-id="b4dc2-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="b4dc2-137">Hay varias consideraciones que deben tenerse en cuenta a la hora de usar el modelo de entrada "mira fijamente y confirmar" o "encabezado de mira y confirmación".</span><span class="sxs-lookup"><span data-stu-id="b4dc2-137">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="b4dc2-138">Si va a desarrollar para un casco envolvente o para HoloLens (1ª generación), la elección es sencilla: encabezado y confirmación.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-138">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="b4dc2-139">Si está desarrollando para HoloLens 2, la elección es un poco más difícil.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-139">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="b4dc2-140">Es importante comprender las ventajas y los desafíos que acompañan a cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-140">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="b4dc2-141">Hemos compilado algunos grandes Pro y con en la tabla siguiente para diferenciar las orientaciones de mirada y miradas.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-141">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="b4dc2-142">Esta información es muy completa y le sugerimos que obtenga más información sobre el objetivo de mirarnos en la realidad mixta aquí:</span><span class="sxs-lookup"><span data-stu-id="b4dc2-142">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="b4dc2-143">[Seguimiento ocular de hololens 2](eye-tracking.md): introducción general de nuestra nueva funcionalidad de seguimiento ocular en hololens 2, que incluye algunas instrucciones para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-143">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="b4dc2-144">[Interacción ocular](eye-gaze-interaction.md): consideraciones de diseño y recomendaciones cuando se planea usar el seguimiento ocular como entrada.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-144">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="b4dc2-145"><strong>Apuntar a la mirada</strong></span><span class="sxs-lookup"><span data-stu-id="b4dc2-145"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="b4dc2-146"><strong>Establecer el destino de la mirada con la cabeza</strong></span><span class="sxs-lookup"><span data-stu-id="b4dc2-146"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-147">Fast!</span><span class="sxs-lookup"><span data-stu-id="b4dc2-147">Fast!</span></span></td>
        <td><span data-ttu-id="b4dc2-148">Lentamente</span><span class="sxs-lookup"><span data-stu-id="b4dc2-148">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-149">Bajo esfuerzo (apenas se necesitan movimientos del cuerpo)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-149">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="b4dc2-150">Puede ser fatiguing (por ejemplo, la presión del cuello)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-150">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-151">No requiere un cursor, pero se recomiendan comentarios sutiles</span><span class="sxs-lookup"><span data-stu-id="b4dc2-151">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="b4dc2-152">Requiere para mostrar un cursor</span><span class="sxs-lookup"><span data-stu-id="b4dc2-152">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-153">Sin movimientos sin efecto ocular (por ejemplo, no es bueno para dibujar)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-153">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="b4dc2-154">Más controlado y explícito</span><span class="sxs-lookup"><span data-stu-id="b4dc2-154">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-155">Difícil para destinos pequeños (por ejemplo, botones pequeños o weblinks)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-155">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="b4dc2-156">Estable!</span><span class="sxs-lookup"><span data-stu-id="b4dc2-156">Reliable!</span></span> <span data-ttu-id="b4dc2-157">¡ Gran retroceso!</span><span class="sxs-lookup"><span data-stu-id="b4dc2-157">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b4dc2-158">...</span><span class="sxs-lookup"><span data-stu-id="b4dc2-158">...</span></span></td>
        <td><span data-ttu-id="b4dc2-159">...</span><span class="sxs-lookup"><span data-stu-id="b4dc2-159">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="b4dc2-160">Tanto si usa la vista de encabezado o miras hacia abajo para el modelo de entrada de la mirada y la confirmación, cada uno viene con distintos conjuntos de restricciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-160">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="b4dc2-161">Estos se describen por separado en los artículos de [miras](gaze-and-commit-eyes.md) y de la [mirada y el](gaze-and-commit-head.md) dedo.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-161">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="b4dc2-162">Cursor</span><span class="sxs-lookup"><span data-stu-id="b4dc2-162">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b4dc2-163">En el caso de la mirada, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) u otra indicación visual o de auditoría para dar la confianza del usuario en lo que están a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-163">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="b4dc2-164">Normalmente, este cursor se coloca en el mundo en el que su rayo de miras hacia abajo intersecta primero con un objeto, que puede ser un holograma o una superficie del mundo real.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-164">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="b4dc2-165">En general, se recomienda *no* mostrar un cursor, ya que esto puede resultar más rápido y molesto para el usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-165">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="b4dc2-166">En su lugar, resalte de forma sutilmente los destinos visuales o use un cursor de ojo tenue para proporcionar confianza sobre lo que está a punto de interactuar con el usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-166">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="b4dc2-167">Para obtener más información, consulte nuestra [Guía de diseño para la entrada basada en ojo](eye-tracking.md) en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-167">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="b4dc2-168">![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-168">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="b4dc2-169">*Imagen: un cursor visual de ejemplo para mostrar la mirada*</span><span class="sxs-lookup"><span data-stu-id="b4dc2-169">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="b4dc2-170">Commit</span><span class="sxs-lookup"><span data-stu-id="b4dc2-170">Commit</span></span>
<span data-ttu-id="b4dc2-171">Después de hablar sobre las distintas formas de _mirarnos_ en un destino, vamos a hablar un poco más sobre la parte de _confirmación_ en la _mirada y la confirmación_.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-171">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="b4dc2-172">Después de establecer como destino un objeto o un elemento de la interfaz de usuario, el usuario puede interactuar o hacer clic en él mediante una entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-172">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="b4dc2-173">Esto se conoce como el paso de confirmación del modelo de entrada.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-173">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="b4dc2-174">Se admiten los siguientes métodos de confirmación:</span><span class="sxs-lookup"><span data-stu-id="b4dc2-174">The following commit methods are supported:</span></span>
- <span data-ttu-id="b4dc2-175">Gesto de puntear en el aire (es decir, levantar la mano del usuario y reunir el dedo del índice y el control de posición)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-175">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="b4dc2-176">Decir _"seleccionar"_ o uno de los comandos de voz de destino</span><span class="sxs-lookup"><span data-stu-id="b4dc2-176">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="b4dc2-177">Presionar un solo botón en un [clic de HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-177">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="b4dc2-178">Presione el botón ' A ' en un controlador para juegos de Xbox</span><span class="sxs-lookup"><span data-stu-id="b4dc2-178">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="b4dc2-179">Presione el botón ' A ' en un controlador adaptable de Xbox</span><span class="sxs-lookup"><span data-stu-id="b4dc2-179">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="b4dc2-180">Gesto de puntear y tocar el aire</span><span class="sxs-lookup"><span data-stu-id="b4dc2-180">Gaze and air tap gesture</span></span>
<span data-ttu-id="b4dc2-181">Pulsar en el aire es hacer el gesto de pulsar con la mano vertical.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-181">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="b4dc2-182">Para usar una derivación de aire, eleve el dedo del índice a la posición listo y, a continuación, acerque el dedo y vuelva a colocar el dedo de índice en la versión.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-182">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="b4dc2-183">En HoloLens (1ª generación), Air TAP es la entrada secundaria más común.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-183">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="b4dc2-184">![Dedo en la posición listo](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-184">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="b4dc2-185">**Dedo en la posición listo**</span><span class="sxs-lookup"><span data-stu-id="b4dc2-185">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="b4dc2-186">![Presione el dedo para pulsar o hacer clic en](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-186">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="b4dc2-187">**Presione el dedo para pulsar o hacer clic en**</span><span class="sxs-lookup"><span data-stu-id="b4dc2-187">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="b4dc2-188">Air TAP también está disponible en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-188">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="b4dc2-189">Se ha relajado de la versión original.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-189">It has been relaxed from the original version.</span></span> <span data-ttu-id="b4dc2-190">Ahora se admiten casi todos los tipos de gestos, siempre y cuando la mano esté en vertical y manteniendo todavía.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-190">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="b4dc2-191">Esto hace que sea mucho más fácil para los usuarios aprender y usar el gesto.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-191">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="b4dc2-192">Esta nueva derivación de aire reemplaza a la antigua a través de la misma API, por lo que las aplicaciones existentes tendrán el nuevo comportamiento automáticamente después de volver a compilar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-192">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="b4dc2-193">Mira y "selecciona" comando de voz</span><span class="sxs-lookup"><span data-stu-id="b4dc2-193">Gaze and "Select" voice command</span></span>
<span data-ttu-id="b4dc2-194">Los comandos de voz son uno de los métodos de interacción principales en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-194">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="b4dc2-195">Proporciona un potente mecanismo gratuito para controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-195">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="b4dc2-196">Existen diferentes tipos de modelos de interacción de voz:</span><span class="sxs-lookup"><span data-stu-id="b4dc2-196">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="b4dc2-197">Comando "Select" genérico que usa una acción de hacer clic o confirmar como entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-197">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="b4dc2-198">Los comandos de objeto (por ejemplo, "cerrar" o "hacer que sean más grandes") realizan y confirman una acción como entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-198">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="b4dc2-199">Los comandos globales (por ejemplo, "ir a Inicio") no requieren un destino.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-199">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="b4dc2-200">Las interfaces o entidades de usuario de conversación como Cortana tienen una capacidad de lenguaje natural de AI.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-200">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="b4dc2-201">Comandos de voz personalizados</span><span class="sxs-lookup"><span data-stu-id="b4dc2-201">Custom voice commands</span></span>

<span data-ttu-id="b4dc2-202">Para obtener más información acerca de los detalles y una lista completa de los comandos de voz disponibles y cómo usarlos, consulte nuestra guía de [comandos de voz](../out-of-scope/voice-design.md) .</span><span class="sxs-lookup"><span data-stu-id="b4dc2-202">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="b4dc2-203">Clic en fijamente y HoloLens</span><span class="sxs-lookup"><span data-stu-id="b4dc2-203">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b4dc2-204">El clic de HoloLens es el primer dispositivo periférico creado específicamente para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-204">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="b4dc2-205">Está incluida en la edición de desarrollo de HoloLens (1º gen).</span><span class="sxs-lookup"><span data-stu-id="b4dc2-205">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="b4dc2-206">El clic de HoloLens permite que un usuario haga clic con el movimiento mínimo de mano y se confirme como una entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-206">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="b4dc2-207">El clic de HoloLens se conecta a HoloLens (1º gen) o a HoloLens 2 con Bluetooth de baja energía (BTLE).</span><span class="sxs-lookup"><span data-stu-id="b4dc2-207">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="b4dc2-208">Más información e instrucciones para emparejar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="b4dc2-208">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="b4dc2-209">*Imagen: clic de HoloLens*</span><span class="sxs-lookup"><span data-stu-id="b4dc2-209">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="b4dc2-211">Controlador inalámbrico de mira y Xbox</span><span class="sxs-lookup"><span data-stu-id="b4dc2-211">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="b4dc2-212">La controladora inalámbrica Xbox realiza una acción de clic como entrada secundaria mediante el botón "A".</span><span class="sxs-lookup"><span data-stu-id="b4dc2-212">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="b4dc2-213">El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-213">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="b4dc2-214">Si desea personalizar el controlador, use la aplicación accesorios de Xbox para configurar el controlador inalámbrico de Xbox.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-214">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="b4dc2-215">Cómo emparejar un controlador Xbox con su PC</span><span class="sxs-lookup"><span data-stu-id="b4dc2-215">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="b4dc2-216">*Imagen: controlador inalámbrico Xbox*</span><span class="sxs-lookup"><span data-stu-id="b4dc2-216">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controlador inalámbrico de Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="b4dc2-218">Mira el controlador adaptable de la consola Xbox</span><span class="sxs-lookup"><span data-stu-id="b4dc2-218">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="b4dc2-219">Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el controlador adaptable Xbox es un concentrador unificado para dispositivos que ayuda a hacer que la realidad mixta sea más accesible.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-219">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="b4dc2-220">El controlador adaptable de la Xbox realiza una acción de clic como entrada secundaria mediante el botón "A".</span><span class="sxs-lookup"><span data-stu-id="b4dc2-220">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="b4dc2-221">El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-221">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="b4dc2-222">Si desea personalizar el controlador, use la aplicación accesorios de Xbox para configurar el controlador adaptable de Xbox.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-222">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="b4dc2-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="b4dc2-224">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="b4dc2-224">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="b4dc2-225">Conecte dispositivos externos como conmutadores, botones, montajes y joysticks para crear una experiencia de controlador personalizada que sea suya exclusiva.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-225">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="b4dc2-226">Las entradas de los botones, el stick analógico y el desencadenador se controlan con dispositivos de asistencia conectados a través de conectores 3,5-mm y puertos USB.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-226">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="b4dc2-227">![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="b4dc2-227">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="b4dc2-228">*Puertos del Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="b4dc2-228">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="b4dc2-229">Instrucciones para emparejar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="b4dc2-229">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="b4dc2-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a></span><span class="sxs-lookup"><span data-stu-id="b4dc2-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="b4dc2-231">Gestos compuestos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-231">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="b4dc2-232">Pulsar en el aire</span><span class="sxs-lookup"><span data-stu-id="b4dc2-232">Air tap</span></span>
<span data-ttu-id="b4dc2-233">El gesto de pulsación de aire (y los otros gestos que aparecen a continuación) reacciona solo en una derivación específica.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-233">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="b4dc2-234">Para detectar otras pulsaciones, como menú o agarre, la aplicación debe usar directamente las interacciones de nivel inferior descritas en la sección dos gestos de componentes clave anteriores.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-234">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="b4dc2-235">Mantener pulsado</span><span class="sxs-lookup"><span data-stu-id="b4dc2-235">Tap and hold</span></span>
<span data-ttu-id="b4dc2-236">Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-236">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="b4dc2-237">La combinación de la pulsación de aire y la suspensión permite varias interacciones "hacer clic y arrastrar" más complejas al combinarse con el movimiento de ARM, como la selección de un objeto en lugar de activarlo o de las interacciones secundarias de MouseDown, como mostrar un menú contextual.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-237">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="b4dc2-238">Sin embargo, debe tener cuidado al diseñar para este gesto, ya que los usuarios pueden ser propensos a relajar sus posturas de mano durante cualquier gesto extendido.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-238">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="b4dc2-239">Manipulación</span><span class="sxs-lookup"><span data-stu-id="b4dc2-239">Manipulation</span></span>
<span data-ttu-id="b4dc2-240">Los gestos de manipulación se pueden usar para desplazar, cambiar de tamaño o girar un holograma cuando se desea que el holograma reaccione 1:1 a los movimientos del usuario.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-240">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="b4dc2-241">Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-241">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="b4dc2-242">El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-242">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="b4dc2-243">Una vez que se inicia la acción de pulsar y mantener, cualquier manipulación de objetos se controla a través de los movimientos manuales, lo que libera al usuario para que mire mientras manipula.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-243">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="b4dc2-244">Navegación</span><span class="sxs-lookup"><span data-stu-id="b4dc2-244">Navigation</span></span>
<span data-ttu-id="b4dc2-245">Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-245">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="b4dc2-246">Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-246">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="b4dc2-247">Puede desplace la mano a lo largo del eje X, Y o Z de un valor de-1 a 1, siendo 0 el punto inicial.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-247">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="b4dc2-248">La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-248">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="b4dc2-249">La navegación con raíles se refiere a la capacidad de reconocer movimientos en cierto eje hasta que se alcanza un umbral determinado en dicho eje.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-249">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="b4dc2-250">Esto solo es útil cuando el desarrollador habilita el movimiento en más de un eje en una aplicación, por ejemplo, si una aplicación está configurada para reconocer los gestos de navegación por el eje X, Y, pero también especifica el eje X con raíles.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-250">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="b4dc2-251">En este caso, el sistema reconocerá los movimientos de mano en el eje X siempre y cuando permanezcan dentro de un raíl imaginario (guía) en el eje X, si el movimiento de mano también se produce en el eje Y.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-251">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="b4dc2-252">En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-252">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="b4dc2-253">Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-253">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="b4dc2-254">Los usuarios pueden seleccionar cuál de estas acciones tienen lugar alternando entre las herramientas de la barra situada encima de la aplicación, ya sea seleccionando el botón o diciendo ' <herramienta de desplazamiento/arrastrar/zoom> '.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-254">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="b4dc2-255">Más información sobre los gestos compuestos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-255">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="b4dc2-256">Reconocedores de gestos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-256">Gesture recognizers</span></span>

<span data-ttu-id="b4dc2-257">Una ventaja de usar el reconocimiento de gestos es que puede configurar un reconocedor de gestos solo para los gestos que el holograma de destino actual puede aceptar.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-257">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="b4dc2-258">La plataforma solo realiza la desambiguación según sea necesario para distinguir los gestos admitidos en particular.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-258">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="b4dc2-259">De esta manera, un holograma que solo admita Air TAP puede aceptar cualquier período de tiempo entre la prensa y la versión, mientras que un holograma que admita tanto tap como Hold puede promover la derivación a una retención después del umbral de tiempo de espera.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-259">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="b4dc2-260">Reconocimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="b4dc2-260">Hand recognition</span></span>
<span data-ttu-id="b4dc2-261">HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-261">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="b4dc2-262">HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo).</span><span class="sxs-lookup"><span data-stu-id="b4dc2-262">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="b4dc2-263">Cuando las manos están en otras, HoloLens las omite.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-263">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="b4dc2-264">Para cada mano que HoloLens detecta, puede tener acceso a su posición sin orientación y su estado presionado.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-264">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="b4dc2-265">A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-265">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="b4dc2-266">Marco gestual</span><span class="sxs-lookup"><span data-stu-id="b4dc2-266">Gesture frame</span></span>
<span data-ttu-id="b4dc2-267">En el caso de los gestos en HoloLens, la mano debe estar dentro de un marco de gestos, en un intervalo en el que las cámaras de detección de gestos pueden ver adecuadamente, de la nariz a la waist y entre los hombros.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-267">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="b4dc2-268">Los usuarios deben estar entrenados en esta área de reconocimiento tanto para el éxito de la acción como para su comodidad.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-268">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="b4dc2-269">En principio, muchos usuarios suponen que el marco de gestos debe estar dentro de la vista a través de HoloLens y mantener sus ramas de forma no cómoda de interactuar.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-269">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="b4dc2-270">Al usar el clic de HoloLens, no es necesario que las manos estén dentro del marco de gestos.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-270">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="b4dc2-271">Para los gestos continuos en concreto, hay algún riesgo de que los usuarios muevan sus manos fuera del marco de gestos mientras están en movimiento intermedio al mover un objeto holográfica, por ejemplo, y perder el resultado previsto.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-271">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="b4dc2-272">Hay tres cosas que hay que tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="b4dc2-272">There are three things that you should consider:</span></span>

- <span data-ttu-id="b4dc2-273">Educación del usuario sobre la existencia y los límites aproximados del marco de gestos.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-273">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="b4dc2-274">Esto se enseña durante la instalación de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-274">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="b4dc2-275">Notificar a los usuarios cuando sus gestos están próximos o rompiendo los límites del marco de gestos dentro de una aplicación hasta el grado en que un movimiento perdido conduce a resultados no deseados.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-275">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="b4dc2-276">La investigación ha mostrado las cualidades clave de este sistema de notificación.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-276">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="b4dc2-277">El shell de HoloLens proporciona un buen ejemplo de este tipo de notificación: visual, en el cursor central, que indica la dirección en la que se está llevando a cabo el cruce de límites.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-277">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="b4dc2-278">Se deben minimizar las consecuencias de traspasar los límites del marco gestual.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-278">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="b4dc2-279">En general, esto significa que el resultado de un gesto debe detenerse en el límite y no revertirse.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-279">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="b4dc2-280">Por ejemplo, si un usuario mueve algún objeto holográfica a través de una habitación, el movimiento debe detenerse cuando se infrinja el marco de gestos y no se devuelva al punto inicial.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-280">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="b4dc2-281">El usuario puede experimentar cierta frustración, pero es posible que comprenda más rápidamente los límites y no tenga que reiniciar todas las acciones previstas en cada momento.</span><span class="sxs-lookup"><span data-stu-id="b4dc2-281">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="b4dc2-282">Consulte también</span><span class="sxs-lookup"><span data-stu-id="b4dc2-282">See also</span></span>
* [<span data-ttu-id="b4dc2-283">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-283">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="b4dc2-284">Seguimiento de los ojos en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4dc2-284">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="b4dc2-285">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="b4dc2-285">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="b4dc2-286">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="b4dc2-286">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="b4dc2-287">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="b4dc2-287">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="b4dc2-288">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="b4dc2-288">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="b4dc2-289">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="b4dc2-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="b4dc2-290">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="b4dc2-290">Voice input</span></span>](voice-input.md)