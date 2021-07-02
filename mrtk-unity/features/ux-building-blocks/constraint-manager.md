---
title: Administrador de restricciones
description: Información general sobre el Administrador de restricciones en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177556"
---
# <a name="constraint-manager"></a><span data-ttu-id="d3bdc-104">Administrador de restricciones</span><span class="sxs-lookup"><span data-stu-id="d3bdc-104">Constraint manager</span></span>

<span data-ttu-id="d3bdc-105">El administrador de restricciones permite aplicar un conjunto de componentes de restricción a una transformación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="d3bdc-106">Se pueden tener en cuenta los componentes de tipo asociados al objeto [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) de juego.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="d3bdc-107">De forma predeterminada, el administrador de restricciones recopilará automáticamente todos los componentes [de](#transform-constraints) restricción asociados al objeto de juego y los aplicará a las transformaciones procesadas.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="d3bdc-108">Sin embargo, los usuarios pueden optar por configurar la lista de restricciones aplicadas manualmente y permitir que solo se aplique un subconjunto de restricciones asociadas.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="d3bdc-109">Actualmente, los siguientes elementos de la experiencia de usuario de MRTK admiten el administrador de restricciones:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="d3bdc-110">Control Bounds</span><span class="sxs-lookup"><span data-stu-id="d3bdc-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="d3bdc-111">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="d3bdc-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="d3bdc-112">Propiedades y campos del inspector</span><span class="sxs-lookup"><span data-stu-id="d3bdc-112">Inspector properties and fields</span></span>

<span data-ttu-id="d3bdc-113">El administrador de restricciones se puede operar en dos modos:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="d3bdc-114">Selección de restricciones automáticas</span><span class="sxs-lookup"><span data-stu-id="d3bdc-114">Auto constraint selection</span></span>
- <span data-ttu-id="d3bdc-115">Selección manual de restricciones</span><span class="sxs-lookup"><span data-stu-id="d3bdc-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="d3bdc-116">Selección de restricciones automáticas</span><span class="sxs-lookup"><span data-stu-id="d3bdc-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="d3bdc-117">El modo predeterminado del administrador de restricciones, selección automática de restricciones, proporcionará una lista de todos los componentes de restricción asociados, así como botones y un [botón agregar restricción](#add-constraint-to-game-object). [](#go-to-component)</span><span class="sxs-lookup"><span data-stu-id="d3bdc-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="d3bdc-118">Agregar restricción al objeto de juego</span><span class="sxs-lookup"><span data-stu-id="d3bdc-118">Add constraint to game object</span></span>

<span data-ttu-id="d3bdc-119">Este botón permite agregar un componente de restricción directamente desde el inspector del administrador de restricciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="d3bdc-120">Todos los tipos de restricción de un proyecto deben estar visibles aquí.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="d3bdc-121">Consulte [Restricciones de transformación](#transform-constraints) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="d3bdc-122">Ir al componente</span><span class="sxs-lookup"><span data-stu-id="d3bdc-122">Go to component</span></span>

<span data-ttu-id="d3bdc-123">Todas las restricciones que se encuentran en el objeto se mostrarán aquí con un botón *Ir* al componente.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="d3bdc-124">Este botón hará que el inspector se desplace hasta el componente de restricción seleccionado para que se pueda configurar.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="d3bdc-125">Selección manual de restricciones</span><span class="sxs-lookup"><span data-stu-id="d3bdc-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="d3bdc-126">Si el administrador de restricciones se establece en modo manual, solo las restricciones vinculadas en la lista de restricciones se procesan y se aplican a la transformación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="d3bdc-127">La lista mostrada solo mostrará las restricciones [](#go-to-component) seleccionadas por el usuario, así como los botones u opciones para quitar o agregar entradas.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="d3bdc-128">Al habilitar el modo manual por primera vez, el administrador de restricciones rellenará la lista con todos los componentes disponibles como punto de partida para seleccionar los componentes de restricción asociados.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="d3bdc-129">Quitar entrada</span><span class="sxs-lookup"><span data-stu-id="d3bdc-129">Remove entry</span></span>

<span data-ttu-id="d3bdc-130">Esto quita la entrada de la lista seleccionada manualmente.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="d3bdc-131">Tenga en cuenta que esta opción no quitará el componente de restricción del objeto de juego.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="d3bdc-132">Los componentes de restricción siempre deben quitarse manualmente para asegurarse de que no se rompe accidentalmente ningún otro componente que hace referencia a este componente.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="d3bdc-133">Agregar entrada</span><span class="sxs-lookup"><span data-stu-id="d3bdc-133">Add entry</span></span>

<span data-ttu-id="d3bdc-134">Agregar entrada abrirá una lista desplegable que muestra todos los componentes de restricción disponibles que aún no están en la lista manual.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="d3bdc-135">Al hacer clic en cualquiera de las entradas que el componente agregará a la selección de restricción manual.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="d3bdc-136">Agregar nueva restricción</span><span class="sxs-lookup"><span data-stu-id="d3bdc-136">Add new constraint</span></span>

<span data-ttu-id="d3bdc-137">Esta opción agregará un componente del tipo seleccionado al objeto de juego y agregará el componente de restricción recién creado a la lista de restricciones manual.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="d3bdc-138">Restricciones de transformación</span><span class="sxs-lookup"><span data-stu-id="d3bdc-138">Transform constraints</span></span>

<span data-ttu-id="d3bdc-139">Las restricciones se pueden usar para limitar la manipulación de alguna manera.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="d3bdc-140">Por ejemplo, algunas aplicaciones pueden requerir rotación, pero también requieren que el objeto permanezca vertical.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="d3bdc-141">En este caso, se puede agregar un objeto al objeto y usarse para limitar la rotación a `RotationAxisConstraint` la rotación del eje Y.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="d3bdc-142">MRTK proporciona una serie de restricciones, todas las cuales se describen a continuación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="d3bdc-143">También es posible definir nuevas restricciones y usarlas para crear un comportamiento de manipulación único que pueda ser necesario para algunas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="d3bdc-144">Para ello, cree un script que herede de [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implemente la propiedad `ConstraintType` abstracta y el método `ApplyConstraint` abstracto.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="d3bdc-145">Al agregar una nueva restricción al objeto , debe restringir la manipulación de la manera que se definió.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="d3bdc-146">Esta nueva restricción también debe mostrarse en la lista desplegable de selección [automática](#auto-constraint-selection) del administrador de restricciones o agregar [entrada](#add-entry) en modo manual.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="d3bdc-147">Todas las restricciones proporcionadas por MRTK comparten las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="d3bdc-148">Tipo de mano</span><span class="sxs-lookup"><span data-stu-id="d3bdc-148">Hand Type</span></span>

<span data-ttu-id="d3bdc-149">Especifica si la restricción se usa para una mano, dos manos o ambos tipos de manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="d3bdc-150">Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d3bdc-151">*Con una mano:* la restricción se usará durante la manipulación con una mano si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="d3bdc-152">*Dos manos:* la restricción se usará durante la manipulación con dos manos si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="d3bdc-153">Tipo de proximidad</span><span class="sxs-lookup"><span data-stu-id="d3bdc-153">Proximity Type</span></span>

<span data-ttu-id="d3bdc-154">Especifica si la restricción se usa para los tipos de manipulación cercanos, lejanos o ambos.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="d3bdc-155">Dado que esta propiedad es una marca, se pueden seleccionar ambas opciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="d3bdc-156">*Near*: la restricción se usará durante la manipulación próxima si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="d3bdc-157">*Far:* la restricción se usará durante la manipulación lejana si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="d3bdc-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="d3bdc-159">Cuando esta restricción se adjunta a un objeto, la rotación se limitará para que el objeto siempre se enfrentará al usuario.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="d3bdc-160">Esto es útil para pizarras o paneles.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-160">This is useful for slates or panels.</span></span> <span data-ttu-id="d3bdc-161">Las propiedades de `FaceUserConstraint` son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="d3bdc-162">Distancia de la cara</span><span class="sxs-lookup"><span data-stu-id="d3bdc-162">Face away</span></span>

<span data-ttu-id="d3bdc-163">El objeto se enfrenta al usuario si es true.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="d3bdc-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="d3bdc-165">Esta restricción corrige la distancia entre el objeto manipulado y otra transformación de objeto al iniciar la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="d3bdc-166">Esto es útil para comportamientos como corregir la distancia desde el objeto manipulado a la transformación principal.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="d3bdc-167">Las propiedades de `FixedDistanceConstraint` son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="d3bdc-168">Transformación de restricciones</span><span class="sxs-lookup"><span data-stu-id="d3bdc-168">Constraint transform</span></span>

<span data-ttu-id="d3bdc-169">Esta es la otra transformación a la que el objeto manipulado tendrá una distancia fija.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="d3bdc-170">El valor predeterminado es la transformación de la cámara.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="d3bdc-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="d3bdc-172">Esta restricción corrige la rotación relativa entre el usuario y el objeto manipulado mientras se manipula.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="d3bdc-173">Esto es útil para pizarras o paneles, ya que garantiza que el objeto manipulado siempre muestra la misma cara al usuario que al principio de la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="d3bdc-174">no `FixedRotationToUserConstraint` tiene ninguna propiedad única.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="d3bdc-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="d3bdc-176">Esta restricción corrige la rotación global del objeto manipulado mientras se manipula.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="d3bdc-177">Esto puede ser útil en casos en los que no se debe realizar ninguna rotación mediante la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="d3bdc-178">no `FixedRotationToWorldConstraint` tiene ninguna propiedad única:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="d3bdc-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="d3bdc-180">Cuando esta restricción se adjunta a un objeto, independientemente de lo lejos que esté el objeto del usuario, mantendrá el mismo tamaño aparente para el usuario (es decir, ocupará la misma proporción del campo de vista del usuario).</span><span class="sxs-lookup"><span data-stu-id="d3bdc-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="d3bdc-181">Esto se puede usar para asegurarse de que una pizarra o un panel de texto permanece legible durante la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="d3bdc-182">no `MaintainApparentSizeConstraint` tiene ninguna propiedad única:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="d3bdc-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="d3bdc-184">Esta restricción se puede usar para corregir los ejes en los que se puede mover un objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="d3bdc-185">Esto puede ser útil para manipular objetos sobre la superficie de un plano o a lo largo de una línea.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="d3bdc-186">Las propiedades de `MoveAxisConstraint` son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="d3bdc-187">Restricción del movimiento</span><span class="sxs-lookup"><span data-stu-id="d3bdc-187">Constraint on movement</span></span>

<span data-ttu-id="d3bdc-188">Especifica los ejes en los que se va a evitar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="d3bdc-189">De forma predeterminada, estos ejes serán globales en lugar de locales, pero esto se puede cambiar a continuación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="d3bdc-190">Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="d3bdc-191">*Eje X:* el movimiento a lo largo del eje X está restringido si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="d3bdc-192">*Eje Y:* el movimiento a lo largo del eje Y está restringido si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="d3bdc-193">*Eje Z:* el movimiento a lo largo del eje Z está restringido si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="d3bdc-194">Uso del espacio local para la restricción</span><span class="sxs-lookup"><span data-stu-id="d3bdc-194">Use local space for constraint</span></span>

<span data-ttu-id="d3bdc-195">Restringirá los ejes de transformación local del objeto manipulado si es true.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="d3bdc-196">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="d3bdc-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="d3bdc-198">Esta restricción se puede usar para corregir los ejes sobre los que se puede girar un objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="d3bdc-199">Esto puede ser útil para mantener un objeto manipulado verticalmente, pero seguir permitiendo rotaciones del eje Y, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="d3bdc-200">Las propiedades de `RotationAxisConstraint` son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="d3bdc-201">Restricción en la rotación</span><span class="sxs-lookup"><span data-stu-id="d3bdc-201">Constraint on rotation</span></span>

<span data-ttu-id="d3bdc-202">Especifica los ejes sobre los que se va a evitar la rotación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="d3bdc-203">De forma predeterminada, estos ejes serán globales en lugar de locales, pero esto se puede cambiar a continuación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="d3bdc-204">Dado que esta propiedad es una marca, se puede seleccionar cualquier número de opciones.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="d3bdc-205">*Eje Y:* la rotación sobre el eje Y está restringida si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="d3bdc-206">*Eje Z:* la rotación sobre el eje Z está restringida si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="d3bdc-207">*Eje X:* la rotación sobre el eje X está restringida si se selecciona.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="d3bdc-208">Uso del espacio local para la restricción</span><span class="sxs-lookup"><span data-stu-id="d3bdc-208">Use local space for constraint</span></span>

<span data-ttu-id="d3bdc-209">Restringirá los ejes de transformación local del objeto manipulado si es true.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="d3bdc-210">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="d3bdc-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="d3bdc-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="d3bdc-212">Esta restricción permite establecer valores mínimos y máximos para la escala del objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="d3bdc-213">Esto es útil para evitar que los usuarios e escalar un objeto demasiado pequeño o demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="d3bdc-214">Las propiedades de `MinMaxScaleConstraint` son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="d3bdc-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="d3bdc-215">Escala mínima</span><span class="sxs-lookup"><span data-stu-id="d3bdc-215">Scale minimum</span></span>

<span data-ttu-id="d3bdc-216">Valor de escala mínimo durante la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="d3bdc-217">Escalado máximo</span><span class="sxs-lookup"><span data-stu-id="d3bdc-217">Scale maximum</span></span>

<span data-ttu-id="d3bdc-218">Valor de escala máximo durante la manipulación.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="d3bdc-219">En relación con el estado inicial</span><span class="sxs-lookup"><span data-stu-id="d3bdc-219">Relative to initial state</span></span>

<span data-ttu-id="d3bdc-220">Si es true, los valores anteriores se interpretarán como relativos a la escala inicial de los objetos.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="d3bdc-221">De lo contrario, se interpretarán como valores de escala absolutos.</span><span class="sxs-lookup"><span data-stu-id="d3bdc-221">Otherwise they will be interpreted as absolute scale values.</span></span>
