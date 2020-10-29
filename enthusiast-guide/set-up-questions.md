---
title: Preguntas más frecuentes sobre la instalación
description: Solución avanzada de problemas de Windows Mixed Reality para preguntas de configuración que van más allá de nuestra documentación de soporte técnico estándar para el consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, solución de problemas, errores, ayuda, soporte técnico, configuración, Inicio de Windows Mixed Reality, portal de Windows Mixed Reality
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91692458"
---
# <a name="setup-faqs"></a>Preguntas más frecuentes sobre la instalación 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>El portal de realidad mixta no se abre cuando se conectan los auriculares.

Portal de realidad mixta, la aplicación que le guía a través de la configuración de Windows Mixed Reality, está diseñada para abrirse automáticamente cuando conecta un casco compatible. Si no se abre, vaya a Inicio y escriba "portal de realidad mixta" en el cuadro de búsqueda para abrir la aplicación. Si no encuentra el portal de realidad mixta, es posible que deba [actualizar a la versión más reciente de Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Cómo elegir entre "sentado y permanente" y "todas las experiencias"

Si elige "sentado y permanente", ya sea durante la configuración del auricular o más adelante, utilizará los auriculares sin límite. Puede ponerse al día, pero tendrá que permanecer en un solo lugar, ya que no tendrá ningún límite que le ayude a evitar obstáculos físicos. Algunas aplicaciones pueden estar diseñadas para trabajar con un límite, por lo que es posible que no pueda usarlas o que no tenga la misma experiencia si las usa sin límite. Consulte ["¿Qué es un límite y por qué debo crear uno?"](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one).

Si elige "todas las experiencias", configurará un límite y podrá usar aplicaciones y experiencias que funcionen con un límite, así como los que no lo necesiten. 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>Aprenda que la realidad mixta no se ejecutó en el primer inicio y me gustó de la Página principal de Windows Mixed Reality.

Puede volver a ejecutar la experiencia de aprendizaje siguiendo los [pasos de volver a ejecutar](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Mis controladores no se muestran en la Página principal de Windows Mixed Reality.

Asegúrese de que los controladores tienen baterías completas y que se emparejan correctamente con Bluetooth. Pruebe a desconectar y apagar los controladores con el botón Windows. Si todavía no puede ver los controladores, pruebe a quitar y volver a emparejar cada controlador: 
* Si el casco tiene una radio integrada, use la aplicación complementaria suministrada con los auriculares para desemparejar y volver a emparejar los controladores (el portal de realidad mixta puede ayudarle a encontrar la aplicación complementaria correcta). 
* Si los controladores se emparejan con el equipo, vaya a **dispositivos > configuración de > de Bluetooth** para desemparejar y volver a emparejar los controladores. 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>El nivel inferior de la Página principal de Windows Mixed Reality no parece estar en el alto correcto.

Seleccione **inicio > ajuste de piso** , que se iniciará una vez que coloque la aplicación en el mundo, para realizar cambios mientras se contiene el casco. En esta aplicación, se le indicará que use el teclado táctil (controlador de movimiento) o el panel de control (controlador de vídeo) para ajustar el alto del piso. Cuando el piso sea correcto, use el botón Windows para volver a la Página principal.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>No se puede mostrar una vista previa de lo que veo en el escritorio.

El portal de Windows Mixed Reality tiene un botón **reproducir** en la parte inferior de la pantalla que le permite obtener una vista previa de lo que está viendo en el casco en la pantalla del escritorio. Por motivos de rendimiento, esta característica solo está disponible en equipos que ejecutan Windows Mixed Reality ultra (90Hz).

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Obtengo un mensaje de error "algo salió mal" o tengo problemas en el portal de realidad mixta
Para obtener más información sobre un código de error específico, mire [aquí](error-codes.md). También puede intentar:

Reiniciar Windows Mixed Reality:
1. Desconecte ambos cables de auriculares del equipo.
2. Reinicia tu equipo.
3. Vuelva a conectar los auriculares.

Asegúrese de que el equipo reconoce los auriculares:
1. Seleccione Inicio.
2. Escriba "Device Manager" en el cuadro de búsqueda y selecciónelo en la lista. 
3. Expanda "dispositivos de realidad mixta" y compruebe si aparece el casco. 

Si no aparece en la lista:
1. Conecte los auriculares a puertos diferentes en el equipo, si está disponible.
2. Busque las actualizaciones de software más recientes desde Windows Update.
3. Desinstalar y reinstalar Windows Mixed Reality:
    1. Desconecte ambos cables de auriculares del equipo.
    2. Seleccione **configuración > realidad mixta > desinstalar** .
    3. Si los controladores de movimiento están emparejados al equipo, seleccione **configuración > dispositivos > Bluetooth & otros dispositivos** para desemparejarlos. Seleccione cada controlador y "quitar dispositivo". Si los controladores se emparejan con el casco, puede omitir este paso.
    4. Vuelva a conectar el casco al equipo para volver a instalar Windows Mixed Reality.

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>No puedo dirigir la entrada (controladores, controlador de juegos, Mouse/teclado) a Windows Mixed Reality.

Al colocar el casco, la entrada se debe cambiar automáticamente a la experiencia de realidad mixta a través del sensor de presencia del casco. En el escritorio debe aparecer una barra azul:

![Escritorio de Windows con entrada que se dirige al casco](images/1050px-windowsy.png)

Si la entrada no se activa automáticamente, es posible que haya deshabilitado el cambio de entrada automático en la **configuración > realidad mixta > la visualización de los auriculares > el cambio de entrada** . Siempre puede escribir **tecla Windows + Y** en el teclado para alternar manualmente la entrada al casco o volver al escritorio.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante el inicio de la realidad mixta, estoy atascado en "gire el cabezal hacia el lateral y, a continuación, en el suelo".

Este paso permite que los auriculares reconozcan su espacio y restauren el suelo y el límite virtual existentes. Al colocar el casco, este proceso de análisis puede tardar hasta 10 segundos. Una vez finalizado, estará en la Página principal de Windows Mixed Reality o se le pedirá que configure de nuevo el límite.

Si el proceso de análisis tarda más de 10 segundos, podría haber un problema con el sensor de proximidad en el casco:
1. Compruebe que la etiqueta se ha quitado del sensor de proximidad. El sensor de proximidad se encuentra dentro del casco aproximadamente donde sería el centro del Forehead.
2. Compruebe que el sensor de proximidad está alternando la entrada al casco: con el dedo, cubra y descubra el sensor de proximidad varias veces para comprobar que la entrada está cambiando al casco. Debería ver el banner **clave de Windows + Y** en la parte superior de su PC. Puede cambiar manualmente la entrada al casco en cualquier momento escribiendo **tecla Windows + Y** en el teclado.

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>El controlador Xbox no funciona con Windows Mixed Reality.

* Asegúrese de que el controlador esté encendido, totalmente cargado y conectado al equipo.
* Reemplace las baterías del controlador.
* Si usa un controlador de Bluetooth, vaya a **configuración > dispositivos > Bluetooth & otros dispositivos** del equipo y asegúrese de que esté emparejado (debe aparecer en la página).
