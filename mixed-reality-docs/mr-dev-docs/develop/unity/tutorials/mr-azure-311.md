---
title: 'HoloLens de primera generación y Azure (311): Microsoft Graph'
description: Complete este curso para aprender a aprovechar Microsoft Graph y conectarse a los datos que impulsan la productividad, dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, microsoft graph, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 16fb7853d202c39399b48595a17e7e9b2edf224f18d5e315c5ddcf4a0054d8f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215422"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a>HoloLens de primera generación y Azure (311): Microsoft Graph

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

En este curso, aprenderá a usar *Microsoft Graph* para iniciar sesión en su cuenta Microsoft mediante la autenticación segura dentro de una aplicación de realidad mixta. A continuación, recuperará y mostrará las reuniones programadas en la interfaz de aplicación.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* es un conjunto de API diseñadas para permitir el acceso a muchos de los servicios de Microsoft. Microsoft describe microsoft Graph como una matriz de recursos conectados por relaciones, lo que significa que permite que una aplicación acceda a todo tipo de datos de usuario conectados. Para obtener más información, visite la [página de Graph Microsoft](https://developer.microsoft.com/graph).

El desarrollo incluirá la creación de una aplicación en la que se le indicará al usuario que mire y, a continuación, pulse una esfera, lo que pedirá al usuario que inicie sesión de forma segura en una cuenta Microsoft. Una vez que haya iniciado sesión en su cuenta, el usuario podrá ver una lista de reuniones programadas para el día.

Una vez completado este curso, tendrá una aplicación de realidad HoloLens mixta, que podrá hacer lo siguiente:

1.  Con el gesto Pulsar, pulse en un objeto , lo que le pedirá al usuario que inicie sesión en una cuenta Microsoft (salga de la aplicación para iniciar sesión y, a continuación, vuelva a la aplicación).
2.  Vea una lista de las reuniones programadas para el día. 

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con el proyecto de Unity. Es su trabajo usar los conocimientos que obtenga de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (311): Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de la escritura (julio de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) tal como se muestra en el artículo Instalación de las herramientas, aunque no se debe suponer que la información de este curso coincidirá perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Microsoft HoloLens](/hololens/hololens1-hardware) con el modo de desarrollador habilitado
- Acceso a Internet para la instalación de Azure y la recuperación de datos Graph Microsoft
- Una cuenta **Microsoft válida** (personal o laboral o educativa)
- Algunas reuniones programadas para el día actual, con la misma cuenta Microsoft

### <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo [HoloLens instalación de](/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre calibración, siga este vínculo al artículo HoloLens [Calibración.](/hololens/hololens-calibration#hololens-2)

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capítulo 1: Creación de la aplicación en el Portal de registro de aplicaciones

Para empezar, deberá crear y registrar la aplicación en el Portal **de registro de aplicaciones**.

En este capítulo también encontrará la clave de servicio que le permitirá realizar llamadas a *Microsoft Graph* acceder al contenido de la cuenta.

1.  Vaya al Portal [de registro de aplicaciones de Microsoft](https://apps.dev.microsoft.com) e inicie sesión con su cuenta Microsoft. Una vez que haya iniciado sesión, se le redirigirá al Portal **de registro de aplicaciones**.

2.  En la **sección Mis aplicaciones,** haga clic en el botón **Agregar una aplicación**.

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > El **Portal de registro de** aplicaciones puede tener un aspecto diferente, en función de si ha trabajado previamente con Microsoft *Graph*. En las capturas de pantalla siguientes se muestran estas distintas versiones.

3.  Agregue un nombre para la aplicación y haga clic **en Crear.**

    ![](images/AzureLabs-Lab311-03.png)

4.  Una vez creada la aplicación, se le redirigirá a la página principal de la aplicación. Copie el **identificador de** aplicación y asegúrese de tener en cuenta este valor en algún lugar seguro; lo usará pronto en el código.

    ![](images/AzureLabs-Lab311-04.png)

5.  En la **sección Plataformas,** asegúrese de **que se muestra** Aplicación nativa. Si *no,* haga clic **en Agregar plataforma** y seleccione Aplicación **nativa.**

    ![](images/AzureLabs-Lab311-05.png)

6.  Desplácese hacia abajo en la misma página y, en la sección denominada **Microsoft Graph Permissions,** deberá agregar permisos adicionales para la aplicación. Haga clic **en Agregar** junto a **Permisos delegados**.

    ![](images/AzureLabs-Lab311-06.png)

7.  Puesto que quiere que la aplicación acceda al calendario del usuario, active la casilla **denominada Calendars.Read** y haga clic en **Aceptar.**

    ![](images/AzureLabs-Lab311-07.png)

8.  Desplácese hasta la parte inferior y haga clic **en el botón** Guardar.

    ![](images/AzureLabs-Lab311-08.png)

9.  Se confirmará el guardado y podrá cerrar sesión en el **Portal de registro de aplicaciones.**

## <a name="chapter-2---set-up-the-unity-project"></a>Capítulo 2: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.**

    ![](images/AzureLabs-Lab311-09.png)

2.  Debe proporcionar un nombre de proyecto de Unity. Inserte **MSGraphMR**. Asegúrese de que la plantilla de proyecto está establecida en **3D.** Establezca la **ubicación en** un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![](images/AzureLabs-Lab311-10.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar**  >  **preferencias** y, a continuación, en la nueva ventana, vaya **a Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![](images/AzureLabs-Lab311-11.png)

4.  Vaya a **File** Build Configuración (Compilación de archivos) y seleccione Universal Windows Platform (Plataforma universal) y haga clic en el botón Switch Platform (Cambiar plataforma)  >   para aplicar la selección.  

    ![](images/AzureLabs-Lab311-12.png)

5.  Mientras sigue en **la**  >  **compilación de Configuración**, asegúrese de que:

    1. **El dispositivo de** destino se **establece en HoloLens**
    2. **Tipo de** compilación se establece en **D3D**
    3. **El SDK** se establece en **Instalado más reciente**
    4. **Visual Studio versión está** establecida en **La versión más reciente instalada**
    5. **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**
    6. Guarde la escena y agrégréla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![](images/AzureLabs-Lab311-13.png)

        2. Cree una nueva carpeta para esta escena y para cualquier escenario futuro. Seleccione el **botón Nueva** carpeta para crear una nueva carpeta, así como el nombre **Scenes**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *Nombre* de archivo: texto, **escriba MR_ComputerVisionScene** y, a continuación, haga clic **en Guardar.**

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Tenga en cuenta que debe guardar las escenas de Unity en la *carpeta Recursos,* ya que deben estar asociadas con el proyecto de Unity. La creación de la carpeta scenes (y otras carpetas similares) es una forma típica de estructurar un proyecto de Unity.

    7.  El resto de la configuración, *en Build Configuración*, se debe dejar como valor predeterminado por ahora.

6.  En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![](images/AzureLabs-Lab311-16.png)

7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1.  **La** **versión del entorno de** ejecución de scripting debe ser **Experimental** (equivalente de .NET 4.6), lo que desencadenará la necesidad de reiniciar el editor.

        2. **El back-end de scripting** debe ser **.NET**

        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración),** compruebe Virtual Reality Supported (Virtual **Reality compatible)** y asegúrese de que se ha agregado Windows Mixed Reality **SDK.**

        ![](images/AzureLabs-Lab311-19.png)

8.  De nuevo *en build Configuración*, los proyectos de *C#* de Unity ya no están en gris; Active la casilla situada junto a esta.

9.  Cierre la ventana *Build Settings* (Configuración de compilación).

10.  Guarde la escena y el proyecto **(ARCHIVO**  >  **GUARDAR ESCENAS / ARCHIVO** GUARDAR  >  **PROYECTO**).

## <a name="chapter-3---import-libraries-in-unity"></a>Capítulo 3: Importación de bibliotecas en Unity

> [!IMPORTANT]
> Si quiere omitir el componente Configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar este paquete [Azure-MR-311.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)importarlo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continuar desde el [capítulo 5.](#chapter-5---create-meetingsui-class)

Para usar *Microsoft Graph* en Unity, debe usar el archivo DLL **Microsoft.Identity.Client.** Sin embargo, es posible usar el SDK de Microsoft Graph; sin embargo, requerirá la adición de un paquete de NuGet después de compilar el proyecto de Unity (lo que significa editar el proyecto después de la compilación). Se considera más sencillo importar los archivos DLL necesarios directamente en Unity.

> [!NOTE]
> Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (del 4 al 7 de esta sección) ya no serán necesarios una vez resuelto el error.

Para importar *Microsoft Graph* en su propio proyecto, descargue el [MSGraph_LabPlugins.zip archivo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage). Este paquete se ha creado con versiones de las bibliotecas que se han probado.

Si desea obtener más información sobre cómo agregar archivos DLL personalizados al proyecto de Unity, [siga este vínculo.](https://docs.unity3d.com/Manual/UsingDLL.html)

Para importar el paquete:

1.  Agregue el paquete de Unity a Unity mediante la opción de  >  **menú Importar paquete** personalizado  >  **de** recursos. Seleccione el paquete que acaba de descargar.

2.  En el **cuadro Importar paquete de Unity** que aparece, asegúrese de que todo lo que hay en (e incluido) **Complementos** está seleccionado.

    ![](images/AzureLabs-Lab311-20.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta MSGraph** en **Complementos** en el panel de Project *y* seleccione el complemento **denominado Microsoft.Identity.Client.**

    ![](images/AzureLabs-Lab311-21.png)

5.  Con el *complemento* seleccionado, asegúrese de que **cualquier** plataforma esté desactivada, asegúrese de que **WSAPlayer** también esté desactivado y, a continuación, haga clic **en Aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Marcar estos complementos los configura para que solo se utilicen en el editor de Unity. Hay un conjunto diferente de archivos DLL en la carpeta WSA que se usará después de que el proyecto se exporte desde Unity como una aplicación de Windows universal.

6.  A continuación, debe abrir la **carpeta WSA,** dentro de la **carpeta MSGraph.** Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector:

    -   asegúrese de **que cualquier plataforma** está **desactivada** y de **que solo** **WSAPlayer** está **activado.**

    -   Asegúrese **de que el SDK** está establecido en **UWP** y el **back-end de scripting** está establecido en Dot **Net.**

    -   Asegúrese de **que La opción No procesar** está **activada.**

        ![](images/AzureLabs-Lab311-23.png)

7.  Haga clic en **Aplicar**.

## <a name="chapter-4---camera-setup"></a>Capítulo 4: Configuración de la cámara

Durante este capítulo, configurará la cámara principal de la escena:

1.  En el *Panel de jerarquía,* seleccione la **cámara principal**.

2.  Una vez seleccionada, podrá ver todos los componentes de **la** cámara principal en el *panel* Inspector.

    1.  El **objeto Camera** debe denominarse Cámara **principal** (tenga en cuenta la ortografía).

    2.  La etiqueta de **cámara** principal debe establecerse **en MainCamera** (tenga en cuenta la ortografía).

    3.  Asegúrese de que **la posición de** transformación está establecida en **0, 0, 0**

    4.  Establezca **Clear Flags (Borrar marcas)** **en Solid Color (Color sólido)**

    5.  Establezca el **color de fondo** del componente de cámara en **Negro, Alfa 0** **(Código hexadecimal: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  La estructura de objetos final del *Panel de* jerarquía debe ser similar a la que se muestra en la imagen siguiente:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capítulo 5: Crear clase MeetingsUI

El primer script que debe crear es **MeetingsUI,** que es responsable de hospedar y rellenar la interfaz de usuario de la aplicación (mensaje de bienvenida, instrucciones y detalles de las reuniones).

Para crear esta clase:

1.  Haga clic con el botón derecho **en la** carpeta Activos en el panel *Project y,* a continuación, seleccione **Crear**  >  **carpeta.** Asigne a la carpeta el nombre **Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Abra la **carpeta Scripts** y, dentro de esa carpeta, haga clic con el botón derecho en **Crear** script  >  **de C#.** Asigne al script **el nombre MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Haga doble clic en el nuevo script **MeetingsUI** para abrirlo con *Visual Studio*.

4.  Inserte los siguientes espacios de nombres:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  Dentro de la clase , inserte las siguientes variables:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  A continuación, **reemplace el método Start()** y agregue **un método Awake().** Se llamará a estos cuando se inicialice la clase:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Agregue los métodos responsables de crear la interfaz de usuario *de Meetings* y rellene con las reuniones actuales cuando se solicite:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Elimine** el **método Update()** y **guarde los** cambios en Visual Studio antes de volver a Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capítulo 6: Creación de la Graph clase

El siguiente script que se va a crear **es Graph** script. Este script es responsable de realizar las llamadas para autenticar al usuario y recuperar las reuniones programadas para el día actual del calendario del usuario.

Para crear esta clase:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el **nombre Graph**.

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los siguientes espacios de nombres:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Observará que las partes del código de este script se encapsulan en torno a las directivas de [precompilación,](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)lo que es para evitar problemas con las bibliotecas al compilar la solución Visual Studio.

5.  Elimine los **métodos Start()** **y Update(),** ya que no se usarán.

6.  Fuera de **la Graph,** inserte los siguientes objetos, que son necesarios para deserializar el objeto JSON que representa las reuniones programadas diariamente:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Dentro de **la Graph,** agregue las siguientes variables:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Cambie el **valor de appId** para que sea el identificador **de** aplicación que anotó en el **[capítulo 1,](#chapter-1---create-your-app-in-the-application-registration-portal)paso 4.** Este valor debe ser el mismo que el que se muestra en el Portal de **registro de aplicaciones, en** la página de registro de la aplicación.

8.  En la **Graph,** agregue los métodos **SignInAsync()** y **AquireTokenAsync()**, que pedirán al usuario que inserte las credenciales de inicio de sesión.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Agregue los dos métodos siguientes:

    1.  **BuildTodayCalendarEndpoint(),** que compila el URI que especifica el día y el intervalo de tiempo, en el que se recuperan las reuniones programadas.

    2.  **ListMeetingsAsync()**, que solicita las reuniones programadas de *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. Ahora ha completado el script **Graph.** **Guarde los cambios** en Visual Studio antes de volver a Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capítulo 7: Creación del script GazeInput

Ahora creará **gazeinput.** Esta clase controla y realiza un seguimiento de la mirada del usuario, mediante un **raycast** procedente de la cámara **principal,** proyectando hacia delante.

Para crear el script:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el nombre **GazeInput.**

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Cambie el código de espacios de nombres para que coincida con el siguiente, junto con la adición de la etiqueta **\[ "System.Serializable" \]** encima de la **clase GazeInput,** para que se pueda serializar:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  Dentro de **la clase GazeInput,** agregue las siguientes variables:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Agregue el **método CreateCursor()** para crear el cursor HoloLens en la escena y llame al método **desde el método Start():**

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  Los métodos siguientes habilitan el raycast de mirada y mantienen un seguimiento de los objetos centrados.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
                HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;
                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Guarde los cambios** en Visual Studio antes de volver a Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capítulo 8: Creación de la clase Interactions

Ahora deberá crear el script **Interacciones,** que es responsable de:

-   Control de **la interacción** de **pulsación** y la mirada de la cámara , que permite al usuario interactuar con el "botón" de inicio de sesión en la escena.

-   Crear el objeto de "botón" de inicio de sesión en la escena con el que el usuario pueda interactuar.

Para crear el script:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo.

2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic **en Crear** script de  >  **C#.** Asigne al script el nombre **Interacciones.**

3.  Haga doble clic en el script para abrirlo con Visual Studio.

4.  Inserte los siguientes espacios de nombres:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Cambie la herencia de la **clase Interaction** de *MonoBehaviour* a **GazeInput.**

    ~~interacciones de clase pública: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  Dentro de **la clase Interaction,** inserte la siguiente variable:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Reemplace el **método Start;** observe que es un método de invalidación, que llama al método de clase Gaze "base". **Se llamará a Start()** cuando se inicialice la clase, registrándose para el reconocimiento de entrada y creando el botón de *inicio* de sesión en la escena:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Agregue el **método CreateSignInButton(),** que creará una  instancia del botón de inicio de sesión en la escena y establecerá sus propiedades:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Agregue el **método GestureRecognizer_Tapped(),** que responderá para el *evento tap* user.

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Elimine** el **método Update()** y guarde los cambios en Visual Studio antes de volver a Unity. 

## <a name="chapter-9---set-up-the-script-references"></a>Capítulo 9: Configuración de las referencias de script

En este capítulo, debe colocar el script **Interacciones** en la **cámara principal**. A continuación, ese script controlará la colocación de los demás scripts donde deben estar.

-  En la **carpeta Scripts** del panel *de Project*, arrastre el script **Interacciones** al objeto **Cámara** principal, como se muestra a continuación.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capítulo 10: Configuración de la etiqueta

El código que controle la mirada usará la etiqueta **SignInButton** para identificar con qué objeto interactuará el usuario para iniciar sesión en *Microsoft Graph*.

Para crear la etiqueta:

1.  En el Editor de Unity, haga clic en **la cámara** principal en el Panel *de jerarquía*.

2.  En el *Panel del inspector,* haga clic en **la etiqueta MainCamera** *para* abrir una lista desplegable. Haga clic **en Agregar etiqueta...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Haga clic en **+** el botón .

    ![](images/AzureLabs-Lab311-31.png)

4.  Escriba el nombre de etiqueta como **SignInButton y** haga clic en Guardar.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capítulo 11: Compilación del proyecto de Unity en UWP

Ya se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a *Build Configuración* (**File* > *Build Configuración**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Si aún no lo ha hecho, marque **Proyectos de C \# de Unity.**

3.  Haga clic en **Generar**. Unity iniciará una **Explorador de archivos,** donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así mismo den el nombre **App**. A continuación, con **la carpeta Aplicación** seleccionada, haga clic en Seleccionar **carpeta.**

4.  Unity comenzará a compilar el proyecto en la **carpeta Aplicación.**

5.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de **Explorador de archivos** en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-12---deploy-to-hololens"></a>Capítulo 12: Implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para La implementación remota) y para asegurarse de que el HoloLens está en **modo de desarrollador.** Para ello:

    1.  Al mismo tiempo que HoloLens, abra **el Configuración**.

    2.  Vaya a **Network & Internet** Wi-Fi Advanced Options (Opciones avanzadas de  >  **Wi-Fi de** Red &  >  **Internet)**

    3.  Anote **la dirección IPv4.**

    4.  A continuación, vuelva **a Configuración** y, a continuación, a Update & Security for Developers (Actualizar & **seguridad**  >  **para desarrolladores).**

    5.  Establezca **el modo de desarrollador en**.

2.  Vaya a la nueva compilación de Unity (la **carpeta Aplicación)** y abra el archivo de solución **con Visual Studio**.

3.  En Configuración **de la solución,** **seleccione Depurar**.

4.  En la **Plataforma de soluciones,** **seleccione x86, Equipo remoto.** Se le pedirá que inserte la dirección **IP** de un dispositivo remoto (el HoloLens, en este caso, que anotó).

    ![](images/AzureLabs-Lab311-34.png)

5.  Vaya al **menú Compilar** y haga clic **en Implementar** solución para realizar la instalación local de la aplicación en HoloLens.

6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el HoloLens, listo para iniciarse.

## <a name="your-microsoft-graph-hololens-application"></a>Aplicación de Graph HoloLens Microsoft

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha microsoft Graph, para leer y mostrar los datos del calendario del usuario.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Uso de Microsoft Graph para mostrar otra información sobre el usuario

-   Correo electrónico de usuario, número de teléfono o imagen de perfil

### <a name="exercise-1"></a>Ejercicio 1

Implemente el control de voz para navegar por la interfaz de usuario Graph Microsoft.