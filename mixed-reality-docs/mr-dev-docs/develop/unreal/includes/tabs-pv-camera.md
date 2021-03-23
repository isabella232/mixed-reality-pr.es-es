---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98605190"
---
# <a name="426"></a>[<span data-ttu-id="04242-101">4.26</span><span class="sxs-lookup"><span data-stu-id="04242-101">4.26</span></span>](#tab/426) 

## <a name="pv-camera-feed-setup"></a><span data-ttu-id="04242-102">Configuración de la fuente de la cámara de fotos y vídeo</span><span class="sxs-lookup"><span data-stu-id="04242-102">PV Camera Feed Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04242-103">La cámara de fotos y vídeo se implementa en los complementos de Windows Mixed Reality y OpenXR.</span><span class="sxs-lookup"><span data-stu-id="04242-103">PV camera is implemented in both Windows Mixed Reality and OpenXR plugins.</span></span> <span data-ttu-id="04242-104">Sin embargo, OpenXR requiere que el [complemento OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal) esté instalado.</span><span class="sxs-lookup"><span data-stu-id="04242-104">However OpenXR needs [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) to be installed.</span></span> <span data-ttu-id="04242-105">Además, OpenXR tiene una limitación actualmente; la cámara puede funcionar con DirectX11 RHI.</span><span class="sxs-lookup"><span data-stu-id="04242-105">Also OpenXR has current limitation, camera can work with DirectX11 RHI.</span></span> <span data-ttu-id="04242-106">Esta limitación se solucionará en una versión de Unreal posterior.</span><span class="sxs-lookup"><span data-stu-id="04242-106">This limitation will be fixed in a further Unreal version.</span></span> 

- <span data-ttu-id="04242-107">En **Configuración del proyecto > HoloLens**, habilite la funcionalidad **Cámara web**:</span><span class="sxs-lookup"><span data-stu-id="04242-107">In **Project Settings > HoloLens**, enable the **Webcam** capability:</span></span>

![Captura de pantalla de la configuración del proyecto de HoloLens con la propiedad Cámara web resaltada](../images/unreal-pvc-img-01.png)

- <span data-ttu-id="04242-109">Cree un nuevo actor llamado "CamCapture" y agregue un plano para representar la fuente de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-109">Create a new actor called “CamCapture” and add a plane to render the camera feed:</span></span>

![Captura de pantalla de un actor con un plano agregado](../images/unreal-pvc-img-02.png)

- <span data-ttu-id="04242-111">Agregue el actor a la escena, cree un nuevo material denominado CamTextureMaterial con un parámetro de objeto de textura y un ejemplo de textura.</span><span class="sxs-lookup"><span data-stu-id="04242-111">Add the actor to your scene, create a new material called CamTextureMaterial with a Texture Object Parameter, and a texture sample.</span></span>  <span data-ttu-id="04242-112">Envíe los datos RGB de la textura al color emisor de salida:</span><span class="sxs-lookup"><span data-stu-id="04242-112">Send the texture’s rgb data to the output emissive color:</span></span>

![Plano de un ejemplo de material y textura](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a><span data-ttu-id="04242-114">Representación de la fuente de la cámara de fotos y vídeo</span><span class="sxs-lookup"><span data-stu-id="04242-114">Rendering the PV Camera Feed</span></span>

- <span data-ttu-id="04242-115">En el plano técnico CamCapture, active la cámara de fotos y vídeo:</span><span class="sxs-lookup"><span data-stu-id="04242-115">In the CamCapture blueprint, turn on the PV Camera:</span></span>

![Plano técnico de la función Toggle ARCapture con la cámara de fotos y vídeo activada](../images/unreal-pvc-img-04.png)

- <span data-ttu-id="04242-117">Cree una instancia de material dinámico a partir de CamTextureMaterial y asigne este material al plano del actor:</span><span class="sxs-lookup"><span data-stu-id="04242-117">Create a dynamic material instance from CamTextureMaterial and assign this material to the actor’s plane:</span></span>

![Plano técnico de la función Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- <span data-ttu-id="04242-119">Obtenga la textura de la fuente de la cámara y asígnela al material dinámico si es válida.</span><span class="sxs-lookup"><span data-stu-id="04242-119">Get the texture from the camera feed and assign it to the dynamic material if it's valid.</span></span>  <span data-ttu-id="04242-120">Si la textura no es válida, inicie un temporizador y vuelva a intentarlo después del tiempo de espera:</span><span class="sxs-lookup"><span data-stu-id="04242-120">If the texture isn't valid, start a timer and try again after the timeout:</span></span>

![Plano técnico de la textura de la fuente de la cámara asignada al material dinámico](../images/unreal-pvc-img-06.png)

- <span data-ttu-id="04242-122">Por último, escale el plano mediante la relación de aspecto de la imagen de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-122">Finally, scale the plane by the camera image’s aspect ratio:</span></span>

![Plano técnico del plano escalado asociado a la relación de aspecto de las imágenes de la cámara](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a><span data-ttu-id="04242-124">Búsqueda de posiciones de la cámara en el espacio global</span><span class="sxs-lookup"><span data-stu-id="04242-124">Find Camera Positions in World Space</span></span>

<span data-ttu-id="04242-125">La cámara de HoloLens 2 se desplaza verticalmente desde el seguimiento del cabezal del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="04242-125">The camera on the HoloLens 2 is offset vertically from the device’s head tracking.</span></span>  <span data-ttu-id="04242-126">Existen algunas funciones que permiten ubicar la cámara en el espacio global para tenerlo en cuenta para el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="04242-126">A few functions exist to locate the camera in world space to account for the offset.</span></span>

<span data-ttu-id="04242-127">GetPVCameraToWorldTransform obtiene la transformación en el espacio global de la cámara PV y se coloca en la lente de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-127">GetPVCameraToWorldTransform gets the transform in world space of the PV Camera and will be positioned on the camera lens:</span></span>

![Plano técnico de la función Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

<span data-ttu-id="04242-129">GetWorldSpaceRayFromCameraPoint envía un rayo desde la lente de la cámara en la escena del espacio global de Unreal a fin de buscar el contenido de un píxel del encuadre de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-129">GetWorldSpaceRayFromCameraPoint casts a ray from the camera lens into the scene in Unreal world space to find a pixel's content in the camera frame:</span></span>

![Plano técnico de la obtención del rayo del espacio global desde el punto de mira de la cámara](../images/unreal-pvc-img-09.png)

<span data-ttu-id="04242-131">GetPVCameraIntrinsics devuelve los valores intrínsecos de la cámara, que se pueden usar al realizar el procesamiento de Computer Vision en un encuadre de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-131">GetPVCameraIntrinsics returns the camera intrinsic values, which can be used when doing computer vision processing on a camera frame:</span></span>

![Plano técnico de la obtención de las funciones intrínsecas de la cámara de fotos y vídeo](../images/unreal-pvc-img-10.png)

<span data-ttu-id="04242-133">Para buscar lo que hay en el espacio global de una coordenada de píxeles determinada, use un seguimiento de líneas con el rayo del espacio global:</span><span class="sxs-lookup"><span data-stu-id="04242-133">To find what exists in world space at a particular pixel coordinate, use a line trace with the world space ray:</span></span>

![Plano técnico del rayo de espacio global que se usa para averiguar qué hay en el espacio global de una coordenada determinada](../images/unreal-pvc-img-11.png)

<span data-ttu-id="04242-135">Aquí enviamos un rayo de 2 metros desde la lente de la cámara a la posición de un cuarto del espacio de la cámara de la parte superior izquierda del encuadre.</span><span class="sxs-lookup"><span data-stu-id="04242-135">Here we cast a 2-meter ray from the camera lens to the camera-space position ¼ from the top left of the frame.</span></span>  <span data-ttu-id="04242-136">A continuación, use el resultado de posicionamiento para representar un sitio en que el objeto exista en el espacio global:</span><span class="sxs-lookup"><span data-stu-id="04242-136">Then use the hit result to render something where the object exists in world space:</span></span>

![Plano técnico de un envío de un rayo de 2 metros de la lente de la cámara a la posición de un cuarto del espacio de la cámara desde la parte superior izquierda del encuadre.](../images/unreal-pvc-img-12.png)

<span data-ttu-id="04242-138">Cuando se use la asignación espacial, este posicionamiento coincidirá con la superficie que enfoca la cámara.</span><span class="sxs-lookup"><span data-stu-id="04242-138">When using spatial mapping, this hit position will match the surface that the camera is seeing.</span></span>

## <a name="rendering-the-pv-camera-feed-in-c"></a><span data-ttu-id="04242-139">Representación de la fuente de la cámara de fotos y vídeo en C++</span><span class="sxs-lookup"><span data-stu-id="04242-139">Rendering the PV Camera Feed in C++</span></span>

- <span data-ttu-id="04242-140">Cree un nuevo actor de C++ llamado CamCapture.</span><span class="sxs-lookup"><span data-stu-id="04242-140">Create a new C++ actor called CamCapture</span></span>
- <span data-ttu-id="04242-141">En el archivo build.cs del proyecto, agregue "AugmentedReality" en la lista de PublicDependencyModuleNames:</span><span class="sxs-lookup"><span data-stu-id="04242-141">In the project’s build.cs, add “AugmentedReality” to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "AugmentedReality"
});
```

- <span data-ttu-id="04242-142">En CamCapture.h, incluya ARBlueprintLibrary.h.</span><span class="sxs-lookup"><span data-stu-id="04242-142">In CamCapture.h, include ARBlueprintLibrary.h</span></span>

```cpp
#include "ARBlueprintLibrary.h"
```

- <span data-ttu-id="04242-143">También debe agregar variables locales para la malla y el material:</span><span class="sxs-lookup"><span data-stu-id="04242-143">You also need to add local variables for the mesh and material:</span></span>

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- <span data-ttu-id="04242-144">En CamCapture.cpp, actualice el constructor para agregar una malla estática a la escena:</span><span class="sxs-lookup"><span data-stu-id="04242-144">In CamCapture.cpp, update the constructor to add a static mesh to the scene:</span></span>

```cpp
ACamCapture::ACamCapture()
{
    PrimaryActorTick.bCanEverTick = true;

    // Load a mesh from the engine to render the camera feed to.
    StaticMesh = LoadObject<UStaticMesh>(nullptr, TEXT("/Engine/EngineMeshes/Cube.Cube"), nullptr, LOAD_None, nullptr);

    // Create a static mesh component to render the static mesh
    StaticMeshComponent = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CameraPlane"));
    StaticMeshComponent->SetStaticMesh(StaticMesh);

    // Scale and add to the scene
    StaticMeshComponent->SetWorldScale3D(FVector(0.1f, 1, 1));
    this->SetRootComponent(StaticMeshComponent);
}
```

<span data-ttu-id="04242-145">En BeginPlay, cree una instancia de material dinámico a partir del material de la cámara del proyecto, aplíquela al componente de la malla estática e inicie la cámara HoloLens.</span><span class="sxs-lookup"><span data-stu-id="04242-145">In BeginPlay create a dynamic material instance from the project’s camera material, apply it to the static mesh component, and start the HoloLens camera.</span></span> 
 
<span data-ttu-id="04242-146">En el editor, haga clic con el botón derecho en CamTextureMaterial en el explorador de contenido y seleccione "Copiar referencia" para obtener la cadena de CameraMatPath.</span><span class="sxs-lookup"><span data-stu-id="04242-146">In the editor, right-click on the CamTextureMaterial in the content browser and select “Copy Reference” to get the string for CameraMatPath.</span></span>

```cpp
void ACamCapture::BeginPlay()
{
    Super::BeginPlay();

    // Create a dynamic material instance from the game's camera material.
    // Right-click on a material in the project and select "Copy Reference" to get this string.
    FString CameraMatPath("Material'/Game/Materials/CamTextureMaterial.CamTextureMaterial'");
    UMaterial* BaseMaterial = (UMaterial*)StaticLoadObject(UMaterial::StaticClass(), nullptr, *CameraMatPath, nullptr, LOAD_None, nullptr);
    DynamicMaterial = UMaterialInstanceDynamic::Create(BaseMaterial, this);

    // Use the dynamic material instance when rendering the camera mesh.
    StaticMeshComponent->SetMaterial(0, DynamicMaterial);

    // Start the webcam.
    UARBlueprintLibrary::ToggleARCapture(true, EARCaptureType::Camera);
}
```

<span data-ttu-id="04242-147">En Tic, obtenga la textura de la cámara, establézcala en el parámetro Texture en el material de CamTextureMaterial y escale el componente de malla estática con la relación de aspecto del encuadre de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-147">In Tick get the texture from the camera, set it to the texture parameter in the CamTextureMaterial material, and scale the static mesh component by the camera frame’s aspect ratio:</span></span>

```cpp
void ACamCapture::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    // Dynamic material instance only needs to be set once.
    if(IsTextureParamSet)
    {
        return;
    }

    // Get the texture from the camera.
    UARTexture* ARTexture = UARBlueprintLibrary::GetARTexture(EARTextureType::CameraImage);
    if(ARTexture != nullptr)
    {
        // Set the shader's texture parameter (named "Param") to the camera image.
        DynamicMaterial->SetTextureParameterValue("Param", ARTexture);
        IsTextureParamSet = true;

        // Get the camera instrincs
        FARCameraIntrinsics Intrinsics;
        UARBlueprintLibrary::GetCameraIntrinsics(Intrinsics);

        // Scale the camera mesh by the aspect ratio.
        float R = (float)Intrinsics.ImageResolution.X / (float)Intrinsics.ImageResolution.Y;
        StaticMeshComponent->SetWorldScale3D(FVector(0.1f, R, 1));
    }
}
```

# <a name="425"></a>[<span data-ttu-id="04242-148">4.25</span><span class="sxs-lookup"><span data-stu-id="04242-148">4.25</span></span>](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="04242-149">Representación de la cámara PV para MRC</span><span class="sxs-lookup"><span data-stu-id="04242-149">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="04242-150">Se requiere **Unreal Engine 4.25** o versión posterior.</span><span class="sxs-lookup"><span data-stu-id="04242-150">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="04242-151">El sistema y las grabadoras de MRC personalizadas crean capturas de realidad mixta mediante la combinación de la cámara PV con hologramas representados por la aplicación.</span><span class="sxs-lookup"><span data-stu-id="04242-151">The system and custom MRC recorders create mixed reality captures by combining the PV Camera with holograms rendered by the app.</span></span>

<span data-ttu-id="04242-152">De forma predeterminada, la captura de realidad mixta usa la salida holográfica del ojo derecho.</span><span class="sxs-lookup"><span data-stu-id="04242-152">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="04242-153">Si una aplicación inmersiva elige la [representación de la cámara PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), se usará en su lugar.</span><span class="sxs-lookup"><span data-stu-id="04242-153">If an immersive app chooses to [render from the PV Camera](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), then that will be used instead.</span></span> <span data-ttu-id="04242-154">La representación de la cámara PV mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.</span><span class="sxs-lookup"><span data-stu-id="04242-154">Rendering from the PV Camera improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="04242-155">Para participar en la representación de la cámara PV:</span><span class="sxs-lookup"><span data-stu-id="04242-155">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="04242-156">Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="04242-156">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="04242-157">Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.</span><span class="sxs-lookup"><span data-stu-id="04242-157">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![Tercera cámara](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="04242-159">Unreal controlará las solicitudes de MRC para representarlas desde la perspectiva de la cámara PV.</span><span class="sxs-lookup"><span data-stu-id="04242-159">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="04242-160">Solo cuando se desencadena la [Captura de realidad mixta](/hololens/holographic-photos-and-videos), se pedirá a la aplicación que represente desde la perspectiva de la cámara de foto y vídeo.</span><span class="sxs-lookup"><span data-stu-id="04242-160">Only when [Mixed Reality Capture](/hololens/holographic-photos-and-videos) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="04242-161">Uso de la cámara PV</span><span class="sxs-lookup"><span data-stu-id="04242-161">Using the PV Camera</span></span>

<span data-ttu-id="04242-162">La textura de la cámara web se puede recuperar en el juego en tiempo de ejecución, pero debe habilitarse en la opción del editor **Editar > Configuración del proyecto**:</span><span class="sxs-lookup"><span data-stu-id="04242-162">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="04242-163">Vaya a **Plataformas > HoloLens > Capacidades** y marca **Cámara Web**.</span><span class="sxs-lookup"><span data-stu-id="04242-163">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="04242-164">Use la función **StartCameraCapture** para usar la cámara web en tiempo de ejecución y la función **StopCameraCapture** para detener la grabación.</span><span class="sxs-lookup"><span data-stu-id="04242-164">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![Inicio y detención de la cámara](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="04242-166">Representación de una imagen</span><span class="sxs-lookup"><span data-stu-id="04242-166">Rendering an image</span></span>
<span data-ttu-id="04242-167">Para representar la imagen de la cámara:</span><span class="sxs-lookup"><span data-stu-id="04242-167">To render the camera image:</span></span>
1. <span data-ttu-id="04242-168">Cree una instancia de material dinámico basada en un material del proyecto, que se denomine **PVCamMat** en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="04242-168">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="04242-169">Establezca la instancia de material dinámico en una variable de **referencia de objeto dinámico de instancia de material**.</span><span class="sxs-lookup"><span data-stu-id="04242-169">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="04242-170">Establezca el material del objeto en la escena que representará la fuente de la cámara para esta nueva instancia de material dinámico.</span><span class="sxs-lookup"><span data-stu-id="04242-170">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="04242-171">Inicie un temporizador que se usará para enlazar la imagen de la cámara al material.</span><span class="sxs-lookup"><span data-stu-id="04242-171">Start a timer that will be used to bind the camera image to the material.</span></span>

![Representación de la cámara](../images/unreal-camera-render.PNG)

4. <span data-ttu-id="04242-173">Cree una nueva función para este temporizador, en este caso **MaterialTimer**, y llame a **GetARCameraImage** para obtener la textura de la cámara web.</span><span class="sxs-lookup"><span data-stu-id="04242-173">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="04242-174">Si esta textura es válida, defina un parámetro de textura en el sombreador para esta imagen.</span><span class="sxs-lookup"><span data-stu-id="04242-174">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="04242-175">De lo contrario, vuelve a iniciar el temporizador de materiales.</span><span class="sxs-lookup"><span data-stu-id="04242-175">Otherwise, start the material timer again.</span></span>

![Textura de cámara desde la cámara web](../images/unreal-camera-texture.PNG)

5. <span data-ttu-id="04242-177">Asegúrese de que el material tiene un parámetro que coincide con el nombre de **SetTextureParameterValue** que está enlazado a una entrada de color.</span><span class="sxs-lookup"><span data-stu-id="04242-177">Make sure the material has a parameter that matches the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="04242-178">Sin el parámetro, la imagen de la cámara no puede mostrarse correctamente.</span><span class="sxs-lookup"><span data-stu-id="04242-178">Without the parameter, the camera image can't be displayed properly.</span></span>

![Textura de cámara](../images/unreal-camera-material.PNG)