---
title: Configuración de Photon Unity Networking
description: Siga este curso para aprender a implementar Photon Unity Networking en una aplicación de realidad mixta de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, multi-user capabilities, Photon, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, PUN
ms.localizationpriority: high
ms.openlocfilehash: 28776e106b96d1265e435d60e7008b1d88c01060
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702506"
---
# <a name="2-setting-up-photon-unity-networking"></a>2. Configuración de Photon Unity Networking

En este tutorial, se preparará para la creación de una experiencia compartida con Photon Unity Networking (PUN). Obtendrá información sobre cómo crear una aplicación de PUN, importar recursos de PUN en el proyecto de Unity y conectar el proyecto de Unity a la aplicación de PUN.

## <a name="objectives"></a>Objetivos

* Aprender cómo crear una aplicación de PUN
* Aprender cómo buscar e importar los recursos de PUN
* Aprender a conectar el proyecto de Unity a la aplicación de PUN

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Primero, debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de las instrucciones [Adición de la interacción de la mano a un objeto](mr-learning-base-02.md#adding-hand-interaction-to-an-object) y [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*
2. [Cambiar la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform)
3. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importación de Mixed Reality Toolkit y configuración del proyecto de Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Crear la escena y configurar MRTK](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk), y asignar un nombre adecuado a la escena; por ejemplo, *MultiUserCapabilities*

A continuación, siga las instrucciones de la sección [Cambio de la opción de visualización de reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para:

1. Cambiar el **perfil de configuración de MRTK** por **DefaultHoloLens2ConfigurationProfile**.
1. Cambiar las **opciones de visualización de la malla de reconocimiento espacial** a **Oclusión**.

## <a name="enabling-additional-capabilities"></a>Habilitación de funcionalidades adicionales

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busca la sección **Player** >  **Publishing Settings** (Jugador > Configuración de publicación):

![Player Settings (Configuración del reproductor) de Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

En **Configuración de publicación**, desplácese hasta la sección **Funcionalidades** y compruebe que las funcionalidades **InternetClient**, **Microphone**, **SpatialPerception** y **GazeInput** que habilitó durante el paso anterior titulado [Configuración del proyecto de Unity](mr-learning-base-02.md#configuring-the-unity-project), estén habilitadas.

A continuación, habilite las siguientes funcionalidades adicionales:

* Funcionalidad **InternetClientServer**
* Funcionalidad **PrivateNetworkClientServer**

![Capabilities Settings (Configuración de funcionalidades) de Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a>Importación de los recursos del tutorial

Agregue el SDK de Azure Spatial Anchors V2.7.1 al proyecto de Unity. Para agregar los paquetes, siga este [tutorial](/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage).


Descarga e **importa** los siguientes paquetes personalizados de Unity **en el orden en que aparecen**:
 
* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.7.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.7.2.unitypackage)
* [MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.7.2/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.7.2.unitypackage)

Después de importar los recursos del tutorial, la ventana Project (Proyecto) debería tener un aspecto similar al siguiente:

![Ventanas Hierarchy (Jerarquía), Scene (Escena) y Project (Proyecto) después de importar los recursos del tutorial](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> Para repasar cómo se importa un paquete personalizado de Unity, consulte las instrucciones de [Importación de los recursos del tutorial](mr-learning-base-04.md#importing-the-tutorial-assets).

> [!NOTE]
> Después de importar el paquete de recursos del tutorial de MultiUserCapabilities, verás varios errores con el código [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) en la ventana de la consola en los que se indicará que falta el tipo o el espacio de nombres. Este comportamiento es el esperado y se resolverá en la sección siguiente cuando importes los recursos de PUN.

## <a name="importing-the-pun-assets"></a>Importación de recursos de PUN

En el menú de Unity, seleccione **Ventana** > **Asset Store** (Almacén de recursos) para abrir la ventana del almacén de recursos, busque y seleccione **PUN 2 - FREE** de Exit Games y haga clic en el botón **Descargar** para descargar el paquete de recursos en su cuenta de Unity.

Una vez completada la descarga, haz clic en el botón **Importar** para abrir la ventana Import Unity Package (Importar paquete de Unity):

![Asset Store (Almacén de recursos) de Unity con PUN 2 - Free](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![Ventana de importación de Unity con PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

Una vez que Unity haya completado el proceso de importación, se mostrará la ventana Pun Wizard (Asistente para PUN) con el menú de configuración de PUN cargado. Por ahora, puedes omitir o cerrar esta ventana:

![Ventana de importación de Unity con PUN Setup (Instalación de PUN)](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a>Creación de la aplicación de PUN

En esta sección, creará una cuenta de Photon, si aún no tiene ninguna, y creará una nueva aplicación de PUN.

Ve al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">panel</a> de Photon e inicia sesión si ya tienes una cuenta que quieras usar. De lo contrario, haz clic en el vínculo **Crear una** y sigue las instrucciones para registrar una cuenta nueva:

![Página de inicio de sesión de Photon](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

Una vez que hayas iniciado sesión, haz clic en el botón **Crear una nueva aplicación**:

![Página de bienvenida del panel de Photon](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

En la página Crear una nueva aplicación, escribe los valores siguientes:

* En Photon Type (Tipo de Photon), seleccione PUN.
* En Nombre, escribe un nombre adecuado, por ejemplo, _Tutoriales de MRTK_.
* En Descripción, puedes escribir una descripción adecuada.
* En URL, deja el campo vacío.

A continuación, haga clic en el botón **Crear** para crear la nueva aplicación:

![Página de creación de aplicaciones de Photon](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

Una vez que Photon haya finalizado el proceso de creación, la nueva aplicación de PUN se mostrará en el panel:

![Página de la aplicación de Photon](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a>Conexión del proyecto de Unity con la aplicación de PUN

En esta sección, conectará el proyecto de Unity a la aplicación de PUN que creó en la sección anterior.

En el panel de Photon, haz clic en el campo **Id. de la aplicación** para mostrar el identificador de la aplicación y, a continuación, cópialo en el portapapeles:

![Página de la aplicación de Photon con el identificador de aplicación seleccionado](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

En el menú de Unity, selecciona **Ventana** > **Photon Unity Networking** > **Pun Wizard** (Asistente para PUN) para abrir la ventana del asistente para PUN, haz clic en el botón **Proyecto de instalación** para abrir el menú de configuración de PUN y configúralo de la siguiente manera:

* En el campo **AppId or Email** (Id. de la aplicación o correo electrónico), pega el identificador de la aplicación de PUN que copiaste en el paso anterior

A continuación, haz clic en el botón **Proyecto de instalación** para aplicar el id. de la aplicación:

![Ventana PUN Setup (Instalación de PUN) de Unity con AppId rellenado](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

Una vez que Unity termine el proceso de configuración de PUN, se mostrará el mensaje **Listo** en el menú de configuración de PUN. Asimismo, se seleccionará automáticamente el recurso **PhotonServerSettings** en la ventana Proyecto para que sus propiedades se muestren en la ventana Inspector:

![Ventana PUN Setup (Instalación de PUN) de Unity con el proyecto de instalación aplicado](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a>Enhorabuena

Creó correctamente una aplicación de PUN y la conectó al proyecto de Unity. El siguiente paso consiste en permitir las conexiones con otros usuarios para que varios usuarios puedan verse entre sí.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Conexión de varios usuarios](mr-learning-sharing-03.md)