---
title: Botones
description: Información general sobre los botones de MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Los botones Unity, HoloLens, HoloLens 2, realidad mixta, desarrollo, MRTK y MRTK
ms.openlocfilehash: 43570c225f25b9ea73c9d1fc4cc9b6c92b8c2dfc
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003124"
---
# <a name="button"></a>Botón

![Botón principal](../images/button/MRTK_Button_Main.png)

Un botón ofrece al usuario una forma de desencadenar una acción inmediata. Es uno de los componentes fundamentales de la realidad mixta. MRTK proporciona varios tipos de Prefabs de botón.

## <a name="button-prefabs-in-mrtk"></a>Botón Prefabs en MRTK

Ejemplos del botón Prefabs en la ``MRTK/SDK/Features/UX/Interactable/Prefabs`` carpeta

### <a name="unity-ui-imagegraphic-based-buttons"></a>Botones basados en imagen/gráfico de interfaz de usuario de Unity

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a>Botones basados en Colisionador

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
    Botón de estilo de Shell de HoloLens 2 con placa posterior que admite diversos comentarios visuales como la luz de borde, la luz de proximidad y la placa frontal comprimida
    :::column-end:::
    :::column:::
    Botón de estilo de Shell de HoloLens 2 sin fondo
    :::column-end:::
    :::column:::
    Botón de estilo de Shell de HoloLens 2 con forma circular
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
    Botón de estilo de Shell de 32x96mm Wide HoloLens 2
    :::column-end:::
    :::column:::
    Barra de botones de HoloLens 2 horizontal con planchas compartidas
    :::column-end:::
    :::column:::
    Barra de botones de HoloLens 2 vertical con planchas compartidas
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
    Casilla de estilo de Shell de HoloLens 2 32x32mm
    :::column-end:::
    :::column:::
    Modificador de estilo de Shell de HoloLens 2 32x32mm 
    :::column-end:::
    :::column:::
    32x32mm de radio de estilo de Shell de HoloLens 2
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
    Casilla de estilo de Shell de HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    Modificador de estilo de Shell de HoloLens 2 32x96mm
    :::column-end:::
    :::column:::
    32x96mm de radio de estilo de Shell de HoloLens 2
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    ![](../images/button/MRTK_Button_Radial.png) **Radial** radial
    :::column-end:::
    :::column:::
    ![Casilla](../images/button/MRTK_Button_Checkbox.png) **Casilla**
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
    ![](../images/button/MRTK_Button_Base.png)  Botón base del botón
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    Botón de estilo de Shell de la 1ª de HoloLens
    :::column-end:::
    :::column:::
    Botón de redondear forma redondeada
    :::column-end:::
    :::column:::
    Botón Básica
    :::column-end:::
:::row-end:::

`Button`(Assets/MRTK/SDK/Features/UX/interactuable/Prefabs/Button. recurso prefabricado) se basa en el concepto [interactuable](interactable.md) para proporcionar controles de interfaz de usuario sencillos para botones u otros tipos de superficies interactivas. El botón de línea de base admite todos los métodos de entrada disponibles, incluida la entrada de mano articulada para las interacciones cercanas, así como la pulsación + aérea para las interacciones lejanas. También puede usar el comando Voice para desencadenar el botón.

`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2. recurso prefabricado) es el botón de Shell de HoloLens 2 que admite el movimiento preciso del botón para la entrada de seguimiento de la mano directa. Combina `Interactable` script con `PressableButton` script.

En el caso de HoloLens 2, se recomienda usar botones con una placa posterior opaca. No se recomienda usar botones transparentes debido a estos problemas de facilidad de uso y estabilidad:

* El icono y el texto son difíciles de leer con el entorno físico
* Es difícil comprender cuándo se desencadena el evento.
* Los hologramas que se muestran a través de un plano transparente pueden ser inestables con la estabilización LSR de la profundidad de HoloLens 2.

![Botón revestido](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a>Cómo usar los botones que se van a presionar

### <a name="unity-ui-based-buttons"></a>Botones basados en la interfaz de usuario de Unity

Cree un lienzo en la escena (GameObject-> lienzo de > de interfaz de usuario). En el panel Inspector del lienzo:

* Haga clic en "convertir en lienzo MRTK"
* Haga clic en "agregar NearInteractionTouchableUnityUI".
* Establezca la escala X, y y Z del componente de transformación Rect en 0,001

A continuación, arrastre `PressableButtonUnityUI` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonUnityUI. recurso prefabricado), `PressableButtonUnityUICircular` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonUnityUICircular. recurso prefabricado) o `PressableButtonHoloLens2UnityUI` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2UnityUI. recurso prefabricado) en el lienzo.

### <a name="collider-based-buttons"></a>Botones basados en Colisionador

Simplemente arrastre `PressableButtonHoloLens2` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2. recurso prefabricado) o `PressableButtonHoloLens2Unplated` (assets/MRTK/SDK/Features/UX/interactuable/Prefabs/PressableButtonHoloLens2Unplated. recurso prefabricado) en la escena. Estos Prefabs de botón ya están configurados para tener comentarios visuales de audio para los distintos tipos de entradas, incluida la entrada de mano articulada y la mirada.

Los eventos que se exponen en el propio recurso prefabricado, así como el componente [interactuable](interactable.md) , se pueden usar para desencadenar acciones adicionales. Los botones que se van a presionar en la [escena HandInteractionExample](../example-scenes/hand-interaction-examples.md) usan el evento *onclick* del que se pueda interactuar para desencadenar un cambio en el color de un cubo. Este evento se desencadena para los diferentes tipos de métodos de entrada, como, por ejemplo, la tecla de mira, el toque de aire, la mano y las pulsaciones de botones físicos mediante el script de botón que se admite.

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

Puede configurar el momento en el que el botón presionado activa el evento *onclick* a través de `PhysicalPressEventRouter` en el botón. Por ejemplo, puede establecer *onclick* para que se desencadene cuando se presiona el botón por primera vez, en lugar de presionarlo y soltarlo, estableciendo *interactuable en click* to *Event on press*.

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

Para aprovechar la información específica sobre el estado de entrada articulado, puede utilizar los botones que se pueden presionar: Inicio de la *interacción táctil*, *extremo táctil*, *botón presionado*, *botón liberado*. No obstante, estos eventos no se activarán en respuesta a las entradas de punteo de aire, de mano o de ojo. **Para admitir interacciones Near y Far, se recomienda el uso del evento *onclick* del que se pueda interactuar.**

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a>Estados de interacción

En el estado inactivo, la placa frontal del botón no está visible. A medida que se aproxima a un dedo o un cursor de una entrada de mira hacia la superficie, el borde de resplandor de la placa frontal se vuelve visible. Hay un resaltado adicional de la posición del dedo en la superficie de la placa frontal. Cuando se inserta con un dedo, la placa frontal se mueve con el dedo. Cuando el dedo toca la superficie de la placa frontal, muestra un efecto de impulso sutil para proporcionar comentarios visuales del punto táctil.

En el botón de estilo Shell de HoloLens 2, hay muchas indicaciones visuales y prestaciones para aumentar la confianza del usuario en la interacción.

|  ![Luz de proximidad](../images/button/ux_button_affordance_proximitylight.jpg) | ![Resaltado de foco](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Comprimiendo el Cage](../images/button/ux_button_affordance_compression.jpg) | ![Pulso en desencadenador](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| Luz de proximidad | Resaltado de foco | Comprimiendo el Cage | Pulso en desencadenador |

El efecto de impulso sutil se desencadena mediante el botón que se presiona, que busca *ProximityLight (s)* que se encuentren en el puntero que está interactuando actualmente. Si se encuentran luces de proximidad, `ProximityLight.Pulse` se llama al método, que anima automáticamente los parámetros del sombreador para mostrar un pulso.

## <a name="inspector-properties"></a>Propiedades del inspector

![Estructura del botón](../images/button/MRTK_Button_Structure.png)

Colisionador de caja  
 `Box Collider` para la placa frontal del botón.

**Botón Presionable** La lógica para el movimiento del botón con interacción de prensa de mano.

**Enrutador de eventos de prensa física** Este script envía eventos de interacción de [prensa de mano a](interactable.md)interactivos.

**Interactuable** 
 [Interactúable](interactable.md) controla varios tipos de eventos y Estados de interacción. Este script controla directamente la entrada de voz y el gestos de HoloLens, así como la entrada del controlador de movimiento de auriculares envolvente.

**Origen de audio** Origen de audio de Unity para los clips de comentarios de audio.

*NearInteractionTouchable. CS* necesario para que cualquier objeto pueda tocarse con la entrada de mano articulada.

## <a name="prefab-layout"></a>Diseño de recurso prefabricado

El objeto *ButtonContent* contiene la placa frontal, la etiqueta de texto y el icono. El *FrontPlate* responde a la proximidad del alcance del índice mediante el sombreador de *Button_Box* . Muestra bordes iluminados, luz de proximidad y un efecto de impulso en el tacto. La etiqueta de texto se realiza con TextMesh Pro. La visibilidad de *SeeItSayItLabel* se controla mediante el tema del que se pueda [interactuar](interactable.md).

![Diseño del botón](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a>Cómo cambiar el icono y el texto

Los botones de MRTK usan un `ButtonConfigHelper` componente para ayudarle a cambiar el icono, el texto y la etiqueta del botón. (Tenga en cuenta que algunos campos pueden estar ausentes si los elementos no están presentes en el botón seleccionado).

![Aplicación auxiliar de configuración de botones](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a>Crear y modificar conjuntos de iconos

Un **conjunto de iconos** es un conjunto compartido de activos de iconos utilizados por el `ButtonConfigHelper` componente. Se admiten tres *estilos* de icono.

* Los iconos **cuádruples** se representan en un cuádruple mediante `MeshRenderer` . Este es el estilo de icono predeterminado.
* Los iconos de **Sprite** se representan mediante `SpriteRenderer` . Esto resulta útil si prefiere importar los iconos como una hoja de Sprite o si desea que los recursos de icono se compartan con los componentes de la interfaz de usuario de Unity. Para usar este estilo, deberá instalar el paquete de editor de Sprite **(Windows-> administrador de paquetes-> Sprite 2D)** .
* Los iconos **Char** se representan mediante un `TextMeshPro` componente. Esto resulta útil si prefiere usar una fuente de icono. Para usar la fuente del icono de HoloLens, tendrá que crear un `TextMeshPro` recurso de fuente.

Para cambiar el estilo que utiliza el botón, expanda la lista desplegable *iconos* en el ButtonConfigHelper y seleccione en el menú desplegable *estilo de icono* .

Puede crear un nuevo icono de botón con el menú activo: **crear > kit de herramientas de realidad mixta > conjunto de iconos.** Para agregar iconos de cuatro y Sprite, simplemente arrástrelos a sus respectivas matrices. Para agregar iconos de carácter, primero debe crear y asignar un recurso de fuente.

En MRTK 2,4 y versiones posteriores, se recomienda que las texturas de iconos personalizados se muevan a un IconSet.
Para actualizar los recursos de todos los botones de un proyecto al nuevo formato recomendado, use ButtonConfigHelperMigrationHandler.
(Kit de herramientas de realidad mixta-> Utilities-> ventana de migración-> selección de controlador de migración > Microsoft. MixedReality. Toolkit. Utilities. ButtonConfigHelperMigrationHandler)

Importar el paquete Microsoft. MixedRealityToolkit. Unity. Tools necesario para actualizar los botones.

![Cuadro de diálogo Actualizar ventana](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

Si no se encuentra un icono en el conjunto de iconos predeterminado durante la migración, se creará un conjunto de iconos personalizado en MixedRealityToolkit. generated/CustomIconSets. Un cuadro de diálogo indicará que se ha producido.

![Notificación de icono personalizado](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a>Creación de un recurso de fuente de icono de HoloLens

En primer lugar, importe la fuente del icono en Unity. En máquinas Windows, puede encontrar la fuente HoloLens predeterminada en *Windows/Fonts/holomdl2. ttf.* Copie y pegue este archivo en la carpeta assets.

A continuación, abra el creador del recurso TextMeshPro Font a través de la **ventana > TextMeshPro > Font Asset Creator.** Esta es la configuración recomendada para generar un Atlas de fuentes HoloLens. Para incluir todos los iconos, pegue el siguiente intervalo Unicode en el campo *secuencia de caracteres* :

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creación de botón 1](../images/button/MRTK_Font_Asset_Creation_1.png)

Una vez generado el recurso de fuente, guárdelo en el proyecto y asígnelo al campo de *fuente del icono de char* del conjunto de iconos. Ahora se rellenará la lista desplegable de *iconos disponibles* . Para hacer que un icono esté disponible para que lo use un botón, haga clic en él. Se agregará a la lista desplegable de *iconos seleccionados* y ahora se mostrará en el `ButtonConfigHelper.` , de manera opcional, puede asignarle el icono a una etiqueta. Esto permite establecer el icono en tiempo de ejecución.

![Creación de botón 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creación de botón 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

Para usar el conjunto de iconos, seleccione un botón, expanda la lista desplegable iconos en el `ButtonConfigHelper` y asígnelo al campo *conjunto de iconos* .

![Conjunto de iconos de botón](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a>Cómo cambiar el tamaño de un botón

El tamaño del botón de estilo de Shell de HoloLens 2 es 32x32mm. Para personalizar la dimensión, cambie el tamaño de estos objetos en el botón recurso prefabricado:

1. **FrontPlate**
2. **Cuádruple** debajo del fondo
3. **Colisionador de Box** en la raíz

A continuación, haga clic en el botón **corregir límites** del script NearInteractionTouchable que se encuentra en la raíz del botón.

Actualiza el tamaño de la ![ Personalización del tamaño del botón de FrontPlate 1](../images/button/MRTK_Button_SizeCustomization1.png)

Actualizar el tamaño de la ![ Personalización de tamaño de botón cuádruple 2](../images/button/MRTK_Button_SizeCustomization2.png)

Actualiza el tamaño de la personalización del tamaño del botón del Colisionador de caja ![ 3](../images/button/MRTK_Button_SizeCustomization3.png)

Haga clic en el botón "corregir límites" ![ Personalización de tamaño 4](../images/button/MRTK_Button_SizeCustomization4.png)

## <a name="voice-command-see-it-say-it&quot;></a>Comando de voz (&quot;ver, por ejemplo, ti")

**Controlador de entrada de voz** El script [interactuable](interactable.md) en el botón Presionable ya implementa `IMixedRealitySpeechHandler` . Aquí puede establecerse una palabra clave de comando de voz.

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

**Perfil de entrada de voz** Además, debe registrar la palabra clave de comando de voz en el *perfil* global de comandos de voz.

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

**Ver, por ejemplo, etiqueta de ti** El botón pressable recurso prefabricado tiene una etiqueta de marcador de posición TextMesh Pro en el objeto *SeeItSayItLabel* . Puede usar esta etiqueta para comunicar la palabra clave de comando de voz del botón al usuario.

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a>Cómo crear un botón desde cero

Puede encontrar ejemplos de estos botones en la escena de **PressableButtonExample** .

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a>1. crear un botón que se presione con Cube (solo interacción cercana)

1. Crear un cubo de Unity (GameObject > objeto 3D > cubo)
2. Agregar `PressableButton.cs` script
3. Agregar `NearInteractionTouchable.cs` script

En el `PressableButton` panel Inspector del, asigne el objeto de cubo a los objetos **visuales del botón de movimiento**.

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

Al seleccionar el cubo, verá varias capas de color en el objeto. Esto visualiza los valores de distancia en la **configuración de Press**. Mediante el uso de los identificadores, puede configurar Cuándo se debe iniciar la pulsación (movimiento del objeto) y cuándo se desencadenará el evento.

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

Cuando se presiona el botón, se mueven y generan los eventos adecuados que se exponen en el script, como `PressableButton.cs` TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased ().

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a>Solución de problemas

Si el botón está ejecutando una doble presión, asegúrese de que la propiedad aplicar la entrada **delantera** está activa y de que el plano de **distancia de inicio** se coloca delante del plano táctil de la **interacción cercana** . El plano **táctil cercano** a la interacción se indica mediante el plano azul colocado delante del origen de la flecha blanca en el GIF siguiente:

![Componente de script de botón que se admite con la propiedad aplicar Front-out resaltada](../images/button/MRTK_Button_Enforce_Push.png)

![Ejemplo animado de movimiento de la distancia de la pulsación inicial delante del plano táctil de la interacción cercana](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a>2. agregar comentarios visuales al botón básico del cubo

El sombreador estándar de MRTK proporciona varias características que facilitan la adición de comentarios visuales. Cree un material y seleccione Shader `Mixed Reality Toolkit/Standard` . O bien, puede usar o duplicar uno de los materiales existentes en `/SDK/StandardAssets/Materials/` que usa el sombreador estándar de MRTK.

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

Active `Hover Light` y `Proximity Light` en **Opciones fluidas**. Esto permite que los comentarios visuales se intermuevan a la mano (luz de proximidad) y a las interacciones de puntero lejano (luz de desplazamiento).

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a>3. agregar comentarios de audio al botón básico del cubo

Puesto que el `PressableButton.cs` script expone eventos como TouchBegin (), TouchEnd (), ButtonPressed (), ButtonReleased (), se pueden asignar fácilmente comentarios de audio. Simplemente agregue Unity `Audio Source` al objeto de cubo y, a continuación, asigne los clips de audio seleccionando AudioSource. PlayOneShot (). Puede usar MRTK_Select_Main y MRTK_Select_Secondary clips de audio en `/SDK/StandardAssets/Audio/` carpeta.

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a>4. agregar Estados visuales y controlar eventos de interacción lejana

[Interactúable](interactable.md) es un script que facilita la creación de un estado visual para los distintos tipos de interacciones de entrada. También controla los eventos de interacción Far. Agregue `Interactable.cs` y arrastre y coloque el objeto de cubo en el campo de **destino** en **perfiles**. A continuación, cree un nuevo tema con un tipo **ScaleOffsetColorTheme**. En este tema, puede especificar el color del objeto para los Estados de interacción específicos, como el **foco** y **presionado**. También puede controlar la escala y el desplazamiento. Compruebe la **aceleración** y establezca la duración para que la transición visual sea fluida.

![Seleccionar tema de perfil](../images/button/mrtk_button_profiles.gif)

Verá que el objeto responde a interacciones lejanas (cursor de mano o hacia abajo) y Near (mano).

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a>Ejemplos de botones personalizados

En la [escena de HandInteractionExample](../example-scenes/hand-interaction-examples.md), vea los ejemplos de los botones de piano y redondo que usan `PressableButton` .

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

Cada clave de piano tiene un `PressableButton` y un `NearInteractionTouchable` script asignado. Es importante comprobar que la dirección de *avance local* de `NearInteractionTouchable` es correcta. Se representa mediante una flecha blanca en el editor. Asegúrese de que la flecha apunta fuera de la cara frontal del botón:

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a>Consulte también

* [Interactuable](interactable.md)
* [Temas visuales](visual-themes.md)
