---
title: 5. Adición de un botón y restablecimiento de la ubicación de las piezas
description: Parte 5 de 6 de una serie de tutoriales para crear una aplicación de ajedrez sencilla con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 08/14/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: f903848b8d5c9c1dccfc00cd7bd6d16d2e491a5e
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679844"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a>5. Adición de un botón y restablecimiento de la ubicación de las piezas


## <a name="overview"></a>Introducción

En el tutorial anterior, agregó actores de interacción manual a los componentes Peón y Manipulador en el tablero de ajedrez para que fueran interactivos. En esta sección, continuará trabajando con el complemento UX Tools de Mixed Reality Toolkit compilando las características de la aplicación de ajedrez. Esto incluye la creación de una nueva función y el aprendizaje sobre cómo obtener referencias a actores en un plano técnico. Al final de esta sección, estará listo para empaquetar e implementar la aplicación de realidad mixta en un dispositivo o emulador.

## <a name="objectives"></a>Objetivos

* Adición de un botón interactivo
* Creación de una función para restablecer la ubicación de las piezas
* Enlace del botón para que desencadene la función cuando se presione

## <a name="creating-a-reset-function"></a>Creación de una función de restablecimiento
La primera tarea consiste en crear un plano técnico de función que reestablezca una pieza de ajedrez a su posición original en la escena. 

1.  Abra **WhiteKing**, haga clic en el icono **+** situado junto a la sección **Functions** (Funciones) de **My Blueprint** (Mi plano técnico) y asígnele el nombre **Reset Location**. 

2.  Arrastre la ejecución desde **Reset Location** y suéltela en la cuadrícula del plano técnico para crear un nodo **SetActorRelativeTransform**. 
    * Esta función define la transformación (ubicación, rotación y escala) de un actor en relación con su elemento principal. Usará esta función para restablecer la posición del rey en el tablero, incluso si la posición original del tablero ha cambiado. 
    
3. Haga clic con el botón derecho en el gráfico de eventos, seleccione **Make Transform** (Realizar transformación) y cambie su **Location** (Ubicación) a **X =-26**, **Y = 4**, **Z = 0**.
    * Conecte su **Return Value** (Valor devuelto) a la marca de **New Relative Transform** (Nueva transformación relativa) en **SetActorRelativeTransform**. 

![Función Reset Location (Restablecer ubicación)](images/unreal-uxt/5-function.PNG)

**Compile** y **guarde** el proyecto antes de volver a la ventana principal. 


## <a name="adding-a-button"></a>Agregar un botón
Ahora que la función está configurada correctamente, la siguiente tarea consiste en crear un botón que la desencadene cuando se toque. 


1.  Haga clic en **Agregar nuevo > Blueprint Class (Clase de plano técnico)** , expanda la sección **Todas las clases** y busque **SimpleButton**. 
    * Asigne a este botón el nombre **ResetButton** y haga doble clic para abrir el plano técnico.

> [!NOTE]
> **BP_ButtonHoloLens2** es un actor de plano técnico de botón 3D que forma parte del complemento UX Tools.

![Subclase del nuevo plano técnico del botón de estilo HoloLens 2](images/unreal-uxt/5-subclass.PNG)

2. Asegúrese de que la opción **ResetButton(self)** está seleccionada en el panel **Componentes**. En el panel **Detalles**, desplácese hasta la sección **Botón**. Cambie el valor **Etiqueta de botón** predeterminado a "Restablecer". Expanda la sección **Button Icon Brush** (Pincel de icono del botón ) y presione el botón **Open Icon Brush Editor** (Abrir editor del pincel de icono). 

![Establecimiento de la etiqueta y el icono en el botón](images/unreal-uxt/5-buttonconfig.PNG)

Se abrirá Icon Brush Editor (Editor del pincel de icono), que es una utilidad que proporciona el complemento UX Tools y que puede usar para seleccionar un icono nuevo para el botón. 

![Selección de un icono para el botón](images/unreal-uxt/5-iconbrusheditor.PNG)

Hay muchas otras opciones de configuración que puede ajustar para configurar el botón. Para obtener más información acerca del componente UXT Pressable Button, consulte la [documentación](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).

3. Haga clic en **PressableButton (Inherited)** [PressableButton (heredado)] del panel **Componentes** y desplácese hacia abajo en el panel **Detalles** hasta la sección **Eventos**. 
    * Haga clic en el botón verde **+** situado junto a **On Button Pressed** (Al presionar un botón) para agregar un evento al gráfico de eventos, que se llamará cuando se presione el botón. 
    
Desde aquí, llamará a la función **Reset Location** de **WhiteKing**, que necesita una referencia al actor **WhiteKing** en el nivel. 

4.  En el panel **My Blueprint** (My plano técnico), vaya a la sección **Variables**, haga clic en el botón **+** y asigne a la variable el nombre **WhiteKing**. 
    * En el panel **Details** (Detalles), seleccione la lista desplegable situada junto a **Variable Type** (Tipo de variable), busque **WhiteKing** y seleccione **Object Reference** (Referencia de objetos). 
    * Marque la casilla situada junto a **Instance Editable** (Instance editable). Esto permitirá que la variable se defina desde el nivel principal. 

![Crear una variable](images/unreal-uxt/5-var.PNG)

5.  Arrastre la variable de WhiteKing desde **My Blueprint > Variables** (Mi plano técnico > Variables) hasta el gráfico de eventos del botón de restablecimiento y elija **Get WhiteKing** (Obtener WhiteKing). 

## <a name="firing-the-function"></a>Activación de la función
Lo único que queda es activar oficialmente la función de restablecimiento cuando se presiona el botón.

1.  Arrastra la marca de salida de WhiteKing y suéltala para colocar un nodo nuevo. Selecciona la función **Reset Location** (Restaurar ubicación). Por último, arrastra la marca de ejecución de salida de **On Button Pressed** (Al presionar un botón) a la marca de ejecución de entrada de **Reset Location** (Restablecer ubicación). **Compila** y **guarda** el plano técnico ResetButton y, a continuación, vuelve a la ventana principal. 

![Llamar a la función Reset Location (Restablecer ubicación) desde On Button Pressed (Al presionar un botón)](images/unreal-uxt/5-callresetloc.PNG)

2.  Arrastre **ResetButton** a la ventanilla y establezca su ubicación en **X = 50**, **Y =-25** y **Z = 10**. Establezca su rotación en **Z = 180**. En **Default** (Valor predeterminado), establezca el valor de la variable **WhiteKing** en **WhiteKing**.

![Definir la variable](images/unreal-uxt/5-buttonlevel.PNG)

Ejecute la aplicación, mueva la pieza de ajedrez a una nueva ubicación y presione el botón de estilo HoloLens 2 para ver la lógica de restablecimiento en acción.

Ahora tiene una aplicación de realidad mixta con un tablero y una pieza de ajedrez con los que puede interactuar, así como un botón totalmente funcional que restablecerá la ubicación de la pieza. Puede encontrar la aplicación completada hasta este momento en su repositorio de [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp). No dude en profundizar más allá de este tutorial y configurar el resto de las piezas de ajedrez de modo que se restablezca todo el tablero cuando se presione el botón.

![Escena final en la ventanilla](images/unreal-uxt/5-endscene.PNG)

Está listo para pasar a la sección final de este tutorial, donde aprenderá a empaquetar e implementar correctamente la aplicación en un dispositivo o emulador.

> [!IMPORTANT]
> En este punto, debe actualizar el proyecto con la **[configuración de rendimiento de Unreal](../performance-recommendations-for-unreal.md)** recomendada antes de implementar la aplicación en un dispositivo o emulador.

[Sección siguiente: 6. Empaquetado y implementación en el dispositivo o emulador](unreal-uxt-ch6.md)
