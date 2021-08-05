---
title: 'HoloLens de primera generación y Azure (312): integración de bots'
description: Complete este curso para aprender a crear e implementar un bot mediante Microsoft Bot Framework v4 y comunicarse con él en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, computer vision, hololens, immersive, vr, microsoft bot framework v4, web app bot, bot framework, microsoft bot, Windows 10, Visual Studio
ms.openlocfilehash: 61a39806c2b434cb85d39a9b208ea8659ec8cbc301d8955ee1330bda4149f0db
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189972"
---
# <a name="hololens-1st-gen-and-azure-312-bot-integration"></a>HoloLens (1.ª generación) y Azure 312: integración de bots

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

En este curso, aprenderá a crear e implementar un bot mediante Microsoft Bot Framework V4 y a comunicarse con él a través de una Windows Mixed Reality aplicación. 

![](images/AzureLabs-Lab312-00.png)

La **Microsoft Bot Framework V4 es** un conjunto de API diseñadas para proporcionar a los desarrolladores las herramientas necesarias para crear una aplicación de bot extensible y escalable. Para obtener más información, visite [la página Microsoft Bot Framework o](https://dev.botframework.com/) el repositorio de Git [V4.](https://github.com/Microsoft/botbuilder-dotnet/wiki)

Después de completar este curso, habrá creado una Windows Mixed Reality, que podrá hacer lo siguiente:

1. Use un **gesto de pulsar** para iniciar el bot que escucha la voz de los usuarios.
2. Cuando el usuario haya dicho algo, el bot intentará proporcionar una respuesta.
3. Muestre la respuesta de los bots como texto, situado cerca del bot, en la escena de Unity.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con el proyecto de Unity. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (312): Integración de bots</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a Windows Mixed Reality cascos envolventes (VR). Dado que los cascos envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir cascos envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (julio de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Windows Mixed Reality envolvente envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Acceso a Internet para Azure y para la recuperación de bots de Azure. Para obtener más información, [siga este vínculo](https://dev.botframework.com/).

### <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo HoloLens [instalación de](/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración](/hololens/hololens-calibration#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1--create-the-bot-application"></a>Capítulo 1: Creación de la aplicación bot

El primer paso consiste en crear el bot como una aplicación web ASP.Net Core. Una vez que haya terminado y probado, lo publicará en Azure Portal.

1.  Abra Visual Studio. Cree un proyecto, seleccione **Aplicación web ASP NET Core** como tipo de proyecto (lo encontrará en la subsección .NET Core) y llámelo **MyBot**. Haga clic en **Aceptar**.

2.  En la ventana que aparecerá, seleccione **Vacío.** Asegúrese también de que el destino está establecido en **ASP NET Core 2.0** y de que la autenticación está establecida **en Sin autenticación.** Haga clic en **Aceptar**.  

    ![Creación de la aplicación de bot](images/AzureLabs-Lab312-01.png)

3.  Ahora se abrirá la solución. Haga clic con el botón derecho en **Solution Mybot (Mybot** **de solución)** en Explorador de soluciones haga clic en **Manage NuGet Packages for Solution (Administrar paquetes de NuGet para la solución).** 

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-02.png)

4.  En la **pestaña Examinar,** busque **Microsoft.Bot.Builder.Integration.AspNet.Core** (asegúrese de que la opción Incluir **versión previa está** activada). Seleccione la versión del **paquete 4.0.1-preview** y marque los cuadros del proyecto. A continuación, haga clic **en Instalar**. Ahora ha instalado las bibliotecas necesarias para la **Bot Framework v4.** Cierre la NuGet de trabajo.

    ![Creación de la aplicación de bot](images/AzureLabs-Lab312-03.png)

5.  Haga clic con el botón derecho *en Project*, **MyBot**, en la **Explorador de soluciones** haga clic **en Agregar** **|** **clase**.

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-04.png)

6.  Asigne a la clase **el nombre MyBot** y haga clic en **Agregar.**

    ![Creación de la aplicación de bot](images/AzureLabs-Lab312-05.png)

7.  Repita el punto anterior para crear otra clase denominada **ConversationContext.** 

8.  Haga clic con el botón derecho **en wwwroot** en la **Explorador de soluciones** haga clic **en Agregar** nuevo **|** **elemento**. Seleccione  **Página HTML** (la encontrará en la subsección Web). Asigne al archivo **eldefault.html**. Haga clic en **Agregar**.

    ![Creación de la aplicación de bot](images/AzureLabs-Lab312-06.png)

9.  La lista de clases o objetos de la **Explorador de soluciones** debe ser como la imagen siguiente.

    ![Creación de la aplicación de bot](images/AzureLabs-Lab312-07.png)

10. Haga doble clic en la **clase ConversationContext.** Esta clase es responsable de contener las variables usadas por el bot para mantener el contexto de la conversación. Estos valores de contexto de conversación se mantienen en una instancia de esta clase, porque cualquier instancia de la **clase MyBot** se actualizará cada vez que se reciba una actividad. Agregue el código siguiente a la clase :

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. Haga doble clic en la **clase MyBot.** Esta clase hospedará los controladores a los que llama cualquier actividad entrante del cliente. En esta clase agregará el código usado para compilar la conversación entre el bot y el cliente. Como se mencionó anteriormente, una instancia de esta clase se inicializa cada vez que se recibe una actividad. Agregue el código siguiente a esta clase:

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. Haga doble clic en la **clase Startup.** Esta clase inicializará el bot. Agregue el código siguiente a la clase :

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. Abra el **archivo de** clase Program y compruebe que el código en él es el mismo que el siguiente:

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. Recuerde guardar los cambios, para ello, vaya a **Archivo** Guardar todo , en la barra de herramientas de la parte  >  superior de Visual Studio.

## <a name="chapter-2---create-the-azure-bot-service"></a>Capítulo 2: Creación de la Azure Bot Service

Ahora que ha creado el código para el bot, tiene que publicarlo en una instancia de *Web App Bot* Service, en Azure Portal. En este capítulo se muestra cómo crear y configurar el Bot Service en Azure y, a continuación, publicar el código en él.

1.  En primer lugar, inicie sesión en Azure Portal ( https://portal.azure.com) . 

    1. Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

2.  Una vez que haya  iniciado sesión, haga clic en Crear un recurso en la esquina superior izquierda, busque bot de *aplicación web* y haga clic **en Entrar.**

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  La nueva página proporcionará una descripción de *Web App Bot* Service. En la parte inferior izquierda de esta página, seleccione el **botón** Crear para crear una asociación con este servicio.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  Una vez que haya hecho clic en **Crear:**

    1. Inserte el nombre **deseado para** esta instancia de servicio.
    2. Seleccione una opción en **Suscripción**.
    3. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, [siga este vínculo.](/azure/azure-resource-manager/resource-group-portal)

    4. Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    5. Seleccione el **plan de** tarifa adecuado para usted; si es la primera vez que crea un servicio *de bot* de aplicación web, debe estar disponible un nivel gratuito (denominado F0).
    6. **El nombre de** la aplicación se puede dejar igual que el *nombre del bot.* 
    7. Deje la *plantilla bot* como **Básico (C#).**
    8. *El plan o la ubicación* de App Service se deberían haber rellenado automáticamente para su cuenta.
    9. Establezca la **Azure Storage** que desea usar para hospedar el bot. Si aún no tiene una, puede crearla aquí.
    10. También deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.
    11. Haga clic en Crear.
 
        ![Cree el Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  Haga clic en la notificación para explorar la nueva instancia del servicio. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio de Azure. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  En este momento, debe configurar una característica denominada **Direct Line** permitir que la aplicación cliente se comunique con esta Bot Service. Haga clic **en Canales** y, en la sección **Agregar un canal** destacado, haga clic en Configurar Direct Line **canal**.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. En esta página encontrará las claves **secretas** que permitirán que la aplicación cliente se autentique con el bot. Haga clic en **el botón** Mostrar y tome una copia de una de las claves mostradas, ya que la necesitará más adelante en el proyecto. 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a>Capítulo 3: Publicación del bot en la aplicación web de Azure Bot Service

Ahora que el servicio está listo, debe publicar el código del bot, que creó anteriormente, en la aplicación web recién creada Bot Service.

> [!NOTE] 
> Tendrá que publicar el bot en el servicio de Azure cada vez que realice cambios en la solución o el código del bot.

1.  Vuelva a la solución Visual Studio que creó anteriormente. 
2.  Haga clic con el botón derecho **en el proyecto MyBot,** en la **Explorador de soluciones** y, a continuación, haga clic **en Publicar**.

    ![Publicación del bot en la aplicación web de Azure Bot Service](images/AzureLabs-Lab312-16.png)

3.  En  la página Elegir un destino de publicación, haga clic en **App Service**, seleccione Existente y, por último, haga clic en Crear perfil **(es** posible que tenga que hacer clic en la flecha desplegable junto al botón Publicar, si no está visible).  

    ![Publicación del bot en la aplicación web de Azure Bot Service](images/AzureLabs-Lab312-17.png)

4. Si aún no ha iniciado sesión en su cuenta Microsoft, tendrá que hacerlo aquí.
5. En la **página** Publicar, verá que tiene que establecer la misma **suscripción** que usó para la creación *de Web App Bot* Service. A continuación, **establezca La** vista como **grupo de** recursos y, en la estructura de carpetas desplegable, seleccione el grupo **de** recursos que ha creado anteriormente. Haga clic en **Aceptar**. 

    ![Publicación del bot en la aplicación web de Azure Bot Service](images/AzureLabs-Lab312-18.png)

6.  Ahora haga clic en **el botón** Publicar y espere a que se publique el bot (puede tardar unos minutos).

    ![Publicación del bot en la aplicación web de Azure Bot Service](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a>Capítulo 4: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para el desarrollo con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.** 

    ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-20.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Inserte **HoloLens bot**. Asegúrese de que la plantilla de proyecto está establecida en **3D.** Establezca Ubicación **en un** lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-21.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar > preferencias y,** a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-22.png)

4.  A continuación, vaya a **File > Build Configuración y** seleccione Universal Windows Platform (Plataforma **Windows** universal) y haga clic en el botón **Switch Platform** (Cambiar plataforma) para aplicar la selección.

    ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-23.png)

5.  Mientras sigue en **el > compilación Configuración** y asegúrese de que:

    1.  **El dispositivo de** destino se **establece en HoloLens**

        > Para los cascos envolventes, establezca **Dispositivo de destino** en Cualquier *dispositivo.*

    2.  **Tipo de** compilación se establece en **D3D**

    3.  **El SDK** se establece en **Instalado más reciente.**

    4.  **Visual Studio versión está** establecida en **Instalado más reciente**

    5.  **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**

    6.  Guarde la escena y agrégréla a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.
        
            ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-24.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

             ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-25.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *Nombre* de archivo : texto, escriba **BotScene** y haga clic en **Guardar.**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-26.png)

    7. El resto de la configuración, en **Build Configuración**, se debe dejar como valor predeterminado por ahora.

6. En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-27.png)

7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1. **La versión del entorno de** ejecución de scripting debe ser Experimental (equivalente de NET **4.6);** Para cambiar esto, será necesario reiniciar el Editor.
        2. **El back-end de** scripting debe ser **.NET**
        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-28.png)
      
    2. En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        - **InternetClient**
        - **Micrófono**

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-29.png)

    3. Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración),** marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se ha agregado el **SDK** Windows Mixed Reality web.

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab312-30.png)

8.  De nuevo en *build Configuración* Unity C# Projects (Proyectos de C# de _Unity)_ ya no está en gris; Marque la casilla situada junto a esto. 
9.  Cierre la ventana Build Settings (Configuración de compilación).
10. Guarde la escena y el proyecto **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).


## <a name="chapter-5--camera-setup"></a>Capítulo 5: Configuración de la cámara

> [!IMPORTANT]
> Si desea omitir el componente *De* configuración de Unity de este curso y continuar directamente en el código, no dude en descargar este paquete [Azure-MR-312-Package.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)impórtelo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continúe con el capítulo [7.](#chapter-8--create-the-botobjects-class)

1.  En el *panel Jerarquía*, seleccione la **cámara principal**. 
2.  Una vez seleccionado, podrá ver todos los componentes de **la** cámara principal en el *panel Inspector*.

    1. El **objeto Camera** debe denominarse Cámara **principal** (tenga en cuenta la ortografía)
    2. La etiqueta de **cámara principal** debe establecerse en **MainCamera** (tenga en cuenta la ortografía)
    3. Asegúrese de que **la posición de** transformación está establecida en **0, 0, 0**
    4. Establezca **Clear Flags (Borrar marcas)** **en Solid Color (Color sólido).**
    5. Establezca el **color de** fondo del componente Cámara **en Negro, Alfa 0 (código hexadecimal: #00000000)**

    ![configuración de la cámara](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a>Capítulo 6: Importación de la biblioteca Newtonsoft

Para ayudarle a deserializar y serializar los objetos recibidos y enviados al Bot Service debe descargar la **biblioteca Newtonsoft.** Encontrará una versión [compatible ya organizada con la estructura de carpetas de Unity correcta aquí.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage) 

Para importar la biblioteca Newtonsoft en el proyecto, use el paquete de Unity que se incluye en este curso.

1.  Agregue el *paquete .unitypackage* a Unity mediante la opción de menú **Importar**  >  **paquete**  >  **personalizado de** recursos.

    ![Importación de la biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  En el **cuadro Importar paquete de Unity** que aparece, asegúrese de que todo lo que aparece en (e incluye) **Complementos** está seleccionado.

    ![Importación de la biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta Newtonsoft** en **Complementos en** la vista del proyecto y seleccione el complemento Newtonsoft.

    ![](images/AzureLabs-Lab312-35b.png)

5.  Con el complemento Newtonsoft seleccionado, asegúrese de que **Cualquier** plataforma esté desactivada **y,** a continuación, asegúrese de que **WSAPlayer** también esté desactivado **y,** a continuación, haga clic **en Aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > Marcar estos complementos los configura para que solo se utilicen en el Editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la **carpeta WSA,** dentro de la **carpeta Newtonsoft.** Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** está **desactivada** 
    -   **solo** **WSAPlayer** está **activado**
    -   **No se comprueba el** **proceso**

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a>Capítulo 7: Creación de BotTag

1.  Cree un nuevo **objeto Tag** denominado **BotTag.** Seleccione la cámara principal de la escena. Haga clic en el menú desplegable Etiqueta del panel Inspector. Haga clic en **Agregar etiqueta**.

    ![configuración de la cámara](images/AzureLabs-Lab312-32.png)
 
2.  Haga clic en el **+** símbolo. Asigne a la **nueva etiqueta el** nombre **BotTag** y *guarde*.

    ![configuración de la cámara](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> **No aplique** **BotTag** a la cámara principal. Si ha hecho esto accidentalmente, asegúrese de volver a cambiar la etiqueta Cámara principal a *MainCamera*.

## <a name="chapter-8--create-the-botobjects-class"></a>Capítulo 8: Creación de la clase BotObjects

El primer script que debe crear es la clase **BotObjects,** que es una clase vacía creada para que se pueda almacenar una serie de otros objetos de clase dentro del mismo script y a los que otros scripts de la escena puedan acceder.

La creación de esta clase es simplemente una opción arquitectónica; en su lugar, estos objetos podrían hospedarse en el script bot que creará más adelante en este curso.

Para crear esta clase: 

1.  Haga clic con el botón derecho *en Project panel y,* a continuación, **> carpeta**. Asigne a la carpeta el **nombre Scripts**. 

    ![Cree la carpeta scripts.](images/AzureLabs-Lab312-36.png)

2.  Haga doble clic en la **carpeta Scripts** para abrirlo. A continuación, dentro de esa carpeta, haga clic con el botón derecho y **seleccione Crear > script de C#.** Asigne al script el nombre **BotObjects.** 

3.  Haga doble clic en el nuevo script **BotObjects** para abrirlo con **Visual Studio**.

4.  Elimine el contenido del script y reemplácelo por el código siguiente:

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-9--create-the-gazeinput-class"></a>Capítulo 9: Creación de la clase GazeInput

La siguiente clase que va a crear es **la clase GazeInput.** Esta clase es responsable de:

- Crear un cursor que represente la *mirada* del reproductor.
- Detectar objetos alcanzados por la mirada del reproductor y mantener una referencia a los objetos detectados.

Para crear esta clase: 

1.  Vaya a la **carpeta Scripts** que creó anteriormente. 
2.  Haga clic con el botón derecho en la carpeta **Crear > script de C#.** Llame al script **GazeInput**. 
3.  Haga doble clic en el nuevo script **GazeInput** para abrirlo con **Visual Studio**.
4.  Inserte la siguiente línea justo encima del nombre de clase:

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  A continuación, agregue las siguientes variables dentro de **la clase GazeInput,** encima **del método Start():**

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  Se debe agregar código para el método **Start().** Se llamará a esto cuando se inicialice la clase :

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Implemente un método que cree instancias y configure el cursor de mirada: 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  Implemente los métodos que configurarán Raycast desde la cámara principal y realizará un seguimiento del objeto enfocado actual.

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-10--create-the-bot-class"></a>Capítulo 10: Creación de la clase Bot

El script que va a crear ahora se denomina **Bot**. Esta es la clase principal de la aplicación, que almacena: 

- Las credenciales del bot de aplicación web
- Método que recopila los comandos de voz del usuario
- El método necesario para iniciar conversaciones con el bot de aplicación web 
- Método necesario para enviar mensajes al bot de aplicación web 

Para enviar mensajes al Bot Service, la cortina **SendMessageToBot()** compilará una actividad, que es un objeto reconocido por el Bot Framework como datos enviados por el usuario. 
 
Para crear esta clase: 

1. Haga doble clic en la **carpeta Scripts** para abrirlo. 
2. Haga clic con el botón derecho en **la carpeta Scripts,** haga clic **en Crear > script de C#.** Asigne al script el **nombre Bot**. 
3. Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4. Actualice los espacios de nombres para que sean los mismos que los siguientes, en la parte superior de la **clase Bot:**

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. Dentro de **la clase Bot,** agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > Asegúrese de insertar la clave **secreta del bot** en la variable **botSecret.** Habrá anotado la clave **secreta del bot** al principio de este curso, en el capítulo **[2,](#chapter-2---create-the-azure-bot-service)paso 10.**

7. Ahora es necesario agregar código para **Awake()** y **Start().** 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. Agregue los dos controladores a los que llaman las bibliotecas de voz cuando comienza y termina la captura de voz. *DictationRecognizer* dejará de capturar automáticamente la voz del usuario cuando el usuario deje de hablar.

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. El siguiente controlador recopila el resultado de la entrada de voz del usuario y llama a la corutina responsable de enviar el mensaje a la aplicación web Bot Service.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. Se llama a la corrotina siguiente para iniciar una conversación con el bot. Observará que una vez completada la llamada de conversación, llamará a **SendMessageToCoroutine()** pasando una serie de parámetros que establecerán la actividad que se enviará al Bot Service como un mensaje vacío. Esto se hace para solicitar al Bot Service que inicie el diálogo.

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. Se llama a la corrotina siguiente para compilar la actividad que se va a enviar al Bot Service. 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. Se llama a la corrotina siguiente para solicitar una respuesta después de enviar una actividad al Bot Service. 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. El último método que se va a agregar a esta clase es necesario para mostrar el mensaje en la escena:

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > Es posible que vea un error en la consola del editor de Unity sobre la falta de la **clase SceneOrganiser.** Ignore este mensaje, ya que creará esta clase más adelante en el tutorial.

14.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-11--create-the-interactions-class"></a>Capítulo 11: Creación de la clase Interactions

La clase que va a crear ahora se denomina **Interacciones.** Esta clase se usa para detectar el HoloLens entrada de pulsación del usuario. 

Si el usuario pulsa mientras mira el objeto *Bot* en la escena y el bot está listo  para escuchar entradas de voz, el objeto Bot cambiará el color a rojo y comenzará a escuchar entradas de voz. 

Esta clase hereda de la **clase GazeInput,** por lo que puede hacer referencia al método **Start()** y a las variables de esa clase, lo que se indica mediante el uso de **base**. 
 
Para crear esta clase:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic en > script de **C#.** Asigne al script el nombre **Interactions**. 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres y la herencia de clases para que sean los mismos que los siguientes, en la parte superior de **la clase Interacciones:**

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  Dentro de **la clase Interactions,** agregue la variable siguiente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  A continuación, **agregue el método Start():**

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  Agregue el controlador que se desencadenará cuando el usuario realice el gesto de pulsar delante de la HoloLens cámara.

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-12--create-the-sceneorganiser-class"></a>Capítulo 12: Creación de la clase SceneOrganiser

La última clase necesaria en este laboratorio se denomina **SceneOrganiser**. Esta clase configurará la escena mediante programación, agregando componentes y scripts a la cámara principal y creando los objetos adecuados en la escena.
 
Para crear esta clase:

1.  Haga doble clic en la **carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic en > script de **C#.** Asigne al script el nombre **SceneOrganiser.** 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Dentro de **la clase SceneOrganiser,** agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  A continuación, **agregue los métodos Awake()** **y Start():**

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  Agregue el método siguiente, responsable de crear el objeto Bot en la escena y configurar los parámetros y componentes:

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  Agregue el método siguiente, responsable de crear el objeto de interfaz de usuario en la escena, que representa las respuestas del bot:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*
9.  En el Editor de Unity, arrastre el script **SceneOrganiser** desde la carpeta Scripts a la cámara principal. El componente Scene Desenlace debería aparecer ahora en el objeto Cámara principal, como se muestra en la imagen siguiente.

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a>Capítulo 13: Antes de compilar

Para realizar una prueba exhaustiva de la aplicación, deberá cargarla localmente en el HoloLens.
Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones mencionadas en [**el capítulo 4**](#chapter-4--set-up-the-unity-project) se establecen correctamente. 
-   El script **SceneOrganiser** está asociado al **objeto Cámara** principal. 
-   En la **clase Bot,** asegúrese de que ha insertado la clave secreta **del bot** en la **variable botSecret.**

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a>Capítulo 14: Compilación y instalación local de la HoloLens

Ahora se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a **Build Configuración**, File > **Build Configuración... .**
2.  En la ventana **Compilar Configuración,** haga clic en **Compilar**.

    ![Creación de la aplicación desde Unity](images/AzureLabs-Lab312-38.png)

3.  Si aún no lo ha hecho, marque **Proyectos de C# de Unity.**
4.  Haga clic en **Generar**. Unity iniciará una **Explorador de archivos,** donde debe crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así den su nombre **App.** A continuación, con **la carpeta** Aplicación seleccionada, haga clic **en Seleccionar carpeta.** 
5.  Unity comenzará a compilar el proyecto en la **carpeta Aplicación.** 
6.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de **Explorador de archivos** en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-15--deploy-to-hololens"></a>Capítulo 15: Implementación en HoloLens

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para Implementación remota) y para asegurarse de que el HoloLens está en **modo de desarrollador**. Para ello:

    1. Mientras lleva su HoloLens, abra **el Configuración**.
    2. Vaya a **Network & Internet > Wi-Fi > Advanced Options**
    3. Anote **la dirección IPv4.**
    4. A continuación, vuelva **a Configuración** y, a continuación, a Actualizar & seguridad > **para desarrolladores.** 
    5. Establezca Modo de desarrollador en.

2.  Vaya a la nueva compilación de Unity (la **carpeta Aplicación)** y abra el archivo de solución **con Visual Studio**.
3.  En Configuración **de la solución,** **seleccione Depurar**.
4.  En la **Plataforma de soluciones,** **seleccione x86**, **Equipo remoto.** 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  Vaya al menú **Compilar y haga** clic en Implementar **solución** para realizar la instalación local de la aplicación en el HoloLens.
6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el HoloLens, listo para iniciarse.

    > [!NOTE]
    > Para implementar en casco  envolvente, establezca plataforma de  solución en *Máquina local* y establezca la configuración en *Depurar*, con *x86* como **plataforma**. A continuación, implemente en la máquina local, mediante **el menú Compilar** y seleccione Implementar *solución.* 

## <a name="chapter-16--using-the-application-on-the-hololens"></a>Capítulo 16: Uso de la aplicación en el HoloLens

- Una vez que haya iniciado la aplicación, verá el bot como una esfera azul delante de usted.

- Use el **gesto de pulsar** mientras mira la esfera para iniciar una conversación. 
 
- Espere a que se inicie la conversación (la interfaz de usuario mostrará un mensaje cuando se produce). Una vez que reciba el mensaje introductorio del bot, pulse de nuevo en el bot para que se vuelva rojo y empiece a escuchar la voz. 

- Una vez que deje de hablar, la aplicación enviará el mensaje al bot y recibirá rápidamente una respuesta que se mostrará en la interfaz de usuario. 

- Repita el proceso para enviar más mensajes al bot (tendrá que pulsar cada vez que desee sen un mensaje).

En esta conversación se muestra cómo el bot puede conservar la información (su nombre), a la vez que proporciona información conocida (por ejemplo, los elementos que se han agotado).

#### <a name="some-questions-to-ask-the-bot"></a>Algunas preguntas para hacer al bot:

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a>La aplicación bot de aplicación web (v4) finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el bot de aplicación web de Azure, Microsoft Bot Framework v4.

![Producto final](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

La estructura de conversación de este laboratorio es muy básica. Use Microsoft LUIS para proporcionar al bot funcionalidades de comprensión del lenguaje natural.

### <a name="exercise-2"></a>Ejercicio 2

Este ejemplo no incluye la terminación de una conversación y el reinicio de una nueva. Para completar la característica Bot, intente implementar el cierre en la conversación.