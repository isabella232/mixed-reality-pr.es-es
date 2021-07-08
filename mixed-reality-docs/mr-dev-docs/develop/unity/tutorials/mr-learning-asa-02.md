---
title: Introducción a Azure Spatial Anchors
description: Siga este curso para aprender a usar Azure Spatial Anchors dentro para anclar objetos en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: eddde9b827dcf2a2f054f48a50f38946e5d98533
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175562"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introducción a Azure Spatial Anchors

En este tutorial, explorará los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors, y para crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.

## <a name="objectives"></a>Objetivos

* Aprender los aspectos básicos del desarrollo con Azure Spatial Anchors para HoloLens 2
* Aprender a crear anclajes espaciales y a capturarlos desde Azure

## <a name="creating-and-preparing-the-unity-project"></a>Creación y preparación del proyecto de Unity

En esta sección, crearás un nuevo proyecto de Unity y lo prepararás para el desarrollo con MRTK.

Primero, debe seguir las instrucciones de [Inicialización de su proyecto e implementación de su primera aplicación](mr-learning-base-02.md), a excepción de la sección [Compilación de la aplicación para el dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluyen los pasos siguientes:

1. [Crear el proyecto de Unity](mr-learning-base-02.md#creating-the-unity-project) y asignarle un nombre adecuado; por ejemplo, *MRTK Tutorials*
2. [Cambiar la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform)
3. [Importar los recursos esenciales de TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Importación de Mixed Reality Toolkit y configuración del proyecto de Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Crear y configurar la escena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) y asignarle un nombre adecuado; por ejemplo, *AzureSpatialAnchors*

A continuación, siga las instrucciones de [Cambio de la opción de visualización del reconocimiento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para asegurarse de que el perfil de configuración de MRTK de la escena sea **DefaultHoloLens2ConfigurationProfile** y cambie las opciones de presentación de la malla de reconocimiento espacial a **Occlusion** (Oclusión).

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Instalación de paquetes de Unity integrados e importación de los recursos del tutorial

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.

En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** y, a continuación, haga clic y arrastre los siguientes objetos prefabricados a la ventana Hierarchy (Jerarquía) para agregarlos a la escena:

* Objeto prefabricado **ButtonParent**
* Objeto prefabricado **DebugWindow**
* Objeto prefabricado **Instructions**
* Objeto prefabricado **ParentAnchor**

![Unity con los objetos prefabricados recién agregados seleccionados](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Si le molestan los grandes iconos de la escena; por ejemplo, los grandes iconos "T" enmarcados, puede ocultarlos. Para hacerlo, desactive los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">gizmos</a>, como se muestra en la imagen anterior.

Seleccione el objeto **MixedRealityToolkit** en la ventana Hierarchy (Jerarquía) y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar los componentes siguientes:

* AR Anchor Manager (Script) (Administrador de delimitadores de AR [script])
* DisableDiagnosticsSystem (Script)

![Objeto MixedRealityToolkit de Unity con los componentes AR Anchor Manager y DisableDiagnosticsSystem agregados ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> Hay un problema conocido con ASA v2.9.0 y v2.10.0-preview.1 que requiere que se sitúen en la escena dos objetos adicionales. Use el botón **Add Component** (Agregar componente) de la ventana Inspector para agregar AR Camera Manager (Script) (Administrador de la cámara de AR [script]) y AR Session (Script) (Sesión de AR [script]) al objeto **MixedRealityToolkit.** Asegúrese de deshabilitar la cámara que se crea automáticamente al agregar AR Camera Manager (Script) (Administrador de la cámara de AR [script]); para ello, desactive la casilla situada junto al objeto Camera en la ventana Inspector. Este problema se solucionará en la versión completa de ASA v2.10.0.
> 

> [!NOTE]
> Cuando se agregue el componente AR Anchor Manager (Script) (Administrador de anclaje de AR [script]), se agregará automáticamente el componente AR Session Origin (Script) (Origen de la sesión de AR [script]) según lo requiere el componente AR Anchor Manager (Script).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Configuración de los botones para el funcionamiento de la escena

En esta sección, agregará scripts a la escena para crear una serie de eventos de botón que muestren los aspectos básicos del comportamiento en la aplicación de los anclajes locales y Azure Spatial Anchors.

En la ventana Hierarchy (Jerarquía), expanda el objeto **ButtonParent** y seleccione el primer objeto secundario denominado **StartAzureSession**, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StartAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del botón StartAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-1.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **StopAzureSession**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **StopAzureSession ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del botón StopAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-2.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **CreateAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **CreateAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función CreateAzureAnchor ().

![Unity con el evento OnClick del botón CreateAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-3.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **RemoveLocalAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **RemoveLocalAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Asigne el objeto **ParentAnchor** al campo vacío **None (Game Object)** (Ninguno [objeto de juego]) para convertirlo en el argumento de la función RemoveLocalAnchor ().

![Unity con el evento OnClick del botón RemoveLocalAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-4.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **FindAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **FindAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del botón FindAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-5.png)

En la ventana Hierarchy (Jerarquía), seleccione el siguiente botón denominado **DeleteAzureAnchor**, a continuación, en la ventana Inspector, configure el componente **Button Config Helper (script)** en el evento **On Click ()** de la siguiente manera:

* Asigne el objeto **ParentAnchor** al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **AnchorModuleScript** > **DeleteAzureAnchor ()** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.

![Unity con el evento OnClick del botón DeleteAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Conexión de la escena al recurso de Azure

En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** . Configure la sección **Credentials** (Credenciales) con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mr-learning-asa-01.md#prerequisites) de esta serie de tutoriales:

* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.
* En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.
* En el campo **Spatial Anchors Account Domain** (Dominio de la cuenta de Spatial Anchors), pegue el valor de **Account Domain** (Dominio de cuenta) de la cuenta de Azure Spatial Anchors.

![Unity con Spatial Anchor Manager (Administrador de anclaje espacial) configurado](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Prueba de los comportamientos básicos de Azure Spatial Anchors

Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad de Azure Spatial Anchors, debe compilar el proyecto e implementar la aplicación en el dispositivo.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Cuando la aplicación se ejecute en el dispositivo, siga las instrucciones en pantalla que se muestran en el panel de instrucciones del tutorial de Azure Spatial Anchors:

1. Mueva el cubo a una ubicación diferente.
2. Inicie una sesión de Azure.
3. Cree un anclaje de Azure (se crea un anclaje en la ubicación del cubo).
4. Detenga la sesión de Azure.
5. Quite el anclaje local (permite que el usuario mueva el cubo).
6. Mueva el cubo a otro lugar.
7. Inicie una sesión de Azure.
8. Busque el anclaje de Azure (posiciona el cubo en la ubicación del paso 3).
9. Elimine el anclaje de Azure.
10. Detenga la sesión de Azure.

![Unity con el objeto Instructions (Instrucciones) seleccionado](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> Azure Spatial Anchors usa Internet para guardar y cargar los datos de anclaje, por lo que debe asegurarse de que el dispositivo esté conectado a Internet.

## <a name="anchoring-an-experience"></a>Anclaje de una experiencia

En las secciones anteriores, has aprendido los aspectos básicos de Azure Spatial Anchors. Hemos usado un cubo para representar y visualizar el objeto de juego principal con el anclaje adjunto. En esta sección, aprenderás a anclar una experiencia completa colocándola como elemento secundario del objeto ParentAnchor.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **ParentAnchor** y, en la ventana Inspector, configure los componentes **Transform** de la manera siguiente:

* Cambie **Scale X** (Escala X) a 1.1.
* Cambie **Scale Z** (Escala Z) a 1.1.

![Unity con el objeto ParentAnchor seleccionado, colocado y escalado](images/mr-learning-asa/asa-02-section8-step1-1.png)

En la ventana Project (Proyecto), desplácese hasta la carpeta **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** > **Rover** y haga clic y arrastre el objeto prefabricado **RoverExplorer_Complete** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena:

![Unity con el objeto prefabricado RoverExplorer_Complete recién agregado seleccionado](images/mr-learning-asa/asa-02-section8-step1-2.png)

Con el objeto RoverModule_Complete recién agregado todavía seleccionado en la ventana Hierarchy (Jerarquía), arrástralo sobre el objeto **ParentAnchor** para convertirlo en un elemento secundario del objeto ParentAnchor:

![Unity con el objeto RoverExplorer_Complete establecido como elemento secundario de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

Si vuelve a compilar el proyecto e implementar la aplicación en el dispositivo, ahora podrá cambiar la posición de toda la experiencia del explorador de róver moviendo el cubo cuyo tamaño se ha cambiado.

> [!TIP]
> Hay una variedad de flujos de experiencia del usuario para cambiar la posición de las experiencias, incluido el uso de un objeto de cambio de posición (como el cubo que se usa en este tutorial), el uso de un botón para activar o desactivar el control de límites alrededor de la experiencia, el uso de gizmos de posición y rotación, etc.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido los aspectos básicos de Azure Spatial Anchors. El tutorial le ha proporcionado varios botones que le permiten explorar los distintos pasos necesarios para iniciar y detener una sesión de Azure Spatial Anchors. Además de crear, cargar y descargar Azure Spatial Anchors en un único dispositivo.

En el siguiente tutorial, aprenderá a guardar los identificadores de anclaje de Azure en HoloLens 2 para su recuperación, incluso después de reiniciar la aplicación, así como la forma de transferir los identificadores de anclaje entre varios dispositivos para lograr la alineación espacial.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 3. Guardado, recuperación y uso compartido de Azure Spatial Anchors](mr-learning-asa-03.md)
