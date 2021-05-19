---
title: Grabación de animaciones de entrada
description: Documentación sobre el sistema de grabación de animaciones de entrada en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 81e49178a9f218e5d3be796ec6253ccabe5d44fc
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143918"
---
# <a name="input-animation-recording"></a>Grabación de animación de entrada

MRTK cuenta con un sistema de grabación mediante el cual los datos de movimiento de la cabeza y seguimiento de las manos se pueden almacenar en archivos de animación. A continuación, los datos registrados se pueden reproducir mediante el sistema [de simulación de entrada](input-simulation-service.md).

La entrada de grabación es una herramienta útil en una variedad de situaciones:

* Creación de pruebas automatizadas para la interacción, manipulaciones, solucionadores, etc. La creación del movimiento de controladores y manos para estas pruebas puede llevar mucho tiempo. La entrada de grabación directamente puede acelerar el proceso y proporcionar datos reales.
* Enseñar el uso de elementos de la experiencia de usuario a través de animaciones.
  Mostrar a los usuarios cómo interactuar con botones y otros objetos puede suavizar la curva de aprendizaje.
* Depuración de un comportamiento inesperado que se puede encontrar durante el uso normal.
  El sistema de grabación admite un concepto de "búfer gradual" que permite grabar entradas recientes en segundo plano.
  Vea [Input Recording Service](#input-recording-service).

## <a name="recording-and-playback-services"></a>Servicios de grabación y reproducción

Se proporcionan dos servicios del sistema de entrada para registrar y reproducir entradas, respectivamente.

### <a name="input-recording-service"></a>Servicio de grabación de entrada

[`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) toma datos de la transformación de la cámara principal y los controladores de mano activos y los almacena en un búfer interno. Cuando se solicitan, estos datos se serializan en archivos binarios para su almacenamiento y posterior reproducción.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_RecordingDiagram.png" title="Animación de entrada de grabación" width="80%" alt="Recording diagram" class="center" />
</a>

Para iniciar la grabación de la entrada, llame a [`StartRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StartRecording) la función . [`StopRecording`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.StopRecording) pausará la grabación (pero no descartará los datos registrados hasta ahora, [`DiscardRecordedInput`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.DiscardRecordedInput) use para hacerlo si es necesario).

De forma predeterminada, el tamaño del búfer de grabación está limitado a 30 segundos. Esto permite que el servicio de grabación mantenga la grabación en segundo plano sin acumular demasiados datos y, a continuación, guarde los últimos 30 segundos cuando sea necesario. El intervalo de tiempo se puede cambiar mediante la [`RecordingBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.RecordingBufferTimeLimit) propiedad o la grabación puede ser ilimitada mediante la opción [`UseBufferTimeLimit`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.UseBufferTimeLimit) .

Los datos del búfer de grabación se pueden guardar en un archivo binario mediante [la función SaveInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputRecordingService.SaveInputAnimation*)

Para obtener más información sobre el formato de archivo binario, vea [Especificación de formato de archivo de animación de entrada](input-animation-file-format.md).

### <a name="input-playback-service"></a>Servicio de reproducción de entrada

[`InputPlaybackService`](xref:Microsoft.MixedReality.Toolkit.Input.InputPlaybackService) lee un archivo binario con datos de animación de entrada y, a continuación, aplica estos datos a través de [InputSimulationService](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) para volver a crear los movimientos registrados.

<a target="_blank" href="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png">
  <img src="../images/input-simulation/MRTK_InputAnimation_PlaybackDiagram.png" title="Reproducción de la animación de entrada" width="80%" alt="Play Back diagram" class="center" />
</a>

Para empezar a reproducir la animación de entrada, se debe cargar desde un archivo mediante la [función LoadInputAnimation.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LoadInputAnimation*)

Llame [a Reproducir,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [Pausar](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Play) [o Detener para](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.Stop) controlar la reproducción de animación.

El tiempo de animación actual también se puede controlar directamente con la [propiedad LocalTime.](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime)

> [!WARNING]
> El bucle o el restablecimiento de la animación o configuración de entrada directamente mediante la limpieza de la escala de tiempo puede producir resultados inesperados [`LocalTime`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputPlaybackService.LocalTime) al manipular la escena. Solo se registran los movimientos de entrada, no se restablecerán los cambios adicionales, como mover objetos o voltear conmutadores. Asegúrese de volver a cargar la escena si se han realizado cambios irreversibles.

### <a name="editor-tools-for-recording-and-playing-input-animation"></a>Herramientas del editor para grabar y reproducir animaciones de entrada

Existen varias herramientas en el editor de Unity para grabar y examinar la animación de entrada. Se puede acceder a estas herramientas en la ventana herramientas de simulación de entrada [,](input-simulation-service.md#input-simulation-tools-window)que se puede abrir desde el menú Mixed Reality Toolkit > Utilities > Input Simulation (Simulación _de_ entrada).

> [!NOTE]
> La grabación y reproducción de entrada solo funcionan durante el modo de reproducción.

La ventana de grabación de entrada tiene dos modos:

* _Grabación de_ entrada de grabación durante el modo de reproducción y guardado en archivos de animación.

  Al alternar en el botón de grabación, [`InputRecordingService`](xref:Microsoft.MixedReality.Toolkit.Input.InputRecordingService) está habilitado para grabar la entrada.
  Al desactivar el botón de grabación, se muestra una selección de guardado de archivo y la animación de entrada grabada se guarda en el destino seleccionado.

  El límite de tiempo del búfer también se puede cambiar en este modo.

* _Reproducción para_ cargar archivos de animación y volver a crear la entrada a través del sistema de simulación de entrada.

  Primero se debe cargar una animación en este modo. Después de grabar la entrada en modo de grabación, la animación resultante se carga automáticamente. También puede hacer clic en el botón "Cargar" para seleccionar un archivo de animación existente.

  Los botones de control de tiempo de izquierda a derecha son:

  * _Restablezca_ el tiempo de reproducción al inicio de la animación.
  * _Reproducir animación_ continuamente a lo largo del tiempo.
  * _Avance_ un paso.

  El control deslizante también se puede usar para limpiar la escala de tiempo de animación.

> [!WARNING]
> El bucle o el restablecimiento de la animación de entrada o la limpieza de la escala de tiempo pueden producir resultados inesperados al manipular la escena. Solo se registran los movimientos de entrada, no se restablecerán los cambios adicionales, como mover objetos o voltear conmutadores. Asegúrese de volver a cargar la escena si se han realizado cambios irreversibles.
