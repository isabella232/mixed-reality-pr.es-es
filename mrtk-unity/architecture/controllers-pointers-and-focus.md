---
title: Controladores, punteros y foco
description: Interactuar con controladores, punteros y foco.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, punteros, controladores
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121623"
---
# <a name="controllers-pointers-and-focus"></a>Controladores, punteros y foco

Los controladores, los punteros y el foco son conceptos de nivel superior que se basa en la base establecida por el sistema de entrada principal. Juntos, proporcionan una gran parte del mecanismo para interactuar con los objetos de la escena.

## <a name="controllers"></a>Controladores

Los controladores son representaciones de un controlador físico (6 grados de libertad, mano articulada, etc.). Los administradores de dispositivos los crean y son responsables de comunicarse con el sistema subyacente correspondiente y traducirlos en datos y eventos con forma de MRTK.

Por ejemplo, en la plataforma Windows Mixed Reality, es un controlador responsable de la interacción con las API de seguimiento de manos subyacentes de Windows para obtener información sobre las uniones, la posición y otras propiedades de la [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mano. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Es responsable de convertir estos datos en eventos DE MRTK pertinentes (por ejemplo, llamando a RaisePoseInputChanged o RaiseHandJointsUpdated) y actualizando su propio estado interno para que las consultas de devuelvan los datos [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) correctos.

Por lo general, el ciclo de vida de un controlador implicará:

1. Un administrador de dispositivos crea un controlador tras la detección de un nuevo origen (por ejemplo, el administrador de dispositivos detecta y empieza a realizar el seguimiento de una mano).

2. En el bucle Update() del controlador, llama a su sistema de API subyacente.

3. En el mismo bucle de actualización, genera cambios en los eventos de entrada llamando directamente al propio sistema de entrada principal (por ejemplo, generando HandMeshUpdated o HandJointsUpdated).

## <a name="pointers-and-focus"></a>Punteros y foco

Los punteros se usan para interactuar con objetos de juego. En esta sección se describe cómo se crean los punteros, cómo se actualizan y cómo determinan los objetos que están en el foco. También se tratarán los distintos tipos de punteros que existen y los escenarios en los que están activos.

### <a name="pointer-categories"></a>Categorías de puntero

Los punteros suelen estar en una de las siguientes categorías:

- **Punteros lejanos**

  Estos tipos de punteros se usan para interactuar con objetos que están lejos del usuario (muy lejos se define como simplemente "no cerca"). Por lo general, estos tipos de punteros convierten líneas que pueden llegar lejos al mundo y permiten al usuario interactuar con objetos que no están inmediatamente junto a ellos y manipularlos.

- **Punteros cercanos**

  Estos tipos de punteros se usan para interactuar con objetos que están lo suficientemente cerca del usuario para agarrar, tocar y manipular. Por lo general, estos tipos de punteros interactúan con los objetos buscando objetos en proximidad (ya sea mediante la difusión por rayos a distancias pequeñas, realizando una conversión esférica en busca de objetos en la proximidad o enumerando listas de objetos que se consideran que se pueden agarrar o tocar).

- **Teleportar punteros**

  Estos tipos de punteros se conecta al sistema de teleportación para controlar el traslado del usuario a la ubicación de destino del puntero.

## <a name="pointer-mediation"></a>Mediación de puntero

Dado que un solo controlador puede tener varios punteros (por ejemplo, la mano articulada puede tener punteros de interacción cercanos y lejanos), existe un componente responsable de mediar qué puntero debe estar activo.

Por ejemplo, a medida que la mano del usuario se acerca a un botón que se puede presionar, debe dejar de mostrarse y debe [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) estar activado.

Esto se controla mediante , que es responsable de determinar qué punteros están activos, en función del [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) estado de todos los punteros. Una de las cosas clave que esto hace es deshabilitar punteros lejanos cuando un puntero cercano está cerca de un objeto (consulte [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

Es posible proporcionar una implementación alternativa del mediador de puntero cambiando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propiedad en el perfil de puntero.

### <a name="how-to-disable-pointers"></a>Cómo deshabilitar punteros

Dado que el mediador de puntero ejecuta cada fotograma, termina controlando el estado activo o inactivo de todos los punteros. Por lo tanto, si establece la propiedad IsInteractionEnabled de un puntero en el código, el mediador de puntero sobrescribirá cada fotograma. En su lugar, puede especificar para controlar si los punteros deben [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) estar on o off. Tenga en cuenta que esto solo funcionará si usa el valor predeterminado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) y [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) en MRTK.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Ejemplo: Deshabilitación de los rayos de mano en MRTK

El código siguiente desactivará los rayos de las manos en MRTK:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

El código siguiente devolverá rayos de mano a su comportamiento predeterminado en MRTK:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

El código siguiente forzará la activación de los rayos de mano, independientemente de si están cerca de un control que se pueda agarrar:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

Vea [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) y para obtener más [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) ejemplos.

### <a name="focusprovider"></a>FocusProvider

es el esfuerzo que es responsable de iterar en la lista de todos los punteros y averiguar cuál es el objeto centrado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) para cada puntero.

En cada `Update()` llamada, esto hará lo siguiente:

1. Actualice todos los punteros, mediante la difusión por rayos y la detección de impactos según lo configurado por el propio puntero (por ejemplo, el puntero de esfera podría especificar sphereOverlap raycastMode, por lo que FocusProvider realizará una colisión basada en esferas).

2. Actualice el objeto con foco por puntero (es decir, si un objeto obtuvo el foco, también desencadenaría eventos en ese objeto, si un objeto perdiera el foco, desencadenaría la pérdida de foco, etc.).

### <a name="pointer-configuration-and-lifecycle"></a>Configuración y ciclo de vida del puntero

[Los punteros se pueden configurar](../features/input/pointers.md) en la *sección Punteros* del perfil del sistema de entrada.

La duración de un puntero suele ser la siguiente:

1. Un administrador de dispositivos detectará la presencia de un controlador. A continuación, este administrador de dispositivos creará el conjunto de punteros asociado al controlador mediante una llamada a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. FocusProvider, en su bucle Update(), iterará todos los punteros válidos y realizará la lógica de detección de impactos o raycast asociada. Se usa para determinar el objeto que se centra en cada puntero determinado.

    - Dado que es posible tener varios orígenes de entrada activos al mismo tiempo (por ejemplo, dos manos activas presentes), también es posible tener varios objetos que tengan el foco al mismo tiempo.

3. El administrador de dispositivos, al detectar que se perdió un origen del controlador, desmontará los punteros asociados al controlador perdido.