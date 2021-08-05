---
title: Preguntas más frecuentes sobre límites
description: Solución Windows Mixed Reality solución de problemas de límites que va más allá de la documentación de soporte técnico al consumidor estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Boundary
appliesto:
- Windows 10
ms.openlocfilehash: c1d6a10ae6ed50f7b9088b26c78cde4ccf8386ea0603c39e107ed23910db9308
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187975"
---
# <a name="boundary-faqs"></a>Preguntas más frecuentes sobre límites

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>¿Cuál es un límite y por qué debo crear uno?

Un límite define el área en la que puede moverse mientras lleva el casco Windows Mixed Reality dispositivo. Es importante crear un límite que le ayude a evitar los obstáculos que no puede ver mientras está en el casco. El límite parece un contorno blanco dentro de la realidad mixta y aparece cuando se acerca a él. Cuando lo vea, resalte los movimientos y evite atravesar el límite o ampliar los vehículos más allá de él.

El área dentro del límite debe estar libre de cocinas, accesorios de luz de bajo impacto, ventiladores de puente, y así sucesivamente, por lo que no se topará con nada ni lo superará. [Obtenga información sobre el estado y la seguridad en Windows Mixed Reality](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>Cómo crear un límite?

La primera vez que configure el casco, la aplicación de configuración (Portal de realidad mixta) le llevará por los pasos para crear un límite. Pero puede crear uno en cualquier momento:

1. Seleccione **Iniciar > Portal de realidad mixta** en el escritorio.
2. Abra "Menú".
3. Seleccione "Configurar el límite de la sala" para crear un nuevo límite.

Si otra persona usa el casco, asegúrese de que comprende el límite y cómo usarlo. Si mueve el casco a una nueva ubicación, deberá configurar un nuevo límite para el espacio.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Aparece un mensaje de error al intentar crear un límite

* No se acerca demasiado a una pared u otro obstáculo al crear un límite.
* Asegúrese de mantener el casco a la altura de la altura de la altura y de mirar el equipo mientras realiza el seguimiento del límite.
* Asegúrese de que el sensor no está bloqueado y que hay suficiente luz.
* El espacio que está trazando debe ser mayor que 3 metros cuadrados.
* El espacio no debe ser demasiado grande o demasiado complicado. Se adhiere a una forma geométrica simple con giros y giros.
* No vuelva a través de su propia ruta de acceso mientras está trazando.
* Si se queda atascado en una esquina, empiece de nuevo.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>El sistema no encuentra el límite y se me presenta la interfaz de usuario de configuración.

Esto significa que el sistema de seguimiento no pudo reconocer su entorno. Si se encuentra en un entorno nuevo, debe configurar el [límite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Si anteriormente ha usado el dispositivo en este entorno y ha configurado un límite:

* Asegúrese de que la habitación tiene suficiente luz.
* Asegúrese de que ha agotado el dispositivo y ha mirado por la sala. El dispositivo debe observar el entorno para saber dónde está. No encontrará los límites si está sentado en un escritorio o una mesa.
* Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectarlo.
* Si algo en el entorno ha cambiado, es posible que el dispositivo ya no lo reconozca. Configure un nuevo límite.

Si estos pasos no resuelven el problema, elimine los datos del entorno y vuelva a configurar el límite.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>El sistema me presenta una interfaz de usuario que me pide que elija la configuración de todas las experiencias o sentado o en pie, y veo mis límites.

El dispositivo tarda demasiado tiempo en encontrar los límites. Puede omitir este mensaje si elige la opción para usar un límite y se le mostrará en su Windows Mixed Reality principal con los límites presentes.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>A menudo veo un mensaje que dice "He perdido mis límites".

El sistema de seguimiento tiene dificultades para realizar un seguimiento e identificar su entorno. En este estado, el dispositivo ya no puede mostrar los límites. El casco cambia a 3DOF para evitar que se tope con las cosas del mundo real hasta que vuelva a encontrar los límites. Pruebe los pasos siguientes para corregir el problema:

1. Asegúrese de que la habitación tiene suficiente luz.
2. Vuelva a ejecutar el programa de instalación si ha redecorado o restaurado recientemente la sala.
3. Desconecte el dispositivo, cierre Windows Mixed Reality y vuelva a conectarlo.
4. Borre los datos del entorno y vuelva a configurar el dispositivo.
5. Si el mensaje persiste, póngase en contacto con el soporte técnico al cliente.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Un mensaje indica que no se encuentra mi límite. ¿Cuál debo hacer?

Windows Mixed Reality puede tener problemas para identificar el límite existente. Puede crear un límite o puede usar el dispositivo en modo "Sentado y de pie".

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Un mensaje indica "Seguimiento perdido" o "No tenemos un límite para este espacio"

Cree un nuevo límite:

1. Seleccione **Iniciar > Portal de realidad mixta**.
2. Abra "Menú".
3. Seleccione "Configurar el límite de la sala".

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>El límite siempre está visible. ¿Cómo puedo hacerlo desaparecer?

El límite aparece cuando está cerca de él. Si el límite incluye secciones con una forma estrecha o irregular, es posible que termine cerca de él. El límite puede aparecer con más frecuencia de lo que le gustaría. Intente volver a crear el límite con una forma más grande y regular para corregir el problema:

1. Seleccione **Iniciar > Portal de realidad mixta**.
2. Abra "Menú".
3. Seleccione "Configurar el límite de la sala".

## <a name="can-i-turn-off-the-boundary-temporarily"></a>¿Puedo desactivar temporalmente el límite?

* Seleccione **Iniciar > Portal de realidad mixta**.
* Abra "Menú".
* Active "Boundary" (Límite) en "Off" (Desactivado). Asegúrese de permanecer en un solo lugar mientras el límite está desactivado.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Cómo elegir entre "Sentado y de pie" y "Todas las experiencias"?

Si elige "Sentado y de pie", ya sea durante la configuración del casco o más adelante, se usarán los cascos sin límite. Deberá permanecer en un solo lugar cuando use el casco para evitar obstáculos físicos y riesgos de viaje. Puede ponerse de pie o ponerse de pie, pero no puede moverse. Tenga en cuenta que los obstáculos pueden ser sobrecarga y a su alrededor.

Algunas aplicaciones pueden estar diseñadas para funcionar con un límite. Es posible que no funcionen o proporcionen la misma experiencia si los usa sin un límite.

Si elige "Todas las experiencias", configurará un límite y podrá usar aplicaciones y experiencias que funcionen con y sin límite.

## <a name="see-also"></a>Vea también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico.](https://support.microsoft.com/contactus/)