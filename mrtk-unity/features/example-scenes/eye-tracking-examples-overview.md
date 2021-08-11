---
title: Información general sobre ejemplos del seguimiento ocular
description: Ejemplo para compilar el seguimiento de los ojos en MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, EyeTracking,
ms.openlocfilehash: 32ae64a470572dda71578948d5091887bea9e0e084d97ede7f2f14af596b5a6b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223223"
---
# <a name="eye-tracking-examples-overview"></a>Información general sobre ejemplos del seguimiento ocular

En este tema se describe cómo empezar a trabajar rápidamente con el seguimiento de los ojos en MRTK mediante la creación de ejemplos de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking).
Estos ejemplos le permiten experimentar una de nuestras nuevas funcionalidades mágicas de entrada: **Seguimiento de los ojos.**
La demostración incluye varios casos de uso, desde activaciones implícitas basadas en  los ojos hasta cómo combinar sin problemas información sobre lo que está viendo con la entrada de voz **y** mano.
Esto permite a los usuarios seleccionar y mover contenido holográfico de forma rápida y sin esfuerzo a través de su vista con solo mirar un destino y decir _"Seleccionar"_ o realizar un gesto con la mano.
Las demostraciones también incluyen un ejemplo de desplazamiento dirigido con mirada con los ojos, desplazamiento panorámico y zoom de texto e imágenes en una pizarra.
Por último, se proporciona un ejemplo para grabar y visualizar la atención visual del usuario en una pizarra 2D.
En la sección siguiente, encontrará más detalles sobre lo que incluye cada uno de los diferentes ejemplos del paquete de ejemplo de seguimiento ocular de MRTK (Assets/MRTK/Examples/Demos/EyeTracking):

![Lista de escenas de seguimiento de los ojos](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

La siguiente sección es una introducción rápida de lo que son las escenas de demostración de seguimiento de los ojos individuales.
Las escenas de demostración de seguimiento de los ojos de MRTK [se cargan](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)aditivamente, lo que explicaremos a continuación cómo configurar.

## <a name="overview-of-the-eye-tracking-demo-samples"></a>Información general de los ejemplos de demostración de seguimiento de los ojos

### <a name="eye-supported-target-selection"></a>[**Selección de destino compatible con los ojos**](../input/eye-tracking/eye-tracking-target-selection.md)

En este tutorial se muestra la facilidad de acceso a los datos de mirada con los ojos para seleccionar destinos.
Incluye un ejemplo de comentarios sutiles pero eficaces para proporcionar al usuario la confianza de que un destino se centra sin ser abrumador.
Además, hay un ejemplo sencillo de notificaciones inteligentes que desaparecen automáticamente después de leerse.

**Resumen:** selecciones de destino rápidas y sin esfuerzo mediante una combinación de ojos, voz y entrada de mano.

### <a name="eye-supported-navigation"></a>[**Navegación con los ojos**](../input/eye-tracking/eye-tracking-navigation.md)

Imagine que está leyendo información en una pantalla lejana o en el lector electrónico y cuando llega al final del texto mostrado, el texto se desplaza automáticamente hacia arriba para mostrar más contenido.
O bien, ¿qué tal acercarse directamente hacia donde estaba mirando?
Estos son algunos de los ejemplos que se muestran en este tutorial con respecto a la navegación con los ojos.
Además, hay un ejemplo para la rotación de manos libres de hologramas 3D, ya que los hace girar automáticamente en función del foco actual.

**Resumen:** desplazamiento, desplazamiento panorámico, zoom, rotación 3D mediante una combinación de ojos, voz y entrada de mano.

### <a name="eye-supported-positioning"></a>[**Posición compatible con los ojos**](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

En este tutorial se muestra un escenario de entrada denominado [Put-That-There](https://youtu.be/CbIn8p4_4CQ) que se reentraba a la investigación del laboratorio multimedia mit a principios de la década de 1980 con entrada de ojo, mano y voz.
La idea es sencilla: benefíciese de sus ojos para una selección y un posicionamiento de destino rápidos.
Basta con mirar un holograma y decir _"put this",_ mire dónde quiere colocarlo y diga _"there!"._
Para colocar el holograma de forma más precisa, puede usar entradas adicionales de las manos, la voz o los controladores.

**Resumen:** colocación de hologramas con los ojos, la voz y la entrada de la mano *(arrastrar y colocar).* Controles deslizantes compatibles con los ojos con los ojos y las manos.

### <a name="visualization-of-visual-attention"></a>**Visualización de la atención visual**

Los datos basados en la apariencia de los usuarios son una herramienta enormemente eficaz para evaluar la facilidad de uso de un diseño e identificar problemas en flujos de trabajo eficaces.
En este tutorial se de abordan diferentes visualizaciones de seguimiento de los ojos y cómo se ajustan a distintas necesidades.
Proporcionamos ejemplos básicos para registrar y cargar datos de seguimiento de los ojos y ejemplos de cómo visualizarlos.

**Resumen:** mapa de atención bidimensional (mapas térmicos) en pizarras. Grabación & reproducir datos de seguimiento de los ojos.

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a>Configuración de los ejemplos de seguimiento de los ojos de MRTK

### <a name="prerequisites"></a>Requisitos previos

Tenga en cuenta que el uso de los ejemplos de seguimiento de los ojos en el dispositivo requiere un HoloLens 2 y un paquete de aplicación de ejemplo que se ha creado con la funcionalidad "Entrada de mirada" en appXManifest del paquete.

Para usar estos ejemplos de seguimiento de los [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) ojos en el dispositivo, asegúrese de seguir estos pasos antes de compilar la aplicación en Visual Studio.

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a>1. Load EyeTrackingDemo-00-RootScene.unity

*EyeTrackingDemo-00-RootScene* es laescena base (raíz) que incluye todos los componentes principales de MRTK.
Esta es la escena que debe cargar primero y desde la que ejecutará las demostraciones de seguimiento de los ojos.
Incluye un menú gráfico de escena que permite cambiar fácilmente entre las distintas muestras de seguimiento de los ojos que se [cargarán de forma aditiva.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)

![Menú de escena en el ejemplo de seguimiento de los ojos](../images/eye-tracking/mrtk_et_scenemenu.jpg)

La escena raíz incluye algunos componentes principales que se conservarán en las escenas cargadas aditivamente, como los perfiles configurados por MRTK y la cámara de escena.
_MixedRealityBasicSceneSetup_ (vea la captura de pantalla siguiente) incluye un script que cargará automáticamente la escena a la que se hace referencia al inicio.
De forma predeterminada, se trata _de EyeTrackingDemo-02-TargetSelection._  

![Ejemplo del script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a>2. Agregar escenas al menú de compilación

Para cargar escenas de adición durante el tiempo de ejecución, primero debe agregar estas escenas al menú Build _Configuración -> Scenes in Build_ (Escenas de compilación).
Es importante que la escena raíz se muestra como la primera escena de la lista:

![Menú crear Configuración escena para ejemplos de seguimiento de los ojos](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a>3. Reproducir los ejemplos de seguimiento de los ojos en el editor de Unity

Después de agregar las escenas de seguimiento de los ojos al Configuración de compilación y cargar _EyeTrackingDemo-00-RootScene,_ hay una última cosa que puede que quiera comprobar: ¿Está habilitado el script _"OnLoadStartScene"_ asociado a _MixedRealityBasicSceneSetup_ GameObject? Esto es para que la escena raíz sepa qué escena de demostración se va a cargar primero.

![Ejemplo del script OnLoad_StartScene script](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

¡Vamos a deshacer! Presione _"Reproducir"._
Debería ver que aparecen varias gemas y el menú de la escena en la parte superior.

![Captura de pantalla de ejemplo de la escena de selección de destino et](../images/eye-tracking/mrtk_et_targetselect.png)

También debería observar un pequeño círculo semitransparente en el centro de la vista del juego.
Esto actúa como un indicador (cursor) de la mirada con los ojos simulados: simplemente presione el botón derecho del _mouse_ y mueva el mouse para cambiar su posición.
Cuando el cursor mantenga el puntero sobre las gemas, observará que se ajustará al centro de la gema vista actualmente.
Se trata de una excelente manera de probar si los eventos se desencadenan según lo previsto _al "mirar&quot;_ a un destino.
Tenga en cuenta que la mirada con los ojos _simulados_ a través del control del mouse es un complemento bastante deficiente para nuestros movimientos oculares rápidos e involuntarias.
Sin embargo, es excelente para probar la funcionalidad básica antes de iterar en el diseño implementando en el HoloLens 2 dispositivo.
Volver a la escena de ejemplo de seguimiento de los ojos: la gema gira siempre que se mira y se puede destruir &quot;mirarla&quot; y ...

- Presionar _Entrar_ (que simula decir &quot;seleccionar")
- Decir _"seleccionar"_ en el micrófono
- Al presionar _Espacio para_ mostrar la entrada de la mano simulada, haga clic en el botón izquierdo del mouse para realizar una acción de acercamiento simulada.

Se describe con más detalle cómo puede lograr estas interacciones en nuestro tutorial Selección de destino compatible con [**los ojos.**](../input/eye-tracking/eye-tracking-target-selection.md)

Al mover el cursor hasta la barra de menús superior de la escena, observará que el elemento que se mantiene el mouse se resaltará de forma sutil.
Puede seleccionar el elemento resaltado actualmente mediante uno de los métodos de confirmación descritos anteriormente (por ejemplo, presionar _Entrar)._
De este modo, puede cambiar entre las distintas escenas de ejemplo de seguimiento de los ojos.

### <a name="4-how-to-test-specific-sub-scenes"></a>4. Cómo probar subescciones específicas

Al trabajar en un escenario específico, es posible que no quiera pasar por el menú de la escena cada vez.
En su lugar, puede que quiera empezar directamente desde la escena en la que está trabajando actualmente al presionar el _botón Reproducir._
No se preocupe. Esto es lo que puede hacer:

1. Carga de la _escena_ raíz
2. En la _escena raíz,_ deshabilite el script _"OnLoadStartScene"._
3. _Arrastre y coloque una de_ las escenas de prueba de seguimiento  de los ojos que se describen a continuación (o cualquier otra escena) en la vista Jerarquía, como se muestra en la captura de pantalla siguiente.

    ![Ejemplo de escena de adiciones](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. Presione _Reproducir._

Tenga en cuenta que la carga de la sub escena como esta no es persistente: esto significa que, si implementa la aplicación en el dispositivo HoloLens 2, solo cargará la escena raíz (suponiendo que aparezca en la parte superior de la compilación Configuración).
Además, al compartir el proyecto con otros usuarios, las sub escenas no se cargan automáticamente.

---

Ahora que sabe cómo hacer que las escenas de ejemplo de seguimiento de los ojos de MRTK funcionen, vamos a continuar profundizando en cómo seleccionar hologramas con los ojos: [Selección](../input/eye-tracking/eye-tracking-target-selection.md)de destino compatible con los ojos.

---
[Vuelva a "Eye Tracking in the MixedRealityToolkit" (Seguimiento de los ojos en MixedRealityToolkit)](../input/eye-tracking/eye-tracking-Main.md)
