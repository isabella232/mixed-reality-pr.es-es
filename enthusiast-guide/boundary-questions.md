---
title: Preguntas más frecuentes sobre los límites
description: Solución avanzada de problemas de Windows Mixed Reality para preguntas de límite que van más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, compatibilidad, límite
appliesto:
- Windows 10
ms.openlocfilehash: 8dba6ebb5f74b229cea4ea2d5e1ac0a5e70a3f57
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725286"
---
# <a name="boundary-faqs"></a>Preguntas más frecuentes sobre los límites

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>¿Qué es un límite y por qué debo crear uno?

Un límite define el área que se puede desplazar en el casco de la realidad mixta de Windows. Es importante crear un límite que le ayude a evitar los obstáculos que no puede ver mientras se encuentra en el casco. El límite es similar a un contorno blanco dentro de la realidad mixta y aparece cuando está cerca de él. Cuando lo vea, ralentice los movimientos y Evite cruzar el límite o extender sus extremidades más allá de él.

El área dentro del límite debe ser libre de mobiliario, sujeciones de luz de bajada, ventiladores de techo, etc., por lo que no se saltará ni se desplazará sobre nada. [Obtenga información sobre el estado y la seguridad en Windows Mixed Reality](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>¿Cómo crear un límite?

La primera vez que configure los auriculares, la aplicación de instalación (portal de realidad mixta) le guiará por los pasos necesarios para crear un límite. Sin embargo, puede crear una en cualquier momento:

1. Seleccione **inicio > portal de realidad mixta** en el escritorio.
2. Abra "menú".
3. Seleccione "configurar límite de habitación" para crear un nuevo límite.

Si otra persona usa el casco, asegúrese de que comprenden el límite y cómo usarlo. Si mueve los auriculares a una nueva ubicación, deberá configurar un nuevo límite para el espacio.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Aparece un mensaje de error al intentar crear un límite

* No se acerque demasiado a una pared u otro obstáculo al crear un límite.
* Asegúrese de mantener el casco en el alto de waist y enfrente el equipo mientras realiza el seguimiento del límite.
* Asegúrese de que el sensor no esté bloqueado y de que haya suficiente luz.
* El espacio en el que se realiza el seguimiento debe ser mayor de 3 metros cuadrados.
* El espacio no debe ser demasiado grande o demasiado complicado. Adhiere a una forma geométrica simple con giros y vueltas.
* No vuelva a cruzar su propia ruta de acceso mientras realiza el seguimiento.
* Si se queda atascado en una esquina, empiece de nuevo.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>El sistema no puede encontrar el límite y se está presentando la interfaz de usuario del programa de instalación

Esto significa que el sistema de seguimiento no pudo reconocer el entorno. Si está en un entorno nuevo, debe configurar el [límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Si ya ha usado el dispositivo en este entorno y ha configurado un límite:

* Asegúrese de que el salón tenga suficiente luz.
* Asegúrese de que ha desgastado el dispositivo y ha examinado el salón. El dispositivo debe observar su entorno para saber dónde está. No encontrará los límites si están en un escritorio o en una tabla.
* Desconecte el dispositivo, cierre Windows Mixed Reality y conéctelo de nuevo.
* Si algo ha cambiado en el entorno, es posible que el dispositivo ya no lo reconozca. Configure un nuevo límite.

Si estos pasos no resuelven el problema, elimine los datos del entorno y vuelva a configurar el límite.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>El sistema se presenta con una interfaz de usuario que me pide que elija el programa de instalación para todas las experiencias o bien, y veo mis límites

El dispositivo está tardando demasiado tiempo en encontrar los límites. Puede omitir este mensaje eligiendo la opción para usar un límite y se le dirigirá a la Página principal de Windows Mixed Reality con los límites presentes.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>A menudo veo un mensaje que dice "he perdido mis límites"

El sistema de seguimiento está realizando un seguimiento e identificación del entorno. En este estado, el dispositivo ya no puede mostrar los límites. El casco cambia a 3DOF para evitar que se salten cosas en el mundo real hasta que vuelva a ubicar los límites. Siga estos pasos para solucionar el problema:

1. Asegúrese de que el salón tenga suficiente luz.
2. Vuelva a ejecutar el programa de instalación si ha redecorado o remodelado recientemente el salón.
3. Desconecte el dispositivo, cierre Windows Mixed Reality y conéctelo de nuevo.
4. Borre los datos del entorno y vuelva a configurar el dispositivo.
5. Si el mensaje persiste, póngase en contacto con el servicio de soporte al cliente.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Un mensaje indica que no se puede encontrar el límite. ¿Cuál debo hacer?

Windows Mixed Reality podría tener problemas para identificar el límite existente. Puede crear un nuevo límite o usar el dispositivo en modo "sentado y permanente".

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Un mensaje indica "pérdida de seguimiento" o "no tenemos límite para este espacio"

Cree un nuevo límite:

1. Seleccione **inicio > portal de realidad mixta**.
2. Abra "menú".
3. Seleccione "configurar límite de habitación".

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>El límite siempre es visible. ¿Cómo puedo hacer que salga?

El límite aparece cuando está cerca de él. Si el límite incluye alguna sección con una forma estrecha o irregular, puede acabar cerca de ella. El límite puede aparecer con más frecuencia de la que le gustaría. Intente crear el límite de nuevo con una forma más grande y más regular para solucionar el problema:

1. Seleccione **inicio > portal de realidad mixta**.
2. Abra "menú".
3. Seleccione "configurar límite de habitación".

## <a name="can-i-turn-off-the-boundary-temporarily"></a>¿Se puede desactivar el límite temporalmente?

* Seleccione **inicio > portal de realidad mixta**.
* Abra "menú".
* Active "límite" en "desactivado". Asegúrese de permanecer en un lugar mientras el límite esté desactivado.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Cómo elegir entre "sentado y permanente" y "todas las experiencias"

Si elige "sentado y permanente", ya sea durante la configuración del auricular o más adelante, utilizará los auriculares sin límite. Deberá permanecer en un lugar al usar los auriculares para evitar obstáculos físicos y hacer posibles riesgos. Puede ponerse al día, pero no puede moverse. Tenga en cuenta que los obstáculos pueden ser una sobrecarga y en su lugar.

Algunas aplicaciones pueden estar diseñadas para funcionar con un límite. Es posible que no funcionen o que proporcionen la misma experiencia si se usan sin límite.

Si elige "todas las experiencias", configurará un límite y podrá usar aplicaciones y experiencias que funcionen con y sin límite.

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)