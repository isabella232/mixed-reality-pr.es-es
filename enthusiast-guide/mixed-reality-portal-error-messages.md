---
title: Portal de realidad mixta de error
description: Solución Windows Mixed Reality problemas de mensajes del portal que van más allá de la documentación de soporte técnico al consumidor estándar.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Troubleshoot, Errors, Help, Support, Portal de realidad mixta
appliesto:
- Windows 10
ms.openlocfilehash: c85030da129d90bb0a150ad50a6990e30b68c21bc7a3899c4182e87acd4b4fa5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186875"
---
# <a name="mixed-reality-portal-error-messages"></a>Portal de realidad mixta de error

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>He recibido un mensaje de error "Algo salió mal" o tengo problemas en el Portal de realidad mixta.

Reinicie Windows Mixed Reality:
1. Desconecte ambos cables del casco del equipo.
2. Reinicia tu equipo.
3. Vuelva a conectar el casco.

Si eso no funciona, asegúrese de que el equipo reconoce el casco:
1. Seleccione Inicio.
2. Escriba "administrador de dispositivos" en el cuadro de búsqueda y selecciónelo en la lista. 
3. Expanda "Dispositivos de realidad mixta" y vea si aparece el casco. 

Si no aparece en la lista:
1. Conecte el casco a distintos puertos del equipo, si está disponible.
2. Busque las actualizaciones de software más recientes de Windows Update.
3. Desinstale y vuelva a Windows Mixed Reality:
    1. Desconecte ambos cables del casco del equipo.
    2. Seleccione **Configuración > Mixed reality > Uninstall (Desinstalar).**
    3. Seleccione **Configuración > dispositivos > Bluetooth & otros dispositivos** para desaparpar los controladores de movimiento. Seleccione cada controlador y, a continuación, seleccione "Quitar dispositivo".
    4. Vuelva a conectar el casco al equipo para volver a instalar Windows Mixed Reality.
    
## <a name="im-getting-a-check-your-usb-cable-error-message"></a>Aparece el mensaje de error "Comprobar el cable USB".

Conectar el casco a un puerto USB diferente (y asegúrese de que es un USB SuperSpeed 3.0). Además, intente quitar los extensores o concentradores entre el casco y el equipo.

## <a name="im-getting-a-check-your-display-cable-error-message"></a>Aparece el mensaje de error "Comprobar el cable de pantalla".

Siga estos pasos para solucionar el problema:
* Conectar el casco a DisplayPort 1.2 o posterior, o HDMI 1.4 o posterior. Asegúrese de que el puerto se corresponde con la tarjeta gráfica más avanzada del equipo.
* Si usa un adaptador, asegúrese de que es compatible con 4K.
* Pruebe a usar otro puerto HDMI.
* Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a displayPort en su lugar y use el puerto HDMI para el casco.
