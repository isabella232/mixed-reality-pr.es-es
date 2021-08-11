---
title: Entrada de voz en Unreal
description: Aprenda a configurar y usar la entrada de voz, las asignaciones de voz y el reconocimiento en aplicaciones de realidad mixta de Unreal para HoloLens 2 dispositivos.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, Unreal, Unreal Engine 4, UE4, HoloLens 2, voz, entrada de voz, reconocimiento de voz, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 12d0c595b5319da50e119f4a2463e2ca3e07ce449f11d6fd266c5f988d180465
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221016"
---
# <a name="voice-input-in-unreal"></a>Entrada de voz en Unreal

La entrada de voz en Unreal permite interactuar con un holograma sin tener que usar gestos de mano y solo se admite HoloLens 2. La entrada de voz en HoloLens 2 funciona con el mismo motor que admite voz en todas las demás aplicaciones universales de Windows, pero Unreal usa un motor más limitado para procesar la entrada de voz. Esto limita las características de entrada de voz de Unreal a las asignaciones de voz predefinidas, que se tratan en las secciones siguientes. 

## <a name="enabling-speech-recognition"></a>Habilitación del reconocimiento de voz

Si usa Windows Mixed Reality complemento, la entrada de voz no requiere ninguna api Windows Mixed Reality especiales; se basa en la API de asignación de entrada de Unreal Engine [4](https://docs.unrealengine.com/Gameplay/Input/index.html) existente. Si usa OpenXR, debe instalar además el complemento [De Microsoft OpenXR.](https://github.com/microsoft/Microsoft-OpenXR-Unreal) 

Para habilitar el reconocimiento de voz en HoloLens:
1. Seleccione **Project Configuración > platform > HoloLens > y** habilite **Micrófono.** 
2. Se ha habilitado el reconocimiento **de voz Configuración > privacidad > voz** y seleccione **Inglés.**

> [!NOTE]
> El reconocimiento de voz siempre funciona en Windows idioma de visualización configurado en **Configuración** aplicación. Se recomienda habilitar también el reconocimiento de voz en línea **para** obtener la mejor calidad de servicio.

![Windows Configuración del reconocimiento de voz](images/unreal/speech-recognition-settings.png)

3. Se mostrará un cuadro de diálogo cuando la aplicación empiece a preguntar por primera vez si desea habilitar el micrófono. Al seleccionar **Sí,** se inicia la entrada de voz en la aplicación.

## <a name="adding-speech-mappings"></a>Adición de asignaciones de voz

La conexión de voz a acción es un paso importante al usar la entrada de voz. Estas asignaciones supervisan la aplicación en busca de palabras clave de voz que un usuario podría decir y, a continuación, despeda una acción vinculada. Puede encontrar asignaciones de voz mediante:
1. Seleccione Editar **> Project Configuración**, desplácese hasta la **sección Motor** y haga clic en **Entrada.**

Para agregar una nueva asignación de voz para un comando de salto:
1. Seleccione el **+** icono situado junto a Elementos de **matriz** y rellene los valores siguientes:
    * **jumpWord para** nombre **de acción**
    * **Jump para** palabra **clave de voz**

> [!NOTE]
> Las palabras en inglés o oraciones cortas se pueden usar como palabra clave. 

![Entrada del motor UE4 Configuración](images/unreal/engine-input.png)

Las asignaciones de voz se pueden usar como componentes de entrada, como asignaciones de ejes o de acción, o como nodos de plano técnico en el panel de Graph. Por ejemplo, puede vincular el comando jump para imprimir dos registros diferentes en función de cuándo se hable la palabra:

1. Haga doble clic en un plano técnico para abrirlo en event **Graph**.
2. **Haga clic con** el  botón derecho y busque el nombre de acción de  la asignación de voz (en este caso **jumpWord)** y presione **Entrar** para agregar un nodo Acción de entrada al gráfico.
3. Arrastre y coloque el **pin presionado** en el nodo **Cadena de** impresión como se muestra en la imagen siguiente. Puede dejar el pin **Publicado** vacío, no ejecutará nada para las asignaciones de voz.
 
![Acción sencilla para la voz](images/unreal/voice-input-img-03.png)

4. Reproduce la aplicación, diga la palabra **salto** y vea cómo la consola imprime los registros.

Esa es toda la configuración que necesitará para empezar a agregar entrada de voz a las aplicaciones de HoloLens en Unreal. Puede encontrar más información sobre voz e interactividad en los vínculos siguientes y asegúrese de pensar en la experiencia que está creando para los usuarios.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, la siguiente tarea consiste en explorar las funcionalidades y API de Mixed Reality plataforma: 

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Entrada de voz](../../design/voice-input.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Interacciones instintivas](../../design/interaction-fundamentals.md)

