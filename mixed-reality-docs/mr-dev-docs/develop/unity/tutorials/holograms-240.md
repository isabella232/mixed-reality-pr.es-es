---
title: 'Uso compartido de HoloLens de primera generación (240): varios dispositivos HoloLens'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información sobre el uso compartido de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, sharing, networking, academy, tutorial, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: 1714c9cf1b64953ff319eefb8633b1891568d5a50f2ed778e6e890d3149d3908
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208705"
---
# <a name="hololens-1st-gen-sharing-240-multiple-hololens-devices"></a>HoloLens (1.ª generación) Uso compartido 240: varios HoloLens móviles

>[!IMPORTANT]
>Los tutoriales Mixed Reality Academy se diseñaron con HoloLens (1.ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se_** actualizarán con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

Hologramas se les da presencia en nuestro mundo al permanecer en su lugar a medida que avanzamos en el espacio. HoloLens mantiene los hologramas en su [](../../../design/coordinate-systems.md) lugar mediante el uso de varios sistemas de coordenadas para realizar un seguimiento de la ubicación y orientación de los objetos. Cuando compartimos estos sistemas de coordenadas entre dispositivos, podemos crear una experiencia compartida que nos permita participar en un mundo holográfico compartido.

En este tutorial, veremos lo siguiente:

* Configurar una red para una experiencia compartida.
* Comparta hologramas entre HoloLens dispositivos.
* Descubra otras personas en nuestro mundo holográfico compartido.
* Cree una experiencia interactiva compartida en la que pueda dirigirse a otros jugadores e iniciar proyectos en ellos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Uso compartido de la realidad mixta (240): Varios dispositivos HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las herramientas [correctas instaladas](../../../develop/install-the-tools.md) con acceso a Internet.
* Al menos dos dispositivos HoloLens [configurados para el desarrollo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si todavía necesita compatibilidad con Unity 5.6, use [esta versión.](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)
  * Si todavía necesita compatibilidad con Unity 5.5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Si todavía necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Des archive los archivos en el escritorio u otra ubicación fácil de acceder. Mantenga el nombre de la carpeta **como SharedHolograms**.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

En este capítulo, configuraremos nuestro primer proyecto de Unity y veremos paso a paso el proceso de compilación e implementación.

### <a name="objectives"></a>Objetivos

* Configure Unity para desarrollar aplicaciones holográficas.
* Vea el holograma.

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **Open** (Abrir).
* Escriba location como la **carpeta SharedHolograms** que anteriormente no ha jerarquíado.
* Seleccione **Project nombre y** haga clic en Seleccionar **carpeta.**
* En **jerarquía,** haga clic con el botón derecho en **la cámara** principal y seleccione **Eliminar.**
* En la **carpeta HoloToolkit-Sharing-240/Prefabs/Camera,** busque el prefab **Cámara** principal.
* Arrastre y coloque la **cámara principal** en la **jerarquía**.
* En la **jerarquía ,** haga clic en **Crear** y **crear vacío.**
* Haga clic con el botón derecho en **el nuevo GameObject** y seleccione **Cambiar nombre.**
* Cambie el nombre de GameObject a **HologramCollection.**
* Seleccione el **objeto HologramCollection** en **la jerarquía**.
* En **inspector,** establezca la **posición de transformación** en: **X: 0, Y: -0,25, Z: 2**.
* En la **Hologramas** en el **panel Project**, busque el recurso **de EnergyHub.**
* Arrastre y coloque el **objeto EnergyHub** desde el **panel Project** a **hierarchy** como elemento secundario **de HologramCollection.**
* Seleccione **Archivo > Guardar escena como...**
* Asigne a la escena **el nombre SharedHolograms y** haga clic en **Guardar.**
* Presione el **botón Reproducir** en Unity para obtener una vista previa de los hologramas.
* Presione **Reproducir** una segunda vez para detener el modo de vista previa.

**Exportar el proyecto de Unity a Visual Studio**

* En Unity, **seleccione File > Build Configuración**.
* Haga **clic en Agregar escenas abiertas** para agregar la escena.
* Seleccione **Universal Windows Platform en** la lista **Plataforma** y haga clic en **Cambiar plataforma.**
* Establezca **SDK** en **Universal 10.**
* Establezca **Dispositivo de destino** en **HoloLens** y Tipo de **compilación de UWP** en **D3D.**
* Compruebe **proyectos de C# de Unity.**
* Haga clic en **Generar**.
* En la ventana del Explorador de archivos que aparece, cree **una nueva carpeta** denominada "App".
* Haga clic en la **carpeta Aplicación.**
* Presione **Seleccionar carpeta.**
* Cuando unity haya terminado, aparecerá Explorador de archivos ventana.
* Abra la **carpeta** Aplicación.
* Abra **SharedHolograms.sln para** iniciar Visual Studio.
* Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **X86.**
* Haga clic en la flecha desplegable situada junto a Máquina local y seleccione **Dispositivo remoto.**
    * Establezca **la dirección** en el nombre o la dirección IP de la HoloLens. Si no conoce la dirección IP del dispositivo, busque en Configuración > Network & Internet > Advanced Options (Opciones avanzadas de **Configuración > Network & Internet >)** o pregunte Cortana **"Hey Cortana, What's my IP address?"** (¿Cuál es mi dirección IP?).
    * Deje el **modo de autenticación** establecido en **Universal.**
    * Haga clic en **Seleccionar**
* Haga **clic en Depurar > iniciar sin depurar o** presione Ctrl + **F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar [con Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
* Coloque el HoloLens y busque el holograma de EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2: Interacción

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

En este capítulo, interactuaremos con nuestros hologramas. En primer lugar, agregaremos un cursor para visualizar la [mirada](../../../design/gaze-and-commit.md). A continuación, agregaremos [Gestos](../../../design/gaze-and-commit.md#composite-gestures) y usaremos la mano para colocar los hologramas en el espacio.

### <a name="objectives"></a>Objetivos

* Use la entrada de mirada para controlar un cursor.
* Use la entrada de gestos para interactuar con hologramas.

### <a name="instructions"></a>Instrucciones

**Gaze**

* En el **panel Jerarquía,** seleccione el **objeto HologramCollection.**
* En el **panel Inspector, haga** clic en **el botón Agregar** componente.
* En el menú, escriba en el cuadro de búsqueda **Gaze Manager**. Seleccione el resultado de la búsqueda.
* En la **carpeta HoloToolkit-Sharing-240\Prefabs\Input,** busque el **recurso Cursor.**
* Arrastre y coloque el **recurso Cursor** en **la jerarquía**.

**Gesto**

* En el **panel Jerarquía,** seleccione el **objeto HologramCollection.**
* Haga **clic en Agregar componente** y escriba Administrador de **gestos** en el campo de búsqueda. Seleccione el resultado de la búsqueda.
* En el **panel Jerarquía ,** expanda **HologramCollection**.
* Seleccione el objeto **EnergyHub** secundario.
* En el **panel Inspector, haga** clic en **el botón Agregar** componente.
* En el menú, escriba en el cuadro de búsqueda **Ubicación del holograma.** Seleccione el resultado de la búsqueda.
* Guarde la escena seleccionando Archivo **> Guardar escena.**

**Implementación y disfrute**

* Compile e implemente en su HoloLens, con las instrucciones del capítulo anterior.
* Una vez que la aplicación se inicie en el HoloLens, mueva la cabeza y observe cómo EnergyHub sigue la mirada.
* Observe cómo aparece el cursor al mirar el holograma y cambia a una luz de punto cuando no se desplaza hacia un holograma.
* Realice una pulsación en el aire para colocar el holograma. En este momento, en nuestro proyecto, solo puede colocar el holograma una vez (volver a implementar para intentarlo de nuevo).

## <a name="chapter-3---shared-coordinates"></a>Capítulo 3: Coordenadas compartidas

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es divertido ver hologramas e interactuar con ellos, pero vamos a ir más allá. Configuraremos nuestra primera experiencia compartida: un holograma que todos los usuarios pueden ver juntos.

### <a name="objectives"></a>Objetivos

* Configurar una red para una experiencia compartida.
* Establezca un punto de referencia común.
* Compartir sistemas de coordenadas entre dispositivos.
* Todo el mundo ve el mismo holograma.

>[!NOTE]
>Las **funcionalidades InternetClientServer** y **PrivateNetworkClientServer** deben declararse para que una aplicación se conecte al servidor de uso compartido. Esto se hace por usted ya Hologramas 240, pero tenga esto en cuenta para sus propios proyectos.

>1. En el Editor de Unity, vaya a la configuración del reproductor; para ello, vaya a "Editar > Project Configuración > Player".
>2. Haga clic en la pestaña "Windows Store".
>3. En la sección "Funcionalidades de Configuración > publicación", compruebe la funcionalidad **InternetClientServer** y **la funcionalidad PrivateNetworkClientServer.**

### <a name="instructions"></a>Instrucciones

* En el **Project,** vaya a la **carpeta HoloToolkit-Sharing-240\Prefabs\Sharing.**
* Arrastre y coloque el prefab **Uso** compartido en el **panel Jerarquía**.

A continuación, es necesario iniciar el servicio de uso compartido. Solo **un equipo** de la experiencia compartida debe realizar este paso.

* En Unity, en el menú superior, seleccione el **menú HoloToolkit-Sharing-240**.
* Seleccione el **elemento Launch Sharing Service (Iniciar** servicio de uso compartido) en la lista desplegable.
* Active la **opción Red privada y** haga clic en Permitir **acceso** cuando aparezca el símbolo del sistema del firewall.
* Anote la dirección IPv4 que se muestra en la ventana de la consola del servicio de uso compartido. Se trata de la misma dirección IP que la máquina en la que se ejecuta el servicio.

Siga el resto de las instrucciones de **todos los equipos que** se unirán a la experiencia compartida.

* En **jerarquía,** seleccione el **objeto Compartir.**
* En el **inspector**, en el  componente **Fase** de uso compartido, cambie la dirección del servidor de "localhost" a la dirección IPv4 del equipo que ejecuta SharingService.exe.
* En **Jerarquía,** seleccione el **objeto HologramCollection.**
* En **inspector, haga** clic en **el botón Agregar** componente.
* En el cuadro de búsqueda, escriba **Import Export Anchor Manager**. Seleccione el resultado de la búsqueda.
* En el **panel Project vaya** a la carpeta **Scripts.**
* Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* De nuevo en Unity, seleccione **HologramCollection en** el **panel Jerarquía**.
* En el **panel Inspector, haga** clic en **el botón Agregar** componente.
* En el menú, escriba en el cuadro de búsqueda **App State Manager**. Seleccione el resultado de la búsqueda.

**Implementación y disfrute**

* Compile el proyecto para los dispositivos HoloLens dispositivos.
* Designe una HoloLens que se implementará en primer lugar. Tendrá que esperar a que el delimitador se cargue en el servicio antes de poder colocar EnergyHub (esto puede tardar entre 30 y 60 segundos). Hasta que se realiza la carga, se omitirán los gestos de pulsación.
* Una vez colocado EnergyHub, su ubicación se cargará en el servicio y, a continuación, podrá implementarla en todos los demás HoloLens dispositivos.
* Cuando un nuevo HoloLens se une por primera vez a la sesión, es posible que la ubicación de EnergyHub no sea correcta en ese dispositivo. Sin embargo, tan pronto como se hayan descargado las ubicaciones de Anclaje y EnergyHub desde el servicio, EnergyHub debe saltar a la nueva ubicación compartida. Si esto no sucede en unos 30-60 segundos, pase hasta donde estaba el HoloLens original al establecer el delimitador para recopilar más pistas de entorno. Si la ubicación sigue sin bloquearse, vuelva a implementar en el dispositivo.
* Cuando los dispositivos estén listos y ejecuten la aplicación, busque EnergyHub. ¿Pueden estar todos de acuerdo en la ubicación del holograma y en qué dirección se encuentra el texto?

## <a name="chapter-4---discovery"></a>Capítulo 4: Detección

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Ahora todos los usuarios pueden ver el mismo holograma. Ahora vamos a ver a todos los demás conectados a nuestro mundo holográfico compartido. En este capítulo, tomaremos la ubicación principal y la rotación de todos los demás HoloLens dispositivos en la misma sesión de uso compartido.

### <a name="objectives"></a>Objetivos

* Descórtese unos a otros en nuestra experiencia compartida.
* Elija y comparta un avatar del jugador.
* Adjunte el avatar del jugador junto a las cabezas de todos.

### <a name="instructions"></a>Instrucciones

* En el **panel Project,** vaya a la **Hologramas** carpeta.
* Arrastre y coloque **PlayerAvatarStore** en **hierarchy**.
* En el **panel Project vaya** a la carpeta **Scripts.**
* Haga doble clic en el script **AvatarSelector** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* En **Jerarquía,** seleccione el **objeto HologramCollection.**
* En **inspector, haga** clic **en Agregar componente.**
* En el cuadro de búsqueda, escriba **Administrador del reproductor local**. Seleccione el resultado de la búsqueda.
* En **Jerarquía,** seleccione el **objeto HologramCollection.**
* En **inspector, haga** clic **en Agregar componente.**
* En el cuadro de búsqueda, escriba **Remote Player Manager**. Seleccione el resultado de la búsqueda.
* Abra el script **HologramPlacement** en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Abra el script **AppStateManager** en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Implementación y disfrute**

* Compile e implemente el proyecto en sus HoloLens dispositivos.
* Cuando escuche un sonido de ping, busque el menú de selección de avatar y seleccione un avatar con el gesto de pulsar el aire.
* Si no observa ningún holograma, la luz de punto alrededor del cursor volverá a un color diferente cuando el HoloLens se comunique con el servicio: inicializando (púrpura oscuro), descargando el delimitador (verde), importando o exportando datos de ubicación (amarillo) y cargando el anclaje (azul). Si la luz de punto alrededor del cursor es el color predeterminado (púrpura claro), está listo para interactuar con otros jugadores de la sesión.
* Mire a otras personas conectadas a su espacio: habrá un robot holográfico que flotará sobre su cuello e imitará sus movimientos de cabeza.

## <a name="chapter-5---placement"></a>Capítulo 5: Selección de ubicación

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

En este capítulo, haremos que el anclaje se pueda colocar en superficies del mundo real. Usaremos coordenadas compartidas para colocar ese anclaje en el punto intermedio entre todos los usuarios conectados a la experiencia compartida.

### <a name="objectives"></a>Objetivos

* Coloque hologramas en la malla de asignación espacial en función de la posición de la cabeza de los jugadores.

### <a name="instructions"></a>Instrucciones

* En el **panel Project,** vaya a la **Hologramas** carpeta.
* Arrastre y coloque el objeto **prefab CustomSpatialMapping** en **hierarchy**.
* En el **panel Project vaya** a la carpeta **Scripts.**
* Haga doble clic en el script **AppStateManager** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* En el **panel Project vaya** a la carpeta **Scripts.**
* Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Implementación y disfrute**

* Compile e implemente el proyecto en sus HoloLens dispositivos.
* Cuando la aplicación esté lista, de pie en un círculo y observe cómo aparece EnergyHub en el centro de todos los usuarios.
* Pulse para colocar EnergyHub.
* Pruebe el comando de voz "Reset Target" (Restablecer destino) para seleccionar la copia de seguridad de EnergyHub y trabaje juntos como un grupo para mover el holograma a una nueva ubicación.

## <a name="chapter-6---real-world-physics"></a>Capítulo 6: Real-World física

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

En este capítulo se agregarán hologramas que se despegarán de las superficies del mundo real. Vea que el espacio se llena de proyectos iniciados por usted y sus amigos.

### <a name="objectives"></a>Objetivos

* Inicie los projectiles que se despegarán de las superficies del mundo real.
* Comparta los proyectos para que otros jugadores puedan verlos.

### <a name="instructions"></a>Instrucciones

* En **Jerarquía,** seleccione el **objeto HologramCollection.**
* En **inspector, haga** clic **en Agregar componente.**
* En el cuadro de búsqueda, escriba **Projectile Selector**. Seleccione el resultado de la búsqueda.

**Implementación y disfrute**

* Compile e implemente en sus HoloLens dispositivos.
* Cuando la aplicación se ejecute en todos los dispositivos, realice una pulsación en el aire para iniciar el proyecto en superficies reales.
* Vea lo que sucede cuando el proyecto se intercala con el avatar de otro jugador.

## <a name="chapter-7---grand-finale"></a>Capítulo 7: Gran final

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

En este capítulo, descubriremos un portal que solo se puede detectar con colaboración.

### <a name="objectives"></a>Objetivos

* Trabaje juntos para iniciar suficientes proyectos en el anclaje para descubrir un portal secreto.

### <a name="instructions"></a>Instrucciones

* En el **panel Project,** vaya a la **Hologramas** carpeta.
* Arrastre y coloque el **recurso Underworld** como **elemento secundario de HologramCollection.**
* Con **HologramCollection seleccionado,** haga clic en **el botón Agregar** componente del **inspector**.
* En el menú, escriba en el cuadro de búsqueda **DesenlazadorDestino.** Seleccione el resultado de la búsqueda.
* Con **HologramCollection** seleccionado, en **hierarchy (Jerarquía),** arrastre el **objeto EnergyHub** al campo Target **(Destino)** del **inspector**.
* Con **HologramCollection** seleccionado, desde **jerarquía,** arrastre el objeto **Underworld** al **campo Underworld** en **el inspector**.

**Implementación y disfrute**

* Compile e implemente en sus HoloLens dispositivos.
* Cuando se haya iniciado la aplicación, colabore conjuntamente para iniciar los proyectos en EnergyHub.
* Cuando aparezca el sub mundo, inicie los projectiles en los robots de sub mundo (alcanzará a un robot tres veces para disfrutar de algo más).