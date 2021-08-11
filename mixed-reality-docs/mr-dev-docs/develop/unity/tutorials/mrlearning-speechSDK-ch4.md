---
title: Configuración de reconocimiento de intenciones y comprensión del lenguaje natural
description: Complete este curso para aprender a configurar la comprensión del lenguaje natural y la intención en las aplicaciones de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, MRTK, mixed reality toolkit, UWP, Azure spatial anchors, speech recognition, Windows 10, LUIS, LUIS portal, intent, entities, utterances, natural language understanding
ms.localizationpriority: high
ms.openlocfilehash: fab521f51f653f3d7f381468cfc045c8c8c0f0c79354c5bf41f9531d0178a193
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207136"
---
# <a name="4-setting-up-intent-and-natural-language-understanding"></a>4. Configuración de reconocimiento de intenciones y comprensión del lenguaje natural

En este tutorial, explorarás el reconocimiento de la intención del servicio Voz de Azure. El reconocimiento de la intención te permite equipar nuestra aplicación con comandos de voz con tecnología de IA que permite a los usuarios indicar comandos de voz no específicos y conseguir, igualmente, que les entienda el sistema.

## <a name="objectives"></a>Objetivos

* Aprender a configurar la intención, las entidades y las expresiones en el portal de LUIS
* Aprender a implementar la comprensión del lenguaje natural y la intención en nuestra aplicación

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventaja Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]):

![mrlearning-speech 1](images/mrlearning-speech/tutorial4-section1-step1-1.png)

En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > Objetos prefabricados > RocketLauncher), arrastra el objeto prefabricado **RocketLauncher_Complete** a la ventana Hierarchy (Jerarquía) y, a continuación, colócalo en una ubicación adecuada; por ejemplo, delante de la cámara:

* Transforma el valor de **Position** (Posición) X = 0, Y = 0,4, Z = 1
* Transforma el valor de **Rotation** (Giro) X = 0, Y = 90, Z = 0

![mrlearning-speech 2](images/mrlearning-speech/tutorial4-section1-step1-2.png)

En la ventana Hierarchy (Jerarquía), selecciona de nuevo el objeto **Lunarcom**, expande el objeto **RocketLauncher_Complete** > **Button** (Botón) y asigna cada uno de los objetos secundarios del objeto **Buttons** (Botones) al campo **Lunar Launcher Buttons** (Botones del lanzacohetes lunar):

![mrlearning-speech 3](images/mrlearning-speech/tutorial4-section1-step1-3.png)

## <a name="creating-the-azure-language-understanding-resource"></a>Creación del recurso de Azure Language Understanding

En esta sección, crearás un recurso de predicción de Azure para la aplicación de Language Understanding Intelligent Service (LUIS) que crearás en la próxima sección.

Inicia sesión en <a href="https://portal.azure.com" target="_blank">Azure</a> y haz clic en **Crear un recurso**. A continuación, busca y selecciona **Language Understanding**:

![mrlearning-speech 4](images/mrlearning-speech/tutorial4-section2-step1-1.png)

Haz clic en el botón **Crear** para crear una instancia de este servicio:

![mrlearning-speech 5](images/mrlearning-speech/tutorial4-section2-step1-2.png)

En la página Crear, haz clic en la opción **Predicción** y escribe los valores siguientes:

* En **Suscripción**, selecciona **Free Trail** (Prueba gratuita) si tienes una suscripción de prueba. De lo contrario, selecciona una de las otras suscripciones.
* Para **Grupo de recursos**, haga clic en el vínculo **Crear nuevo**, escriba un nombre adecuado; por ejemplo, *MRKT-Tutorials* y, a continuación, haga clic en **Aceptar**.

![mrlearning-speech 6](images/mrlearning-speech/tutorial4-section2-step1-3.png)

> [!NOTE]
> En el momento de redactar este documento, no es necesario crear un recurso de creación porque se generará automáticamente una clave de prueba de creación en LUIS cuando crees Language Understanding Intelligent Service (LUIS) en la sección siguiente.

> [!TIP]
> Si ya tienes otro grupo de recursos adecuado en tu cuenta de Azure; por ejemplo, si completaste el tutorial de [Azure Spatial Anchors](mr-learning-asa-01.md), puedes usar este grupo de recursos en lugar de crear uno nuevo.

Mientras sigues en la página Crear, escribe los valores siguientes:

* En **Nombre**, escribe un nombre adecuado para el servicio; por ejemplo, *MRTK-tutoriales-AzureSpeechServices*
* Para **Ubicación de la predicción**, elige una ubicación cercana a la ubicación física de los usuarios de la aplicación; por ejemplo,  *(EE. UU.) Oeste de EE. UU.*
* Para **Plan de tarifa de predicción**, para los fines de este tutorial, selecciona **F0 (5 llamadas por segundo, 10 000 llamadas al mes)** .

![mrlearning-speech 7](images/mrlearning-speech/tutorial4-section2-step1-4.png)

A continuación, haga clic en la pestaña **Revisar y crear**, revise los detalles y haga clic en el botón **Crear** situado en la parte inferior de la página para crear el recurso, así como el nuevo grupo de recursos, si configuró alguno para su creación:

![mrlearning-speech 8](images/mrlearning-speech/tutorial4-section2-step1-5.png)

> [!NOTE]
> Después de hacer clic en el botón Crear, tendrás que esperar a que se cree el servicio, lo que puede tardar unos minutos.

Una vez completado el proceso de creación de recursos, se mostrará el mensaje **Se completó la implementación**:

![mrlearning-speech 9](images/mrlearning-speech/tutorial4-section2-step1-6.png)

## <a name="creating-the-language-understanding-intelligent-service-luis"></a>Creación de Language Understanding Intelligent Service (LUIS)

En esta sección, crearás una aplicación de LUIS, configurarás y entrenarás su modelo de predicción y lo conectará al recurso de predicción de Azure que creaste en el paso anterior.

En concreto, crearás una intención: si el usuario dice que se debe realizar una acción, la aplicación desencadenará el evento Interactable.OnClick() en uno de los tres botones rojos de la escena, dependiendo del botón al que haga referencia el usuario.

Por ejemplo, si el usuario dice **go ahead and launch the rocket** (adelante, lanza el cohete), la aplicación predecirá que **adelante** significa que se debe realizar alguna **acción** y que el evento Interactable.OnClick() de **destino** está en el botón **launch** (lanzar).

Los principales pasos que debes seguir para lograrlo son:

1. Crear una aplicación de LUIS
2. Crear intenciones
3. Crear expresiones de ejemplo
4. Crear entidades
5. Asignar entidades a las expresiones de ejemplo
6. Entrenar, probar y publicar la aplicación
7. Asignar un recurso de predicción de Azure a la aplicación

### <a name="1-create-a-luis-app"></a>1. Crear una aplicación de LUIS

Con la misma cuenta de usuario que usaste para crear el recurso de Azure en la sección anterior, inicia sesión en <a href="https://www.luis.ai" target="_blank">LUIS</a>, selecciona tu país y acepta los términos de uso. En el paso siguiente, cuando se te pida **vincular la cuenta de Azure**, elige **Continuar usando la clave de prueba** para usar un recurso de creación de Azure en su lugar.

> [!NOTE]
> Si ya te has registrado en LUIS y ha expirado la clave de prueba de creación, puedes consultar la documentación [Migración a una clave de creación de recursos de Azure](/azure/cognitive-services/luis/luis-migration-authoring) para cambiar el recurso de creación de LUIS a Azure.

Una vez iniciada la sesión, haga clic en **Nueva aplicación** y especifique los valores siguientes en la ventana emergente **Crear una aplicación**:

* En **Nombre**, escribe un nombre adecuado; por ejemplo, *MRTK Tutorials - AzureSpeechServices*.
* En **Referencia cultural**, selecciona **Inglés**
* En **Descripción**, puedes escribir una descripción adecuada.
* En **Recurso de predicción**, seleccione en la lista desplegable el recurso de predicción creado en Azure Portal.

A continuación, haz clic en el botón **Listo** para crear la aplicación:

![mrlearning-speech 10](images/mrlearning-speech/tutorial4-section3-step1-1.png)

Una vez creada la aplicación, se te dirigirá a su página **Panel**:

![mrlearning-speech 11](images/mrlearning-speech/tutorial4-section3-step1-2.png)

### <a name="2-create-intents"></a>2. Crear intenciones

Desde la página Panel, vaya a la página Compilación > Activos de la aplicación > **Intenciones**, haga clic en **Crear** y escriba el siguiente valor en la ventana emergente **Crear intención**:

* En **Nombre de la intención**, escribe **PressButton**.

A continuación, haz clic en el botón **Listo** para crear la nueva intención:

![mrlearning-speech 12](images/mrlearning-speech/tutorial4-section3-step2-1.png)

> [!CAUTION]
> Para los fines de este tutorial, el proyecto de Unity hará referencia a esta intención por su nombre, "PressButton". Por lo tanto, es muy importante que asignes exactamente el mismo nombre a la intención.

Una vez creada la intención, se te dirigirá a su página:

![mrlearning-speech 14](images/mrlearning-speech/tutorial4-section3-step2-2.png)

### <a name="3-create-example-utterances"></a>3. Crear expresiones de ejemplo

En la lista **Expresión de ejemplo** de la intención **PressButton**, agrega las siguientes expresiones de ejemplo:

* activate launch sequence (activar secuencia de lanzamiento)
* show me a placement hint (mostrar sugerencia de selección de ubicación)
* initiate the launch sequence (iniciar secuencia de lanzamiento)
* press placement hints button (presionar botón de sugerencias)
* give me a hint (proporcionar sugerencia)
* push the launch button (presionar botón de lanzamiento)
* i need a hint (necesito una sugerencia)
* press the reset button (presionar botón de restablecimiento)
* time to reset the experience (hora de restablecer la experiencia)
* go ahead and launch the rocket (adelante, lanza el cohete)

Una vez agregadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:

![mrlearning-speech 15](images/mrlearning-speech/tutorial4-section3-step3-1.png)

> [!CAUTION]
> Para los fines de este tutorial, el proyecto de Unity hará referencia a las palabras "hint" (sugerencia), "hints" (sugerencias), "reset" (restablecimiento) y "launch" (lanzar). Por lo tanto, es muy importante que escribas estas palabras exactamente de la misma manera.

### <a name="4-create-entities"></a>4. Crear entidades

Desde la página de la intención PressButton, vaya a la página Compilación > Activos de la aplicación > **Entidades**, haga clic en **Crear** y escriba los valores siguientes en la ventana emergente **Crear una nueva entidad**:

* En **Nombre de entidad**, escribe **Action**.
* En **Tipo de entidad**, seleccione **Machine learned** (De aprendizaje automático).

A continuación, haga clic en el botón **Crear** para crear la nueva entidad:

![mrlearning-speech 16](images/mrlearning-speech/tutorial4-section3-step4-1.png)

**Repite** el paso anterior para crear otra entidad denominada **Target**. De este modo, tendrás dos entidades denominadas Action y Target:

![mrlearning-speech 17](images/mrlearning-speech/tutorial4-section3-step4-2.png)

> [!CAUTION]
> Para los fines de este tutorial, el proyecto de Unity hará referencia a estas entidades por su nombre, "Action" y "Target". Por lo tanto, es muy importante que asignes exactamente el mismo nombre a las entidades.

### <a name="5-assign-entities-to-the-example-utterances"></a>5. Asignar entidades a las expresiones de ejemplo

Desde la página Entidades, vuelve a la página de la intención **PressButton**.

De vuelta a la página de la intención PressButton, haz clic en la palabra **go** y, después, en la palabra **ahead** y, a continuación, selecciona **Action (Simple)** en el menú contextual para etiquetar **go ahead** como valor de la entidad **Action**:

![mrlearning-speech 18](images/mrlearning-speech/tutorial4-section3-step5-1.png)

Ahora, la frase **go ahead** está definida como un valor de la entidad **Action**. Ahora puede ver el valor de la entidad de acción bajo las palabras go ahead:

![mrlearning-speech 19](images/mrlearning-speech/tutorial4-section3-step5-2.png)

> [!NOTE]
> La línea roja que aparece debajo de la etiqueta en la imagen anterior indica que el valor de la entidad no se ha predicho, lo que se resolverá al entrenar el modelo en la siguiente sección.

A continuación, haz clic en la palabra **launch** y selecciona **Target (Simple)** en el menú contextual emergente para etiquetar **launch** como valor de la entidad **Target**:

![mrlearning-speech 20](images/mrlearning-speech/tutorial4-section3-step5-3.png)

Ahora, la palabra **launch** está definida como un valor de la entidad **Target**. Ya aparece el valor de la entidad Target bajo la palabra launch:

![mrlearning-speech 21](images/mrlearning-speech/tutorial4-section3-step5-4.png)

Ahora, la expresión de ejemplo de la intención PressButton "go ahead and launch the rocket" (adelante, lanza el cohete) se ha configurado para predecirse como se indica a continuación:

* Intención: PressButton
* Entidad Action: go ahead
* Entidad Target: launch

**Repite** el proceso anterior de dos pasos para asignar una etiqueta de entidad Action y Target a cada una de las expresiones de ejemplo, teniendo en cuenta que las siguientes palabras se deben etiquetar como entidades **Target**:

* **hint** (destinada a HintsButton en el proyecto de Unity)
* **hints** (destinada a HintsButton en el proyecto de Unity)
* **reset** (destinada a ResetButton en el proyecto de Unity)
* **launch** (destinada a LaunchButton en el proyecto de Unity)

Una vez etiquetadas todas las expresiones de ejemplo, la página de la intención PressButton debería tener un aspecto similar al siguiente:

![mrlearning-speech 22](images/mrlearning-speech/tutorial4-section3-step5-5.png)

### <a name="6-train-test-and-publish-the-app"></a>6. Entrenar, probar y publicar la aplicación

Para entrenar la aplicación, haz clic en el botón **Entrenar** y espera a que se complete el proceso de entrenamiento:

![mrlearning-speech 23](images/mrlearning-speech/tutorial4-section3-step6-1.png)

> [!NOTE]
> Como puedes ver en la imagen anterior, se han quitado las líneas rojas de todas las etiquetas, lo que indica que se han predicho todos los valores de entidad. Observa también que el icono de estado situado a la izquierda del botón Entrenar ha cambiado de color rojo a verde.

Cuando se acabe de procesar el entrenamiento, haz clic en el botón **Probar**, escribe **go ahead and launch the rocket** y presiona la tecla Entrar:

![mrlearning-speech 24](images/mrlearning-speech/tutorial4-section3-step6-2.png)

Una vez procesada la expresión de prueba, haz clic en **Inspeccionar** para ver el resultado de la prueba:

* Intención: PressButton (con una certeza del 98,5 %)
* Entidad Action: go ahead
* Entidad Target: launch

![mrlearning-speech 25](images/mrlearning-speech/tutorial4-section3-step6-3.png)

Para publicar la aplicación, haga clic en el botón **Publicar** de la parte superior derecha y, a continuación, en la ventana emergente **Elige el espacio de publicación y la configuración**, seleccione **Producción** y haga clic en el botón **Listo**:

![mrlearning-speech 26](images/mrlearning-speech/tutorial4-section3-step6-4.png)

Espera hasta que se complete el proceso de publicación:

![mrlearning-speech 27](images/mrlearning-speech/tutorial4-section3-step6-5.png)

Vaya a Administrar > Configuración de la aplicación > página **Recursos de Azure**. La página de recursos de Azure debería tener un aspecto similar a este:

![mrlearning-speech 28](images/mrlearning-speech/tutorial4-section3-step6-6.png)

## <a name="connecting-the-unity-project-to-the-luis-app"></a>Conexión del proyecto de Unity con la aplicación de LUIS

En la página Administrar > Configuración de la aplicación > **Recursos de Azure**, haz clic en el icono **copiar** para copiar el **Ejemplo de consulta**:

![mrlearning-speech 29](images/mrlearning-speech/tutorial4-section4-step1-1.png)

Desde el proyecto de Unity, en la ventana Hierarchy (Jerarquía), selecciona el objeto **Lunarcom** y, a continuación, en la ventana Inspector, busca el componente **Lunarcom Intent Recognizer (Script)** (Reconocimiento de la intención de Lunarcom [script]) y configúralo como se indica a continuación:

* En el campo **LUIS Endpoint** (Punto de conexión de LUIS), después del **Ejemplo de consulta** que copiaste en el paso anterior:

![mrlearning-speech 30](images/mrlearning-speech/tutorial4-section4-step1-2.png)

## <a name="testing-and-improving-the-intent-recognition"></a>Probar y mejorar el reconocimiento de la intención

Para usar el reconocimiento de la intención directamente en el editor de Unity, debes permitir que el equipo de desarrollo use el dictado. Para comprobar esta configuración, abre la **Configuración** de Windows, elige **Privacidad** > **Voz** y asegúrate de que el **Reconocimiento de voz en línea** esté activado:

![mrlearning-speech 31](images/mrlearning-speech/tutorial4-section5-step1-1.png)

Si ahora entras en el modo de juego, puedes probar el reconocimiento de la intención presionando el botón del cohete: Después, suponiendo que el equipo tiene micrófono, al decir la primera expresión de ejemplo, **go ahead and launch the rocket** (adelante, lanza el cohete), verás el lanzamiento al espacio de LunarModule:

![mrlearning-speech 32](images/mrlearning-speech/tutorial4-section5-step1-2.png)

Prueba todas las **expresiones de ejemplo**, algunas **variaciones de las expresiones de ejemplo** y algunas **expresiones aleatorias**.

A continuación, vuelve a <a href="https://www.luis.ai" target="_blank">LUIS</a> y ve a la página Compilación > Mejorar el rendimiento de la aplicación > **Revisar las expresiones de punto de conexión**, usa el botón de **alternancia** para cambiar ente la vista predeterminada de entidades y la de **tokens** y, a continuación, revisa las expresiones:

* En la columna **Expresión**, cambia y quita las etiquetas asignadas según sea necesario para alinearlas con tu intención.
* En la columna **Intención alineada**, comprueba que la intención sea correcta.
* En la columna **Agregar o eliminar**, haz clic en el botón de marca de verificación verde para agregar la expresión o en el botón x rojo para eliminarla.

Cuando haya revisado todas las expresiones que quieras, haz clic en el botón **Entrenar** para volver a entrenar el modelo y, luego, en el botón **Publicar** para volver a publicar la aplicación actualizada:

![mrlearning-speech 33](images/mrlearning-speech/tutorial4-section5-step1-3.png)

> [!NOTE]
> Si una expresión de punto de conexión no está alineada con la intención de PressButton, pero quieres que el modelo sepa que la expresión no tiene ninguna intención, puedes cambiar la intención alineada a Ninguna.

**Repite** este proceso tantas veces como quieras para mejorar el modelo de la aplicación.

## <a name="congratulations"></a>Enhorabuena

Ahora, el proyecto tiene comandos de voz con tecnología de IA, lo que permite que la aplicación reconozca la intención de los usuarios aunque no usen comandos precisos. Ejecuta la aplicación en el dispositivo para asegurarte de que la característica funciona correctamente.
