---
title: Gestos en Unity
description: Obtenga información sobre cómo realizar acciones en la mirada en Unity con la entrada de gestos con la mano mediante XR y las API comunes de botones y ejes.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestos, unity, mirada, entrada, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214783"
---
# <a name="gestures-in-unity"></a>Gestos en Unity

Hay dos maneras clave de tomar medidas en [](../../design/motion-controllers.md) la mirada en [Unity:](gaze-in-unity.md)gestos de mano y controladores de movimiento en HoloLens y HMD [inmersivo.](../../design/gaze-and-commit.md#composite-gestures) Puede acceder a los datos de ambos orígenes de entrada espacial a través de las mismas API en Unity.

Unity proporciona dos formas principales de acceder a los datos de entrada espacial para Windows Mixed Reality. Las API *Input.GetButton/Input.GetAxis* comunes funcionan en varios SDK XR de Unity, mientras que la API *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality expone el conjunto completo de datos de entrada espacial.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API de gestos compuestos de alto nivel (GestureRecognizer)

**Espacio de nombres:** *UnityEngine.XR.WSA.Input*<br>
**Tipos:** *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

La aplicación también puede reconocer gestos compuestos de nivel superior para orígenes de entrada espaciales, gestos de pulsación, retención, manipulación y navegación. Puede reconocer estos gestos compuestos en las manos y [los](../../design/gaze-and-commit.md#composite-gestures) controladores [de movimiento](../../design/motion-controllers.md) mediante GestureRecognizer.

Cada evento Gesture en GestureRecognizer proporciona SourceKind para la entrada, así como el rayo de destino de la cabeza en el momento del evento. Algunos eventos proporcionan información adicional específica del contexto.

Solo hay unos pocos pasos necesarios para capturar gestos mediante un reconocedor de gestos:
1. Creación de un reconocedor de gestos
2. Especificación de los gestos que se deben observar
3. Suscribirse a eventos para esos gestos
4. Inicio de la captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Creación de un reconocedor de gestos

Para usar *GestureRecognizer,* debe haber creado *un objeto GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificación de los gestos que se deben observar

Especifique los gestos que le interesan a través *de SetRecognizableGestures():*

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Suscribirse a eventos para esos gestos

Suscríbase a eventos para los gestos que le interesan.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Los gestos de navegación y manipulación se excluyen mutuamente en una instancia de *GestureRecognizer.*

### <a name="start-capturing-gestures"></a>Inicio de la captura de gestos

De forma predeterminada, *GestureRecognizer* no supervisa la entrada hasta que se llama a *StartCapturingGestures().* Es posible que se genere un evento de gesto después de llamar a *StopCapturingGestures()* si la entrada se realizó antes del fotograma donde se procesó *StopCapturingGestures().* *GestureRecognizer* recordará si estaba o no en el marco anterior en el que se produjo realmente el gesto, por lo que es confiable iniciar y detener la supervisión de gestos en función de la orientación de la mirada de este marco.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Detener la captura de gestos

Para detener el reconocimiento de gestos:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Eliminación de un reconocedor de gestos

No olvide cancelar la suscripción a eventos suscritos antes de destruir un objeto *GestureRecognizer.*

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Representación del modelo de controlador de movimiento en Unity

![Modelo y teleportación del controlador de movimiento](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo de controlador de movimiento y teleportación*

Para representar controladores de movimiento en la aplicación que coincidan con los controladores físicos que los usuarios mantienen y articulan a medida que se presionan varios botones, puede usar el **elemento prefab MotionController** en la [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Este objeto prefab carga dinámicamente el modelo glTF correcto en tiempo de ejecución desde el controlador de movimiento instalado del sistema.  Es importante cargar estos modelos dinámicamente en lugar de importarlos manualmente en el editor, para que la aplicación muestre modelos 3D físicamente precisos para cualquier controlador actual y futuro que puedan tener los usuarios.

1. Siga las [Tareas iniciales](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para descargar el Mixed Reality Toolkit y agregarlo al proyecto de Unity.
2. Si ha reemplazado la cámara por el prefab *MixedRealityCameraParent* como parte de los pasos Tareas iniciales, ya puede ir.  Ese prefab incluye la representación del controlador de movimiento.  De lo contrario, agregue *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* a la escena desde el Project panel.  Querrá agregar ese objeto prefab como elemento secundario de cualquier objeto primario que use para mover la cámara cuando el usuario teleporte dentro de la escena, de modo que los controladores se unan con el usuario.  Si la aplicación no implica la teleportación, solo tiene que agregar el objeto prefab en la raíz de la escena.

## <a name="throwing-objects"></a>Iniciar objetos

El lanzamiento de objetos en la realidad virtual es un problema más difícil de lo que puede parecer al principio. Al igual que con la mayoría de las interacciones basadas físicamente, cuando el juego se inicia de forma inesperada, es inmediatamente obvio y se interrumpe. Hemos dedicado un tiempo a pensar profundamente en cómo representar un comportamiento de lanzamiento físicamente correcto, y hemos encontrado algunas directrices, habilitadas a través de actualizaciones en nuestra plataforma, que nos gustaría compartir con usted.

Puede encontrar un ejemplo de cómo se recomienda implementar throwing [aquí.](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage) Este ejemplo sigue estas cuatro directrices:
* **Use la velocidad del controlador *en* lugar de la posición**. En la actualización de noviembre de Windows, se introdujo un cambio de comportamiento cuando se encuentra en el estado de seguimiento [posicional "Aproximado".](../../design/motion-controllers.md#controller-tracking-state) Cuando se encuentra en este estado, la información de velocidad sobre el controlador se seguirá notificando mientras creamos su alta precisión, que a menudo es más larga que la posición sigue siendo alta precisión.
* **Incorpore *la velocidad angular* del controlador**. Esta lógica está contenida en el archivo del `throwing.cs` método `GetThrownObjectVelAngVel` estático, dentro del paquete vinculado anteriormente:
   1. A medida que se conserva la velocidad angular, el objeto producido debe mantener la misma velocidad angular que tenía en el momento del lanzamiento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como es probable que el centro de masa del objeto que se produce no esté en el origen de la posición de control, es probable que tenga una velocidad diferente a la del controlador en el marco de referencia del usuario. La parte de la velocidad del objeto aportada de esta manera es la velocidad tangencial instantánea del centro de masa del objeto que se produce alrededor del origen del controlador. Esta velocidad tangencial es el producto cruzado de la velocidad angular del controlador con el vector que representa la distancia entre el origen del controlador y el centro de masa del objeto lanzado.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. La velocidad total del objeto que se produce es la suma de la velocidad del controlador y esta velocidad tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste mucha atención al momento *en que* se aplica la velocidad**. Cuando se presiona un botón, ese evento puede tardar hasta 20 ms en llegar a través de Bluetooth al sistema operativo. Esto significa que si sondea un cambio de estado del controlador de presionado a no presionado o al revés, el controlador que posea la información que obtiene con él se adelantará realmente a este cambio de estado. Además, la posición del controlador presentada por nuestra API de sondeo se predice hacia delante para reflejar una posición probable en el momento en que se mostrará el fotograma, que podría ser superior a 20 ms en el futuro. Esto es bueno *para* representar objetos mantenidos,  pero representa nuestro problema de tiempo para dirigirse al objeto a medida que calculamos la trayectoria en el momento en que el usuario lanzó el lanzamiento. Afortunadamente, con la actualización de noviembre, cuando se envía un evento de Unity como *InteractionSourcePressed* o *InteractionSourceReleased,* el estado incluye los datos de posición históricos de atrás cuando se presiona o se libera el botón.  Para obtener la representación del controlador y el destino del controlador más precisos durante los lanzamientos, debe usar correctamente el sondeo y los eventos, según corresponda:
   * Para **que el** controlador represente cada fotograma, la aplicación debe colocar el *GameObject* del controlador en la posición del controlador de predicción hacia delante para el tiempo de foton del fotograma actual.  Estos datos se obtienen de las API de sondeo de Unity, como *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. Wsa. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * En **el caso de los** controladores que tienen como destino una publicación o una publicación, la aplicación debe convertir y calcular los cálculos en función de la posición histórica del controlador para ese evento de lanzamiento o de presión.  Estos datos se obtienen de las API de eventos de Unity, como *[InteractionManager.InteractionSourcePressed.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*
* **Use la posición de control**. Angular velocidad y velocidad se notifican en relación con la posición del control, no con la posición del puntero.

El lanzamiento seguirá mejorando con futuras Windows actualizaciones, y puede esperar encontrar más información al respecto aquí.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Controladores de gestos y movimiento en MRTK

Puede acceder al gesto y al controlador de movimiento desde el Administrador de entrada.

* [Gesto en MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Controlador de movimiento en MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>Seguimiento de tutoriales

Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en Mixed Reality Academy:

- [MR Input 211: gesto](tutorials/holograms-211.md)
- [MR Input 213: controladores de movimiento](../../deprecated/mixed-reality-213.md)

[![Mr Input 213 : controlador de movimiento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Mr Input 213 : controlador de movimiento*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unity que hemos diseñado, se encuentra a la mitad de la exploración de los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Seguimiento de manos y ocular](./hand-eye-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también

* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)