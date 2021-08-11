---
title: 'HoloLens de primera generación y Azure (302b): visión personalizada'
description: Complete este curso para aprender a entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, custom vision, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 25f07dddf53cf8c279f99d230d1bd4d206a663eba884abc0dd32313bce4b7b43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217744"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a>HoloLens (1.ª generación) y Azure 302b: Custom Vision

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>


En este curso, aprenderá a reconocer contenido visual personalizado dentro de una imagen proporcionada, mediante las funcionalidades de Azure Custom Vision en una aplicación de realidad mixta.

Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objetos. A continuación, usará el modelo entrenado para reconocer objetos similares, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectada al equipo para cascos envolventes (VR).

![resultado del curso](images/AzureLabs-Lab302b-00.png)

Azure Custom Vision es un servicio de Microsoft Cognitive Service que permite a los desarrolladores crear clasificadores de imágenes personalizados. Estos clasificadores se pueden usar con nuevas imágenes para reconocer o clasificar objetos dentro de esa nueva imagen. El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar el proceso. Para más información, visite la página [azure Custom Vision Service](/azure/cognitive-services/custom-vision-service/home).

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá funcionar en dos modos:

-   **Modo de análisis:** configurar el servicio Custom Vision manualmente mediante la carga de imágenes, la creación de etiquetas y el entrenamiento del servicio para reconocer diferentes objetos (en este caso, el mouse y el teclado). A continuación, creará HoloLens aplicación que capturará imágenes con la cámara e intentará reconocer esos objetos en el mundo real.

-   **Modo de** entrenamiento: implementará código que habilitará un "modo de entrenamiento" en la aplicación. El modo de entrenamiento le permitirá capturar imágenes mediante la cámara de HoloLens, cargar las imágenes capturadas en el servicio y entrenar el modelo de custom vision.

Este curso le enseñará a obtener los resultados de Custom Vision Service en una aplicación de ejemplo basada en Unity. Será su función aplicar estos conceptos a una aplicación personalizada que pueda estar creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (302b): Custom Vision</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
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
- Una cámara conectada al equipo (para el desarrollo de cascos envolventes)
- Acceso a Internet para la instalación y la recuperación Custom Vision API de Azure
- Una serie de al menos cinco (5) imágenes (diez (10) recomendadas) para cada objeto que le gustaría que el servicio Custom Vision reconocera. Si lo desea, puede usar [las imágenes ya proporcionadas con este curso (un mouse de equipo y un teclado). ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)

## <a name="before-you-start"></a>Antes de comenzar

1.  Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
2.  Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo HoloLens [instalación de](/hololens/hololens-setup). 
3.  Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario). 

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración](/hololens/hololens-calibration#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capítulo 1: El portal Custom Vision Service Portal

Para usar *el Custom Vision en* Azure, deberá configurar una instancia del servicio para que esté disponible para la aplicación.

1.  En primer [lugar, vaya a *la Custom Vision principal del* servicio](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Haga clic en **el Introducción** de texto.

    ![Introducción a Custom Vision Service](images/AzureLabs-Lab302b-01.png)

3.  Inicie sesión en Custom Vision *Service* Portal.

    ![Inicio de sesión en el portal](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

4.  Una vez que haya iniciado sesión por primera vez, se le pedirá el panel *Términos de* servicio. Haga clic en la casilla para aceptar los términos. A continuación, haga **clic en Acepto**.

    ![Los términos del servicio](images/AzureLabs-Lab302b-03.png)

5.  Una vez que haya aceptado los términos, se le desplazará a la sección *Proyectos* del portal. Haga clic **en Nuevo Project**.

    ![Creación de un proyecto](images/AzureLabs-Lab302b-04.png)

6.  Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.

    1.  Inserte un *nombre* para el proyecto.

    2.  Inserte una *descripción* para el proyecto *(opcional).*

    3.  Elija un *grupo de recursos* o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

    4. Establecer los *tipos Project en* **Clasificación**
    
    5. Establezca los *dominios como* **General.**

        ![Establecer los dominios](images/AzureLabs-Lab302b-05.png)

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

7.  Cuando haya terminado, haga clic en **Crear proyecto** y se le redirigirá a la página Custom Vision service, project.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capítulo 2: Entrenamiento del proyecto de Custom Vision

Una vez en Custom Vision portal, el objetivo principal es entrenar el proyecto para reconocer objetos específicos en las imágenes. Necesita al menos cinco (5) imágenes, aunque se prefieren diez (10) para cada objeto que quiera que reconozca la aplicación. [Puede usar las imágenes proporcionadas con este curso (un mouse de equipo y un teclado).](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip) 

Para entrenar el proyecto Custom Vision Service:

1.  Haga clic en **+** el botón situado junto a **Etiquetas.**

    ![Agregar nueva etiqueta](images/AzureLabs-Lab302b-06.png)

2.  Agregue el **nombre** del objeto que desea reconocer. Haga clic en **Guardar**.

    ![Agregar nombre de objeto y guardar](images/AzureLabs-Lab302b-07.png)

3.  Observará que **se ha** agregado la etiqueta (es posible que tenga que volver a cargar la página para que aparezca). Haga clic en la casilla junto a la nueva etiqueta, si aún no está activada.

    ![Habilitación de una nueva etiqueta](images/AzureLabs-Lab302b-08.png)

4.  Haga clic **en Agregar imágenes** en el centro de la página.

    ![Adición de imágenes](images/AzureLabs-Lab302b-09.png)

5.  Haga clic **en Examinar archivos locales** y busque y, a continuación, seleccione las imágenes que desea cargar, siendo el mínimo cinco (5). Recuerde que todas estas imágenes deben contener el objeto que está entrenando.

    > [!NOTE]
    >  Puede seleccionar varias imágenes a la vez para cargarlas.

6.  Una vez que pueda ver las imágenes en la pestaña, seleccione la etiqueta adecuada en el **cuadro Mis etiquetas.**

    ![Seleccionar etiquetas](images/AzureLabs-Lab302b-10.png)

7.  Haga clic en **Upload archivos**. Los archivos comenzarán a cargarse. Una vez que haya confirmado la carga, haga clic **en Listo.**

    ![Carga de archivos](images/AzureLabs-Lab302b-11.png)

8.  Repita el mismo proceso para crear una nueva **etiqueta** denominada **Keyboard** y cargue las fotos adecuadas para ella. Asegúrese de desactivar **mouse** *una* vez que haya creado las nuevas etiquetas, para mostrar la *ventana Agregar* imágenes.

9.  Una vez configuradas ambas etiquetas, haga clic en **Entrenar** y se iniciará la primera iteración de entrenamiento.

    ![Habilitación de la iteración de entrenamiento](images/AzureLabs-Lab302b-12.png)

10. Una vez creado, podrá ver dos botones denominados **Make default** (Hacer predeterminado) y Prediction **URL (Dirección URL de predicción).** En primer lugar, haga clic **en Convertir** en predeterminado y, a continuación, haga clic en Url **de predicción.**

    ![Crear la dirección URL predeterminada y de predicción](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > La dirección URL del punto de conexión  que se proporciona a partir de este se establece en la iteración que se haya marcado como predeterminada. Por lo tanto, si más adelante realiza una *nueva* iteración y la actualiza de forma predeterminada, no tendrá que cambiar el código.

11. Una vez que haya hecho clic en Url de *predicción,* abra *Bloc de notas* y copie y pegue la dirección **URL** y la clave **de** predicción para que pueda recuperarla cuando la necesite más adelante en el código.

    ![Copie y pegue la dirección URL y Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. Haga clic en **el engranaje** en la parte superior derecha de la pantalla.

    ![Haga clic en el icono de engranaje para abrir la configuración.](images/AzureLabs-Lab302b-15.png)

13. Copie la **clave de entrenamiento** y péguela en un *Bloc de notas*, para su uso posterior.

    ![Copia de la clave de entrenamiento](images/AzureLabs-Lab302b-16.png)

14. Copie también el **identificador Project y** péguelo también en el *Bloc de notas,* para su uso posterior.

    ![Copia del identificador del proyecto](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capítulo 3: Configuración del proyecto de Unity

A continuación se muestra una configuración típica para desarrollar con realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra *Unity y* haga clic en **Nuevo.**

    ![Crear un proyecto de Unity](images/AzureLabs-Lab302b-17.png)

2.  Ahora deberá proporcionar un nombre de proyecto de Unity. Inserte **AzureCustomVision.** Asegúrese de que la plantilla de proyecto está establecida en **3D.** Establezca la **ubicación en** un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![Configuración de las opciones del proyecto](images/AzureLabs-Lab302b-18.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar*  >  *preferencias** y, a continuación, en la nueva ventana, vaya **a Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Configuración de herramientas externas](images/AzureLabs-Lab302b-19.png)

4.  A continuación, vaya a **File > Build Configuración y** seleccione Universal Windows Platform (Plataforma **Windows** universal) y haga clic en el botón **Switch Platform** (Cambiar plataforma) para aplicar la selección.

    ![Configurar los valores de compilación ](images/AzureLabs-Lab302b-20.png)

5.  Mientras sigue en **File > Build Configuración** y asegúrese de que:

    1.  **El dispositivo de** destino se **establece en HoloLens**

        > Para los cascos envolventes, establezca **Dispositivo de destino** en Cualquier *dispositivo.*
        
    2.  **Tipo de** compilación se establece en **D3D**
    3.  **El SDK** se establece en **Instalado más reciente**
    4.  **Visual Studio versión está** establecida en **La versión más reciente instalada**
    5.  **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**
    6.  Guarde la escena y agrégréla a la compilación. 

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![Agregar una escena abierta a la lista de compilación](images/AzureLabs-Lab302b-21.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Creación de una carpeta de escena](images/AzureLabs-Lab302b-22.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo Nombre de *archivo:* texto, escriba **CustomVisionScene** y, a continuación, haga clic **en Guardar.**

            ![Nombre del nuevo archivo de escena](images/AzureLabs-Lab302b-23.png)

            > Tenga en cuenta que debe guardar las escenas de Unity en la *carpeta Recursos,* ya que deben estar asociadas con el proyecto de Unity. La creación de la carpeta scenes (y otras carpetas similares) es una manera típica de estructurar un proyecto de Unity.
            
    7.  El resto de la configuración, *en Build Configuración*, se debe dejar como valor predeterminado por ahora.

        ![Configuración de compilación predeterminada](images/AzureLabs-Lab302b-24.png)

6.  En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.*

7. En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión del entorno de** ejecución de scripting debe ser Experimental (equivalente a **.NET 4.6),** lo que desencadenará la necesidad de reiniciar el editor.

        2. **El back-end de** scripting debe ser **.NET**

        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

        ![Establecer la compantiblidad de la API](images/AzureLabs-Lab302b-25.png)

    2.  En la **pestaña Configuración,** en **Funcionalidades**, compruebe:

        1. **InternetClient**

        2.  **Cámara web**

        3. **Micrófono**

        ![Configurar los valores de publicación](images/AzureLabs-Lab302b-26.png)

    3.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración**), marque **Virtual Reality Supported (Compatible con Virtual Reality)** y asegúrese de que se agrega el **SDK** Windows Mixed Reality virtual.

    ![Configuración de XR](images/AzureLabs-Lab302b-27.png)

8.  De nuevo en *Build Configuración* Unity C Projects (Proyectos de *C \# de Unity)* ya no está en gris; marque la casilla situada junto a este.

9.  Cierre la ventana Build Settings (Configuración de compilación).

10.  Guarde la escena y el proyecto **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capítulo 4: Importación del archivo DLL de Newtonsoft en Unity

> [!IMPORTANT]
> Si desea omitir el componente De configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar este paquete [Azure-MR-302b.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)impórtelo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continúe desde el [capítulo 6.](#chapter-6---create-the-customvisionanalyser-class)

Este curso requiere el uso de la **biblioteca Newtonsoft,** que puede agregar como un archivo DLL a los recursos. El paquete que contiene [esta biblioteca se puede descargar desde este vínculo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).
Para importar la biblioteca Newtonsoft en el proyecto, use el paquete de Unity que se incluye en este curso.

1.  Agregue el *paquete .unitypackage* a Unity mediante la opción de menú **Importar*  >   *paquete*  >   *personalizado de** recursos.

2.  En el **cuadro Importar paquete de Unity** que aparece, asegúrese de que todo lo que se encuentra en (e incluye) **Complementos** está seleccionado.

    ![Importar todos los elementos de paquete](images/AzureLabs-Lab302b-28.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta Newtonsoft** en **Complementos** en la vista del proyecto y seleccione el *Newtonsoft.Jscomplemento*.

    ![Selección del complemento Newtonsoft](images/AzureLabs-Lab302b-29.png)

5.  Con el *Newtonsoft.Js* en el complemento  seleccionado, asegúrese de que cualquier plataforma esté desactivada y, a continuación, asegúrese de que **WSAPlayer** también está desactivado **y,** a continuación, haga clic **en Aplicar**. Esto es solo para confirmar que los archivos están configurados correctamente.

    ![Configuración del complemento Newtonsoft](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Marcar estos complementos los configura para que solo se utilicen en el Editor de Unity. Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.

6.  A continuación, debe abrir la **carpeta WSA,** dentro de la **carpeta Newtonsoft.** Verá una copia del mismo archivo que acaba de configurar. Seleccione el archivo y, a continuación, en el inspector, asegúrese de que
    -   **Cualquier plataforma** está **desactivada** 
    -   **solo** **WSAPlayer** está **activado**
    -   **No se comprueba el** **proceso**

    ![Configuración de la plataforma del complemento Newtonsoft](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capítulo 5: Configuración de la cámara

1.  En el Panel de jerarquía, seleccione la *cámara principal*.

2.  Una vez seleccionada, podrá ver todos los componentes de *la* cámara principal en el *panel inspector*.

    1.  El *objeto de* cámara debe denominarse Cámara **principal** (tenga en cuenta la ortografía).

    2.  La etiqueta de **cámara** principal debe establecerse **en MainCamera** (tenga en cuenta la ortografía).

    3.  Asegúrese de que **la posición de** transformación está establecida en **0, 0, 0**

    4.  Establezca **Clear Flags (Borrar marcas)** **en Color sólido** (o no lo haga para los cascos envolventes).

    5.  Establezca el **color de** fondo del componente de la cámara en **Negro, Alfa 0 (código hexadecimal: #00000000)** (omitir esto para los cascos envolventes).

    ![Configuración de propiedades de componentes de cámara](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capítulo 6: Creación de la clase CustomVisionAnalyser.

En este momento, está listo para escribir código.

Comenzará con la *clase CustomVisionAnalyser.*

> [!NOTE]
> Las llamadas a Custom Vision **Service realizadas** en el código que se muestra a continuación se realizan mediante Custom Vision **API REST**. Mediante este uso, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar por su cuenta). Tenga en cuenta que Microsoft ofrece un **SDK Custom Vision Service que** también se puede usar para realizar llamadas al servicio. Para más información, consulte el [artículo Custom Vision SDK de servicio.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Esta clase es responsable de:

-   Carga de la imagen más reciente capturada como una matriz de bytes.

-   Enviar la matriz de bytes a la instancia de Azure *Custom Vision Service para* su análisis.

-   Recibir la respuesta como una cadena JSON.

-   Deserializar la respuesta y pasar la *predicción* resultante a la clase *SceneOrganiser,* que se ocupará de cómo se debe mostrar la respuesta.

Para crear esta clase:

1.  Haga clic con el botón derecho en *la carpeta de recursos* que se encuentra en el panel Project *y,* a continuación, haga clic **en Crear > carpeta**. Llame a la carpeta **Scripts**.

    ![Crear carpeta de scripts](images/AzureLabs-Lab302b-33.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en la carpeta y, a continuación, **haga clic en Crear** script  >  **\# de C.** Asigne al script *el nombre CustomVisionAnalyser.*

4.  Haga doble clic en el nuevo script *CustomVisionAnalyser* para abrirlo con **Visual Studio**.

5.  Actualice los espacios de nombres en la parte superior del archivo para que coincidan con lo siguiente:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  En la *clase CustomVisionAnalyser,* agregue las siguientes variables:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Asegúrese de insertar la clave **de predicción en** la variable **predictionKey** y el punto de conexión **de** predicción en la variable **predictionEndpoint.** Los ha copiado para *Bloc de notas* anteriormente en el curso.

7.  Ahora es necesario agregar código para **Awake()** para inicializar la variable Instance:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Elimine los **métodos Start()** **y Update().**

9.  A continuación, agregue la corrotina (con el método **estático GetImageAsByteArray()** debajo), que obtendrá los resultados del análisis de la imagen capturada por la *clase ImageCapture.*

    > [!NOTE]
    > En la **corrotina AnalyseImageCapture,** hay una llamada a la clase *SceneOrganiser* que aún no se ha creado. Por lo **tanto, deje esas líneas comentadas por ahora.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity.**

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capítulo 7: Creación de la clase CustomVisionObjects

La clase que creará ahora es la *clase CustomVisionObjects.*

Este script contiene una serie de objetos usados por otras clases para serializar y deserializar las llamadas realizadas al *Custom Vision Service*.

> [!WARNING]
> Es importante que tome nota del punto de conexión que proporciona el servicio Custom Vision, ya que la siguiente estructura JSON se ha configurado para funcionar con [*Custom Vision Prediction v2.0.*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290) Si tiene una versión diferente, es posible que tenga que actualizar la estructura siguiente.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta Scripts** y, a continuación, haga clic **en Crear**  >  **\# script de C.** Llame al script *CustomVisionObjects.*

2.  Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres a la parte superior del archivo:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Elimine los **métodos Start()** **y Update()** dentro de *la clase CustomVisionObjects;* Esta clase debería estar ahora vacía.

5.  Agregue las siguientes clases **fuera de** la *clase CustomVisionObjects.* La biblioteca *Newtonsoft* usa estos objetos para serializar y deserializar los datos de respuesta:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capítulo 8: Creación de la clase VoiceRecognizer

Esta clase reconocerá la entrada de voz del usuario.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta Scripts** y, a continuación, haga clic **en Crear**  >  **\# script de C.** Llame al script *VoiceRecognizer.*

2.  Haga doble clic en el nuevo script **VoiceRecognizer** para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres encima de *la clase VoiceRecognizer:*

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  A continuación, agregue las siguientes variables dentro *de la clase VoiceRecognizer,* encima *del método Start():*

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Agregue los *métodos* **Awake()** y **Start(),** el último de los cuales configurará las palabras clave de usuario que se reconocerán al asociar una etiqueta a una imagen:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Elimine el **método Update().**

7.  Agregue el siguiente controlador, al que se llama cada vez que se reconoce la entrada de voz:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity.**

> [!NOTE]
> No se preocupe por el código que podría parecer tener un error, ya que proporcionará más clases pronto, lo que los corregirá.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capítulo 9: Creación de la clase CustomVisionTrainer

Esta clase encadenará una serie de llamadas web para entrenar el *Custom Vision Service*. Cada llamada se explicará con detalle justo encima del código.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta Scripts** y, a continuación, haga clic **en Crear**  >  **\# script de C.** Llame al script *CustomVisionTrainer.*

2.  Haga doble clic en el nuevo script *CustomVisionTrainer* para abrirlo con **Visual Studio**.

3.  Agregue los siguientes espacios de nombres encima de *la clase CustomVisionTrainer:*

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  A continuación, agregue las siguientes variables dentro *de la clase CustomVisionTrainer,* encima **del método Start().** 

    > [!NOTE]
    > La dirección URL de entrenamiento que se usa aquí se proporciona en *la documentación Custom Vision Training 1.2* y tiene una estructura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Para más información, visite la API [*de referencia Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > Es importante que tome nota del punto de conexión que el servicio Custom Vision proporciona para el modo de entrenamiento, ya que la estructura JSON usada (dentro de la clase **CustomVisionObjects)** se ha configurado para funcionar con [*Custom Vision Training v1.2.*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f) Si tiene una versión diferente, es posible que tenga que actualizar la *estructura Objetos* .

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Asegúrese de agregar el valor de **clave de servicio** (clave de entrenamiento) y el Project **identificador,** que anotó anteriormente. estos son los valores que recopiló en el portal anteriormente en el [curso (capítulo 2, paso 10 en adelante).](#chapter-2---training-your-custom-vision-project)

5.  Agregue los métodos **Start()** y **Awake()** siguientes. Estos métodos se llaman al inicializar y contienen la llamada para configurar la interfaz de usuario:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Elimine el **método Update().** Esta clase no la necesitará.

7.  Agregue el **método RequestTagSelection().** Este método es el primero en llamarse cuando se ha capturado y almacenado una imagen en el dispositivo y ahora está listo para enviarse al servicio *Custom Vision ,* para entrenarla. Este método muestra, en la interfaz de usuario de entrenamiento, un conjunto de palabras clave que el usuario puede usar para etiquetar la imagen capturada. También alerta a la *clase VoiceRecognizer* para que empiece a escuchar al usuario para la entrada de voz.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Agregue el **método VerifyTag().** Este método recibirá la entrada de voz reconocida por la clase **VoiceRecognizer** y comprobará su validez y, a continuación, iniciará el proceso de entrenamiento.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Agregue el **método SubmitImageForTraining().** Este método iniciará el proceso de entrenamiento Custom Vision Service. El primer paso es recuperar el identificador **de** etiqueta del servicio que está asociado a la entrada de voz validada del usuario. A **continuación,** se cargará el identificador de etiqueta junto con la imagen.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Agregue el **método TrainCustomVisionProject().** Una vez enviada y etiquetada la imagen, se llamará a este método. Creará una nueva iteración que se entrenará con todas las imágenes anteriores enviadas al servicio más la imagen que acaba de cargar. Una vez completado el entrenamiento, este método llamará  a un método para establecer la iteración recién creada como **Predeterminada,** de modo que el punto de conexión que se usa para el análisis sea la iteración entrenada más reciente.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Agregue el **método SetDefaultIteration().** Este método establecerá la iteración previamente creada y entrenada como *Predeterminada.* Una vez completado, este método tendrá que eliminar la iteración anterior existente en el servicio. En el momento de escribir este curso, hay un límite de diez (10) iteraciones máximas permitidas que pueden existir al mismo tiempo en el servicio.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Agregue el **método DeletePreviousIteration().** Este método buscará y eliminará la iteración no predeterminada anterior:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. El último método que se agrega en esta clase es **el método GetImageAsByteArray(),** que se usa en las llamadas web para convertir la imagen capturada en una matriz de bytes.

    ```csharp
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

14. Asegúrese de guardar los cambios **en** Visual Studio antes de volver a **Unity.**

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capítulo 10: Creación de la clase SceneOrganiser

Esta clase hará lo siguiente:

-   Cree un **objeto Cursor** para adjuntarlo a la cámara principal.

-   Cree un **objeto Label** que aparecerá cuando el servicio reconozca los objetos del mundo real.

-   Configure la cámara principal adjuntando los componentes adecuados a ella.

-   Cuando se **encuentra en modo de** análisis, genera las etiquetas en tiempo de ejecución, en el espacio del mundo adecuado en relación con la posición de la cámara principal, y muestra los datos recibidos del servicio Custom Vision.

-   Cuando se encuentra **en modo de** entrenamiento, genera la interfaz de usuario que mostrará las distintas fases del proceso de entrenamiento.

Para crear esta clase:

1.  Haga clic con el botón derecho en la **carpeta Scripts** y, a continuación, haga clic **en Crear**  >  **\# script de C.** Asigne al script el nombre *SceneOrganiser.*

2.  Haga doble clic en el nuevo script *SceneOrganiser* para abrirlo con **Visual Studio**.

3.  Solo necesitará un espacio de nombres, quite los demás de encima de la *clase SceneOrganiser:*

    ```csharp
    using UnityEngine;
    ```

4.  A continuación, agregue las siguientes variables dentro *de la clase SceneOrganiser,* encima **del método Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Elimine los **métodos Start()** **y Update().**

6.  Justo debajo de las variables, agregue **el método Awake(),** que inicializará la clase y configurará la escena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Ahora agregue el **método CreateCameraCursor()** que crea y coloca el cursor de la cámara principal, y el método **CreateLabel(),** que crea el objeto **Analysis Label.**

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Agregue el **método SetCameraStatus(),** que controlará los mensajes destinados a la malla de texto que proporciona el estado de la cámara.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Agregue los **métodos PlaceAnalysisLabel()** y **SetTagsToLastLabel(),** que generarán y mostrarán los datos del servicio Custom Vision en la escena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Por último, agregue el **método CreateTrainingUI(),** que genera la interfaz de usuario que muestra las varias fases del proceso de entrenamiento cuando la aplicación está en modo de entrenamiento. Este método también se aprovechará para crear el objeto de estado de la cámara.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Asegúrese de guardar los cambios **en** Visual Studio antes de volver a **Unity.**

> [!IMPORTANT]
> Antes de continuar, abra **la clase CustomVisionAnalyser** y, dentro del método **AnalyseLastImageCaptured(),** descomprima las líneas siguientes: 
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capítulo 11: Creación de la clase ImageCapture

La siguiente clase que va a crear es la *clase ImageCapture.*

Esta clase es responsable de:

-   Captura de una imagen mediante la HoloLens cámara y su almacenamiento en la *carpeta de* la aplicación.

-   Control de los gestos de pulsación del usuario.

-   Mantener el *valor enum* que determina si la aplicación se ejecutará en modo *de* análisis o *modo de* entrenamiento.

Para crear esta clase:

1.  Vaya a la **carpeta Scripts** que creó anteriormente.

2.  Haga clic con el botón derecho en la carpeta y, a continuación, haga clic **> script de C. \#** Asigne al script el nombre *ImageCapture.*

3.  Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio**.

4.  Reemplace los espacios de nombres de la parte superior del archivo por lo siguiente:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  A continuación, agregue las siguientes variables dentro *de la clase ImageCapture,* encima **del método Start():**

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implemente un controlador al que se llamará cuando se produzca un gesto de pulsar.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > En *el modo* de análisis, el método **TapHandler** actúa como un modificador para iniciar o detener el bucle de captura de fotos.
    >
    > En *el modo* de entrenamiento, capturará una imagen de la cámara.
    >
    > Cuando el cursor está verde, significa que la cámara está disponible para tomar la imagen.
    >
    > Cuando el cursor está rojo, significa que la cámara está ocupada.

8.  Agregue el método que la aplicación usa para iniciar el proceso de captura de imágenes y almacenar la imagen.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté lista para analizarse. A continuación, el resultado se pasa a *CustomVisionAnalyser* o *CustomVisionTrainer* en función del modo en el que se establezca el código.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Asegúrese de guardar los cambios **en** Visual Studio antes de volver a **Unity.**

11. Ahora que se han completado todos los scripts, vuelva al Editor de Unity y, a continuación, haga clic y arrastre la clase **SceneOrganiser** desde la carpeta **Scripts** hasta el objeto **Cámara** principal del Panel de *jerarquía.*

## <a name="chapter-12---before-building"></a>Capítulo 12: Antes de compilar

Para realizar una prueba exhaustiva de la aplicación, deberá realizar una instalación local en la HoloLens.

Antes de hacerlo, asegúrese de que:

- Todas las configuraciones mencionadas en [el capítulo 2](#chapter-2---training-your-custom-vision-project) se establecen correctamente.

- Todos los campos de la **cámara principal,** el panel inspector, se asignan correctamente.

- El script **SceneOrganiser** está asociado al **objeto Main Camera.**

- Asegúrese de insertar la clave **de predicción en** la variable **predictionKey.**

- Ha insertado el punto **de conexión de predicción** en la variable **predictionEndpoint.**

- Ha insertado la clave **de entrenamiento** en la variable **trainingKey** de la *clase CustomVisionTrainer.*

- Ha insertado el identificador **Project en** la variable **projectId** de la *clase CustomVisionTrainer.*

## <a name="chapter-13---build-and-sideload-your-application"></a>Capítulo 13: Compilación y instalación local de la aplicación

Para comenzar el *proceso de compilación:*

1.  Vaya a **File > Build Configuración**.

2.  Marque **proyectos de C \# de Unity.**

3.  Haga clic en **Generar**. Unity iniciará una **Explorador de archivos,** donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así mismo den el nombre **App**. A continuación, con **la carpeta** Aplicación seleccionada, haga clic **en Seleccionar carpeta.**

4.  Unity comenzará a compilar el proyecto en la **carpeta Aplicación.**

5.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de **Explorador de archivos** en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

Para implementar en HoloLens:

1.  Necesitará la dirección IP de su HoloLens (para Implementación remota) y para asegurarse de que el HoloLens está en **modo de desarrollador**. Para ello:

    1.  Al mismo tiempo que HoloLens, abra **el Configuración**.

    2.  Vaya a **Network & Internet** Wi-Fi Advanced Options (Opciones avanzadas de  >  **Wi-Fi de** Red &  >  **Internet)**

    3.  Anote **la dirección IPv4.**

    4.  A continuación, vuelva **a Configuración** y, a continuación, a Update & Security for Developers (Actualizar & **seguridad**  >  **para desarrolladores).**

    5.  Establezca **el modo de desarrollador en**.

2.  Vaya a la nueva compilación de Unity (la **carpeta Aplicación)** y abra el archivo de solución **con Visual Studio**.

3.  En Configuración *de la solución,* **seleccione Depurar**.

4.  En la *Plataforma de soluciones,* **seleccione x86, Equipo remoto.** Se le pedirá que inserte la dirección **IP** de un dispositivo remoto (el HoloLens, en este caso, que anotó).

    ![Establecer dirección IP](images/AzureLabs-Lab302b-34.png)

5. Vaya al **menú Compilar** y haga clic **en Implementar** solución para realizar la instalación local de la aplicación en HoloLens.

6. La aplicación debería aparecer ahora en la lista de aplicaciones instaladas en el HoloLens, listo para iniciarse.

> [!NOTE]
> Para realizar la implementación  en casco envolvente, establezca  plataforma de solución en *Máquina local* y establezca la configuración en *Depurar*, con *x86* como **plataforma**. A continuación, implemente en la máquina local, mediante el **elemento de** menú Compilar y seleccione *Implementar solución.* 

## <a name="to-use-the-application"></a>Para usar la aplicación:

Para cambiar la  funcionalidad de  la aplicación entre el modo de entrenamiento y el modo de predicción, debe actualizar la variable **AppMode,** que se encuentra en el método **Awake()** ubicado dentro de la *clase ImageCapture.*

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
o
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

En *modo de* entrenamiento:

- Mire el **mouse o** **el teclado** y use el gesto **de pulsar**.

- A continuación, aparecerá texto en el que se le pedirá que proporcione una etiqueta.

- Diga **Mouse** o **Teclado.**


En *modo de* predicción:

- Mire un objeto y use el gesto **de pulsar**.

- Aparecerá texto que proporciona el objeto detectado, con la probabilidad más alta (esto se normaliza).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capítulo 14: Evaluación y mejora del modelo Custom Vision modelo

Para que el servicio sea más preciso, deberá seguir entrenando el modelo usado para la predicción. Esto se logra mediante el uso de  la  nueva aplicación, con los modos de entrenamiento y predicción, y esto último requiere que visite el portal, que es lo que se trata en este capítulo. Prepárese para volver a visitar el portal muchas veces para mejorar continuamente el modelo.

1. Vaya de nuevo a Azure Custom Vision Portal y, una vez  que se encuentra en el proyecto, seleccione la pestaña Predicciones (en el centro superior de la página):

    ![Pestaña Seleccionar predicciones](images/AzureLabs-Lab302b-35.png)

2. Verá todas las imágenes que se enviaron al servicio mientras se ejecutaba la aplicación. Si mantiene el puntero sobre las imágenes, le proporcionarán las predicciones que se realizaron para esa imagen:

    ![Lista de imágenes de predicción](images/AzureLabs-Lab302b-36.png)

3. Seleccione una de las imágenes para abrirlo. Una vez abierto, verá las predicciones realizadas para esa imagen a la derecha. Si las predicciones eran correctas y desea agregar esta imagen al modelo  de entrenamiento del servicio, haga clic en el cuadro de entrada Mis etiquetas y seleccione la etiqueta que desea asociar. Cuando haya terminado, haga clic en el botón *Guardar* y cerrar situado en la parte inferior derecha y continúe con la siguiente imagen.

    ![Selección de la imagen para abrir](images/AzureLabs-Lab302b-37.png)

4. Una vez que vuelva a la cuadrícula de imágenes, observará que las imágenes a las que ha agregado etiquetas (y guardado) se quitarán. Si encuentra imágenes que cree que no tienen el elemento etiquetado dentro de ellas, puede eliminarlas; para ello,  haga clic en el paso de esa imagen (puede hacerlo para varias imágenes) y, a continuación, haga clic en Eliminar en la esquina superior derecha de la página de cuadrícula. En el menú emergente siguiente, puede hacer clic en *Sí,* eliminar o *No* para confirmar la eliminación o cancelarla, respectivamente. 

    ![Eliminación de imágenes](images/AzureLabs-Lab302b-38.png)

5. Cuando esté listo para continuar, haga clic en el botón *Verde Entrenar* de la parte superior derecha. El modelo de servicio se entrenará con todas las imágenes que ha proporcionado ahora (lo que lo hará más preciso). Una vez completado el entrenamiento,  asegúrese de hacer clic una vez más en el botón Convertir en predeterminado para que la dirección *URL* de predicción siga utilizando la iteración más actualizada del servicio.

    ![Iniciar el modelo de servicio de entrenamiento ](images/AzureLabs-Lab302b-39.png) ![ Seleccione la opción Make default (Crear opción predeterminada).](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>La aplicación de API Custom Vision finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de Azure Custom Vision para reconocer objetos del mundo real, entrenar el modelo de servicio y mostrar la confianza de lo que se ha visto.

![Ejemplo de proyecto finalizado](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Entrena a **Custom Vision Service para** que reconozca más objetos.

### <a name="exercise-2"></a>Ejercicio 2

Para ampliar lo que ha aprendido, complete los ejercicios siguientes:

Reproducir un sonido cuando se reconoce un objeto.

### <a name="exercise-3"></a>Ejercicio 3

Use la API para volver a entrenar el servicio con las mismas imágenes que está analizando la aplicación, para que el servicio sea más preciso (realizar predicciones y entrenamientos simultáneamente).