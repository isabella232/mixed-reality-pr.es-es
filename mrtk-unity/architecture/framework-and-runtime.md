---
title: Marco de trabajo y tiempo de ejecución
description: Información relacionada con el marco de trabajo y el entorno de ejecución en MRTK.
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: a44e5f32cda2803091e27ae1a2c30a1976385a2f
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121613"
---
# <a name="framework-and-runtime"></a><span data-ttu-id="1cf3f-104">Marco de trabajo y tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="1cf3f-104">Framework and runtime</span></span>

## <a name="changes-to-the-scene"></a><span data-ttu-id="1cf3f-105">Cambios en la escena</span><span class="sxs-lookup"><span data-stu-id="1cf3f-105">Changes to the scene</span></span>

<span data-ttu-id="1cf3f-106">Para usar el kit de herramientas, una instancia del script MixedRealityToolkit debe estar en la escena.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-106">To use the toolkit an instance of the MixedRealityToolkit script must be in your scene.</span></span>
<span data-ttu-id="1cf3f-107">Para agregar uno, use la opción de menú: Mixed Reality Toolkit -> Agregar a la escena y configurar.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-107">To add one use the menu option: Mixed Reality Toolkit -> Add to Scene and Configure.</span></span> <span data-ttu-id="1cf3f-108">Esta instancia es responsable de registrar, actualizar y destruir servicios.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-108">This instance is responsible for registering, updating and tearing down services.</span></span> <span data-ttu-id="1cf3f-109">También es donde se elige el perfil de configuración.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-109">It's also where your configuration profile is chosen.</span></span>

<span data-ttu-id="1cf3f-110">Además de agregar el GameObject de MRTK a la escena, la opción de menú también hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1cf3f-110">Apart from adding the MRTK GameObject to the scene the menu option will also:</span></span>

- <span data-ttu-id="1cf3f-111">Agregue MixedRealityPlayspace, que usan muchos otros componentes de MRTK para razonar sobre las transformaciones de espacio mundial y local.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-111">Add the MixedRealityPlayspace, which is used by many other MRTK components to reason over world and local space transformations.</span></span>
- <span data-ttu-id="1cf3f-112">Mueva la cámara principal como elemento secundario de MixedRealityPlayspace (y agregue también algunos scripts relacionados con la entrada y la mirada a la cámara principal, lo que ayuda a encender UnityUI y a la funcionalidad de entrada relacionada con la mirada).</span><span class="sxs-lookup"><span data-stu-id="1cf3f-112">Move the main Camera as a child of the MixedRealityPlayspace (and also adding some input and gaze related scripts to the main Camera, which help power UnityUI and gaze related input functionality).</span></span>

## <a name="mixedrealitytoolkit-object-and-runtime"></a><span data-ttu-id="1cf3f-113">Objeto y tiempo de ejecución de MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1cf3f-113">MixedRealityToolkit object and runtime</span></span>

<span data-ttu-id="1cf3f-114">MRTK tiene varios servicios principales.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-114">The MRTK has several core services.</span></span> <span data-ttu-id="1cf3f-115">Algunas se coordinan entre sí; otros son independientes.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-115">Some coordinate with one another; others are independent.</span></span>
<span data-ttu-id="1cf3f-116">Todos comparten el mismo ciclo de vida (inicio, registro, actualización y desmontaje), y este ciclo de vida se diferencia del ciclo de vida monobehaviour de Unity.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-116">All share the same life cycle - startup, registration, update and teardown - and this life cycle stands apart from Unity's MonoBehaviour life cycle.</span></span> <span data-ttu-id="1cf3f-117">En [esta publicación mediana](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) se explican algunos de los antecedentes y la motivación que hay detrás de este enfoque.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-117">This [medium post](https://medium.com/@stephen_hodgson/the-mixed-reality-framework-6fdb5c11feb2) explains some of the background and motivation behind this approach.</span></span> <span data-ttu-id="1cf3f-118">MRTK tiene un único objeto que administra la vida y el tiempo de ejecución de sus servicios.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-118">MRTK has a single object that manages life and runtime of its services.</span></span>

<span data-ttu-id="1cf3f-119">Esta entidad garantiza que:</span><span class="sxs-lookup"><span data-stu-id="1cf3f-119">This entity ensures that:</span></span>

- <span data-ttu-id="1cf3f-120">cuando se inicia el juego, la detección y la inicialización de servicios se produce en un orden predefinido.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-120">when the game starts, discovery and initialization of services happens in a pre-defined order.</span></span>
- <span data-ttu-id="1cf3f-121">proporciona un mecanismo para que los servicios se registren ellos mismos (es decir, "soporte este servicio") y para que otros llamadores obtengan una retención de esos servicios.</span><span class="sxs-lookup"><span data-stu-id="1cf3f-121">it provides a mechanism for services to register themselves (i.e. “I support this service!”) and for other callers to get a hold of those services.</span></span>
- <span data-ttu-id="1cf3f-122">proporciona las llamadas Update()/LateUpdate() y las reenvía a los distintos servicios (es decir, a través de UpdateAllServices/LateUpdateAllServices).</span><span class="sxs-lookup"><span data-stu-id="1cf3f-122">it provides the Update()/LateUpdate() calls and forwards them onto the various services (i.e. via UpdateAllServices/LateUpdateAllServices).</span></span>
