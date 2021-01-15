---
title: Cámara localizable en Unity
description: Obtenga información acerca de cómo capturar una foto en un archivo o en un Texture2D, cómo capturar una foto e interactuar con los bytes sin formato y cómo capturar un vídeo.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Foto, vídeo, hololens, cámara, Unity, localizable, PVC, cámara de vídeo fotográfico, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual, cámara web, captura de fotos, captura de vídeo
ms.openlocfilehash: 8916b332774185e4453b514ca7b6916947bdcd81
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226424"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="138c9-104">Cámara localizable en Unity</span><span class="sxs-lookup"><span data-stu-id="138c9-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="138c9-105">Habilitación de la funcionalidad de la cámara de vídeo fotográfico</span><span class="sxs-lookup"><span data-stu-id="138c9-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="138c9-106">La funcionalidad "WebCam" se debe declarar para que una aplicación use la [cámara](../platform-capabilities-and-apis/locatable-camera.md).</span><span class="sxs-lookup"><span data-stu-id="138c9-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="138c9-107">En el editor de Unity, vaya a la página "editar > configuración del proyecto > reproductor" para ir a la configuración del reproductor.</span><span class="sxs-lookup"><span data-stu-id="138c9-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="138c9-108">Seleccione la pestaña "tienda Windows"</span><span class="sxs-lookup"><span data-stu-id="138c9-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="138c9-109">En la sección "configuración de publicación > funcionalidades", compruebe las funcionalidades de la **cámara web** y el **micrófono**</span><span class="sxs-lookup"><span data-stu-id="138c9-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="138c9-110">Solo se puede realizar una operación con la cámara a la vez.</span><span class="sxs-lookup"><span data-stu-id="138c9-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="138c9-111">Puede comprobar con el modo en que la cámara está actualmente en con UnityEngine. XR. WSA. WebCam. Mode.</span><span class="sxs-lookup"><span data-stu-id="138c9-111">You can check with mode the camera is currently in with UnityEngine.XR.WSA.WebCam.Mode.</span></span> <span data-ttu-id="138c9-112">Los modos disponibles son fotográfico, vídeo o ninguno.</span><span class="sxs-lookup"><span data-stu-id="138c9-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="138c9-113">Captura de foto</span><span class="sxs-lookup"><span data-stu-id="138c9-113">Photo Capture</span></span>

<span data-ttu-id="138c9-114">**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="138c9-114">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="138c9-115">**Tipo:** *fotocapture*</span><span class="sxs-lookup"><span data-stu-id="138c9-115">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="138c9-116">El tipo de *fotocaptura* le permite tomar fotografías con la cámara de vídeo fotográfico.</span><span class="sxs-lookup"><span data-stu-id="138c9-116">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="138c9-117">El patrón general para usar *fotocapture* para tomar una foto es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="138c9-117">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="138c9-118">Creación de un objeto *Fotocapture*</span><span class="sxs-lookup"><span data-stu-id="138c9-118">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="138c9-119">Cree un objeto *CameraParameters* con los valores que desee.</span><span class="sxs-lookup"><span data-stu-id="138c9-119">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="138c9-120">Iniciar el modo fotográfico a través de *StartPhotoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="138c9-120">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="138c9-121">Tome la foto que desee</span><span class="sxs-lookup"><span data-stu-id="138c9-121">Take the photo you want</span></span>
    * <span data-ttu-id="138c9-122">opta Interactuar con esa imagen</span><span class="sxs-lookup"><span data-stu-id="138c9-122">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="138c9-123">Detener el modo fotográfico y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="138c9-123">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="138c9-124">Configuración común para fotocaptura</span><span class="sxs-lookup"><span data-stu-id="138c9-124">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="138c9-125">Para los tres usos, empiece con los tres primeros pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="138c9-125">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="138c9-126">Inicio mediante la creación de un objeto *Fotocapture*</span><span class="sxs-lookup"><span data-stu-id="138c9-126">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="138c9-127">A continuación, almacene el objeto, establezca los parámetros e inicie el modo fotográfico.</span><span class="sxs-lookup"><span data-stu-id="138c9-127">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="138c9-128">Al final, también usará el mismo código de limpieza que se muestra aquí.</span><span class="sxs-lookup"><span data-stu-id="138c9-128">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="138c9-129">Después de estos pasos, puede elegir el tipo de foto que desea capturar.</span><span class="sxs-lookup"><span data-stu-id="138c9-129">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="138c9-130">Capturar una foto en un archivo</span><span class="sxs-lookup"><span data-stu-id="138c9-130">Capture a Photo to a File</span></span>

<span data-ttu-id="138c9-131">La operación más sencilla consiste en capturar una foto directamente en un archivo.</span><span class="sxs-lookup"><span data-stu-id="138c9-131">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="138c9-132">La foto se puede guardar como JPG o PNG.</span><span class="sxs-lookup"><span data-stu-id="138c9-132">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="138c9-133">Si ha iniciado correctamente el modo fotográfico, tome una foto y almacénela en el disco</span><span class="sxs-lookup"><span data-stu-id="138c9-133">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="138c9-134">Después de capturar la foto en el disco, salga del modo fotográfico y limpie los objetos</span><span class="sxs-lookup"><span data-stu-id="138c9-134">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="138c9-135">Capturar una foto en un Texture2D</span><span class="sxs-lookup"><span data-stu-id="138c9-135">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="138c9-136">Al capturar datos en un Texture2D, el proceso es similar a la captura en disco.</span><span class="sxs-lookup"><span data-stu-id="138c9-136">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="138c9-137">Siga el proceso de instalación anterior.</span><span class="sxs-lookup"><span data-stu-id="138c9-137">Follow the setup process above.</span></span>

<span data-ttu-id="138c9-138">En *OnPhotoModeStarted*, Capture un fotograma en la memoria.</span><span class="sxs-lookup"><span data-stu-id="138c9-138">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="138c9-139">A continuación, aplicará el resultado a una textura y usará el código de limpieza común anterior.</span><span class="sxs-lookup"><span data-stu-id="138c9-139">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="138c9-140">Capturar una foto e interactuar con los bytes sin formato</span><span class="sxs-lookup"><span data-stu-id="138c9-140">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="138c9-141">Para interactuar con los bytes sin formato de un marco de memoria, siga los mismos pasos de configuración descritos anteriormente y *OnPhotoModeStarted* como en la captura de una foto en un Texture2D.</span><span class="sxs-lookup"><span data-stu-id="138c9-141">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="138c9-142">La diferencia está en *OnCapturedPhotoToMemory* , donde puede obtener los bytes sin formato e interactuar con ellos.</span><span class="sxs-lookup"><span data-stu-id="138c9-142">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="138c9-143">En este ejemplo, creará una *lista <Color>* que se procesará o se aplicará a una textura a través de *SetPixels ()* .</span><span class="sxs-lookup"><span data-stu-id="138c9-143">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="138c9-144">Captura de vídeo</span><span class="sxs-lookup"><span data-stu-id="138c9-144">Video Capture</span></span>

<span data-ttu-id="138c9-145">**Espacio de nombres:** *UnityEngine. XR. WSA. webcam*</span><span class="sxs-lookup"><span data-stu-id="138c9-145">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="138c9-146">**Tipo:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="138c9-146">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="138c9-147">*VideoCapture* funciona de forma similar a *fotocapture*.</span><span class="sxs-lookup"><span data-stu-id="138c9-147">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="138c9-148">Las únicas dos diferencias son que debe especificar un valor de fotogramas por segundo (FPS) y solo puede guardar directamente en el disco como un archivo. MP4.</span><span class="sxs-lookup"><span data-stu-id="138c9-148">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="138c9-149">Los pasos para usar *VideoCapture* son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="138c9-149">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="138c9-150">Creación de un objeto de *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="138c9-150">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="138c9-151">Cree un objeto *CameraParameters* con los valores que desee.</span><span class="sxs-lookup"><span data-stu-id="138c9-151">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="138c9-152">Iniciar el modo de vídeo a través de *StartVideoModeAsync*</span><span class="sxs-lookup"><span data-stu-id="138c9-152">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="138c9-153">Iniciar grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="138c9-153">Start recording video</span></span>
5. <span data-ttu-id="138c9-154">Detener grabación de vídeo</span><span class="sxs-lookup"><span data-stu-id="138c9-154">Stop recording video</span></span>
6. <span data-ttu-id="138c9-155">Detener el modo de vídeo y limpiar los recursos</span><span class="sxs-lookup"><span data-stu-id="138c9-155">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="138c9-156">Empiece por crear el objeto *VideoCapture* de *videocaptura m_VideoCapture = null;*</span><span class="sxs-lookup"><span data-stu-id="138c9-156">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="138c9-157">A continuación, configure los parámetros que desea para la grabación y el inicio.</span><span class="sxs-lookup"><span data-stu-id="138c9-157">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="138c9-158">Una vez iniciado, comience la grabación.</span><span class="sxs-lookup"><span data-stu-id="138c9-158">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="138c9-159">Una vez iniciada la grabación, puede actualizar la interfaz de usuario o los comportamientos para habilitar la detención.</span><span class="sxs-lookup"><span data-stu-id="138c9-159">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="138c9-160">Aquí solo tiene que registrar.</span><span class="sxs-lookup"><span data-stu-id="138c9-160">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="138c9-161">En un momento posterior, querrá detener la grabación mediante un temporizador o una entrada del usuario, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="138c9-161">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="138c9-162">Una vez que la grabación se ha detenido, detenga el modo de vídeo y limpie los recursos.</span><span class="sxs-lookup"><span data-stu-id="138c9-162">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="138c9-163">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="138c9-163">Troubleshooting</span></span>
* <span data-ttu-id="138c9-164">No hay ninguna solución disponible</span><span class="sxs-lookup"><span data-stu-id="138c9-164">No resolutions are available</span></span>
    * <span data-ttu-id="138c9-165">Asegúrese de que la funcionalidad de la **cámara web** está especificada en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="138c9-165">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="138c9-166">Siguiente punto de control de desarrollo</span><span class="sxs-lookup"><span data-stu-id="138c9-166">Next Development Checkpoint</span></span>

<span data-ttu-id="138c9-167">Si está siguiendo el viaje de punto de control de desarrollo de Unity que hemos diseñado, está en medio de explorar las API y funcionalidades de la plataforma de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="138c9-167">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="138c9-168">Desde aquí, puede continuar con el siguiente tema:</span><span class="sxs-lookup"><span data-stu-id="138c9-168">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="138c9-169">Punto de enfoque</span><span class="sxs-lookup"><span data-stu-id="138c9-169">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="138c9-170">O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:</span><span class="sxs-lookup"><span data-stu-id="138c9-170">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="138c9-171">Implementación en HoloLens o con auriculares de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="138c9-171">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="138c9-172">Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="138c9-172">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="138c9-173">Consulte también</span><span class="sxs-lookup"><span data-stu-id="138c9-173">See Also</span></span>
* [<span data-ttu-id="138c9-174">Cámara localizable</span><span class="sxs-lookup"><span data-stu-id="138c9-174">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
