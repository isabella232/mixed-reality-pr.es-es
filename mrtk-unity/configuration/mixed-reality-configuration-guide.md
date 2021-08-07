---
title: Guía de configuración de perfiles de MRTK
description: Documentación para configurar MRTK en Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK,
ms.openlocfilehash: e18695610b5e07c4f811e7c43bc13607857a9459407f9b16f39d4f7350f354e6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215005"
---
# <a name="mrtk-profile-configuration-guide"></a>Guía de configuración de perfiles de MRTK

El Mixed Reality Toolkit centralizar la mayor parte de la configuración necesaria para administrar el kit de herramientas como sea posible (excepto para las verdaderas "cosas" en tiempo de ejecución).

Esta guía es un tutorial sencillo para cada una de las pantallas de perfil de configuración disponibles actualmente para el kit de herramientas.

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a>Perfil de configuración Mixed Reality Toolkit principal

El perfil de configuración principal, que está asociado al gameObject *MixedRealityToolkit* de la escena, proporciona el punto de entrada principal para la Toolkit en el proyecto.

> [!NOTE]
> El Mixed Reality Toolkit "bloquea" las pantallas de configuración predeterminadas para asegurarse de que siempre tiene un punto de inicio común para el proyecto y se recomienda empezar a definir su propia configuración a medida que evoluciona el proyecto. La configuración de MRTK no se puede editar durante el modo de reproducción.

![Perfil de configuración de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

Todos los perfiles "predeterminados" de la Mixed Reality Toolkit pueden encontrarse en el proyecto del SDK en la carpeta Assets/MRTK/SDK/Profiles.

> [!IMPORTANT]
> DefaultHoloLens2ConfigurationProfile está optimizado para HoloLens 2. Consulte [Perfiles para](../features/profiles/profiles.md) obtener más información.

Al abrir el perfil Mixed Reality Toolkit configuración principal, verá la siguiente pantalla en el inspector:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

Si selecciona un recurso MixedRealityToolkitConfigurationProfile sin MixedRealityToolkit en la escena, se le preguntará si desea que MRTK configure automáticamente la escena. Sin embargo, esto es opcional, debe haber un objeto MixedRealityToolkit activo en la escena para acceder a todas las pantallas de configuración.

Esto aloja la configuración actual del entorno de ejecución activo para el proyecto.

Desde aquí puede navegar a todos los perfiles de configuración de MRTK, incluidos:

- [Mixed Reality Toolkit de configuración de perfiles](#mrtk-profile-configuration-guide)
  - [Perfil de configuración Mixed Reality Toolkit principal](#the-main-mixed-reality-toolkit-configuration-profile)
  - [Configuración de la experiencia](#experience-settings)
  - [Configuración de la cámara](#camera-settings)
  - [Configuración del sistema de entrada](#input-system-settings)
  - [Configuración de visualización de límites](#boundary-visualization-settings)
  - [Selección del sistema de teleportación](#teleportation-system-selection)
  - [Configuración de reconocimiento espacial](#spatial-awareness-settings)
  - [Configuración de diagnóstico](#diagnostics-settings)
  - [Configuración del sistema de escena](#scene-system-settings)
  - [Configuración de servicios adicionales](#additional-services-settings)
  - [Configuración de acciones de entrada](#input-actions-settings)
  - [Reglas de acciones de entrada](#input-actions-rules)
  - [Configuración de puntero](#pointer-configuration)
  - [Configuración de gestos](#gestures-configuration)
  - [Comandos de voz](#speech-commands)
  - [Configuración de asignación de controladores](#controller-mapping-configuration)
  - [Configuración de visualización del controlador](#controller-visualization-settings)
  - [Utilidades del editor](#editor-utilities)
    - [Inspectores de servicio](#service-inspectors)
    - [Representador de búfer de profundidad](#depth-buffer-renderer)
  - [Cambio de perfiles en tiempo de ejecución](#changing-profiles-at-runtime)
    - [Modificador de perfil de inicialización de MRTK anterior](#pre-mrtk-initialization-profile-switch)
    - [Conmutador de perfil activo](#active-profile-switch)
  - [Consulte también](#see-also)

Estos perfiles de configuración se detallan a continuación en sus secciones pertinentes:

---
<a name="experience"></a>

## <a name="experience-settings"></a>Configuración de la experiencia

Ubicado en la página Mixed Reality Toolkit configuración principal, esta configuración define la operación predeterminada de la escala de Mixed Reality [del](/windows/mixed-reality/coordinate-systems-in-unity) proyecto.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a>Configuración de la cámara

La configuración de la cámara define cómo se configurará la cámara para el proyecto de Mixed Reality, definiendo la configuración genérica de recorte, calidad y transparencia.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a>Configuración del sistema de entrada

El Mixed Reality Project proporciona un sistema de entrada sólido y bien entrenado para enrutar todos los eventos de entrada alrededor del proyecto que está seleccionado de forma predeterminada.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

Detrás del sistema de entrada proporcionado por MRTK hay otros sistemas, que ayudan a impulsar y administrar las complejas intercalaciones necesarias para abstraer las complejidades de un marco multiplataforma o de realidad mixta.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

Cada uno de los perfiles individuales se detalla a continuación:

- Enfoque Configuración
- [Configuración de acciones de entrada](#input-actions-settings)
- [Reglas de acciones de entrada](#input-actions-rules)
- [Configuración de puntero](#pointer-configuration)
- [Configuración de gestos](#gestures-configuration)
- [Comandos de voz](#speech-commands)
- [Configuración de asignación de controladores](#controller-mapping-configuration)
- [Configuración de visualización del controlador](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a>Configuración de visualización de límites

El sistema de límites traduce el límite percibido notificado por el sistema de protección o límite de las plataformas subyacentes. La configuración del visualizador de límites le ofrece la capacidad de mostrar automáticamente el límite registrado dentro de la escena en relación con la posición del usuario. El límite también reaccionará o actualizará en función de dónde se teleporte el usuario dentro de la escena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a>Selección del sistema de teleportación

El Mixed Reality Project proporciona un sistema de teleportación completo para administrar eventos de teleportación en el proyecto que está seleccionado de forma predeterminada.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a>Configuración de reconocimiento espacial

El Mixed Reality Project proporciona un sistema de reconocimiento espacial creado para trabajar con sistemas de examen espacial en el proyecto que está seleccionado de forma predeterminada.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

La Mixed Reality Toolkit de reconocimiento espacial le permite adaptar cómo se inicia el sistema, ya sea automáticamente cuando se inicia la aplicación o posterior mediante programación, así como establecer las extensiones para el campo de vista.

También le permite configurar la malla y la superficie, personalizando aún más cómo el proyecto entiende el entorno que le rodea.

Esto solo es aplicable a los dispositivos que pueden proporcionar un entorno analizado.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a>Configuración de diagnóstico

Una característica opcional pero muy útil de MRTK es la funcionalidad de diagnóstico del complemento.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

El perfil de diagnóstico proporciona varios sistemas sencillos para supervisar mientras se ejecuta el proyecto, incluido un práctico conmutador de encendido y apagado para habilitar o deshabilitar el panel de visualización en la escena.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a>Configuración del sistema de escena

MRTK proporciona este servicio opcional para ayudarle a administrar la carga y descarga complejas de la escena de adición. Para decidir si scene system sería una buena opción para el proyecto, lea scene system Tareas iniciales Guide (Guía de configuración [del sistema de Tareas iniciales escena).](../features/scene-system/scene-system-getting-started.md)

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a>Configuración de servicios adicionales

Una de las áreas más avanzadas de [](https://en.wikipedia.org/wiki/Service_locator_pattern) la Mixed Reality Toolkit es su implementación del patrón de localizador de servicios que permite el registro de cualquier "servicio" con el marco. Esto permite ampliar el marco con nuevas características o sistemas fácilmente, pero también permite que los proyectos aprovechen estas funcionalidades para registrar sus propios componentes en tiempo de ejecución.

Cualquier servicio registrado sigue aprovechando al máximo todos los eventos de Unity, sin la sobrecarga y el costo de implementar patrones monobehaviour o singleton desordenados. Esto permite componentes de C# puros sin sobrecarga de escena para ejecutar procesos en primer plano y en segundo plano, por ejemplo, generación de sistemas, lógica de juego en tiempo de ejecución o prácticamente cualquier otra cosa.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a>Configuración de acciones de entrada

Las acciones de entrada proporcionan una manera de abstraer las interacciones físicas y las entradas de un proyecto en tiempo de ejecución. Toda la entrada física (de controladores, manos, mouse, etc.) se traduce en una acción de entrada lógica para su uso en el proyecto en tiempo de ejecución. Esto garantiza que, independientemente de dónde procede la entrada, el proyecto simplemente implementa estas acciones como "Cosas que hacer" o "Interactuar con" en sus escenas.

Para crear una nueva acción de entrada, simplemente haga clic en el botón "Agregar una nueva acción" y escriba un nombre de texto descriptivo para lo que representa. A continuación, solo necesita seleccionar un eje (el tipo de datos) que la acción está pensada para transmitir, o en el caso de los controladores físicos, el tipo de entrada física al que se puede adjuntar, por ejemplo:

| Restricción de eje | Tipo de datos | Descripción | Ejemplo de uso |
| :--- | :--- | :--- | :--- |
| Ninguno | Sin datos | Se usa para una acción o un evento vacíos. | Desencadenador de eventos |
| Sin procesar (reservado) | objeto | Reservado para uso futuro | N/D |
| Digital | bool | Datos de tipo booleanos on o off | Un botón de controlador |
| Eje único | FLOAT | Un valor de datos de precisión única | Una entrada de intervalo, por ejemplo, un desencadenador |
| Eje dual | Vector2 | Una fecha de tipo float dual para varios ejes | Un Dpad o thumbstick |
| Posición de tres dof | Vector3 | Datos de tipo posicional de con 3 ejes flotantes | Controlador solo de estilo de posición 3D |
| Rotación de tres dof | Quaternion | Entrada de solo rotación con 4 ejes flotantes | Un controlador de estilo de tres grados, por ejemplo, el controlador Oculus Go |
| Seis dof | Mixed Reality Pose (Vector3, Quaternion) | Entrada de estilo de posición y rotación con los componentes Vector3 y Quaternion | Un controlador de movimiento o un puntero |

Los eventos que usan acciones de entrada no se limitan a los controladores físicos y todavía se pueden usar en el proyecto para que los efectos en tiempo de ejecución generen nuevas acciones.

> [!NOTE]
> Las acciones de entrada son uno de los pocos componentes que no se pueden editar en tiempo de ejecución, son solo una configuración en tiempo de diseño. Este perfil no se debe intercambiar mientras el proyecto se ejecuta debido a la dependencia del marco (y los proyectos) en los identificadores generados para cada acción.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a>Reglas de acciones de entrada

Las reglas de acción de entrada proporcionan una manera de traducir automáticamente un evento que se genera para una acción de entrada en a acciones diferentes en función de su valor de datos. Estos se administran sin problemas dentro del marco de trabajo y no incurren en ningún costo de rendimiento.

Por ejemplo, convertir el evento de entrada de eje dual único de un DPad en las 4 acciones "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" correspondientes (como se muestra en la imagen siguiente).

Esto también se puede hacer en su propio código. Sin embargo, al ver que se trata de un patrón muy común, el marco proporciona un mecanismo para hacerlo "de forma lista".

Las reglas de acción de entrada se pueden configurar para cualquiera de los ejes de entrada disponibles. Sin embargo, las acciones de entrada de un tipo de eje se pueden traducir a otra acción de entrada del mismo tipo de eje. Puede asignar una acción de eje dual a otra acción de eje dual, pero no a una acción digital o ninguna.

![Perfil de reglas de acción de entrada](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a>Configuración del puntero

Los punteros se usan para impulsar la interactividad en la escena desde cualquier dispositivo de entrada, lo que da una dirección y una prueba de acceso con cualquier objeto de una escena (que tiene un colisionador asociado o es un componente de la interfaz de usuario). De forma predeterminada, los punteros se configuran automáticamente para controladores, cascos (mirada/foco) y entrada táctil o de mouse.

Los punteros también se pueden visualizar dentro de la escena activa mediante uno de los muchos componentes de línea proporcionados por el Mixed Reality Toolkit o cualquiera de los suyos propios si implementan la interfaz IMixedRealityPointer de MRTK.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- Extensión de apuntar: determina la extensión de apuntar global para todos los punteros, incluida la mirada.
- Máscaras de capa de Raycast que apuntan: determina con qué capas se van a convertir los punteros.
- Debug Draw Pointing Ray: asistente de depuración para visualizar los rayos usados para la difusión de rayos.
- Depurar los colores de los rayos de dibujo que apuntan: un conjunto de colores que se usarán para visualizar.
- Prefab de cursor de mirada: facilita la especificación de un cursor de mirada global para cualquier escena.

Hay un botón auxiliar adicional para saltar rápidamente al proveedor de miradas para invalidar algunos valores específicos de Gaze si es necesario.

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a>Configuración de gestos

Los gestos son una implementación específica del sistema que permite asignar acciones de entrada a los distintos métodos de entrada "Gesto" proporcionados por varios SDK (por ejemplo, HoloLens).

> [!NOTE]
> La implementación actual de Gestos es solo para el HoloLens y se mejorará para otros sistemas a medida que se agregan al Toolkit en el futuro (aún no hay fechas).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a>Comandos de voz

Al igual que los gestos, algunas plataformas en tiempo de ejecución también proporcionan funcionalidad "Speech to Text" inteligente con la capacidad de generar comandos que un proyecto de Unity puede recibir. Este perfil de configuración permite configurar lo siguiente:

1. El Configuración general: "Comportamiento de inicio" establecido en Inicio automático o Inicio manual determina si inicializar KeywordRecognizer al iniciar el sistema de entrada o dejar que el proyecto decida cuándo inicializar KeywordRecognizer. "Nivel de confianza de reconocimiento" se usa para inicializar la [API KeywordRecognizer de](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity
2. Comandos de voz: registra "palabras" y las traduce en a acciones de entrada que el proyecto puede recibir. También se pueden adjuntar a las acciones del teclado si es necesario.

> [!IMPORTANT]
> Actualmente, el sistema solo admite voz cuando se ejecuta en plataformas de Windows 10, por ejemplo, escritorio de HoloLens y Windows 10, y se mejorará para otros sistemas a medida que se agregan a MRTK en el futuro (aún no hay fechas).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a>Configuración de asignación de controladores

Una de las pantallas de configuración principales de la Mixed Reality Toolkit es la capacidad de configurar y asignar los distintos tipos de controladores que puede usar el proyecto.

La pantalla de configuración siguiente permite configurar cualquiera de los controladores reconocidos actualmente por el kit de herramientas.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

MRTK proporciona una configuración predeterminada para los siguientes controladores o sistemas:

- Mouse (incluida la compatibilidad con el mouse espacial 3D)
- Pantalla táctil
- Mandos de Xbox
- Windows Mixed Reality controladores
- HoloLens Gestos
- CONTROLADORES DE WAND DE LA WAND DE LA PROGRAMACIÓN
- Controladores táctiles de Oculus
- Controlador remoto de Oculus
- Dispositivos OpenVR genéricos (solo usuarios avanzados)

Al hacer clic en la imagen de cualquiera de los sistemas de controlador pre built, puede configurar una sola acción de entrada para todas sus entradas correspondientes; por ejemplo, consulte la pantalla de configuración del controlador táctil de Oculus a continuación:

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

También hay una pantalla avanzada para configurar otros controladores de entrada de OpenVR o Unity que no se han identificado anteriormente.

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a>Configuración de visualización del controlador

Además de la asignación del controlador, se proporciona un perfil de configuración independiente para personalizar cómo se presentan los controladores en sus escenas.

Esto se puede configurar en un "Global" (todas las instancias de un controlador para una mano específica) o específico de un tipo de controlador o mano individual.

MRTK también admite modelos de controlador de SDK nativos para Windows Mixed Reality y OpenVR. Se cargan como GameObjects en la escena y se posicionan mediante el seguimiento del controlador de la plataforma.

Si la representación del controlador en la escena debe desplazarse desde la posición del controlador físico, simplemente establezca ese desplazamiento con respecto al prefab del modelo de controlador (por ejemplo, establecer la posición de transformación del prefab del controlador con una posición de desplazamiento).

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a>Utilidades del editor

Las utilidades siguientes solo funcionan en el editor y son útiles para mejorar la productividad del desarrollo.

![Utilidades de configuración del editor de MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a>Inspectores de servicio

Los inspectores de servicio son una característica solo del editor que genera objetos en escena que representan servicios activos. Al seleccionar estos objetos se muestran inspectores que ofrecen vínculos de documentación, control sobre las visualizaciones del editor e información sobre el estado del servicio.

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

Para habilitar los inspectores de servicio, *active Usar inspectores* de servicio en *Editor Configuración* el perfil de configuración.

### <a name="depth-buffer-renderer"></a>Representador de búfer de profundidad

Compartir el búfer de profundidad con algunas plataformas de realidad mixta puede mejorar la [estabilización del holograma.](../performance/hologram-stabilization.md) Por ejemplo, la plataforma de Windows Mixed Reality puede modificar la escena representada por píxel para tener en cuenta los movimientos sutiles de la cabeza durante el tiempo que se tardó en representar un fotograma. Sin embargo, estas técnicas requieren búferes de profundidad con datos precisos para saber dónde y a qué distancia está la geometría del usuario.

Para asegurarse de que una escena representa todos los  datos necesarios en el búfer de profundidad, los desarrolladores pueden alternar la característica Búfer de profundidad de *representación en* Editor Configuración en el perfil de configuración. Esto tomará el búfer de profundidad actual y lo representará como color en la vista de escena aplicando un efecto posterior al procesamiento, , a [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) la cámara principal.

![Utilidad de búfer de profundidad de representación El cilindro azul de la escena tiene un ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>material con ZWrite</sup> desactivado para que no se escriban datos de profundidad

## <a name="changing-profiles-at-runtime"></a>Cambio de perfiles en tiempo de ejecución

Es posible actualizar perfiles en tiempo de ejecución y, por lo general, hay dos escenarios y horas diferentes en los que esto resulta útil:

1. Modificador de perfil de inicialización de **MRTK** anterior: en el inicio, antes de inicializar MRTK y de que el perfil se active, reemplazando el perfil que aún no está en uso para habilitar o deshabilitar diferentes características en función de las funcionalidades del dispositivo. Por ejemplo, si la experiencia se ejecuta en REALIDAD virtual que no tiene hardware de asignación espacial, probablemente no tenga sentido tener habilitado el componente de asignación espacial.
1. **Conmutador de perfil** activo: después del inicio, después de inicializar MRTK y de que se haya activado un perfil, cambie el perfil actualmente en uso para cambiar la forma en que se comportan determinadas características. Por ejemplo, puede haber una sub experiencia específica en la aplicación que quiera quitar completamente los punteros de mano lejanos.

### <a name="pre-mrtk-initialization-profile-switch"></a>Modificador de perfil de inicialización de MRTK anterior

Esto se puede lograr asociando un monobehaviour (ejemplo siguiente) que se ejecuta antes de la inicialización de MRTK (es decir, con El activo()). Tenga en cuenta que el script (es decir, llamar a ) debe ejecutarse antes que el script, lo que se puede lograr estableciendo la configuración del orden `SetProfileBeforeInitialization` `MixedRealityToolkit` de ejecución del [script.](https://docs.unity3d.com/Manual/class-MonoManager.html)

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

En lugar de "profileToUse", es posible tener un conjunto arbitrario de perfiles que se aplican a plataformas específicas (por ejemplo, uno para HoloLens 1, otro para VR, otro para HoloLens 2, etc.). Es posible usar otros indicadores (por ejemplo, , o si la cámara es opaca o transparente), para averiguar qué perfil https://docs.unity3d.com/ScriptReference/SystemInfo.html cargar.

### <a name="active-profile-switch"></a>Conmutador de perfil activo

Esto se puede lograr estableciendo la `MixedRealityToolkit.Instance.ActiveProfile` propiedad en un nuevo perfil reemplazando el perfil activo.

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

Tenga en cuenta que al establecer durante el tiempo de ejecución, la destrucción de los servicios en ejecución se realizará después de la última lateupdate() de todos los servicios y la creación de instancias e inicialización de los servicios asociados con el nuevo perfil se realizará antes de la primera Actualización() de todos los `ActiveProfile` servicios.

Durante este proceso puede producirse un error apreciable en la aplicación. Además, cualquier script con mayor prioridad que el script puede escribir su actualización antes de `MixedRealityToolkit` que el nuevo perfil se configure correctamente. Consulte [Configuración del orden de ejecución del script](https://docs.unity3d.com/Manual/class-MonoManager.html) para obtener más información sobre la prioridad del script.

En el proceso de cambio de perfil, la cámara de interfaz de usuario existente permanecerá sin cambios, lo que garantiza que los componentes de la interfaz de usuario de Unity que requieren lienzo sigan funcionando después del cambio.

## <a name="see-also"></a>Consulte también

- [Estabilización de hologramas](../performance/hologram-stabilization.md)
