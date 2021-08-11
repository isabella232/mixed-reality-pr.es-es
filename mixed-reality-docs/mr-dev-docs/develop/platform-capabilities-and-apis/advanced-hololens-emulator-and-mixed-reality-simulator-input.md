---
title: Simulador HoloLens Emulator y Mixed Reality avanzado
description: Instrucciones detalladas para usar el teclado, el mouse y el controlador de Xbox para simular la entrada del HoloLens Emulator y Windows Mixed Reality simulador.
author: pbarnettms
ms.author: pbarnett
ms.date: 06/8/2020
ms.topic: article
keywords: HoloLens, Emulator, simulación, Windows Mixed Reality, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: a4e66b2738d5f89949b14fd6f901e2b30dc38cd9e02072f640345d374b9eb9fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217131"
---
# <a name="advanced-hololens-emulator-and-mixed-reality-simulator-input"></a>Introducción de datos avanzada en el emulador de HoloLens y el simulador de realidad mixta

La mayoría de los usuarios del emulador solo necesitarán usar los controles de entrada básicos [para](using-the-hololens-emulator.md#basic-emulator-input) el HoloLens Emulator o [Windows Mixed Reality simulador](using-the-windows-mixed-reality-simulator.md#basic-simulator-input). Los detalles siguientes son para los usuarios avanzados que han encontrado la necesidad de simular tipos de entrada más complejos.

## <a name="concepts"></a>Conceptos

Para empezar a controlar la entrada virtual en el simulador HoloLens Emulator y Windows Mixed Reality, primero debe comprender algunos conceptos.

El movimiento hace referencia a controlar y cambiar la posición y la orientación de algo en la escena. Para un objeto controlable de destino, el movimiento se controla con rotación y traducción (movimiento) a lo largo de tres ejes.
* **Yaw:** girar a la izquierda o a la derecha.
* **Pitch**: subir o bajar.
* Roll: roll side-to-side **(Roll:** roll-to-side).
* **X:** mover a la izquierda o a la derecha.
* **Y:** subir o bajar.
* **Z:** avanzar o retroceder.

La entrada del controlador de movimiento y el gesto se asignan estrechamente a los dispositivos físicos:
* **Acción:** simula la acción de presionar el índice en el control o de extraer el botón de acción en un controlador. Por ejemplo, la entrada Acción se puede usar para simular el gesto de pulsar el aire, desplazarse por el contenido y presionar y mantener presionado.
* **[Gesto](../../design/system-gesture.md#bloom)de Bloom/Sistema** o Inicio: el HoloLens gesto de bloom/sistema o el botón Inicio de un controlador se usa para volver al shell y para iniciar acciones del sistema.

Las manos tienen una representación enriquez en HoloLens 2.  Además de que se realiza un seguimiento o no se realiza un seguimiento y se puede usar para impulsar gestos, las manos ahora tienen un modelo de esqueleto articulado que se ajusta a ellos y se expone al desarrollador.  El modelo de esqueleto tiene 26 puntos de seguimiento en cada mano.  
* **Conjunto:** una de las 20 posiciones de seguimiento de una mano determinada con seguimiento con un punto asociado en un espacio 3d.
* **Pose:** colección completa de todas las uniones en una mano con seguimiento, 26 juntas en total. 

Actualmente no se expone el control directo de posiciones conjuntas individuales a través del emulador, pero se pueden establecer a través de la API de simulación. Tenemos un conjunto de poses representativas útiles que el emulador le permite alternar entre ellos.

También puede controlar el estado de la entrada del sensor simulado:
* **Restablecer:** devuelve todos los sensores simulados a sus valores predeterminados.  A partir del HoloLens 2 Emulator, un restablecimiento se puede establecer en una o ambas manos. Atrape las manos deseadas mediante las teclas modificadoras o los botones (Alt izquierdo o derecho, o el parachoques izquierdo o derecho del mando).
* **Seguimiento:** recorrerá los modos de seguimiento posicional, incluidos:
  * **Valor** predeterminado: el sistema operativo elige el mejor modo de seguimiento en función de las solicitudes realizadas del sistema.
   * **Orientación:** fuerza el seguimiento de solo orientación, independientemente de las solicitudes del sistema.
   * **Posicional:** fuerza el seguimiento posicional, independientemente de las solicitudes del sistema.

## <a name="types-of-input"></a>Tipos de entrada

En la tabla siguiente se muestra cómo se asigna cada tipo de entrada al teclado, el mouse y el controlador de Xbox. Cada tipo tiene una asignación diferente en función del modo de control de entrada. Puede encontrar más información sobre los modos de control de entrada más adelante en este documento.

| Entrada |  Keyboard |  Mouse |  Controlador de Xbox | 
|----------|----------|----------|----------|
|  Desvío |  Flechas izquierdas y derechas |  Arrastrar izquierda/derecha |  Huella digital derecha izquierda/derecha | 
|  Inclinación |  Flechas arriba y abajo |  Arrastrar hacia arriba o hacia abajo |  Flecha derecha hacia arriba y hacia abajo | 
|  Rodillo |  Q/E |  |  DPad izquierda/derecha | 
|  X |  A/D |  |  Huella digital izquierda izquierda/derecha | 
|  Y |  Página anterior/página abajo |  |  DPad arriba o abajo | 
|  Z |  W/S |  |  Flecha izquierda hacia arriba o hacia abajo | 
|  Acción |  Escriba o espacio. |  Botón derecho |  Un botón o un desencadenador | 
|  Bloom/System |  F2 o Windows clave |  |  Botón B | 
|  Botón de control del controlador/control de la mano |  G  |  |  | 
|  Botón de menú Controlador |  M  |  |  | 
|  Touchpad touch del controlador |  U  |  |  | 
|  Presione el panel táctil del controlador. |  P  |  |  | 
|  Presión de la huella digital del controlador |  K  |  |  | 
|  Estado de seguimiento del controlador izquierdo |  F9 |  |  | 
|  Estado de seguimiento del controlador correcto |  F10 |  |  | 
|  Posición "Cerrar" de la mano | 7 |  |  |
|  Posición "Abrir" con la mano (valor predeterminado) | 8 |  |  |
|  Posición "Punto" de la mano | 9 |  |  |
|  Posición "Acercar" de la mano | 0 |  |  |
|  Reset |  Clave de escape |  |  Botón Iniciar | 
|  Seguimiento |  T o F3 |  |  Botón X | 


Nota: Los botones del controlador se pueden dirigir a una mano o controlador u otra mediante los modificadores de destino de la mano.

## <a name="targeting"></a>Establecer destinos 

Algunos de los conceptos de entrada anteriores son propios.  Action, Bloom/System, Reset y Tracking son conceptos completos, no necesitan y no se ven afectados por ningún modificador adicional para el destino.  Los conceptos restantes se pueden aplicar a uno de varios destinos. Hemos introducido formas de especificar a qué destino se debe aplicar el comando.  En todos los casos, es posible especificar a través de la interfaz de usuario o mediante pulsaciones de teclado, qué objeto se va a dirigir.  En algunos casos, también es posible especificar con el controlador de Xbox directamente. 

En la tabla siguiente se describen las opciones de destino y la manera de activar cada una de ellas.

| Objeto | Modificador de teclado | Modificador de controlador | Emulator Modificador de interfaz de usuario |
|----------|----------|----------|----------|
| Cuerpo | (predeterminado). | (predeterminado). | (predeterminado). |
| Head | Mantener presionada la H | (No disponible) | (No disponible) |
| Mano izquierda/controlador | Mantener presionado el botón Alt izquierdo | Botón Mantener presionado el botón de botón de mano izquierda | Left-Hand de inserción | 
| Mano derecha/controlador | Mantener presionado el botón Alt a la derecha | Botón Mantener a la derecha el botón de botón | Right-Hand de inserción |
| Ojos | Mantener presionada la Y | (No disponible) | Chin de ojos |
  
En la tabla siguiente se muestra cómo cada modificador de destino asigna cada uno de los conceptos de entrada de movimiento principal.

| Entrada | Valor predeterminado (cuerpo) |  Mano o controlador (mantenga presionada la tecla Alt, mantenga presionado el botón de botón del controlador de juego o presione la tecla de alternancia de la interfaz de usuario) |  Head (Hold H)  |  Ojos (mantener presionada la tecla Y o alternar el botón de inserción de la interfaz de usuario) |
|----------|----------|----------|----------|----------|
|  Desvío |  Girar el cuerpo a la izquierda o derecha |  Mover la mano a la izquierda o derecha |  Girar la cabeza a la izquierda o a la derecha | La mirada con los ojos parece izquierda/derecha |
|  Inclinación |  Subir o bajar |  Mover la mano hacia arriba y hacia abajo |  Subir o bajar la cabeza | Mirada con los ojos hacia arriba y hacia abajo | 
|  Rodillo |  Lanzamiento de la cabeza a la izquierda o derecha |  |  Lanzamiento de la cabeza a la izquierda o derecha | (Sin acción) |
|  X |  Cuerpo de la diapositiva a la izquierda o derecha |  Mover la mano/controlador izquierda/derecha |  Girar la cabeza a la izquierda o a la derecha | (Sin acción) |
|  Y |  Mover el cuerpo hacia arriba y hacia abajo |  Mover la mano o el controlador hacia arriba y hacia abajo |  Subir o bajar | (Sin acción) |
|  Z |  Mover el cuerpo hacia delante o hacia atrás |  Mover la mano/controlador hacia delante o hacia atrás |  Subir o bajar | (Sin acción) |
 
 
## <a name="controlling-an-app"></a>Control de una aplicación

Se sugiere el siguiente conjunto de controles para su uso diario:

|  Operación |  Teclado y mouse |  Controller | 
|----------|----------|----------|
|  Cuerpo X |  A/D |  Clic de posición izquierda izquierda/derecha | 
|  Cuerpo Y |  Página anterior/página hacia abajo |  DPad arriba o abajo | 
|  Cuerpo Z |  W/S |  Flecha izquierda hacia arriba y hacia abajo | 
|  Body Yaw |  Arrastrar el mouse a la izquierda o a la derecha |  Dedo índice derecho a la izquierda o derecha | 
|  Head Yaw |  H + arrastrar el mouse a la izquierda o derecha |  H (en el teclado) + barra de posición derecha izquierda/derecha | 
|  Inclinación de la cabeza |  Arrastrar el mouse hacia arriba o hacia abajo |  Flecha derecha hacia arriba o hacia abajo | 
|  Lanzamiento de la cabeza |  Q/E |  DPad a la izquierda o derecha | 
|  Hand/Controller X |  Alt + A/ D |  Botones + flecha izquierda izquierda/derecha | 
|  Hand/Controller Y |  Alt + Página anterior/ página abajo |  Flecha arriba y abajo de DPad | 
|  Mano/controlador Z |  Alt + W/ S |  Flecha arriba y abajo con el botón de control izquierdo | 
|  Hand/Controller Yaw |  Alt + arrastrar el mouse a la izquierda o derecha |  Botones y dedo parado derecho a la izquierda o derecha | 
|  Paso de mano/controlador |  Alt + arrastrar el mouse hacia arriba o hacia abajo |  Flecha arriba o abajo con el botón derecho | 
|  Hand/Controller Roll |  Alt + Q / E |  Cuello + DPad a la izquierda o derecha | 
|  Acción |  Botón derecho del mouse |  Desencadenador | 
|  Bloom/System/Home |  Tecla F2 o Windows clave |  Botón B | 
|  Reset |  Escape |  Botón Iniciar | 
|  Seguimiento |  T |  Botón X | 
|  Desplazamiento |  Alt + botón derecho del mouse + arrastrar el mouse hacia arriba o hacia abajo |  Flecha arriba y abajo + desenlazador + desenlazador derecho | 
|  Mover o girar más rápido | Tecla Mayús izquierda o derecha | Mantenga presionado el botón de control derecho. |
|  Mover o girar lentamente | Tecla Ctrl izquierda o derecha | Mantenga presionado el botón de posición izquierdo. |

## <a name="using-a-windows-mixed-reality-immersive-headset-and-motion-controllers-with-the-hololens-2-emulator"></a>Uso de un casco envolvente y controladores de movimiento de Windows Mixed Reality con el emulador de HoloLens 2

Al usar un casco Windows Mixed Reality envolvente con el HoloLens 2 Emulator, el movimiento y la rotación se asignan automáticamente al movimiento y rotación del casco.  La posición y la orientación del controlador de movimiento se asignan automáticamente a la posición y orientación de la mano en el emulador.  En la tabla siguiente se enumeran las acciones adicionales disponibles al usar un controlador de movimiento.

> [!NOTE]
> Cuando se usa un casco, se omiten automáticamente los controles estándar de teclado, mouse y gamepad.

|  Operación |  Acción |  Notas | 
|----------|----------|----------|
|  Cuerpo X |  Thumbstick Left /Right |   | 
|  Cuerpo Z |  Thumbstick Forward/Back |   | 
|  Cuerpo Y |  Página de teclado Arriba/Abajo | Asegúrese de que Windows Mixed Reality tiene el foco.  Presione Win+Y si el foco está en Windows Desktop para devolver el foco a Windows Mixed Reality. |
|  Mirada con los ojos a la izquierda o derecha |  DPad a la izquierda o derecha | |
|  Miradas hacia arriba y abajo | DPad Arriba/Abajo | |
|  Pulsar | Desencadenador | |
|  Acercar/agarrar | Botón De control | |
|  Gesto del sistema | Botón de menú | |
|  Restablecer posición | Clic de la chincheta | |

## <a name="perception-simulation-control-panel-keyboard-shortcuts"></a>Perception Simulation Panel de control métodos abreviados de teclado

Puede acceder al panel de control de simulación de percepción y habilitar o deshabilitar los dispositivos de entrada de PC con los siguientes métodos abreviados de teclado.

| Operación | Acceso directo | Descripción y notas |
|-----------|----------|-------------|
| Alternar "Usar teclado para la simulación" | F4 | Cuando está desactivada, la entrada de teclado va a la HoloLens o Windows Mixed Reality aplicación. |
| Alternar "Usar el mouse para la simulación" | F5 | Cuando está desactivada, la entrada del mouse va al entorno Mixed Reality (Windows Mixed Reality solo). |
| Alternar "Use gamepad for simulation" (Usar el bloc de juegos para la simulación) | F6 | Cuando está desactivada, la simulación omite la entrada del gamepad. |
| Mostrar u ocultar el panel de control | F7 | |
| Establecer el foco del teclado en el panel de control | F8 | Si el panel no está visible actualmente, se mostrará primero. |
| Acoplar o desacoplar el panel hacia o desde el emulador o Portal de realidad mixta ventana | F9 | Si la ventana se cierra cuando se desacopla, se acopla y se oculta. |

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Uso del simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md)
