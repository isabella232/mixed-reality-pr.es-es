---
title: Uso del simulador de Windows Mixed Reality
description: El Windows Mixed Reality de aplicaciones le permite probar aplicaciones de realidad mixta en el equipo sin un casco Windows Mixed Reality envolvente.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows Mixed Reality, Simulador, Pruebas
ms.openlocfilehash: 0a6ff0cb0cd893c40e354c0590437201fb97e75c67421a638e47897b19a8f688
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220941"
---
# <a name="using-the-windows-mixed-reality-simulator"></a>Uso del simulador de Windows Mixed Reality

El Windows Mixed Reality de aplicaciones le permite probar aplicaciones de realidad mixta en el equipo sin un casco Windows Mixed Reality envolvente. El simulador está disponible con el Windows 10 Creators Update. El simulador es similar al [HoloLens Emulator](using-the-hololens-emulator.md), aunque el simulador no usa una máquina virtual. Las aplicaciones simuladas se ejecutan en Windows 10 sesión de usuario de escritorio, como lo harían si usara un casco envolvente. En su lugar, las entradas humanas y ambientales leídas por los sensores en un casco envolvente se simulan mediante el teclado, el mouse o el controlador de Xbox. Las aplicaciones no necesitan ninguna modificación para ejecutarse en el simulador y no saben que no se ejecutan en un casco envolvente.

## <a name="enabling-the-windows-mixed-reality-simulator"></a>Habilitación del Windows Mixed Reality de datos

1. **Habilitar el modo de** desarrollador Configuración -> Update and Security -> Para desarrolladores
2. Inicio del **Portal de realidad mixta** desde el escritorio
3. Si es la primera vez que inicia el portal, deberá seguir la experiencia de configuración.
   1. Seleccione **Introducción.**
   2. Seleccione **Acepto aceptar** el contrato.
   3. Seleccione **Configurar para la simulación (para desarrolladores)** para continuar con la configuración sin un dispositivo físico.
   4. Seleccione **Set up (Configurar)** para confirmar su elección.
4. Seleccione el **botón Para** desarrolladores en el lado izquierdo de la Portal de realidad mixta
5. Activar el conmutador de alternancia **Simulación**
   * La habilitación de la simulación instala y habilita el controlador 6-DOF simulado izquierdo de forma predeterminada.  Antes de la Windows 10 de mayo de 2019, la instalación de un controlador 6-DOF simulado requiere permisos de administrador.  Acepte el cuadro de diálogo Control de cuentas de usuario si aparece uno.

Ahora debería ejecutar con simulación.

Si desea deshabilitar el modo de desarrollador en Configuración, primero debe  activar  el conmutador de alternancia Simulación a Desactivado en la sección Para desarrolladores de la Portal de realidad mixta.

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a>Implementación de aplicaciones en el simulador Mixed Reality aplicación

Dado que el simulador se ejecuta en el equipo local sin una máquina virtual, puede implementar las aplicaciones universales Windows en la máquina **local** al depurar.

## <a name="basic-simulator-input"></a>Entrada básica del simulador

Controlar el simulador es similar a muchos juegos de vídeo 3D comunes y el [emulador HoloLens .](using-the-hololens-emulator.md) Hay opciones de entrada mediante el teclado, el mouse o un mando de Xbox.

Para controlar el simulador, dirija las acciones de un usuario simulado que lleva un casco envolvente. Las acciones mueven al usuario simulado y provocan interacciones con aplicaciones que responden como lo harían en un casco envolvente.
* **Andar hacia delante, hacia atrás, a la izquierda y a la derecha**: usa las teclas W, A, S y D del teclado o el stick izquierdo en un mando de Xbox.
* **Buscar, bajar, izquierda** y derecha: seleccione y arrastre el mouse, use las teclas de dirección del teclado o el stick derecho en un controlador de Xbox.
* **Botón Acción presione el controlador:** haga clic con el botón derecho en el mouse, presione la tecla Entrar en el teclado o use el botón A en un controlador Xbox.
* **Botón Inicio presione el controlador:** presione la tecla Windows o F2 del teclado, o bien presione el botón B en un controlador Xbox.
* **Movimiento del controlador para desplazarse:** mantenga presionada la tecla Alt y el botón derecho del mouse y arrastre el mouse hacia arriba o hacia abajo. Si usa un mando de Xbox, mantenga presionado el gatillo derecho y el botón A, y mueva el stick derecho hacia arriba y hacia abajo.

## <a name="tracked-controllers"></a>Controladores con seguimiento

El Mixed Reality puede simular hasta dos controladores de movimiento con seguimiento manual. Se habilitan mediante los modificadores de alternancia de la Portal de realidad mixta. Cada controlador simulado tiene:
* Posición y orientación en el espacio
* Botón Inicio
* Botón de menú
* Botón De control
* Panel táctil
* Stick
* Nivel de la batería

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra a la mitad de la fase de implementación. Desde aquí, puede continuar con el [tema](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) siguiente o pasar directamente a la adición de servicios avanzados.

> [!div class="nextstepaction"]
> [Servicios avanzados](../../develop/unity/unity-development-overview.md#5-adding-services)


## <a name="see-also"></a>Consulte también
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Entrada avanzada Mixed Reality simulador de carga](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [Asignación espacial en Unity](../../develop/unity/spatial-mapping-in-unity.md)
* [Asignación espacial en DirectX](../../develop/native/spatial-mapping-in-directx.md)
