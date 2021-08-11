---
title: 'HoloLens de primera generación y Azure (302): Computer Vision'
description: Complete este curso para aprender a reconocer contenido visual dentro de una imagen proporcionada, mediante Azure Computer Vision en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, computer vision, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226042"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (1ª generación) y Azure 302: Computer Vision

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

En este curso, aprenderá a reconocer el contenido visual dentro de una imagen proporcionada, mediante las funcionalidades de Azure Computer Vision en una aplicación de realidad mixta.

Los resultados del reconocimiento se mostrarán como etiquetas descriptivas. Puede usar este servicio sin necesidad de entrenar un modelo de aprendizaje automático. Si la implementación requiere el entrenamiento de un modelo de aprendizaje automático, consulte [MR y Azure 302b](mr-azure-302b.md).

![resultado del laboratorio](images/AzureLabs-Lab2-000.png)

Microsoft Computer Vision es un conjunto de API diseñadas para proporcionar a los desarrolladores procesamiento y análisis de imágenes (con información de devolución), mediante algoritmos avanzados, todo ello desde la nube. Los desarrolladores cargan una dirección URL de imagen o imagen y los algoritmos de api de Microsoft Computer Vision analizan el contenido visual, en función de las entradas elegidas por el usuario, que luego pueden devolver información, incluida la identificación del tipo y la calidad de una imagen, detectar caras humanas (devolver sus coordenadas) y etiquetar o categorizar imágenes. Para obtener más información, visite la página [de api Computer Vision Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Una vez completado este curso, tendrá una aplicación de realidad mixta HoloLens, que podrá hacer lo siguiente:

1.  Con el gesto De pulsar, la cámara del HoloLens capturará una imagen.
2.  La imagen se enviará a Azure Computer Vision API Service. 
3.  Los objetos reconocidos se mostrarán en un grupo de interfaz de usuario simple situado en la escena de Unity.

En la aplicación, es el usuario el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con el proyecto de Unity. Es su trabajo usar los conocimientos que obtenga de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (302): Computer Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a Windows Mixed Reality cascos envolventes (VR). Dado que los cascos envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir cascos envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de la escritura (mayo de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo Instalación de las herramientas, aunque no se debe suponer que la información de este curso coincidirá perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR).
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [casco Windows Mixed Reality envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Una cámara conectada al equipo (para el desarrollo de cascos envolventes)
- Acceso a Internet para la instalación y recuperación Computer Vision API de Azure

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo [HoloLens instalación de](/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración.](/hololens/hololens-calibration#hololens-2)

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: Azure Portal

Para usar el *Computer Vision API* en Azure, deberá configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer lugar, inicie sesión en [Azure Portal.](https://portal.azure.com) 

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los proctores para configurar la nueva cuenta.

2.  Una vez que haya  iniciado sesión, haga clic en Nuevo en la esquina superior izquierda y busque Computer Vision *API* y haga clic en **Entrar.**

    ![Creación de un nuevo recurso en Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.
 
3.  La nueva página proporcionará una descripción del servicio *Computer Vision API.* En la parte inferior izquierda de esta página, seleccione el **botón** Crear para crear una asociación con este servicio.

    ![Acerca del servicio Computer Vision API](images/AzureLabs-Lab2-01.png)
 
4.  Una vez que haya hecho clic en **Crear:**

    1. Inserte el nombre **deseado para** esta instancia de servicio.
    2. Seleccione una opción en **Suscripción**.
    3. Seleccione el **plan de** tarifa adecuado para usted; si es la primera vez que crea un servicio de API de *Computer Vision,* debe estar disponible un nivel gratuito (denominado F0).
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    6. También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.
    7. Haga clic en Crear.

        ![Información de creación de servicios](images/AzureLabs-Lab2-02.png)

5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Consulte la nueva notificación para el nuevo servicio.](images/AzureLabs-Lab2-03.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Seleccione el botón Ir al recurso.](images/AzureLabs-Lab2-04.png)
 
8. Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio Computer Vision API. 

    ![Nueva imagen del servicio Computer Vision API](images/AzureLabs-Lab2-05.png)
 
9.  En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.
10. En  la página Inicio rápido, del servicio de API de *Computer Vision,* vaya al primer *paso,* Tomar las claves y haga clic en Claves **(también** puede hacerlo haciendo clic en el hipervínculo azul Claves, ubicado en el menú de navegación de servicios, que indica el icono de clave). Esto revelará las claves de *servicio*.
11. Tome una copia de una de las claves mostradas, ya que la necesitará más adelante en el proyecto. 

12. Vuelva a la *página Inicio rápido* y, desde allí, obtenga el punto de conexión. Tenga en cuenta que la de usted puede ser diferente, en función de su región (que, si es así, tendrá que realizar un cambio en el código más adelante). Tome una copia de este punto de conexión para usarla más adelante:

    ![El nuevo servicio Computer Vision API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > Puede comprobar cuáles son los distintos puntos de conexión [AQUÍ.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.** 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab2-06.png)

2.  Ahora deberá proporcionar un nombre de Project Unity. Inserte **MR_ComputerVision**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca Ubicación **en un** lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Proporcione detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar > preferencias y,** a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab2-08.png)

4.  A continuación, vaya a **File > Build Configuración y** seleccione Universal Windows Platform (Plataforma **Windows** universal) y haga clic en el botón **Switch Platform** (Cambiar plataforma) para aplicar la selección.

    ![Cree Configuración ventana y cambie la plataforma a UWP.](images/AzureLabs-Lab2-10.png)

5.  Mientras sigue en **el > compilación Configuración** y asegúrese de que:

    1. **El dispositivo de** destino se **establece en HoloLens**

        > Para los cascos envolventes, establezca **Dispositivo de destino** en Cualquier *dispositivo.*

    2. **Tipo de** compilación se establece en **D3D**
    3. **El SDK** se establece en **Instalado más reciente.**
    4. **Visual Studio versión está** establecida en **Instalado más reciente**
    5. **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**
    6. Guarde la escena y agrégréla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.
        
            ![Haga clic en el botón Agregar escenas abiertas.](images/AzureLabs-Lab2-11.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Creación de una nueva carpeta de scripts](images/AzureLabs-Lab2-12.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *Nombre* de archivo : texto, **escriba MR_ComputerVisionScene** y, a continuación, haga clic **en Guardar.**

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab2-13.png)

            > Tenga en cuenta que debe guardar las escenas de Unity en la carpeta *Activos,* ya que deben estar asociadas con el Project Unity. La creación de la carpeta scenes (y otras carpetas similares) es una forma típica de estructurar un proyecto de Unity.

    7. El resto de la configuración, en *Build Configuración*, se debe dejar como valor predeterminado por ahora.

6. En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![Abra la configuración del reproductor.](images/AzureLabs-Lab2-14.png)

7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1. **La versión del runtime de** scripting debe ser **estable** (equivalente a .NET 3.5).
        2. **El back-end de** scripting debe ser **.NET**
        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Actualice otras opciones.](images/AzureLabs-Lab2-15.png)
      
    2. En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        1. **InternetClient**
        2. **Cámara web**

            ![Actualización de la configuración de publicación.](images/AzureLabs-Lab2-16.png)

    3. Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración),** marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se ha agregado el **SDK** Windows Mixed Reality web.

        ![Actualice el archivo X R Configuración.](images/AzureLabs-Lab2-17.png)

8.  De nuevo *en Build Configuración* Unity C# Projects (Proyectos de C# de _Unity)_ ya no está en gris; Marque la casilla situada junto a esta. 
9.  Cierre la ventana Build Settings (Configuración de compilación).
10. Guarde la escena y Project (**FILE > SAVE SCENE /FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: Configuración de la cámara principal

> [!IMPORTANT]
> Si quiere omitir el componente *De* configuración de Unity de este curso y continuar directamente en el código, no dude en descargar [este archivo .unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)importarlo en el proyecto como un paquete personalizado y, [a](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continuar desde el capítulo [5.](#chapter-5--create-the-resultslabel-class)

1.  En el *Panel de jerarquía,* seleccione la **cámara principal**. 
2.  Una vez seleccionada, podrá ver todos los componentes de **la** cámara principal en el *panel inspector*.

    1. El **objeto Camera** debe denominarse Cámara **principal** (tenga en cuenta la ortografía).
    2. La etiqueta de **cámara** principal debe establecerse **en MainCamera** (tenga en cuenta la ortografía).
    3. Asegúrese de que **la posición de** transformación está establecida en **0, 0, 0**
    4. Establezca **Clear Flags (Borrar marcas)** **en Color sólido** (o no lo haga para los cascos envolventes).
    5. Establezca el **color de** fondo del componente de cámara en **Negro, Alfa 0 (código hexadecimal: #00000000)** (omitir esto para los cascos envolventes).

        ![Actualice los componentes de la cámara.](images/AzureLabs-Lab2-18.png)
 
3.  A continuación, tendrá que crear un objeto "Cursor" simple asociado a la cámara principal **,** que le ayudará a colocar la salida del análisis de imágenes cuando se ejecuta la aplicación. Este cursor determinará el punto central del foco de la cámara.

Para crear el cursor:

1.  En el *Panel de jerarquía*, haga clic con el botón derecho en la cámara **principal**. En **Objeto 3D**, haga clic en **Sphere**.

    ![Seleccione el objeto cursor.](images/AzureLabs-Lab2-19.png)
 
2.  Cambie el nombre **de sphere** a **Cursor** (haga doble clic en el objeto Cursor o presione el botón de teclado "F2" con el objeto seleccionado) y asegúrese de que se encuentra como elemento secundario de la **cámara principal**.

3.  En el *Panel de jerarquía*, haga clic a la izquierda en **cursor**. Con el cursor seleccionado, ajuste las siguientes variables en el *panel inspector*:

    1. Establezca la *posición de transformación* en **0, 0, 5**
    2. Establezca *La escala* en **0.02, 0.02, 0.02**

        ![Actualice la posición y la escala de transformación.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capítulo 4: Configuración del sistema de etiquetas

Una vez que haya capturado una imagen con la cámara HoloLens, esa imagen se enviará a la instancia de *Azure Computer Vision API* Service para su análisis. 

Los resultados de ese análisis serán una lista de objetos reconocidos denominados **Etiquetas**. 

Usará Etiquetas (como texto 3D en el espacio del mundo) para mostrar estas etiquetas en la ubicación en la que se tomó la foto.

En los pasos siguientes se muestra cómo configurar el **objeto Label.**

1.  Haga clic con el botón derecho en cualquier lugar del Panel de jerarquía (la ubicación no importa en este momento), en **Objeto 3D**, agregue un **texto 3D**. Así mismo, **den el nombre LabelText.**

    ![Cree un objeto Text 3D.](images/AzureLabs-Lab2-21.png)
 
2.  En el *Panel de jerarquía*, haga clic a la izquierda en **LabelText**. Con **labelText** seleccionado, ajuste las siguientes variables en el *panel inspector*:

    1. Establezca la **posición** en **0,0,0**
    2. Establezca la **escala** en **0,01, 0,01, 0,01**
    3. En el componente **Text Mesh**:
    4. Reemplace todo el texto de **Text** por "..."        
    5. Establecer el **delimitador en** **Centro central**
    6. Establecer la **alineación** en **Centro**
    7. Establecer el **tamaño de tabulación** en **4**
    8. Establezca el **tamaño de fuente** en **50**
    9. Establezca **color en** **#FFFFFFFF**

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  Arrastre **LabelText** desde el *Panel de jerarquía hasta* la carpeta Asset *,* en el panel *Project panel*. Esto hará que **LabelText** sea prefab, de modo que se pueda crear una instancia en el código.

    ![Cree un objeto prefab del objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  Debe eliminar **LabelText** del *Panel de* jerarquía para que no se muestre en la escena de apertura. Como ahora es un objeto prefab, al que llamará para instancias individuales desde la carpeta Assets, no es necesario mantenerlo dentro de la escena. 
5.  La estructura de objetos final del *Panel de* jerarquía debe ser similar a la que se muestra en la imagen siguiente:

    ![Estructura final del panel de jerarquía.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capítulo 5: Creación de la clase ResultsLabel

El primer script que debe crear es la *clase ResultsLabel,* que es responsable de lo siguiente: 

- Crear las etiquetas en el espacio del mundo adecuado, en relación con la posición de la cámara.
- Mostrar las etiquetas de Image Anaysis.

Para crear esta clase: 

1.  Haga clic con el botón derecho *en Project panel y,* a continuación, **> carpeta**. Asigne a la carpeta el nombre **Scripts**. 

    ![Cree la carpeta scripts.](images/AzureLabs-Lab2-24.png)

2.  Con la **carpeta Scripts,** haga doble clic en ella para abrirla. A continuación, en esa carpeta, haga clic con el botón derecho y seleccione **Crear >** script **de C#.** Asigne al script el nombre *ResultsLabel.* 

3.  Haga doble clic en el nuevo script *ResultsLabel* para abrirlo con **Visual Studio**.

4.  Dentro de la clase , inserte el código siguiente en la *clase ResultsLabel:*

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*
7.  De nuevo en el *Editor de Unity,* haga clic y arrastre la clase *ResultsLabel* desde la carpeta **Scripts** hasta el objeto **Cámara** principal en el Panel *de jerarquía*.
8.  Haga clic en **la cámara principal** y mire en el panel *inspector*.

Observará que, desde el script que acaba de arrastrar a la cámara, hay dos campos: **Cursor** y **Etiqueta prefab**.

9.  Arrastre el objeto llamado **Cursor** desde el *Panel de* jerarquía a la ranura denominada **Cursor**, como se muestra en la imagen siguiente.
10. Arrastre el objeto **denominado LabelText** desde la carpeta *Assets* del *panel Project a* la ranura denominada Label **Prefab**, como se muestra en la imagen siguiente. 

    ![Establezca los destinos de referencia en Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capítulo 6: Creación de la clase ImageCapture

La siguiente clase que va a crear es la *clase ImageCapture.* Esta clase es responsable de:

-   Capturar una imagen mediante la HoloLens cámara y almacenarla en la carpeta de la aplicación.
-   Captura de gestos de pulsar del usuario.

Para crear esta clase: 

1.  Vaya a la **carpeta Scripts** que creó anteriormente. 
2.  Haga clic con el botón derecho en la carpeta **Crear > script de C#.** Llame al script *ImageCapture.* 
3.  Haga doble clic en el nuevo script *ImageCapture* para abrirlo con **Visual Studio**.
4.  Agregue los siguientes espacios de nombres a la parte superior del archivo:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro *de la clase ImageCapture,* encima *del método Start():*

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
La **variable tapsCount** almacenará el número de gestos de pulsación capturados del usuario. Este número se usa en la nomenclatura de las imágenes capturadas.

6.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().* Se llamará a estos cuando se inicialice la clase:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente un controlador al que se llamará cuando se produzca un gesto de pulsar. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
El *método TapHandler()* incrementa el número de pulsaciones capturadas del usuario y usa la posición actual del cursor para determinar dónde colocar una nueva etiqueta.

A continuación, este método llama *al método ExecuteImageCaptureAndAnalysis()* para comenzar la funcionalidad principal de esta aplicación.

8.  Una vez capturada y almacenada una imagen, se llamará a los siguientes controladores. Si el proceso se realiza correctamente, el resultado se pasa a *VisionManager* (que aún no ha creado) para su análisis.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  A continuación, agregue el método que la aplicación usa para iniciar el proceso de captura de imágenes y almacenar la imagen.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> En este momento observará que aparece un error en el panel de consola *del editor de Unity.* Esto se debe a que el código hace referencia *a la clase VisionManager* que creará en el capítulo siguiente.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capítulo 7: Llamada a Azure y análisis de imágenes

El último script que debe crear es la *clase VisionManager.* 

Esta clase es responsable de:

-   Carga de la imagen más reciente capturada como una matriz de bytes.
-   Envío de la matriz de bytes a la *instancia de Azure Computer Vision API* Service para su análisis.
-   Recibir la respuesta como una cadena JSON.
-   Deserializar la respuesta y pasar las etiquetas resultantes a la *clase ResultsLabel.*
 
Para crear esta clase:

1.  Haga doble clic en **la carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic > script de **C#.** Asigne al script el nombre *VisionManager.* 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sean los mismos que los siguientes, en la parte superior de la *clase VisionManager:*

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  En la parte superior del *script,* dentro de la clase *VisionManager* (encima  del *método Start(),* ahora debe crear dos clases que representarán la respuesta JSON deserializado de Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Las *clases TagData* y *AnalysedObject* deben tener el atributo *[System.Serializable]* agregado antes de la declaración para poder deserializarse con las bibliotecas de Unity.

6.  En la clase VisionManager, debe agregar las siguientes variables:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Asegúrese de insertar la clave **de autenticación en** la variable **authorizationKey.** Habrá anotado la **clave de autenticación** al principio de este curso, [capítulo 1.](#chapter-1--the-azure-portal)

    > [!WARNING] 
    > La **variable visionAnalysisEndpoint** puede diferir de la especificada en este ejemplo. El **oeste de EE. UU.** hace referencia estrictamente a las instancias de servicio creadas para la región Oeste de EE. UU. Actualíctelo con la dirección [URL del punto de conexión;](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) Estos son algunos ejemplos del aspecto que podría tener:
    > - Oeste de Europa: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Sudeste Asiático: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Este de Australia: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  Ahora es necesario agregar código para El activo. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  A continuación, agregue la corrotina (con el método de secuencia estática debajo), que obtendrá los resultados del análisis de la imagen capturada por *la clase ImageCapture.* 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Asegúrese de guardar los cambios *en* Visual Studio antes de volver a *Unity.*
10. De nuevo en el Editor de Unity, haga clic y arrastre las clases *VisionManager* *e ImageCapture* desde la carpeta **Scripts** hasta el objeto **Cámara** principal del Panel *de jerarquía.* 

## <a name="chapter-8--before-building"></a>Capítulo 8: Antes de compilar

Para realizar una prueba exhaustiva de la aplicación, deberá realizar una instalación local en la HoloLens.
Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones mencionadas [en el capítulo 2](#chapter-2--set-up-the-unity-project) se establecen correctamente. 
-   Todos los scripts están asociados al **objeto Cámara** principal. 
-   Todos los campos del *panel inspector de la* cámara principal se asignan correctamente.
-   Asegúrese de insertar la clave **de autenticación en** la variable **authorizationKey.**
-   Asegúrese de que también ha comprobado el punto de conexión en el script *de VisionManager* y que se alinea con su *región* (este documento usa *west-us* de forma predeterminada).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capítulo 9: Compilación de la solución para UWP y instalación local de la aplicación
Ya se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a *Build Configuración* File >  -  **Build Configuración...**
2.  En la ventana *Compilar Configuración,* haga clic en **Compilar**.

    ![Creación de la aplicación desde Unity](images/AzureLabs-Lab2-26.png)

3.  Si aún no lo ha hecho, marque **Proyectos de C# de Unity.**
4.  Haga clic en **Generar**. Unity iniciará una *Explorador de archivos,* donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así mismo den el nombre *App*. Después, con la *carpeta Aplicación* seleccionada, presione **Seleccionar carpeta.** 
5.  Unity comenzará a compilar el proyecto en la *carpeta Aplicación.* 
6.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de *Explorador de archivos* en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-10--deploy-to-hololens"></a>Capítulo 10: Implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para Implementación remota) y para asegurarse de que el HoloLens está en **modo de desarrollador**. Para ello:

    1. Al mismo tiempo que HoloLens, abra **el Configuración**.
    2. Vaya a **Network & Internet > Wi-Fi > Advanced Options**
    3. Anote **la dirección IPv4.**
    4. A continuación, vuelva **a Configuración** y, a continuación, a Update & Security > For Developers (Actualizar > seguridad **para desarrolladores).** 
    5. Establezca Modo de desarrollador en.

2.  Vaya a la nueva compilación de Unity (la *carpeta Aplicación)* y abra el archivo de solución *con Visual Studio*.
3.  En Configuración de la solución, **seleccione Depurar**.
4.  En la Plataforma de soluciones, **seleccione x86**, **Equipo remoto.** 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Vaya al menú **Compilar y haga** clic en Implementar **solución** para realizar la instalación local de la aplicación en el HoloLens.
6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el HoloLens, listo para iniciarse.

> [!NOTE]
> Para implementar en casco  envolvente, establezca plataforma de  solución en *Máquina local* y establezca la configuración en *Depurar*, con *x86* como **plataforma**. A continuación, implemente en la máquina local, mediante **el menú Compilar** y seleccione Implementar *solución.* 

## <a name="your-finished-computer-vision-api-application"></a>La aplicación de API Computer Vision finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de Azure Computer Vision para reconocer objetos del mundo real y mostrar la confianza de lo que se ha visto.

![resultado del laboratorio](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Del mismo modo que ha usado el  parámetro *Tags* (como se muestra en el punto de conexión usado dentro de *VisionManager),* extienda la aplicación para detectar otra información. vea qué otros parámetros tiene acceso a [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).

### <a name="exercise-2"></a>Ejercicio 2

Muestre los datos de Azure devueltos, de una manera más conversacional y legible, quizás ocultando los números. Como si un bot pudiera estar hablando con el usuario.