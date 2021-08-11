---
title: 'HoloLens de primera generación espacial (220): sonido espacial'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los detalles de los conceptos de sonido espacial.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, spatial sound, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: d53b449916405d8bf42bb8dd63cc1d3cb5d6127bbf9b2989ce7cb09c3762a6e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200416"
---
# <a name="hololens-1st-gen-spatial-220-spatial-sound"></a>HoloLens (1ª generación) Espacial 220: Sonido espacial

>[!IMPORTANT]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (1ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se actualizarán_** con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

[El sonido](../../../design/spatial-sound.md) espacial convierte la vida en hologramas y les proporciona presencia en nuestro mundo. Hologramas se componen de luz y sonido, y si pierde de vista los hologramas, el sonido espacial puede ayudarle a encontrarlos. El sonido espacial no es como el sonido típico que se escucharía en la radio, es el sonido que se coloca en el espacio 3D. Con el sonido espacial, puede hacer que los hologramas suenen como si se encontrara detrás de usted, junto a usted o incluso en la cabeza. En este curso, hará lo siguiente:

* Configure el entorno de desarrollo para usar Microsoft Spatial Sound.
* Use el sonido espacial para mejorar las interacciones.
* Use Spatial Sound junto con [Spatial Mapping](../../../design/spatial-mapping.md).
* Comprenda el diseño sólido y los procedimientos recomendados de combinación.
* Use sonido para mejorar los efectos especiales y llevar al usuario al Mixed Reality mundo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Asignación espacial de realidad mixta (220): Sonido espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../../develop/install-the-tools.md)
* Alguna capacidad básica de programación de C#.
* Debe haber completado [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Un HoloLens configurado [para el desarrollo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si todavía necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip). Es posible que esta versión ya no esté actualizada.
  * Si todavía necesita compatibilidad con Unity 5.5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip). Es posible que esta versión ya no esté actualizada.
  * Si todavía necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip). Es posible que esta versión ya no esté actualizada.
* Des archive los archivos en el escritorio u otra ubicación de fácil acceso.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).

### <a name="errata-and-notes"></a>Errata y Notes

* "Habilitar Solo mi código" debe deshabilitarse *(desactivado)* en Visual Studio en Herramientas->Opciones->Depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: Configuración de Unity

### <a name="objectives"></a>Objetivos

* Cambie la configuración de sonido de Unity para usar Microsoft Spatial Sound.
* Agregue sonido 3D a un objeto en Unity.

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **Open** (Abrir).
* Vaya al escritorio y busque la carpeta que anteriormente des archivó.
* Haga clic en **la carpeta Starting\Decibel** y, a continuación, presione **el botón Seleccionar** carpeta.
* Espere a que el proyecto se cargue en Unity.
* En el **Project,** abra **Scenes\Decibel.unity**.
* En el panel **Jerarquía,** expanda **HologramCollection** y seleccione **P0LY**.
* En inspector, expanda **AudioSource y** observe que no hay ninguna casilla **Espacializar.**

De forma predeterminada, Unity no carga un complemento de espacializador. Los pasos siguientes habilitarán el sonido espacial en el proyecto.

* En el menú superior de Unity, vaya **a Editar > Project Configuración > Audio**.
* Busque la lista **desplegable Spatializer Plugin (Complemento** espacializador) y seleccione **MS HRTF Spatializer**.
* En el panel **Jerarquía,** seleccione **HologramCollection > P0LY**.
* En el **panel Inspector,** busque el **componente Origen de** audio.
* Active la **casilla Espacializar.**
* Arrastre el **control deslizante de Spatial Blend** hasta **3D** o escriba **1** en el cuadro de edición.

Ahora compilaremos el proyecto en Unity y configuraremos la solución en Visual Studio.

1. En Unity, seleccione **File > Build Configuración**.
2. Haga **clic en Agregar escenas abiertas** para agregar la escena.
3. Seleccione **Universal Windows Platform en** la lista **Plataforma** y haga clic en **Cambiar plataforma.**
4. Si va a desarrollar específicamente para HoloLens, establezca **Dispositivo de destino** en **HoloLens**. De lo contrario, déjelo en **Cualquier dispositivo.**
5. Asegúrese **de que Tipo** de compilación está establecido en **D3D** y **sdk** está establecido en Instalado más reciente **(que** debe ser SDK 16299 o posterior).
6. Haga clic en **Generar**.
7. Cree una **nueva carpeta** denominada "App".
8. Haga clic en la **carpeta** Aplicación.
9. Presione **Seleccionar carpeta**.

Cuando Unity haya terminado, aparecerá Explorador de archivos ventana.

1. Abra la **carpeta** Aplicación.
2. Abra la **solución de Visual Studio Decibel**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x86.**
2. Haga clic en la flecha desplegable situada junto al botón Máquina local y seleccione **Equipo remoto.**
3. Escriba **la HoloLens IP del dispositivo y** establezca Modo de autenticación en Universal **(protocolo sin cifrar).** Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en Configuración > **Network & Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar con [Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).

Si se implementa en un casco envolvente:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x64.**
2. Asegúrese de que el destino de implementación está establecido en **Máquina local.**
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar** sin depurar o **presione Ctrl + F5**.

## <a name="chapter-2---spatial-sound-and-interaction"></a>Capítulo 2: Interacción y sonido espacial

### <a name="objectives"></a>Objetivos

* Mejorar el realismo del holograma mediante el sonido.
* Dirija la mirada del usuario mediante sonido.
* Proporcionar comentarios de gestos mediante sonido.

### <a name="part-1---enhancing-realism"></a>Parte 1: Mejorar el realismo

#### <a name="key-concepts"></a>Conceptos clave

* Espacialice los sonidos del holograma.
* Los orígenes de sonido deben colocarse en una ubicación adecuada en el holograma.

La ubicación adecuada para el sonido va a depender del holograma. Por ejemplo, si el holograma es de una persona, la fuente de sonido debe estar cerca de la cabeza y no de los pies.

#### <a name="instructions"></a>Instrucciones

Las instrucciones siguientes asociarán un sonido espacializado a un holograma.

* En el panel **Jerarquía,** expanda **HologramCollection** y seleccione **P0LY**.
* En el **panel Inspector,** en **AudioSource,** haga clic en el círculo situado junto a **AudioClip** y seleccione **PolyHover** en el menú emergente.
* Haga clic en el círculo **situado junto a Salida** y seleccione **SoundEffects** en el menú emergente.

Project Decibel usa un componente **AudioMixer de** Unity para habilitar el ajuste de los niveles de sonido para grupos de sonidos. Al agrupar sonidos de esta manera, el volumen general se puede ajustar mientras se mantiene el volumen relativo de cada sonido.

* En **AudioSource,** expanda **3D Sound Configuración**.
* Establezca **Doppler Level en** **0.**

Si se establece el nivel de Doppler en cero, se deshabilitan los cambios en el tono causados por el movimiento (ya sea del holograma o del usuario). Un ejemplo clásico de Doppler es un automóvil de movimiento rápido. A medida que el automóvil se aproxima a un agente de escucha estacionado, aumenta el tono del motor. Cuando pasa el agente de escucha, el tono disminuye con la distancia.

### <a name="part-2---directing-the-users-gaze"></a>Parte 2: Dirigir la mirada del usuario

#### <a name="key-concepts"></a>Conceptos clave

* Use sonido para llamar la atención sobre hologramas importantes.
* Las manos ayudan a dirigir dónde deben mirar los ojos.
* El cerebro tiene algunas expectativas aprendidas.

Un ejemplo de expectativas aprendidas es que los animales suelen estar por encima de las cabezas de los seres humanos. Si un usuario escucha un sonido de ave, su reacción inicial es buscar. Colocar un ave debajo del usuario puede provocar que se encuentre con la dirección correcta del sonido, pero no puede encontrar el holograma en función de la expectativa de tener que buscarlo.

#### <a name="instructions"></a>Instrucciones

Las instrucciones siguientes permiten que P0LY se oculte detrás de usted, de modo que pueda usar sonido para buscar el holograma.

* En el panel **Jerarquía,** seleccione **Administradores.**
* En el **panel Inspector,** busque **Speech Input Handler**.
* En **Speech Input Handler (Controlador de entrada de** voz), expanda Go Hide **(Ocultar).**
* Cambie **Ninguna función** a **PolyActions.GoHide**.

![Palabra clave: Ocultar](images/gohide.png)

### <a name="part-3---gesture-feedback"></a>Parte 3: Comentarios de gestos

#### <a name="key-concepts"></a>Conceptos clave

* Proporcionar al usuario confirmación de gesto positivo mediante sonido
* No sobrecargar al usuario: los sonidos demasiado sonordos se mete en el camino
* Los sonidos sutiles funcionan mejor: no eclipse la experiencia.

#### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** expanda **HologramCollection**.
* Expanda **EnergyHub y** seleccione **Base**.
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue Gesture Sound **Handler**.
* En **Gesture Sound Handler**(Controlador de sonido de gestos), haga clic en el círculo situado junto a Navigation Started **Clip** and Navigation Updated Clip (Clip iniciado de navegación y navegación) Updated **Clip (Clip** actualizado de navegación) y seleccione **RotateClick** en el menú emergente para ambos.
* Haga doble clic en "GestureHandler" para cargar en Visual Studio.

El controlador de sonido de gestos realiza las siguientes tareas:

* Cree y configure una **clase AudioSource.**
* Coloque **AudioSource en** la ubicación del **elemento GameObject adecuado.**
* Reproduce el **audioclip** asociado al gesto.

#### <a name="build-and-deploy"></a>Compilación e implementación

1. En Unity, seleccione **File > Build Configuración**.
2. Haga clic en **Generar**.
3. Haga clic en la **carpeta** Aplicación.
4. Presione **Seleccionar carpeta.**

Compruebe que la barra de herramientas dice "Release", "x86" o "x64" y "Remote Device". Si no es así, esta es la instancia de codificación de Visual Studio. Es posible que tenga que volver a abrir la solución desde la carpeta Aplicación.

* Si se le solicita, vuelva a cargar los archivos del proyecto.
* Como antes, implemente desde Visual Studio.

Después de implementar la aplicación:

* Observe cómo cambia el sonido a medida que se mueve por P0LY.
* Diga *"Ocultar" para* que P0LY se mueva a una ubicación detrás de usted. Buscarlo por el sonido.
* Mire la base del centro de energía. Pulse y arrastre a la izquierda o derecha para girar el holograma y observe cómo el sonido de clic confirma el gesto.

Nota: Hay un panel de texto que se etiquetará con usted. Contendrá los comandos de voz disponibles que puede usar a lo largo de este curso.

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a>Capítulo 3: Sonido espacial y asignación espacial

### <a name="objectives"></a>Objetivos

* Confirme la interacción entre hologramas y el mundo real mediante sonido.
* Occlude sound using the physical world (Occlude sound using the physical world).

### <a name="part-1---physical-world-interaction"></a>Parte 1: Interacción del mundo físico

#### <a name="key-concepts"></a>Conceptos clave

* Los objetos físicos suelen hacer un sonido al encontrar una superficie u otro objeto.
* Los sonidos deben ser el contexto adecuado dentro de la experiencia.

Por ejemplo, el establecimiento de una taza en una tabla debe hacer un sonido más silencioso que colocar un pórtero en una pieza de metal.

#### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** expanda **HologramCollection**.
* Expanda **EnergyHub** y seleccione **Base**.
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue Tap To Place With Sound and Action (Pulsar para colocar con sonido y **acción).**
* En Tap To Place With Sound and Action (Pulsar **para colocar con sonido y acción):**
  * Active **Colocar elemento primario al pulsar**.
  * Establezca **Sonido de colocación** en **Colocar**.
  * Establezca **Sonido de recogida** en **Recogida.**
  * Presione el signo + en la parte inferior derecha en On Pickup Action (Acción **de recogida)** y **On Placement Action (Acción de colocación).** Arrastre EnergyHub desde la escena a **los campos Ninguno (objeto).**
    * En **On Pickup Action (Acción de recogida),** haga clic en No Function EnergyHubBase ResetAnimation **(Sin función**  ->  **EnergyHubBase**  ->  **ResetAnimation).**
    * En **On Placement Action (Acción de selección de** ubicación), haga clic en No Function EnergyHubBase OnSelect **(Sin función**  ->  **EnergyHubBase**  ->  **enSeleccionar**).

![Pulsar para colocar con sonido y acción](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a>Parte 2: Oclusión de sonido

#### <a name="key-concepts"></a>Conceptos clave

* El sonido, como la luz, se puede ocluyen.

Un ejemplo clásico es una sala de conferencias. Cuando un agente de escucha se encuentra fuera del salón y la puerta está cerrada, la música suena desconcertada. También suele haber una reducción del volumen. Cuando se abre la puerta, se escucha todo el espectro del sonido en el volumen real. Los sonidos de alta frecuencia suelen ser más que frecuencias bajas.

#### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** expanda **HologramCollection** y seleccione **P0LY**.
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue Emisor de **audio.**

La clase Emisor de audio proporciona las siguientes características:

* Restaura los cambios realizados en el volumen de **AudioSource.**
* Realiza un **objeto Physics.RaycastNonAlloc** desde la posición del usuario en la dirección del **GameObject** al que está asociado **AudioEmitter.**

El método RaycastNonAlloc se usa como optimización del rendimiento para limitar las asignaciones, así como el número de resultados devueltos.

* Para cada **IAudioInfluencer** encontrado, llama al **método ApplyEffect.**
* Para cada **IAudioInfluencer** anterior que ya no se encuentre, llame al **método RemoveEffect.**

Tenga en cuenta que AudioEmitter se actualiza en escalas de tiempo humanas, en lugar de por fotograma. Esto se hace porque, por lo general, los seres humanos no se mueven lo suficientemente rápido como para que el efecto tenga que actualizarse con más frecuencia que cada trimestre o mitad de segundo. Hologramas que se teleporte rápidamente de una ubicación a otra puede interrumpir la esperanza.

* En el panel **Jerarquía,** expanda **HologramCollection**.
* Expanda **EnergyHub y** seleccione **BlobOutside**.
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue Audio **Occluder**.
* En **Audio Occluder**, establezca **Frecuencia de límite** en **1500.**

Esta configuración limita las frecuencias de AudioSource a 1500 Hz y a continuación.

* Establezca **Paso a través del volumen** en **0,9.**

Esta configuración reduce el volumen de AudioSource al 90 % de su nivel actual.

Audio Occluder implementa IAudioInfluencer para:

* Aplique un efecto de oclusión mediante **audioLowPassFilter** que se adjunta a la compra administrada de **AudioSource** **de AudioEmitter.**
* Aplica la atenuación de volumen a AudioSource.
* Deshabilita el efecto estableciendo una frecuencia de límite neutro y deshabilitando el filtro.

La frecuencia usada como neutra es de 22 kHz (22000 Hz). Esta frecuencia se eligió debido a que está por encima de la frecuencia máxima nominal que puede escuchar el oído humano, lo que no afecta al sonido.

* En el panel **Jerarquía,** seleccione **SpatialMapping**.
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue Audio **Occluder**.
* En **Audio Occluder**, establezca **Frecuencia de límite** en **750**.

Cuando hay varios occluders en la ruta de acceso entre el usuario y **AudioEmitter**, se aplica la frecuencia más baja al filtro.

* Establezca **Paso a través del volumen** en **0,75**.

Cuando hay varios occluders en la ruta de acceso entre el usuario y **AudioEmitter**, el paso del volumen se aplica de forma aditiva.

* En el panel **Jerarquía,** seleccione **Administradores.**
* En el **panel Inspector,** expanda Controlador **de entrada de voz**.
* En **El controlador de entrada de voz**, expanda Ir **cargo**.
* Cambie **No Function** a **PolyActions.GoCharge**.

![Palabra clave: Go Charge](images/gocharge.png)

* Expanda **Ven aquí.**
* Cambie **No Function** a **PolyActions.ComeBack**.

![Palabra clave: Ven aquí](images/comehere.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto en Unity e impleméntese en Visual Studio.

Después de implementar la aplicación:

* Diga *"Go Charge" (Ir* a cargo) para que P0LY escriba el centro de energía.

Observe el cambio en el sonido. Debería parecer un poco más silencioso. Si puede colocarse con una pared u otro objeto entre usted y el centro de energía, debería observar un mayor desasociemiento del sonido debido a la oclusión por parte del mundo real.

* Diga *"Ven aquí"* para que P0LY deje el centro de energía y se coloque delante de usted.

Tenga en cuenta que la oclusión de sonido se quita una vez que P0LY sale del centro de energía. Si sigue escuchando oclusión, P0LY puede ser oclusión en el mundo real. Intente moverse para asegurarse de que tiene una línea de visión clara a P0LY.

### <a name="part-3---room-models"></a>Parte 3: Modelos de habitación

#### <a name="key-concepts"></a>Conceptos clave

* El tamaño del espacio proporciona colas sublicientes que contribuyen a la localización de sonido.
* Los modelos de habitación se establecen por **AudioSource.**
* [MixedRealityToolkit para Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) proporciona código para establecer el modelo de habitación.
* Para Mixed Reality experiencias, seleccione el modelo de habitación que mejor se adapte al espacio real.

Si va a crear un escenario de realidad virtual, seleccione el modelo de habitación que mejor se adapte al entorno virtual.

## <a name="chapter-4---sound-design"></a>Capítulo 4: Diseño de sonido

### <a name="objectives"></a>Objetivos

* Comprenda las consideraciones para un diseño de sonido eficaz.
* Obtenga información sobre la combinación de técnicas e instrucciones.

### <a name="part-1---sound-and-experience-design"></a>Parte 1: Diseño de sonido y experiencia

En esta sección se de abordan las consideraciones y las directrices de diseño de sonido y experiencia clave.

#### <a name="normalize-all-sounds"></a>Normalizar todos los sonidos

Esto evita la necesidad de código de caso especial para ajustar los niveles de volumen por sonido, lo que puede llevar mucho tiempo y limita la capacidad de actualizar fácilmente los archivos de sonido.

#### <a name="design-for-an-untethered-experience"></a>Diseño para una experiencia no atesociada

HoloLens es un equipo holográfico completamente independiente y sin ateso. Los usuarios pueden y usarán sus experiencias mientras se mueven. Asegúrese de probar la mezcla de audio recorriéndola.

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a>Emisión de sonido desde ubicaciones lógicas en los hologramas

En el mundo real, un perro no procede de su cola y la voz de un humano no procede de sus pies. Evite que los sonidos emitan por partes inesperadas de los hologramas.

En el caso de los hologramas pequeños, es razonable que se emita sonido desde el centro de la geometría.

#### <a name="familiar-sounds-are-most-localizable"></a>Los sonidos conocidos son más localizables

La voz humana y la música son muy fáciles de localizar. Si alguien llama a su nombre, puede determinar con mucha precisión desde qué dirección llegó la voz y desde qué distancia. Los sonidos cortos y desconocidos son más difíciles de encontrar.

#### <a name="be-cognizant-of-user-expectations"></a>Estar al tanto de las expectativas del usuario

La experiencia de la vida desempeña un papel en nuestra capacidad de identificar la ubicación de un sonido. Este es un motivo por el que la voz humana es especialmente fácil de localizar. Es importante tener en cuenta las expectativas aprendidas del usuario al colocar los sonidos.

Por ejemplo, cuando alguien escucha una canción de ave, generalmente busca, ya que los animales tienden a estar por encima de la línea de visión (vuelo o en un árbol). No es raro que un usuario gire en la dirección correcta de un sonido, pero mire en la dirección vertical incorrecta y se confunda o se frustra cuando no encuentra el holograma.

#### <a name="avoid-hidden-emitters"></a>Evitar emisores ocultos

En el mundo real, si escuchamos un sonido, generalmente podemos identificar el objeto que emite el sonido. Esto también debe ser cierto en sus experiencias. Puede ser muy desconcertante que los usuarios oigan un sonido, sepan desde dónde se origina el sonido y no puedan ver un objeto.

Hay algunas excepciones a esta guía. Por ejemplo, los sonidos ambientales, como los críquetes en un campo, no deben estar visibles. La experiencia de la vida nos proporciona familiaridad con el origen de estos sonidos sin necesidad de verlos.

### <a name="part-2---sound-mixing"></a>Parte 2: Mezcla de sonido

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a>Dirigir la combinación para un volumen del 70 % en el HoloLens

Mixed Reality experiencias permiten ver hologramas en el mundo real. También deben permitir que se escuche sonidos del mundo real. Un destino de volumen del 70 % permite al usuario escuchar el mundo que le rodea junto con el sonido de su experiencia.

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a>HoloLens un volumen al 100 % debe evitar sonidos externos

Un nivel de volumen del 100 % es similar a una experiencia de realidad virtual. Visualmente, el usuario se transporta a un mundo diferente. Lo mismo debe contener true de forma sondíbly.

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a>Uso de AudioMixer de Unity para ajustar categorías de sonidos

Al diseñar la combinación, a menudo resulta útil crear categorías de sonido y tener la capacidad de aumentar o reducir su volumen como una unidad. Esto conserva los niveles relativos de cada sonido a la vez que permite cambios rápidos y sencillos en la combinación general. Entre las categorías comunes se incluyen: efectos de sonido, ambiente, sobres de voz y música de fondo.

#### <a name="mix-sounds-based-on-the-users-gaze"></a>Combinación de sonidos basados en la mirada del usuario

A menudo puede ser útil cambiar la combinación de sonido en la experiencia en función de dónde esté (o no) el usuario. Un uso común de esta técnica es reducir el nivel de volumen de los hologramas que están fuera del marco holográfico para facilitar al usuario centrarse en la información delante de ellos. Otro uso es aumentar el volumen de un sonido para atraer la atención del usuario a un evento importante.

#### <a name="building-your-mix"></a>Creación de la combinación

Al crear la combinación, se recomienda empezar con el audio de fondo de la experiencia y agregar capas en función de la importancia. A menudo, esto hace que cada capa sea más alta que la anterior.

Si la mezcla se combina como un embudo invertido, con los sonidos menos importantes (y generalmente más silenciosos) en la parte inferior, se recomienda estructurar la mezcla de forma similar al diagrama siguiente.

![Estructura de combinación de sonidos](images/soundlevels.png)

Los sobres de voz son un escenario interesante. En función de la experiencia que esté creando, es posible que desee tener un sonido estéreo (no localizado) o espacializar las overs de voz. Dos experiencias publicadas de Microsoft ilustran ejemplos excelentes de cada escenario.

[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) usa una voz estéreo. Cuando el narrador describe la ubicación que se está visualizando, el sonido es coherente y no varía en función de la posición del usuario. Esto permite al narrador describir la escena sin quitar los sonidos espacializados del entorno.

[Los fragmentos](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) usan una voz espacializada sobre en forma de sonido. La voz del médico se usa para ayudar a llamar la atención del usuario a una pista importante como si hubiera una persona real en la sala. Esto permite una sensación aún mayor de inmersiones en la experiencia de resolver el problema.

### <a name="part-3--performance"></a>Parte 3: Rendimiento

#### <a name="cpu-usage"></a>Uso de CPU

Cuando se usa sonido espacial, entre 10 y 12 emisores consumirán aproximadamente el 12 % de la CPU.

#### <a name="stream-long-audio-files"></a>Transmisión de archivos de audio largos

Los datos de audio pueden ser grandes, especialmente con frecuencias de muestreo comunes (44,1 y 48 kHz). Una regla general es que los archivos de audio de más de 5 a 10 segundos se deben transmitir para reducir el uso de memoria de la aplicación.

En Unity, puede marcar un archivo de audio para el streaming en la configuración de importación del archivo.

![Configuración de importación de audio](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a>Capítulo 5: Efectos especiales

### <a name="objectives"></a>Objetivos

* Agregue profundidad a "Magic Windows".
* Lleve al usuario al mundo virtual.

### <a name="magic-windows"></a>Magic Windows

#### <a name="key-concepts"></a>Conceptos clave

* La creación de vistas en un mundo oculto es visualmente atractiva.
* Mejore el realismo agregando efectos de audio cuando un holograma o el usuario están cerca del mundo oculto.

#### <a name="instructions"></a>Instrucciones

* En el panel **Jerarquía,** expanda **HologramCollection** y seleccione **Underworld**.
* Expanda **Subworld** y seleccione **VoiceSource.**
* En el **panel Inspector,** haga clic **en Agregar componente** y agregue User Voice **Effect**.

Se **agregará un** componente AudioSource a **VoiceSource.**

* En **AudioSource**, establezca **Salida** en **UserVoice (Mixer).**
* Active la casilla **Espacializar.**
* Arrastre el **control deslizante Spatial Blend** hasta **3D** o escriba **1** en el cuadro de edición.
* Expanda **3D Sound Configuración**.
* Establezca **Doppler Level en** **0.**
* En **User Voice Effect (Efecto de voz de** usuario), establezca Parent Object **(Objeto primario)** en **underworld (Subworld)** desde la escena.
* Establezca **Distancia máxima** en **1**.

Establecer **distancia máxima** indica al efecto de **voz** del usuario lo cerca que debe estar el usuario del objeto primario antes de habilitar el efecto.

* En **User Voice Effect (Efecto de voz del usuario),** expanda Parameters **(Parámetros de acción).**
* Establezca **Profundidad** en **0,1.**
* Establezca **Pulse 1 volumen,** **Pulse 2 volumen** y Pulse **3 Volumen** en **0,8.**
* Establezca **Volumen de sonido original** en **0,5.**

La configuración anterior configura los parámetros de **AudioChorusFilter** de Unity que se usan para agregar enriquecimiento a la voz del usuario.

* En **User Voice Effect (Efecto de voz de** usuario), expanda Echo Parameters **(Parámetros de eco).**
* Establezca **Retraso** en **300**
* Establezca **Relación de decadencia** en **0,2**.
* Establezca **Volumen de sonido original** en **0.**

La configuración anterior configura los parámetros de Unity **AudioEchoFilter** que se usan para hacer que la voz del usuario resuena.

El script Efecto de voz de usuario es responsable de:

* Medir la distancia entre el usuario y **el GameObject** al que está asociado el script.
* Determinar si el usuario se enfrenta o no a **GameObject.**

El usuario debe estar orientado al GameObject, independientemente de la distancia, para que el efecto se habilite.

* Aplicación y configuración de **AudioChorusFilter** y **AudioEchoFilter** a **AudioSource.**
* Deshabilitar el efecto deshabilitando los filtros.

Efecto de voz de usuario usa el componente Selector de flujo de micrófono, de [MixedRealityToolkit para Unity,](https://github.com/Microsoft/MixedRealityToolkit-Unity)para seleccionar la secuencia de voz de alta calidad y enrutarla al sistema de audio de Unity.

* En el panel **Jerarquía,** seleccione **Administradores.**
* En el **panel Inspector,** expanda Controlador **de entrada de voz**.
* En **El controlador de entrada de** voz , expanda Mostrar **subworld**.
* Cambie **Ninguna función** a **UnderworldBase.OnEnable.**

![Palabra clave: Mostrar subworld](images/showunderworld.png)

* Expanda **Ocultar subworld**.
* Cambie **Ninguna función** a **UnderworldBase.OnDisable.**

![Palabra clave: Ocultar subworld](images/hideunderworld.png)

#### <a name="build-and-deploy"></a>Compilación e implementación

* Como antes, compile el proyecto en Unity e impleméntese en Visual Studio.

Después de implementar la aplicación:

* Enfóciese a una superficie (pared, suelo, tabla) y diga *"Show Underworld".*

Se mostrará el subworld y se ocultarán todos los demás hologramas. Si no ve el subworld, asegúrese de que se encuentra frente a una superficie real.

* Aproximarse a menos de un metro del holograma de subworld y empezar a hablar.

Ahora hay efectos de audio aplicados a su voz.

* Aléjese del subworld y observe cómo ya no se aplica el efecto.
* Diga *"Hide Underworld" (Ocultar subworld)* para ocultar el subworld.

El subworld se ocultará y volverán a aparecer los hologramas previamente ocultos.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ya ha completado **MR Spatial 220: Sonido espacial.**

Escuche al mundo y haga que sus experiencias se a lifeen con sonido.