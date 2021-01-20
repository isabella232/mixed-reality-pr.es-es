---
title: Características compatibles con el complemento OpenXR en Unity
description: Descubra las características que OpenXR admite para el desarrollo de la realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 09067498d33fb2c96da53aa54c0449959355d809
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583512"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Características admitidas de OpenXR de realidad mixta en Unity

El paquete de **Complementos OpenXR de realidad mixta** es una extensión del **complemento OpenXR** de Unity y admite un conjunto de características para los auriculares HoloLens 2 y Windows Mixed Reality. Antes de continuar, asegúrese de que ha instalado **unity 2020,2** o posterior, **OpenXR plugin versión 0.1.2** o posterior y el proyecto de Unity está [configurado para OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Lo que se admite

Actualmente se admiten las siguientes características:

* Admite aplicaciones de UWP para HoloLens 2 y optimizar para el modelo de aplicación de HoloLens 2.
* Admite aplicaciones Win32 VR para auriculares con Windows Mixed Reality con los perfiles de controlador más recientes y la comunicación remota de la aplicación holográfica.
* Seguimiento de escala mundial con delimitadores y espacio sin enlazar.
* [Delimite la API de almacenamiento para conservar los delimitadores](#anchors-and-anchor-persistence) en el almacenamiento local de HoloLens 2.
* Control de [movimiento y interacciones de mano](#motion-controller-and-hand-interactions), incluido el nuevo controlador de HP reverberación G2.
* Seguimiento de mano articulado mediante 26 uniones y entradas de radio uniones.
* Interacción de ojo mirada en HoloLens 2.
* Buscar la cámara de foto/vídeo (PV) en HoloLens 2.
* Captura de realidad mixta mediante la representación de la tercera vista a través de la cámara PV.
* Admite ["Play" en HoloLens 2 con la aplicación de comunicación remota holográfica](#holographic-remoting-in-unity-editor-play-mode), lo que permite a los desarrolladores depurar scripts sin compilar e implementar en el dispositivo.
* Compatible con MRTK Unity 2.5.3 y versiones más recientes a través de la compatibilidad con el [proveedor de MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).
* Compatible con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting en el modo de reproducción del editor de Unity

Compilar un proyecto de Unity de UWP en un proyecto de Visual Studio y, luego, empaquetarlo e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la comunicación remota del editor holográfica, que le permite depurar el script de C# mediante el modo "reproducir" directamente en un dispositivo HoloLens 2 a través de la red. En este escenario se evita la sobrecarga de crear e implementar un paquete de UWP en un dispositivo remoto.

1. En primer lugar, debe [instalar la aplicación de reproductor de comunicación remota holográfica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la tienda en HoloLens 2.
2. Ejecute la aplicación holográfica Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a la que se conectará.
    * Necesitará v 2.4 o posterior para trabajar con el complemento OpenXR

    ![Captura de pantalla del reproductor de acceso remoto holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

3. Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** :

    ![Captura de pantalla del panel de configuración del proyecto abrir en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-features-img-02.png)

4. Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**
5. Active la casilla de **comunicación remota del editor holográfica** y escriba la dirección IP que obtiene de la aplicación de acceso remoto holográfica:

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "reproducir" para reproducir la aplicación de Unity en la aplicación de acceso remoto holográfica en HoloLens. También puede [adjuntar Visual Studio a Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0, el tiempo de ejecución de la comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica está disponible en futuras versiones.

## <a name="anchors-and-anchor-persistence"></a>Delimitadores y persistencia del delimitador

El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity. Para obtener información sobre los conceptos básicos de **ARAnchor** s en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html). A partir de la versión 0.1.0, este complemento es compatible con toda la funcionalidad de ARAnchorManager, excepto la creación de delimitadores conectados a un plano, que se publica en una versión futura.

### <a name="anchor-persistence-and-the-xranchorstore"></a>Persistencia del delimitador y XRAnchorStore

Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones. XRAnchorStore es una representación de los delimitadores guardados en el dispositivo. Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.

> [!NOTE]
> Estos delimitadores se guardan y se cargan en el mismo dispositivo. El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Para ver un ejemplo completo de los delimitadores persistentes o no persistentes, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample.cs en la [escena de ejemplo de complemento Mixed Reality OpenXR](openxr-getting-started.md#hololens-2-samples):

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a>Interacciones de controlador de movimiento y mano

Para conocer los aspectos básicos sobre las interacciones de la realidad mixta en Unity, visite el [manual de Unity para la entrada de Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentación de Unity cubre las asignaciones de entradas específicas del controlador a **InputFeatureUsage** s más generalizadas, cómo se pueden identificar y clasificar las entradas de XR disponibles, cómo leer datos de estas entradas, etc.

El complemento OpenXR de realidad mixta proporciona perfiles de interacción de entrada adicionales, asignados a **InputFeatureUsage** s estándar, como se detalla a continuación:

| InputFeatureUsage | Controlador de HP reverberación G2 (OpenXR) | Mano de HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick: haga clic | |
| desencadenador | Desencadenador  | |
| sujeta | Sujeta | Puntear o comprimir el aire |
| primaryButton | [X/A]-presionar | Pulsar en el aire |
| secondaryButton | [Y/B]-Presione | |
| gripButton | Agarre: presionar | |
| triggerButton | Desencadenador: Presione | |
| menuButton | Menú | |

### <a name="aim-and-grip-poses"></a>Objetivos y planteamiento

Tiene acceso a dos conjuntos de planteamientos a través de las interacciones de entrada de OpenXR:

* El control tiene que presentar los objetos a mano
* El objetivo plantea la señal del mundo.

Puede encontrar más información sobre este diseño y las diferencias entre las dos supuestos en la [especificación de OpenXR: subtrazados de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

Las supuestos suministradas por InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** y **DeviceAngularVelocity** representan la representación del **control** OpenXR. Los InputFeatureUsages relacionados con los planteamientos de agarre se definen en [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)de Unity.

Las supuestos suministradas por InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** y **PointerAngularVelocity** representan la representación de **objetivo** OpenXR. Estos InputFeatureUsages no se definen en ningún archivo de C# incluido, por lo que deberá definir su propia InputFeatureUsages como se indica a continuación:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a>Hápticos

Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el [manual de Unity para entrada-hápticos de Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="whats-coming-soon"></a>Novedades próximamente

Los siguientes problemas y las características que faltan se conocen con la **versión 0.1.0** del complemento OpenXR de realidad mixta. Estamos trabajando en ellos y publicará correcciones y nuevas características en las próximas versiones.

* **ARPlaneSubsystem** todavía no se admite. **ARPlaneManager**, **ARRaycastManager** y API relacionada como **ARAnchorManager. AttachAnchor** tampoco se admiten en HoloLens 2.
* El **delimitador** no es compatible aún con la comunicación remota holográfica, pero está próximamente en un futuro.
* Todavía no se admite el seguimiento de **mallas de mano** , los **códigos QR** y los **XRMeshSubsystem** .
* La compatibilidad con los **anclajes espaciales de Azure** está disponible en una versión futura.
* **ARM64** es la única plataforma admitida para las aplicaciones de HoloLens 2. La plataforma **ARM** está próximamente en una versión futura.

## <a name="troubleshooting"></a>Solución de problemas

Al suspender y reanudar una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista de HoloLens.
* Establezca el **modo de envío de profundidad** en **ninguno** en la configuración del proyecto OpenXR como solución alternativa.