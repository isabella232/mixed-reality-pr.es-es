---
title: Entrada de realidad mixta (213)
description: Siga este tutorial de codificación con Unity, Visual Studio cascos envolventes para aprender los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, inmersivo, controlador de movimiento, academy, tutorial
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210230"
---
# <a name="mr-input-213-motion-controllers"></a>Entrada de realidad mixta (213): Controladores de movimiento

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](../develop/unity/tutorials/mr-learning-base-01.md) para HoloLens 2.

Los controladores de movimiento en el mundo de la realidad mixta agregan otro nivel de interactividad. Con [los controladores de](../design/motion-controllers.md)movimiento, podemos interactuar directamente con los objetos de una manera más natural, similar a nuestras interacciones físicas en la vida real, lo que aumenta la experiencia de la aplicación.

En mr input 213, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una experiencia de dibujo espacial simple. Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con varios tipos de pinceles y colores.

## <a name="topics-covered-in-this-tutorial"></a>Temas tratados en este tutorial

|![Tema MixedReality2131](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualización del controlador**|**Eventos de entrada del controlador**|**Controlador personalizado e interfaz de usuario**|
|Obtenga información sobre cómo representar modelos de controlador de movimiento en el modo de juego y el entorno de ejecución de Unity.|Comprenda los distintos tipos de eventos de botón y sus aplicaciones.|Obtenga información sobre cómo superponer elementos de la interfaz de usuario sobre el controlador o personalizarlo por completo.|

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada de realidad mixta (213): Controladores de movimiento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

Consulte la lista de comprobación de instalación de cascos envolventes en [esta página](../develop/install-the-tools.md).

* Este tutorial requiere [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Archivos de proyecto

* [Descargue los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requeridos por el proyecto y extraiga los archivos en el escritorio.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Configuración de Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Optimización de Unity para Windows Mixed Reality desarrollo
* Configuración Cámara de realidad mixta
* Configura el entorno

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **Open** (Abrir).
* Vaya al escritorio y busque **la carpeta MixedReality213-master** que anteriormente no ha jerarquíado.
* Haga clic en **Seleccionar carpeta**.
* Una vez que Unity termine de cargar los archivos del proyecto, podrá ver el editor de Unity.
* En Unity, seleccione **File > Build Configuración**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Seleccione **Universal Windows Platform en** la lista **Plataforma** y haga clic en el **botón Cambiar** plataforma.
* Establecer dispositivo de destino en **Cualquier dispositivo**
* Establezca Build Type (Tipo de compilación) en **D3D**.
* Establezca SDK en **Instalado más reciente**
* Comprobar **proyectos de C# de Unity**
    * Esto le permite modificar los archivos de script del Visual Studio sin volver a generar el proyecto de Unity.
* Haga clic **en Player Configuración**.
* En el **panel Inspector,** desplácese hacia abajo hasta la parte inferior.
* En XR Configuración, compruebe **Virtual Reality Supported (Compatible con Virtual Reality)**
* En SDK de realidad virtual, **seleccione Windows Mixed Reality**

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Cierre **la ventana Configuración** compilación.

### <a name="project-structure"></a>Estructura del proyecto

En este tutorial **[se Mixed Reality Toolkit: Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Puede encontrar las versiones en [esta página.](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Escenas completadas para la referencia**

* Encontrará dos escenas de Unity completadas en la **carpeta Escenas.**
    * **MixedReality213:** escena completada con un solo pincel
    * **MixedReality213 Avanzado:** escena completada para el diseño avanzado con varios pinceles

**Nueva configuración de escena para el tutorial**

* En Unity, haga clic **en Archivo > Nueva escena.**
* Eliminar **cámara principal y** luz **direccional**
* En el **Project,** busque y arrastre los siguientes elementos prefabs al panel **Jerarquía:**
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/Environment

    ![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)

* Hay dos prefabs de cámara en Mixed Reality Toolkit:
    * **MixedRealityCamera.prefab:** solo cámara
    * **MixedRealityCameraParent.prefab:** Cámara + Teleportación + Límite
    * En este tutorial, usaremos **la característica MixedRealityCamera** sin teleportación. Por este motivo, se  ha agregado un prefab de entorno sencillo que contiene una planta básica para que el usuario se sienta arrobado.
    * Para más información sobre la teleportación con **MixedRealityCameraParent,** consulte Diseño avanzado: [teleportación y conmoción.](#advanced-design---teleportation-and-locomotion)

**Configuración de Skybox**

* Haga **clic en Window > Lighting > Configuración**
* Haga clic en el círculo del lado derecho del **campo Material de Skybox.**
* Escriba "gray" y seleccione **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

    ![Configuración de Skybox](images/mr123-skyboxsetting-400px.jpg)

* Active **la opción Skybox** para poder ver el skybox degradado gris asignado

    ![Alternancia de la opción skybox](images/mr213-skyboxcheck-400px.jpg)

* La escena con MixedRealityCamera, Environment y skybox gris tendrá este aspecto.

    ![Entorno de MixedReality213](images/mr213-environment-600px.jpg)

* Haga **clic en File > Save Scene as (Guardar escena como).**
* **Guarde la** escena en la carpeta Escenas con cualquier nombre.

## <a name="chapter-1---controller-visualization"></a>Capítulo 1: Visualización del controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo representar modelos de controlador de movimiento en el modo de juego de Unity y en tiempo de ejecución.

Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador. Hay varios enfoques que puede seguir para la visualización del controlador en la aplicación:

* Valor predeterminado: uso del controlador predeterminado sin modificación
* Híbrido: uso del controlador predeterminado, pero personalización de algunos de sus elementos o superposición de componentes de interfaz de usuario
* Reemplazo: uso de su propio modelo 3D personalizado para el controlador

En este capítulo, conoceremos los ejemplos de estas personalizaciones de controlador.

### <a name="instructions"></a>Instrucciones

* En el **Project,** escriba **MotionControllers** en el cuadro de búsqueda. También puede encontrarlo en Assets/HoloToolkit/Input/Prefabs/.
* Arrastre el **prefab MotionControllers** al panel **Jerarquía.**
* Haga clic en el prefab **MotionControllers** en el panel **Jerarquía.**

**MotionControllers prefab**

**MotionControllers** prefab tiene un script **MotionControllerVisualizer** que proporciona las ranuras para los modelos de controlador alternativos. Si asigna sus propios modelos 3D personalizados, como una mano o un pregón, y marca "Usar siempre un modelo alternativo a la izquierda o la derecha", los verá en lugar del modelo predeterminado. Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador por un pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Instrucciones**

* En el **panel Inspector,** haga doble clic en El script **MotionControllerVisualizer** para ver el código en la Visual Studio

**Script MotionControllerVisualizer**

Las **clases MotionControllerVisualizer** y **MotionControllerInfo** proporcionan los medios para acceder a & modificar los modelos de controlador predeterminados. **MotionControllerVisualizer** se suscribe al evento **InteractionSourceDetected** de Unity y crea automáticamente instancias de los modelos de controlador cuando se encuentran.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF). Este formato se ha creado para proporcionar un formato común, a la vez que se mejora el proceso de transmisión y desempaquete de recursos 3D. En este caso, es necesario recuperar y cargar los modelos de controlador en tiempo de ejecución, ya que queremos que la experiencia del usuario sea lo más fluida posible y no se garantiza qué versión de los controladores de movimiento podría estar usando el usuario. Este curso, a través de la Mixed Reality Toolkit, usa una versión del proyecto [UnityGLTF del grupo Derronos](https://github.com/KhronosGroup/UnityGLTF).

Una vez entregado el controlador, los scripts pueden usar **MotionControllerInfo** para buscar las transformaciones de elementos de controlador específicos para que puedan colocarse correctamente.

En un capítulo posterior, aprenderemos a usar estos scripts para adjuntar elementos de la interfaz de usuario a los controladores.

*En algunos scripts, encontrará bloques de código **con #if ! UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código solo se ejecutan en el entorno de ejecución de UWP cuando se implementa en Windows. Esto se debe a que el conjunto de API que usan el editor de Unity y el entorno de ejecución de la aplicación para UWP son diferentes.*

* **Guarde la** escena y haga clic en **el botón de** reproducción.

Podrá ver la escena con controladores de movimiento en el casco. Puede ver animaciones detalladas para los clics de botón, el movimiento de la chincheta y el resaltado táctil.

![MR213_Controller de visualización predeterminada](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2: Adjuntar elementos de la interfaz de usuario al controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre los elementos de los controladores de movimiento.
* Obtenga información sobre cómo adjuntar objetos a partes específicas de los controladores.

En este capítulo, aprenderá a agregar elementos de la interfaz de usuario al controlador a los que el usuario puede acceder y manipular fácilmente en cualquier momento. También aprenderá a agregar una interfaz de usuario sencilla del selector de colores mediante la entrada del panel táctil.

### <a name="instructions"></a>Instrucciones

* En el **panel Project,** busque El script **MotionControllerInfo.**
* En el resultado de la búsqueda, haga doble clic en el script **MotionControllerInfo** para ver el código en Visual Studio.

**Script MotionControllerInfo**

El primer paso consiste en elegir a qué elemento del controlador desea que se adjunte la interfaz de usuario. Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Página principal**
* **Menú**
* **Agarran**
* **Stick**
* **Select**
* **Panel táctil**
* **Posición de apuntar:** este elemento representa la punta del controlador que apunta hacia delante.

**Instrucciones**

* En el **panel Project,** busque **Script AttachToController.**
* En el resultado de la búsqueda, haga doble clic en el script **AttachToController** para ver el código en Visual Studio.

**Script AttachToController**

El script **AttachToController** proporciona una manera sencilla de asociar cualquier objeto a una entrega y un elemento de controlador especificados.

En **AttachElementToController()**,

* Comprobación de la entrega **mediante MotionControllerInfo.Handedness**
* Obtener un elemento específico del controlador mediante **MotionControllerInfo.TryGetElement()**
* Después de recuperar la transformación del elemento del modelo de controlador, primaria el objeto debajo de él y establezca la posición local del objeto & rotación en cero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type &quot; + element + &quot; under controller &quot; + newController.ControllerParent.name + &quot;; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

La manera más sencilla de usar el script **AttachToController** es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.** Simplemente invalide las funciones **OnAttachToController** y **OnDetachFromController** para realizar la configuración o el desglose cuando se detecta o desconecta el controlador.

**Instrucciones**

* En el **panel Project,** escriba en el cuadro de búsqueda **ColorPickerWheel**. También puede encontrarlo en Assets/AppPrefabs/.
* Arrastre **el prefab ColorPickerWheel** al panel **Jerarquía.**
* Haga clic en el prefab **ColorPickerWheel** en el panel **Jerarquía.**
* En el **panel Inspector,** haga doble clic **en ColorPickerWheel** Script para ver el código en Visual Studio.

![Prefab ColorPickerWheel](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Dado **que ColorPickerWheel** hereda **AttachToController,** muestra **Handedness** y **Element** en el **panel Inspector.** Se adjuntará la interfaz de usuario al elemento Touchpad del controlador izquierdo.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** invalida **OnAttachToController** y **OnDetachFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de colores con entrada de panel táctil.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Guarde la** escena y haga clic en **el botón de** reproducción.

**Método alternativo para adjuntar objetos a los controladores**

Se recomienda que los scripts hereden **de AttachToController** e invalide **OnAttachToController.** Sin embargo, puede que esto no siempre sea posible. Una alternativa es usarlo como componente independiente. Esto puede ser útil cuando se desea asociar un objeto prefab existente a un controlador sin refactorizar los scripts. Simplemente haga que la clase espere a que IsAttached se establezca en true antes de realizar cualquier configuración. La manera más sencilla de hacerlo es mediante una corertina para "Iniciar".

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3: Trabajar con la entrada del panel táctil

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo obtener eventos de datos de entrada del panel táctil.
* Obtenga información sobre cómo usar la información de posición del eje del panel táctil para la experiencia de la aplicación.

### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** haga clic **en ColorPickerWheel.**
* En el **panel Inspector,** en **Animator**, haga doble clic **en ColorPickerWheelController.**
* Podrá ver la pestaña **Animator** abierta.

**Mostrar o ocultar la interfaz de usuario con el controlador de animación de Unity**

Para mostrar y ocultar la interfaz **de usuario colorPickerWheel** con animación, se usa el sistema [de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Establecer la propiedad Visible  **de ColorPickerWheel** en los desencadenadores true o false **Mostrar** y ocultar **desencadenadores de** animación. **Los** parámetros **Mostrar y** Ocultar se definen en el controlador de animación **ColorPickerWheelController.**

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

**Instrucciones**

* En el panel **Jerarquía,** seleccione **ColorPickerWheel** prefab
* En el **panel Inspector,** haga doble clic en el script **ColorPickerWheel** para ver el código en la Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** se suscribe al evento **InteractionSourceUpdated** de Unity para escuchar los eventos del panel táctil.

En **InteractionSourceUpdated()**, el script comprueba primero para asegurarse de que:

* es realmente un evento touchpad (obj.state.**touchpadTouched**)
* se origina en el controlador izquierdo (obj.state.source.**handedness**)

Si ambos son true, la posición del panel táctil (obj.state.**touchpadPosition**) se asigna a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

En **Update()**, en función de la **propiedad visible,** desencadena los desencadenadores de animación Mostrar y Ocultar en el componente del animador del selector de colores.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

En **Update()**, **selectorPosition** se usa para convertir un rayo en el colisionador de malla de la rueda de color, que devuelve una posición UV. A continuación, esta posición se puede usar para buscar la coordenada de píxeles y el valor de color de la textura de la rueda de color. Este valor es accesible para otros scripts a través de **la propiedad SelectedColor.**

![Selector de colores Wheel Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4: Invalidación del modelo de controlador

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instrucciones

* Haga **clic en MotionControllers** en el panel **Jerarquía.**
* Haga clic en el círculo del lado derecho del **campo Controlador derecho** alternativo.
* Escriba **"BrushController"** y seleccione el objeto prefab del resultado. Puede encontrarlo en Assets/AppPrefabs/**BrushController**.
* Comprobar **usar siempre un modelo de derecha alternativo**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

El **prefab BrushController** no tiene que incluirse en el panel **Jerarquía.** Sin embargo, para comprobar sus componentes secundarios:

* En el **panel Project,** escriba **BrushController** y arrastre el objeto prefab **BrushController** al panel **Jerarquía.**

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Encontrará el componente **Tip en** **BrushController.** Usaremos su transformación para iniciar o detener el dibujo de líneas.

* Elimine **BrushController** del panel **Jerarquía.**
* **Guarde la** escena y haga clic en **el botón de** reproducción. Podrá ver que el modelo de pincel ha reemplazado al controlador de movimiento derecho.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5: Pintar con la entrada Select

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar el evento de botón Seleccionar para iniciar y detener un dibujo de línea.

### <a name="instructions"></a>Instrucciones

* Busque **brushController** prefab en el **panel Project** datos.
* En el **panel Inspector,** haga doble clic **en BrushController** Script para ver el código en Visual Studio

**Script BrushController**

**BrushController** se suscribe a los eventos **InteractionSourcePressed** e **InteractionSourceReleased de** InteractionManager. Cuando se desencadena el evento **InteractionSourcePressed,** la propiedad **Draw** del pincel se establece en true; cuando **se desencadena el evento InteractionSourceReleased,** la propiedad **Draw** del pincel se establece en false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Aunque **Draw** está establecido en true, el pincel generará puntos en un representador de línea **de** Unity con instancias. Se mantiene una referencia a este objeto prefab en el campo **Stroke Prefab (Prefab de** trazo) del pincel.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Para usar el color seleccionado actualmente en la interfaz de usuario de la rueda del selector de colores, **BrushController** debe tener una referencia al **objeto ColorPickerWheel.** Dado que se crea una instancia del objeto **prefab BrushController** en tiempo de ejecución como controlador de reemplazo, cualquier referencia a los objetos de la escena tendrá que establecerse en tiempo de ejecución. En este caso, usamos **GameObject.FindObjectOfType para** buscar **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Guarde la** escena y haga clic en **el botón de** reproducción. Podrá dibujar las líneas y pintar con el botón seleccionar del controlador derecho.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6: Generación de objetos con la entrada Select

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar los eventos de entrada del botón Seleccionar y comprender.
* Aprenda a crear instancias de objetos

### <a name="instructions"></a>Instrucciones

* En el **Project,** escriba **ObjectSpawner en** el cuadro de búsqueda. También puede encontrarlo en Assets/AppPrefabs/
* Arrastre el **objeto Prefab ObjectSpawner** al panel **Jerarquía.**
* Haga **clic en ObjectSpawner en** el panel Hierarchy **(Jerarquía).**
* **ObjectSpawner tiene** un campo denominado **Origen de color.**
* En el panel **Jerarquía,** arrastre la **referencia ColorPickerWheel** a este campo.

    ![Object Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Haga clic en el objeto **Prefab ObjectSpawner** en el panel **Jerarquía.**
* En el **panel Inspector,** haga doble clic **en ObjectSpawner Script (ObjectSpawner** Script) para ver el código en Visual Studio.

**Script ObjectSpawner**

**ObjectSpawner crea** instancias de copias de una malla primitiva (cubo, esfera, cilindro) en el espacio. Cuando se **detecta interactionSourcePressed,** comprueba la entrega y si se trata de un evento **InteractionSourcePressType.Grasp** o **InteractionSourcePressType.Select.**

En el **caso de un evento Dedo,** incrementa el índice del tipo de malla actual (esfera, cubo, cilindro)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Para un **evento Select,** en **SpawnObject()**, se crea una instancia de un nuevo objeto, no tiene elementos primarios y se libera en el mundo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner usa** **ColorPickerWheel** para establecer el color del material del objeto de presentación. A los objetos generados se les da una instancia de este material para que conserven su color.

* **Guarde la** escena y haga clic en **el botón de** reproducción.

Podrá cambiar los objetos con el botón Comprender y generar objetos con el botón Seleccionar.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Compilación e implementación de una aplicación en Portal de realidad mixta

* En Unity, seleccione **File > Build Configuración**.
* Haga **clic en Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a Scenes In Build **(Escenas en la compilación).**
* Haga clic en **Generar**.
* Cree una **nueva carpeta** denominada "App".
* Haga clic en la **carpeta** Aplicación.
* Haga clic en **Seleccionar carpeta**.
* Cuando Unity haya terminado, aparecerá Explorador de archivos ventana.
* Abra la **carpeta** Aplicación.
* Haga doble clic **en YourSceneName.sln** Visual Studio archivo de solución.
* Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **X64.**
* Haga clic en la flecha desplegable situada junto al botón Dispositivo y seleccione **Equipo local.**
* Haga **clic en Depurar -> Iniciar sin depurar** en el menú o presione Ctrl + **F5**.

Ahora la aplicación se ha creado e instalado en Portal de realidad mixta. Puede iniciarla de nuevo a través de menú Inicio en Portal de realidad mixta.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Diseño avanzado: herramientas de pincel con diseño radial

![MixedReality213 Main](images/mr213-main-600px.jpg)

En este capítulo, aprenderá a reemplazar el modelo de controlador de movimiento predeterminado por una colección de herramientas de pincel personalizada. Como referencia, puede encontrar la escena completada **MixedReality213Advanced en** la **carpeta Scenes.**

### <a name="instructions"></a>Instrucciones

* En el **panel Project,** escriba **BrushSelector en** el cuadro de búsqueda . También puede encontrarlo en Assets/AppPrefabs/
* Arrastre el **objeto prefab BrushSelector** al panel **Jerarquía.**
* Para la organización, cree un Objeto GameObject vacío denominado **Brushes.**
* Arrastre los siguientes elementos prefabs **desde Project** panel a **Pinceles.**
    * Assets/AppPrefabs/BrushRev
    * Assets/AppPrefabs/BrushThin
    * Assets/AppPrefabs/Eraser
    * Assets/AppPrefabs/MarkerRev
    * Assets/AppPrefabs/MarkerThin
    * Assets/AppPrefabs/Pencil

    ![Pinceles](images/mixedreality213-brushes-250px.png)

* Haga clic en el prefab **MotionControllers** en el panel **Jerarquía.**
* En el **panel Inspector,** desactive **Usar siempre el modelo derecho alternativo** en el **visualizador del controlador de movimiento.**
* En el panel **Jerarquía,** haga clic **en BrushSelector.**
* **BrushSelector** tiene un campo denominado **ColorPicker**
* En el panel **Jerarquía,** arrastre **ColorPickerWheel** al **campo ColorPicker** **del** panel Inspector.

    ![Asignación de ColorPickerWheel al selector de pinceles](images/mr213-brushselector-500px.jpg)

* En el panel **Jerarquía,** en **BrushSelector** prefab, seleccione el **objeto Menu.**
* En el **panel Inspector,** en el **componente LineObjectCollection,** abra la lista **desplegable Matriz** de objetos. Verá 6 ranuras vacías.
* En el panel **Jerarquía,** arrastre cada uno de los elementos prefabs primarios bajo el objeto GameObject **Brushes** a estas ranuras en cualquier orden. (Asegúrese de arrastrar los elementos prefabs desde la escena, no los elementos prefab en la carpeta del proyecto).

![Selector de pinceles](images/mr213-brushselectorbrushes-700px.jpg)

**Prefab BrushSelector**

Dado que **BrushSelector** hereda **AttachToController,** muestra las opciones **Handedness** y **Element** en el **panel Inspector.** Hemos seleccionado **Right (Derecha)** **y Pointing Pose (Posición** de apuntar) para adjuntar herramientas de pincel al controlador derecho con dirección hacia delante.

**BrushSelector usa** dos utilidades:

* **Elipse:** se usa para generar puntos en el espacio a lo largo de una forma de elipse.
* **LineObjectCollection:** distribuye objetos mediante los puntos generados por cualquier clase Line (por ejemplo, Ellipse). Esto es lo que usaremos para colocar los pinceles a lo largo de la forma Elipse.

Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.

**Script LineObjectCollection**

**LineObjectCollection tiene** controles para el tamaño, la posición y la rotación de los objetos distribuidos a lo largo de su línea. Esto resulta útil para crear menús radiales como el selector de pinceles. Para crear la apariencia de pinceles que se escalan verticalmente desde nada cuando se aproximan a la posición central seleccionada, la curva **ObjectScale** alcanza los picos en el centro y se apaga en los bordes.

**Script BrushSelector**

En el caso de **BrushSelector,** hemos elegido usar la animación de procedimientos. En primer lugar, el script **LineObjectCollection** distribuye los modelos de pincel en una elipse. A continuación, cada pincel es responsable de mantener su posición en la mano del usuario en función de su valor **DisplayMode,** que cambia en función de la selección. Elegimos un enfoque de procedimiento debido a la alta probabilidad de que se interrumpan las transiciones de posición del pincel a medida que el usuario selecciona pinceles. Las animaciones Mecanim pueden controlar las interrupciones correctamente, pero tienden a ser más complicadas que una sencilla operación Lerp.

**BrushSelector** usa una combinación de ambos. Cuando se detecta la entrada del panel táctil, las opciones de pincel se vuelven visibles y se escalan verticalmente a lo largo del menú radial. Después de un período de tiempo de espera (que indica que el usuario ha realizado una selección), las opciones de pincel se escalan verticalmente de nuevo, dejando solo el pincel seleccionado.

**Visualización de la entrada del panel táctil**

Incluso en los casos en los que el modelo de controlador se ha reemplazado por completo, puede resultar útil mostrar la entrada en las entradas del modelo original. Esto ayuda a reducir las acciones del usuario en realidad. Para **BrushSelector,** hemos elegido hacer que el panel táctil sea brevemente visible cuando se recibe la entrada. Esto se hizo recuperando el elemento Touchpad del controlador, reemplazando su material por un material personalizado y aplicando después un degradado al color de ese material en función de la última vez que se recibió la entrada del panel táctil.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Selección de herramientas de pincel con entrada de panel táctil**

Cuando el selector de pincel detecta la entrada presionada del panel táctil, comprueba la posición de la entrada para determinar si estaba a la izquierda o a la derecha.

**Grosor del trazo con selectPressedAmount**

En lugar **del evento InteractionSourcePressType.Select** en **InteractionSourcePressed(),** puede obtener el valor análogo de la cantidad presionada mediante **selectPressedAmount**. Este valor se puede recuperar en **InteractionSourceUpdated()**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script de borrador**

**Eraser** es un tipo especial de pincel que invalida la **función** **DrawOverTime()** del pincel base. Aunque Draw es true, el borrador comprueba si su propina forma una intersección con los trazos de pincel existentes. Si es así, se agregan a una cola que se va a bajar y eliminar.

## <a name="advanced-design---teleportation-and-locomotion"></a>Diseño avanzado: teleportación y degradación

Si desea permitir que el usuario se mueva por la escena con la teleportación mediante la herramienta thumbstick, use **MixedRealityCameraParent en** lugar de **MixedRealityCamera**. También debe agregar **InputManager y** **DefaultCursor**. Puesto **que MixedRealityCameraParent** ya incluye **MotionControllers** y **Boundary** como componentes secundarios, debe quitar los elementos MotionController y **Environment** prefab **existentes.**

### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** elimine **MixedRealityCamera**, **Environment** y **MotionControllers.**
* En el **panel Project ,** busque y arrastre los siguientes elementos prefabs al panel **Jerarquía:**
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![Cámara de realidad mixta principal](images/mr213-cameraparent-300px.png)

* En el panel **Jerarquía,** haga clic en **Administrador de entrada.**
* En el **panel Inspector,** desplácese hacia abajo hasta la **sección Simple Single Pointer Selector (Selector de puntero simple).**
* En el panel **Jerarquía,** arrastre **DefaultCursor** al **campo Cursor.**

    ![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Guarde la** escena y haga clic en **el botón de** reproducción. Podrá usar el botón de posición para girar a la izquierda o a la derecha o teleportar.

## <a name="the-end"></a>Fin

Y este es el final de este tutorial. Ha aprendido:

* Cómo trabajar con modelos de controlador de movimiento en el modo de juego y el entorno de ejecución de Unity.
* Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.
* Cómo superponer elementos de la interfaz de usuario sobre el controlador o personalizarlo por completo.

Ya está listo para empezar a crear su propia experiencia inmersiva con controladores de movimiento.

## <a name="completed-scenes"></a>Escenas completadas

* En el panel **de** Project de Unity, haga clic en la carpeta **Escenas.**
* Encontrará dos escenas de Unity **MixedReality213** y **MixedReality213Advanced**.
    * **MixedReality213:** escena completada con un solo pincel
    * **MixedReality213Advanced:** escena completada con varios pinceles con el ejemplo de cantidad de presión del botón select

## <a name="see-also"></a>Consulte también

* [Archivos de proyecto mr input 213](https://github.com/Microsoft/MixedReality213)
* [Mixed Reality Toolkit: escena de prueba del controlador de movimiento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Mixed Reality Toolkit- Mecánica de toma](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Directrices de desarrollo del controlador de movimiento](../design/motion-controllers.md)