---
title: Anclajes espaciales locales en Unreal
description: Aprenda a usar, guardar y administrar delimitadores espaciales en aplicaciones de realidad mixta de Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, spatial anchors, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: c8fe7fef5af247663eefed097d3494d6187195272967434ecc7696349e1e6889
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213604"
---
# <a name="local-spatial-anchors-in-unreal"></a>Anclajes espaciales locales en Unreal

Los anclajes espaciales sirven para guardar los hologramas en el espacio del mundo real entre sesiones de aplicación como **ARPin**. Una vez guardados en el almacén de anclajes de HoloLens,los ARPin se pueden cargar en futuras sesiones y es una opción de reserva ideal cuando no hay conectividad a Internet.

> [!NOTE]
> Las funciones de anclaje de UE 4.25 han quedado obsoletas en la versión 4.26 y deben reemplazarse por otras más recientes. 

> [!IMPORTANT]
> Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube. Si desea usar servicios en la nube de Azure para almacenar los anclajes, existe un documento que le guiará por la integración de [Azure Spatial Anchors](unreal-azure-spatial-anchors.md). Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.

## <a name="checking-the-anchor-store"></a>Comprobación del almacén de anclajes

Antes de guardar o cargar anclajes, debe comprobar si el almacén de anclajes está listo.  Si se llama a cualquiera de las funciones de anclaje de HoloLens antes de que el almacén de anclajes esté listo, la llamada no se completará correctamente.  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a>Guardar anclajes

Cuando la aplicación tenga un componente que se necesite anclar en el mundo, se puede guardar en el almacén de anclajes con la siguiente secuencia: 

[!INCLUDE[](includes/tabs-sa-2.md)]

Desglose:
1. Genere un actor en una ubicación conocida.
2. Cree un elemento **ARPin** con esa ubicación y un nombre basado en la clase del actor. 
3. Agregue el actor al elemento **ARPin** y guarde el marcador en el almacén de anclajes de HoloLens.  
    * El nombre del anclaje que elija debe ser único, en este ejemplo, es la marca de tiempo actual. 

4. Si el anclaje se guarda correctamente en el almacén de anclajes, se puede establecer en el portal de dispositivos de HoloLens en **Sistema > Administrador de mapas > Archivos de anclajes guardados en el dispositivo**. 

## <a name="loading-anchors"></a>Carga de anclajes

Cuando se inicia una aplicación, se puede usar el siguiente plano técnico para restaurar los componentes en sus ubicaciones de anclaje:

[!INCLUDE[](includes/tabs-sa-3.md)]

Desglose:
1. Recorra en iteración todos los anclajes del almacén de anclajes. 
2. Genere un actor en la identidad.
3. Marque ese actor en **ARPin** en el almacén de anclajes.  

    * Es importante generar el actor en la identidad, ya que el anclaje es responsable de cambiar la posición del holograma en el mundo en función de dónde se guardó. Cualquier transformación que se proporcione aquí agregará un desplazamiento al anclaje. 

También se consulta el identificador del anclaje para que se puedan generar diferentes actores en función del nombre guardado del anclaje. 

## <a name="removing-anchors"></a>Eliminación de anclajes 

Cuando haya terminado con un anclaje, puede borrar anclajes individuales o todo el almacén de anclajes con los componentes **Quitar ARPin del almacén WMRAnchor** y **Quitar todos los ARPin del almacén WMRAnchor**.

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> Tenga en cuenta que Spatial Anchors todavía están en versión beta, por lo que debe asegurarse de consultar la información y las características actualizadas.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación: 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](unreal-development-overview.md#2-core-building-blocks) en cualquier momento.

## <a name="see-also"></a>Consulta también

* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [Delimitadores espaciales](../../design/spatial-anchors.md)
* [Sistemas de coordenadas](../../design/coordinate-systems.md)
