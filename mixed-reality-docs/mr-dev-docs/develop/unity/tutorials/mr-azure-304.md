---
title: 'HoloLens de primera generación y Azure (304): reconocimiento facial'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, face recognition, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219566"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (1.ª generación) y Azure 304: reconocimiento facial

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

![resultado de completar este curso](images/AzureLabs-Lab4-00.png)

En este curso aprenderá a agregar funcionalidades de reconocimiento facial a una aplicación de realidad mixta, mediante Azure Cognitive Services, con Microsoft Face API.

*Azure Face API es* un servicio de Microsoft que proporciona a los desarrolladores los algoritmos faciales más avanzados, todos en la nube. *Face API tiene* dos funciones principales: detección de caras con atributos y reconocimiento facial. Esto permite a los desarrolladores establecer simplemente un conjunto de grupos para caras y, a continuación, enviar imágenes de consulta al servicio más adelante para determinar a quién pertenece una cara. Para más información, visite la página [Azure Face Recognition](https://azure.microsoft.com/services/cognitive-services/face/).

Una vez completado este curso, tendrá una aplicación de realidad mixta HoloLens, que podrá hacer lo siguiente:

1. Use un **gesto de pulsar** para iniciar la captura de una imagen mediante la cámara HoloLens integrada. 
2. Envíe la imagen capturada al *servicio Azure Face API.*
3. Reciba los resultados del *algoritmo de Face API.*
4. Use un nombre Interfaz de usuario, para mostrar el nombre de las personas coincidentes.

Esto le enseñará a obtener los resultados del servicio Face API en la aplicación de realidad mixta basada en Unity.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con unity Project. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar la aplicación de realidad mixta.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (304): Reconocimiento facial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a Windows Mixed Reality cascos envolventes (VR). Dado que los cascos envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir cascos envolventes (VR).

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (mayo de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) tal como se muestra en el artículo instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Un [Windows Mixed Reality envolvente envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Una cámara conectada al equipo (para el desarrollo de cascos envolventes)
- Acceso a Internet para la instalación de Azure y la recuperación de Face API

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo HoloLens [instalación de](/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración](/hololens/hololens-calibration#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1---the-azure-portal"></a>Capítulo 1: Azure Portal

Para usar el *servicio Face API* en Azure, deberá configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer lugar, inicie sesión en [Azure Portal.](https://portal.azure.com) 

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **Nuevo en** la esquina superior izquierda y busque *Face API* y presione **Entrar.**

    ![búsqueda de Face API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > Es posible que **la palabra Nuevo** se haya reemplazado por Crear un **recurso** en los portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *Face API.* En la parte inferior izquierda de este símbolo del sistema, seleccione **el botón** Crear para crear una asociación con este servicio.

    ![Información de face API](images/AzureLabs-Lab4-02.png)

4.  Una vez que haya hecho clic en **Crear:**

    1. Inserte el nombre deseado para esta instancia de servicio.

    2. Seleccione una suscripción.

    3. Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un servicio *Face API,* debe estar disponible un nivel gratuito (denominado F0).

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común. 

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. La aplicación para UWP, **Person Maker,** que se usa más adelante, requiere el uso de "Oeste de EE. UU. " para la ubicación.

    6. También deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.

    7. Seleccione **Crear*.**

        ![creación del servicio Face API](images/AzureLabs-Lab4-03.png)

5.  Una vez que haya hecho clic en **Crear*,** tendrá que esperar a que se cree el servicio; esto puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación de creación de servicios](images/AzureLabs-Lab4-04.png)

7.  Haga clic en las notificaciones para explorar la nueva instancia del servicio.

    ![Ir a la notificación de recursos](images/AzureLabs-Lab4-05.png)

8.  Cuando esté listo, haga clic en **el botón Ir** al recurso de la notificación para explorar la nueva instancia del servicio.

    ![acceso a las claves de face API](images/AzureLabs-Lab4-06.png)

9.  En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la "clave" de suscripción del servicio. En la *página Inicio* rápido, del servicio *Face API,* el primer punto es el número 1, *para obtener las claves.*

10. En  la página Servicio, seleccione el hipervínculo azul **Claves** (si está en la página Inicio rápido) o el vínculo Claves en el menú de navegación de servicios (a la izquierda, anotado por el icono "clave"), para mostrar las claves. 

    > [!NOTE] 
    > Tome nota de cualquiera de las claves y resguarde, ya que la necesitará más adelante.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capítulo 2: Uso de la aplicación para UWP "Person Maker"

Asegúrese de descargar la aplicación para UWP precompilada denominada [Person Maker.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip) Esta aplicación no es el producto final de este curso, solo una herramienta para ayudarle a crear las entradas de Azure, en las que se basará el proyecto posterior.

**Person Maker** permite crear entradas de Azure, que están asociadas a personas y grupos de personas. La aplicación colocará toda la información necesaria en un formato que posteriormente faceAPI puede usar para reconocer las caras de las personas que ha agregado. 

> [IMPORTANTE] **Person Maker** usa cierta limitación básica para ayudar a garantizar que no se supera el número de llamadas de servicio por minuto para el **nivel de suscripción gratuita.** El texto verde de la parte superior cambiará a rojo y se actualizará como "ACTIVE" cuando se esté produciendo la limitación. Si este es el caso, simplemente espere a la aplicación (esperará hasta que pueda continuar accediendo al servicio face, actualizándola como "IN-ACTIVE" cuando pueda usarla de nuevo).

Esta aplicación usa las *bibliotecas Microsoft.ProjectOxford.Face,* lo que le permitirá hacer un uso completo de Face API. Esta biblioteca está disponible de forma gratuita como NuGet Paquete. Para obtener más información sobre esto y similares, las API asegúrese [de visitar el artículo de referencia de API](/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Estos son solo los pasos necesarios; las instrucciones sobre cómo hacer estas cosas se encuentran más abajo en el documento. La **aplicación Person Maker** le permitirá:
>
> - Cree un *grupo de personas*, que es un grupo compuesto por varias personas que desea asociar a él. Con su cuenta de Azure puede hospedar varios grupos de personas.
>
> - Cree una *persona*, que es miembro de un grupo de personas. Cada persona tiene un número de imágenes *de face* asociadas a ella.
>
> -  Asigne *imágenes de caras* a una *persona* para permitir que el servicio Azure Face API reconozca *a* una persona por la cara *correspondiente.*
>
> -  *Entrena* el *servicio Azure Face API.*

Tenga en cuenta que, para entrenar esta aplicación para que reconozca a las personas, necesitará diez (10) fotos de primer nivel de cada persona que quiera agregar a su grupo de personas. La Windows 10 app de Cam puede ayudarle a tomar estas medidas. Debe asegurarse de que cada foto está clara (evite desenfocar, ocultar o estar demasiado lejos del asunto), tener la foto en formato de archivo jpg o png, con un tamaño de archivo de imagen no superior a **4 MB** y no inferior a **1 KB.**

> [!NOTE]
> Si va a seguir este tutorial, no use su propia cara para el entrenamiento, ya que al colocar el HoloLens, no puede mirarse a sí mismo. Use la cara de un compañero o compañero de estudios.

Running **Person Maker**:

1.  Abra la **carpeta PersonMaker** y haga doble clic en la *solución PersonMaker* para abrirla *Visual Studio*.

2.  Una vez *abierta la solución PersonMaker,* asegúrese de que:

    1. La *configuración de la* solución se establece en **Depurar**.

    2. La *plataforma de* solución se establece en **x86**

    3. La *plataforma de destino* es Máquina **local.**

    4.  También es posible que tenga que restaurar NuGet  *paquetes* (haga clic con el botón derecho en la solución y seleccione Restaurar **NuGet paquetes**).

3.  Haga *clic en Equipo* local y se iniciará la aplicación. Tenga en cuenta que, en pantallas más pequeñas, es posible que todo el contenido no esté visible, aunque puede desplazarse más hacia abajo para verlo.

    ![interfaz de usuario del creador de personas](images/AzureLabs-Lab4-07.png)

4.  Inserte la **clave de autenticación de Azure**, que debe tener, desde el servicio Face *API* en Azure.

5.  Insertar:

    1. Identificador *que* desea asignar al grupo *de personas*. El identificador debe estar en minúsculas, sin espacios. Anote este identificador, ya que será necesario más adelante en el proyecto de Unity.
    2. Nombre *que* desea asignar al grupo *de personas* (puede tener espacios).


6.  Presione **el botón Crear grupo de** personas. Debe aparecer un mensaje de confirmación debajo del botón.

> [!NOTE]
> Si tiene un error de "Acceso denegado", compruebe la ubicación que estableció para el servicio de Azure. Como se indicó anteriormente, esta aplicación está diseñada para "Oeste de EE. UU.".

> [!IMPORTANT]
> Observará que también puede  hacer clic en el botón Capturar un grupo conocido: es para si ya ha creado un grupo de personas y desea usarlo, en lugar de crear uno nuevo. Tenga en cuenta que si hace clic *en Crear un grupo de personas* con un grupo conocido, también capturará un grupo.

7.  Inserte el *nombre* de la *persona* que desea crear.

    1. Haga clic en **el botón Crear** persona.

    2. Debe aparecer un mensaje de confirmación debajo del botón.

    3. Si desea eliminar una persona que ha creado anteriormente, puede escribir el nombre en el cuadro de texto y presionar **Eliminar persona.**

8.  Asegúrese de conocer la ubicación de diez (10) fotos de la persona que desea agregar a su grupo.

9.  Presione **Crear y abrir carpeta para** abrir Windows Explorer en la carpeta asociada a la persona. Agregue las diez (10) imágenes de la carpeta . Deben tener el formato *de* archivo *JPG o PNG.*

10. Haga clic **en Enviar a Azure.** Un contador mostrará el estado del envío, seguido de un mensaje cuando se haya completado.

11. Una vez que el contador haya finalizado y se muestre un mensaje de confirmación, haga clic en **Entrenar** para entrenar el servicio.

Una vez completado el proceso, está listo para pasar a Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para el desarrollo con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.** 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab4-08.png)

2.  Ahora deberá proporcionar un nombre de Project Unity. Inserte **MR_FaceRecognition**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca Ubicación **en un** lugar adecuado para usted (recuerde que es mejor estar más cerca de los directorios raíz). A continuación, haga **clic en Crear proyecto.**

    ![Proporcione detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar > preferencias y,** a continuación, en la nueva ventana, vaya a **Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab4-10.png)

4.  A continuación, vaya a **File > Build Configuración and switch** the platform to Universal Windows **Platform**(Plataforma Windows universal) haciendo clic en el **botón Cambiar** plataforma.

    ![Cree Configuración ventana y cambie la plataforma a UWP.](images/AzureLabs-Lab4-11.png)

5.  Vaya a **Archivo > compilación Configuración** y asegúrese de que:

    1. **El dispositivo de** destino se **establece en HoloLens**

        > Para los cascos envolventes, establezca **Dispositivo de destino** en Cualquier *dispositivo.*

    2. **Tipo de** compilación se establece en **D3D**
    3. **El SDK** se establece en **Instalado más reciente.**
    4. **Visual Studio versión está** establecida en **Instalado más reciente**
    5. **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**
    6. Guarde la escena y agrégréla a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![Haga clic en el botón Agregar escenas abiertas.](images/AzureLabs-Lab4-12.png)

        2. Seleccione el **botón Nueva** carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Creación de una nueva carpeta de scripts](images/AzureLabs-Lab4-13.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo **Nombre** de archivo : texto, escriba **FaceRecScene** y presione **Guardar.**

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab4-14.png)

    7. El resto de la configuración, en *Build Configuración*, se debe dejar como valor predeterminado por ahora.

6. En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![Abra la configuración del reproductor.](images/AzureLabs-Lab4-15.png)

7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1. **La** **versión del entorno de** ejecución de scripting debe ser **Experimental** (equivalente a .NET 4.6). Al cambiar esto, se desencadenará la necesidad de reiniciar el editor.
        2. **El back-end de** scripting debe ser **.NET**
        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Actualice otras opciones.](images/AzureLabs-Lab4-16.png)
      
    2. En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        - **InternetClient**
        - **Cámara web**

            ![Actualización de la configuración de publicación.](images/AzureLabs-Lab4-17.png)

    3. Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración),** marque **Virtual Reality Supported (Compatible** con virtual Reality), asegúrese de que se ha agregado el **SDK** Windows Mixed Reality web.

        ![Actualice el archivo X R Configuración.](images/AzureLabs-Lab4-18.png)

8.  De nuevo *en build Configuración*, los proyectos de **C#** de Unity ya no están en gris; Marque la casilla situada junto a esta. 
9.  Cierre la ventana Build Settings (Configuración de compilación).
10. Guarde la escena y Project (**FILE > SAVE SCENE /FILE > SAVE PROJECT**).

## <a name="chapter-4---main-camera-setup"></a>Capítulo 4: Configuración de la cámara principal

> [!IMPORTANT]
> Si quiere omitir el componente De configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar [este archivo .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo en el proyecto como un paquete [personalizado.](https://docs.unity3d.com/Manual/AssetPackages.html) Tenga en cuenta que este paquete también incluye la importación del *archivo DLL de Newtonsoft,* que se trata en el [capítulo 5.](#chapter-5--import-the-newtonsoftjson-library) Con esta importación, puede continuar desde el [capítulo 6.](#chapter-6---create-the-faceanalysis-class)

1.  En el Panel *de* jerarquía, seleccione la **cámara principal**.

2.  Una vez seleccionada, podrá ver todos los componentes de **la** cámara principal en el *panel inspector*.

    1. El **objeto Camera** debe denominarse Cámara **principal** (tenga en cuenta la ortografía).

    2. La etiqueta de **cámara** principal debe establecerse **en MainCamera** (tenga en cuenta la ortografía).

    3. Asegúrese de que **la posición de** transformación está establecida en **0, 0, 0**

    4. Establezca **Clear Flags (Borrar marcas)** **en Solid Color (Color sólido)**

    5. Establezca el **color de** fondo del componente de cámara **en Negro, Alfa 0 (Código hexadecimal: #00000000)**

        ![configurar componentes de cámara](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capítulo 5: Importación del Newtonsoft.Jsen la biblioteca

> [!IMPORTANT]
> Si importó ".unitypackage" en el [último capítulo,](#chapter-4---main-camera-setup)puede omitir este capítulo.

Para ayudarle a deserializar y serializar los objetos recibidos y enviados al Bot Service debe descargar elNewtonsoft.Js *en la* biblioteca. Encontrará una versión compatible ya organizada con la estructura de carpetas de Unity correcta en este [archivo de paquete de Unity.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage) 

Para importar la biblioteca:

1.  Descargue el paquete de Unity.
2.  Haga clic **en Activos,** **Importar paquete,** **Paquete personalizado.**

    ![Importación Newtonsoft.Jsen](images/AzureLabs-Lab4-20.png)

3.  Busque el paquete de Unity que ha descargado y haga clic en Abrir.
4.  Asegúrese de que todos los componentes del paquete están marcados y haga clic **en Importar**.

    ![Importación de la Newtonsoft.Jsrecursos](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capítulo 6: Creación de la clase FaceAnalysis

El propósito de la clase FaceAnalysis es hospedar los métodos necesarios para comunicarse con azure Face Recognition Service. 

- Después de enviar al servicio una imagen de captura, la analizará e identificará las caras dentro de , y determinará si alguna pertenece a una persona conocida. 
- Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.

Para crear la *clase FaceAnalysis:*

 1. Haga clic con el botón derecho en *la carpeta Recursos* que se encuentra en el panel Project y, a continuación, haga clic en **Crear**  >  **carpeta.** Llame a la carpeta **Scripts**. 

    ![Cree la clase FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla. 
3.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic **en Crear** script  >  **de C#.** Llame al script *FaceAnalysis*. 
4.  Haga doble clic en el nuevo script *de FaceAnalysis* para abrirlo con Visual Studio 2017.
5.  Escriba los siguientes espacios de nombres encima de *la clase FaceAnalysis:*

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  Ahora debe agregar todos los objetos que se usan para deserializar. Estos objetos deben agregarse fuera **del** script *FaceAnalysis* (debajo del corchete inferior). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. Los *métodos Start()* *y Update()* no se usarán, así que elimínelos ahora. 

8.  Dentro de *la clase FaceAnalysis,* agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Reemplace la **clave** y **personGroupId** por la clave de servicio y el identificador del grupo que creó anteriormente.

9.  Agregue el *método Awake(),* que inicializa la clase , agregando la clase *ImageCapture* a la cámara principal y llama al método de creación Label:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Agregue el *método CreateLabel(),* que crea el *objeto Label* para mostrar el resultado del análisis:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Agregue los *métodos DetectFacesFromImage()* *y GetImageAsByteArray().* El primero solicitará al Servicio de reconocimiento facial que detecte cualquier cara posible en la imagen enviada, mientras que la segunda es necesaria para convertir la imagen capturada en una matriz de bytes:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Agregue el *método IdentifyFaces(),* que  solicita al Servicio de reconocimiento facial que identifique cualquier cara conocida detectada anteriormente en la imagen enviada. La solicitud devolverá un identificador de la persona identificada, pero no el nombre:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Agregue el *método GetPerson().* Al proporcionar el identificador de persona,  este método solicita al Servicio de reconocimiento facial que devuelva el nombre de la persona identificada:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Recuerde guardar **los** cambios antes de volver al Editor de Unity.
15.  En el Editor de Unity, arrastre el script FaceAnalysis desde la carpeta Scripts del panel Project al objeto Cámara principal en el *panel Jerarquía*. El nuevo componente de script se agregará a la cámara principal. 

![Colocar FaceAnalysis en la cámara principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capítulo 7: Creación de la clase ImageCapture

El propósito de la clase *ImageCapture* es hospedar los métodos necesarios para comunicarse con *azure Face Recognition Service* a fin de analizar la imagen que va a capturar, identificar caras en ella y determinar si pertenece a una persona conocida. Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.

Para crear la *clase ImageCapture:*
 
1.  Haga clic con el botón derecho en **la carpeta Scripts** que ha creado anteriormente y, a continuación, haga clic en **Crear**, Script **de C#.** Llame al script *ImageCapture.* 
2.  Haga doble clic en el nuevo script *ImageCapture* para abrirlo con Visual Studio 2017.
3.  Escriba los siguientes espacios de nombres encima de la clase ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  Dentro de *la clase ImageCapture,* agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Agregue los *métodos Awake()* y *Start()* necesarios para inicializar la clase y permitir que el HoloLens capture los gestos del usuario:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Agregue el *tapHandler() al* que se llama cuando el usuario realiza un *gesto de pulsar:*

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Agregue el *método ExecuteImageCaptureAndAnalysis(),* que iniciará el proceso de captura de imágenes:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Agregue los controladores a los que se llama cuando se haya completado el proceso de captura de fotos:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Recuerde guardar **los** cambios antes de volver al Editor de Unity.

## <a name="chapter-8---building-the-solution"></a>Capítulo 8: Creación de la solución

Para realizar una prueba exhaustiva de la aplicación, deberá realizar una instalación local en la HoloLens.

Antes de hacerlo, asegúrese de que:

-   Todas las configuraciones mencionadas en el capítulo 3 se establecen correctamente. 
-   El script *FaceAnalysis* está asociado al objeto Cámara principal. 
-   Tanto la **clave de autenticación como** el identificador **de** grupo se han establecido en el script *FaceAnalysis.*

Este punto está listo para compilar la solución. Una vez creada la solución, estará listo para implementar la aplicación.

Para comenzar el proceso de compilación:

1.  Guarde la escena actual haciendo clic en Archivo, Guardar.
2.  Vaya a Archivo, Compilar Configuración, haga clic en Agregar escenas abiertas.
3.  Asegúrese de marcar Proyectos de C# de Unity.

    ![Implementación de la Visual Studio implementación](images/AzureLabs-Lab4-24.png)

4.  Presione Compilar. Al hacerlo, Unity iniciará una ventana de Explorador de archivos, donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora, dentro del proyecto de Unity, y llámela Aplicación. Después, con la carpeta Aplicación seleccionada, presione Seleccionar carpeta. 
5.  Unity comenzará a compilar el proyecto en la carpeta Aplicación. 
6.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una Explorador de archivos en la ubicación de la compilación.

    ![Implementación de la solución desde Visual Studio](images/AzureLabs-Lab4-25.png)

7.  Abra la carpeta Aplicación y, a continuación, abra la nueva solución Project (como se ha visto anteriormente, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capítulo 9: Implementación de la aplicación

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

    ![Cambio de la configuración de la solución](images/AzureLabs-Lab4-26.png)
 
5.  Vaya al menú **Compilar y** haga clic en **Implementar solución** para realizar la instalación local de la aplicación en la HoloLens.
6.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el HoloLens, listo para iniciarse.

> [!NOTE]
> Para implementar en casco  envolvente, establezca plataforma de  solución en *Máquina local* y establezca la configuración en *Depurar*, con *x86* como **plataforma**. A continuación, implemente en la máquina local, mediante **el menú Compilar** y seleccione Implementar *solución.* 


## <a name="chapter-10---using-the-application"></a>Capítulo 10: Uso de la aplicación

1.  Con el HoloLens, inicie la aplicación.
2.  Mire a la persona que se ha registrado en *Face API.* Asegúrese de lo siguiente:

    -  La cara de la persona no está demasiado lejana y claramente visible
    -  La iluminación del entorno no es demasiado oscura

3.  Use el gesto de pulsar para capturar la imagen de la persona.
4.  Espere a que la aplicación envíe la solicitud de análisis y reciba una respuesta.
5.  Si la persona se ha reconocido correctamente, el nombre de la persona aparecerá como texto de la interfaz de usuario.
6.  Puede repetir el proceso de captura con el gesto de pulsar cada pocos segundos.

## <a name="your-finished-azure-face-api-application"></a>La aplicación de Azure Face API finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio Azure Face Recognition para detectar caras dentro de una imagen e identificar las caras conocidas.

![resultado de completar este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

**Azure Face API es** lo suficientemente eficaz como para detectar hasta 64 caras en una sola imagen. Extienda la aplicación para que pueda reconocer dos o tres caras, entre muchas otras personas.

### <a name="exercise-2"></a>Ejercicio 2

Azure **Face API también** puede proporcionar todo tipo de información de atributos. Integre esto en la aplicación. Esto podría ser incluso más interesante, cuando se combina con [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).