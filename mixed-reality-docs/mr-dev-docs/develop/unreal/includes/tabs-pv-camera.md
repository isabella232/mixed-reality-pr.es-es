---
ms.openlocfilehash: e79b14c19a452b5b78c6f8cf7ea24bd65bfa0eaa
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98605190"
---
# <a name="426"></a>[4.26](#tab/426) 

## <a name="pv-camera-feed-setup"></a>Configuración de la fuente de la cámara de fotos y vídeo

> [!IMPORTANT]
> La cámara de fotos y vídeo se implementa en los complementos de Windows Mixed Reality y OpenXR. Sin embargo, OpenXR requiere que el [complemento OpenXR de Microsoft](https://github.com/microsoft/Microsoft-OpenXR-Unreal) esté instalado. Además, OpenXR tiene una limitación actualmente; la cámara puede funcionar con DirectX11 RHI. Esta limitación se solucionará en una versión de Unreal posterior. 

- En **Configuración del proyecto > HoloLens**, habilite la funcionalidad **Cámara web**:

![Captura de pantalla de la configuración del proyecto de HoloLens con la propiedad Cámara web resaltada](../images/unreal-pvc-img-01.png)

- Cree un nuevo actor llamado "CamCapture" y agregue un plano para representar la fuente de la cámara:

![Captura de pantalla de un actor con un plano agregado](../images/unreal-pvc-img-02.png)

- Agregue el actor a la escena, cree un nuevo material denominado CamTextureMaterial con un parámetro de objeto de textura y un ejemplo de textura.  Envíe los datos RGB de la textura al color emisor de salida:

![Plano de un ejemplo de material y textura](../images/unreal-pvc-img-03.png)

## <a name="rendering-the-pv-camera-feed"></a>Representación de la fuente de la cámara de fotos y vídeo

- En el plano técnico CamCapture, active la cámara de fotos y vídeo:

![Plano técnico de la función Toggle ARCapture con la cámara de fotos y vídeo activada](../images/unreal-pvc-img-04.png)

- Cree una instancia de material dinámico a partir de CamTextureMaterial y asigne este material al plano del actor:

![Plano técnico de la función Create Dynamic Material Instance](../images/unreal-pvc-img-05.png)

- Obtenga la textura de la fuente de la cámara y asígnela al material dinámico si es válida.  Si la textura no es válida, inicie un temporizador y vuelva a intentarlo después del tiempo de espera:

![Plano técnico de la textura de la fuente de la cámara asignada al material dinámico](../images/unreal-pvc-img-06.png)

- Por último, escale el plano mediante la relación de aspecto de la imagen de la cámara:

![Plano técnico del plano escalado asociado a la relación de aspecto de las imágenes de la cámara](../images/unreal-pvc-img-07.png)

## <a name="find-camera-positions-in-world-space"></a>Búsqueda de posiciones de la cámara en el espacio global

La cámara de HoloLens 2 se desplaza verticalmente desde el seguimiento del cabezal del dispositivo.  Existen algunas funciones que permiten ubicar la cámara en el espacio global para tenerlo en cuenta para el desplazamiento.

GetPVCameraToWorldTransform obtiene la transformación en el espacio global de la cámara PV y se coloca en la lente de la cámara:

![Plano técnico de la función Get PVCamera to World Transform](../images/unreal-pvc-img-08.png)

GetWorldSpaceRayFromCameraPoint envía un rayo desde la lente de la cámara en la escena del espacio global de Unreal a fin de buscar el contenido de un píxel del encuadre de la cámara:

![Plano técnico de la obtención del rayo del espacio global desde el punto de mira de la cámara](../images/unreal-pvc-img-09.png)

GetPVCameraIntrinsics devuelve los valores intrínsecos de la cámara, que se pueden usar al realizar el procesamiento de Computer Vision en un encuadre de la cámara:

![Plano técnico de la obtención de las funciones intrínsecas de la cámara de fotos y vídeo](../images/unreal-pvc-img-10.png)

Para buscar lo que hay en el espacio global de una coordenada de píxeles determinada, use un seguimiento de líneas con el rayo del espacio global:

![Plano técnico del rayo de espacio global que se usa para averiguar qué hay en el espacio global de una coordenada determinada](../images/unreal-pvc-img-11.png)

Aquí enviamos un rayo de 2 metros desde la lente de la cámara a la posición de un cuarto del espacio de la cámara de la parte superior izquierda del encuadre.  A continuación, use el resultado de posicionamiento para representar un sitio en que el objeto exista en el espacio global:

![Plano técnico de un envío de un rayo de 2 metros de la lente de la cámara a la posición de un cuarto del espacio de la cámara desde la parte superior izquierda del encuadre.](../images/unreal-pvc-img-12.png)

Cuando se use la asignación espacial, este posicionamiento coincidirá con la superficie que enfoca la cámara.

## <a name="rendering-the-pv-camera-feed-in-c"></a>Representación de la fuente de la cámara de fotos y vídeo en C++

- Cree un nuevo actor de C++ llamado CamCapture.
- En el archivo build.cs del proyecto, agregue "AugmentedReality" en la lista de PublicDependencyModuleNames:

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

- En CamCapture.h, incluya ARBlueprintLibrary.h.

```cpp
#include "ARBlueprintLibrary.h"
```

- También debe agregar variables locales para la malla y el material:

```cpp
private:
    UStaticMesh* StaticMesh;
    UStaticMeshComponent* StaticMeshComponent;
    UMaterialInstanceDynamic* DynamicMaterial;
    bool IsTextureParamSet = false;
```

- En CamCapture.cpp, actualice el constructor para agregar una malla estática a la escena:

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

En BeginPlay, cree una instancia de material dinámico a partir del material de la cámara del proyecto, aplíquela al componente de la malla estática e inicie la cámara HoloLens. 
 
En el editor, haga clic con el botón derecho en CamTextureMaterial en el explorador de contenido y seleccione "Copiar referencia" para obtener la cadena de CameraMatPath.

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

En Tic, obtenga la textura de la cámara, establézcala en el parámetro Texture en el material de CamTextureMaterial y escale el componente de malla estática con la relación de aspecto del encuadre de la cámara:

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

# <a name="425"></a>[4.25](#tab/425)

## <a name="render-from-the-pv-camera-for-mrc"></a>Representación de la cámara PV para MRC

> [!NOTE]
> Se requiere **Unreal Engine 4.25** o versión posterior.

El sistema y las grabadoras de MRC personalizadas crean capturas de realidad mixta mediante la combinación de la cámara PV con hologramas representados por la aplicación.

De forma predeterminada, la captura de realidad mixta usa la salida holográfica del ojo derecho. Si una aplicación inmersiva elige la [representación de la cámara PV](../../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in), se usará en su lugar. La representación de la cámara PV mejora el mapeo entre el mundo real y los hologramas en el vídeo de MRC.

Para participar en la representación de la cámara PV:

1. Llame a **SetEnabledMixedRealityCamera** y **ResizeMixedRealityCamera**
    * Use los valores **Tamaño X** y **Tamaño Y** para establecer las dimensiones del vídeo.

![Tercera cámara](../../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

Unreal controlará las solicitudes de MRC para representarlas desde la perspectiva de la cámara PV.

> [!NOTE]
> Solo cuando se desencadena la [Captura de realidad mixta](/hololens/holographic-photos-and-videos), se pedirá a la aplicación que represente desde la perspectiva de la cámara de foto y vídeo.

## <a name="using-the-pv-camera"></a>Uso de la cámara PV

La textura de la cámara web se puede recuperar en el juego en tiempo de ejecución, pero debe habilitarse en la opción del editor **Editar > Configuración del proyecto**:
1. Vaya a **Plataformas > HoloLens > Capacidades** y marca **Cámara Web**.
    * Use la función **StartCameraCapture** para usar la cámara web en tiempo de ejecución y la función **StopCameraCapture** para detener la grabación.

![Inicio y detención de la cámara](../images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a>Representación de una imagen
Para representar la imagen de la cámara:
1. Cree una instancia de material dinámico basada en un material del proyecto, que se denomine **PVCamMat** en la siguiente captura de pantalla.  
2. Establezca la instancia de material dinámico en una variable de **referencia de objeto dinámico de instancia de material**.  
3. Establezca el material del objeto en la escena que representará la fuente de la cámara para esta nueva instancia de material dinámico.
    * Inicie un temporizador que se usará para enlazar la imagen de la cámara al material.

![Representación de la cámara](../images/unreal-camera-render.PNG)

4. Cree una nueva función para este temporizador, en este caso **MaterialTimer**, y llame a **GetARCameraImage** para obtener la textura de la cámara web.  
5. Si esta textura es válida, defina un parámetro de textura en el sombreador para esta imagen.  De lo contrario, vuelve a iniciar el temporizador de materiales.

![Textura de cámara desde la cámara web](../images/unreal-camera-texture.PNG)

5. Asegúrese de que el material tiene un parámetro que coincide con el nombre de **SetTextureParameterValue** que está enlazado a una entrada de color. Sin el parámetro, la imagen de la cámara no puede mostrarse correctamente.

![Textura de cámara](../images/unreal-camera-material.PNG)