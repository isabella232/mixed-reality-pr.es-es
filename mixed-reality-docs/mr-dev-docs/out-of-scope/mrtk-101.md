---
title: 'MRTK 101: uso de interacciones espaciales comunes'
description: Uso de Unity con Mixed Reality Toolkit para interacciones básicas en HoloLens 2, HoloLens, Windows Mixed Reality y Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, design, sample app, controls, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.localizationpriority: high
ms.openlocfilehash: 8b9af843dc059ef4d50aa5508356c7aeed968a4e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98248151"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a>MRTK 101: Uso de Mixed Reality Toolkit Unity para interacciones espaciales comunes

![MRTK](images/MRTK101/MRTK101Cover.png)

Aprende a usar MRTK para lograr algunos de los patrones de interacción comunes más usados en la realidad mixta.

- ¿Cómo simular interacciones de entrada en el editor de Unity?
- ¿Cómo agarrar y desplazar un objeto?
- ¿Cómo cambiar el tamaño de un objeto?
- ¿Cómo mover o girar un objeto con precisión?
- ¿Cómo conseguir que un objeto responda a eventos de entrada?
- ¿Cómo agregar comentarios visuales?
- ¿Cómo agregar comentarios de audio?
- ¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?
- ¿Cómo hacer que un objeto te siga?
- ¿Cómo hacer que un objeto se ponga delante de ti?

> [!NOTE]
> Este artículo se ha actualizado para reflejar los cambios en [MRTK, versión 2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).

Todo el contenido de esta página se puede probar en el editor de Unity con la simulación de entrada de MRTK. Si no lo ha hecho, siga la [Guía de instalación de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) para instalar la versión más reciente de MRTK.

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a>¿Cómo simular interacciones de entrada en el editor de Unity?

MRTK admite la simulación de entrada en el editor. Ejecute la escena haciendo clic en el botón Reproducir de Unity y, a continuación, use las claves siguientes para simular la entrada:
- Presiona las teclas W, A, S y D para mover la cámara.
- Mantén presionado el botón derecho del ratón y muévelo para mirar alrededor.
- Presione la barra espaciadora (mano derecha) o la tecla Mayús izquierda (mano izquierda) para abrir las manos simuladas.
- Presione las teclas T o Y para mantener las manos simuladas en la vista.
- Presione Q o E (horizontal)/R o F (vertical) para girar las manos simuladas.

Puede obtener más información sobre la simulación de entrada en la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).

## <a name="how-to-grab-and-move-an-object"></a>¿Cómo agarrar y desplazar un objeto?

Adjunte los scripts **ObjectManipulator.cs** y **NearInteractionGrabbable.cs** para que se pueda obtener un objeto. ObjectManipulator admite interacciones cercanas y lejanas. Puede agarrar y mover un objeto con la entrada de seguimiento de manos articulada de HoloLens 2 (cercana), el haz de mano (lejano), el cursor del controlador de movimiento (lejano), el cursor de mirada de HoloLens y el toque en el aire (lejano).

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a>¿Cómo cambiar el tamaño de un objeto?
**ObjectManipulator.cs** admite el escalado o la rotación con dos manos. El script funciona con varios tipos de entrada, como la entrada de manos articulada de HoloLens 2, la entrada de mirada y gestos de HoloLens 1 y la entrada del controlador de movimiento del casco envolvente de Windows Mixed Reality.

- [Más información sobre Object Manipulator en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>¿Cómo mover o girar un objeto con precisión?
Asigne **BoundsControl.cs** a un objeto para usar el cuadro de límite, que es la interfaz para escalar y girar un objeto. De forma predeterminada, se muestran los controladores y los cables de color azul del estilo de HoloLens 1. Para usar controladores animados basados en proximidad del estilo de HoloLens 2, debes asignar objetos prefabricados y materiales. 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [Más información sobre Bounds Control en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a>¿Cómo conseguir que un objeto responda a eventos de entrada?
Asigne **PointerHandler.cs** a un objeto. En el inspector, puede usar los eventos OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Para usarlos en un script, implemente **IMixedRealityPointerHandler**.

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [Más información sobre el sistema de entrada en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>¿Cómo agregar comentarios visuales?
Asigne **Interactable.cs** a un objeto. En el inspector, agregue el objeto de destino y cree un nuevo tema. Mediante el uso de perfiles de tema interactuables, puedes agregar comentarios visuales a todos los estados de interacción de entrada disponibles.

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Los elementos interactuables proporcionan varios tipos de temas, incluido el tema del sombreador, que permite controlar las propiedades del sombreador por estado de interacción.

- [Más información sobre los elementos interactuables en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

Otro bloque de creación importante para los comentarios visuales es **MRTK Standard Shader**. Con el sombreador estándar de MRTK, puedes agregar fácilmente efectos de comentarios visuales, como luz de desplazamiento y de proximidad. Dado que el sombreador estándar de MRTK realiza un cálculo menor que el sombreador estándar de Unity, puede crear una experiencia de rendimiento.

Crea un nuevo material y selecciona el sombreador "Mixed Reality Toolkit > Standard (Estándar)". También puedes elegir uno de los materiales existentes que usan el sombreador estándar de MRTK.

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [Más información sobre el sombreador estándar de MRTK en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>¿Cómo agregar comentarios de audio?
Agregue **AudioSource** a un objeto. A continuación, en los scripts que exponen eventos de entrada (p. ej., Interactable.cs o PointerHandler.cs), asigne el objeto con AudioSource al evento y seleccione **AudioSource.PlayOneShot()** . Puedes usar los clips de audio o elegir uno de los recursos de audio de MRTK.

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a>¿Cómo usar los objetos prefabricados de botón de estilo de HoloLens 2?
MRTK proporciona varios tipos de botones de estilo de shell (SO) de HoloLens 2, incluidos los comentarios visuales, como la luz de proximidad, el cuadro de compresión y un efecto de ondulación en la superficie del botón, que mejoran la confianza del usuario.

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

Arrastre y coloque uno de los **objetos prefabricados de botón presionable del estilo de HoloLens 2** a la escena. El objeto prefabricado usa el Interactable.cs presentado anteriormente. Puedes usar eventos expuestos como OnClick() en el objeto interactuable para desencadenar acciones.

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Más información sobre los objetos prefabricados de botón en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a>¿Cómo hacer que un objeto te siga?
Asigne el script **RadialView.cs** o **Follow.cs** a un objeto. Forma parte de la serie de scripts del solucionador que permite lograr distintos tipos de selección de ubicación de objetos en el espacio 3D. **SolverHandler.cs** se agregará automáticamente.
A continuación se incluye un ejemplo de configuración de RadialView para lograr el comportamiento y la etiqueta "lazy follow" (seguimiento diferido), como el menú Inicio del shell de HoloLens. Puedes especificar la distancia mínima/máxima y los grados de vista mínimos y máximos. En el ejemplo siguiente se muestra cómo colocar el objeto en un intervalo entre 0,4 m y 0,8 m en 15°. Ajusta los valores de tiempo de Lerp para que la actualización posicional sea más rápida o más lenta.

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [Más información sobre los solucionadores en la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a>¿Cómo hacer que un objeto se ponga delante de ti?
Asigne el script **Billboard.cs** a un objeto. Siempre se situará delante de usted, independientemente de su posición. Puedes especificar la opción del eje dinámico.

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


¿Estás listo para crear experiencias sorprendentes para la realidad mixta? Visita las páginas siguientes y obtén más información sobre MRTK y Mixed Reality.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Consulte también
* [Guía de instalación de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Portal de documentación de MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Guía de portabilidad de HoloToolkit a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
