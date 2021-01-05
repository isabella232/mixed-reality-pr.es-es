---
title: Preguntas más frecuentes sobre seguimiento
description: Seguimiento de la solución de problemas de Windows Mixed Reality que va más allá de nuestra documentación de soporte técnico de consumidor estándar.
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, seguimiento
ms.openlocfilehash: 2634b95cf876a5b540710f80d3dd7f9d48b3bad9
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725836"
---
# <a name="tracking-faqs"></a>Preguntas más frecuentes sobre seguimiento

## <a name="my-headset-has-stopped-tracking"></a>El micrófono ha dejado de realizar el seguimiento

Asegúrese de que las luces están encendidas y de que no hay nada que obstruya las cámaras de seguimiento interior de la parte delantera del casco. Si se pierde el seguimiento, puede tardar unos segundos en reanudarse. Reiniciar el portal de Windows Mixed Reality el seguimiento no se reinicia.

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Puedo buscar, pero no puedo traducir (Estoy atascado en 3DOF)

Esto significa que el sistema de seguimiento no puede generar una representación o que la aplicación se ha detenido con los nuevos datos de pose que se van a representar. Para solucionar el problema:

* Asegúrese de que el salón tenga suficiente luz.
* Asegúrese de que el salón tenga suficientes detalles para realizar el seguimiento.
* Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectar el dispositivo.
* Si el mensaje persiste, póngase en contacto [con el servicio de soporte al cliente](https://support.microsoft.com/) .

## <a name="the-view-in-the-hmd-is-frozen"></a>La vista del HMD está inmovilizada

Normalmente, esto significa que se ha producido un error en la aplicación o en un componente de nivel de sistema. Intente:

1. Presione el botón "Inicio" para salir de la aplicación.
2. Desconecte el dispositivo, cierre PRM y vuelva a conectar el dispositivo.
3. Reinicia el equipo.

## <a name="the-world-briefly-froze-and-tilted-or-flipped-upside-down-before-returning-to-normal"></a>El mundo se inmovilizó brevemente y se inclina o voltea hacia abajo antes de volver a la normalidad

Esto puede deberse a que una aplicación o un componente de nivel de sistema ha provocado un error irrecuperable o una falta temporal de memoria o recursos de CPU. Para comprobar lo siguiente:

1. Abra el administrador de tareas y asegúrese de que al menos el 20% de la CPU sea gratuito, 400 MB de memoria disponible y la e/s de disco debe ser inferior al 80%.
2. Vaya a **Visor de eventos > registros de Windows > aplicación** para buscar errores en torno a la inmovilización. Busque cualquier elemento que haga referencia a los sensores de HoloLens, la realidad mixta o la aplicación que se estaba ejecutando en ese momento. Esos registros podrían explicar qué causó el error.
3. Reinicie el equipo si el problema persiste.

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>El mundo se invierte momentáneamente hacia abajo y se devolvió a la normalidad

Esto se debe normalmente a errores en la obtención de datos de sensor desde los auriculares para informar sobre los algoritmos de seguimiento. Si esto sucede con frecuencia:

1. Conecte los auriculares a otro puerto USB 3,0.
2. Conecte los auriculares directamente al equipo en lugar de a un concentrador USB 3,0.
3. Si el problema persiste, póngase en contacto [con el servicio de soporte al cliente](https://support.microsoft.com/).

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a>El mundo está inclinado, pero puedo navegar y desplazarse por Windows Mixed Reality.

Si los errores de datos del sensor se registran en los datos del entorno del equipo, puede hacer que Windows Mixed Reality aparezca inclinado, a veces permanentemente. Para solucionar este error:

1. Desenchufe los auriculares, cierre Windows Mixed Reality y vuelva a conectar el casco.
2. Reinicia el equipo.
3. Borre los datos del entorno.