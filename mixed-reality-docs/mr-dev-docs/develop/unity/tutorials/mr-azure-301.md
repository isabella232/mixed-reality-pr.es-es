---
title: 'HoloLens de primera generación y Azure (301): traducción de idiomas'
description: Complete este curso para aprender a implementar Azure Traductor Text API dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, translator text, hololens, immersive, vr, language translation, Windows 10, Visual Studio
ms.openlocfilehash: 8eeeab45c6e7d93c1b04afa4db811f220b0c2f9c85400fc93a81ac413164a6b7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115229751"
---
# <a name="hololens-1st-gen-and-azure-301-language-translation"></a>HoloLens (1ª generación) y Azure 301: traducción de idioma

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

En este curso, aprenderá a agregar funcionalidades de traducción a una aplicación de realidad mixta mediante Azure Cognitive Services, con Traductor Text API.

![Producto final](images/AzureLabs-Lab1-00.png)

La Traductor Text API es un servicio de traducción que funciona casi en tiempo real. El servicio está basado en la nube y, mediante una llamada API REST, una aplicación puede hacer uso de la tecnología de traducción automática neuronal para traducir texto a otro idioma. Para más información, visite la página [de Azure Traductor Text API](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).

Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:

1.  El usuario hablará en un micrófono conectado a un casco envolvente (VR) (o al micrófono integrado de HoloLens).
2.  La aplicación capturará el dictado y lo enviará a Azure Traductor Text API.
3.  El resultado de la traducción se mostrará en un grupo de interfaz de usuario simple en la escena de Unity.

Este curso le enseñará a obtener los resultados de Traductor Service en una aplicación de ejemplo basada en Unity. Será su función aplicar estos conceptos a una aplicación personalizada que pueda estar creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (301): Traducción de idiomas</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente en Windows Mixed Reality cascos envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que podría necesitar emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algún eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de la escritura (mayo de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo Instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente que el que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR).
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [casco Windows Mixed Reality envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Un conjunto de auriculares con un micrófono integrado (si el casco no tiene un micrófono y altavoces integrados)
- Acceso a Internet para la instalación y recuperación de traducción de Azure

## <a name="before-you-start"></a>Antes de comenzar

- Para evitar problemas al compilar este proyecto, se recomienda encarecidamente crear el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
- El código de este tutorial le permitirá grabar desde el dispositivo de micrófono predeterminado conectado al equipo. Asegúrese de que el dispositivo de micrófono predeterminado está establecido en el dispositivo que planea usar para capturar la voz.
- Para permitir que el equipo habilite el dictado, vaya a Configuración > **Privacy > Speech (Privacidad** > Voz), escriba & y seleccione el botón Turn On speech services and typing suggestions (Activar servicios de voz y **sugerencias** de escritura).
- Si usa un micrófono y auriculares conectados a los cascos (o integrados en él), asegúrese de que la opción "Cuando uso el casco, cambie al micrófono del casco" está activada en Configuración > **Mixed Reality > Audio and speech**.

   ![Configuración de realidad mixta](images/AzureLabs-Lab1-00-5.png)

   ![Configuración del micrófono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> Tenga en cuenta que si está desarrollando para un casco envolvente para este laboratorio, puede experimentar problemas con el dispositivo de salida de audio. Esto se debe a un problema con Unity, que se ha corregido en versiones posteriores de Unity (Unity 2018.2). El problema impide que Unity cambie el dispositivo de salida de audio predeterminado en tiempo de ejecución. Para evitarlo, asegúrese de que ha completado los pasos anteriores y cierre y vuelva a abrir el editor cuando este problema se presente.

## <a name="chapter-1--the-azure-portal"></a>Capítulo 1: Azure Portal

Para usar azure Traductor API, deberá configurar una instancia del servicio para que esté disponible para la aplicación.

1.  Inicie sesión en [Azure Portal.](https://portal.azure.com)

    > [!NOTE]
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los proctores para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **Nuevo en** la esquina superior izquierda y busque "Traductor Text API". Seleccione **Entrar**.

    ![Nuevo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > Es posible que **la** palabra Nuevo se haya reemplazado **por Crear un recurso** en los portales más recientes.

3.  La nueva página proporcionará una descripción del servicio *Traductor Text API.* En la parte inferior izquierda de esta página, seleccione **el botón** Crear para crear una asociación con este servicio.

    ![Creación de Traductor Text API Service](images/AzureLabs-Lab1-03.png)

4.  Una vez que haya hecho clic en **Crear:**

    1. Inserte el nombre **deseado para** esta instancia de servicio.
    2. Seleccione una suscripción **adecuada.**
    3. Seleccione el **plan de** tarifa adecuado para usted; si es la primera vez que crea un servicio de texto de *Traductor,* debe estar disponible un nivel gratuito (denominado F0).
    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, [visite el artículo del grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Determine la **ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos). Lo ideal es que la ubicación esté en la región donde se ejecutaría la aplicación. Algunos recursos de Azure solo están disponibles en determinadas regiones.
    6. También deberá confirmar que ha comprendido los términos y condiciones aplicados a este servicio.
    7. Seleccione **Crear**.

        ![Seleccione el botón Crear.](images/AzureLabs-Lab1-04.png)

5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.
6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. 

    ![Notificación de creación de servicios de Azure](images/AzureLabs-Lab1-05.png)

7.  Haga clic en la notificación para explorar la nueva instancia de servicio. 

    ![Vaya al menú emergente del recurso.](images/AzureLabs-Lab1-06.png)

8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia de Traductor text API Service. 

    ![Traductor Página Servicio Text API](images/AzureLabs-Lab1-07.png)

9.  En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio. 
10. En  la página Inicio rápido del servicio de texto de *Traductor,* vaya al primer *paso,* Tomar las claves y haga clic en Claves **(también** puede hacerlo haciendo clic en el hipervínculo azul Claves, que se encuentra en el menú de navegación Servicios, anotado por el icono de clave). Esto revelará las claves de *servicio*.
11. Tome una copia de una de las claves mostradas, ya que la necesitará más adelante en el proyecto. 

## <a name="chapter-2--set-up-the-unity-project"></a>Capítulo 2: Configuración del proyecto de Unity

Configure y pruebe los cascos envolventes de realidad mixta.

> [!NOTE]
> No necesitará controladores de movimiento para este curso. Si necesita soporte técnico para configurar un casco envolvente, [siga estos pasos.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

A continuación se muestra una configuración típica para desarrollar con realidad mixta y, como tal, es una buena plantilla para otros proyectos:

1.  Abra *Unity y* haga clic en **Nuevo.** 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab1-08.png)

2.  Ahora deberá proporcionar un nombre de Project Unity. Inserte **MR_Translation**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca la *ubicación en* un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![Proporcione detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab1-09.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar > preferencias y,** a continuación, en la nueva ventana, vaya **a Herramientas externas**. Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![Actualice la preferencia del editor de scripts.](images/AzureLabs-Lab1-10.png)

4.  A continuación, vaya a **File > Build Configuración and switch** the platform to Universal Windows Platform (Crear Windows plataforma **universal).** Para ello, haga clic en el **botón Switch Platform (Cambiar plataforma).**

    ![Cree Configuración ventana y cambie la plataforma a UWP.](images/AzureLabs-Lab1-11.png)

5.  Vaya a **Archivo > compilación Configuración** y asegúrese de que:

    1. **El dispositivo de** destino se establece **en Cualquier dispositivo.**

        > Para Microsoft HoloLens, establezca **Dispositivo de destino** *en HoloLens*.

    2. **Tipo de** compilación se establece en **D3D**
    3. **El SDK** se establece en **Instalado más reciente.**
    4. **Visual Studio versión está** establecida en **La versión más reciente instalada**
    5. **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**
    6. Guarde la escena y agrégréla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![Haga clic en el botón Agregar escenas abiertas.](images/AzureLabs-Lab1-12.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![Creación de una nueva carpeta de scripts](images/AzureLabs-Lab1-13.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo *Nombre* de archivo : texto, **escriba MR_TranslationScene** y, a continuación, **presione Guardar.**

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab1-14.png)

            > Tenga en cuenta que debe guardar las escenas de Unity en la carpeta *Recursos,* ya que deben estar asociadas con el Project. La creación de la carpeta scenes (y otras carpetas similares) es una manera típica de estructurar un proyecto de Unity.

    7. El resto de la configuración, *en Build Configuración*, se debe dejar como valor predeterminado por ahora.

6. En la *ventana Build Configuración* (Compilar Configuración), haga clic en el botón Player Configuración (Player **Configuración)** y se abrirá el panel relacionado en el espacio donde se encuentra *el inspector.* 

    ![Abra la configuración del reproductor.](images/AzureLabs-Lab1-15.png)

7. En este panel, es necesario comprobar algunas configuraciones:

    1. En la **pestaña Otros Configuración** datos:

        1. **La versión del entorno de** ejecución de scripting debe ser **estable** (equivalente a .NET 3.5).
        2. **El back-end de** scripting debe **ser .NET**
        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Actualice otras opciones.](images/AzureLabs-Lab1-16.png)
      
    2. En la **pestaña Configuración,** en **Funcionalidades**, compruebe:

        1. **InternetClient**
        2. **Micrófono**

            ![Actualización de la configuración de publicación.](images/AzureLabs-Lab1-17.png)

    3. Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de Publicar **Configuración**), marque **Virtual Reality Supported (Compatible con Virtual Reality)** y asegúrese de que se agrega el **SDK** Windows Mixed Reality virtual.

        ![Actualice el X R Configuración.](images/AzureLabs-Lab1-18.png)

8.  De nuevo **en build Configuración,** los proyectos *de C#* de Unity ya no están en gris; Marque la casilla situada junto a esto. 
9.  Cierre la ventana Build Settings (Configuración de compilación).
10. Guarde la escena y Project (**FILE > SAVE SCENE /FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Capítulo 3: Configuración de la cámara principal

> [!IMPORTANT]
> Si desea omitir el componente De configuración de *Unity* de este curso y continuar directamente en el código, no dude en descargar este [paquete de Unity,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)importarlo en el proyecto como un paquete personalizado y, a continuación, continuar desde el capítulo [5.](#chapter-5--create-the-results-class) [](https://docs.unity3d.com/Manual/AssetPackages.html) Todavía tendrá que crear una aplicación de Unity Project.

1.  En el *Panel de* jerarquía, encontrará un objeto denominado **Cámara** principal, que representa el punto de vista "principal" una vez que está "dentro" de la aplicación.
2.  Con el panel de Unity delante de usted, seleccione el **elemento GameObject de la cámara principal.** Observará que el *Panel inspector* (que se encuentra generalmente a la derecha, dentro del panel) mostrará los distintos componentes de *ese GameObject*, con *Transformación* en la parte superior, seguido de *Cámara* y algunos otros componentes. Deberá restablecer la transformación de la cámara principal para que esté correctamente posicionada.
3.  Para ello, seleccione el icono **de engranaje** situado junto al componente *Transformación* de la cámara y seleccione **Restablecer**. 

    ![Restablezca la transformación Cámara principal.](images/AzureLabs-Lab1-19.png)
 
4.  A *continuación,* el componente Transformar debe tener el siguiente aspecto:

    1. La *posición* se establece **en 0, 0, 0**
    2. *La* rotación se establece **en 0, 0, 0**
    3. Y *Scale* se establece en **1, 1, 1**

        ![Información de transformación para la cámara](images/AzureLabs-Lab1-20.png)

5.  A continuación, con **el objeto Cámara** principal seleccionado, vea el **botón** Agregar componente situado en la parte inferior del *panel inspector*. 
6.  Seleccione ese botón y busque (escribiendo Origen de *audio* en el campo de búsqueda o navegando por las secciones) para el componente denominado Origen de **audio** como se muestra a continuación y selecciónelo (al presionar Entrar también funciona).
7.  Se *agregará un* componente De origen de audio a la **cámara** principal, como se muestra a continuación.

    ![Agregue un componente De origen de audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > Por Microsoft HoloLens, también debe cambiar lo siguiente, que forman parte del componente **Cámara** en la **cámara principal:**
    > - **Borrar marcas:** Color sólido.
    > - **Fondo** "Negro, Alfa 0": color hexadecimal: #00000000.

## <a name="chapter-4--setup-debug-canvas"></a>Capítulo 4: Configuración del lienzo de depuración

Para mostrar la entrada y salida de la traducción, es necesario crear una interfaz de usuario básica. Para este curso, creará un objeto de interfaz de usuario de lienzo, con varios objetos "Text" para mostrar los datos.

1.  Haga clic con el botón derecho en un área vacía del *Panel de* jerarquía, en **la interfaz de usuario**, agregue un **lienzo**.

    ![Agregue un nuevo objeto de interfaz de usuario de lienzo.](images/AzureLabs-Lab1-22.png)

2.  Con el objeto Canvas seleccionado, en el *panel Inspector* (dentro del componente "Canvas"), cambie Render Mode (Modo **de** representación) a World **Space (Espacio mundial).** 
3.  A continuación, cambie los parámetros siguientes en *la transformación Dect del panel inspector*:

    1. *POS*  -   **X** 0 **Y** 0 **Z** 40
    2. *Ancho:* 500
    3. *Alto:* 300
    4. *Escala*  -  **X** 0.13 **Y** 0.13 **Z** 0.13

        ![Actualice la transformación de rect para el lienzo.](images/AzureLabs-Lab1-23.png)
 
4.  Haga clic con el botón **derecho en el** lienzo en el Panel de *jerarquía,* en **la interfaz de** usuario , y agregue un **panel**. Este **panel** proporcionará un fondo al texto que se mostrará en la escena.
5.  Haga clic con el botón **derecho en el Panel** en el Panel de *jerarquía,* en **la interfaz de** usuario , y agregue un objeto **Text**. Repita el mismo proceso hasta que haya creado cuatro objetos de texto de la interfaz de usuario en total (Sugerencia: si tiene seleccionado el primer objeto "Text", simplemente presione **"Ctrl" + "D"** para duplicarlo, hasta que tenga cuatro en total). 
6.  Para cada **objeto de texto**, selecciónelo y use las tablas siguientes para establecer los parámetros en el Panel *inspector*.

    1. Para el *componente Transformación de rect:*

        | Name                   | Transformación: *posición*             | Ancho      | Alto    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | MicrophoneStatusLabel  | **X** -80 **Y** 90 **Z** 0         | 300        | 30        |
        | AzureResponseLabel     | **X** -80 **Y** 30 **Z** 0         | 300        | 30        |
        | DictationLabel         | **X** -80 **Y** -30 **Z** 0        | 300        | 30        |
        | TranslationResultLabel | **X** -80 **Y** -90 **Z** 0        | 300        | 30        |


    2. Para el **componente Texto (script):**


        | Nombre                   | Texto               | Tamaño de fuente    |
        |:----------------------:|:------------------:|:------------:|
        | MicrophoneStatusLabel  | Estado del micrófono: | 20           |
        | AzureResponseLabel     | Respuesta web de Azure | 20           |
        | DictationLabel         |   Acaba de decir:   | 20           |
        | TranslationResultLabel |    Conversión:    | 20           |

        ![Introduzca los valores correspondientes para las etiquetas de la interfaz de usuario.](images/AzureLabs-Lab1-24.png)

    3. Además, haga que el estilo de fuente en **negrita**. Esto hará que el texto sea más fácil de leer.

        ![Fuente en negrita.](images/AzureLabs-Lab1-25.png)

7.  Para cada objeto *de texto de la interfaz de* usuario creado en el capítulo [5,](#chapter-5--create-the-results-class)cree un nuevo *objeto de texto de* interfaz de usuario **secundario**. Estos secundarios mostrarán la salida de la aplicación. Cree *objetos* secundarios haciendo clic con el botón derecho en el elemento  primario deseado (por *ejemplo, MicrophoneStatusLabel),* seleccione IU y, a continuación, **seleccione Texto.**
8.  Para cada uno de estos secundarios, selecciónelo y use las tablas siguientes para establecer los parámetros en el Panel inspector.

    1. Para el **componente Transformación de** rect:

        | Name                  | Transformación: *posición* | Ancho      | Alto    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | MicrophoneStatusText  | X 0 Y -30 Z 0          | 300        | 30        |
        | AzureResponseText     | X 0 Y -30 Z 0          | 300        | 30        |
        | DictationText         | X 0 Y -30 Z 0          | 300        | 30        |
        | TranslationResultText | X 0 Y -30 Z 0          | 300        | 30        |

    2. Para el **componente Texto (script):**

        | Nombre                  | Texto          | Tamaño de fuente    |
        |:---------------------:|:-------------:|:------------:|
        | MicrophoneStatusText  |      ??       | 20           |
        | AzureResponseText     |      ??       | 20           |
        | DictationText         |      ??       | 20           |
        | TranslationResultText |      ??       | 20           |

9. A continuación, seleccione la opción de alineación "centre" para cada componente de texto:

    ![alinear texto.](images/AzureLabs-Lab1-26.png)

10. Para asegurarse de que **los objetos de texto de** la interfaz de usuario secundarios se puedan leer fácilmente, cambie su *color*. Para ello, haga clic en la barra (actualmente "Negro") junto a *Color*. 

    ![Introduzca los valores correspondientes para las salidas de texto de la interfaz de usuario.](images/AzureLabs-Lab1-27.png)
 
11. A continuación, en la nueva ventana *Color,* little, cambie *el color hexadecimal* a: **0032EAFF.**

    ![Actualice el color a azul.](images/AzureLabs-Lab1-28.png)
 
12. A continuación se muestra el aspecto **de** la interfaz de usuario.
    1.  En el *panel Jerarquía*:

        ![Tener jerarquía en la estructura proporcionada.](images/AzureLabs-Lab1-29.png)

    2.  En las vistas *de escena* *y juego:*

        ![Tener las vistas de escena y juego en la misma estructura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a>Capítulo 5: Creación de la clase Results

El primer script que debe crear es la *clase Results,* que es responsable de proporcionar una manera de ver los resultados de la traducción. La clase almacena y muestra lo siguiente: 

- Resultado de la respuesta de Azure.
- Estado del micrófono. 
- Resultado del dictado (voz a texto).
- Resultado de la traducción.

Para crear esta clase: 

1.  Haga clic con el botón derecho *en Project panel y,* a continuación, **cree > carpeta**. Asigne a la carpeta el **nombre Scripts**. 
 
    ![Cree la carpeta scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra la carpeta scripts.](images/AzureLabs-Lab1-32.png)
 
2.  Con la **carpeta Scripts** de creación, haga doble clic en ella para abrirla. A continuación, dentro de esa carpeta, haga clic con el botón derecho y **seleccione Crear >** script de **C#.** Asigne al script el nombre *Results*. 

    ![Cree el primer script.](images/AzureLabs-Lab1-33.png)
 
3.  Haga doble clic en el nuevo script *Resultados* para abrirlo con **Visual Studio**.
4.  Inserte los siguientes espacios de nombres:

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  Dentro de la clase , inserte las siguientes variables:

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  A continuación, agregue el método *Awake(),* al que se llamará cuando se inicialice la clase . 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  Por último, agregue a la interfaz de usuario los métodos responsables de generar la información de los distintos resultados. 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-6--create-the-microphonemanager-class"></a>Capítulo 6: Creación de la *clase MicrophoneManager*

La segunda clase que va a crear es *MicrophoneManager*.

Esta clase es responsable de:

- Detectar el dispositivo de grabación conectado al casco o la máquina (lo que sea el valor predeterminado).
- Capture el audio (voz) y use el dictado para almacenarlo como una cadena.
- Una vez que la voz se haya pausado, envíe el dictado a la Traductor llamada.
- Hospedar un método que pueda detener la captura de voz si lo desea.

Para crear esta clase: 
1.  Haga doble clic en **la carpeta Scripts** para abrirlo. 
2.  Haga clic con el botón derecho en la **carpeta Scripts** y haga clic > script **de C#.** Asigne al script el nombre *MicrophoneManager.* 
3.  Haga doble clic en el nuevo script para abrirlo con Visual Studio.
4.  Actualice los espacios de nombres para que sean los mismos que los siguientes, en la parte superior de la *clase MicrophoneManager:*

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  A continuación, agregue las siguientes variables dentro de la *clase MicrophoneManager:*

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().* Se llamará a estos cuando se inicialice la clase:

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  Puede eliminar *el* *método Update(),* ya que esta clase no lo usará.
8.  Ahora necesita los métodos que usa la aplicación para iniciar y detener la captura de voz y pasarla a la clase *Traductor,* que compilará pronto. Copie el código siguiente y péguelo debajo *del método Start().*

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > Aunque esta aplicación no la usará, aquí también se ha proporcionado el método *StopCapturingAudio(),* en caso de que quiera implementar la capacidad de detener la captura de audio en la aplicación.

9.  Ahora debe agregar un controlador de dictado que se invocará cuando se detenga la voz. A continuación, este método pasará el texto dictado a la *Traductor* especificada.

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.

> [!WARNING]  
> En este momento observará que aparece un error en el panel de la consola del editor de *Unity* ("El nombre "Traductor" no existe...". Esto se debe a que el código *hace referencia Traductor* clase , que creará en el capítulo siguiente.

## <a name="chapter-7--call-to-azure-and-translator-service"></a>Capítulo 7: Llamada a Azure y al servicio de traductor

El último script que debe crear es la *Traductor* clase . 

Esta clase es responsable de:

-   Autenticación de la aplicación *con Azure* a cambio de un token **de autenticación.**
-   Use el **token de autenticación** para enviar texto (recibido de la *clase MicrophoneManager)* que se va a traducir.
-   Recibir el resultado traducido y pasarlo a la *clase Results* para visualizarlo en la interfaz de usuario.

Para crear esta clase: 
1.  Vaya a la **carpeta Scripts** que creó anteriormente. 
2.  Haga clic con el botón derecho **en el panel Project ,** cree > script de **C#.** Llame al script *Traductor*.
3.  Haga doble clic en el nuevo script *Traductor* para abrirlo **con Visual Studio**.
4.  Agregue los siguientes espacios de nombres a la parte superior del archivo:

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  A continuación, agregue las siguientes variables dentro *de Traductor* clase :

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - Los idiomas insertados en la **enumeración** languages son solo ejemplos. No dude en agregar más si lo desea. la [API admite más de 60 idiomas](/azure/cognitive-services/translator/languages) (incluido Asín).
    > - Hay una página más interactiva que abarca los [idiomas](https://www.microsoft.com/translator/business/languages/)disponibles, aunque tenga en cuenta que la página solo parece funcionar cuando el idioma del sitio está establecido en "" (y es probable que el sitio de Microsoft se redirija a su idioma nativo). Puede cambiar el idioma del sitio en la parte inferior de la página o modificando la dirección URL.
    > - El **valor authorizationKey,** en el fragmento  de código anterior, debe ser la clave que recibió al suscribirse a La API de Azure *Traductor Text.* Esto se ha abordado [en el capítulo 1.](#chapter-1--the-azure-portal)

6.  Ahora es necesario agregar código para los métodos *Awake()* y *Start().* 
7.  En este caso, el código realizará una llamada a *Azure* mediante la clave de autorización para obtener un *token*.

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > El token expirará después de 10 minutos. Dependiendo del escenario de la aplicación, es posible que tenga que realizar la misma llamada de coroutina varias veces.

8.  La corrotina para obtener el token es la siguiente:

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > Si edita el nombre del método IEnumerator **GetTokenCoroutine(),** debe actualizar los valores de cadena de llamada *StartCoroutine* y *StopCoroutine* en el código anterior. [Según la documentación de Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para detener una *cortina* específica, debe usar el método de valor de cadena.

9.  A continuación, agregue la corrotina (con un método de secuencia "support" justo debajo) para obtener la traducción del texto recibido por la *clase MicrophoneManager.* Este código crea una cadena de consulta para enviar a Text API de *Azure Traductor* y, a continuación, usa la clase UnityWebRequest interna de Unity para realizar una llamada "Get" al punto de conexión con la cadena de consulta. A continuación, el resultado se usa para establecer la traducción en el objeto Results. El código siguiente muestra la implementación:

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity.*

## <a name="chapter-8--configure-the-unity-scene"></a>Capítulo 8: Configuración de la escena de Unity

1.  De nuevo en el Editor de  Unity, haga clic en la clase *Results* y arrástrela desde la carpeta **Scripts** hasta el objeto **Main Camera** (Cámara principal) en el Panel de *jerarquía .*
2.  Haga clic en **la cámara principal** y mire en el panel *inspector*. Observará que, dentro del componente *script* recién agregado, hay cuatro campos con valores vacíos. Estas son las referencias de salida a las propiedades del código. 
3.  Arrastre los objetos **Text adecuados** desde el *Panel de jerarquía a* esas cuatro ranuras, como se muestra en la imagen siguiente.

    ![Actualice las referencias de destino con los valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  A continuación, haga clic y *arrastre la Traductor* desde la carpeta **Scripts** hasta el objeto **Cámara** principal en el Panel *de jerarquía*. 
5.  A continuación, haga clic y arrastre la *clase MicrophoneManager* desde la **carpeta Scripts** hasta el objeto **Cámara** principal en el Panel *de jerarquía*. 
6.  Por último, haga clic en **la cámara** principal y mire en el *panel inspector*. Observará que, en el script que arrastró, hay dos cuadros desplegables que le permitirán establecer los idiomas.
 
    ![Asegúrese de que los idiomas de traducción previstos son de entrada.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a>Capítulo 9: Prueba en realidad mixta

En este momento, debe probar que la escena se ha implementado correctamente.

Asegúrese de que:

- Todas las configuraciones mencionadas [en el capítulo 1](#chapter-1--the-azure-portal) se establecen correctamente. 
- Los scripts *Results*, *Traductor*, *y MicrophoneManager*, se adjuntan al **objeto Cámara** principal. 
- Ha colocado la clave de *servicio Traductor Text API* **de** Azure en la variable **authorizationKey** dentro del script *Traductor.*  
- Todos los campos del panel *inspector de la* cámara principal se asignan correctamente.
- El micrófono funciona al ejecutar la escena (si no  es así, compruebe que el micrófono conectado es el dispositivo predeterminado y que lo ha configurado correctamente dentro de [Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).

Puede probar el casco envolvente presionando el **botón Reproducir** en el Editor *de Unity.*
La aplicación debe funcionar a través del casco envolvente conectado.

> [!WARNING]  
> Si ve un error en la consola de Unity sobre el cambio predeterminado del dispositivo de audio, es posible que la escena no funcione según lo previsto. Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los cascos que los tienen. Si ve este error, basta con detener la escena e iniciarla de nuevo y las cosas deberían funcionar según lo previsto.

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a>Capítulo 10: Compilación de la solución para UWP y instalación local en la máquina local

Ya se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a **Build Configuración**: File > **Build Configuración...**
2.  En la ventana **Compilar Configuración,** haga clic en **Compilar**.

    ![Cree la escena de Unity.](images/AzureLabs-Lab1-36.png)
  
3.  Si aún no lo ha hecho, marque **Proyectos de C# de Unity.**
4.  Haga clic en **Generar**. Unity iniciará una *Explorador de archivos,* donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación. Cree esa carpeta ahora y así mismo den el nombre *App*. Después, con la *carpeta Aplicación* seleccionada, presione **Seleccionar carpeta.** 
5.  Unity comenzará a compilar el proyecto en la *carpeta Aplicación.* 
6.  Una vez que Unity haya terminado de compilar (puede tardar algún tiempo), se abrirá una ventana de *Explorador de archivos* en la ubicación de la compilación (compruebe la barra de tareas, ya que es posible que no siempre aparezca encima de las ventanas, pero le notificará la adición de una nueva ventana).

## <a name="chapter-11--deploy-your-application"></a>Capítulo 11: Implementación de la aplicación

Para implementar la aplicación:

1.  Vaya a la nueva compilación de Unity (la *carpeta Aplicación)* y abra el archivo de solución *con Visual Studio*.
2.  En Configuración de la solución, **seleccione Depurar**.
3.  En la Plataforma de soluciones, **seleccione x86**, **Máquina local.** 

    > Para la Microsoft HoloLens, es posible que le resulte más fácil establecer esta opción en Equipo remoto *para* que no se le ate con el equipo. Sin embargo, también tendrá que hacer lo siguiente:
    > - Conozca la **dirección IP de** su HoloLens, que puede encontrarse en las opciones avanzadas de Configuración > Network & Internet > Wi-Fi > *;* IPv4 es la dirección que debe usar. 
    > - Asegúrese *de que el modo de* desarrollador está en **;** se encuentra *en Configuración > actualización & seguridad > para desarrolladores*.

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  Vaya al **menú Compilar y** haga clic en Implementar **solución** para realizar la instalación local de la aplicación en el equipo.
5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.
6.  Una vez iniciada, la aplicación le pedirá que autorice el acceso al micrófono. Asegúrese de hacer clic en el **botón SÍ.**
7.  Ya está listo para empezar a traducir.

## <a name="your-finished-translation-text-api-application"></a>La aplicación Translation Text API finalizada

Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Translation Text API para convertir la voz en texto traducido.

![Producto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

¿Puede agregar la funcionalidad de texto a voz a la aplicación para que se hable con el texto devuelto?

### <a name="exercise-2"></a>Ejercicio 2

Haga posible que el usuario cambie los idiomas de origen y salida ('from' y 'to') dentro de la propia aplicación, por lo que no es necesario volver a generar la aplicación cada vez que quiera cambiar los idiomas.