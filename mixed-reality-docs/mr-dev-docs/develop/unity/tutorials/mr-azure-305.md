---
title: 'HoloLens de primera generación y Azure (305): funciones y almacenamiento'
description: Complete este curso para aprender a implementar Azure Storage y Functions dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, functions, storage, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115194107"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (1ª generación) y Azure 305: Funciones y almacenamiento

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br> 

![final product -start](images/AzureLabs-Lab5-00.png)

En este curso, aprenderá a crear y usar Azure Functions almacenar datos con un recurso Azure Storage, dentro de una aplicación de realidad mixta.

*Azure Functions* es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "functions", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas. *Azure Functions* admite varios lenguajes de desarrollo, incluidos \# C, \# F, Node.js, Java y PHP. Para obtener más información, visite el [artículo Azure Functions .](/azure/azure-functions/functions-overview)

*Azure Storage* es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos, con el seguro de que serán de alta disponibilidad, seguros, duraderos, escalables y redundantes. Esto significa que Microsoft controlará todo el mantenimiento y los problemas críticos. Para obtener más información, visite Azure Storage [artículo](/azure/storage/common/storage-introduction).

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta que podrá hacer lo siguiente:

1.  Permitir que el usuario mire alrededor de una escena.
2.  Desencadena la generación de objetos cuando el usuario mira un "botón" 3D.
3.  Una función de Azure elegirá los objetos generados.
4.  A medida que se genera cada objeto, la aplicación almacenará el tipo de objeto en un archivo de *Azure,* ubicado *en Azure Storage*.
5.  Tras la carga por segunda vez, se recuperarán los datos de *Azure File* y se usarán para reproducir las acciones de generación de la instancia anterior de la aplicación.

En la aplicación, es el usuario el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con unity Project. Es su trabajo usar los conocimientos que obtenga de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Realidad mixta y Azure (305): Funciones y almacenamiento</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en Windows Mixed Reality cascos envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir HoloLens.

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
- Una suscripción a una cuenta de Azure para crear recursos de Azure
- Acceso a Internet para la instalación y recuperación de datos de Azure

## <a name="before-you-start"></a>Antes de comenzar

Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure Portal

Para usar **el Azure Storage,** deberá crear y configurar una cuenta de Storage **en** el Azure Portal.

1.  Inicie sesión en [Azure Portal.](https://portal.azure.com)

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los proctores para configurar la nueva cuenta.

2.  Una vez que haya  iniciado sesión, haga clic en Nuevo en la esquina superior izquierda y busque Storage *cuenta y* haga clic en **Entrar.**

    ![azure storage search](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *Azure Storage cuenta.* En la parte inferior izquierda de este símbolo del sistema, seleccione **el botón** Crear para crear una asociación con este servicio.

    ![crear servicio](images/AzureLabs-Lab5-02.png)

4.  Una vez que haya hecho clic en **Crear:**

    1.  Inserte un *nombre* para la cuenta, tenga en cuenta que este campo solo acepta números y letras minúsculas.

    2.  En *Modelo de implementación,* seleccione **Resource Manager.**

    3.  En *Tipo de cuenta,* **seleccione Storage (uso general v1).**

    4.  Determine la *ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.

    5.  En *Replicación,* seleccione Almacenamiento con redundancia geográfica con acceso de **lectura (RA-GRS).**

    6.  En *Rendimiento*, seleccione **Estándar**.

    7.  Deje *Transferencia segura requerida como* **Deshabilitado.**

    8.  Seleccione una opción en *Suscripción*.

    9. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.

    11. Seleccione **Crear**.

        ![información del servicio de entrada](images/AzureLabs-Lab5-03.png)

5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación en Azure Portal](images/AzureLabs-Lab5-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![ir al recurso](images/AzureLabs-Lab5-05.png)

8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia de servicio *Storage cuenta.*

    ![Claves de acceso](images/AzureLabs-Lab5-06.png)

9.  Haga *clic en Claves de* acceso para mostrar los puntos de conexión de este servicio en la nube. Use *Bloc de notas* o similar para copiar una de las claves para usarla más adelante. Además, tenga en cuenta *el valor de* Cadena de conexión, ya que se usará en la clase *AzureServices,* que creará más adelante.

    ![copiar cadena de conexión](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capítulo 2: Configuración de una función de Azure

Ahora escribirá una **función de Azure** **en** el servicio de Azure.

Puede usar una función de **Azure** para hacer casi todo lo que haría con una función clásica en el código, la diferencia es que cualquier aplicación que tenga credenciales para acceder a su cuenta de Azure puede acceder a esta función.

Para crear una función de Azure:

1.  En *Azure Portal, haga* clic en **Nuevo en** la esquina superior izquierda, busque *Function App* y haga clic **en Entrar.**

    ![creación de una aplicación de función](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.

2.  La nueva página proporcionará una descripción de *Azure Function App* Service. En la parte inferior izquierda de este símbolo del sistema, seleccione **el botón** Crear para crear una asociación con este servicio.

    ![información de la aplicación de función](images/AzureLabs-Lab5-09.png)

3.  Una vez que haya hecho clic en **Crear:**

    1.  Proporcione un nombre *de aplicación*. Aquí solo se pueden usar letras y números (se permiten mayúsculas o minúsculas).

    2.  Seleccione la suscripción que *prefiera.*

    3. Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    4.  Para este ejercicio, seleccione *Windows* como el **sistema operativo elegido.**

    5.  Seleccione *Plan de consumo* para el Plan de **hospedaje.**

    6.  Determine la *ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones. Para obtener un rendimiento óptimo, seleccione la misma región que la cuenta de almacenamiento.

    7.  Para *Storage*, seleccione **Usar existente** y, a continuación, mediante el menú desplegable, busque el almacenamiento creado anteriormente.

    8.  Deje *Application Ideas* desactivado para este ejercicio.

        ![detalles de la aplicación de función de entrada](images/AzureLabs-Lab5-10.png)

4.  Haga clic en el botón **Crear**.

5.  Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación de Azure Portal](images/AzureLabs-Lab5-11.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia del servicio. 

    ![ir a la aplicación de función de recursos](images/AzureLabs-Lab5-12.png)

8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia de *Function App* Service.

9.  En el *panel de Function App,* mantenga el mouse sobre *Functions*, que se encuentra en el panel de la izquierda y, a continuación, haga clic en el símbolo **+ (más).**

    ![create new function](images/AzureLabs-Lab5-13.png)

10. En la página siguiente, asegúrese de que **webhook + API** está seleccionado y, en Elegir un *idioma,* seleccione **CSharp**, ya que este será el idioma que se usará para este tutorial. Por último, haga clic en **el botón Crear esta** función.

    ![seleccionar web hook csharp](images/AzureLabs-Lab5-14.png)

11. Debe ir a la página de códigos (run.csx), si no es así, haga clic en la función recién creada en la lista Funciones del panel de la izquierda.

    ![abrir nueva función](images/AzureLabs-Lab5-15.png)

12. Copie el código siguiente en la función. Esta función simplemente devolverá un entero aleatorio entre 0 y 2 cuando se llame a . No se preocupe por el código existente, no dude en pegarlo en la parte superior.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Seleccione **Guardar**.

14. El resultado debe ser parecido a la imagen siguiente.

15. Haga clic en **Obtener dirección URL de** función y anote el punto de *conexión* que se muestra. Tendrá que insertarlo en la *clase AzureServices* que creará más adelante en este curso.

    ![Obtener el punto de conexión de la función](images/AzureLabs-Lab5-16.png)

    ![Inserción del punto de conexión de la función](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capítulo 3: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con Mixed Reality y, como tal, es una buena plantilla para otros proyectos.

Configure y pruebe los cascos envolventes de realidad mixta.

> [!NOTE]
> No necesitará **controladores** de movimiento para este curso. Si necesita soporte técnico para configurar el casco envolvente, visite [el artículo configuración de realidad mixta](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra Unity y haga clic en **Nuevo.**

    ![Creación de un nuevo proyecto de Unity](images/AzureLabs-Lab5-17.png)

2.  Ahora deberá proporcionar un nombre de Project Unity. Inserte **MR_Azure_Functions**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca Ubicación *en un* lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Asigne un nombre al nuevo proyecto de Unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar**  >  **preferencias** y, a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![establecer Visual Studio como editor de scripts](images/AzureLabs-Lab5-19.png)

4.  A continuación, vaya a **File**  >  **Build Configuración** and switch the platform to Universal Windows **Platform**,by click on the Switch Platform button( Cambiar **plataforma).**

    ![cambiar la plataforma a uwp](images/AzureLabs-Lab5-20.png)

5.  Vaya a **File** Build Configuración (Compilación de  >   archivos) y asegúrese de que:

    1. **El dispositivo de** destino se establece **en Cualquier dispositivo.**

        > Para Microsoft HoloLens, establezca **Dispositivo de destino** *en HoloLens*.

    2. **Tipo de** compilación se establece en **D3D**

    3. **El SDK** se establece en **Instalado más reciente.**

    4. **Visual Studio versión está** establecida en **Más reciente instalada**

    5. **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**

    6. Guarde la escena y agrégréla a la compilación.

        1.  Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab5-21.png)

        2.  Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![crear carpeta de escenas](images/AzureLabs-Lab5-22.png)

        3.  Abra la carpeta **Scenes** recién creada y, a continuación, en el campo Nombre de **archivo:** texto, escriba **FunctionsScene** y presione **Guardar.**

            ![Guardar escena de funciones](images/AzureLabs-Lab5-23.png)

6.  El resto de la configuración, en **Build Configuración**, se debe dejar como valor predeterminado por ahora.

    ![Dejar la configuración de compilación predeterminada](images/AzureLabs-Lab5-24.png)

7.  En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.*

    ![configuración del reproductor en inspector](images/AzureLabs-Lab5-25.png)

8.  En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión del runtime de** scripting debe ser **Experimental** (equivalente a .NET 4.6), lo que desencadenará la necesidad de reiniciar el editor.
        2.  **El back-end de scripting** debe ser **.NET**
        3.  **El nivel de compatibilidad de** API debe ser **.NET 4.6**

    2.  En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:
        
        -  **InternetClient**

            ![establecer funcionalidades](images/AzureLabs-Lab5-26.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de **Publishing Configuración**), marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se ha agregado Windows Mixed Reality **SDK.**

        ![establecer la configuración de XR](images/AzureLabs-Lab5-27.png)

9.  De nuevo *en Build Configuración* Unity C# Projects (Proyectos de C# de *Unity)* ya no está en gris; Marque la casilla situada junto a esta.

    ![Tic c# projects](images/AzureLabs-Lab5-28.png)

10.  Cierre la ventana Build Settings (Configuración de compilación).

11. Guarde la escena y Project (**ARCHIVO GUARDAR** ESCENA /  >  **ARCHIVO GUARDAR**  >  **PROYECTO**).

## <a name="chapter-4---setup-main-camera"></a>Capítulo 4: Configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir los componentes de configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar [este archivo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo en el proyecto como un paquete [personalizado.](https://docs.unity3d.com/Manual/AssetPackages.html) También contendrá los archivos DLL del capítulo siguiente. Después de la importación, continúe desde [el capítulo 7.](#chapter-7---create-the-azureservices-class) 

1.  En el *Panel de* jerarquía, encontrará un objeto denominado **Cámara** principal, este objeto representa el punto de vista "principal" una vez que está "dentro" de la aplicación.

2.  Con el panel de Unity delante de usted, seleccione la cámara **principal GameObject**. Observará que el *panel inspector* (que se encuentra generalmente a la derecha, dentro del panel) mostrará los distintos componentes de *ese GameObject*, con *Transformar* en la parte superior, seguido de *Cámara* y algunos otros componentes. Deberá restablecer la transformación de la cámara principal para que esté correctamente posicionada.

3.  Para ello, seleccione el icono **de engranaje** situado junto al componente *Transformar* de la cámara y seleccione **Restablecer**.

    ![restablecer transformación](images/AzureLabs-Lab5-29.png)

4.  A continuación, **actualice el componente** Transformar para que se parezca a lo siguiente:

    |         |    TRANSFORMACIÓN: POSICIÓN   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **S**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRANSFORMACIÓN: ROTACIÓN |       |
    | :---: | :------------------: | :----:|
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORMACIÓN: ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 1     | 1                 | 1     |

    ![establecer la transformación de la cámara](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capítulo 5: Configuración de la escena de Unity

1.  Haga clic con el botón derecho en un área vacía del *Panel de jerarquía*, en Objeto **3D**, agregue un **plano**.

    ![crear nuevo plano](images/AzureLabs-Lab5-31.png)

2.  Con el **objeto Plano** seleccionado, cambie los parámetros siguientes en el *Panel inspector*:

    |       | TRANSFORMACIÓN: POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORMACIÓN: ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 10    | 1                 | 10    |

    ![establecer posición y escala del plano](images/AzureLabs-Lab5-32.png)

    ![vista de escena del plano](images/AzureLabs-Lab5-33.png)

3.  Haga clic con el botón derecho en un área vacía del *Panel de jerarquía*, en Objeto **3D**, agregue un **cubo**.

    1.  Cambie el nombre del cubo **a GazeButton** (con el cubo seleccionado, presione "F2").

    2.  Cambie los parámetros siguientes en el *panel inspector*:

        |       | TRANSFORMACIÓN: POSICIÓN |       |
        | :---: | :------------------: |:-----:|
        | **X** | **S**                | **Z** |
        | 0     | 3                    | 5     |


        ![establecer la transformación del botón de mirada](images/AzureLabs-Lab5-34.png)

        ![vista de la escena del botón de mirada](images/AzureLabs-Lab5-35.png)

    3.  Haga clic en **el botón desplegable** Etiqueta y haga clic en Agregar etiqueta para abrir el panel *Etiquetas & Capas.* 

        ![agregar nueva etiqueta](images/AzureLabs-Lab5-36.png)

        ![seleccionar más](images/AzureLabs-Lab5-37.png)

    4.  Seleccione el **botón + (más)** y, en el campo Nuevo nombre *de* etiqueta, escriba **GazeButton** y presione **Guardar.**

        ![name new tag](images/AzureLabs-Lab5-38.png)

    5.  Haga clic en **el objeto GazeButton** en el *Panel de* jerarquía y, en el *panel inspector,* asigne la etiqueta **GazeButton recién** creada.

        ![asignar el botón de mirada a la nueva etiqueta](images/AzureLabs-Lab5-39.png)

4.  Haga clic con el botón derecho en el objeto **GazeButton,** en el *Panel* de jerarquía, y agregue un **objeto GameObject vacío** (que se agregará como un *objeto* secundario).

5.  Seleccione el nuevo objeto y cámbiele el nombre **ShapeSpawnPoint.**

    1.  Cambie los parámetros siguientes en el *panel inspector*:

        |       | TRANSFORMACIÓN: POSICIÓN |       |
        | :---: | :------------------: |:----: |
        | **X** |**S**                 | **Z** |
        | 0     | -1                   | 0     |

        ![actualizar transformación de punto de generación de forma](images/AzureLabs-Lab5-40.png)

        ![vista de la escena del punto de generación de formas](images/AzureLabs-Lab5-41.png)

6.  A continuación, creará un **objeto Text 3D** para proporcionar comentarios sobre el estado del servicio de Azure.

    Vuelva a hacer clic con el botón derecho en **GazeButton** en el Panel de jerarquía y agregue un objeto **3D Object**  >  **3D Text** como elemento *secundario.*

    ![Crear nuevo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  Cambie el nombre **del objeto 3D Text** a **AzureStatusText.**

8.  Cambie el **objeto AzureStatusText** Transform como se muestra a continuación:

    |       | TRANSFORMACIÓN: POSICIÓN |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORMACIÓN: ESCALA |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > No se preocupe si parece estar fuera del centro, ya que se solucionará cuando se actualice el componente Text Mesh siguiente.

9.  Cambie el **componente Text Mesh** para que coincida con lo siguiente:

    ![establecer componente de malla de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > El color seleccionado aquí es color hexadecimal: **000000FF,** aunque no dude en elegir el suyo propio, simplemente asegúrese de que sea legible.

10. La estructura del Panel de jerarquía ahora debe tener el siguiente aspecto:

    ![Malla de texto en la jerarquía](images/AzureLabs-Lab5-43b.png)

10. La escena debería tener ahora este aspecto:

    ![Malla de texto en la vista de escena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capítulo 6: Importación de Azure Storage para Unity

Va a usar Azure Storage para Unity (que a su vez aprovecha el SDK de .NET para Azure). Puede leer más sobre esto en el artículo de [Azure Storage for Unity](/sandbox/gamedev/unity/azure-storage-unity).

Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (del 4 al 7 de esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente de [".unitypackage" GitHub](https://aka.ms/azstorage-unitysdk). A continuación, haga lo siguiente:

1.  Agregue el **archivo .unitypackage** a Unity mediante la opción de menú **Importar**  >  **paquete**  >  **personalizado de** recursos.

2.  En el **cuadro Importar paquete de Unity** que aparece, puede seleccionar todo en **Complemento**  >  **Storage**. Desactive todo lo demás, ya que no es necesario para este curso.

    ![importar al paquete](images/AzureLabs-Lab5-45.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la *carpeta Storage* complementos en *Complementos*, en la Project y seleccione solo los siguientes *complementos:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![desactive Cualquier plataforma.](images/AzureLabs-Lab5-46.png)

5.  Con *estos complementos específicos seleccionados,* **desactive Cualquier** *plataforma* **y** *desactive WSAPlayer* y haga clic **en Aplicar.**

    ![aplicar archivos DLL de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Vamos a marcar estos complementos concretos para que solo se utilicen en el editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la *carpeta Storage* complemento, seleccione solo:

    -   Microsoft.Data.Services.Client

        ![set don't process for dlls](images/AzureLabs-Lab5-48.png)

7.  Active la casilla **No procesar en** Plataforma Configuración haga clic en **Aplicar**. 

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Vamos a marcar este complemento como "No procesar" porque el patcher de ensamblados de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se procese.

## <a name="chapter-7---create-the-azureservices-class"></a>Capítulo 7: Creación de la clase AzureServices

La primera clase que va a crear es *la clase AzureServices.*

La *clase AzureServices* será responsable de:

-   Almacenamiento de credenciales de la cuenta de Azure.

-   Llamar a la App de Azure función.

-   Carga y descarga del archivo de datos en azure cloud Storage.

Para crear esta clase:

1.  Haga clic con el botón derecho *en la carpeta asset,* que se encuentra en el panel Project, Create Folder   >  **(Crear carpeta).** Asigne a la carpeta el **nombre Scripts**.

    ![crear nueva carpeta](images/AzureLabs-Lab5-50.png)

    ![carpeta de llamadas: scripts](images/AzureLabs-Lab5-51.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en la carpeta **Create**  >  **C# Script (Crear script de C#).** Llame al script *AzureServices.*

4.  Haga doble clic en la *nueva clase AzureServices* para abrirla *con Visual Studio*.

5.  Agregue los siguientes espacios de nombres a la parte superior de *AzureServices*:

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Agregue los siguientes campos de inspector dentro de *la clase AzureServices:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  A continuación, agregue las siguientes variables miembro dentro *de la clase AzureServices:*

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Asegúrese de reemplazar los valores del punto *de conexión* y la *cadena de* conexión por los valores del almacenamiento de Azure, que se encuentran en Azure Portal.

8.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().* Se llamará a estos métodos cuando se inicialice la clase :

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Rellenaremos el código de *CallAzureFunctionForNextShape()* en un [capítulo futuro.](#chapter-10---completing-the-azureservices-class)

9.  Elimine el *método Update(),* ya que esta clase no lo usará.

10. Guarde los cambios en Visual Studio y, a continuación, vuelva a Unity.

11. Haga clic en la *clase AzureServices y* arrástrela desde la carpeta Scripts hasta el objeto Cámara principal del *Panel de jerarquía.*

12. Seleccione la cámara principal, a continuación, tome el objeto secundario **AzureStatusText** debajo del objeto **GazeButton** y colócalo dentro del campo de destino de referencia **AzureStatusText,** en *el inspector*, para proporcionar la referencia al script *AzureServices.*

    ![asignar destino de referencia de texto de estado de Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capítulo 8: Creación de la clase ShapeFactory

El siguiente script que se va a crear es la *clase ShapeFactory.* El rol de esta clase es crear una nueva forma, cuando se solicite, y mantener un historial de las formas creadas en una lista *de historial de formas*. Cada vez que se crea una forma, la lista *Historial* de formas se actualiza en la *clase AzureService* y, a continuación, se *almacena en el Azure Storage*. Cuando se inicia la aplicación, si se encuentra un  archivo almacenado en el Azure Storage *,* se recupera y reproduce la lista Historial de formas, con el objeto **Texto 3D** que proporciona si la forma generada es del almacenamiento o es nueva.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts** que creó anteriormente.

2.  Haga clic con el botón derecho en la carpeta **Create**  >  **C# Script (Crear script de C#).** Llame al script *ShapeFactory*.

3.  Haga doble clic en el nuevo script *ShapeFactory* para abrirlo con *Visual Studio*.

4.  Asegúrese de *que la clase ShapeFactory* incluye los siguientes espacios de nombres:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Agregue las variables que se muestran a continuación a *la clase ShapeFactory* y reemplace las *funciones Start()* y *Awake()* por las siguientes:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  El *método CreateShape()* genera las formas primitivas, basándose en el parámetro *entero* proporcionado. El parámetro booleano se usa para especificar si la forma creada actualmente es del almacenamiento o es nueva. Coloque el código siguiente en la *clase ShapeFactory,* debajo de los métodos anteriores:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.

8.  De nuevo en el Editor de Unity, haga clic en la clase *ShapeFactory* y arrástrela desde la carpeta **Scripts** hasta el objeto **Cámara** principal del *Panel de jerarquía.*

9. Con la cámara principal seleccionada, observará que al componente de script *ShapeFactory* le falta la referencia *de punto de generación.* Para corregirlo, arrastre el objeto **ShapeSpawnPoint** desde el *Panel de* jerarquía hasta el destino **de referencia de punto** de generación.

    ![set shape factory reference target](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capítulo 9: Creación de la clase Gaze

El último script que debe crear es la *clase Gaze.*

Esta clase es responsable de crear un **raycast** que se proyectará hacia delante desde la cámara principal para detectar qué objeto está mirando el usuario. En este caso, Raycast deberá identificar si el usuario está mirando el objeto **GazeButton** en la escena y desencadenar un comportamiento.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts** que creó anteriormente.

2.  Haga clic con el botón derecho en Project panel, **Crear**  >  **script de C#.** Llame al script *Gaze*.

3.  Haga doble clic en el nuevo script *gaze* para abrirlo con *Visual Studio.*

4.  Asegúrese de que el siguiente espacio de nombres está incluido en la parte superior del script:

    ```csharp
        using UnityEngine;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *clase Gaze:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Algunas de estas variables se podrán editar en el *editor*.

6.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().*

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Agregue el código siguiente, que creará un objeto de cursor al principio, junto con el método *Update(),* que ejecutará el método Raycast, junto con donde se alterna el booleano GazeEnabled:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. A continuación, agregue el método *UpdateRaycast(),* que proyectará un raycast y detectará el destino de la llamada.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

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

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Por último, agregue el *método ResetFocusedObject(),* que alternará el color actual de los objetos GazeButton, lo que indica si está creando una nueva forma o no.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Guarde los cambios en Visual Studio antes de volver a Unity.

11.  Haga clic en la *clase Gaze y* arrástrela desde la carpeta Scripts hasta el objeto **Cámara** principal del Panel *de jerarquía.*

## <a name="chapter-10---completing-the-azureservices-class"></a>Capítulo 10: Finalización de la clase AzureServices

Con los demás scripts en su lugar, ahora es posible *completar la* *clase AzureServices.* Esto se logrará mediante:

1.  Agregar un nuevo método denominado *CreateCloudIdentityAsync()*, para configurar las variables de autenticación necesarias para comunicarse con Azure.

    > Este método también comprobará la existencia de un archivo almacenado previamente que contiene la lista de formas.
    >
    > **Si se encuentra el archivo**, deshabilitará la mirada del usuario y desencadenará la creación de formas, según el patrón de formas, tal como se almacena en **Azure Storage archivo**. El usuario puede ver esto, ya que text **mesh** proporcionará la pantalla "Storage" o "New", según el origen de las formas.
    >
    > **Si no se encuentra ningún archivo,** habilitará *gaze*, lo que permite al usuario crear formas al mirar el objeto **GazeButton** en la escena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  El siguiente fragmento de código es desde el *método Start();* donde se realizará una llamada al *método CreateCloudIdentityAsync().* No dude en copiar el método *Start()* actual, con lo siguiente:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Rellene el código del método *CallAzureFunctionForNextShape().* Usará la instancia de *Azure Function App* creada anteriormente para solicitar un índice de forma. Una vez recibida la nueva forma, este método enviará la forma a la clase *ShapeFactory* para crear la nueva forma en la escena. Use el código siguiente para completar el cuerpo de *CallAzureFunctionForNextShape().*

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Agregue un método para crear una cadena, concatenando los enteros almacenados en la lista del historial de formas y *guardándose* en el Azure Storage archivo .

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Agregue un método para recuperar el texto almacenado en el archivo ubicado en Azure Storage *File* y *deserializarlo* en una lista.

6.  Una vez completado este proceso, el método vuelve a habilitar la mirada para que el usuario pueda agregar más formas a la escena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Guarde los cambios en Visual Studio antes de volver a Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capítulo 11: Compilación de la solución para UWP

Para comenzar el proceso de compilación:

1.  Vaya a  >  **Compilación de archivos Configuración**.

    ![compilación de la aplicación](images/AzureLabs-Lab5-54.png)

2.  Haga clic en **Generar**. Unity iniciará una *Explorador de archivos,* donde debe crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así den su nombre *App.* A continuación, *con la carpeta* Aplicación seleccionada, presione Seleccionar **carpeta**.

3.  Unity comenzará a compilar el proyecto en la *carpeta Aplicación.*

4.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de *Explorador de archivos* en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-12---deploying-your-application"></a>Capítulo 12: Implementación de la aplicación

Para implementar la aplicación:

1.  Vaya a la *carpeta Aplicación* que se creó en el último [capítulo .](#chapter-11---build-the-uwp-solution) Verá un archivo con el nombre de las aplicaciones, con la extensión ".sln", en el que debe hacer doble clic, para abrirlo dentro *de Visual Studio*.

2.  En la **Plataforma de soluciones,** **seleccione x86, Máquina local.**

3.  En Configuración **de la solución,** **seleccione Depurar**.

    > Para la Microsoft HoloLens, es posible que le resulte más fácil establecer esta opción en Equipo remoto *para* que no se le aterrizó en el equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP** de su HoloLens, que se puede encontrar en las opciones avanzadas de Wi-Fi de Internet de **Configuración**  >  **Network**  >    >  &; IPv4 es la dirección que debe usar. 
    > - Asegúrese **de que el modo de** desarrollador está en **on**; se encuentra **en Configuración** Update &  >  **Security para**  >  **desarrolladores.**

    ![implementación de la solución](images/AzureLabs-Lab5-55.png)

4.  Vaya al menú **Compilar y** haga clic en Deploy **Solution (Implementar solución)** para realizar la instalación local de la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse y probarse.

## <a name="your-finished-azure-functions-and-storage-application"></a>La aplicación Azure Functions y Storage finalizadas

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha los Azure Functions y Azure Storage servicios. La aplicación podrá sacar partido de los datos almacenados y proporcionar una acción basada en los datos.

![final product -end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Cree un segundo punto de generación y registre desde qué punto de generación se creó un objeto. Al cargar el archivo de datos, reproduce las formas que se generan desde la ubicación en la que se crearon originalmente.

### <a name="exercise-2"></a>Ejercicio 2

Cree una manera de reiniciar la aplicación, en lugar de tener que volver a abrirla cada vez. **La carga de** escenas es un buen punto de inicio. Después de hacerlo, cree una manera de borrar la lista almacenada en *Azure Storage*, para que se pueda restablecer fácilmente desde la aplicación.