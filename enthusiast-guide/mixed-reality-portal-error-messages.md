---
title: Mensajes de error del portal de realidad mixta
description: Los mensajes avanzados del portal de Windows Mixed Reality solucionan problemas que van más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, portal de realidad mixta
appliesto:
- Windows 10
ms.openlocfilehash: 11fa60b16a350d794a08db6a5f6120d88259c9ac
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692498"
---
# <a name="mixed-reality-portal-error-messages"></a>Mensajes de error del portal de realidad mixta

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Obtengo un mensaje de error "algo salió mal" o tengo problemas en el portal de realidad mixta.

Reiniciar Windows Mixed Reality:
1. Desconecte ambos cables de auriculares del equipo.
2. Reinicia tu equipo.
3. Vuelva a conectar los auriculares.

Si eso no funciona, asegúrese de que el equipo reconoce los auriculares:
1. Seleccione Inicio.
2. Escriba "Administrador de dispositivos" en el cuadro de búsqueda y selecciónelo en la lista. 
3. Expanda "dispositivos de realidad mixta" y compruebe si aparece el casco. 

Si no aparece, intente lo siguiente:
1. Conecte los auriculares a puertos diferentes en el equipo, si está disponible.
2. Busque las actualizaciones de software más recientes desde Windows Update.
3. Desinstalar y reinstalar Windows Mixed Reality:
    1. Desconecte ambos cables de auriculares del equipo.
    2. Seleccione **configuración > realidad mixta > desinstalar** .
    3. Seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** para desemparejar los controladores de movimiento. Seleccione cada controlador y, a continuación, seleccione "quitar dispositivo".
    4. Vuelva a conectar el casco al equipo para volver a instalar Windows Mixed Reality.
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>Obtengo un mensaje de error "comprobar el cable USB".

Conecte los auriculares a otro puerto USB (y asegúrese de que es un SuperSpeed USB 3,0). Además, pruebe a quitar cualquier dispositivo extender o concentrador entre los auriculares y el equipo.

## <a name="im-getting-a-check-your-display-cable-error-message"></a>Obtengo un mensaje de error "comprobar el cable de pantalla".

Pruebe lo siguiente:
* Conecte los auriculares a un DisplayPort 1,2 o posterior, o HDMI 1,4 o posterior. Asegúrese de que el puerto corresponde a la tarjeta de gráficos más avanzada del equipo.
* Si utiliza un adaptador, asegúrese de que sea compatible con 4K.
* Pruebe a usar un puerto HDMI diferente.
* Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a un DisplayPort en su lugar y use el puerto HDMI para sus auriculares.
