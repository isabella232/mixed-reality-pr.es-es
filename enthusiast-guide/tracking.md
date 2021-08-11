---
title: Preguntas más frecuentes sobre el seguimiento
description: Seguimiento Windows Mixed Reality solución de problemas que va más allá de la documentación de soporte técnico para consumidores estándar.
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Tracking
ms.openlocfilehash: fe5462a53de7b196db37edbbf0e56199a17c4c99b54ea1e7d9edf72e0845c9e5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199481"
---
# <a name="tracking-faqs"></a>Preguntas más frecuentes sobre el seguimiento

## <a name="my-headset-has-stopped-tracking"></a>Mi casco ha dejado de realizar el seguimiento

Asegúrese de que las luces estén apagadas y de que no haya nada que entorpece las cámaras de seguimiento dentro y fuera en la parte delantera del casco. Si se pierde el seguimiento, puede tardar unos segundos en reanudarse. Reinicie el Windows Mixed Reality el portal de seguimiento no se reinicia.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Puedo mirar a mi alrededor, pero no puedo traducir (estoy bloqueado en 3DOF)

Esto significa que el sistema de seguimiento no puede generar pose o que la aplicación ha dejado de usar nuevos datos de posición para representar. Para solucionar el problema:

* Asegúrese de que la habitación tiene suficiente luz.
* Asegúrese de que la sala tiene suficientes detalles para realizar el seguimiento.
* Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectarlo.
* Si el mensaje persiste, póngase en contacto con el [soporte técnico al cliente.](https://support.microsoft.com/)

## <a name="the-view-in-the-hmd-is-frozen"></a>La vista del HMD está inmovilizada.

Esto suele significar que la aplicación o un componente de nivel de sistema han dado error. Intente:

1. Presione el botón "Inicio" para salir de la aplicación.
2. Desconecte el dispositivo, cierre MRP y vuelva a conectarlo.
3. Reinicia el equipo.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>El mundo se congeló brevemente y se inclinó o volteó al revés antes de volver a la normalidad.

Esto podría deberse a que un componente de nivel de sistema o aplicación se encuentra con un error grave o una falta temporal de memoria o recursos de CPU. comprobar:

1. Abra Administrador de tareas y asegúrese de que al menos el 20 % de la CPU esté libre, que 400 MB de memoria esté disponible y que la E/S del disco esté por debajo del 80 %.
2. Vaya a **Visor de eventos > Windows registros > aplicación** para buscar errores en torno al momento de la inmovilización. Busque cualquier cosa que haga referencia HoloLens sensores, Mixed Reality o la aplicación que estaba ejecutando en ese momento. Esos registros podrían explicar lo que produjo el error.
3. Reinicie el equipo si el problema persiste.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>El mundo se voltea al revés momentáneamente y vuelve a la normalidad

Esto suele deberse a errores al obtener datos del sensor del casco para informar a los algoritmos de seguimiento. Si esto sucede con frecuencia:

1. Conecte el casco a otro puerto USB 3.0.
2. Conecte el casco directamente al equipo en lugar de a un concentrador USB 3.0.
3. Si el problema persiste, póngase en contacto con el [servicio de soporte al cliente.](https://support.microsoft.com/)

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>El mundo está inclinado, pero puedo navegar y recorrerlo por Windows Mixed Reality

Si los errores de datos del sensor se registran en los datos del entorno en el equipo, puede hacer que los Windows Mixed Reality aparezcan inclinados, a veces de forma permanente. Para solucionar este error:

1. Desconecte el casco, cierre Windows Mixed Reality y vuelva a conectar el casco.
2. Reinicia el equipo.
3. Borre los datos del entorno.