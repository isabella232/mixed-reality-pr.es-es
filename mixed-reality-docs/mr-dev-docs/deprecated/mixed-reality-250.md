---
title: 'Mr Sharing 250: cascos HoloLens y envolventes'
description: Siga este tutorial de codificación con unity, Visual Studio, HoloLens y Windows Mixed Reality cascos para aprender los detalles del uso compartido de hologramas entre dispositivos de realidad mixta.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, motion controller, sharing, xbox controller, networking, cross-device
ms.openlocfilehash: 9f1b136193feefece3235d853503c05c69dbd451f9c2916fb178f1bcac0e3972
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208315"
---
# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>Uso compartido de la realidad mixta (250): HoloLens y cascos envolventes

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](../develop/unity/tutorials/mr-learning-base-01.md) para HoloLens 2.

Con la flexibilidad de la Plataforma Windows universal (UWP), es fácil crear una aplicación que abarque varios dispositivos. Con esta flexibilidad, podemos crear experiencias que aprovechen las ventajas de cada dispositivo. En este tutorial se trata una experiencia compartida básica que se ejecuta en HoloLens y Windows Mixed Reality cascos envolventes. Este contenido se entregó originalmente en la conferencia de Microsoft Build 2017 en Seattle, WA.

**En este tutorial, veremos lo siguiente:**

* Configure una red mediante UNET.
* Compartir hologramas entre dispositivos de realidad mixta.
* Establezca una vista diferente de la aplicación en función del dispositivo de realidad mixta que se esté utilizando.
* Cree una experiencia compartida en la que los HoloLens guían a los usuarios de cascos envolventes a través de una sencilla experiencia.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Uso compartido de la realidad mixta (250): HoloLens y cascos envolventes</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 equipo con las herramientas [de desarrollo necesarias](../develop/install-the-tools.md) y configurado para admitir un casco Windows Mixed Reality [envolvente](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Un controlador de Xbox que funcione con el equipo.
* Al menos un dispositivo HoloLens y un casco envolvente.
* Una red que permite la difusión UDP para la detección.

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) requeridos por el proyecto. Extraiga los archivos en una ubicación fácil de recordar.
* Este proyecto requiere la [versión recomendada de Unity con Windows Mixed Reality compatibilidad con](../develop/install-the-tools.md).

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Asegúrese de que el entorno de desarrollo está listo para usar un proyecto simple.

### <a name="what-we-will-build"></a>Qué vamos a crear

Una aplicación que muestra un holograma en un HoloLens o un casco Windows Mixed Reality envolvente.

### <a name="steps"></a>Pasos

* Abra Unity.
    * Seleccione **Open** (Abrir).
    * Vaya a donde extrajo los archivos del proyecto.
    * Haga clic en **Seleccionar carpeta**.
    * *Unity puede tardar un poco en procesar el proyecto por primera vez.*
* Compruebe que Mixed Reality está habilitado en Unity.
    * Abra el cuadro de diálogo de configuración de compilación **(Control+Mayús+B** o **Archivo > compilar Configuración...).**
    * Seleccione **Plataforma Windows universal y, a continuación,** haga clic en Cambiar **plataforma.**
    * Seleccione **Editar>Player Configuración**.
    * En el **panel Inspector** del lado derecho, expanda **XR Configuración**.
    * Active la **casilla Virtual Reality Supported (Realidad** virtual admitida).
    * *Windows Mixed Reality debe ser el SDK de Virtual Reality.*
* Cree una escena.
    * En Jerarquía, **haga clic con** el botón derecho en Cámara **principal** y **seleccione Eliminar.**
    * Desde **HoloToolkit > Entrada > prefabs** arrastre **MixedRealityCameraParent** a **hierarchy**.
* Agregar Hologramas a la escena
    * Desde **AppPrefabs,** arrastre **Skybox** a la **vista de escena**.
    * Desde **AppPrefabs,** arrastre **Administradores** a **la jerarquía**.
    * Desde **AppPrefabs,** arrastre **Isla** a **la jerarquía**.
* Guardar y compilar
    * Guardar **(Control+S o** Archivo **> Guardar escena)**
    * Puesto que se trata de una escena nueva, deberá nombrarla. El nombre no importa, pero usamos SharedMixedReality.
* Exportar a Visual Studio
    * Abra el menú de compilación **(Control+Mayús+B** o **Archivo > Compilación Configuración**)
    * Haga clic **en Agregar escenas abiertas.**
    * Comprobar proyectos **de C# de Unity**
    * Haga clic en **Generar**.
    * En la ventana del explorador de archivos que aparece, cree una nueva carpeta denominada **App**.
    * Haga clic en la **carpeta** Aplicación.
    * Presione **Seleccionar carpeta.**
    * **Esperar a que se complete la compilación**
    * En la ventana del explorador de archivos que aparece, vaya a la **carpeta Aplicación.**
    * Haga doble clic **en SharedMixedReality.sln** para iniciar Visual Studio
* Compilar a partir de Visual Studio
    * Con la barra de herramientas superior, cambie el **destino a Versión** y **x86**.
    * Haga clic en la flecha situada junto **a Máquina local** y seleccione **Dispositivo** para implementar en HoloLens
    * Haga clic en la flecha situada junto **a Dispositivo** y seleccione Local **Machine (Máquina local)** para implementar el casco de realidad mixta.
    * Haga **clic en Depurar->Iniciar sin depurar** o **Control+F5** para iniciar la aplicación.

### <a name="digging-into-the-code"></a>Profundización en el código

En el panel del proyecto, vaya a **Assets\HoloToolkit\Input\Scripts\Utilities** y haga doble clic en **MixedRealityCameraManager.cs** para abrirlo.

**Información general:** MixedRealityCameraManager.cs es un script simple que ajusta el nivel de calidad y la configuración de fondo en función del dispositivo. La clave aquí es HolographicSettings.IsDisplayOpaque, que permite que un script detecte si el dispositivo es un HoloLens (IsDisplayOpaque devuelve false) o un casco envolvente (IsDisplayOpaque devuelve true).

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

En este momento, la aplicación simplemente representará un holograma. Más adelante agregaremos interacción al holograma. Ambos dispositivos representarán el holograma de la misma manera. El casco envolvente también representará un cielo azul y un fondo de nubes.

## <a name="chapter-2---interaction"></a>Capítulo 2: Interacción

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

Muestra cómo controlar la entrada de una Windows Mixed Reality aplicación.

### <a name="what-we-will-build"></a>Qué vamos a crear

A partir de la aplicación del capítulo 1, agregaremos funcionalidad para permitir al usuario recoger el holograma y colocarlo en una superficie real en HoloLens o en una tabla virtual en un casco envolvente.

**Actualizador de entrada:** En HoloLens el gesto de selección es la **pulsación en el aire.** En los cascos envolventes, usaremos el **botón A** en el controlador de Xbox. Para más información, consulte la introducción [al modelo de interacción.](../design/interaction-fundamentals.md)

### <a name="steps"></a>Pasos

* Agregar administrador de entrada
    * Desde **HoloToolkit > Entrada > prefabs** arrastre **InputManager** a **Hierarchy** como elemento secundario de **Managers**.
    * Desde **HoloToolkit > entrada > prefabs > Cursor** arrastre cursor **a** **Hierarchy**.
* Agregar asignación espacial
    * En **HoloToolkit > SpatialMapping > Prefabs** arrastre **SpatialMapping** a **Hierarchy**.
* Agregar espacio de reproducción virtual
    * En **Jerarquía,** expanda **MixedRealityCameraParent y** seleccione **Límite.**
    * En **el** panel Inspector, active la casilla para habilitar **Límites.**
    * En **AppPrefabs,** arrastre **VRRoom** a **Hierarchy**.
* Agregar WorldAnchorManager
    * En **Jerarquía,** seleccione **Administradores.**
    * En **Inspector**, haga clic **en Agregar componente**.
    * Escriba **World Anchor Manager**.
    * Seleccione **World Anchor Manager** para agregarlo.
* Agregar TapToPlace a la isla
    * En **Hierarchy (Jerarquía),** expanda **Island**.
    * Seleccione **MixedRealityLand.**
    * En **Inspector**, haga clic **en Agregar componente**.
    * Escriba **Pulse Para colocar** y selecciónelo.
    * Active **Colocar elemento primario al pulsar**.
    * Establezca **Desplazamiento de ubicación** en **(0, 0,1, 0).**
* Guardar y compilar como antes

### <a name="digging-into-the-code"></a>Profundización en el código

**Script 1: GamepadInput.cs**

En el panel del proyecto, vaya a **Assets\HoloToolkit\Input\Scripts\InputSources** y haga doble clic **en GamepadInput.cs** para abrirlo. En la misma ruta de acceso del panel del proyecto, haga doble clic en **InteractionSourceInputSource.cs**.

Tenga en cuenta que ambos scripts tienen una clase base común, BaseInputSource.

BaseInputSource mantiene una referencia a inputManager, lo que permite que un script desencadene eventos. En este caso, el evento InputClicked es relevante. Esto será importante recordar cuando lleguemos al script 2, TapToPlace. En el caso de GamePadInput, sondeamos para que se presione el botón A en el controlador y, a continuación, generamos el evento InputClicked. En el caso de InteractionSourceInputSource, se genera el evento InputClicked en respuesta a TappedEvent.

**Script 2: TapToPlace.cs**

En el panel del proyecto, vaya a **Assets\HoloToolkit\SpatialMapping\Scripts y** haga doble clic **en TapToPlace.cs** para abrirlo.

Lo primero que muchos desarrolladores quieren implementar al crear una aplicación holográfica es mover Hologramas entrada de gestos. Por lo tanto, nos hemos esforzado por comentar exhaustivamente este script. Merece la pena resaltar algunas cosas para este tutorial.

En primer lugar, tenga en cuenta que TapToPlace implementa IInputClickHandler. IInputClickHandler expone las funciones que controlan el evento InputClicked que genera GamePadInput.cs o InteractionSourceInputSource.cs. Se llama a OnInputClicked cuando BaseInputSource detecta un clic mientras el objeto con TapToPlace está en el foco. El evento se desencadenará al HoloLens o al presionar el botón A en el controlador de Xbox.

En segundo lugar, el código se ejecuta en actualización para ver si se está buscando una superficie para poder colocar el objeto de juego en una superficie, como una tabla. El casco envolvente no tiene un concepto de superficies reales, por lo que el objeto que representa la parte superior de la tabla (Vroom > TableThingy > Cube) se ha marcado con la capa física SpatialMapping, por lo que la conversión de rayos en Update colisionará con la parte superior de la tabla virtual.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez puede seleccionar la isla para moverla. En HoloLens puede mover la isla a una superficie real. En el casco envolvente, puede mover la isla a la tabla virtual que hemos agregado.

## <a name="chapter-3---sharing"></a>Capítulo 3: Uso compartido

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Asegúrese de que la red está configurada correctamente y detalle cómo se comparten los anclajes espaciales entre los dispositivos.

### <a name="what-we-will-build"></a>Qué vamos a crear

Convertiremos el proyecto en un proyecto multijugador. Agregaremos la interfaz de usuario y la lógica para hospedar o unir sesiones. HoloLens usuarios se verán entre sí en la sesión con nubes sobre la cabeza, y los usuarios de cascos envolventes tienen nubes cerca de donde está el anclaje. Los usuarios de los cascos envolventes verán los HoloLens en relación con el origen de la escena. HoloLens usuarios verán el holograma de la isla en el mismo lugar. Es clave tener en cuenta que los usuarios de los cascos envolventes no estarán en la isla durante este capítulo, pero se comportarán de forma muy similar a HoloLens, con una vista visual de la isla.

### <a name="steps"></a>Pasos

* Remove Island y VRRoom
    * En **Jerarquía,** haga clic con el botón **derecho en Isla** y seleccione **Eliminar.**
    * En **Jerarquía,** haga clic con el botón **derecho en VRRoom** y seleccione **Eliminar.**
* Agregar Usland
    * Desde **AppPrefabs,** arrastre **Usland** a **Hierarchy**.
* Desde **AppPrefabs,** arrastre cada uno de los elementos siguientes a **Hierarchy**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Guardar y compilar como antes

### <a name="digging-into-the-code"></a>Profundización en el código

En el panel del proyecto, vaya a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** y haga doble clic en **UnetAnchorManager.cs**. La capacidad de una HoloLens compartir información de seguimiento con otra HoloLens, de modo que ambos dispositivos puedan compartir el mismo espacio es casi mágica. La potencia de la realidad mixta cobra vida cuando dos o más personas pueden colaborar con los mismos datos digitales.

Algunos aspectos que hay que señalar en este script:

En la función start, observe la comprobación de **IsDisplayOpaque.** En este caso, simulamos que se ha establecido el delimitador. Esto se debe a que los cascos envolventes no exponen una manera de importar o exportar anclajes. Sin embargo, si se ejecuta en HoloLens, este script implementa el uso compartido de delimitadores entre los dispositivos. El dispositivo que inicia la sesión creará un delimitador para la exportación. El dispositivo que se une a una sesión solicitará el delimitador del dispositivo que inició la sesión.

**Exportación:**

Cuando un usuario crea una sesión, NetworkDiscoveryWithAnchors llamará a la función CreateAnchor de UNETAnchorManagers. Vamos a seguir el flujo CreateAnchor.

Empezamos por realizar algunas tareas de mantenimiento, borrando los datos que podamos haber recopilado para anclajes anteriores. A continuación, se comprueba si hay un delimitador almacenado en caché para cargar. Los datos de anclaje tienden a estar entre 5 y 20 MB, por lo que volver a usar los anclajes almacenados en caché puede ahorrar en la cantidad de datos que necesitamos transferir a través de la red. Veremos cómo funciona esto un poco más tarde. Incluso si se va a volver a usar el delimitador, es necesario preparar los datos del anclaje en caso de que se una un cliente nuevo que no tenga el delimitador.

Hablando de preparar los datos de anclaje, la clase WorldAnchorTransferBatch expone la funcionalidad para preparar los datos de anclaje para enviarlos a otro dispositivo o aplicación y la funcionalidad para importar los datos de anclaje. Puesto que estamos en la ruta de exportación, agregaremos nuestro delimitador a WorldAnchorTransferBatch y llamaremos a la función ExportAsync. ExportAsync llamará a la devolución de llamada WriteBuffer a medida que genere datos para la exportación. Cuando todos los datos se hayan exportado, se llamará a ExportComplete. En WriteBuffer se agrega el fragmento de datos a una lista que se mantiene para exportar. En ExportComplete, la lista se convierte en una matriz. También se establece la variable AnchorName, que desencadenará que otros dispositivos soliciten el delimitador si no lo tienen.

En algunos casos, el delimitador no exportará o creará tan pocos datos que volveremos a intentarlo. Aquí simplemente llamamos a CreateAnchor de nuevo.

Una función final en la ruta de acceso de exportación es AnchorFoundRemotely. Cuando otro dispositivo encuentre el delimitador, ese dispositivo lo indicará al host y lo usará como señal de que el anclaje es un "anclaje bueno" y se puede almacenar en caché.

**Importar:**

Cuando un HoloLens se une a una sesión, debe importar un delimitador. En la función Update de UNETAnchorManager, se sondea AnchorName. Cuando cambia el nombre del delimitador, comienza el proceso de importación. En primer lugar, intentamos cargar el delimitador con el nombre especificado desde el almacén de anclajes local. Si ya lo tenemos, podemos usarlo sin volver a descargar los datos. Si no lo tenemos, llamamos a WaitForAnchor, que iniciará la descarga.

Una vez completada la descarga, NetworkTransmitter_dataReadyEvent se llama a . Esto señalará el bucle Update para llamar a ImportAsync con los datos descargados. ImportAsync llamará a ImportComplete cuando se complete el proceso de importación. Si la importación se realiza correctamente, el delimitador se guardará en el almacén del reproductor local. PlayerController.cs realiza realmente la llamada a AnchorFoundRemotely para que el host sepa que se ha establecido un buen delimitador.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez, un usuario con un HoloLens hospedará una sesión mediante el botón **Iniciar sesión** en la interfaz de usuario. Otros usuarios, tanto en HoloLens como en un casco envolvente, seleccionarán la sesión y, a continuación, seleccionarán el botón unir **sesión** en la interfaz de usuario. Si tiene varias personas con HoloLens dispositivos, tendrán nubes rojas sobre sus cabezas. También habrá una nube azul para cada casco envolvente, pero las nubes azules no estarán por encima de los cascos, ya que los cascos no están intentando encontrar el mismo espacio de coordenadas mundial que los dispositivos HoloLens.

Este punto del proyecto es una aplicación de uso compartido independiente; no hace mucho y podría actuar como base de referencia. En los capítulos siguientes, comenzaremos a crear una experiencia para que los usuarios disfruten. Para obtener más instrucciones sobre el diseño de experiencia compartida, vaya aquí.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4: Consorte y teleportación

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Atienden la experiencia a cada tipo de dispositivo de realidad mixta.

### <a name="what-we-will-build"></a>Qué vamos a crear

Actualizaremos la aplicación para colocar a los usuarios de cascos envolventes en la isla con una vista inmersiva. HoloLens usuarios seguirán teniendo la vista de la isla. Los usuarios de cada tipo de dispositivo pueden ver a otros usuarios a medida que aparecen en el mundo. Por ejemplo, los usuarios de cascos envolventes pueden ver los demás avatares en otras rutas de acceso de la isla y ven los usuarios de HoloLens como nubes gigantes sobre la isla. Los usuarios de cascos envolventes también verán el cursor del rayo de mirada del usuario HoloLens si el usuario HoloLens está mirando la isla. HoloLens usuarios verán un avatar en la isla para representar a cada usuario de casco envolvente.

**Entrada actualizada para el dispositivo inmersivo:**

* Los botones del parachoques izquierdo y derecho del controlador de Xbox giran el reproductor.
* Al mantener presionado el botón Y en el controlador de Xbox, se habilitará un cursor [de teleportado.](../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) Si el cursor tiene un indicador de flecha girando al soltar el botón Y, se le teleportará a la ubicación del cursor.

### <a name="steps"></a>Pasos

* Adición de MixedRealityTeleport a MixedRealityCameraParent
    * En **Jerarquía,** seleccione **Usland.**
    * En **inspector**, habilite **Control de nivel**.
    * En **Jerarquía,** seleccione **MixedRealityCameraParent**.
    * En **Inspector**, haga clic **en Agregar componente**.
    * Escriba **Mixed Reality Teleport y** selecciónelo.

### <a name="digging-into-the-code"></a>Profundización en el código

Los usuarios de cascos envolventes se tethered a sus equipos con un cable, pero nuestra isla es más grande que el cable es largo. Para compensarlo, necesitamos la capacidad de mover la cámara independientemente del movimiento del usuario. Consulte la página [de confort para](../design/comfort.md) obtener más información sobre el diseño de la aplicación de realidad mixta (en particular, automoción y movimiento automático).

Para describir este proceso, será útil definir dos términos. En primer **lugar, será** el objeto que mueva la cámara independientemente del usuario. Un objeto de juego secundario de **la clase será** la cámara **principal.** La cámara principal está conectada a la cabeza del usuario.

En el panel del proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **MixedRealityTeleport.cs**.

MixedRealityTeleport tiene dos trabajos. En primer lugar, controla la rotación mediante los parachoques. En la función de actualización sondeamos para "ButtonUp" en LeftBumper y RightBumper. GetButtonUp solo devuelve true en el primer fotograma en el que un botón está en marcha después de haber estado fuera de línea. Si se ha producido cualquiera de los botones, sabemos que el usuario debe girar.

Cuando giramos, hacemos un desvanecimiento y se atenua con un script simple denominado "control de atenuación". Esto se hace para evitar que el usuario vea un movimiento poco natural que podría provocar incomodidad. El efecto de entrada y salida de atenuación es bastante sencillo. Tenemos un cuadrándes negro en la parte delantera de **la cámara principal.** Al desvanezca, se pasa el valor alfa de 0 a 1. Esto hace que los píxeles negros del cuadrándular se representen y oculten todo lo que hay detrás. Al volver a desvanezca en, el valor alfa vuelve a ser cero.

Al calcular la rotación, tenga en  cuenta que estamos girando la rotación, pero calculando la rotación alrededor de la **cámara principal.** Esto es importante, ya  que cuanto más lejos esté la cámara principal de 0,0,0, menos precisa sería una rotación alrededor de la pantalla desde el punto de vista del usuario. De hecho, si no gira alrededor de la posición de la  cámara, el usuario se moverá sobre un arco alrededor del cuerpo en lugar de girar.

El segundo trabajo de MixedRealityTeleport es controlar el movimiento del **.** Esto se hace en SetWorldPosition. SetWorldPosition toma la posición de mundo deseada, la posición en la que el usuario quiere percve que se descime. Es necesario colocar  el desplazamiento en esa posición menos la posición local de la cámara **principal,** ya que ese desplazamiento se agregará a cada fotograma.

Un segundo script llama a SetWorldPosition. Echemos un vistazo a ese script. En el panel del proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **TeleportScript.cs**.

Este script está un poco más implicado que MixedRealityTeleport. El script está comprobando si el botón Y del controlador de Xbox se mantiene apagado. Mientras se mantiene el botón hacia abajo, se representa un cursor de teleportador y el script proyecta un rayo desde la posición de la mirada del usuario. Si ese rayo se intercala con una superficie que apunta más o menos hacia arriba, la superficie se considerará una buena superficie a la que teleportar y se habilitará la animación en el cursor de teleport. Si el rayo no colisiona con una superficie que apunta más o menos hacia arriba, la animación del cursor se deshabilitará. Cuando se libera el botón Y y el punto calculado del rayo es una posición válida, el script llama a SetWorldPosition con la posición en la que el rayo se intersecó.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez deberá encontrar un amigo.

Una vez más, un usuario con el HoloLens hospedará una sesión. Otros usuarios se unirán a la sesión. La aplicación colocará los tres primeros usuarios que se unirán desde un casco envolvente en una de las tres rutas de acceso de la isla. No dude en explorar la isla en esta sección.

Detalles que debe tener en cuenta:

1. Puede ver caras en las nubes, lo que ayuda a un usuario inmerso a ver qué dirección HoloLens está buscando un usuario.
2. Los avatares de la isla tienen cuellos que giran. No seguirán lo que el usuario está haciendo es realidad real (no tenemos esa información), pero resulta una buena experiencia.
3. Si el HoloLens está mirando la isla, los usuarios inmersos pueden ver su cursor.
4. Las nubes que representan el HoloLens los usuarios proyectan sombras.

## <a name="chapter-5---finale"></a>Capítulo 5: Final

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Cree una experiencia interactiva colaborativa entre los dos tipos de dispositivos.

### <a name="what-we-will-build"></a>Qué vamos a crear

A partir del capítulo 4, cuando un usuario con un casco envolvente se acerca a un juego de objetos en la isla, los usuarios de HoloLens recibirán una sugerencia de herramientas con una pista para el juego. Una vez que todos los usuarios de los cascos envolventes se alojen más allá de su casco y lleguen al "panel listo" de la sala de cohetes, el cohete se lanzará.

### <a name="steps"></a>Pasos

* En **Jerarquía,** seleccione **Usland.**
* En **inspector**, en Control **de nivel**, active Habilitar **colaboración**.

### <a name="digging-into-the-code"></a>Profundización en el código

Ahora echemos un vistazo a LevelControl.cs. Este script es el núcleo de la lógica del juego y mantiene el estado del juego. Puesto que se trata de un juego multijugador que usa UNET, es necesario comprender cómo fluyen los datos, al menos lo suficientemente bien como para modificar este tutorial. Para obtener información general más completa de UNET, consulte la documentación de Unity.

En el panel del proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **LevelControl.cs**.

Veamos cómo un casco envolvente indica que están listos para el lanzamiento del cohete. La preparación para el lanzamiento de cohetes se comunica estableciendo uno de los tres bools en una lista de bools que corresponden a las tres rutas de acceso de la isla. El valor bool de una ruta de acceso se establecerá cuando el usuario asignado a la ruta de acceso esté en la parte superior de la almohadilla marrones dentro de la sala de cohetes. De acuerdo, ahora a los detalles.

Comenzaremos en la función Update(). Tendrá en cuenta que hay una función "cheat". Lo hemos usado en el desarrollo para probar el lanzamiento y el restablecimiento de la secuencia del cohete. No funcionará en la experiencia de varios usuarios. Esperemos que en el momento en que internalice la siguiente información, pueda hacer que funcione. Después de comprobar si se debe hacer una infiel, se comprueba si el jugador local está inmerso. Queremos centrarnos en cómo encontramos que estamos en el objetivo. Dentro de la comprobación if (Inmerso), hay una llamada a CheckGoal que se oculta detrás de **enableCollaboration** bool. Esto corresponde a la casilla que ha activado al completar los pasos de este capítulo. Dentro de EnableCollaboration, vemos una llamada a CheckGoal().

CheckGoal hace algunos cálculos matemáticos para ver si estamos más o menos de pie en el panel. Cuando estamos, debug.log "Arrived at goal" y, a continuación, llamamos a "SendAtGoalMessage()". En SendAtGoalMessage llamamos a playerController.SendAtGoal. Para ahorrar tiempo, este es el código:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Tenga en cuenta que SendAtGoalMessage llama a CmdSendAtGoal, que llama a levelState.SetGoalIndex, que está de vuelta en LevelControl.cs. A primera vista, esto parece extraño. ¿Por qué no llamar simplemente a SetGoalIndex en lugar de a este extraño enrutamiento a través del controlador del reproductor? El motivo es que nos ajustamos al modelo de datos que usa UNET para mantener los datos sincronizados. Para evitar la infidelidad y la modificación, UNET requiere que cada objeto tenga un usuario que tenga autoridad para cambiar las variables sincronizadas. Además, solo el host (el usuario que inició la sesión) puede cambiar los datos directamente. Los usuarios que no son el host, pero tienen autoridad, deben enviar un "comando" al host que cambiará la variable. De forma predeterminada, el host tiene autoridad sobre todos los objetos, excepto el objeto generado para representar al usuario. En nuestro caso, este objeto tiene el script playercontroller. Hay una manera de solicitar autoridad para un objeto y, a continuación, realizar cambios, pero elegimos aprovechar el hecho de que el controlador del reproductor tiene autoridad propia y enruta los comandos a través del controlador del jugador.

Dicho de otro modo, cuando nos hayamos encontrado en nuestro objetivo, el jugador debe decir al host y el host se lo dirá a todos los demás.

De nuevo en LevelControl.cs, vea SetGoalIndex. Aquí vamos a establecer el valor de un valor en una lista de sincronización (AtGoal). Recuerde que estamos en el contexto del host mientras lo hacemos. De forma similar a un comando, una RPC es algo que el host puede emitir y que hará que todos los clientes ejecuten código. Aquí llamamos a "RpcCheckAllGoals". Cada cliente comprobará individualmente si los tres Dispositivos AtGoal están establecidos y, si es así, lanzarán el cohete.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

A partir del capítulo anterior, iniciaremos la sesión como antes. Esta vez, cuando los usuarios del casco envolvente lleguen a la "puerta" de su ruta de acceso, aparecerá una información sobre herramientas que solo los usuarios HoloLens pueden ver. Los HoloLens usuarios son responsables de comunicar esta pista a los usuarios en el casco envolvente. El cohete se lanzará al espacio una vez que cada avatar haya escalonado su correspondiente panel marron dentro del cohete. La escena se restablecerá después de 60 segundos para que pueda volver a hacerlo.

## <a name="see-also"></a>Consulte también

* [MR Input 213: controladores de movimiento](mixed-reality-213.md)