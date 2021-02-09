---
title: Integración de Azure Custom Vision
description: Complete este curso para aprender a implementar Azure Custom Vision con una aplicación de realidad mixta de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, azure custom vision, azure cognitive services, azure cloud services, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: cb391aa2cdb7944234cdeede7dd05825c008d0d8
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590577"
---
# <a name="3-integrating-azure-custom-vision"></a>3. Integración de Azure Custom Vision

En este tutorial, aprenderá a usar **Azure Custom Vision**. Cargará un conjunto de fotos para asociarlo a un *objeto con seguimiento*, las cargará en el servicio **Custom Vision** y comenzará el proceso de entrenamiento. A continuación, usará el servicio para detectar el *objeto con seguimiento* al capturar las fotos de la fuente de la cámara web.

## <a name="objectives"></a>Objetivos

* Aprender los aspectos básicos de Azure Custom Vision
* Aprender a configurar la escena para usar Custom Vision en este proyecto.
* Aprender a integrar, cargar, entrenar y detectar imágenes

## <a name="understanding-azure-custom-vision"></a>Descripción de Azure Custom Vision

**Azure Custom Vision** forma parte de la familia **Cognitive Services** y se usa para entrenar clasificadores de imágenes. El clasificador de imágenes es un servicio de IA que usa el modelo entrenado para aplicar etiquetas coincidentes. Nuestra aplicación usará esta característica de clasificación para detectar *objetos con seguimiento*.

Más información sobre [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).

## <a name="preparing-azure-custom-vision"></a>Preparación de Azure Custom Vision

Antes de empezar, tiene que crear un proyecto de Custom Vision, la manera más rápida es usar el portal web.

Siga este [tutorial de inicio rápido](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) para configurar la cuenta y el proyecto hasta la sección *Carga y etiquetado de imágenes*.

> [!WARNING]
> Para entrenar un modelo, debe tener al menos 2 etiquetas y 5 imágenes por etiqueta. Para usar esta aplicación, debe crear al menos una etiqueta con 5 imágenes, de modo que el proceso de entrenamiento no genere errores más adelante.

## <a name="preparing-the-scene"></a>Preparación de la escena

En la ventana Proyecto, navega hasta la carpeta **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager**.

![Unity con la ventana Project (Proyecto) que muestra la ruta de acceso al objeto prefabricado ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

Desde ahí, arrastre el recurso prefabricado **ObjectDetectionManager** hasta la jerarquía de la escena.

![Unity con los campos de configuración del componente de script ObjectDetectionManager que aparecen en Inspector](images/mr-learning-azure/tutorial3-section4-step1-2.png)

En la ventana Hierarchy (Jerarquía), busque el objeto **ObjectDetectionManager** y selecciónelo.
El recurso prefabricado **ObjectDetectionManager** contiene el componente **ObjectDetectionManager (script)** y, como puede ver en la ventana Inspector, depende de varios valores de Azure y del proyecto.

## <a name="retrieving-azure-api-resource-credentials"></a>Recuperación de credenciales de recursos de API de Azure

Las credenciales necesarias para la configuración de **ObjectDetectionManager (script)** se pueden recuperar de Azure Portal y del portal de Custom Vision.

### <a name="retrieving-azure-settings-credentials"></a>Recuperación de las credenciales de configuración de Azure

Busque el recurso de Custom Vision de tipo **Cognitive Services** que ha creado en la sección *Preparación de la escena* de este tutorial y búsquelo (seleccione el nombre de los recursos de Custom Vision seguido de *-Prediction*). Haga clic en *Información general* o *Claves y punto de conexión* para recuperar las credenciales necesarias.

### <a name="retrieving-project-settings-credentials"></a>Recuperación de las credenciales de configuración de proyecto

En el panel de [Custom Vision](https://www.customvision.ai/projects), abra el proyecto que ha creado para este tutorial y haga clic en la esquina superior derecha de la página en el icono de engranaje para abrir la página de configuración. Aquí, en la sección *Resources* (Recursos) de la derecha encontrará las credenciales necesarias.

Ahora con **ObjectDetectionManager (script)** configurado correctamente, busque el objeto de **SceneController** en la jerarquía de escenas y selecciónelo.

![Unity con los campos de configuración del componente de script SceneController que aparecen en el Inspector](images/mr-learning-azure/tutorial3-section4-step1-3.png)

Se ve que el campo *Object Detection Manager* (Administrador de detección de objetos) en el componente **SceneController** está vacío, arrastre **ObjectDetectionManager** desde la jerarquía hasta ese campo y guarde la escena.

![Unity con el componente de script SceneController configurado](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>Toma y carga de imágenes

Ejecute la escena y haga clic en **Set Object** (Establecer objeto), escriba el nombre de uno de los **objetos con seguimiento** que ha creado en la [lección anterior](mr-learning-azure-02.md). Ahora, haga clic en el botón **Computer Vision** (Visión de equipo) que se encuentra en la parte inferior de la **Object Card** (Tarjeta de objeto).

Se abrirá una nueva ventana en la que tendrá que tomar seis fotos para entrenar el modelo para el reconocimiento de imágenes. Haga clic en el botón **Camera** (Cámara) y realice una pulsación en el aire al mirar el objeto del que desea realizar un seguimiento, haga esto seis veces.

> [!TIP]
> Para mejorar el entrenamiento del modelo, intente tomar cada imagen desde distintos ángulos y con distintas condiciones de iluminación.

Una vez que tenga suficientes imágenes, haga clic en el botón **Train** (Entrenar) para iniciar el proceso de entrenamiento del modelo en la nube. Al activar el entrenamiento se cargarán todas las imágenes y, luego, comenzará el entrenamiento, lo que puede tardar un minuto o más. Un mensaje dentro del menú indica el progreso actual y, una vez que indica la finalización, puede detener la aplicación.

> [!TIP]
> **ObjectDetectionManager (script)** carga directamente las imágenes tomadas en el servicio Custom Vision. Como alternativa, Custom Vision API acepta las direcciones URL de las imágenes; como ejercicio, puede modificar **ObjectDetectionManager (script)** para que cargue las imágenes en un almacenamiento de blobs en su lugar.

## <a name="detect-objects"></a>Detección de objetos

Para poder detectar los objetos, es necesario cambiar la clave de API que existe en **ObjectDetectionManager (script)** de la configuración del proyecto que ya se ha asignado por la de Custom Vision.

Busque el recurso de Custom Vision en Azure Portal. Haga clic en *Claves y punto de conexión* para recuperar la clave de API y reemplácela por la clave de API anterior de la configuración del proyecto.

Ahora puede poner a prueba el modelo entrenado; ejecute la aplicación y, en el *menú principal* haga clic en **Search Object** (Buscar objeto) y escriba el nombre del **objeto con seguimiento** en cuestión. Aparecerá **Object Card** (Tarjeta de objeto) y haga clic en el botón **Custom Vision**. Desde aquí, **ObjectDetectionManager** comenzará a tomar capturas de imagen en segundo plano desde la cámara, y el progreso se indicará en el menú. Apunte la cámara al objeto que usó para entrenar el modelo y verá que, después de un breve lapso, detectará el objeto.

## <a name="congratulations"></a>Enhorabuena

En este tutorial ha aprendido cómo se puede usar Azure Custom Vision para entrenar imágenes y usar el servicio de clasificación para detectar imágenes que coincidan con el **objeto con seguimiento** asociado.

En el siguiente tutorial aprenderá a usar Azure Spatial Anchors para vincular un *objeto con seguimiento* a una ubicación en el mundo físico y a mostrar una flecha que le devolverá al usuario a la ubicación vinculada del objeto con seguimiento.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 4. Integración de Azure Spatial Anchors](mr-learning-azure-04.md)