---
title: 'Aspectos básicos de HoloLens de primera generación (101): proyecto completo con dispositivo'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los conceptos básicos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, academy, tutorial, HoloLens, Mixed Reality Academy, unity, casco de realidad mixta, cascos de realidad mixta de Windows, cascos de realidad virtual, Windows 10
ms.openlocfilehash: 63219edebeb63dbf4589e8162f8dc1bab83275c38f29b106db9bae234cdabde0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200965"
---
# <a name="hololens-1st-gen-basics-101-complete-project-with-device"></a>HoloLens (1.ª generación) Basics 101: Complete project with device (Conceptos básicos 101: Completar el proyecto con el dispositivo)

<br>

>[!IMPORTANT]
>Los tutoriales Mixed Reality Academy se diseñaron con HoloLens (1.ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se_** actualizarán con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Este tutorial le guía por un proyecto completo, integrado en Unity, que muestra las características principales de Windows Mixed Reality en HoloLens como la [mirada,](../../../design/gaze-and-commit.md)los [gestos,](../../../design/gaze-and-commit.md#composite-gestures) [la](../../../design/voice-input.md)entrada de [voz,](../../../design/spatial-sound.md) el sonido espacial y la asignación [espacial.](../../../design/spatial-mapping.md)

El tutorial tarda aproximadamente una hora en completarse.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Aspectos básicos de realidad mixta (101): Proyecto completo con dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../install-the-tools.md)
* Un HoloLens configurado [para el desarrollo.](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si todavía necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Si todavía necesita compatibilidad con Unity 5.5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Si todavía necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Des archive los archivos en el escritorio u otra ubicación fácil de acceder. Mantenga el nombre de la carpeta **como Origami.**

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1: mundo "Holo"

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

En este capítulo, configuraremos nuestro primer proyecto de Unity y veremos paso a paso el proceso de compilación e implementación.

### <a name="objectives"></a>Objetivos

* Configure Unity para el desarrollo holográfico.
* Crear un holograma.
* Vea un holograma que ha realizado.

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **Open** (Abrir).
* Escriba location como la **carpeta Origami** que des archivó anteriormente.
* Seleccione **Origami y haga** clic en Seleccionar **carpeta.**
* Puesto que **el proyecto de Origami** no contiene una escena, guarde la escena predeterminada vacía en un nuevo archivo mediante: **Guardar** escena de  /  **archivo como**.
* Asigne a la nueva escena el **nombre Origami y** presione **el botón** Guardar.

#### <a name="setup-the-main-virtual-camera"></a>Configuración de la cámara virtual principal

* En **Hierarchy Panel** (Panel de jerarquía), seleccione **Main Camera** (Cámara principal).
* En **inspector,** establezca su posición de transformación **en 0,0,0.**
* Busque la **propiedad Borrar marcas** y cambie la lista desplegable de **Skybox** a **Color sólido.**
* Haga clic en el campo **Background** (Fondo) para abrir un selector de colores.
* Establezca **R, G, B, and A** (R, G, B y A) en **0**.

#### <a name="setup-the-scene"></a>Configuración de la escena

* En el **Panel de jerarquía**, haga clic en **Crear** y **crear vacío.**
* Haga clic con el botón derecho en **el nuevo GameObject** y seleccione Cambiar nombre. Cambie el nombre de GameObject a **OrigamiCollection.**
* En la **carpeta Hologramas** del panel de Project (expanda Activos y seleccione Hologramas o haga doble clic en la carpeta Hologramas en el panel de Project):
  * Arrastre **Stage** a hierarchy para que sea un elemento secundario de **OrigamiCollection.**
  * Arrastre **Sphere1** a hierarchy para que sea un elemento secundario **de OrigamiCollection.**
  * Arrastre **Sphere2** a hierarchy para que sea un elemento secundario **de OrigamiCollection.**
* Haga clic con el botón derecho **en el objeto Directional Light** en el Panel **de** jerarquía y seleccione **Eliminar.**
* Desde la **Hologramas,** arrastre **Lights** a la raíz del **Panel de jerarquía.**
* En la **jerarquía**, seleccione **OrigamiCollection**.
* En **inspector**, establezca la posición de transformación **en 0, -0,5, 2,0**.
* Presione el **botón Reproducir** en Unity para obtener una vista previa de los hologramas.
* Debería ver los objetos Origami en la ventana de vista previa.
* Presione **Reproducir** una segunda vez para detener el modo de vista previa.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar el proyecto de Unity a Visual Studio

* En Unity, **seleccione File > Build Configuración**.
* Seleccione **Universal Windows Platform en** la lista **Plataforma** y haga clic en **Cambiar plataforma.**
* Establezca **SDK** en **Universal 10** y **Tipo de compilación** en **D3D.**
* Compruebe **proyectos de C# de Unity.**
* Haga **clic en Agregar escenas abiertas** para agregar la escena.
* Haga clic en **Generar**.
* En la ventana del Explorador de archivos que aparece, cree **una nueva carpeta** denominada "App".
* Haga clic en la **carpeta De la aplicación.**
* Presione **Seleccionar carpeta.**
* Cuando unity haya terminado, aparecerá Explorador de archivos ventana.
* Abra la **carpeta** Aplicación.
* Abra (doble clic) **Origami.sln**.
* Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **X86.**
* Haga clic en la flecha situada junto al botón Dispositivo y seleccione **Equipo remoto** para implementar a través de Wi-Fi.
  * Establezca **la dirección** en el nombre o la dirección IP de la HoloLens. Si no conoce la dirección IP del dispositivo, busque en Configuración > Network & Internet > Advanced Options (Opciones avanzadas de **Configuración > Network & Internet >)** o pregunte Cortana **"Hey Cortana, What's my IP address?"** (¿Cuál es mi dirección IP?).
  * Si el HoloLens está conectado a través de USB, puede seleccionar Dispositivo **para** implementar a través de USB.
  * Deje el **modo de autenticación** establecido en **Universal.**
  * Haga clic en **Seleccionar**

* Haga **clic en Depurar > iniciar sin depurar o** presione Ctrl + **F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar [con Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).

* El proyecto Origami ahora se compilará, se implementará en el HoloLens y, a continuación, se ejecutará.
* Coloque el HoloLens y mire a su alrededor para ver los nuevos hologramas.

## <a name="chapter-2---gaze"></a>Capítulo 2: Mirada

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

En este capítulo, vamos a presentar la primera de las tres formas de interactuar con los hologramas: [mirar](../../../design/gaze-and-commit.md).

### <a name="objectives"></a>Objetivos

* Visualice la mirada con un cursor bloqueado por el mundo.

### <a name="instructions"></a>Instrucciones

* Vuelva al proyecto de Unity y cierre la ventana build Configuración (Compilar) si sigue abierta.
* Seleccione la **carpeta Hologramas** en el **Project panel**.
* Arrastre el **objeto Cursor** al **panel Jerarquía** en el nivel raíz.
* Haga doble clic en el **objeto Cursor** para echar un vistazo más de cerca.
* Haga clic con el botón derecho en **la carpeta Scripts** en Project panel.
* Haga clic **en el** submenú Crear.
* Seleccione **Script de C#.**
* Asigne al script **el nombre WorldCursor.** Nota: El nombre distingue mayúsculas de minúsculas. No es necesario agregar la extensión .cs.
* Seleccione el **objeto Cursor** en el **panel Jerarquía**.
* Arrastre y coloque el script **WorldCursor** en el **panel Inspector**.
* Haga doble clic en el script **WorldCursor** para abrirlo en Visual Studio.
* Copie y pegue este código en **WorldCursor.cs** y **Guardar todo.**

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Recompile la aplicación **desde File > Build Configuración**.
* Vuelva a la Visual Studio solución usada anteriormente para implementar en el HoloLens.
* Seleccione "Volver a cargar todo" cuando se le solicite.
* Haga **clic en Depurar -> Iniciar sin depurar** o presione Ctrl + **F5**.
* Ahora, mire alrededor de la escena y observe cómo interactúa el cursor con la forma de los objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3: Gestos

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

En este capítulo, agregaremos compatibilidad con [gestos](../../../design/gaze-and-commit.md#composite-gestures). Cuando el usuario selecciona una esfera de papel, haremos que la esfera se desafíe al activar la gravedad mediante el motor físico de Unity.

### <a name="objectives"></a>Objetivos

* Controle los hologramas con el gesto Seleccionar.

### <a name="instructions"></a>Instrucciones

Para empezar, crearemos un script y, a continuación, detectaremos el gesto Seleccionar.

* En la **carpeta Scripts,** cree un script denominado **GazeGestureManager**.
* Arrastre el script **GazeGestureManager** al **objeto OrigamiCollection** en la jerarquía.
* Abra el script **GazeGestureManager** en Visual Studio y agregue el código siguiente:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Cree otro script en la carpeta Scripts, esta vez denominado **SphereCommands**.
* Expanda el **objeto OrigamiCollection** en la vista Jerarquía.
* Arrastre el script **SphereCommands** al objeto **Sphere1** en el panel Jerarquía.
* Arrastre el script **SphereCommands** al objeto **Sphere2** en el panel Jerarquía.
* Abra el script en Visual Studio para editarlo y reemplace el código predeterminado por el siguiente:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exporte, compile e implemente la aplicación en su HoloLens.
* Mire una de las esferas.
* Realice el gesto de selección y observe cómo la esfera se coloca en la superficie siguiente.

## <a name="chapter-4---voice"></a>Capítulo 4: Voz

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

En este capítulo, agregaremos compatibilidad con dos comandos de [voz:](../../../design/voice-input.md)"Restablecer mundo" para devolver las esferas descartadas a su ubicación original y "Drop sphere" para hacer que la esfera se coloque.

### <a name="objectives"></a>Objetivos

* Agregue comandos de voz que siempre escuchan en segundo plano.
* Cree un holograma que reaccione a un comando de voz.

### <a name="instructions"></a>Instrucciones

* En la **carpeta Scripts,** cree un script denominado **SpeechManager.**
* Arrastre el script **speechManager** al **objeto OrigamiCollection** en la jerarquía.
* Abra el script **speechManager** en Visual Studio.
* Copie y pegue este código en **SpeechManager.cs** y **Guardar todo:**

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Abra el script **SphereCommands** en Visual Studio.
* Actualice el script para que lea de la siguiente manera:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exporte, compile e implemente la aplicación en su HoloLens.
* Mire una de las esferas y diga **"Drop Sphere".**
* Diga **"Restablecer mundo"** para que vuelvan a sus posiciones iniciales.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5: Sonido espacial

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

En este capítulo, agregaremos música a la aplicación y, a continuación, desencadenaremos efectos de sonido en determinadas acciones. Usaremos el sonido [espacial para](../../../design/spatial-sound.md) proporcionar a los sonidos una ubicación específica en el espacio 3D.

### <a name="objectives"></a>Objetivos

* Escuche hologramas en su mundo.

### <a name="instructions"></a>Instrucciones

* En Unity, seleccione en el menú superior **Editar > Project Configuración > audio**
* En el panel inspector del lado derecho, busque la configuración del complemento **Spatializer** y seleccione **MS HRTF Spatializer**.
* En la **Hologramas** del panel Project, arrastre el objeto Desaceptar al objeto **OrigamiCollection** en el Panel de jerarquía. 
* Seleccione **OrigamiCollection y** busque el **componente Audio Source (Origen de** audio) en el panel Inspector. Cambie estas propiedades:
  * Compruebe la **propiedad Spatialize.**
  * Compruebe play **on awake**.
  * Cambie **Spatial Blend** a **3D** arrastrando el control deslizante hasta la derecha. El valor debe cambiar de 0 a 1 al mover el control deslizante.
  * Compruebe la **propiedad Loop.**
  * Expanda **3D Sound Configuración** y escriba **0.1** en **Doppler Level (Nivel de Doppler).**
  * Establezca **Lanzamiento de volumen en** Lanzamiento **logarítmico.**
  * Establezca **Distancia máxima** en **20.**
* En la **carpeta Scripts,** cree un script denominado **SphereSounds.**
* Arrastre y coloque **Sphere Sounds** en los **objetos Sphere1** y **Sphere2** de la jerarquía.
* Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **Guarde todo.**

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Guarde el script y vuelva a Unity.
* Exporte, compile e implemente la aplicación en su HoloLens.
* Acercarse y avanzar desde la fase y girar de lado a lado para escuchar los sonidos cambiar.

## <a name="chapter-6---spatial-mapping"></a>Capítulo 6: Asignación espacial

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Ahora vamos a usar la [asignación espacial para](../../../design/spatial-mapping.md) colocar el tablero de juego en un objeto real en el mundo real.

### <a name="objectives"></a>Objetivos

* Lleve su mundo real al mundo virtual.
* Coloque los hologramas donde más le importan.

### <a name="instructions"></a>Instrucciones

* En Unity, haga clic en **la carpeta Hologramas** en el Project panel.
* Arrastre el **recurso Asignación** espacial a la raíz de **la jerarquía**.
* Haga clic en **el objeto Asignación** espacial en la jerarquía.
* En el **panel Inspector**, cambie las propiedades siguientes:
  * Active la **casilla Dibujar mallas visuales.**
  * Busque **Draw Material (Dibujar material)** y haga clic en el círculo de la derecha. Escriba "**wireframe**" en el campo de búsqueda de la parte superior. Haga clic en el resultado y cierre la ventana. Al hacerlo, el valor de Draw Material debe establecerse en Wireframe.
* Exporte, compile e implemente la aplicación en su HoloLens.
* Cuando se ejecuta la aplicación, una malla de wireframe se superponerá al mundo real.
* Observe cómo una esfera gradual se despedará del escenario y se pondrá en el suelo.

Ahora le mostraremos cómo mover OrigamiCollection a una nueva ubicación:

* En la **carpeta Scripts,** cree un script denominado **TapToPlaceParent.**
* En **jerarquía,** expanda **OrigamiCollection** y seleccione el **objeto Stage.**
* Arrastre el script **TapToPlaceParent** al objeto Stage.
* Abra el script **TapToPlaceParent** Visual Studio y actualícuelo para que sea el siguiente:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exporte, compile e implemente la aplicación.
* Ahora debería poder colocar el juego en una ubicación específica si lo mira, usa el gesto Seleccionar y, a continuación, se mueve a una nueva ubicación y vuelve a usar el gesto Seleccionar.

## <a name="chapter-7---holographic-fun"></a>Capítulo 7: Juego holográfico

### <a name="objectives"></a>Objetivos

* Mostrar la entrada a un infraworld holográfico.

### <a name="instructions"></a>Instrucciones

Ahora le mostraremos cómo descubrir el infraworld holográfico:

* Desde la **Hologramas** en el panel de Project:
  * Arrastre **Underworld** a hierarchy para que sea un elemento secundario de **OrigamiCollection.**
* En la **carpeta Scripts,** cree un script denominado **HitTarget.**
* En la **jerarquía**, expanda **OrigamiCollection**.
* Expanda el **objeto Stage** y seleccione el objeto **Target (ventilador** azul).
* Arrastre el script **HitTarget** al **objeto Target.**
* Abra el script **HitTarget** en Visual Studio y actualíctelo para que sea el siguiente:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* En Unity, seleccione el **objeto Destino.**
* Ahora hay dos propiedades públicas visibles en el componente **Destino de** acceso y deben hacer referencia a objetos de nuestra escena:
  * Arrastre **Underworld** desde el panel **Hierarchy (Jerarquía)** a la **propiedad Underworld (Subworld)** del **componente Hit Target (Destino de** acceso).
  * Arrastre **Stage** desde el panel **Hierarchy (Jerarquía)** hasta la **propiedad Object to Hide (Objeto para ocultar)** del componente **Hit Target (Destino de** acceso).
* Exporte, compile e implemente la aplicación.
* Coloque la colección Origami en el suelo y, a continuación, use el gesto Seleccionar para colocar una esfera.
* Cuando la esfera alcanza el destino (ventilador azul), se producirá una explosión. La colección se ocultará y aparecerá un hueco en el subworld.

## <a name="the-end"></a>Fin

Y ese es el final de este tutorial.

Ha aprendido:

* Cómo crear una aplicación holográfica en Unity.
* Cómo usar la mirada, el gesto, la voz, el sonido y la asignación espacial.
* Cómo compilar e implementar una aplicación mediante Visual Studio.

Ya está listo para empezar a crear su propia experiencia holográfica.

## <a name="see-also"></a>Consulte también

* [MR Basics 101E: proyecto completo con emulador](holograms-101e.md)
* [Gaze](../../../design/gaze-and-commit.md)
* [Mirada-cabeza y confirmación](../../../design/gaze-and-commit.md)
* [Entrada de voz](../../../design/voice-input.md)
* [Sonido espacial](../../../design/spatial-sound.md)
* [Asignación espacial](../../../design/spatial-mapping.md)