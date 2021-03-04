---
title: Gestos en Unity
description: Obtenga información sobre cómo realizar una acción en Unity en Unity con la entrada de gestos de mano mediante XR y las API de eje y de botón comunes.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestos, Unity, miras, entrada, auriculares de realidad mixta, auriculares de la realidad mixta de Windows, auriculares de realidad virtual, MRTK, kit de herramientas de realidad mixta
ms.openlocfilehash: 4c3db98e3047cdc74663c5cbee1c4607b77008e0
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759086"
---
# <a name="gestures-in-unity"></a>Gestos en Unity

Hay dos formas clave de tomar medidas en su [mirada en Unity](gaze-in-unity.md), [gestos de mano](../../design/gaze-and-commit.md#composite-gestures) y [controladores de movimiento](../../design/motion-controllers.md) en HoloLens y HMDs envolventes. Puede tener acceso a los datos de los dos orígenes de entrada espacial a través de las mismas API en Unity.

Unity proporciona dos maneras principales de tener acceso a los datos de entrada espacial para Windows Mixed Reality. Las API de *Input. GetButton/Input. GetAxis* comunes funcionan en varios SDK de Unity XR, mientras que la API *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality expone el conjunto completo de datos de entrada espacial.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API de gesto compuesto de alto nivel (GestureRecognizer)

**Espacio de nombres:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

La aplicación también puede reconocer gestos compuestos de nivel superior para orígenes de entrada espaciales, puntear, retener, manipular y gestos de navegación. Puede reconocer estos gestos compuestos a través de las [manos](../../design/gaze-and-commit.md#composite-gestures) y [los controladores de movimiento](../../design/motion-controllers.md) mediante GestureRecognizer.

Cada evento de gesto en el GestureRecognizer proporciona el SourceKind para la entrada, así como el rayo del cabezal de destino en el momento del evento. Algunos eventos proporcionan información adicional específica del contexto.

Solo se requieren algunos pasos para capturar gestos mediante un reconocedor de gestos:
1. Crear un nuevo reconocedor de gestos
2. Especificar los gestos que se van a inspeccionar
3. Suscripción a eventos para esos gestos
4. Iniciar la captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Crear un nuevo reconocedor de gestos

Para usar *GestureRecognizer*, debe haber creado un *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificar los gestos que se van a inspeccionar

Especifique los gestos que le interesan a través de *SetRecognizableGestures ()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Suscripción a eventos para esos gestos

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
>Los gestos de navegación y manipulación se excluyen mutuamente en una instancia de un *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Iniciar la captura de gestos

De forma predeterminada, un *GestureRecognizer* no supervisa la entrada hasta que se llama a *StartCapturingGestures ()* . Es posible que se genere un evento de gesto después de que se llame a *StopCapturingGestures ()* si la entrada se realizó antes que el marco en el que se procesó *StopCapturingGestures ()* . El *GestureRecognizer* recordará si está activado o desactivado durante el fotograma anterior en el que se produjo realmente el gesto, por lo que es confiable iniciar y detener la supervisión de gestos según el destino de la mirada a este fotograma.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Detener captura de movimientos

Para detener el reconocimiento de gestos:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Quitar un reconocedor de gestos

Recuerde cancelar la suscripción a los eventos suscritos antes de destruir un objeto *GestureRecognizer* .

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

![Modelo de controlador de movimiento y teleportabilidad](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo de controlador de movimiento y teleportabilidad*

Para representar los controladores de movimiento en la aplicación que coincidan con las controladoras físicas que están manteniendo los usuarios y articular a medida que se presionan varios botones, puede usar **MotionController recurso prefabricado** en el [Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Este recurso prefabricado carga dinámicamente el modelo de glTF correcto en tiempo de ejecución desde el controlador de controlador de movimiento instalado del sistema.  Es importante cargar estos modelos dinámicamente en lugar de importarlos manualmente en el editor, de modo que la aplicación muestre modelos 3D físicamente precisos para cualquier controlador actual y futuro que puedan tener los usuarios.

1. Siga las instrucciones [Introducción](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para descargar el kit de herramientas de realidad mixta y agréguelo al proyecto de Unity.
2. Si ha reemplazado la cámara con el recurso prefabricado de *MixedRealityCameraParent* como parte de los pasos introducción, está listo para empezar.  Ese recurso prefabricado incluye la representación del controlador de movimiento.  En caso contrario, agregue *assets/HoloToolkit/INPUT/Prefabs/MotionControllers. recurso prefabricado* a la escena desde el panel Proyecto.  Querrá agregar ese recurso prefabricado como elemento secundario del objeto primario que usa para mover la cámara cuando el usuario teletransporta dentro de la escena, de modo que los controladores entren junto con el usuario.  Si la aplicación no implica teletransportarse, solo tiene que agregar el recurso prefabricado en la raíz de la escena.

## <a name="throwing-objects"></a>Producir objetos

Lanzar objetos en realidad virtual es un problema más difícil de lo que puede parecer al principio. Al igual que con la mayoría de las interacciones basadas físicamente, al iniciar el juego funciona de forma inesperada, es evidente de inmediato e interrumpe la inmersión. Hemos dedicado mucho tiempo a pensar en el modo de representar un comportamiento de lanzamiento que se ha corregido físicamente y han llegado algunas directrices, habilitadas a través de las actualizaciones de nuestra plataforma, que nos gustaría compartir con usted.

Puede encontrar un ejemplo de cómo se recomienda implementar el lanzamiento [aquí](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este ejemplo sigue estas cuatro instrucciones:
* **Use la *velocidad* del controlador en lugar de la posición**. En la actualización de noviembre de Windows, se presentó un cambio de comportamiento en el [Estado de seguimiento posicional ' ' aproximado](../../design/motion-controllers.md#controller-tracking-state)' '. Cuando se encuentra en este estado, se seguirá informando de la información de velocidad de la controladora mientras creemos su alta precisión, que suele ser mayor que la posición es una precisión alta.
* **Incorpore la *velocidad angular* del controlador**. Esta lógica está contenida en el `throwing.cs` archivo en el `GetThrownObjectVelAngVel` método estático, dentro del paquete vinculado anteriormente:
   1. A medida que se conserva la velocidad angular, el objeto producido debe mantener la misma velocidad angular que tenía en el momento del lanzamiento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Dado que es probable que el centro de la masa del objeto iniciado no sea el origen de la representación del puño, es probable que tenga una velocidad distinta a la del controlador en el marco de referencia del usuario. La parte de la velocidad del objeto aportada de esta manera es la velocidad tangencial instantánea del centro de la masa del objeto producido en torno al origen del controlador. Esta velocidad tangencial es el producto cruzado de la velocidad angular del controlador con el vector que representa la distancia entre el origen del controlador y el centro de la masa del objeto iniciado.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. La velocidad total del objeto generado es la suma de la velocidad del controlador y esta velocidad tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste mucha atención a la *hora* a la que se aplica la velocidad**. Cuando se presiona un botón, puede tardar hasta 20 ms para ese evento en pasar a través de Bluetooth al sistema operativo. Esto significa que, si sondea un cambio de estado del controlador de presionado a no presionado o viceversa, el controlador de la información de la forma que se obtiene se encuentra realmente por encima de este cambio en el estado. Además, la causa del controlador presentada por nuestra API de sondeo se predice para reflejar una posible suposición en el momento en que se muestra el fotograma, lo que podría ser superior a 20 MS en el futuro. Esto es adecuado para la *representación* de objetos retenidos, pero proporciona un problema de tiempo para el *objetivo* del objeto a medida que calculamos la trayectoria en el momento en que el usuario liberó el lanzamiento. Afortunadamente, con la actualización de noviembre, cuando se envía un evento de Unity, como *InteractionSourcePressed* o *InteractionSourceReleased* , el estado incluye los datos de la representación histórica al presionar o soltar el botón.  Para obtener la representación del controlador y el destino del controlador más precisos durante las throws, debe usar correctamente el sondeo y los eventos, según corresponda:
   * Para que el **controlador presente** cada fotograma, la aplicación debe colocar el *GameObject* del controlador en la representación del controlador de predicción para la hora de Photon del marco actual.  Estos datos se obtienen de las API de sondeo de Unity como *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * En el caso de que el **controlador se dirija** a una imprenta o una versión, la aplicación debe Raycast y calcular las trayectorias en función de la suposición del controlador histórico para ese evento Press o Release.  Estos datos se obtienen de las API de eventos de Unity, como *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Utilice la postura de control**. La velocidad y la velocidad de angular se registran en relación con la pose de control, no con la función de puntero.

El lanzamiento continuará mejorando con futuras actualizaciones de Windows y puede esperar encontrar más información aquí.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Gestos y controladores de movimiento en MRTK

Puede tener acceso al gesto y al controlador de movimiento desde el administrador de entrada.
* [Gesto en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/gestures.md)
* [Controlador de movimiento en MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md)


## <a name="follow-along-with-tutorials"></a>Seguimiento de tutoriales

Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en la Academia de realidad mixta:

- [MR Input 211: gesto](tutorials/holograms-211.md)
- [MR Input 213: controladores de movimiento](../../deprecated/mixed-reality-213.md)

[![Entrada MR 213-controlador de movimiento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213-controlador de movimiento*

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si está siguiendo el viaje de desarrollo de Unity que hemos diseñado, está a la mitad de explorar los bloques de creación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Seguimiento de manos y ocular](./hand-eye-in-unity.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Experiencias compartidas](shared-experiences-in-unity.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también

* [Mirada-cabeza y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)