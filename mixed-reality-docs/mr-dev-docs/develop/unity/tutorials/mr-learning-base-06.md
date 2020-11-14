---
title: 'Tutoriales de introducción: 6. Creación de interfaces de usuario'
description: En este curso se muestra cómo usar Mixed Reality Toolkit (MRTK) para crear interfaces de usuario.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 2d3a826ba3bf8fdf1299038a7964278f0d57dbb7
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353543"
---
# <a name="6-creating-user-interfaces"></a>6. Creación de interfaces de usuario

## <a name="overview"></a>Introducción

En este tutorial, obtendrá información sobre cómo crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú de MRTK junto con el componente TextMeshPro de Unity. También aprenderá a configurar los botones para desencadenar eventos y agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar a los usuarios información adicional.

## <a name="objectives"></a>Objetivos

* Aprender a organizar los botones de una colección
* Aprender a usar los elementos prefabricados de menú de MRTK
* Aprender a interactuar con hologramas mediante botones y elementos de la interfaz de usuario
* Aprender a agregar elementos de texto
* Aprender a generar información sobre herramientas en objetos dinámicamente

## <a name="creating-a-static-panel-of-buttons"></a>Creación de un panel estático de botones

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **RoverExplorer** y seleccione **Create Empty** ( Crear vacío)para agregar un objeto vacío como elemento secundario de RoverExplorer, asigne el nombre **Buttons** al objeto y configure el componente **Transform** (Transformación) como se indica a continuación:

* **Posición** : X = 0.6, Y = 0.036, Z = 0.5
* **Rotación** : X = 90, Y = 0, Z = 0
* **Escala** : X = 1, Y = 1, Z = 1

![Unity con el objeto Buttons recién creado seleccionado y colocado](images/mr-learning-base/base-06-section1-step1-1.png)

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** , haga clic y arrastre el elemento prefabricado **PressableRoundButton** sobre el objeto **Buttons** y, a continuación, haga clic con el botón derecho en PressableRoundButton, seleccione **Duplicate** (Duplicar) para crear una copia y repita el proceso hasta que tenga un total de tres objetos PressableRoundButton:

![Unity con los objetos prefabricados PressableRoundButton recién agregados](images/mr-learning-base/base-06-section1-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **Buttons** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **GridObjectCollection** y configúrelo del modo siguiente:

* **Tipo de orden** : Orden secundario
* **Diseño** : Horizontal
* **Ancho de celda** : 0.2
* **Ancla** : Centro a la izquierda

A continuación, haga clic en el botón **Update Collection** (Actualizar colección) para actualizar la posición de los objetos secundarios del objeto Buttons:

![Objeto Buttons de Unity con el componente GridObjectCollection agregado, configurado y aplicado](images/mr-learning-base/base-06-section1-step1-3.png)

En la ventana Hierarchy (Jerarquía), asigne el nombre **Hints** , **Explode** y **Reset** a los botones.

Para cada botón, seleccione el objeto secundario **SeeItSayItLabel** > **TextMeshPro** y, a continuación, en la ventana Inspector, cambie el texto del componente **TextMeshPro - Text** respectivo para que coincida con los nombres de los botones:

![Unity con etiquetas de texto de botón configuradas](images/mr-learning-base/base-06-section1-step1-4.png)

Una vez hecho esto, contraiga los objetos secundarios del objeto Buttons.

En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Hints** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:

* Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No function** (Ninguna función), seleccione **PlacementHintsController** > **TogglePlacementHints ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del objeto de botón Hints configurado](images/mr-learning-base/base-06-section1-step1-5.png)

En la ventana Hierarchy (Jerarquí)a, seleccione el objeto del botón **Explode** y, a continuación, en la ventana Inspector, configure el evento **OnClick ()** de la siguiente manera:

* Asigne el objeto **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No function** (Ninguna función), seleccione **ExplodedViewController** > **ToggleExplodedView ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del objeto de botón Explode configurado](images/mr-learning-base/base-06-section1-step1-6.png)

Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionada la barra espaciadora para activar la mano y use el mouse para presionar el botón **Hints** para activar y desactivar la visibilidad de los objetos de sugerencia de colocación:

![Vista dividida del modo de reproducción de Unity con el botón Hints presionado](images/mr-learning-base/base-06-section1-step1-7.png)

y el botón **Explode** para activar y desactivar la vista seccionada:

![Vista dividida del modo de reproducción de Unity con el botón Explode presionado](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Creación de un menú dinámico que sigue al usuario

En la ventana Proyecto, vaya a la carpeta **Recursos** > **MRTK** > **SDK** > **Características** > **Experiencia del usuario** > **Prefabs (Elementos prefabricados)**  > **Menús** , haga clic y arrastre el elemento prefabricado **NearMenu4x1** en la ventana Jerarquía, establezca su **posición** de transformación en X = 0, Y = -0.4, Z = 0 y configúrelo de la forma siguiente:

* Compruebe que el **Tracked Target Type** (Tipo de objetivo de seguimiento) del componente **SolverHandler** esté establecido en **Head** (Cabeza).
* Marque la casilla junto al componente **RadialView** del solucionador para que esté habilitado de forma predeterminada

![Unity con el objeto prefabricado Menu recién agregado seleccionado](images/mr-learning-base/base-06-section2-step1-1.png)

En la ventana Hierarchy (Jerarquía), cambie el nombre del objeto a **Menu** y, a continuación, expanda el objeto secundario **ButtonCollection** para mostrar los cuatro botones:

![Unity con el objeto Menu seleccionado y el objeto ButtonCollection expandido](images/mr-learning-base/base-06-section2-step1-2.png)

Cambie el nombre del primer botón por **Indicator** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:

* Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.
* Asigne el objeto **Indicator** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Compruebe que la casilla del argumento esté **activada**.
* Cambie el **icono** al icono de "búsqueda".

![Unity con el objeto de botón Indicator con Button Config Helper configurado](images/mr-learning-base/base-06-section2-step1-3.png)

En la ventana Jerarquía, seleccione el objeto **Indicador** y, a continuación, en la ventana del Inspector:

* Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.
* Use el botón **Agregar componente** para agregar el componente **Controlador del indicador de dirección (Script)** .

![Unity con el objeto Indicator seleccionado, deshabilitado, y el componente DirectionalIndicatorController agregado](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Ahora, cuando se inicia la aplicación, el objeto Indicator está deshabilitado de forma predeterminada y se puede habilitar presionando el botón Indicator.

Cambie el nombre del segundo botón por **TapToPlace** y, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (Script)** (Asistente de configuración del botón [script]) de la siguiente manera:

* Cambie el **texto de la etiqueta principal** para que coincida con el nombre del botón.
* Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Compruebe que la casilla del argumento esté **activada**.
* Cambie el **icono** al icono de "mano con rayo".

![Unity con el objeto de botón TapToPlace con Button Config Helper configurado](images/mr-learning-base/base-06-section2-step1-5.png)

En la ventana Jerarquía, seleccione el objeto **RoverAssembly** y, a continuación, en la ventana Inspector, configure el componente **Tap To Place (Script)** (Pulsar para colocar [Script]) del modo siguiente:

* Desactive la casilla situada junto a su nombre para que esté inactivo de forma predeterminada.
* En la sección del evento **On Placing Stopped ()** , haga clic en el icono **+** para agregar un nuevo evento:
* Asigne el objeto RoverExplorer > **RoverAssembly** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool Enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Compruebe que la casilla del argumento esté **desactivada**.

![Unity con el componente TapToPlace reconfigurado](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Ahora, cuando se inicia la aplicación, la funcionalidad Tap to Place (Tocar para colocar) está deshabilitada de forma predeterminada y se puede habilitar presionando el botón Tap to Place. Además, cuando se complete la acción de tocar para colocar, se deshabilitará.

## <a name="adding-text-to-the-scene"></a>Agregación de texto a la escena

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en el objeto **Table** (Tabla) y seleccione **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para agregar un objeto de texto como elemento secundario del objeto Table y, a continuación, en la ventana Inspector, configure el componente **Rect Transform** (Transformación rectangular) como se indica a continuación:

* Cambie **Pos Y** (Posición Y) a 1.
* Cambie **Width** (Ancho) a 1.
* Cambie **Height** (Altura) a 1.
* Cambie **Rotation X** (Rotación X) a 90.

![Unity con el objeto TextMeshPro recién creado seleccionado](images/mr-learning-base/base-06-section3-step1-1.png)

A continuación, configure el componente **TextMeshPro - Text** como se indica a continuación:

* Cambie **Text** (Texto) a Rover Explorer.
* Cambie **Font Style** (Estilo de fuente) a Bold (Negrita).
* Cambie **Font Size** (Tamaño de fuente) a 1.
* Cambie Extra Settings > **Margins** (Configuración adicional > Márgenes) a 0.03.

![Unity con el componente TextMeshPro configurado](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Agregación de información sobre herramientas

En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** para buscar los objetos prefabricados de información sobre herramientas:

![Ventana Project (Proyecto) de Unity con la carpeta ToolTips seleccionada](images/mr-learning-base/base-06-section4-step1-1.png)

En la ventana Hierarchy (Jerarquía), expanda el objeto RoverExplorer > **RoverParts** y seleccione todos los objetos secundarios de partes, y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **ToolTipSpawner** y configúrelo de la forma siguiente:

* Asegúrese de que la casilla de verificación **Focus enabled** (Enfoque habilitado) está activada para requerir que el usuario mire la parte para que aparezca la información sobre herramientas.
* Asigne el elemento prefabricado **Simple Line ToolTip** (Información sobre herramientas de línea simple) desde la ventana Project (Proyecto) al campo **Tool Tip Prefab** (Elemento prefabricado de información de herramientas).
* Cambie ToolTip Override Settings > **Settings Mode** (Configuración de invalidación de información sobre herramientas > Modo de configuración) a **Override** (Invalidar).
* Cambie ToolTip Override Settings > **Manual Pivot Local Position Y** (Configuración de invalidación de información sobre herramientas > Posición Y local del pivote manual) a **1.5**.

![Unity con todos los objetos de partes del róver seleccionados y el componente ToolTipSpawner agregado y configurado](images/mr-learning-base/base-06-section4-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione la primera parte del rover, RoverParts > **Camera_Part** y configure el componente **ToolTipSpawner** como se indica a continuación:

* Cambie **Tool Tip Text** para reflejar el nombre de la parte; por ejemplo, **Camera**.

![Unity con ToolTipText Camera configurado](images/mr-learning-base/base-06-section4-step1-3.png)

**Repita** este paso para cada uno de los objetos de parte del rover para configurar el componente **ToolTipSpawner** como se indica a continuación:

* Para **Generator_Part** , cambie **Tool Tip Text** a **Generator**.
* Para **Lights_Part** , cambie **Tool Tip Text** a **Lights**.
* Para **UHFAntenna_Part** , cambie **Tool Tip Text** a **UHF Antenna**.
* Para **Spectrometer_Part** , cambie **Tool Tip Text** a **Spectrometer**.

Presione el botón Play (Reproducir) para entrar en el modo de juego y, a continuación, mantenga presionado el botón derecho del mouse mientras mueve el mouse hasta que la mirada entre en contacto con una de las partes y la información sobre herramientas de la parte se mostrará:

![Vista dividida del modo de reproducción de Unity con información sobre herramientas desencadenada por la mirada](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a crear una interfaz de usuario sencilla con los elementos prefabricados de botón y menú proporcionados por MRTK junto con el componente TextMeshPro de Unity y a configurar los botones para desencadenar eventos cuando se presionan. También ha aprendido a agregar elementos dinámicos de información sobre herramientas en la interfaz de usuario para proporcionar información adicional al usuario.

[Tutorial siguiente: 7. Interacción con objetos 3D](mr-learning-base-07.md)