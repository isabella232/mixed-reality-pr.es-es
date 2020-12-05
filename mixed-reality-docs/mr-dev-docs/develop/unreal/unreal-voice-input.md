---
title: Entrada de voz
description: Tutorial sobre la configuración y el uso de la entrada de voz en HoloLens 2 e inreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality, inreal, no real, motor 4, UE4, HoloLens 2, voz, entrada de voz, reconocimiento de voz, realidad mixta, desarrollo, características, documentación, guías, hologramas, desarrollo de juegos, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609756"
---
# <a name="voice-input-in-unreal"></a>Entrada de voz en inreal

La entrada de voz en no real permite interactuar con un holograma sin tener que usar gestos de mano y solo es compatible con HoloLens 2. La entrada de voz en HoloLens 2 se basa en el mismo motor que admite la voz en todas las demás aplicaciones universales de Windows, pero no real usa un motor más limitado para procesar la entrada de voz. Esto limita las características de entrada de voz en no real a las asignaciones de voz predefinidas, que se describen en las secciones siguientes. 

## <a name="enabling-speech-recognition"></a>Habilitación del reconocimiento de voz

Para habilitar el reconocimiento de voz en HoloLens:
1. Seleccione **configuración del proyecto > plataforma > HoloLens > funcionalidades** y habilite el **micrófono**. 
2. Habilitado el reconocimiento de voz en **configuración > privacidad > voz** y seleccione **Inglés**.

> [!NOTE]
> El reconocimiento de voz siempre funciona en el idioma de visualización de Windows configurado en la aplicación de **configuración** . Se recomienda habilitar también el reconocimiento de **voz en línea** para obtener la mejor calidad de servicio.

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

3. Se mostrará un cuadro de diálogo cuando se inicie la aplicación por primera vez para preguntar si desea habilitar el micrófono. Si selecciona **sí** , se iniciará la entrada de voz en la aplicación.

La entrada de voz no requiere ninguna API especial de Windows Mixed Reality; se basa en la API de asignación de [entrada](https://docs.unrealengine.com/Gameplay/Input/index.html) de Engine 4 inreal Engine existente. 

## <a name="adding-speech-mappings"></a>Agregar asignaciones de voz

La conexión de voz a la acción es un paso importante cuando se usa la entrada de voz. Estas asignaciones supervisan las palabras clave de la aplicación para la voz que un usuario podría decir y, a continuación, activa una acción vinculada. Puede buscar las asignaciones de voz:
1. Seleccione **editar > configuración del proyecto**, desplácese hasta la sección **motor** y haga clic en **entrada**.

Para agregar una nueva asignación de voz para un comando de salto:
1. Seleccione el **+** icono situado junto a **elementos** de la matriz y rellene los valores siguientes:
    * **jumpWord** para **el nombre de acción**
    * **saltar** la **palabra clave de voz**

> [!NOTE]
> Cualquier palabra o frase en inglés (s) se puede usar como palabra clave. 

![Configuración de entrada del motor de UE4](images/unreal/engine-input.png)

Las asignaciones de voz se pueden usar como componentes de entrada como asignaciones de acción o de eje o como nodos de plano en el gráfico de eventos. Por ejemplo, puede vincular el comando de salto para imprimir dos registros diferentes en función de Cuándo se pronuncia la palabra:

1. Haga doble clic en un plano para abrirlo en el **gráfico de eventos**.
2. **Haga clic con el botón derecho** y busque el nombre de la **acción** de la asignación de voz (en este caso, **jumpWord**) y presione **entrar** para agregar un nodo de **acción de entrada** al gráfico.
3. Arrastre y coloque el anclaje **presionado** en el nodo de la **cadena de impresión** , tal como se muestra en la imagen siguiente. Puede dejar el PIN **liberado** vacío, no ejecutará nada para las asignaciones de voz.
 
![Acción simple para voz](images/unreal/voice-input-img-03.png)

4. Juegue a la aplicación, por ejemplo, la palabra **Jump** y observe que la consola imprime los registros.

Esta es toda la configuración que necesitará para empezar a agregar entradas de voz a las aplicaciones de HoloLens en el mundo real. Puede encontrar más información sobre la voz y la interactividad en los vínculos siguientes y asegúrese de pensar en la experiencia que está creando para los usuarios.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo no real que hemos diseñado, la tarea siguiente está explorando las funcionalidades y API de la plataforma de realidad mixta: 

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Entrada de voz](../../design/voice-input.md)
* [Mirada y confirmación](../../design/gaze-and-commit.md)
* [Interacciones instintivas](../../design/interaction-fundamentals.md)

