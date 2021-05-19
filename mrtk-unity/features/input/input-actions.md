---
title: Acciones de entrada
description: Documentación para crear acciones de entrada en MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, InputActions,
ms.openlocfilehash: 071d4bc8bb4193a3d60cb53852c192ae975d79df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144150"
---
# <a name="input-actions"></a>Acciones de entrada

[**Las acciones de**](input-actions.md) entrada son abstracciones sobre entradas sin procesar diseñadas para ayudar a aislar la lógica de la aplicación de los orígenes de entrada específicos que producen una entrada. Puede ser útil, por ejemplo,  definir una acción Seleccionar y asignarla al botón izquierdo del mouse, un botón en un controlador gamepad y un desencadenador en un controlador de 6 DOF. A continuación, puede hacer que la lógica de la aplicación escuche los eventos select *input* action en lugar de tener que tener en cuenta todas las distintas entradas que pueden producirla.

## <a name="creating-an-input-action"></a>Creación de una acción de entrada

Las acciones de entrada se configuran  en el perfil de acciones de entrada **,** dentro del perfil del sistema de entrada del componente del kit de herramientas de Mixed Reality, especificando un nombre para la acción y el tipo de entradas *(restricción* del eje ) al que se puede asignar:

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

Estos son los valores que se usan con más frecuencia para **la restricción de eje:**

Restricción de eje | Descripción
--- | ---
Digital | Entrada de encendido y apagado como un botón binario en un gamepad o mouse.
Eje único | Entrada de eje único, como un desencadenador análogo en un gamepad.
Eje dual | Entrada de eje dual, como una huella digital.
Seis dof | Posición 3D con traducción y rotación como la producida por 6 controladores DOF.

Puede encontrar la lista completa en [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .

## <a name="mapping-input-to-actions"></a>Asignación de entrada a acciones

La forma de asignar una entrada a una acción y depende del tipo de origen de entrada:

### <a name="controller-input"></a>Entrada del controlador

Vaya al perfil de **asignación de entrada del controlador**, en el perfil del sistema de *entrada*. Allí encontrará una lista de todos los controladores admitidos:

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

Seleccione la que desea configurar y aparecerá una ventana de diálogo con todas las entradas del controlador, lo que le permite establecer una acción para cada una de ellas:

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a>Entrada de voz

En Perfil **de comando de voz**, en El perfil del sistema *de* entrada , encontrará la lista de comandos de voz definidos actualmente. Para asignar uno de ellos a una acción, selecciónelo en la *lista desplegable* Acción.

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a>Entrada de gesto

El **perfil de gestos**, en el *perfil del sistema de entrada*, contiene todos los gestos definidos. Puede asignar cada una de ellas a una acción seleccionándolo en la *lista desplegable* Acción.

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a>Control de acciones de entrada

> [!WARNING]
> Actualmente solo se pueden controlar las *acciones de* entrada de tipo Digital mediante los métodos descritos en esta sección. Para otros tipos de acción, tendrá que controlar directamente los eventos de las entradas correspondientes en su lugar. Por ejemplo, para controlar una acción de 6 DOF asignada a las entradas del controlador, tendrá que usar [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

La manera más fácil de controlar las acciones de entrada es usar el [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script. Esto le permite definir la acción que quiere escuchar y reaccionar a los eventos iniciados y finalizados de la acción mediante eventos de Unity.

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

Si desea más control, puede implementar la [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interfaz directamente en el script. Consulte la sección [**Eventos de entrada**](input-events.md) para obtener más detalles sobre el control de eventos a través de interfaces de controlador.

## <a name="examples"></a>Ejemplos

Vea una escena de ejemplo en la que se muestra cómo crear una acción, asignarla a entradas de controlador, voz y gestos y usarla para girar un `MRTK/Examples/Demos/Input/Scenes/InputActions` objeto en el comando.

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">
