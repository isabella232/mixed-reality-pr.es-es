---
title: Uso de los comandos de voz
description: En este curso se muestra cómo configurar, crear y usar los comandos de voz en las aplicaciones de realidad mixta con Mixed Reality Toolkit (MRTK).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, speech commands, voice input
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982955"
---
# <a name="9-using-speech-commands"></a>9. Uso de los comandos de voz

En este tutorial, aprenderá a crear comandos de voz y a controlarlos de forma global. También aprenderá a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.

## <a name="objectives"></a>Objetivos

* Aprender a crear comandos de voz
* Aprender a controlar los comandos de voz global y localmente

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a>Creación de comandos de voz

En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit**, a continuación, en la ventana Inspector, seleccione MixedRealityToolkit > pestaña **Input** (Entrada) y siga los pasos a continuación:

* Expanda la sección **Speech** (Voz).
* Clone **DefaultMixedRealitySpeechCommandsProfile** y asígnele un nombre adecuado, por ejemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_.
* Verifique que **Start Behaviour** (Iniciar comportamiento) está establecido en **Auto Start** (Inicio automático).

![Creación de comandos de voz](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [Configuración de los perfiles de MRTK](mr-learning-base-03.md).

En Speech (Voz) > sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) cuatro veces para agregar cuatro nuevos comandos de voz a la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escriba las frases siguientes:

* Enable Indicator (Habilitar indicador)
* Enable Tap to Place (Habilitar pulsar para colocar)
* Enable Bounds Control (Habilitar control de límites)
* Disable Bounds Control (Deshabilitar control de límites)

![Adición de nuevos comandos de voz](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Si el equipo no tiene micrófono, puede asignar un KeyCode a los comandos de voz, lo que le permitirá desencadenarlos cuando se presione la tecla correspondiente.

## <a name="controlling-speech-commands"></a>Control de los comandos de voz

En la ventana Project (Proyecto), vaya a la carpeta **Packages** > **Mixed Reality Toolkit Foundation** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** (Paquetes > Mixed Reality Toolkit Foundation > SDK > Características > Experiencia del usuario > Objetos prefabricados > Información sobre herramientas) para buscar los objetos prefabricados de información sobre herramientas:

![Apertura de la carpeta de información sobre herramientas](images/mr-learning-base/base-09-section3-step1-1.png)

En la ventana Hierarchy (Jerarquía), haga clic con el botón derecho en un lugar vacío y seleccione **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena.

Asigna al objeto el nombre **SpeechInputHandler_Global** y, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo de la siguiente manera:

* **Desactive** la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe el objeto con el componente SpeechInputHandler para desencadenar el comando de voz.
* En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.

![Configuración del componente de controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-2.png)

En el componente SpeechInputHandler, haga clic en el icono pequeño **+** tres veces para agregar tres elementos de palabra clave:

![Adición de elementos de palabra clave al controlador de entrada de voz](images/mr-learning-base/base-09-section3-step1-3.png)

Expanda **Element 0** (Elemento 0) y configúrelo de la siguiente manera:

* En el campo **Keyword** (Palabra clave), escriba **Enable Indicator** (Habilitar indicador) para hacer referencia al comando de voz Enable Indicator que creó en la sección anterior.
* Haga clic en el icono **+** pequeño para agregar un evento.
* En la ventana Hierarchy (Jerarquía), asigne el objeto **Indicator** al campo **None (Object)** (Ninguno objeto).
* En la lista desplegable **No Function** (Ninguna función), seleccione **GameObject** > **SetActive (bool)** para establecer esta función como la acción que se va a ejecutar cuando se desencadene el evento.
* Marque la casilla del argumento para que esté **activada**.

![Configuración del elemento de palabra clave 0](images/mr-learning-base/base-09-section3-step1-4.png)

Expanda **Element 1** (Elemento 1) y configúrelo de la siguiente manera:

* En el campo **Keyword** (Palabra clave), escriba **Enable Bounds Control** (Habilitar control de límites) para hacer referencia al comando Enable Bounds Control que creó en la sección anterior.
* Haga clic en el icono **+** pequeño para agregar un evento.
* En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).
* En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento
* Marque la casilla del argumento para que esté **activada**.
* Haga clic en el icono **+** pequeño para agregar otro evento.
* En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).
* En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Marque la casilla del argumento para que esté **activada**.

![Configuración del elemento de palabra clave 1](images/mr-learning-base/base-09-section3-step1-5.png)

Expanda **Element 2** (Elemento 2) y configúrelo de la siguiente manera:

* En el campo **Keyword** (Palabra clave), escriba **Disable Bounds Control** (Deshabilitar control de límites) para hacer referencia al comando Disable Bounds Control que creó en la sección anterior.
* Haga clic en el icono **+** pequeño para agregar un evento.
* En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).
* En la lista desplegable **No Function** (Ninguna función), seleccione **BoundsControl** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento
* Verifique que la casilla del argumento esté **desactivada**.
* Haga clic en el icono **+** pequeño para agregar otro evento.
* En la ventana Hierarchy (Jerarquía), asigne el objeto **RoverExplorer** al campo **None (Object)** (Ninguno objeto).
* En la lista desplegable **No Function** (Ninguna función), seleccione **ObjectManipulator** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Verifique que la casilla del argumento esté **desactivada**.

![Configuración del elemento de palabra clave 2](images/mr-learning-base/base-09-section3-step1-6.png)

En la ventana Hierarchy (Jerarquía), seleccione RoverExplorer > objeto **RoverAssembly** y, a continuación, en la ventana Inspector, use el botón **Add Component** (Agregar componente) para agregar el componente **SpeechInputHandler** y configúrelo del modo siguiente:

* Verifique que la casilla **Is Focus Required** (Se requiere foco) esté **activada** para exigir que el usuario observe el objeto con el componente SpeechInputHandler, es decir, RoverAssembly, para desencadenar el comando de voz.
* En la ventana Project (Proyecto), asigne el objeto prefabricado **SpeechConfirmation Tooltip** (Información sobre herramientas de SpeechConfirmation) al campo **Confirmation Tooltip Prefab** (Objeto prefabricado de información sobre herramientas de confirmación de voz) para que este objeto prefabricado aparezca cuando se reconozca un comando de voz.

![Adición del controlador de entrada de voz al ensamblado del róver](images/mr-learning-base/base-09-section3-step1-7.png)

En el componente SpeechInputHandler, haga clic en el icono **+** pequeño para agregar un elemento de palabra clave, expanda el elemento recién creado y configúrelo de la siguiente manera:

* En el campo **Keyword** (Palabra clave), escriba **Enable Tap to Place** (Habilitar pulsar para colocar) para hacer referencia al comando de voz Enable Tap to Place que creó en la sección anterior.
* Haga clic en el icono **+** pequeño para agregar un evento.
* En la ventana Hierarchy (Jerarquía), asigne el propio objeto, es decir, el mismo objeto **RoverAssembly**, al campo **None (Object)** (Ninguno [objeto]).
* En la lista desplegable **No Function** (Ninguna función), seleccione **TapToPlace** > **bool enabled** para actualizar el valor de esta propiedad cuando se desencadene el evento.
* Marque la casilla del argumento para que esté **activada**.

![Configuración del controlador de entrada de voz en el ensamblado del róver](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a crear comandos de voz y a controlarlos de forma global. También ha aprendido a controlar comandos de voz locales que requieren que el usuario vea el objeto que controla el comando de voz.

Esto también concluye la serie de [tutoriales de introducción](mr-learning-base-01.md). A través de estos tutoriales, ha creado correctamente una experiencia de realidad mixta completa desde cero con MRTK.

En las siguientes dos series de tutoriales, [Tutoriales de Azure Spatial Anchors](mr-learning-asa-01.md) y [Tutoriales de funcionalidades para varios usuarios](mr-learning-sharing-01.md), primero aprenderá a integrar Azure Spatial Anchors en el proyecto para anclar la experiencia del explorador de róver que creó en el mundo real. A continuación, aprenderá a agregar funcionalidades de varios usuarios al proyecto para compartir movimientos de usuarios y objetos en tiempo real.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, la siguiente tarea consiste en familiarizarse con los principales bloques de creación de aplicaciones de realidad mixta.

> [!div class="nextstepaction"]
> [Interacciones básicas](../../../out-of-scope/mrtk-101.md)

Puede volver a los [puntos de control de desarrollo de Unity](../unity-development-overview.md#1-getting-started) en cualquier momento.