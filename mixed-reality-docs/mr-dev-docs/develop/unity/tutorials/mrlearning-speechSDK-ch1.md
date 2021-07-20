---
title: 'Tutoriales de los servicios de voz de Azure: 1. Integración y uso de reconocimiento de voz y la transcripción'
description: Haz este curso para aprender a implementar el SDK de voz de Azure dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 39eaa8a17d4616dc9c044f9bff7522dde41cffb7
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656629"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a>1. Integración y uso del reconocimiento de voz y la transcripción

## <a name="overview"></a>Introducción

En esta serie de tutoriales, crearás una aplicación de Mixed Reality que explore el uso de los servicios de voz de Azure con HoloLens 2. Cuando completes esta serie de tutoriales, podrás usar el micrófono del dispositivo para transcribir la voz a texto en tiempo real, traducir la voz a otros idiomas y aprovechar la característica Reconocimiento de la intención para comprender los comandos de voz mediante inteligencia artificial.

## <a name="objectives"></a>Objetivos

* Aprender a integrar los servicios de voz de Azure con una aplicación de HoloLens 2
* Aprender a usar el reconocimiento de voz para transcribir texto

## <a name="prerequisites"></a>Requisitos previos

>[!TIP]
>Si aún no has completado la serie de [tutoriales de introducción](mr-learning-base-01.md), es recomendable que lo hagas en primer lugar.

* Un equipo Windows 10 configurado con las [herramientas correctas instaladas](../../install-the-tools.md)
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

> [!Important]
> Esta serie de tutoriales admite Unity 2020 LTS (actualmente 2020.3.x) si usa Open XR o el complemento de XR de Windows y también Unity 2019 LTS (actualmente 2019.4.x) si usa WSA heredado o el complemento de XR de Windows. Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Para ello, antes debes seguir las instrucciones de [Inicialización de tu proyecto y primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*
2. [Cambiar la plataforma de compilación](mr-learning-base-02.md#configuring-the-unity-project)
3. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importación de Mixed Reality Toolkit y configuración del proyecto de Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Crear y configurar la escena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) y asignarle un nombre adecuado; por ejemplo, *AzureSpeechServices*

A continuación, siga las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK de la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

## <a name="configuring-the-speech-commands-start-behavior"></a>Configurar el comportamiento inicial de los comandos de voz

Dado que usarás el SDK de voz para el reconocimiento de voz y la transcripción, debes configurar los comandos de voz de MRTK para que no interfieran con la funcionalidad del SDK de voz. Para ello, puedes cambiar el comportamiento inicial de los comandos de voz de Auto Start (Inicio automático) a Manual Start (Inicio manual).

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Input** (Entrada), clona **DefaultHoloLens2InputSystemProfile** y **DefaultMixedRealitySpeechCommandsProfile** y, a continuación, cambia el valor de **Start Behavior** (Comportamiento inicial) de los comandos de voz a **Manual Start** (Inicio manual):

![mrlearning-speech 1](images/mrlearning-speech/tutorial1-section2-step1-1.png)

## <a name="configuring-the-capabilities"></a>Configuración de las funcionalidades

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):

![mrlearning-speech 2](images/mrlearning-speech/tutorial1-section3-step1-1.png)

En **Publishing Settings** (Configuración de publicación), desplácese hasta la sección **Capabilities** (Funcionalidades) y compruebe nuevamente que las funcionalidades **InternetClient**, **Microphone** y **SpatialPerception**, que se habilitaron al crear el proyecto al principio del tutorial, estén habilitadas. A continuación, habilita las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer**:

![mrlearning-speech 3](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:

* [Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (versión más reciente)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/azure-speech-services-v2.5.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.5.2.unitypackage)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulte las instrucciones del artículo [Importación de Mixed Reality Toolkit](mr-learning-base-04.md#importing-the-tutorial-assets).

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![mrlearning-speech 4](images/mrlearning-speech/tutorial1-section4-step1-1.png)

Tiene que configurar el proyecto de Unity para publicar los complementos de Voz de Azure para ARM64; para ello, en la ventana de Project (Proyecto), vaya a **Assets** > **SpeechSDK** > **Plugins** > **WSA** > **ARM64** (Recursos > SpeechSDK > Complementos > WSA > ARM64) y seleccione el complemento **Microsoft.CognitiveServices.Speech.core**.

![mrlearning-speech 5](images/mrlearning-speech/tutorial1-section4-step1-2.PNG)

Con el complemento **Microsoft.CognitiveServices.Speech.core** aún seleccionado, en la ventana Inspector, habilite **WSA Player** (Reproductor de WSA) en **Platform settings** (Configuración de la plataforma), seleccione **UWP** para SDK, **ARM64** para CPU, y haga clic en Apply (Aplicar) para aplicar esta configuración al complemento.

![mrlearning-speech 6](images/mrlearning-speech/tutorial1-section4-step1-3.PNG)

Repita estos pasos para cada uno de los complementos restantes:

* **Microsoft.CognitiveServices.Speech.extension.audio.sys**
* **Microsoft.CognitiveServices.Speech.extension.kws**
* **Microsoft.CognitiveServices.Speech.extension.lu**
* **Microsoft.CognitiveServices.Speech.extension.silk_codec**

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, prepararás la escena agregando el objeto prefabricado del tutorial y configurarás el componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) para controlar la escena.

En la ventana Project (Proyecto), desplázate hasta **Assets** (Recursos) > **MRTK.Tutorials.AzureSpeechServices** > carpeta **Prefabs** y arrastra y coloca el objeto prefabricado **Lunarcom** en la ventana Hierarchy (Jerarquía) para agregarlo a la escena:

![mrlearning-speech 7](images/mrlearning-speech/tutorial1-section5-step1-1.png)

Con el objeto **Lunarcom** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) al objeto Lunarcom:

![mrlearning-speech 8](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> El componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Con el objeto **Lunarcom** todavía seleccionado, expándelo para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **Terminal** al campo **Terminal** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]):

![mrlearning-speech 9](images/mrlearning-speech/tutorial1-section5-step1-3.png)

Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Terminal para mostrar sus objetos secundarios y, a continuación, arrastra el objeto **ConnectionLight** al campo **Connection Light** del componente Lunarcom Controller (Script) (Controlador de Lunarcom [script]) y el objeto **OutputText** al campo **Output Text** (Texto de salida):

![mrlearning-speech 10](images/mrlearning-speech/tutorial1-section5-step1-4.png)

Con el objeto **Lunarcom** todavía seleccionado, expande el objeto Buttons para mostrar sus objetos secundarios y, a continuación, en la ventana Inspector, expande la lista **Buttons** (Botones), establece su valor de **Size** (Tamaño) en 3 y arrastra los objetos **MicButton**, **SatelliteButton** y **RocketButton** a los campos de **Element** (Elemento) 0, 1 y 2, respectivamente:

![mrlearning-speech 11](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a>Conexión del proyecto de Unity con el recurso de Azure

Para usar los servicios de voz de Azure, debes crear un recurso de Azure y obtener una clave de API para el servicio de voz. Sigue las instrucciones de [Prueba gratuita del servicio Voz](/azure/cognitive-services/speech-service/get-started) y toma nota de la región de servicio (también conocida como ubicación) y la clave de API (también conocida como Key1 o Key2).

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca la sección **Speech SDK Credentials** (Credenciales del SDK de voz) de **Lunarcom Controller (Script)** (Controlador de Lunarcom [script]) y configúrala como se indica a continuación:

* En el campo **Speech Service API Key** (Clave de API del servicio Voz), escribe la clave de API (Key1 o Key2)
* En el campo **Speech Service Region** (Región del servicio Voz), escribe tu región de servicio (ubicación) con letras minúsculas y sin espacios.

![mrlearning-speech 12](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a>Uso del reconocimiento de voz para transcribir la voz

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Speech Recognizer (Script)** (Reconocimiento de voz de Lunarcom [script]):

![mrlearning-speech 13](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> El componente Lunarcom Speech Recognizer (Script) (Reconocimiento de voz de Lunarcom [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

Si ahora entras en el modo de juego, puedes probar el reconocimiento de voz presionando primero el botón del micrófono:

![mrlearning-speech 14](images/mrlearning-speech/tutorial1-section7-step1-2.png)

A continuación, suponiendo que el equipo tiene un micrófono, cuando digas algo, la voz se transcribirá en el panel del terminal:

![mrlearning-speech 15](images/mrlearning-speech/tutorial1-section7-step1-3.png)

> [!CAUTION]
> La aplicación necesita conectarse a Azure, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.

## <a name="congratulations"></a>Enhorabuena

Has implementado el reconocimiento de voz con tecnología de Azure. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.

En el próximo tutorial, obtendrás información sobre cómo ejecutar comandos con el reconocimiento de voz de Azure.

> [!div class="nextstepaction"]
> [Siguiente tutorial: 2. Ejecución de comandos mediante el reconocimiento de voz de Azure](mrlearning-speechSDK-ch2.md)
