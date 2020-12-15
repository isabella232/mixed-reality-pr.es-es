---
title: Uso del simulador de Windows Mixed Reality
description: El simulador de realidad mixta de Windows le permite probar aplicaciones de realidad mixtas en su PC sin un casco de Windows Mixed Reality.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, simulador, pruebas
ms.openlocfilehash: 4ed3355df242f1df35c009e53149d834ea113e1f
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530301"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Uso del simulador de Windows Mixed Reality

El simulador de realidad mixta de Windows le permite probar aplicaciones de realidad mixtas en su PC sin un casco de Windows Mixed Reality. El simulador está disponible con Windows 10 Creators Update. El simulador es similar al [emulador de HoloLens](using-the-hololens-emulator.md), aunque el simulador no usa una máquina virtual. Las aplicaciones simuladas se ejecutan en la sesión de usuario de escritorio de Windows 10, al igual que si usara un casco inmersivo. Las entradas humanas y del entorno leídas por los sensores en un casco envolvente se simulan en su lugar con el teclado, el mouse o la controladora Xbox. Las aplicaciones no necesitan ninguna modificación para ejecutarse en el simulador y no saben que no se ejecutan en un casco envolvente.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitar el simulador de realidad mixta de Windows

1. **Habilitar el modo de desarrollador** desde configuración-> Update y > de seguridad para desarrolladores
2. Inicio del **portal de realidad mixta** desde el escritorio
3. Si esta es la primera vez que inicia el portal, deberá pasar por la experiencia de instalación.
   1. Seleccionar **Introducción**
   2. Seleccione **acepto** para aceptar el contrato
   3. Seleccione **configurar para simulación (para desarrolladores)** para continuar con la instalación sin un dispositivo físico.
   4. Seleccione **configurar** para confirmar su elección
4. Seleccione el botón **para desarrolladores** en el lado izquierdo del portal de realidad mixta.
5. Activar el modificador **de alternancia de** simulación
   * La habilitación de la simulación instala y habilita de forma predeterminada el controlador simulado 6-DOF de la izquierda.  Antes de la actualización de Windows 10 de mayo de 2019, la instalación de un controlador simulado 6-DOF requiere permisos de administrador.  Acepte el cuadro de diálogo control de cuentas de usuario si aparece alguno.

Ahora debería ejecutarse con simulación.

Si desea deshabilitar el modo de Desarrollador en configuración, primero debe activar el conmutador de alternancia de simulación en **OFF** en la sección **para desarrolladores** del portal de realidad mixta.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implementación de aplicaciones en el simulador de realidad mixta

Dado que el simulador se ejecuta en el equipo local sin una máquina virtual, puede implementar las aplicaciones universales de Windows en el **equipo local** durante la depuración.

## <a name="basic-simulator-input"></a>Entrada básica del simulador

Controlar el simulador es similar a muchos juegos de vídeo 3D comunes y el [emulador de HoloLens](using-the-hololens-emulator.md). Hay opciones de entrada mediante el teclado, el mouse o un mando de Xbox.

Puede controlar el simulador dirigiendo las acciones de un usuario simulado con un casco envolvente. Sus acciones mueven el usuario simulado y causan interacciones con las aplicaciones que responden como lo harían en un casco envolvente.
* **Andar hacia delante, hacia atrás, a la izquierda y a la derecha**: usa las teclas W, A, S y D del teclado o el stick izquierdo en un mando de Xbox.
* **Buscar hacia arriba, hacia abajo, a la izquierda y** a la derecha: seleccione y arrastre el mouse, use las teclas de flecha del teclado o el botón derecho en un controlador de Xbox.
* **Botón de acción Presione en el controlador** : haga clic con el botón derecho en el mouse, presione la tecla entrar en el teclado o use el botón a en un controlador de Xbox.
* **Botón Inicio presionar el controlador** : Presione la tecla Windows o la tecla F2 del teclado o presione el botón B en un controlador Xbox.
* **Movimiento del controlador para el desplazamiento** : mantenga presionada la tecla Alt y el botón secundario del mouse y, a continuación, arrastre el mouse hacia arriba o hacia abajo. En un controlador de Xbox, mantenga presionado el desencadenador derecho y un botón, y mueva el botón derecho hacia arriba y hacia abajo.

## <a name="tracked-controllers"></a>Controladores controlados

El simulador de realidad mixta puede simular hasta dos controladores de movimiento de seguimiento a mano. Habilítelo mediante los modificadores de alternancia en el portal de realidad mixta. Cada controlador simulado tiene:
* Posición y orientación en el espacio
* Botón Inicio
* Botón de menú
* Botón de control
* Panel táctil
* Palanca
* Nivel de batería

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra a la mitad de la fase de implementación. Desde aquí, puede continuar con el [tema](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) siguiente o ir directamente a agregar Advanced Services.

> [!div class="nextstepaction"]
> [Servicios avanzados](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Consulte también
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Entrada del simulador de realidad mixta avanzada](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Asignación espacial en Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](../../develop/native/spatial-mapping-in-directx.md)
