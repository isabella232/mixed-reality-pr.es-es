---
title: Cámara de fotos y vídeo en Unity
description: Obtenga información sobre cómo capturar una foto en un archivo o en un objeto Texture2D, cómo capturar una foto e interactuar con los bytes sin procesar y cómo capturar un vídeo.
author: keveleigh
ms.author: v-hferrone
ms.date: 03/21/2021
ms.topic: article
keywords: photo, video, hololens, camera, unity, locatable, PVC, photo video camera, mixed reality headset, windows mixed reality headset, virtual reality headset, camera, photo capture, video capture
ms.openlocfilehash: 4fdf895e6b2b7ed1fc051b45b07ce49052f8a95587178caddfc71a0cfd364eee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193509"
---
# <a name="photo-video-camera-in-unity"></a>Cámara de fotos y vídeo en Unity

## <a name="enabling-the-capability-for-camera-access"></a>Habilitación de la funcionalidad para el acceso a la cámara

La funcionalidad "WebCam" debe declararse para que una aplicación use la [cámara](../platform-capabilities-and-apis/locatable-camera.md).

1. En el Editor de Unity, vaya a la configuración del reproductor; para ello, vaya a la página "Editar > Project Configuración > reproductor".
2. Seleccione la pestaña "Windows Store" (Tienda de aplicaciones).
3. En la sección "Publishing Configuración > Capabilities" (Funcionalidades de Configuración > web), compruebe las funcionalidades **WebCam** **y Microphone.**

Solo se puede producir una sola operación con la cámara a la vez. Puede comprobar en qué modo se encuentra actualmente la cámara en Unity 2018 y versiones anteriores o `UnityEngine.XR.WSA.WebCam.Mode` `UnityEngine.Windows.WebCam.Mode` en Unity 2019 y versiones posteriores. Los modos disponibles son foto, vídeo o ninguno.

## <a name="photo-capture"></a>Captura de fotos

**Espacio de nombres (antes de Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Espacio de nombres (Unity 2019 y versiones posteriores):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *PhotoCapture*

El *tipo PhotoCapture* le permite tomar fotografías con photo video camera. El patrón general para usar *PhotoCapture para* tomar una foto es el siguiente:

1. Creación de un *objeto PhotoCapture*
2. Cree un *objeto CameraParameters* con la configuración que desee.
3. Modo Start Photo mediante *StartPhotoModeAsync*
4. Tomar la foto que quiera
    * (opcional) Interactuar con esa imagen
5. Detener el modo foto y limpiar los recursos

### <a name="common-set-up-for-photocapture"></a>Configuración común de PhotoCapture

Para los tres usos, comience con los mismos tres primeros pasos anteriores.

Para empezar, cree un *objeto PhotoCapture.*

```cs
private void Start()
{
    PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
}
```

A continuación, almacene el objeto, establezca los parámetros e inicie el modo foto.

```cs
private PhotoCapture photoCaptureObject = null;

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

Al final, también usará el mismo código de limpieza que se presenta aquí.

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
{
    photoCaptureObject.Dispose();
    photoCaptureObject = null;
}
```

Después de estos pasos, puede elegir el tipo de foto que se va a capturar.

### <a name="capture-a-photo-to-a-file"></a>Capturar una foto a un archivo

La operación más sencilla es capturar una foto directamente en un archivo. La foto se puede guardar como JPG o PNG.

Si ha iniciado correctamente el modo de foto, tome una foto y almacéne en el disco.

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

Después de capturar la foto en el disco, salga del modo de foto y, a continuación, limpie los objetos.

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

### <a name="capture-a-photo-to-a-texture2d-with-location"></a>Captura de una foto en un objeto Texture2D con ubicación

Al capturar datos en texture2D, el proceso es similar a la captura en el disco.

Siga el proceso de instalación anterior.

En *OnPhotoModeStarted,* capture un fotograma en la memoria.

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

A continuación, aplicará el resultado a una textura y usará el código de limpieza común anterior.

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

#### <a name="locatable-camera"></a>Cámara localizable

Para colocar esta textura en la escena y mostrarla mediante las matrices de cámara localizables, agregue el código siguiente a *OnCapturedPhotoToMemory* en la `result.success` comprobación:

```cs
if (photoCaptureFrame.hasLocationData)
{
    photoCaptureFrame.TryGetCameraToWorldMatrix(out Matrix4x4 cameraToWorldMatrix);

    Vector3 position = cameraToWorldMatrix.GetColumn(3) - cameraToWorldMatrix.GetColumn(2);
    Quaternion rotation = Quaternion.LookRotation(-cameraToWorldMatrix.GetColumn(2), cameraToWorldMatrix.GetColumn(1));

    photoCaptureFrame.TryGetProjectionMatrix(Camera.main.nearClipPlane, Camera.main.farClipPlane, out Matrix4x4 projectionMatrix);
}
```

[Unity ha proporcionado código de ejemplo](https://forum.unity.com/threads/holographic-photo-blending-with-photocapture.416023/?_ga=2.57872105.210548785.1614215615-862490274.1597860099) para aplicar la matriz de proyección a un sombreador específico en sus foros.

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>Captura de una foto e interacción con los bytes sin procesar

Para interactuar con los bytes sin procesar de un marco en memoria, siga los mismos pasos de configuración anteriores y *OnPhotoModeStarted* como al capturar una foto en texture2D. La diferencia está en *OnCapturedPhotoToMemory,* donde puede obtener los bytes sin procesar e interactuar con ellos.

En este ejemplo, creará una lista para procesarla o aplicarla *a <Color>* una textura a través de *SetPixels()*

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

## <a name="video-capture"></a>Captura de vídeo

**Espacio de nombres (antes de Unity 2019):** *UnityEngine.XR.WSA.WebCam*<br>
**Espacio de nombres (Unity 2019 y versiones posteriores):** *UnityEngine.Windows. WebCam*<br>
**Tipo:** *VideoCapture*

*VideoCapture funciona* de forma similar a *PhotoCapture.* Las dos únicas diferencias son que debe especificar un valor fotogramas por segundo (FPS) y solo puede guardar directamente en el disco como un archivo .mp4 segundo. Los pasos para usar *VideoCapture* son los siguientes:

1. Creación de un *objeto VideoCapture*
2. Cree un *objeto CameraParameters* con la configuración que desee.
3. Iniciar el modo de vídeo *a través de StartVideoModeAsync*
4. Inicio de la grabación de vídeo
5. Detener la grabación de vídeo
6. Detener el modo de vídeo y limpiar los recursos

Empiece por crear el *objeto VideoCapture* *VideoCapture m_VideoCapture = null;*

```cs
void Start ()
{
    VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
}
```

A continuación, configure los parámetros que desee para la grabación y el inicio.

```cs
void OnVideoCaptureCreated(VideoCapture videoCapture)
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

Una vez iniciado, comience la grabación.

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

Una vez iniciada la grabación, puede actualizar la interfaz de usuario o los comportamientos para habilitar la detención. Aquí solo tiene que registrar.

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
{
    Debug.Log("Started Recording Video!");
    // We will stop the video from recording via other input such as a timer or a tap, etc.
}
```

En un momento posterior, querrá detener la grabación mediante un temporizador o una entrada de usuario, por ejemplo.

```cs
// The user has indicated to stop recording
void StopRecordingVideo()
{
    m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
}
```

Una vez detenida la grabación, detenga el modo de vídeo y limpie los recursos.

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

## <a name="troubleshooting"></a>Solución de problemas

* No hay soluciones disponibles
  * Asegúrese de **que la funcionalidad WebCam** está especificada en el proyecto.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido del punto de control de desarrollo de Unity que hemos diseñado, está a punto de explorar las API y las funcionalidades de Mixed Reality plataforma. Desde aquí, puede continuar con el siguiente tema:

> [!div class="nextstepaction"]
> [Punto de enfoque](focus-point-in-unity.md)

O bien puede ir directamente a la implementación de la aplicación en un dispositivo o emulador:

> [!div class="nextstepaction"]
> [Implementación en HoloLens o Windows Mixed Reality cascos envolventes](../platform-capabilities-and-apis/using-visual-studio.md)

Puede volver a los [puntos de control de desarrollo de Unity](unity-development-overview.md#3-advanced-features) en cualquier momento.

## <a name="see-also"></a>Consulte también

* [Cámara localizable](../platform-capabilities-and-apis/locatable-camera.md)