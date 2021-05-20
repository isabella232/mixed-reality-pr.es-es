---
title: Mirada y confirmación
description: Obtenga información sobre el modelo de entrada de mirada y confirmación, incluidos dos tipos de mirada (mirada con la cabeza y mirada con los ojos) y varios tipos de confirmación.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality, mirada, objetivo de mirada, interacción, diseño, seguimiento de los ojos, seguimiento de la cabeza, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db394ab4aded7136550e8e88eb3d66e06f3eeb92
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196570"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="1a5fe-104">Mirada y confirmación</span><span class="sxs-lookup"><span data-stu-id="1a5fe-104">Gaze and commit</span></span>

<span data-ttu-id="1a5fe-105">_La mirada y confirmación_ es un modelo de entrada fundamental que está estrechamente relacionado con la forma en que interactuamos con nuestros equipos mediante el mouse: haga clic _& clic en_.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="1a5fe-106">En esta página, se presentan dos tipos de entrada de mirada (mirada con la cabeza y los ojos) y diferentes tipos de acciones de confirmación.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="1a5fe-107">_La mirada y la confirmación_ se consideran un modelo de entrada lejana con manipulación indirecta.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="1a5fe-108">Se usa mejor para interactuar con contenido holográfico que está fuera de alcance.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="1a5fe-109">Los cascos de realidad mixta pueden usar la posición y la orientación de la cabeza del usuario para determinar el vector de dirección de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="1a5fe-110">Piense en la mirada como un rayo que apunta directamente directamente entre los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="1a5fe-111">Esto es una aproximación bastante general de dónde mira el usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="1a5fe-112">La aplicación puede formar una intersección con objetos virtuales o reales y dibujar un cursor en esa ubicación para que el usuario sepa a qué se dirigirá.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="1a5fe-113">Además de la mirada con la cabeza, algunos cascos de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento ocular que producen un vector de mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="1a5fe-114">Esto proporciona una medida específica de adónde mira el usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="1a5fe-115">En ambos casos, la mirada representa una señal importante para la intención del usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="1a5fe-116">Entre mejor el sistema pueda interpretar y predecir las acciones previstas del usuario, mayor será la satisfacción y el rendimiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="1a5fe-117">A continuación se muestran algunos ejemplos de cómo usted como desarrollador de realidad mixta puede beneficiarse de la mirada con la cabeza o los ojos:</span><span class="sxs-lookup"><span data-stu-id="1a5fe-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="1a5fe-118">La aplicación puede formar intersección con la mirada con los hologramas de la escena para determinar dónde está la atención del usuario (más precisa con la mirada con los ojos).</span><span class="sxs-lookup"><span data-stu-id="1a5fe-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="1a5fe-119">La aplicación puede canalizar gestos y presiones del controlador en función de la mirada del usuario, lo que permite al usuario seleccionar, activar, agarrar, desplazarse o interactuar sin problemas con sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="1a5fe-120">La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real mediante la intersección de su rayo de mirada con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="1a5fe-121">La aplicación puede saber cuándo el usuario no busca en la dirección de un objeto importante, lo que puede llevar a la aplicación a proporcionar indicaciones visuales y de audio para dirigirse hacia ese objeto.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="1a5fe-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1a5fe-123"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="1a5fe-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="1a5fe-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1a5fe-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1a5fe-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1a5fe-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1a5fe-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="1a5fe-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1a5fe-127">Mirada con la cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="1a5fe-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="1a5fe-128">✔️ Recomendado</span><span class="sxs-lookup"><span data-stu-id="1a5fe-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="1a5fe-129">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="1a5fe-130">➕ Opción alternativa</span><span class="sxs-lookup"><span data-stu-id="1a5fe-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="1a5fe-131">Mirada con los ojos y confirmación</span><span class="sxs-lookup"><span data-stu-id="1a5fe-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="1a5fe-132">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="1a5fe-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="1a5fe-133">✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="1a5fe-134">❌ No disponible</span><span class="sxs-lookup"><span data-stu-id="1a5fe-134">❌ Not available</span></span></td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="1a5fe-135">Demostración de conceptos de diseño de seguimiento de la cabeza y los ojos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-135">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="1a5fe-136">Si quiere ver los conceptos de diseño de Head and Eye Tracking en acción, consulte la demostración de vídeo Diseño de **hologramas:** seguimiento de la cabeza y seguimiento de los ojos a continuación.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-136">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="1a5fe-137">Cuando haya terminado, continúe para obtener un análisis más detallado de temas específicos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-137">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="1a5fe-138">*Este vídeo se tomó de la aplicación "Diseño de hologramas" HoloLens 2 aplicación. Descargue y disfrute de la experiencia [completa aquí.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-138">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="gaze"></a><span data-ttu-id="1a5fe-139">Mirar</span><span class="sxs-lookup"><span data-stu-id="1a5fe-139">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="1a5fe-140">¿Mirada con los ojos o con la cabeza?</span><span class="sxs-lookup"><span data-stu-id="1a5fe-140">Eye- or head-gaze?</span></span>
<span data-ttu-id="1a5fe-141">Hay varias consideraciones cuando se enfrenta a la pregunta de si debe usar el modelo de entrada "mirada con los ojos y confirmación" o "mirada con la cabeza y confirmación".</span><span class="sxs-lookup"><span data-stu-id="1a5fe-141">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="1a5fe-142">Si está desarrollando para un casco envolvente o para HoloLens (1.ª generación), la elección es sencilla: mirada con la cabeza y confirmación.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-142">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="1a5fe-143">Si va a desarrollar para HoloLens 2, la elección se vuelve un poco más difícil.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-143">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="1a5fe-144">Es importante comprender las ventajas y los desafíos que se incluyen con cada uno de ellos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-144">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="1a5fe-145">Hemos compilado algunas ventajas y desventajas generales en la tabla siguiente para contrastar el objetivo de la cabeza frente a la mirada con los ojos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-145">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="1a5fe-146">Esto está lejos de completarse y se recomienda obtener más información sobre el objetivo de la mirada con los ojos en la realidad mixta aquí:</span><span class="sxs-lookup"><span data-stu-id="1a5fe-146">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="1a5fe-147">[Seguimiento de los HoloLens 2:](eye-tracking.md)introducción general de nuestra nueva funcionalidad de seguimiento de los HoloLens 2 incluir algunas instrucciones para desarrolladores.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-147">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="1a5fe-148">[Interacción con la mirada con los](eye-gaze-interaction.md)ojos: consideraciones y recomendaciones de diseño al planear el uso del seguimiento de los ojos como entrada.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-148">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="1a5fe-149"><strong>Objetivo de la mirada con los ojos</strong></span><span class="sxs-lookup"><span data-stu-id="1a5fe-149"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="1a5fe-150"><strong>Establecer el destino de la mirada con la cabeza</strong></span><span class="sxs-lookup"><span data-stu-id="1a5fe-150"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-151">¡rápido!</span><span class="sxs-lookup"><span data-stu-id="1a5fe-151">Fast!</span></span></td>
        <td><span data-ttu-id="1a5fe-152">más despacio</span><span class="sxs-lookup"><span data-stu-id="1a5fe-152">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-153">Poco esfuerzo (casi todos los movimientos corporales necesarios)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-153">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="1a5fe-154">Puede ser fatiguing: posibles molestias (por ejemplo, presión de cuello)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-154">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-155">No requiere un cursor, pero se recomiendan comentarios sutiles</span><span class="sxs-lookup"><span data-stu-id="1a5fe-155">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="1a5fe-156">Requiere mostrar un cursor</span><span class="sxs-lookup"><span data-stu-id="1a5fe-156">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-157">Sin movimientos de los ojos suavizados; por ejemplo, no es bueno para dibujar</span><span class="sxs-lookup"><span data-stu-id="1a5fe-157">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="1a5fe-158">Más controlado y explícito</span><span class="sxs-lookup"><span data-stu-id="1a5fe-158">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-159">Difícil para destinos pequeños (por ejemplo, botones pequeños o vínculos web)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-159">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="1a5fe-160">¡fidedigno!</span><span class="sxs-lookup"><span data-stu-id="1a5fe-160">Reliable!</span></span> <span data-ttu-id="1a5fe-161">¡Excelente reserva!</span><span class="sxs-lookup"><span data-stu-id="1a5fe-161">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1a5fe-162">...</span><span class="sxs-lookup"><span data-stu-id="1a5fe-162">...</span></span></td>
        <td><span data-ttu-id="1a5fe-163">...</span><span class="sxs-lookup"><span data-stu-id="1a5fe-163">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="1a5fe-164">Tanto si usa la mirada con la cabeza como la mirada con los ojos para el modelo de entrada de mirada y confirmación, cada uno incluye distintos conjuntos de restricciones de diseño.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-164">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="1a5fe-165">Se tratan por separado en los [artículos de](gaze-and-commit-eyes.md) mirada con los ojos y confirmación y mirada con la cabeza [y confirmación.](gaze-and-commit-head.md)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-165">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="1a5fe-166">Cursor</span><span class="sxs-lookup"><span data-stu-id="1a5fe-166">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1a5fe-167">Para la mirada con la cabeza, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) u otra indicación auditiva o visual para proporcionar al usuario confianza en lo que están a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-167">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="1a5fe-168">Normalmente, este cursor se coloca en el mundo donde su rayo de mirada con la cabeza forma primero una intersección con un objeto, que puede ser un holograma o una superficie real.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-168">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="1a5fe-169">En el caso de  la mirada con los ojos, por lo general se recomienda no mostrar un cursor, ya que esto puede llegar a distraer e incoerablemente al usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-169">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="1a5fe-170">En su lugar, resalte de forma sutil los destinos visuales o use un cursor de ojo atractivo para proporcionar confianza sobre lo que el usuario está a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-170">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="1a5fe-171">Para obtener más información, consulte nuestra guía de diseño para [obtener información](eye-tracking.md) detallada sobre HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-171">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="1a5fe-172">![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-172">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="1a5fe-173">*Imagen: un cursor visual de ejemplo para mostrar la mirada*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-173">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="1a5fe-174">Commit</span><span class="sxs-lookup"><span data-stu-id="1a5fe-174">Commit</span></span>
<span data-ttu-id="1a5fe-175">Después de hablar  sobre diferentes maneras de mirar un destino, vamos a hablar un poco más sobre la parte de confirmación en la mirada _y confirmar_. </span><span class="sxs-lookup"><span data-stu-id="1a5fe-175">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="1a5fe-176">Después de tener como destino un objeto o elemento de interfaz de usuario, el usuario puede interactuar o hacer clic en él mediante una entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-176">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="1a5fe-177">Esto se conoce como el paso de confirmación del modelo de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-177">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="1a5fe-178">Se admiten los siguientes métodos de confirmación:</span><span class="sxs-lookup"><span data-stu-id="1a5fe-178">The following commit methods are supported:</span></span>
- <span data-ttu-id="1a5fe-179">Gesto de pulsar en el aire (es decir, elevar la mano delante de usted y reunir el dedo índice y el dedo)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-179">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="1a5fe-180">Diga _"seleccionar"_ o uno de los comandos de voz de destino.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-180">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="1a5fe-181">Presionar un solo botón en un [clicker de HoloLens](/hololens/hololens1-clicker)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-181">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="1a5fe-182">Presione el botón "A" en un gamepad de Xbox.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-182">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="1a5fe-183">Presione el botón "A" en un controlador adaptable de Xbox.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-183">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="1a5fe-184">Gesto de mirada y pulsación en el aire</span><span class="sxs-lookup"><span data-stu-id="1a5fe-184">Gaze and air tap gesture</span></span>
<span data-ttu-id="1a5fe-185">Pulsar en el aire es hacer el gesto de pulsar con la mano vertical.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-185">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="1a5fe-186">Para usar una pulsación en el aire, coloque el dedo índice en la posición lista, luego práctese con el dedo y vuelva a subir el dedo del índice hasta liberarlo.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-186">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="1a5fe-187">En HoloLens (1.ª generación), el toque de aire es la entrada secundaria más común.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-187">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="1a5fe-188">![Dedo en la posición lista](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-188">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="1a5fe-189">**Dedo en la posición lista**</span><span class="sxs-lookup"><span data-stu-id="1a5fe-189">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1a5fe-190">![Presione el dedo hacia abajo para pulsar o hacer clic en](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-190">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="1a5fe-191&quot;>**Presione el dedo hacia abajo para pulsar o hacer clic en**</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-191&quot;>**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id=&quot;1a5fe-192&quot;>La pulsación en el aire también está disponible HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-192&quot;>Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id=&quot;1a5fe-193&quot;>Se ha relajado con la versión original.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-193&quot;>It has been relaxed from the original version.</span></span> <span data-ttu-id=&quot;1a5fe-194&quot;>Ahora se admiten casi todos los tipos de pesquete, siempre y cuando la mano esté vertical y deteniendo.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-194&quot;>Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id=&quot;1a5fe-195&quot;>Esto facilita a los usuarios aprender y usar el gesto.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-195&quot;>This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id=&quot;1a5fe-196&quot;>Esta nueva pulsación en el aire reemplaza la anterior a través de la misma API, por lo que las aplicaciones existentes tendrán el nuevo comportamiento automáticamente después de volver a compilar HoloLens 2.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-196&quot;>This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name=&quot;gaze-and-select-voice-command&quot;></a><span data-ttu-id=&quot;1a5fe-197&quot;>Comando de voz &quot;Seleccionar&quot; y mirada</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-197&quot;>Gaze and &quot;Select&quot; voice command</span></span>
<span data-ttu-id=&quot;1a5fe-198&quot;>Los comandos de voz son uno de los métodos de interacción principales de la realidad mixta.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-198&quot;>Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id=&quot;1a5fe-199&quot;>Proporciona un eficaz mecanismo de manos libres para controlar el sistema.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-199&quot;>It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id=&quot;1a5fe-200&quot;>Hay diferentes tipos de modelos de interacción de voz:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-200&quot;>There are different types of voice interaction models:</span></span>

- <span data-ttu-id=&quot;1a5fe-201&quot;>El comando genérico &quot;Select&quot; que usa una acción de clic o confirmación como entrada secundaria.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;1a5fe-201&quot;>The generic &quot;Select&quot; command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id=&quot;1a5fe-202&quot;>Los comandos object (por ejemplo, &quot;Close&quot; o &quot;Make it bigger") realizan y confirman una acción como entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-202">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="1a5fe-203">Los comandos globales (por ejemplo, "Ir al inicio") no requieren un destino.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-203">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="1a5fe-204">Las interfaces de usuario de conversación o entidades como Cortana tienen una funcionalidad de lenguaje natural de inteligencia artificial.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-204">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="1a5fe-205">Comandos de voz personalizados</span><span class="sxs-lookup"><span data-stu-id="1a5fe-205">Custom voice commands</span></span>

<span data-ttu-id="1a5fe-206">Para obtener más información sobre los detalles y una lista completa de los comandos de voz disponibles y cómo usarlos, consulte nuestra guía [de comandos de](../out-of-scope/voice-design.md) voz.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-206">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="1a5fe-207">Gaze y HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="1a5fe-207">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1a5fe-208">HoloLens Clicker es el primer dispositivo periférico creado específicamente para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-208">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="1a5fe-209">Se incluye con HoloLens (1.ª generación) Development Edition.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-209">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="1a5fe-210">HoloLens Clicker permite que un usuario haga clic con movimiento mínimo de la mano y se confirme como una entrada secundaria.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-210">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="1a5fe-211">HoloLens Clicker se conecta a HoloLens (1ª generación) o HoloLens 2 mediante Bluetooth de bajo consumo (BTLE).</span><span class="sxs-lookup"><span data-stu-id="1a5fe-211">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="1a5fe-212">Más información e instrucciones para emparejar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="1a5fe-212">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="1a5fe-213">*Imagen: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-213">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="1a5fe-215">Control inalámbrico de Mirada y Xbox</span><span class="sxs-lookup"><span data-stu-id="1a5fe-215">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1a5fe-216">El controlador inalámbrico xbox realiza una acción de clic como entrada secundaria mediante el botón "A".</span><span class="sxs-lookup"><span data-stu-id="1a5fe-216">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="1a5fe-217">El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-217">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="1a5fe-218">Si quieres personalizar el controlador, usa la aplicación Accesorios de Xbox para configurar el controlador inalámbrico xbox.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-218">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="1a5fe-219">Cómo emparejar un controlador de Xbox con el equipo</span><span class="sxs-lookup"><span data-stu-id="1a5fe-219">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="1a5fe-220">*Imagen: Xbox Wireless Controller*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-220">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Controlador inalámbrico de Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="1a5fe-222">Mirada y controlador adaptable de Xbox</span><span class="sxs-lookup"><span data-stu-id="1a5fe-222">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="1a5fe-223">Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el controlador adaptable de Xbox es un centro unificado para dispositivos que ayuda a que la realidad mixta sea más accesible.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-223">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="1a5fe-224">El controlador adaptable de Xbox realiza una acción de clic como entrada secundaria mediante el botón "A".</span><span class="sxs-lookup"><span data-stu-id="1a5fe-224">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="1a5fe-225">El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-225">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="1a5fe-226">Si desea personalizar el controlador, use la aplicación Accesorios de Xbox para configurar el controlador adaptable de Xbox.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-226">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="1a5fe-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-227">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="1a5fe-228">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-228">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="1a5fe-229">Conecte dispositivos externos, como conmutadores, botones, montajes y flechas, para crear una experiencia de controlador personalizada que sea exclusiva de usted.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-229">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="1a5fe-230">Las entradas de botones, de botones y desencadenadores se controlan con dispositivos de asistencia conectados a través de conectores de 3,5 mm y puertos USB.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-230">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="1a5fe-231">![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="1a5fe-231">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="1a5fe-232">*Puertos del Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="1a5fe-232">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="1a5fe-233">Instrucciones para emparejar el dispositivo</span><span class="sxs-lookup"><span data-stu-id="1a5fe-233">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="1a5fe-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a></span><span class="sxs-lookup"><span data-stu-id="1a5fe-234"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="1a5fe-235">Gestos compuestos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-235">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="1a5fe-236">Pulsar en el aire</span><span class="sxs-lookup"><span data-stu-id="1a5fe-236">Air tap</span></span>
<span data-ttu-id="1a5fe-237">El gesto de pulsación de aire (y los demás gestos siguientes) reacciona solo a una pulsación específica.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-237">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="1a5fe-238">Para detectar otras pulsaciones, como Menu o Ctrl, la aplicación debe usar directamente las interacciones de nivel inferior descritas en la sección anterior de los dos gestos de componente clave.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-238">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="1a5fe-239">Mantener pulsado</span><span class="sxs-lookup"><span data-stu-id="1a5fe-239">Tap and hold</span></span>
<span data-ttu-id="1a5fe-240">Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-240">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="1a5fe-241">La combinación de pulsación y retención del aire permite varias interacciones más complejas de "hacer clic y arrastrar" cuando se combina con el movimiento de los brazos, como la selección de un objeto en lugar de activarlo o las interacciones secundarias del mouse, como mostrar un menú contextual.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-241">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="1a5fe-242">Sin embargo, se debe tener cuidado al diseñar para este gesto, ya que los usuarios pueden ser propensos a relajar sus posturas de mano durante cualquier gesto extendido.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-242">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="1a5fe-243">Manipulación</span><span class="sxs-lookup"><span data-stu-id="1a5fe-243">Manipulation</span></span>
<span data-ttu-id="1a5fe-244">Los gestos de manipulación se pueden usar para mover, cambiar el tamaño o girar un holograma cuando quiera que el holograma reaccione 1:1 a los movimientos de las manos del usuario.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-244">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="1a5fe-245">Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-245">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="1a5fe-246">El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-246">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="1a5fe-247">Una vez que se inicia la pulsación y la retención, cualquier manipulación de objetos se controla mediante movimientos de mano, lo que permite al usuario mirar alrededor mientras manipula.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-247">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="1a5fe-248">Navegación</span><span class="sxs-lookup"><span data-stu-id="1a5fe-248">Navigation</span></span>
<span data-ttu-id="1a5fe-249">Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-249">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="1a5fe-250">Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-250">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="1a5fe-251">Puede mover la mano a lo largo del eje X, Y o Z de un valor de -1 a 1, siendo 0 el punto inicial.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-251">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="1a5fe-252">La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-252">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="1a5fe-253">La navegación con raíles hace referencia a la capacidad de reconocer los movimientos en determinado eje hasta que se alcanza un umbral determinado en ese eje.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-253">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="1a5fe-254">Esto solo es útil cuando el desarrollador habilita el movimiento en más de un eje en una aplicación, por ejemplo, si una aplicación está configurada para reconocer gestos de navegación en los ejes X e Y, pero también en el eje X especificado con raíles.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-254">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="1a5fe-255">En este caso, el sistema reconocerá los movimientos de las manos a través del eje X siempre que permanezcan dentro de un raíl imaginario (guía) en el eje X, si también se produce el movimiento de la mano en el eje Y.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-255">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="1a5fe-256">En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-256">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="1a5fe-257">Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-257">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="1a5fe-258">Los usuarios pueden seleccionar cuál de estas acciones se lleva a cabo al alternar entre las herramientas de la barra encima de la aplicación; para ello, seleccione el botón o diga "<Scroll/Drag/Zoom> Tool".</span><span class="sxs-lookup"><span data-stu-id="1a5fe-258">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="1a5fe-259">Más información sobre los gestos compuestos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-259">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="1a5fe-260">Reconocedores de gestos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-260">Gesture recognizers</span></span>

<span data-ttu-id="1a5fe-261">Una ventaja de usar el reconocimiento de gestos es que solo puede configurar un reconocedor de gestos para los gestos que el holograma de destino puede aceptar.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-261">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="1a5fe-262">La plataforma solo realiza la desambiguación según sea necesario para distinguir esos gestos admitidos concretos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-262">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="1a5fe-263">De este modo, un holograma que solo admite el toque de aire puede aceptar cualquier período de tiempo entre presionar y soltar, mientras que un holograma que admita pulsar y mantener pulsado puede promover la pulsación a una retención después del umbral de tiempo de retención.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-263">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="1a5fe-264">Reconocimiento de la mano</span><span class="sxs-lookup"><span data-stu-id="1a5fe-264">Hand recognition</span></span>
<span data-ttu-id="1a5fe-265">HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-265">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="1a5fe-266">HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo).</span><span class="sxs-lookup"><span data-stu-id="1a5fe-266">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="1a5fe-267">Cuando las manos están en otras poses, HoloLens las omite.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-267">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="1a5fe-268">Por cada mano que HoloLens detecte, puede acceder a su posición sin orientación y su estado presionado.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-268">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="1a5fe-269">A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-269">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="1a5fe-270">Marco gestual</span><span class="sxs-lookup"><span data-stu-id="1a5fe-270">Gesture frame</span></span>
<span data-ttu-id="1a5fe-271">En el caso de los gestos en HoloLens, la mano debe estar dentro de un marco de gestos, en un intervalo que las cámaras de detección de gestos puedan ver adecuadamente, desde la sensibilidad hasta la sensibilidad y entre las manos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-271">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="1a5fe-272">Los usuarios deben estar entrenados en esta área de reconocimiento tanto para el éxito de la acción como para su propia comodidad.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-272">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="1a5fe-273">Inicialmente, muchos usuarios asumirán que el marco de gestos debe estar dentro de su vista a través de HoloLens y mantener los manos presionados para interactuar.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-273">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="1a5fe-274">Al usar HoloLens Clicker, no es necesario que las manos se encuentran dentro del marco de gestos.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-274">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="1a5fe-275">En concreto, en el caso de los gestos continuos, hay cierto riesgo de que los usuarios muevan las manos fuera del marco de gestos mientras están en medio del gesto al mover un objeto holográfico, por ejemplo, y perder el resultado previsto.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-275">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="1a5fe-276">Hay tres cosas que hay que tener en cuenta:</span><span class="sxs-lookup"><span data-stu-id="1a5fe-276">There are three things that you should consider:</span></span>

- <span data-ttu-id="1a5fe-277">Educación del usuario sobre la existencia del marco de gestos y los límites aproximados.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-277">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="1a5fe-278">Esto se enseña durante la configuración de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-278">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="1a5fe-279">Notificación a los usuarios cuando sus gestos se acercan o traspasan los límites del marco de gestos dentro de una aplicación hasta el punto de que un gesto perdido conduce a resultados no deseados.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-279">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="1a5fe-280">La investigación ha mostrado las principales calidades de este sistema de notificación.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-280">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="1a5fe-281">El shell de HoloLens proporciona un buen ejemplo de este tipo de notificación: visual, en el cursor central, que indica la dirección en la que se realiza el cruce de límites.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-281">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="1a5fe-282">Se deben minimizar las consecuencias de traspasar los límites del marco gestual.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-282">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="1a5fe-283">En general, esto significa que el resultado de un gesto debe detenerse en el límite y no invertirse.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-283">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="1a5fe-284">Por ejemplo, si un usuario mueve algún objeto holográfico a través de una sala, el movimiento debe detenerse cuando se infringe el marco de gestos y no se devuelve al punto inicial.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-284">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="1a5fe-285">Es posible que el usuario experimente cierta frustración, pero podría comprender más rápidamente los límites y no tener que reiniciar todas las acciones previstas cada vez.</span><span class="sxs-lookup"><span data-stu-id="1a5fe-285">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="1a5fe-286">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1a5fe-286">See also</span></span>
* [<span data-ttu-id="1a5fe-287">Interacción basada en los ojos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-287">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="1a5fe-288">Seguimiento de los ojos en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1a5fe-288">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="1a5fe-289">Mirada y permanencia</span><span class="sxs-lookup"><span data-stu-id="1a5fe-289">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="1a5fe-290">Manos: manipulación directa</span><span class="sxs-lookup"><span data-stu-id="1a5fe-290">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1a5fe-291">Manos: gestos</span><span class="sxs-lookup"><span data-stu-id="1a5fe-291">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="1a5fe-292">Manos: apuntar y confirmar</span><span class="sxs-lookup"><span data-stu-id="1a5fe-292">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="1a5fe-293">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="1a5fe-293">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1a5fe-294">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="1a5fe-294">Voice input</span></span>](voice-input.md)