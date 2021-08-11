---
title: Integración de Azure Spatial Anchors
description: Siga este curso para aprender a implementar Azure Spatial Anchors dentro de una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, hololens 2, Azure spatial anchors, azure cloud services, azure custom vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7f85efae0ee24e4785d862873b8b1723460791d2d6a00406a3fd81f465c6faa7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115218571"
---
# <a name="4-integrating-azure-spatial-anchors"></a>4. Integración de Azure Spatial Anchors

En este tutorial, aprenderá a usar **Azure Spatial Anchors**. Almacenará la ubicación de un **objeto del que realiza un seguimiento** como un anclaje espacial de Azure. Una vez que haya consultado el anclaje, aparecerá una flecha que le guiará hacia la ubicación.

## <a name="objectives"></a>Objetivos

* Conocer los aspectos básicos de Azure Spatial Anchors.
* Aprender a configurar la escena para usar Azure Spatial Anchors en este proyecto.
* Aprender a integrar el almacenamiento y la consulta de ubicaciones.

## <a name="understanding-azure-spatial-anchors"></a>Descripción de Azure Spatial Anchors

 **Azure Spatial Anchors** forma parte de la familia de servicios en la nube de Azure y se usa para guardar las ubicaciones de anclaje. Las ubicaciones de anclaje guardadas se pueden recuperar en función del *identificador de anclaje* de la nube. Para compartir y acceder a dicha ubicación de anclaje, se pueden usar dispositivos multiplataforma, como HoloLens, iOS y Android.

Obtenga más información sobre [Azure Spatial Anchors](/azure/spatial-anchors/overview).

## <a name="preparing-azure-spatial-anchors"></a>Preparación de Azure Spatial Anchors

Antes de empezar, tiene que crear un recurso de anclaje espacial en Azure Portal.
Obtenga información sobre cómo crear un [recurso de anclaje espacial](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).

## <a name="preparing-the-scene"></a>Preparación de la escena

En esta sección, aprenderá a configurar la escena y realizar los cambios necesarios.

Seleccione el objeto **MixedRealityToolkit** en la ventana Hierarchy (Jerarquía) y use el botón **Add Component** (Agregar componente) en la ventana Inspector para agregar **AR Anchor Manager (Script)** .

![Objeto MixedRealityToolkit de Unity con los componentes AR Anchor Manager agregados ](images/mr-learning-azure/tutorial4-section1-step1-1.png)

> [!NOTE]
> Cuando se agregue el componente AR Anchor Manager (Script) (Administrador de anclaje de AR [script]), se agregará automáticamente el componente AR Session Origin (Script) (Origen de la sesión de AR [script]) según lo requiere el componente AR Anchor Manager (Script).

En la ventana Proyecto, navegue a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager** (Recursos > MRTK.Tutorials.AzureCloudServices > Objetos prefabricados > Administrador).

![Unity con el objeto prefabricado AnchorManager seleccionado](images/mr-learning-azure/tutorial4-section1-step1-2.png)

En la carpeta **Manager** (Administrador), arrastre y coloque el objeto prefabricado **Anchor Manager** (Administrador de anclajes) en la jerarquía de la escena.

Seleccione el objeto Game (Juego) de **Anchor Manager** (Administrador de anclajes) en la jerarquía y, en la sección Inspector, encontrará la opción **Spatial Anchor Manager** (Script) (Administrador de anclajes espacial [script]). Busque el campo del identificador de la cuenta y la clave y agregue las credenciales que creó en el requisito previo de la fase anterior.

![Unity con el objeto prefabricado AnchorManager recién agregado aún seleccionado](images/mr-learning-azure/tutorial4-section1-step2-1.png)

Ahora, busque el objeto **Scene Controller** (Controlador de escenas) en la jerarquía de escenas y selecciónelo. Verá **Scene Controller** (Controlador de escenas) en la sección de Inspector.

![Unity con el componente de script SceneController configurado](images/mr-learning-azure/tutorial4-section1-step3-1.png)

Observará que el campo **Anchor Manager** (Administrador de anclajes) del componente **Scene Controller** (Controlador de escenas) está vacío. Arrastre y coloque el elemento **Anchor Manager** (Administrador de anclajes) de la jerarquía de escenas en ese campo y guarde la escena.

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a>Compilación e implementación de la aplicación en HoloLens 2

Azure Spatial Anchors no se puede ejecutar en Unity, de modo que, para probar la funcionalidad Azure Spatial Anchors, debes implementar el proyecto en el dispositivo.

> [!TIP]
> Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación a HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>Ejecutar la aplicación en HoloLens 2 y seguir las instrucciones desde la aplicación

### <a name="create-an-anchor-to-store-a-location"></a>Creación de un anclaje para almacenar una ubicación

En esta sección, verá cómo guardar la ubicación del objeto.

Ejecute la aplicación y haga clic en **Set Object** (Establecer objeto) en el menú principal de la experiencia.

Asigne el **nombre** del objeto que quiera guardar y haga clic en **Set Object** (Establecer objeto) para continuar. Para agregar más información sobre el objeto, seleccione la **imagen** y describa el objeto.

Para guardar la ubicación, haga clic en **Sabe Location** (Guardar ubicación).

Verá un **puntero de anclaje** que puede desplazar y colocar en la ubicación que quiera guardar. Después, se le mostrará una ventana emergente de confirmación. Si quiere confirmar y guardar la ubicación, haga clic en **Sí**. De lo contrario, puede cambiar la ubicación haciendo clic en **No** y seleccionándola de nuevo.

Una vez haya hecho clic en **Sí** para confirmar la ubicación, dicha ubicación y el identificador de anclaje se guardarán en el almacenamiento en la nube de Azure. Una vez guardados, verá la **etiqueta del objeto** en el anclaje con el nombre del objeto.

Ahora la ubicación del objeto se ha guardado correctamente.

### <a name="query-for-finding-an-anchor-location"></a>Consulta para buscar una ubicación de anclaje

Una vez que haya guardado correctamente la ubicación del anclaje, podrá buscar su ubicación. Para ello, seleccione **Search Object** (Buscar objeto) en el menú principal.

Después de hacer clic en **Search Object** (Buscar objeto), aparecerá una nueva ventana en la que deberá proporcionar el nombre del objeto que quiere buscar.

Escríbalo y haga clic en **Search Object** (Buscar objeto). Si el objeto se guarda previamente y se encuentra en la base de datos, obtendrá la tarjeta del objeto con todos los detalles de este que haya guardado anteriormente.

Ahora puede hacer clic en **Show Location** (Mostrar ubicación) para buscar el objeto. Una vez que haga clic en **Show Location** (Mostrar ubicación) , el sistema consultará la dirección del objeto en el almacenamiento en la nube.

Después de recuperar correctamente la ubicación, una **flecha** le dirigirá hacia la ubicación del objeto. Siga la marca de la flecha hasta que encuentre la ubicación del objeto.

Una vez que lo encuentre, su nombre aparecerá en la parte superior y la marca de la flecha desaparecerá. A continuación, podrá hacer clic en la **etiqueta del objeto** para ver sus detalles.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a guardar y recuperar la ubicación del objeto con Azure Spatial Anchors en HoloLens 2.

En el tutorial final, aprenderá a usar **Azure Bot Service** para agregar lenguaje natural como un nuevo método de interacción para nuestra aplicación.

> [!div class="nextstepaction"]
> [Tutorial siguiente: 5. Integración de Azure Bot Service con LUIS](mr-learning-azure-05.md)