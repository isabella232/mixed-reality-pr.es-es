---
title: Manos y controladores de movimiento en DirectX
description: Introducción a la guía para desarrolladores para usar controladores de movimiento y seguimiento de manos en aplicaciones nativas de DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: manos, controladores de movimiento, directx, entrada, hologramas, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 13988df80052ef85662dcf9834406baa91d48f7c0b70242d1c904548c2707105
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210966"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Manos y controladores de movimiento en DirectX

> [!NOTE]
> Este artículo se relaciona con las API nativas de WinRT heredadas.  Para los nuevos proyectos de aplicaciones nativas, se recomienda usar la **[API de OpenXR](openxr-getting-started.md)**.

En Windows Mixed Reality, tanto la entrada manual como la entrada del [controlador](../../design/motion-controllers.md) de movimiento se controlan a través de las API de entrada espacial, que se encuentran en el [Windows. Ui. Espacio de nombres Input.Spatial.](/uwp/api/windows.ui.input.spatial) Esto le permite controlar fácilmente acciones comunes, como las presiones **Select** de la misma manera entre las manos y los controladores de movimiento.

## <a name="getting-started"></a>Introducción

Para acceder a la entrada espacial Windows Mixed Reality, comience con la interfaz SpatialInteractionManager.  Puede acceder a esta interfaz llamando a  [SpatialInteractionManager::GetForCurrentView](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente en algún momento durante el inicio de la aplicación.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

El trabajo de SpatialInteractionManager es proporcionar acceso a [SpatialInteractionSources](/uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representan un origen de entrada.  Hay tres tipos de SpatialInteractionSources disponibles en el sistema.
* **Mano** representa la mano detectada de un usuario. Los orígenes de manos ofrecen diferentes características basadas en el dispositivo, que van desde gestos básicos en HoloLens hasta el seguimiento de manos totalmente articulado en HoloLens 2. 
* **El** controlador representa un controlador de movimiento emparejado. Los controladores de movimiento pueden ofrecer diferentes funcionalidades, por ejemplo, seleccionar desencadenadores, botones de menú, botones de sujeción, táctiles y botones de posición.
* **Voz** representa las palabras clave detectadas por el sistema de voz del usuario. Por ejemplo, este origen insertará una tecla Select y la liberará cada vez que el usuario diga "Seleccionar".

Los datos por fotograma de un origen se representan mediante la [interfaz SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Hay dos maneras diferentes de acceder a estos datos, en función de si desea usar un modelo basado en sondeos o basado en eventos en la aplicación.

### <a name="event-driven-input"></a>Entrada controlada por eventos
SpatialInteractionManager proporciona una serie de eventos que la aplicación puede escuchar.  Algunos ejemplos son [SourcePressed,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)[SourceReleased y [SourceUpdated.](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)

Por ejemplo, el código siguiente conecta un controlador de eventos denominado MyApp::OnSourcePressed al evento SourcePressed.  Esto permite que la aplicación detecte presiones en cualquier tipo de origen de interacción.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Este evento presionado se envía a la aplicación de forma asincrónica, junto con el spatialInteractionSourceState correspondiente en el momento en que se produjo la presión. Es posible que la aplicación o el motor de juegos quiera iniciar el procesamiento de inmediato o poner en cola los datos de eventos en la rutina de procesamiento de entrada. Esta es una función de controlador de eventos para el evento SourcePressed, que comprueba si se ha presionado el botón seleccionar.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

El código anterior solo busca la tecla "Seleccionar", que corresponde a la acción principal en el dispositivo. Algunos ejemplos son realizar una acción AirTap HoloLens o extraer el desencadenador en un controlador de movimiento.  Las presiones "Select" representan la intención del usuario de activar el holograma al que se va a dirigir.  El evento SourcePressed se va a abrir para varios botones y gestos diferentes, y puede inspeccionar otras propiedades en SpatialInteractionSource para probar esos casos.

### <a name="polling-based-input"></a>Entrada basada en sondeo
También puede usar SpatialInteractionManager para sondear el estado actual de entrada de cada fotograma.  Para ello, llame a [GetDetectedSourcesAtTimestamp en](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada fotograma.  Esta función devuelve una matriz que contiene [un SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) por cada [SpatialInteractionSource activo.](/uwp/api/windows.ui.input.spatial.spatialinteractionsource) Esto significa uno para cada controlador de movimiento activo, uno para cada mano con seguimiento y otro para voz si se ha proferido recientemente un comando "select". A continuación, puede inspeccionar las propiedades de cada SpatialInteractionSourceState para impulsar la entrada en la aplicación. 

Este es un ejemplo de cómo comprobar la acción "select" mediante el método de sondeo. La  variable de predicción representa [un objeto HolographicFramePrediction,](/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) que se puede obtener de [HolographicFrame.](/uwp/api/windows.graphics.holographic.holographicframe)

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Cada SpatialInteractionSource tiene un identificador, que puede usar para identificar nuevos orígenes y correlacionar los orígenes existentes de fotograma a marco.  Las manos obtienen un nuevo identificador cada vez que salen y escriben la FOV, pero los identificadores de controlador permanecen estáticos durante la sesión.  Puede usar los eventos de SpatialInteractionManager, como [SourceDetected](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) y [SourceLost,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)para reaccionar cuando las manos entran o salen de la vista del dispositivo, o cuando los controladores de movimiento están activados o desactivados o emparejados o no emparejados.

### <a name="predicted-vs-historical-poses"></a>Predicho frente a poses históricas
GetDetectedSourcesAtTimestamp tiene un parámetro timestamp. Esto le permite solicitar el estado y posar datos que son predichos o históricos, lo que le permite correlacionar las interacciones espaciales con otros orígenes de entrada. Por ejemplo, al representar la posición de la mano en el marco actual, puede pasar la marca de tiempo de predicción proporcionada por [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe). Esto permite que el sistema predijo hacia delante la posición de la mano para alinearse estrechamente con la salida del fotograma representado, lo que minimiza la latencia percibida.

Sin embargo, este tipo de pose predicho no genera un rayo de referencia ideal para dirigirse a un origen de interacción. Por ejemplo, cuando se presiona un botón de controlador de movimiento, puede tardar hasta 20 ms para que ese evento se ebuje a través de Bluetooth al sistema operativo. De forma similar, después de que un usuario realiza un gesto con la mano, puede pasar algo de tiempo antes de que el sistema detecte el gesto y la aplicación lo sondee. En el momento en que la aplicación sondea si hay un cambio de estado, las poses de la cabeza y la mano usadas para dirigirse a esa interacción se han producido realmente en el pasado. Si el destino es pasar la marca de tiempo de HolographicFrame actual a GetDetectedSourcesAtTimestamp, la posición se reenviará al rayo de destino en el momento en que se mostrará el fotograma, que podría ser superior a 20 ms en el futuro. Esta posición futura  es buena para representar el origen  de interacción, pero se compondrá nuestro problema de tiempo para dirigirse a la interacción, ya que la selección de destino del usuario se produjo en el pasado.

Afortunadamente, los [eventos SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased y [SourceUpdated](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) proporcionan el estado histórico [asociado](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) a cada evento de entrada.  Esto incluye directamente la cabeza histórica y las poses de mano [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) disponibles a través de [TryGetPointerPose,](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)junto con una marca de tiempo histórica que puede pasar a otras API para correlacionar con este evento.

Esto conduce a los siguientes procedimientos recomendados al representar y dirigirse con manos y controladores a cada fotograma:
* Para **representar a mano o** controlador  cada fotograma, la aplicación debe sondear la **posición** prevista hacia delante de cada origen de interacción en el momento del foton del fotograma actual.  Puede sondear todos los orígenes de interacción llamando a [GetDetectedSourcesAtTimestamp](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) en cada fotograma, pasando la marca de tiempo predicho proporcionada por [HolographicFrame::CurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* En **el caso** de la aplicación que tiene como destino la mano o el  controlador en una pulsación o una versión, la aplicación debe controlar los eventos presionados o publicados, la difusión por rayos en función de la posición histórica de la cabeza o la mano para ese evento.  Para obtener este rayo de destino, controle el evento [SourcePressed](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased,](/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) obtenga la propiedad [State](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) de los argumentos del evento y, a continuación, llame a su [método TryGetPointerPose.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)

## <a name="cross-device-input-properties"></a>Propiedades de entrada entre dispositivos
La API SpatialInteractionSource admite controladores y sistemas de seguimiento de manos con una amplia gama de funcionalidades. Algunas de estas funcionalidades son comunes entre los tipos de dispositivo. Por ejemplo, los controladores de movimiento y de seguimiento de manos proporcionan una acción "select" y una posición 3D. Siempre que sea posible, la API asigna estas funcionalidades comunes a las mismas propiedades en SpatialInteractionSource.  Esto permite que las aplicaciones admitan más fácilmente una amplia gama de tipos de entrada. En la tabla siguiente se describen las propiedades que se admiten y cómo se comparan entre los tipos de entrada.

| Propiedad | Description | HoloLens(1.ª generación) Gestos | Controladores de movimiento | Manos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handedness**](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Derecha o izquierda/ controlador. | No compatible | Compatible | Compatible |
| [SpatialInteractionSourceState::**IsSelectPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado actual del botón principal. | Pulsación en el aire | Desencadenador | Pulsación de aire relajada (desenlazador vertical) |
| [SpatialInteractionSourceState::**IsGrasped**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado actual del botón de toma. | No admitido | Botón Desgarr | Mano cerrada o desenlazador |
| [SpatialInteractionSourceState::**IsMenuPressed**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado actual del botón de menú.    | No admitido | Botón menú | No admitido |
| [SpatialInteractionSourceLocation::**Position**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Ubicación XYZ de la posición de la mano o del control en el controlador. | Ubicación de la mano | Posición de posición del control | Ubicación de la mano |
| [SpatialInteractionSourceLocation::**Orientation**](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Cuaternión que representa la orientación de la posición de la mano o del control en el controlador. | No admitido | Orientación de posición del control | Orientación de la mano |
| [SpatialPointerInteractionSourcePose::**Position**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origen del rayo que apunta. | No compatible | Compatible | Compatible |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Dirección del rayo que apunta. | No compatible | Compatible | Compatible |

Algunas de las propiedades anteriores no están disponibles en todos los dispositivos y la API proporciona un medio para probarlo. Por ejemplo, puede inspeccionar la propiedad [SpatialInteractionSource::IsGraspSupported](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) para determinar si el origen proporciona una acción de comprensión.

### <a name="grip-pose-vs-pointing-pose"></a>Posición de control frente a posición de apuntar

Windows Mixed Reality admite controladores de movimiento en diferentes factores de forma.  También admite sistemas de seguimiento de manos articulados.  Todos estos sistemas tienen relaciones diferentes entre la posición de la mano y la dirección "hacia delante" natural que las aplicaciones deben usar para señalar o representar objetos en la mano del usuario.  Para admitir todo esto, se proporcionan dos tipos de poses 3D tanto para el seguimiento de manos como para los controladores de movimiento.  La primera es la posición del control, que representa la posición de la mano del usuario.  La segunda es la posición de apuntar, que representa un rayo que apunta que se origina en la mano o el controlador del usuario. Por lo tanto,  si desea representar la mano del usuario o un objeto que se mantiene en la mano del **usuario,** como un pólver o un revólver, use la posición de control. Si desea la transmisión por rayos desde el controlador o la mano, por ejemplo, cuando el usuario apunta a la interfaz de usuario, use la posición de punto.

Puede acceder a la **posición de control** a través de [SpatialInteractionSourceState::P roperties::TryGetLocation(...)](/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_). Se define de la siguiente manera:
* Posición **del control:** centroide de la mano al mantener el controlador de forma natural, ajustado a la izquierda o a la derecha para centrar la posición dentro del control.
* Eje **derecho** de la orientación del control: cuando se abre completamente la mano para formar una posición plana de 5 dedos, el rayo que es normal para la mano (hacia delante desde la mano izquierda, hacia atrás desde la mano derecha).
* Eje **hacia** delante de la orientación del control: al cerrar la mano parcialmente (como si sostendes el controlador), el rayo que apunta "hacia delante" a través del canal formado por los dedos que no son de los dedos.
* Eje **Up de la orientación del control:** eje Up implícito en las definiciones Right y Forward.

Puede acceder a la **posición** del puntero a través de [SpatialInteractionSourceState::P roperties::TryGetLocation(...)::SourcePointerPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState::TryGetPointerPose(...)::TryGetInteractionSourcePose](/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propiedades de entrada específicas del controlador
Para los controladores, SpatialInteractionSource tiene una propiedad Controller con funcionalidades adicionales.
* **HasThumbstick:** Si es true, el controlador tiene una chincheta. Inspeccione la [propiedad ControllerProperties](/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) de SpatialInteractionSourceState para adquirir los valores x e y de la huella digital (ThumbstickX y ThumbstickY), así como su estado presionado (IsThumbstickPressed).
* **HasTouchpad:** Si es true, el controlador tiene un panel táctil. Inspeccione la propiedad ControllerProperties de SpatialInteractionSourceState para adquirir los valores x e y del panel táctil (TouchpadX y TouchpadY), y para saber si el usuario está tocándose el panel (IsTouchpadTouched) y si presiona el panel táctil hacia abajo (IsTouchpadPressed).
* **SimpleHapticsController:** La API SimpleHapticsController del controlador permite inspeccionar las funcionalidades hápticas del controlador y también permite controlar los comentarios hápticos.

El intervalo de touchpad y thumbstick es de -1 a 1 para ambos ejes (de abajo a arriba y de izquierda a derecha). El intervalo del desencadenador análogo, al que se accede mediante la propiedad SpatialInteractionSourceState::SelectPressedValue, tiene un intervalo de 0 a 1. Un valor de 1 se correlaciona con IsSelectPressed que es igual a true; cualquier otro valor se correlaciona con IsSelectPressed que es igual a false.

## <a name="articulated-hand-tracking"></a>Seguimiento de manos articulado
La API Windows Mixed Reality proporciona compatibilidad completa con el seguimiento de manos articulado, por ejemplo, en HoloLens 2. El seguimiento de manos articulado se puede usar para implementar la manipulación directa y los modelos de entrada de punto y confirmación en las aplicaciones. También se puede usar para crear interacciones totalmente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto de la mano
El seguimiento de manos articulado proporciona un esqueleto de 25 uniones que permite muchos tipos diferentes de interacciones.  El esqueleto proporciona cinco uniones para el índice, el anillo medio, los dedos pequeños, cuatro para el dedo y una para la mano.  La unión de cuello actúa como base de la jerarquía. En la siguiente imagen se muestra el diseño del esqueleto.

![Esqueleto de la mano](images/hand-skeleton.png)

En la mayoría de los casos, cada unión se denomina según el póreo que representa.  Dado que hay dos animales en cada coyuntura, usamos una convención para asignar un nombre a cada unión en función del perro secundario en esa ubicación.  El cuello secundario se define como el cuello más lejos de la vaquera.  Por ejemplo, la unión "Index Uno" contiene la posición inicial del pórmico del índice y la orientación de ese pórmico.  No contiene la posición final del póreo.  Si lo necesita, lo obtiene de la siguiente unión de la jerarquía, la unión "Index Intermediate".

Además de las 25 uniones jerárquicas, el sistema proporciona una coyuntura de mano.  Normalmente, la mano no se considera parte de la estructura esquelética. Solo se proporciona como una manera cómoda de obtener la posición general y la orientación de la mano.

Se proporciona la siguiente información para cada unión:

| Nombre | Descripción |
|--- |--- |
|Posición | Posición 3D de la unión, disponible en cualquier sistema de coordenadas solicitado. |
|Orientación | Orientación 3D del coordenado, disponible en cualquier sistema de coordenadas solicitado. |
|Radio | Distancia a la superficie de la máscara en la posición de la unión. Resulta útil para optimizar interacciones directas o visualizaciones que se basan en el ancho de los dedos. |
|Precisión | Proporciona una sugerencia sobre la confianza del sistema con respecto a la información de esta unión. |

Puede acceder a los datos del esqueleto de la mano a través de una función en [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  La función se denomina [TryGetHandPose](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)y devuelve un objeto denominado [HandPose.](/uwp/api/windows.perception.people.handpose)  Si el origen no admite manos articuladas, esta función devolverá null.  Una vez que tenga un HandPose, puede obtener los datos conjuntos actuales llamando a [TryGetJoint](/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con el nombre de la unión que le interesa.  Los datos se devuelven como una [estructura JointPose.](/uwp/api/windows.perception.people.jointpose)  El código siguiente obtiene la posición de la punta del dedo índice. La variable *currentState* representa una instancia de [SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Malla de mano

La API de seguimiento de manos articulada permite una malla de mano de triángulo totalmente deformable.  Esta malla puede deformarse en tiempo real junto con el esqueleto de la mano, y es útil para las técnicas de visualización y física avanzada.  Para acceder a la malla de mano, primero debe crear un objeto [HandMeshObserver](/uwp/api/windows.perception.people.handmeshobserver) mediante una llamada a [TryCreateHandMeshObserverAsync](/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) en [SpatialInteractionSource](/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Esto solo debe hacerse una vez por origen, normalmente la primera vez que lo vea.  Esto significa que llamará a esta función para crear un objeto HandMeshObserver cada vez que una mano entre en la FOV.  Se trata de una función asincrónica, por lo que tendrá que tratar un poco de simultaneidad aquí.  Una vez disponible, puede solicitar al objeto HandMeshObserver el búfer de índice del triángulo llamando a [GetTriangleIndices](/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Los índices no cambian el marco sobre el marco, por lo que puede obtenerlos una vez y almacenarlos en caché durante la vigencia del origen.  Los índices se proporcionan en orden de sinuoso en el sentido de las agujas del reloj.

El código siguiente gira un std::thread desasociado para crear el observador de malla y extrae el búfer de índice una vez que el observador de malla está disponible.  Se inicia a partir de una variable denominada *currentState*, que es una instancia de [SpatialInteractionSourceState](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa una mano con seguimiento.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas.  Como alternativa, puedes usar la nueva [funcionalidad co_await](/windows/uwp/cpp-and-winrt-apis/concurrency) compatible con C++/WinRT.

Una vez que tenga un objeto HandMeshObserver, debe retenerlo mientras su spatialInteractionSource correspondiente esté activo.  A continuación, cada fotograma puede solicitarle el búfer de vértice más reciente que representa la mano llamando a [GetVertexStateForPose](/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) y pasando una instancia [de HandPose](/uwp/api/windows.perception.people.handpose) que representa la posición para la que desea vertices.  Cada vértice del búfer tiene una posición y una normal.  Este es un ejemplo de cómo obtener el conjunto actual de vértices para una malla de mano.  Como antes, la variable *currentState* representa una instancia de [SpatialInteractionSourceState.](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

A diferencia de las juntas de esqueleto, la API de malla de mano no permite especificar un sistema de coordenadas para los vértices.  En su lugar, [HandMeshVertexState](/uwp/api/windows.perception.people.handmeshvertexstate) especifica el sistema de coordenadas en el que se proporcionan los vértices.  A continuación, puede obtener una transformación de malla llamando a [TryGetTransformTo](/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) y especificando el sistema de coordenadas que desee.  Deberá usar esta transformación de malla siempre que trabaje con los vértices.  Este enfoque reduce la sobrecarga de CPU, especialmente si solo usa la malla con fines de representación.

## <a name="gaze-and-commit-composite-gestures"></a>Gestos compuestos de mirada y confirmación
Para las aplicaciones que usan el modelo de entrada de mirada y confirmación, especialmente en HoloLens (primera generación), spatial input API proporciona un [spatialGestureRecognizer](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) opcional que se puede usar para habilitar gestos compuestos creados sobre el evento "select".  Mediante el enrutamiento de interacciones de SpatialInteractionManager a SpatialGestureRecognizer de un holograma, las aplicaciones pueden detectar eventos de pulsación, retención, manipulación y navegación uniformemente entre las manos, la voz y los dispositivos de entrada espacial, sin tener que controlar las presiones y las versiones manualmente.

SpatialGestureRecognizer solo realiza la desambiguación mínima entre el conjunto de gestos que se solicita. Por ejemplo, si solo solicita Pulsar, el usuario puede mantener presionado el dedo siempre que quiera y se producirá una pulsación. Si solicita Pulsar y Mantener presionado, después de aproximadamente un segundo de mantener presionado el dedo, el gesto se promoverá a Hold (Mantener) y ya no se producirá una pulsación.

Para usar SpatialGestureRecognizer, controle el evento [InteractionDetected](/uwp/api/Windows.UI.Input.Spatial.SpatialInteractionManager) de SpatialInteractionManager y tome el SpatialPointerPose expuesto allí. Use el rayo de mirada con la cabeza del usuario de esta posición para formar una intersección con los hologramas y las mallas de superficie en el entorno del usuario para determinar con qué pretende interactuar el usuario. A continuación, enruta SpatialInteraction en los argumentos de evento al spatialGestureRecognizer del holograma de destino, mediante su [método CaptureInteraction.](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer) Esto comienza a interpretar esa interacción según el valor [de SpatialGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureSettings) establecido en ese reconocedor en el momento de la creación o [por TrySetGestureSettings](/uwp/api/Windows.UI.Input.Spatial.SpatialGestureRecognizer).

En HoloLens (primera generación), las interacciones y los gestos deben derivar su destino de la mirada con la cabeza del usuario, en lugar de representar o interactuar en la ubicación de la mano. Una vez iniciada una interacción, se pueden usar movimientos relativos de la mano para controlar el gesto, como con el gesto Manipulación o Navegación.

## <a name="see-also"></a>Consulte también
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Modelo de entrada de manipulación directa](../../design/direct-manipulation.md)
* [Modelo de entrada de punto y confirmación](../../design/point-and-commit.md)
* [Modelo de entrada de mirada y confirmación](../../design/gaze-and-commit.md)
* [Controladores de movimiento](../../design/motion-controllers.md)