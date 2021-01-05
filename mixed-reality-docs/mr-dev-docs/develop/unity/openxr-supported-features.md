---
title: Características compatibles con el complemento OpenXR en Unity
description: Descubra las características que OpenXR admite para el desarrollo de la realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: 94ec7ae6c89dea8f953fea6f4c794ca51e044d87
ms.sourcegitcommit: 5784336a780486d05db6a627839efe47f08fac36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97880589"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="5fafa-104">Características admitidas de OpenXR de realidad mixta en Unity</span><span class="sxs-lookup"><span data-stu-id="5fafa-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="5fafa-105">El paquete de **Complementos OpenXR de realidad mixta** es una extensión del **complemento OpenXR** de Unity y admite un conjunto de características para los auriculares HoloLens 2 y Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5fafa-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="5fafa-106">Antes de continuar, asegúrese de que ha instalado **unity 2020,2** o posterior, **OpenXR plugin versión 0.1.1** o posterior y el proyecto de Unity está [configurado para OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="5fafa-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="5fafa-107">Lo que se admite</span><span class="sxs-lookup"><span data-stu-id="5fafa-107">What's supported</span></span>

<span data-ttu-id="5fafa-108">Actualmente se admiten las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="5fafa-108">The following features are currently supported:</span></span>

* <span data-ttu-id="5fafa-109">Admite aplicaciones para UWP para aplicaciones de HoloLens 2 y Win32 VR para auriculares con Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="5fafa-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="5fafa-110">Optimiza el paquete UWP y la interacción con CoreWindow para aplicaciones de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="5fafa-111">Seguimiento de escala mundial con delimitadores y espacio sin enlazar.</span><span class="sxs-lookup"><span data-stu-id="5fafa-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="5fafa-112">[Delimite la API de almacenamiento para conservar los delimitadores](#anchors-and-anchor-persistence) en el almacenamiento local de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="5fafa-113">Control de [movimiento y interacciones de mano](#motion-controller-and-hand-interactions), incluido el nuevo controlador de HP reverberación G2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="5fafa-114">Seguimiento de mano articulado mediante 26 uniones y entradas de radio uniones.</span><span class="sxs-lookup"><span data-stu-id="5fafa-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="5fafa-115">Interacción de ojo mirada en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="5fafa-116">Buscar la cámara de foto/vídeo (PV) en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="5fafa-117">Captura de realidad mixta mediante la representación de la tercera vista a través de la cámara PV.</span><span class="sxs-lookup"><span data-stu-id="5fafa-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="5fafa-118">Admite ["Play" en HoloLens 2 con la aplicación de comunicación remota holográfica](#holographic-remoting-in-unity-editor-play-mode), lo que permite a los desarrolladores depurar scripts sin compilar e implementar en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5fafa-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="5fafa-119">Compatible con MRTK Unity 2.5.2 y versiones más recientes a través de la compatibilidad con el proveedor de MRTK OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5fafa-119">Compatible with MRTK Unity 2.5.2 and newer through MRTK OpenXR provider support.</span></span> <span data-ttu-id="5fafa-120">[Consulte la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) para empezar a trabajar.</span><span class="sxs-lookup"><span data-stu-id="5fafa-120">[See the MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) to get started.</span></span>
* <span data-ttu-id="5fafa-121">Compatible con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior</span><span class="sxs-lookup"><span data-stu-id="5fafa-121">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="5fafa-122">Holographic Remoting en el modo de reproducción del editor de Unity</span><span class="sxs-lookup"><span data-stu-id="5fafa-122">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="5fafa-123">Compilar un proyecto de Unity de UWP en un proyecto de Visual Studio y, luego, empaquetarlo e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo.</span><span class="sxs-lookup"><span data-stu-id="5fafa-123">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="5fafa-124">Una solución es habilitar la comunicación remota del editor holográfica, que le permite depurar el script de C# mediante el modo "reproducir" directamente en un dispositivo HoloLens 2 a través de la red.</span><span class="sxs-lookup"><span data-stu-id="5fafa-124">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="5fafa-125">En este escenario se evita la sobrecarga de crear e implementar un paquete de UWP en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="5fafa-125">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="5fafa-126">En primer lugar, debe [instalar la aplicación de reproductor de comunicación remota holográfica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la tienda en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-126">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="5fafa-127">Ejecute la aplicación holográfica Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a la que se conectará.</span><span class="sxs-lookup"><span data-stu-id="5fafa-127">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="5fafa-128">Necesitará v 2.4 o posterior para trabajar con el complemento OpenXR</span><span class="sxs-lookup"><span data-stu-id="5fafa-128">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de pantalla del reproductor de acceso remoto holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

3. <span data-ttu-id="5fafa-130">Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="5fafa-130">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abrir en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-features-img-02.png)

4. <span data-ttu-id="5fafa-132">Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**</span><span class="sxs-lookup"><span data-stu-id="5fafa-132">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="5fafa-133">Active la casilla de **comunicación remota del editor holográfica** y escriba la dirección IP que obtiene de la aplicación de acceso remoto holográfica:</span><span class="sxs-lookup"><span data-stu-id="5fafa-133">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con características resaltadas](images/openxr-features-img-03.png)

<span data-ttu-id="5fafa-135">Ahora puede hacer clic en el botón "reproducir" para reproducir la aplicación de Unity en la aplicación de acceso remoto holográfica en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5fafa-135">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="5fafa-136">También puede [adjuntar Visual Studio a Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts de C# en el modo de reproducción.</span><span class="sxs-lookup"><span data-stu-id="5fafa-136">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="5fafa-137">A partir de la versión 0.1.0, el tiempo de ejecución de la comunicación remota holográfica no admite delimitadores y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.</span><span class="sxs-lookup"><span data-stu-id="5fafa-137">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="5fafa-138">Esta característica está disponible en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="5fafa-138">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="5fafa-139">Delimitadores y persistencia del delimitador</span><span class="sxs-lookup"><span data-stu-id="5fafa-139">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="5fafa-140">El complemento OpenXR de realidad mixta proporciona la funcionalidad básica de delimitador a través de una implementación de ARFoundation **ARAnchorManager** de Unity.</span><span class="sxs-lookup"><span data-stu-id="5fafa-140">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="5fafa-141">Para obtener información sobre los conceptos básicos de **ARAnchor** s en ARFoundation, visite el [manual de ARFoundation para el administrador de delimitadores de ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="5fafa-141">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="5fafa-142">A partir de la versión 0.1.0, este complemento es compatible con toda la funcionalidad de ARAnchorManager, excepto la creación de delimitadores conectados a un plano, que se publica en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="5fafa-142">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="5fafa-143">Persistencia del delimitador y XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="5fafa-143">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="5fafa-144">Una API adicional denominada **XRAnchorStore** permite que los delimitadores se conserven entre sesiones.</span><span class="sxs-lookup"><span data-stu-id="5fafa-144">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="5fafa-145">XRAnchorStore es una representación de los delimitadores guardados en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5fafa-145">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="5fafa-146">Los delimitadores se pueden conservar de **ARAnchors** en la escena de Unity, cargarse desde el almacenamiento en nuevo **ARAnchors** o eliminarse del almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="5fafa-146">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="5fafa-147">Estos delimitadores se guardan y se cargan en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5fafa-147">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="5fafa-148">El almacenamiento de delimitadores entre dispositivos se admitirá a través de los anclajes espaciales de Azure en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="5fafa-148">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="5fafa-149">Para cargar XRAnchorStore, el complemento proporciona un método de extensión en XRAnchorSubsystem, el subsistema de ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="5fafa-149">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="5fafa-150">Para usar este método de extensión, acceda a él desde el subsistema de ARAnchorManager como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="5fafa-150">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="5fafa-151">Para ver un ejemplo completo de los delimitadores persistentes o no persistentes, consulte el script delimitadores-> delimitadores de ejemplo GameObject y AnchorsSample.cs en la [escena de ejemplo de complemento Mixed Reality OpenXR](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="5fafa-151">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de pantalla del panel de jerarquías abierto en el editor de Unity con el ejemplo de anclajes resaltado](images/openxr-features-img-04.png)

![Captura de pantalla del panel de inspectores abierta en el editor de Unity con el script de ejemplo de delimitadores resaltado](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="5fafa-154">Interacciones de controlador de movimiento y mano</span><span class="sxs-lookup"><span data-stu-id="5fafa-154">Motion controller and hand interactions</span></span>

<span data-ttu-id="5fafa-155">Para conocer los aspectos básicos sobre las interacciones de la realidad mixta en Unity, visite el [manual de Unity para la entrada de Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="5fafa-155">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="5fafa-156">Esta documentación de Unity cubre las asignaciones de entradas específicas del controlador a **InputFeatureUsage** s más generalizadas, cómo se pueden identificar y clasificar las entradas de XR disponibles, cómo leer datos de estas entradas, etc.</span><span class="sxs-lookup"><span data-stu-id="5fafa-156">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="5fafa-157">El complemento OpenXR de realidad mixta proporciona perfiles de interacción de entrada adicionales, asignados a **InputFeatureUsage** s estándar, como se detalla a continuación:</span><span class="sxs-lookup"><span data-stu-id="5fafa-157">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="5fafa-158">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="5fafa-158">InputFeatureUsage</span></span> | <span data-ttu-id="5fafa-159">Controlador de HP reverberación G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="5fafa-159">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="5fafa-160">Mano de HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="5fafa-160">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="5fafa-161">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="5fafa-161">primary2DAxis</span></span> | <span data-ttu-id="5fafa-162">Joystick</span><span class="sxs-lookup"><span data-stu-id="5fafa-162">Joystick</span></span> | |
| <span data-ttu-id="5fafa-163">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="5fafa-163">primary2DAxisClick</span></span> | <span data-ttu-id="5fafa-164">Joystick: haga clic</span><span class="sxs-lookup"><span data-stu-id="5fafa-164">Joystick - Click</span></span> | |
| <span data-ttu-id="5fafa-165">desencadenador</span><span class="sxs-lookup"><span data-stu-id="5fafa-165">trigger</span></span> | <span data-ttu-id="5fafa-166">Desencadenador</span><span class="sxs-lookup"><span data-stu-id="5fafa-166">Trigger</span></span>  | |
| <span data-ttu-id="5fafa-167">sujeta</span><span class="sxs-lookup"><span data-stu-id="5fafa-167">grip</span></span> | <span data-ttu-id="5fafa-168">Sujeta</span><span class="sxs-lookup"><span data-stu-id="5fafa-168">Grip</span></span> | <span data-ttu-id="5fafa-169">Puntear o comprimir el aire</span><span class="sxs-lookup"><span data-stu-id="5fafa-169">Air tap or squeeze</span></span> |
| <span data-ttu-id="5fafa-170">primaryButton</span><span class="sxs-lookup"><span data-stu-id="5fafa-170">primaryButton</span></span> | <span data-ttu-id="5fafa-171">[X/A]-presionar</span><span class="sxs-lookup"><span data-stu-id="5fafa-171">[X/A] - Press</span></span> | <span data-ttu-id="5fafa-172">Pulsar en el aire</span><span class="sxs-lookup"><span data-stu-id="5fafa-172">Air tap</span></span> |
| <span data-ttu-id="5fafa-173">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="5fafa-173">secondaryButton</span></span> | <span data-ttu-id="5fafa-174">[Y/B]-Presione</span><span class="sxs-lookup"><span data-stu-id="5fafa-174">[Y/B] - Press</span></span> | |
| <span data-ttu-id="5fafa-175">gripButton</span><span class="sxs-lookup"><span data-stu-id="5fafa-175">gripButton</span></span> | <span data-ttu-id="5fafa-176">Agarre: presionar</span><span class="sxs-lookup"><span data-stu-id="5fafa-176">Grip - Press</span></span> | |
| <span data-ttu-id="5fafa-177">triggerButton</span><span class="sxs-lookup"><span data-stu-id="5fafa-177">triggerButton</span></span> | <span data-ttu-id="5fafa-178">Desencadenador: Presione</span><span class="sxs-lookup"><span data-stu-id="5fafa-178">Trigger - Press</span></span> | |
| <span data-ttu-id="5fafa-179">menuButton</span><span class="sxs-lookup"><span data-stu-id="5fafa-179">menuButton</span></span> | <span data-ttu-id="5fafa-180">Menú</span><span class="sxs-lookup"><span data-stu-id="5fafa-180">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="5fafa-181">Objetivos y planteamiento</span><span class="sxs-lookup"><span data-stu-id="5fafa-181">Aim and Grip Poses</span></span>

<span data-ttu-id="5fafa-182">Tiene acceso a dos conjuntos de planteamientos a través de las interacciones de entrada de OpenXR:</span><span class="sxs-lookup"><span data-stu-id="5fafa-182">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="5fafa-183">El control tiene que presentar los objetos a mano</span><span class="sxs-lookup"><span data-stu-id="5fafa-183">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="5fafa-184">El objetivo plantea la señal del mundo.</span><span class="sxs-lookup"><span data-stu-id="5fafa-184">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="5fafa-185">Puede encontrar más información sobre este diseño y las diferencias entre las dos supuestos en la [especificación de OpenXR: subtrazados de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="5fafa-185">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="5fafa-186">Las supuestos suministradas por InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** y **DeviceAngularVelocity** representan la representación del **control** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5fafa-186">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="5fafa-187">Los InputFeatureUsages relacionados con los planteamientos de agarre se definen en [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)de Unity.</span><span class="sxs-lookup"><span data-stu-id="5fafa-187">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="5fafa-188">Las supuestos suministradas por InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** y **PointerAngularVelocity** representan la representación de **objetivo** OpenXR.</span><span class="sxs-lookup"><span data-stu-id="5fafa-188">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="5fafa-189">Estos InputFeatureUsages no se definen en ningún archivo de C# incluido, por lo que deberá definir su propia InputFeatureUsages como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="5fafa-189">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="5fafa-190">Hápticos</span><span class="sxs-lookup"><span data-stu-id="5fafa-190">Haptics</span></span>

<span data-ttu-id="5fafa-191">Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el [manual de Unity para entrada-hápticos de Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="5fafa-191">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="5fafa-192">Novedades próximamente</span><span class="sxs-lookup"><span data-stu-id="5fafa-192">What's coming soon</span></span>

<span data-ttu-id="5fafa-193">Los siguientes problemas y las características que faltan se conocen con la **versión 0.1.0** del complemento OpenXR de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="5fafa-193">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="5fafa-194">Estamos trabajando en ellos y publicará correcciones y nuevas características en las próximas versiones.</span><span class="sxs-lookup"><span data-stu-id="5fafa-194">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="5fafa-195">**ARPlaneSubsystem** todavía no se admite.</span><span class="sxs-lookup"><span data-stu-id="5fafa-195">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="5fafa-196">**ARPlaneManager**, **ARRaycastManager** y API relacionada como **ARAnchorManager. AttachAnchor** tampoco se admiten en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-196">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="5fafa-197">El **delimitador** no es compatible aún con la comunicación remota holográfica, pero está próximamente en un futuro.</span><span class="sxs-lookup"><span data-stu-id="5fafa-197">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="5fafa-198">Todavía no se admite el seguimiento de **mallas de mano** , los **códigos QR** y los **XRMeshSubsystem** .</span><span class="sxs-lookup"><span data-stu-id="5fafa-198">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="5fafa-199">La compatibilidad con los **anclajes espaciales de Azure** está disponible en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="5fafa-199">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="5fafa-200">**ARM64** es la única plataforma admitida para las aplicaciones de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="5fafa-200">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="5fafa-201">La plataforma **ARM** está próximamente en una versión futura.</span><span class="sxs-lookup"><span data-stu-id="5fafa-201">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="5fafa-202">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="5fafa-202">Troubleshooting</span></span>

<span data-ttu-id="5fafa-203">Al suspender y reanudar una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5fafa-203">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="5fafa-204">Establezca el **modo de envío de profundidad** en **ninguno** en la configuración del proyecto OpenXR como solución alternativa.</span><span class="sxs-lookup"><span data-stu-id="5fafa-204">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
