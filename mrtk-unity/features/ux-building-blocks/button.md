---
title: Botones
description: Información general sobre botones en MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, botones de MRTK
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281852"
---
# <a name="buttons"></a>Botones

![Button Main](../images/button/MRTK_Button_Main.png)

Un botón ofrece al usuario una forma de desencadenar una acción inmediata. Es uno de los componentes más fundamentales de la realidad mixta. MRTK proporciona varios tipos de elementos prefabs de botón.

## <a name="button-prefabs-in-mrtk"></a>Prefabs de botón en MRTK

Ejemplos de los requisitos previos del botón en la ``MRTK/SDK/Features/UX/Interactable/Prefabs`` carpeta

### <a name="unity-ui-imagegraphic-based-buttons"></a>Botones basados en gráficos o imágenes de la interfaz de usuario de Unity

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Botones basados en colisionador

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) PressableButtonHoloLens2 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) PressableButtonHoloLens2Unplated 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) PressableButtonHoloLens2Circular 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    HoloLens 2 botón de estilo shell con placa trasera que admite varios comentarios visuales, como luz de borde, luz de proximidad y placa frontal comprimida
    :::column-end:::
    :::column:::
    HoloLens 2 botón de estilo shell sin placa trasera
    :::column-end:::
    :::column:::
    HoloLens 2 botón de estilo shell con forma circular
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    ![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    Botón de HoloLens 2 estilo shell de Wide HoloLens 2 32 x 96 mm
    :::column-end:::
    :::column:::
    Barra de HoloLens 2 horizontal con placa trasera compartida
    :::column-end:::
    :::column:::
    Barra de HoloLens 2 vertical con placa trasera compartida
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    casilla de HoloLens 2 estilo de shell de 32 x 32 mm
    :::column-end:::
    :::column:::
    HoloLens 2 conmutador de estilo shell de 32 x 32 mm 
    :::column-end:::
    :::column:::
    radio de estilo shell de HoloLens 2 32 x 32 mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    ![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96** 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96** 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens 2 de la casilla de estilo shell de 32 x 96 mm
    :::column-end:::
    :::column:::
    HoloLens 2 de estilo shell de 32 x 96 mm
    :::column-end:::
    :::column:::
    radio de estilo shell de HoloLens 2 32 x 96 mm
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![Radial ](../images/button/MRTK_Button_Radial.png) **radial**
    :::column-end:::
    :::column:::
    ![Casilla de ](../images/button/MRTK_Button_Checkbox.png) **verificación**
    :::column-end:::
    :::column:::
    ![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Botón radial 
    :::column-end:::
    :::column:::
    Casilla de verificación 
    :::column-end:::
    :::column:::
    Modificador para alternar
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**
    :::column-end:::
    :::column:::
    ![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton** 
    :::column-end:::
    :::column:::
    ![Botón Base del ](../images/button/MRTK_Button_Base.png) **botón**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    HoloLens botón de estilo de shell de 1.ª generación
    :::column-end:::
    :::column:::
    Botón de inserción de forma redondeada
    :::column-end:::
    :::column:::
    Botón Básica
    :::column-end:::
:::row-end:::

`Button`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) se basa en el concepto [Interactable](interactable.md) para proporcionar controles de interfaz de usuario sencillos para botones u otros tipos de superficies interactivas. El botón de línea base admite todos los métodos de entrada disponibles, incluida la entrada de mano articulada para las interacciones cercanas, así como la mirada y la pulsación en el aire para las interacciones lejanas. También puede usar el comando de voz para desencadenar el botón.

`PressableButtonHoloLens2`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) es el botón de estilo de shell de HoloLens 2 que admite el movimiento preciso del botón para la entrada de seguimiento directo de la mano. Combina el `Interactable` script con el `PressableButton` script.

Por HoloLens 2, se recomienda usar botones con una placa trasera opaca. Los botones transparentes no se recomiendan debido a estos problemas de facilidad de uso y estabilidad:

* El icono y el texto son difíciles de leer con el entorno físico
* Es difícil entender cuándo se desencadena el evento
* Hologramas que se muestran a través de un plano transparente puede ser inestable con la estabilización LSR de profundidad de HoloLens 2 de datos

![Botón adosado](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Uso de botones presionables

### <a name="unity-ui-based-buttons"></a>Botones basados en la interfaz de usuario de Unity

Cree un lienzo en la escena (GameObject -> UI -> Canvas). En el panel Inspector del lienzo:

* Haga clic en "Convertir al lienzo de MRTK".
* Haga clic en "Add NearInteractionTouchableUnityUI" (Agregar NearInteractionTouchableUnityUI).
* Establezca la escala X, Y y Z del componente Transformación de rect en 0,001.

A continuación, arrastre `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/. PressableButtonUnityUICircular.prefab) o `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) en el lienzo.

### <a name="collider-based-buttons"></a>Botones basados en colisionador

Simplemente arrastre `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) o `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) a la escena. Estos elementos prefabs de botón ya están configurados para tener comentarios visuales de audio para los distintos tipos de entradas, incluida la entrada y la mirada con la mano articuladas.

Los eventos expuestos en el propio elemento prefab, así como el [componente Interactable,](interactable.md) se pueden usar para desencadenar acciones adicionales. Los botones presionables de la [escena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usan el evento *OnClick* de Interactable para desencadenar un cambio en el color de un cubo. Este evento se desencadena para diferentes tipos de métodos de entrada, como la mirada, el toque de aire, el rayo de la mano, así como las pulsaciones de botón físicos a través del script de botón que se puede presionar.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Puede configurar cuando el botón presionable desan el evento *OnClick* a través `PhysicalPressEventRouter` de en el botón. Por ejemplo, puede establecer *OnClick* para que se desenlome cuando se presione el botón por primera vez, en lugar de presionarlo y liberarlo, estableciendo *Interactable On Click (Interactable* al hacer clic) en Event On Press (Evento al *presionar).*

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Para aprovechar la información específica del estado de entrada de la mano articulada, puede usar eventos de botones presionables: *Touch Begin*, *Touch End*, Button *Pressed*, *Button Released*. Sin embargo, estos eventos no se mostrarán en respuesta a las entradas de pulsación del aire, de rayos de mano o de los ojos. **Para admitir interacciones cercanas y lejanas, se recomienda usar el evento *OnClick de Interactable.***

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Estados de interacción

En el estado de inactividad, la placa frontal del botón no está visible. A medida que un dedo se acerca o un cursor de la entrada de mirada apunta a la superficie, el borde brillante de la placa frontal se vuelve visible. Hay un resaltado adicional de la posición del dedo en la superficie de la placa frontal. Cuando se inserta con un dedo, la placa frontal se mueve con el dedo. Cuando el dedo toca la superficie de la placa frontal, muestra un efecto de pulso sutil para proporcionar comentarios visuales del punto táctil.

En HoloLens 2 de estilo shell, hay muchas indicaciones visuales y asequiciones para aumentar la confianza del usuario en la interacción.

|  ![Luz de proximidad](../images/button/ux_button_affordance_proximitylight.jpg) | ![Resaltado del foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compresión de la caja de seguridad](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on trigger (Pulse on trigger)](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Luz de proximidad | Resaltado del foco | Compresión de la caja de seguridad | Pulse on trigger (Pulse on trigger) |

El efecto de pulso sutil se desencadena mediante el botón que se puede presionar, que busca *proximityLight(s)* que se encuentran en el puntero que interactúa actualmente. Si se encuentra alguna luz de proximidad, se llama al método , que anima automáticamente los parámetros del `ProximityLight.Pulse` sombreador para mostrar un pulso.

## <a name="inspector-properties"></a>Propiedades del inspector

![Estructura de botones](../images/button/MRTK_Button_Structure.png)

**Box Collider** 
 `Box Collider` para la placa frontal del botón.

**Botón que se puede presionar** Lógica para el movimiento del botón con la interacción de la pulsación con la mano.

**Enrutador de eventos de presión física** Este script envía eventos desde la interacción de la pulsación a mano [a Interactable.](interactable.md)

**Interactuable** 
 [Interactable controla](interactable.md) varios tipos de estados y eventos de interacción. HoloLens la mirada, el gesto y la entrada de voz y la entrada del controlador de movimiento del casco envolvente se controlan directamente mediante este script.

**Origen de audio** Origen de audio de Unity para los clips de comentarios de audio.

*NearInteractionTouchable.cs* Obligatorio para que cualquier objeto sea táctil con entrada de mano articulada.

## <a name="prefab-layout"></a>Diseño prefab

El *objeto ButtonContent* contiene la placa frontal, la etiqueta de texto y el icono. FrontPlate *responde a* la proximidad del dedo del índice mediante el *sombreador Button_Box* índice. Muestra bordes brillantes, luz de proximidad y un efecto de pulso en el toque. La etiqueta de texto se realiza con TextMesh Pro. *La visibilidad de SeeItSayItLabel* se controla mediante el tema de [Interactable.](interactable.md)

![Diseño de botón](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Cómo cambiar el icono y el texto

Los botones de MRTK usan un componente para ayudarle a cambiar el icono, el `ButtonConfigHelper` texto y la etiqueta del botón. (Tenga en cuenta que algunos campos pueden estar ausentes si los elementos no están presentes en el botón seleccionado).

![Asistente de configuración de botón](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Crear y modificar conjuntos de iconos

Un **conjunto de iconos** es un conjunto compartido de recursos de icono usados por el `ButtonConfigHelper` componente. Se admiten *estilos de* tres iconos.

* **Los** iconos de cuatro se representan en un cuadrándido mediante `MeshRenderer` . Este es el estilo de icono predeterminado.
* **Los** iconos de sprite se representan mediante `SpriteRenderer` . Esto resulta útil si prefiere importar los iconos como una hoja de sprites, o si quiere que los recursos de icono se compartan con los componentes de la interfaz de usuario de Unity. Para usar este estilo, deberá instalar el paquete Sprite Editor **(Windows -> Administrador de paquetes -> sprite 2D)**
* **Los** iconos char se representan mediante un `TextMeshPro` componente. Esto resulta útil si prefiere usar una fuente de icono. Para usar la HoloLens de icono de fuente, deberá crear un recurso `TextMeshPro` de fuente.

Para cambiar el estilo que usa el botón, expanda la lista desplegable *Iconos* de ButtonConfigHelper y seleccione en la lista desplegable *Estilo de* icono.

Puede crear un nuevo conjunto de iconos de botón con el menú de recursos: **Crear > Mixed Reality Toolkit > conjunto de iconos.** Para agregar iconos de cuatro y sprites, simplemente arrástrelos a sus respectivas matrices. Para agregar iconos char, primero debe crear y asignar un recurso de fuente.

En MRTK 2.4 y posteriores, se recomienda mover texturas de icono personalizadas a iconSet.
Para actualizar los recursos de todos los botones de un proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.
(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)

Importar el paquete Microsoft.MixedRealityToolkit.Unity.Tools necesario para actualizar los botones.

![Cuadro de diálogo actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit.Generated/CustomIconSets. Un cuadro de diálogo indicará que esto ha tenido lugar.

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Crear un recurso de fuente HoloLens icono de archivo

En primer lugar, importe la fuente del icono en Unity. En Windows máquinas virtuales, puede encontrar la fuente HoloLens predeterminada *en Windows/Fonts/holomdl2.ttf.* Copie y pegue este archivo en la carpeta Recursos.

A continuación, abra TextMeshPro Font Asset Creator a través de **Window > TextMeshPro > Font Asset Creator.** Esta es la configuración recomendada para generar un atlas HoloLens fuente. Para incluir todos los iconos, pegue el siguiente intervalo Unicode en el *campo Secuencia de* caracteres:

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creación de botones 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Una vez generado el recurso de fuente, guárdelo en el proyecto y asígnelo al campo Fuente de *icono de char* del conjunto de iconos. Ahora *se rellenará la* lista desplegable Iconos disponibles. Para que un icono esté disponible para que lo use un botón, haga clic en él. Se agregará a la lista desplegable *Iconos* seleccionados y ahora se mostrará en La opción Puede dar al `ButtonConfigHelper.` icono una etiqueta. Esto permite establecer el icono en tiempo de ejecución.

![Creación de botones 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creación de botones 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Para usar el conjunto de iconos, seleccione un botón, expanda la lista desplegable Iconos de y `ButtonConfigHelper` asígnelo al campo *Conjunto de* iconos.

![Conjunto de iconos de botón](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Cómo cambiar el tamaño de un botón

HoloLens 2 el tamaño del botón de estilo shell es de 32 x 32 mm. Para personalizar la dimensión, cambie el tamaño de estos objetos en el botón prefab:

1. **FrontPlate**
2. **Quad** en BackPlate
3. **Box Collider** en la raíz

A continuación, haga clic en el botón Corregir **límites** del script NearInteractionTouchable que se encuentra en la raíz del botón.

Actualización del tamaño de la personalización de tamaño de botón FrontPlate ![ 1](../images/button/MRTK_Button_SizeCustomization1.png)

Actualización del tamaño de la personalización de ![ tamaño de botón cuadránitrido 2](../images/button/MRTK_Button_SizeCustomization2.png)

Actualizar el tamaño de la personalización del tamaño del botón ![ colisionador de cuadro 3](../images/button/MRTK_Button_SizeCustomization3.png)

Haga clic en la personalización del tamaño del botón "Corregir ![ límites" 4.](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it"></a>Comando de voz ('see-it, say-it')

**Controlador de entrada de voz** El [script Interactable](interactable.md) de Pressable Button ya implementa `IMixedRealitySpeechHandler` . Aquí se puede establecer una palabra clave de comando de voz.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Perfil de entrada de voz** Además, debe registrar la palabra clave de comando de voz en el perfil global *de comandos de voz*.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**See-it, Say-it label** El botón prefab presionable tiene un marcador de posición TextMesh Pro etiqueta en el *objeto SeeItSayItLabel.* Puede usar esta etiqueta para comunicar al usuario la palabra clave del comando de voz para el botón.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Cómo crear un botón desde cero

Puede encontrar los ejemplos de estos botones en la **escena PressableButtonExample.**

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. Creación de un botón presionable con cubo (solo interacción cercana)

1. Crear un cubo de Unity (GameObject > 3D Object > Cube)
2. Agregar `PressableButton.cs` script
3. Agregar `NearInteractionTouchable.cs` script

En el `PressableButton` panel Inspector del , asigne el objeto de cubo a los objetos visuales de botón de **movimiento**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Al seleccionar el cubo, verá varias capas de color en el objeto. Esto visualiza los valores de distancia en **Presione Configuración**. Con los identificadores, puede configurar cuándo iniciar la pulsación (mover el objeto) y cuándo desencadenar el evento.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Al presionar el botón, se moverá y generará los eventos adecuados expuestos en el script, como `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Solución de problemas

Si el botón está ejecutando una doble  pulsación, asegúrese de  que la propiedad Aplicar inserción frontal está activa y de que el plano Iniciar distancia de inserción se coloca delante del plano táctil Interacción **cercana.** El **plano táctil Interacción** cercana se indica mediante el plano azul situado delante del origen de la flecha blanca en el gif siguiente:

![Componente de script de botón presionable con la propiedad Aplicar inserción front-push resaltada](../images/button/MRTK_Button_Enforce_Push.png)

![Ejemplo animado de mover la distancia de inserción inicial delante del plano táctil de interacción cercana](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. Adición de comentarios visuales al botón de cubo básico

MrTK Standard Shader proporciona varias características que facilita la adición de comentarios visuales. Cree un material y seleccione el sombreador `Mixed Reality Toolkit/Standard` . O bien, puede usar o duplicar uno de los materiales existentes en `/SDK/StandardAssets/Materials/` que usa el sombreador estándar de MRTK.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Active `Hover Light` y en Fluent `Proximity Light` **opciones**. Esto habilita los comentarios visuales para las interacciones de mano cercana (luz de proximidad) y puntero lejano (mantener el puntero sobre la luz).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. Adición de comentarios de audio al botón básico del cubo

Dado que el script expone eventos como `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), podemos asignar fácilmente comentarios de audio. Simplemente agregue unity al objeto de cubo y, a `Audio Source` continuación, asigne clips de audio seleccionando AudioSource.PlayOneShot(). Puede usar los clips MRTK_Select_Main y MRTK_Select_Secondary audio en la `/SDK/StandardAssets/Audio/` carpeta .

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. Adición de estados visuales y control de eventos de interacción lejana

[Interactable](interactable.md) es un script que facilita la creación de un estado visual para los distintos tipos de interacciones de entrada. También controla eventos de interacción lejana. Agregue `Interactable.cs` y arrastre y coloque el objeto de cubo en el campo **Destino** en **Perfiles**. A continuación, cree un tema con un tipo **ScaleOffsetColorTheme**. En este tema, puede especificar el color del objeto para los estados de interacción específicos, como **Foco** **y Presionado.** También puede controlar la escala y el desplazamiento. Compruebe **Easing (Aceleración)** y establezca la duración para que la transición visual sea fluida.

![Selección del tema del perfil](../images/button/mrtk_button_profiles.gif)

Verá que el objeto responde a interacciones lejanas (de rayo de mano o de mirada) y cercanas (mano).

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Ejemplos de botones personalizados

En la [escena HandInteractionExample,](../example-scenes/hand-interaction-examples.md)vea los ejemplos de botones de redondeo y de teclado que usan `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Cada clave tiene un `PressableButton` y un `NearInteractionTouchable` script asignados. Es importante comprobar que la dirección de *reenvío local* de `NearInteractionTouchable` es correcta. Se representa mediante una flecha blanca en el editor. Asegúrese de que la flecha apunta lejos de la cara frontal del botón:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Vea también

* [Interactuable](interactable.md)
* [Temas visuales](visual-themes.md)
