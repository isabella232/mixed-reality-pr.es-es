---
title: Accesorios de hardware
description: Describe los tipos de accesorios disponibles para su uso Windows Mixed Reality y cómo configurarlos.
author: mattzmsft
ms.author: mazeller
ms.date: 05/20/2020
ms.topic: article
keywords: how-to, accessories, bluetooth, bt, controller, gamepad, clicker, xbox, hardware, mixed reality headset, windows mixed reality headset, virtual reality headset, motion controller
ms.openlocfilehash: a6776df9374fce3f1399de944be06c93ff6fdcb3e6f4a38dcc92453556857376
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188464"
---
# <a name="hardware-accessories"></a>Accesorios de hardware

Windows Mixed Reality dispositivos admiten accesorios. Puede usar puertos Bluetooth o USB para emparejar los accesorios admitidos con un casco envolvente desde el equipo.

Para obtener información sobre el uso Bluetooth accesorios con HoloLens, consulte Conectar [para Bluetooth dispositivos USB-C.](/hololens/hololens-connect-devices)

Windows Mixed Reality cascos envolventes requieren accesorios para la entrada más allá [de la mirada](../design/gaze-and-commit.md) y la [voz.](../design/voice-input.md) Entre los accesorios **admitidos se incluyen el teclado y el mouse,** **el controlador para juegos** y los controladores de **[movimiento.](../design/motion-controllers.md)**

## <a name="pairing-bluetooth-accessories"></a>Emparejamiento de Bluetooth accesorios

Emparejar un periférico Bluetooth con un casco envolvente es similar a emparejar un periférico de Bluetooth con un Windows 10 o dispositivo móvil:

1. En el menú Inicio, abra la **Configuración** aplicación.
2. Ir a **Dispositivos**
3. Active la radio Bluetooth si está desactivada con el control deslizante.
4. Coloque el dispositivo Bluetooth en modo de emparejamiento. Este proceso varía de un dispositivo a otro, pero en la mayoría Bluetooth dispositivos mantiene presionados uno o varios botones.
5. Espere a que el nombre del dispositivo se muestre en la lista de Bluetooth dispositivos. Cuando lo haga, seleccione el dispositivo y, a continuación, **seleccione el botón** Emparejar. Si tiene muchos dispositivos Bluetooth cercanos, es posible que tenga que desplazarse hasta la parte inferior de la lista de dispositivos Bluetooth para ver el dispositivo que está intentando emparejar.
6. Al emparejar Bluetooth periféricos con la funcionalidad de entrada (por ejemplo, Bluetooth teclados), se puede mostrar un pin de 6 o 8 dígitos. Asegúrese de escribir ese pin en el periférico y, a continuación, presione Entrar para completar el emparejamiento con el casco.

## <a name="motion-controllers"></a>Controladores de movimiento

Windows Mixed Reality controladores [de movimiento son](../design/motion-controllers.md) compatibles con los cascos envolventes, pero no HoloLens. Estos controladores ofrecen un seguimiento de movimiento preciso y con capacidad de respuesta en el campo de vista. Los sensores de los cascos envolventes hacen el seguimiento, lo que significa que no es necesario instalar hardware en las paredes del espacio. Cada controlador incluye varios métodos de entrada.

![Windows Mixed Reality controladores de movimiento](../design/images/winmr-ck-1080x1080-350px.jpg)

## <a name="bluetooth-keyboards"></a>Bluetooth teclados

Qwerty en inglés Bluetooth teclados se pueden emparejar y usar en cualquier lugar donde pueda usar el teclado holográfico. La obtención de un teclado de calidad marca la diferencia, por lo que se recomienda el teclado universal de [Microsoft](https://www.microsoft.com/accessories/products/keyboards/universal-foldable-keyboard/gu5-00001) o [Microsoft Designer Bluetooth Desktop](https://www.microsoft.com/accessories/products/keyboards/designer-bluetooth-desktop/7n9-00001).

## <a name="bluetooth-gamepads"></a>Bluetooth gamepads

Puede usar un controlador con aplicaciones y juegos que habiliten específicamente la compatibilidad con el controlador de juegos. Los gamepads no se pueden usar para controlar el HoloLens interfaz de usuario.

Los controladores inalámbricos de Xbox que se incluyen con el Xbox One S o se venden como accesorios para la característica Xbox One S Bluetooth conectividad, por lo que puede usarlos con cascos envolventes y HoloLens de seguridad. El controlador inalámbrico xbox [debe actualizarse para](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) poder usarse con HoloLens.

Otras marcas de Bluetooth para juegos pueden funcionar con Windows Mixed Reality dispositivos, pero la compatibilidad variará según la aplicación.

## <a name="other-bluetooth-accessories"></a>Otros Bluetooth accesorios

Siempre que el periférico admita los Bluetooth perfiles HID o COMB, puede emparejarse con HoloLens. Otros Bluetooth dispositivos HID y NFC, además del teclado, mouse y HoloLens Clicker, pueden requerir una aplicación complementaria en Microsoft HoloLens para que sea totalmente funcional.

Los periféricos no admitidos incluyen:

* No se admiten periféricos Bluetooth perfiles de audio.
* Bluetooth dispositivos de audio como altavoces y cascos pueden estar disponibles en la aplicación Configuración, pero no se admiten con Microsoft HoloLens como punto de conexión de audio.
* Bluetooth teléfonos y equipos habilitados para el emparejamiento y las transferencias de archivos no se admiten.

## <a name="unpairing-a-bluetooth-peripheral"></a>Desaparpair un Bluetooth periférico

1. En el menú Inicio, abra la **Configuración** aplicación.
2. Ir a **Dispositivos**
3. Activar la radio Bluetooth si está desactivada
4. Busque el dispositivo en la lista de dispositivos de Bluetooth disponibles
5. Seleccione el dispositivo en la lista y, a continuación, seleccione **el botón** Quitar.