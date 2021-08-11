---
title: 'Entrada de HoloLens de primera generación (211): gesto'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los detalles de los conceptos de gestos.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gesture, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: 75cfb836e5a9702c1d949ed57450984081db0c5d6ec14c76cae5148edf637e7e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206434"
---
# <a name="hololens-1st-gen-input-211-gesture"></a>HoloLens (1ª generación) Entrada 211: Gesto

>[!IMPORTANT]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (1ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se actualizarán_** con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

[Los gestos](../../../design/gaze-and-commit.md#composite-gestures) convierten la intención del usuario en acción. Con los gestos, los usuarios pueden interactuar con los hologramas. En este curso, aprenderemos a realizar un seguimiento de las manos del usuario, responder a la entrada del usuario y enviar comentarios al usuario en función del estado y la ubicación de la mano.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

En [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md), hemos usado un sencillo gesto de pulsar el aire para interactuar con nuestros hologramas. Ahora, vamos a ir más allá del gesto de pulsar el aire y exploraremos nuevos conceptos para:

* Detecte cuándo se realiza el seguimiento de la mano del usuario y proporcione comentarios al usuario.
* Use un gesto de navegación para girar los hologramas.
* Proporcione comentarios cuando la mano del usuario esté a punto de salir de la vista.
* Use eventos de manipulación para permitir a los usuarios mover hologramas con las manos.

En este curso, volveremos a visitar el explorador de modelos del proyecto de **Unity,** que hemos creado en [mr input 210](holograms-210.md). Nuestro amigo astronauta ha vuelto para ayudarnos a explorar estos nuevos conceptos de gestos.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el Mixed Reality Toolkit. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la pósteridad y porque los conceptos tratados siguen siendo aplicables.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada de realidad mixta (211): Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../../develop/install-the-tools.md)
* Alguna capacidad básica de programación de C#.
* Debe haber completado [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Debe haber completado la [entrada mr 210](holograms-210.md).
* Un HoloLens configurado [para el desarrollo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
* Des archive los archivos en el escritorio u otra ubicación de fácil acceso.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Errata y Notes

* "Habilitar Solo mi código" debe deshabilitarse *(desactivado)* en Visual Studio en Herramientas->Opciones->Depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0: Configuración de Unity

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **Open** (Abrir).
3. Vaya a la **carpeta Gesto** que anteriormente des archivó.
4. Busque y seleccione la carpeta **Starting** / **Model Explorer (Iniciar explorador de** modelos).
5. Haga clic en **el botón Seleccionar** carpeta.
6. En el **panel Project,** expanda la **carpeta Escenas.**
7. Haga doble clic **en ModeloExplorador** de la escena para cargarla en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **File > Build Configuración**.
2. Si **Scenes/ModelExplorer no** aparece en **Scenes In Build (Escenas** en la compilación), haga clic en **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena.
3. Si va a desarrollar específicamente para HoloLens, establezca **Dispositivo de destino** en **HoloLens**. De lo contrario, déjelo en **Cualquier dispositivo.**
4. Asegúrese **de que Tipo** de compilación está establecido en **D3D** y **sdk** está establecido en Instalado más reciente **(que** debe ser SDK 16299 o posterior).
5. Haga clic en **Generar**.
6. Cree una **carpeta denominada** "App".
7. Haga clic en la **carpeta** Aplicación.
8. Presione **Seleccionar carpeta y** Unity comenzará a compilar el proyecto para Visual Studio.

Cuando Unity haya terminado, aparecerá Explorador de archivos ventana.

1. Abra la **carpeta** Aplicación.
2. Abra la **solución ModelExplorer Visual Studio**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x86.**
2. Haga clic en la flecha desplegable situada junto al botón Máquina local y seleccione **Equipo remoto.**
3. Escriba **la HoloLens IP del dispositivo y** establezca Modo de autenticación en Universal **(protocolo sin cifrar).** Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en Configuración > **Network & Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar con [Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Cuando se haya implementado la aplicación, descarte **fitbox** con un **gesto de selección.**

Si se implementa en un casco envolvente:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x64.**
2. Asegúrese de que el destino de implementación está establecido en **Máquina local.**
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**.
4. Cuando la aplicación se haya implementado, descarte **fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojos en el panel Visual Studio errores. Es seguro omitirlos. Cambie al panel Salida para ver el progreso real de la compilación. Los errores del panel Salida requerirán que realice una corrección (la mayoría de las veces se deben a un error en un script).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1: Comentarios detectados a mano

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Suscríbase a eventos de seguimiento manual.
* Use los comentarios del cursor para mostrar a los usuarios cuándo se realiza el seguimiento de una mano.

>[!NOTE]
>En HoloLens 2 , las manos detectadas se activa cada vez que las manos están visibles (no solo cuando un dedo apunta hacia arriba).

### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** expanda el **objeto InputManager.**
* Busque y seleccione el **objeto GesturesInput.**

El script **InteractionInputSource.cs** realiza estos pasos:

1. Se suscribe a los eventos InteractionSourceDetected e InteractionSourceLost.
2. Establece el estado HandDetected.
3. Cancela la suscripción de los eventos InteractionSourceDetected e InteractionSourceLost.

A continuación, actualizaremos el cursor de [mr input 210](holograms-210.md) a uno que muestre comentarios en función de las acciones del usuario.

1. En el panel **Jerarquía,** seleccione el **objeto Cursor** y elimínelo.
2. En el **Project,** busque **CursorWithFeedback** y arrástrelo al panel **Jerarquía.**
3. Haga clic en **InputManager** en el **panel** Jerarquía y arrastre  el objeto **CursorWithFeedback** desde la jerarquía hasta el campo **Cursor** de **SimpleSinglePointerSelector** de InputManager, en la parte inferior del **inspector**.
4. Haga clic en **cursorWithFeedback en** la **jerarquía**.
5. En el **panel Inspector,** expanda **Datos de estado del cursor** en el script Cursor **de** objeto.

Los **datos de estado del cursor** funcionan de esta forma:

* Cualquier **estado observe** significa que no se detecta ninguna mano y el usuario simplemente está mirando alrededor.
* Cualquier **estado Interact** significa que se detecta una mano o un controlador.
* Cualquier **estado hover** significa que el usuario está mirando un holograma.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, use **File > Build Configuración** para recompilar la aplicación.
* Abra la **carpeta** Aplicación.
* Si aún no está abierto, abra el archivo **ModelExplorer Visual Studio solution**.
  * (Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "Recargar todo" cuando se le solicite).
* En Visual Studio, haga clic **en Depurar -> Iniciar** sin depurar o presione Ctrl + **F5**.
* Una vez que la aplicación se implemente en HoloLens, descarte la caja de ajuste mediante el gesto de pulsar en el aire.
* Mueva la mano a la vista y apunte el dedo índice al cielo para iniciar el seguimiento de las manos.
* Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.
* Observe cómo cambia el cursor cuando se detecta la mano y, a continuación, se pierde de la vista.
* Si está en un casco envolvente, tendrá que conectarse y desconectar el controlador. Estos comentarios se vuelven menos interesantes en un dispositivo inmersivo, ya que un controlador conectado siempre estará "disponible".

## <a name="chapter-2---navigation"></a>Capítulo 2: Navegación

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use eventos de gesto de navegación para girar al astronauta.

### <a name="instructions"></a>Instrucciones

Para usar gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.cs** para girar objetos cuando se produzca el gesto de navegación. Además, agregaremos comentarios al cursor para mostrarlos cuando la navegación esté disponible.

1. En el panel **Jerarquía,** expanda **CursorWithFeedback**.
2. En la **Hologramas,** busque el **recurso ScrollFeedback.**
3. Arrastre y coloque el objeto **prefab ScrollFeedback** en **cursorWithFeedback** GameObject en la **jerarquía**.
4. Haga clic **en CursorWithFeedback**.
5. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
6. En el menú, escriba en el cuadro de búsqueda **CursorFeedback**. Seleccione el resultado de la búsqueda.
7. Arrastre y coloque el objeto **ScrollFeedback** desde la jerarquía hasta la propiedad **Scroll Detected Game Object** del componente **Cursor Feedback** del **inspector**. 
8. En el panel **Jerarquía,** seleccione el **objeto AstroMan.**
9. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
10. En el menú, escriba en el cuadro de búsqueda **Acción de gesto**. Seleccione el resultado de la búsqueda.

A continuación, **abra GestureAction.cs** en Visual Studio. En el ejercicio de codificación 2.c, edite el script para hacer lo siguiente:

1. **Gira el objeto AstroMan** cada vez que se realiza un gesto de navegación.
2. Calcule **rotationFactor** para controlar la cantidad de rotación aplicada al objeto.
3. **Gira el objeto** alrededor del eje Y cuando el usuario mueve la mano a la izquierda o a la derecha.

Complete los ejercicios de codificación 2.c en el script o reemplace el código por la solución completa siguiente:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Observará que los demás eventos de navegación ya están rellenados con cierta información. Insertamos el Elemento GameObject en la pila modal inputSystem del Toolkit, por lo que el usuario no tiene que mantener el foco en el astronauta una vez que se ha iniciado la rotación. En consecuencia, se quitará el elemento GameObject de la pila una vez completado el gesto.

### <a name="build-and-deploy"></a>Compilación e implementación

1. Recompile la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutarla en el HoloLens.
2. Al mirar al astronauta, deben aparecer dos flechas a cada lado del cursor. Este nuevo objeto visual indica que el astronauta se puede girar.
3. Coloque la mano en la posición lista (dedo índice apuntando hacia el cielo) para que el HoloLens empiece a realizar el seguimiento de la mano.
4. Para girar el astronauta, reduzca el dedo índice a una posición de reducción y, a continuación, mueva la mano a la izquierda o a la derecha para desencadenar el gesto NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3: Guía de mano

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use **la puntuación de instrucciones a mano** para ayudar a predecir cuándo se perderá el seguimiento de las manos.
* Proporcione **comentarios sobre el cursor para** mostrar cuándo la mano del usuario se acerca al borde de la cámara.

### <a name="instructions"></a>Instrucciones

1. En el panel **Jerarquía,** seleccione el **objeto CursorWithFeedback.**
2. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
3. En el menú, escriba en el cuadro de búsqueda **Manual de instrucciones.** Seleccione el resultado de la búsqueda.
4. En el **Project** panel **Hologramas** carpeta, busque el **recurso HandGuidanceFeedback.**
5. Arrastre y coloque el **recurso HandGuidanceFeedback** en la propiedad **Hand Guidance Indicator** del panel **Inspector.**

### <a name="build-and-deploy"></a>Compilación e implementación

* Recompile la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.
* Lleve la mano a la vista y suba el dedo índice para realizar el seguimiento.
* Comience a girar al astronauta con el gesto de navegación (acercar el dedo índice y el dedo).
* Mueva la mano más a la izquierda, a la derecha, hacia arriba y hacia abajo.
* A medida que la mano se acerca al borde del marco de gestos, debe aparecer una flecha junto al cursor para advertirle de que se perderá el seguimiento de las manos. La flecha indica qué dirección debe mover la mano para evitar que se pierda el seguimiento.

## <a name="chapter-4---manipulation"></a>Capítulo 4: Manipulación

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Use eventos de manipulación para mover al astronauta con las manos.
* Proporcione comentarios sobre el cursor para que el usuario sepa cuándo se puede usar la manipulación.

### <a name="instructions"></a>Instrucciones

GestureManager.cs y AstronautManager.cs nos permitirán hacer lo siguiente:

1. Use la palabra clave de voz **"Move Astronaut" (Mover astronauta)** para habilitar **los** gestos de manipulación y **"Rotate Astronaut" (Girar astronauta)** para deshabilitarlos.
2. Cambie a para responder al reconocedor **de gestos de manipulación**.

Comencemos.

1. En el panel **Jerarquía,** cree un elemento GameObject vacío. Asíételo "**AstronautManager**".
2. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
3. En el menú, escriba en el cuadro de búsqueda **Astronaut Manager**. Seleccione el resultado de la búsqueda.
4. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
5. En el menú, escriba en el cuadro de búsqueda Origen de **entrada de voz.** Seleccione el resultado de la búsqueda.

Ahora agregaremos los comandos de voz necesarios para controlar el estado de interacción del astronauta.

1. Expanda la **sección Palabras clave** del **inspector**.
2. Haga clic **+** en en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **Move Astronaut**. Si lo desea, no dude en agregar un método abreviado de teclado.
4. Haga clic **+** en en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **Rotate Astronaut**. Si lo desea, no dude en agregar un método abreviado de teclado.
6. El código de controlador correspondiente se puede encontrar **en GestureAction.cs**, en el controlador **ISpeechHandler.OnSpeechKeywordRecognized.**

![Configuración del origen de entrada de voz para el capítulo 4](images/holograms211-speech.png)

A continuación, configuraremos los comentarios de manipulación en el cursor.

1. En el **panel Project** de **Hologramas,** busque el **recurso PathingFeedback.**
2. Arrastre y coloque el objeto **prefab PathingFeedback** en el **objeto CursorWithFeedback** de la **jerarquía**.
3. En el panel **Jerarquía,** haga clic **en CursorWithFeedback**.
4. Arrastre y coloque el objeto **PathingFeedback** desde la jerarquía hasta la propiedad **Pathing Detected Game Object** del componente Cursor **Feedback** del **inspector**. 

Ahora es necesario agregar código a **GestureAction.cs** para habilitar lo siguiente:

1. Agregue código **a** **la función IManipulationHandler.OnManipulationUpdated,** que moverá al astronauta cuando se detecte un gesto de manipulación.
2. Calcule **el vector de** movimiento para determinar a dónde debe moverse el astronauta en función de la posición de la mano.
3. **Mueva** el astronauta a la nueva posición.

Complete el ejercicio de codificación 4.a en **GestureAction.cs** o use nuestra solución completa a continuación:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilación e implementación

* Recompile en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.
* Mueva la mano delante de la HoloLens y mueva el dedo índice para que se pueda realizar el seguimiento.
* Centre el cursor sobre el astronauta.
* Diga "Move Astronaut" (Mover astronauta) para mover al astronauta con un gesto de manipulación.
* Deben aparecer cuatro flechas alrededor del cursor para indicar que el programa responderá ahora a los eventos de manipulación.
* Bajar el dedo índice hacia abajo hasta el control y mantenerlos juntos.
* Al mover la mano, el astronauta también se moverá (esto es manipulación).
* Elevar el dedo índice para detener la manipulación del astronauta.
* Nota: Si no dice "Mover astronauta" antes de mover la mano, se usará en su lugar el gesto navegación.
* Diga "Rotate Astronaut" (Girar astronauta) para volver al estado rotable.

## <a name="chapter-5---model-expansion"></a>Capítulo 5: Expansión de modelos

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda el modelo Astronaut en varias partes más pequeñas con las que el usuario pueda interactuar.
* Mueva cada pieza individualmente mediante gestos de navegación y manipulación.

### <a name="instructions"></a>Instrucciones

En esta sección, realizaremos las siguientes tareas:

1. Agregue una nueva palabra clave "**Expandir modelo**" para expandir el modelo de astronauta.
2. Agregue una nueva palabra clave "**Reset Model**" para devolver el modelo a su formulario original.

Para ello, agregaremos dos palabras clave más al origen de entrada de voz del capítulo anterior. También mostraremos otra manera de controlar los eventos de reconocimiento.

1. Haga clic de nuevo **en AstronautManager** **en el inspector y** expanda la sección **Palabras** clave del **inspector**.
2. Haga clic **+** en en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **Expandir modelo.** Si lo desea, no dude en agregar un método abreviado de teclado.
4. Haga clic **+** en en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **Restablecer modelo.** Si lo desea, no dude en agregar un método abreviado de teclado.
6. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
7. En el menú, escriba en el cuadro de búsqueda **Controlador de entrada de voz**. Seleccione el resultado de la búsqueda.
8. Active **Is Global Listener**(Es el agente de escucha global), ya que queremos que estos comandos funcionen independientemente del Elemento GameObject que nos centramos.
9. Haga clic en **+** el botón y seleccione Expandir modelo **en** la lista desplegable Palabra clave.
10. Haga clic **+** en en Response (Respuesta) y arrastre **AstronautManager** desde **hierarchy (Jerarquía)** **al campo None (Object) (Ninguno [objeto]).**
11. Ahora, haga clic en **la lista desplegable Sin** función, seleccione **AstronautManager** y, a continuación, **ExpandaModelCommand**.
12. Haga clic en el botón del controlador de entrada **+** de voz y seleccione Restablecer **modelo** en la lista desplegable Palabra clave.
13. Haga clic **+** en en Response (Respuesta) y arrastre **AstronautManager** desde **hierarchy (Jerarquía)** **al campo None (Object) (Ninguno [objeto]).**
14. Ahora, haga clic en **la lista desplegable Sin** función, seleccione **AstronautManager** y, a continuación, **ResetModelCommand**.

![Configuración del controlador y el origen de entrada de voz para el capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilación e implementación

* ¡Pruébelo! Compile e implemente la aplicación en el HoloLens.
* Diga **Expandir modelo** para ver el modelo de astronauta expandido.
* Use **Navegación** para girar partes individuales del palo del astronauta.
* Diga **Move Astronaut (Mover astronauta)** y, a continuación, use **Manipulation** (Manipulación) para mover piezas individuales del palo del astronauta.
* Diga **Rotate Astronaut (Girar astronauta)** para girar las piezas de nuevo.
* Diga **Restablecer modelo** para devolver al astronauta a su forma original.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ya ha completado mr **input 211: gesture**.

* Sabe cómo detectar y responder a eventos de manipulación, navegación y seguimiento de manos.
* Comprende la diferencia entre los gestos de navegación y manipulación.
* Sabe cómo cambiar el cursor para proporcionar comentarios visuales sobre cuándo se detecta una mano, cuándo está a punto de perderse una mano y cuándo un objeto admite interacciones diferentes (navegación frente a manipulación).