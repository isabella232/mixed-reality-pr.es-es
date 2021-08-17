---
title: 'HoloLens de primera generación y Azure (310): detección de objetos'
description: Complete este curso para aprender a entrenar y usar un modelo de aprendizaje automático para reconocer objetos similares y su posición en el mundo real.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, custom vision, detección de objetos, realidad mixta, academy, unity, tutorial, api, hololens, Windows 10, Visual Studio
ms.openlocfilehash: b152aaebbd3858140b79133a8f8e551aab06b4f3
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905740"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (1.ª generación) y Azure 310: detección de objetos

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

En este curso, aprenderá a reconocer el contenido visual personalizado y su posición espacial dentro de una imagen proporcionada, mediante las funcionalidades de "Detección de objetos" de Azure Custom Vision en una aplicación de realidad mixta.

Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objetos. Después, usará el modelo entrenado para reconocer objetos similares y aproximarse a su ubicación en el mundo real, tal y como proporciona la captura de cámara de Microsoft HoloLens o una cámara que se conecta a un equipo para cascos envolventes (VR).

![resultado del curso](images/AzureLabs-Lab310-00.png)

**Azure Custom Vision, la detección de** objetos es un servicio de Microsoft que permite a los desarrolladores crear clasificadores de imágenes personalizados. Estos clasificadores se pueden usar con nuevas imágenes para detectar objetos dentro de esa nueva imagen, proporcionando los límites de **Box dentro** de la propia imagen. El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar este proceso. Para más información, visite los vínculos siguientes:

* [Página de Custom Vision Azure](/azure/cognitive-services/custom-vision-service/home)
* [Límites y cuotas](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1. El usuario podrá mirar *un* objeto, que ha entrenado mediante azure Custom Vision Service, detección de objetos.
2. El usuario usará el gesto *Pulsar* para capturar una imagen de lo que está viendo.
3. La aplicación enviará la imagen a Azure Custom Vision Service.
4. Habrá una respuesta del servicio que mostrará el resultado del reconocimiento como texto del espacio mundial. Esto se logrará mediante el uso del seguimiento espacial de Microsoft HoloLens, como una manera de comprender la  posición mundial del objeto reconocido y, a continuación, usar la etiqueta asociada a lo que se detecta en la imagen para proporcionar el texto de la etiqueta.

El curso también abarcará la carga manual de imágenes, la creación de etiquetas y el entrenamiento del servicio para reconocer distintos objetos (en el ejemplo proporcionado, un cup) estableciendo el cuadro *de* límites dentro de la imagen que envíe.

> [!IMPORTANT]
> Después de la creación y el uso de la aplicación, el desarrollador debe volver al servicio azure Custom Vision, identificar las predicciones realizadas por el servicio y determinar si eran correctas o no (mediante el etiquetado de todo lo que faltaba en el servicio y el ajuste de los rectángulos *delimitadores).* A continuación, se puede volver a entrenar el servicio, lo que aumentará la probabilidad de que reconozca objetos del mundo real.

Este curso le enseñará a obtener los resultados de Azure Custom Vision Service, Detección de objetos, en una aplicación de ejemplo basada en Unity. Será su función aplicar estos conceptos a una aplicación personalizada que pueda estar creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (310): Detección de objetos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (julio de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist-for-hololens)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](../../install-the-tools.md#installation-checklist-for-hololens)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist-for-hololens)
- Un [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details) con el modo de desarrollador habilitado
- Acceso a Internet para la instalación de Azure y la recuperación Custom Vision Service
-  Se requiere una serie de al menos quince (15) imágenes) para cada objeto que quiera que Custom Vision reconocer. Si lo desea, puede usar las imágenes ya proporcionadas con este curso, [una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para esto, visite el artículo HoloLens [configuración de .](/hololens/hololens-setup)
3.  Es una buena idea realizar la calibración y el ajuste de sensores al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración](/hololens/hololens-calibration#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1---the-custom-vision-portal"></a>Capítulo 1: El portal de Custom Vision

Para usar **Azure Custom Vision Service**, deberá configurar una instancia de para que esté disponible para la aplicación.

1.  Vaya [a la página principal Custom Vision **Service**](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en **Tareas iniciales**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Inicie sesión en Custom Vision Portal.

    ![](images/AzureLabs-Lab310-02.png)

4.  Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

5.  Una vez que haya iniciado sesión por primera vez, se le pedirá el panel *Términos de* servicio. Haga clic en la casilla *para aceptar los términos*. A continuación, **haga clic en Acepto**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Una vez aceptados los términos, ahora se encuentra en la *sección Mis* proyectos. Haga clic **en Nuevo Project**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.

    1.  Insertar un nombre para el proyecto

    2.  Insertar una descripción para el proyecto **(opcional)**

    3.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Si desea obtener más [información sobre los grupos de recursos de Azure, vaya a la documentación asociada.](/azure/azure-resource-manager/resource-group-portal)

    4.  Establezca los **tipos Project como** **Detección de objetos (versión preliminar).**

8.  Cuando haya terminado, haga clic en **Crear proyecto** y se le redirigirá a la página del proyecto Custom Vision Service.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: Entrenamiento del Custom Vision proyecto

Una vez en Custom Vision Portal, el objetivo principal es entrenar el proyecto para reconocer objetos específicos en imágenes.

Necesita al menos quince (15) imágenes para cada objeto que quiera que reconozca la aplicación. Puede usar las imágenes proporcionadas con este curso[(una serie de tazas).](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)

Para entrenar el Custom Vision proyecto:

1.  Haga clic en el **+** botón situado junto a **Etiquetas**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Agregue un **nombre** para la etiqueta que se usará para asociar las imágenes. En este ejemplo se usan imágenes de cups para el reconocimiento, por lo que hemos denominado la etiqueta para esta, **Cup**. Haga clic **en Guardar** una vez finalizada.

    ![](images/AzureLabs-Lab310-07.png)

3.  Observará que **se ha** agregado la etiqueta (es posible que tenga que volver a cargar la página para que aparezca). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Haga clic **en Agregar imágenes** en el centro de la página.

    ![](images/AzureLabs-Lab310-09.png)

5.  Haga clic **en Examinar archivos locales** y vaya a las imágenes que desea cargar para un objeto, con el mínimo de quince (15).

    > [!TIP]
    >  Puede seleccionar varias imágenes a la vez para cargarlas.

    ![](images/AzureLabs-Lab310-10.png)

6.  Presione **Upload archivos** una vez que haya seleccionado todas las imágenes con las que desea entrenar el proyecto. Los archivos comenzarán a cargarse. Una vez que haya confirmado la carga, haga clic **en Listo.**

    ![](images/AzureLabs-Lab310-11.png)

7.  En este momento, las imágenes se cargan, pero no se etiquetan.

    ![](images/AzureLabs-Lab310-12.png)

8.  Para etiquetar las imágenes, use el mouse. Al mantener el puntero sobre la imagen, un resaltado de selección le ayudará dibujando automáticamente una selección alrededor del objeto. Si no es preciso, puede dibujar los suyos propios. Esto se logra manteniendo presionado el botón izquierdo en el mouse y arrastrando la región de selección para abarcar el objeto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Después de seleccionar el objeto dentro de la imagen, un pequeño símbolo del sistema le pedirá que *agregue la etiqueta de región*. Seleccione la etiqueta creada anteriormente ('Cup', en el ejemplo anterior), o si va a agregar más etiquetas, escriba y haga clic en **el botón + (más).**

    ![](images/AzureLabs-Lab310-14.png) 

10. Para etiquetar la siguiente imagen, puede hacer clic en la flecha situada a la derecha de la hoja o cerrar la hoja de etiquetas (haciendo clic en la **X** en la esquina superior derecha de la hoja) y, a continuación, haga clic en la siguiente imagen. Una vez que tenga lista la siguiente imagen, repita el mismo procedimiento. Haga esto para todas las imágenes que ha cargado, hasta que todas estén etiquetadas. 

    > [!NOTE]
    >  Puede seleccionar varios objetos en la misma imagen, como la imagen siguiente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Una vez que los haya etiquetado todos, haga clic en el botón **etiquetado,** a la izquierda de la pantalla, para mostrar las imágenes etiquetadas. 

    ![](images/AzureLabs-Lab310-16.png)

12. Ya está listo para entrenar el servicio. Haga clic en **el botón** Train (Entrenar) y se iniciará la primera iteración de entrenamiento.

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Una vez creado, podrá ver dos botones denominados **Make default (Hacer** predeterminado) y **Prediction URL (Dirección URL de predicción).** Haga clic primero **en Crear valor** predeterminado y, a continuación, haga clic en Url de **predicción.**

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > El punto de conexión que se proporciona  a partir de este se establece en la iteración que se haya marcado como predeterminada. Por lo tanto, si más adelante realiza una *nueva* iteración y la actualiza como predeterminada, no tendrá que cambiar el código.

14. Una vez que haya hecho clic en Url de **predicción,** abra *Bloc de notas* y copie y pegue la dirección **URL** (también denominada **Prediction-Endpoint**) y la clave de predicción **del** servicio , para poder recuperarla cuando la necesite más adelante en el código.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para el desarrollo con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity y** haga clic en **Nuevo.**

    ![](images/AzureLabs-Lab310-21.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Inserte **CustomVisionObjDetection.** Asegúrese de que el tipo de proyecto está  establecido en **3D** y establezca la ubicación en un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar*  >  *preferencias** y, a continuación, en la nueva ventana, vaya a **Herramientas externas.** Cambie **Editor de scripts externos** a **Visual Studio**. Cierre la **ventana Preferencias.**

    ![](images/AzureLabs-Lab310-23.png)

4.  A continuación, vaya a **File > Build Configuración and** switch the **Platform** to Universal *Windows Platform*(Plataforma Windows universal) y haga clic en el botón Switch **Platform (Cambiar plataforma).**

    ![](images/AzureLabs-Lab310-24.png)

5.  En la misma **ventana de Configuración** compilación, asegúrese de que se establecen los siguientes valores:

    1.  **El dispositivo de** destino se establece **en HoloLens**        
    2.  **Tipo de** compilación se establece en **D3D**
    3.  **El SDK** se establece en **Instalado más reciente.**
    4.  **Visual Studio versión está** establecida en **Más reciente instalada**
    5.  **Build and Run (Compilar** y ejecutar) se establece en **Local Machine (Máquina local).**            
    6.  El resto de la configuración, **en Build Configuración**, se debe dejar como valor predeterminado por ahora.

        ![](images/AzureLabs-Lab310-25.png)

6.  En la misma **ventana Configuración** compilación, haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.**

7. En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión del runtime de** scripting debe ser **Experimental** (equivalente a .NET 4.6), lo que desencadenará la necesidad de reiniciar el editor.

        2. **El back-end de** scripting debe **ser .NET.**

        3. **El nivel de compatibilidad de** api debe ser **.NET 4.6.**

            ![](images/AzureLabs-Lab310-26.png)

    2.  En la **pestaña Publishing Configuración** (Configuración publicación), en **Capabilities (Funcionalidades),** active:

        1. **InternetClient**

        2.  **Cámara web**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración),** marque **Virtual Reality Supported (Compatible con virtual Reality)** y, a continuación, asegúrese de que se agrega el **SDK** Windows Mixed Reality.

        ![](images/AzureLabs-Lab310-29.png)

8.  De nuevo en **Build Configuración** *,Unity C \# Projects* ya no está en gris: marque la casilla situada junto a esto.

9.  Cierre la ventana **Build Settings** (Configuración de compilación).

10. En el **Editor**, haga clic en **Editar**  >  **Project Configuración**  >  **Gráficos**.

    ![](images/AzureLabs-Lab310-30.png)

11. En el **Panel del inspector,** *se abrirá Configuración* gráficos. Desplácese hacia abajo hasta que vea una matriz denominada **Always Include Shaders**. Agregue una ranura aumentando la variable **Tamaño** en uno (en este ejemplo, era 8, por lo que se ha hecho 9). Aparecerá una nueva ranura, en la última posición de la matriz, como se muestra a continuación:

    ![](images/AzureLabs-Lab310-31.png)

12. En la ranura, haga clic en el círculo de destino pequeño junto a la ranura para abrir una lista de sombreadores. Busque el **sombreador Sombreadores heredados/Transparente/Difuso** y haga doble clic en él. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capítulo 4: Importación del paquete CustomVisionObjDetection de Unity

Para este curso, se le proporciona un paquete de recursos de Unity denominado **Azure-MR-310.unitypackage.** 

> [SUGERENCIA] Los objetos compatibles con Unity, incluidas escenas enteras, se pueden empaquetar en un **archivo .unitypackage** y exportarse o importarse en otros proyectos. Es la manera más segura y eficaz de mover recursos entre diferentes **proyectos de Unity.**

Puede encontrar el [paquete Azure-MR-310](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)que debe descargar aquí.

1.  Con el panel de Unity delante  de usted, haga clic en Activos en el menú de la parte superior de la pantalla y, a continuación, haga clic en Importar paquete **> paquete personalizado.**

    ![](images/AzureLabs-Lab310-33.png)

2.  Use el selector de archivos para seleccionar **el paquete Azure-MR-310.unitypackage** y haga clic **en Abrir**. Se mostrará una lista de componentes para este recurso. Para confirmar la importación, haga clic **en el botón** Importar.

    ![](images/AzureLabs-Lab310-34.png)

3.  Una vez que haya terminado de importarse, observará que las carpetas del paquete ahora se han agregado a la **carpeta Assets.** Este tipo de estructura de carpetas es típica de un proyecto de Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  La **carpeta Materials** contiene el material utilizado por el cursor de **mirada.** 

    2.  La **carpeta Plugins** contiene el archivo DLL de Newtonsoft usado por el código para deserializar la respuesta web del servicio. Las dos (2) versiones diferentes contenidas en la carpeta y la sub carpeta son necesarias para permitir que la biblioteca se utilice y compile tanto en el Editor de Unity como en la compilación de UWP. 

    3.  La **carpeta Prefabs** contiene los elementos prefabs contenidos en la escena. Estos son:

        1.  **GazeCursor**, el cursor usado en la aplicación. Funcionará junto con el objeto prefab SpatialMapping para poder colocarse en la escena sobre objetos físicos.
        2.  Label **, que** es el objeto de interfaz de usuario que se usa para mostrar la etiqueta de objeto en la escena cuando es necesario.
        3.  **SpatialMapping**, que es el objeto que permite a la aplicación usar la creación de un mapa virtual, mediante el seguimiento espacial Microsoft HoloLens la aplicación.

    4.  La **carpeta Scenes** que contiene actualmente la escena pre-creada para este curso.

4.  Abra la **carpeta Scenes** , en el panel de **Project y** haga doble clic en **ObjDetectionScene** para cargar la escena que usará para este curso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **No se incluye ningún código,** se escribirá el código siguiendo este curso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capítulo 5: Creación de la clase CustomVisionAnalyser.

En este momento, está listo para escribir código. Comenzará con la **clase CustomVisionAnalyser.**

> [!NOTE]
> Las llamadas al **servicio Custom Vision ,** realizadas en el código que se muestra a continuación, se realizan mediante la API REST **Custom Vision**. Mediante este uso, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar por su cuenta). Tenga en cuenta que Microsoft ofrece **un SDK Custom Vision que** también se puede usar para realizar llamadas al servicio. Para obtener más información, visite [el artículo Custom Vision SDK de .](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Esta clase es responsable de:

- Carga de la imagen más reciente capturada como una matriz de bytes.

- Enviar la matriz de bytes a la instancia de Azure **Custom Vision Service para** su análisis.

- Recibir la respuesta como una cadena JSON.

- Deserializar la respuesta y pasar la **predicción** resultante a la clase **SceneOrganiser,** que se ocupará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta Asset ,** que se encuentra en el panel Project **y,** a continuación, haga clic **en Crear**  >  **carpeta.** Llame a la carpeta **Scripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Haga doble clic en la carpeta recién creada para abrirla.

3.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic **en Crear**  >  **script \# de C.** Asigne al script **el nombre CustomVisionAnalyser.**

4.  Haga doble clic en el nuevo script **CustomVisionAnalyser** para abrirlo con **Visual Studio.**

5.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  En la **clase CustomVisionAnalyser,** agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Asegúrese de insertar la clave **de predicción de servicio** en la variable **predictionKey** y **prediction-endpoint** en la variable **predictionEndpoint.** Los ha copiado en [Bloc de notas anterior, en el capítulo 2, paso 14.](#chapter-2---training-your-custom-vision-project)

7.  Ahora es necesario agregar código para **Awake()** para inicializar la variable Instance:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Agregue la coroutina (con el método **estático GetImageAsByteArray()** debajo), que obtendrá los resultados del análisis de la imagen, capturados por la **clase ImageCapture.**

    > [!NOTE]
    > En la corrotina **AnalyseImageCapture,** hay una llamada a la clase **SceneOrganiser** que todavía no se ha creado. Por lo **tanto, deje esas líneas comentadas por ahora.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Elimine los **métodos Start()** **y Update(),** ya que no se usarán. 

10.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**

> [!IMPORTANT]
> Como se mencionó anteriormente, no se preocupe por el código que podría parecer tener un error, ya que pronto proporcionará más clases, lo que los corregirá.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capítulo 6: Creación de la clase CustomVisionObjects

La clase que creará ahora es la **clase CustomVisionObjects.**

Este script contiene una serie de objetos utilizados por otras clases para serializar y deserializar las llamadas realizadas al Custom Vision Service.

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta Scripts** y, a continuación, haga clic en **Crear**  >  **script \# de C.** Llame al script **CustomVisionObjects.**

2.  Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Elimine los **métodos Start()** **y Update()** dentro de la **clase CustomVisionObjects;** esta clase debería estar vacía.

    > [!WARNING]
    > Es importante que siga cuidadosamente la siguiente instrucción. Si coloca las nuevas declaraciones de clase dentro de la clase **CustomVisionObjects,** recibirá errores de compilación en el capítulo [10,](#chapter-10---create-the-imagecapture-class)que indican que no se encuentran **AnalysisRootObject** y **BoundingBox.**

5.  Agregue las siguientes clases *fuera de* la **clase CustomVisionObjects.** La biblioteca **Newtonsoft** usa estos objetos para serializar y deserializar los datos de respuesta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capítulo 7: Creación de la clase SpatialMapping

Esta clase establecerá el **colisionador de** asignación espacial en la escena para poder detectar colisiones entre objetos virtuales y objetos reales.

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta Scripts** y, a continuación, haga clic en **Crear**  >  **script \# de C.** Llame al script **SpatialMapping.**

2.  Haga doble clic en el nuevo script **SpatialMapping** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia encima de la **clase SpatialMapping:**

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  A continuación, agregue las siguientes variables dentro de **la clase SpatialMapping,** encima **del método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Agregue **las etiquetas Awake()** **y Start()**:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Elimine el **método Update().**

7.  Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**


## <a name="chapter-8---create-the-gazecursor-class"></a>Capítulo 8: Creación de la clase GazeCursor

Esta clase es responsable de configurar el cursor en la ubicación correcta en el espacio real, mediante el uso de **SpatialMappingCollider**, creado en el capítulo anterior.

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta Scripts** y, a continuación, haga clic en **Crear**  >  **script \# de C.** Llamada al script **GazeCursor**

2.  Haga doble clic en el nuevo script **GazeCursor** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene el siguiente espacio de nombres al que se hace referencia encima de la **clase GazeCursor:**

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue la siguiente variable dentro de la **clase GazeCursor,** encima **del método Start().** 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Actualice el **método Start()** con el código siguiente:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Actualice el **método Update()** con el código siguiente:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > No se preocupe por el error de la **clase SceneOrganiser** que no se encuentra, la creará en el capítulo siguiente.

7. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capítulo 9: Creación de la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Configure la *cámara principal adjuntando* a ella los componentes adecuados.

-   Cuando se detecta un objeto, será responsable de calcular su posición  en el mundo real y colocar una etiqueta de etiqueta cerca de él con el nombre **de etiqueta adecuado.**    

Para crear esta clase:

1.  Haga clic con el botón derecho en **la carpeta Scripts** y, a continuación, haga clic en **Crear**  >  **script \# de C.** Asigne al script el nombre **SceneOrganiser.**

2.  Haga doble clic en el nuevo script **SceneOrganiser** para abrirlo con **Visual Studio.**

3.  Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia encima de la **clase SceneOrganiser:**

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro **de la clase SceneOrganiser,** encima **del método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Elimine los **métodos Start()** **y Update().**

6.  Debajo de las variables, agregue **el método Awake(),** que inicializará la clase y configurará la escena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Agregue el **método PlaceAnalysisLabel(),** que crea una instancia de la etiqueta en la escena (que en este momento es invisible para el usuario).  También coloca el cuadrándular (también invisible) donde se coloca la imagen y se superpone con el mundo real. Esto es importante porque las coordenadas de cuadro recuperadas del servicio después del análisis se trazan de nuevo en este cuadráneo para determinar la ubicación aproximada del objeto en el mundo real. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Agregue el **método FinaliseLabel().** Es el responsable de:

    *   Establecer el *texto etiqueta* con la *etiqueta* de la predicción con la confianza más alta.
    *   Llamar al cálculo del *rectángulo delimitador en* el objeto quad, colocado previamente, y colocar la etiqueta en la escena.
    *   Ajustar la profundidad de la etiqueta mediante un raycast hacia el rectángulo de selección *,* que debe colisionar contra el objeto en el mundo real.
    * Restablecer el proceso de captura para permitir que el usuario capture otra imagen.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Agregue el **método CalculateBoundingBoxPosition(),** que hospeda una serie de cálculos necesarios para traducir las coordenadas *del* cuadro de límite recuperadas del servicio y volver a crearlas proporcionalmente en el cuadránto.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**

    > [!IMPORTANT]
    > Antes de continuar, abra la **clase CustomVisionAnalyser** y, dentro del método **AnalyseLastImageCaptured(),** descomprima las líneas siguientes: 
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> No se preocupe por el mensaje de la clase **ImageCapture** "no se encontró", lo creará en el capítulo siguiente.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capítulo 10: Creación de la clase ImageCapture

La siguiente clase que va a crear es la **clase ImageCapture.**

Esta clase es responsable de:

*   Capturar una imagen mediante la HoloLens cámara y almacenarla en la *carpeta Aplicación.*
*   Control *de los* gestos de pulsación del usuario.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts** que creó anteriormente.

2.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic **en Crear**  >  **script \# de C.** Asigne al script el nombre **ImageCapture.**

3.  Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio.**

4.  Reemplace los espacios de nombres de la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro **de la clase ImageCapture,** encima **del método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  Ahora es necesario agregar código para los métodos **Awake()** y **Start():**

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implemente un controlador al que se llamará cuando se produzca un gesto de pulsar:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Cuando el cursor es **verde,** significa que la cámara está disponible para tomar la imagen. Cuando el cursor está **rojo,** significa que la cámara está ocupada.

8.  Agregue el método que la aplicación usa para iniciar el proceso de captura de imágenes y almacenar la imagen:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté lista para analizarse. A continuación, el resultado se pasa a **CustomVisionAnalyser para** su análisis.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity.**

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capítulo 11: Configuración de los scripts en la escena

Ahora que ha escrito todo el código necesario para este proyecto, es el momento de configurar los scripts en la escena y en los elementos prefabs para que se comporten correctamente.

1.  En el **Editor de Unity,** en el **Panel de** jerarquía, seleccione la cámara **principal**.
2.  En el panel **inspector**, con la cámara principal seleccionada, haga clic en Agregar componente y, a continuación, busque SceneOrganiser script (Script de **SceneOrganiser)** y haga doble clic en él para agregarlo. 

    ![](images/AzureLabs-Lab310-38.png)

3.  En el **panel Project**, abra la carpeta **Prefabs**, arrastre el objeto Prefab **Label** al área de entrada Label *empty* reference target (Etiqueta de destino de referencia vacía), en el script **SceneOrganiser** que acaba de agregar a la cámara *principal,* como se muestra en la imagen siguiente:

    ![](images/AzureLabs-Lab310-39.png)

4.  En el **Panel de jerarquía,** seleccione el **elemento secundario GazeCursor** de la **cámara principal**.
5.  En el panel **inspector**, con **gazecursor** seleccionado, haga clic en Agregar componente y, a continuación, busque el script **GazeCursor** y haga doble clic en él para agregarlo. 

    ![](images/AzureLabs-Lab310-40.png)

6.  De nuevo, en el **Panel de jerarquía,** seleccione el elemento **secundario SpatialMapping** de la **cámara principal**.
7.  En el Panel **inspector**, con **spatialMapping** seleccionado, haga clic en Agregar componente y, a continuación, busque el script  **SpatialMapping** y haga doble clic en él para agregarlo.

    ![](images/AzureLabs-Lab310-41.png)

El código agregará los scripts restantes que no haya establecido en el script **SceneOrganiser,** durante el tiempo de ejecución.

## <a name="chapter-12---before-building"></a>Capítulo 12: Antes de compilar

Para realizar una prueba exhaustiva de la aplicación, deberá cargarla localmente en el Microsoft HoloLens.

Antes de hacerlo, asegúrese de que:

-  Todas las configuraciones mencionadas en [el capítulo 3](#chapter-3---set-up-the-unity-project) se establecen correctamente.
- El script **SceneOrganiser** está asociado al **objeto Main Camera.**
- El script **GazeCursor** está asociado al **objeto GazeCursor.**
- El script **SpatialMapping** está asociado al **objeto SpatialMapping.**
- En [el capítulo 5,](#chapter-5---create-the-customvisionanalyser-class)paso 6:

    - Asegúrese de insertar la clave **de predicción de servicio** en la variable **predictionKey.**
    - Ha insertado el punto **de conexión de predicción** en la clase **predictionEndpoint.**

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capítulo 13: Compilación de la solución para UWP y instalación local de la aplicación

Ya está listo para compilar la aplicación como una solución para UWP que podrá implementar en el Microsoft HoloLens. Para comenzar el proceso de compilación:

1.  Vaya a **File > Build Configuración**.

2.  Marque **proyectos de C \# de Unity.**

3.  Haga clic en **Agregar escenas abiertas.** Esto agregará la escena abierta actualmente a la compilación.

    ![](images/AzureLabs-Lab310-42.png)

4.  Haga clic en **Generar**. Unity iniciará una *Explorador de archivos,* donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así mismo den el nombre **App**. A continuación, con **la carpeta** Aplicación seleccionada, haga clic **en Seleccionar carpeta.**

5.  Unity comenzará a compilar el proyecto en la **carpeta Aplicación.**

6.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de **Explorador de archivos** en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

7.  Para realizar la implementación en Microsoft HoloLens, necesitará la dirección IP de ese dispositivo (para la implementación remota) y para asegurarse de que también tiene establecido el **modo de** desarrollador. Para ello, siga estos pasos:

    1.  Mientras lleva el HoloLens, abra **el Configuración**.

    2.  Vaya a **Network & Internet** Wi-Fi Advanced Options (Opciones avanzadas de  >  **Wi-Fi de** Red &  >  **Internet)**

    3.  Anote **la dirección IPv4.**

    4.  A continuación, vuelva **a Configuración** y, a continuación, a Update & Security for Developers (Actualizar & **seguridad**  >  **para desarrolladores).**

    5.  Establezca **el modo de desarrollador** *en*.

8.  Vaya a la nueva compilación de Unity (la **carpeta Aplicación)** y abra el archivo de solución **con Visual Studio**.

9.  En Configuración de la solución, **seleccione Depurar**.

10. En la Plataforma de soluciones, **seleccione x86, Equipo remoto.** Se le pedirá que inserte la dirección **IP** de un dispositivo remoto (el Microsoft HoloLens, en este caso, que anotó).

    ![](images/AzureLabs-Lab310-43.png)

11. Vaya al menú **Compilar y** haga clic en **Implementar solución** para realizar la instalación local de la aplicación en el HoloLens.

12. La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el Microsoft HoloLens, listo para iniciarse.

### <a name="to-use-the-application"></a>Para usar la aplicación:

* Mire un objeto que ha entrenado con azure **Custom Vision Service,** detección de objetos y use el **gesto de pulsar**.
* Si el objeto se detecta correctamente, aparecerá un texto de etiqueta de espacio mundial con el nombre de etiqueta. 

> [!IMPORTANT]
> Cada vez que capture una foto y la envíe al servicio, puede volver a la página Servicio y volver a entrenar el servicio con las imágenes recién capturadas. Al principio, probablemente también tendrá que corregir los rectángulos *delimitadores* para ser más precisos y volver a entrenar el servicio.

> [!NOTE]
> Es posible que el texto de etiqueta colocado no aparezca cerca del objeto cuando los sensores de Microsoft HoloLens o SpatialTrackingComponent en Unity no puedan colocar los colisionantes adecuados, en relación con los objetos reales. Intente usar la aplicación en una superficie diferente si ese es el caso.

## <a name="your-custom-vision-object-detection-application"></a>Aplicación Custom Vision, detección de objetos

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha La API de detección de objetos de Azure Custom Vision, que puede reconocer un objeto de una imagen y, a continuación, proporcionar una posición aproximada para ese objeto en el espacio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Al agregar a la etiqueta de texto, use un cubo semitransparente para encapsular el objeto real en un cuadro de *límite 3D*.

### <a name="exercise-2"></a>Ejercicio 2

Entrena a Custom Vision Service para reconocer más objetos.

### <a name="exercise-3"></a>Ejercicio 3

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-4"></a>Ejercicio 4

Use la API para volver a entrenar el servicio con las mismas imágenes que está analizando la aplicación, de modo que el servicio sea más preciso (realice la predicción y el entrenamiento simultáneamente).
