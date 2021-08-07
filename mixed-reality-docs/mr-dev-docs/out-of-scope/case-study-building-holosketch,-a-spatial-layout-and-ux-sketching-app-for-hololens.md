---
title: 'Caso práctico: creación de Holo Holo HoloTch, una aplicación de diseño espacial y de dibujo de la experiencia de usuario para HoloLens'
description: Holo Holo HoloTch es una herramienta de diseño espacial en el dispositivo y de dibujo de la experiencia de usuario HoloLens para ayudar a crear experiencias holográficas.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Holo Holo HoloTch, HoloLens, Windows Mixed Reality, sketching, app
ms.openlocfilehash: 614572c91067399cc0235ef2570543aa81e2c24ab36a7b9e9bfa03b77e452420
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213923"
---
# <a name="case-study---building-holosketch-a-spatial-layout-and-ux-sketching-app-for-hololens"></a>Caso práctico: creación de Holo Holo HoloTch, una aplicación de diseño espacial y de dibujo de la experiencia de usuario para HoloLens

Holo Holo HoloTch es una herramienta de diseño espacial en el dispositivo y de dibujo de la experiencia de usuario HoloLens para ayudar a crear experiencias holográficas. HoloPlacetch funciona con un teclado Bluetooth y mouse, así como con comandos de gesto y voz. El propósito de Holo Holo HoloTch es proporcionar una sencilla herramienta de diseño de la experiencia de usuario para una visualización e iteración rápidas.

![Holo Holo HoloTch: una aplicación de diseño espacial y de dibujo de la experiencia de usuario para HoloLens.](images/holosketch-image-01-640px.png)<br>
*Holo Holo HoloTch: diseño espacial y aplicación de dibujo de la experiencia de usuario para HoloLens*

![Una sencilla herramienta de diseño de la experiencia de usuario para una visualización e iteración rápidas.](images/holosketch-image-02.png)<br>
*Una sencilla herramienta de diseño de la experiencia de usuario para una visualización e iteración rápidas*

## <a name="features"></a>Características

### <a name="primitives-for-quick-studies-and-scale-prototyping"></a>Primitivas para estudios rápidos y creación de prototipos de escala

![Uso de formas primitivas](images/holosketch-primitives-giphy.gif)

Use formas primitivas para realizar rápidos estudios de masa y creación de prototipos de escala.

### <a name="import-objects-through-onedrive"></a>Importación de objetos mediante OneDrive

![importar objetos](images/holosketch-importobjects-giphy.gif)

Importe imágenes PNG/JPG u objetos FBX 3D (requiere empaquetado en Unity) en el espacio de realidad mixta a través de OneDrive.

### <a name="manipulate-objects"></a>Manipulación de objetos

![manipular objetos](images/manipulate-objects-640px.jpg)

Manipular objetos (mover, girar o escalar) con una interfaz de objeto 3D conocida.

### <a name="bluetooth-mousekeyboard-gestures-and-voice-commands"></a>Bluetooth, mouse/teclado, gestos y comandos de voz

![admite Bluetooth](images/supports-bluetooth-640px.jpg)

HoloPlacetch admite Bluetooth mouse/teclado, gestos y comandos de voz.

## <a name="background"></a>Segundo plano

### <a name="importance-of-experiencing-your-design-in-the-device"></a>Importancia de experimentar el diseño en el dispositivo

Al diseñar algo para HoloLens, es importante experimentar el diseño en el dispositivo. Uno de los mayores desafíos en el diseño de aplicaciones de realidad mixta es que es difícil obtener la sensación de escala, posición y profundidad, especialmente a través de los bocetos 2D tradicionales.

### <a name="cost-of-2d-based-communication"></a>Costo de la comunicación basada en 2D

Para comunicar eficazmente los flujos y escenarios de la experiencia de usuario a otros usuarios, es posible que un diseñador termine dedicando mucho tiempo a crear recursos mediante herramientas 2D tradicionales, como Designer, Photoshop y PowerPoint. Estos diseños 2D a menudo requieren esfuerzos adicionales para convertirlos en 3D. Algunas ideas se pierden en esta traducción de 2D a 3D.

### <a name="complex-deployment-process"></a>Proceso de implementación complejo

Puesto que la realidad mixta es un nuevo lienzo para nosotros, implica una gran cantidad de iteración de diseño y prueba y error por su naturaleza. Para los diseñadores que no están familiarizados con herramientas como Unity y Visual Studio, no es fácil reunir algo en HoloLens. Normalmente, debe seguir el proceso siguiente para ver las ilustraciones 2D/3D en el dispositivo. Esto era una gran barrera para los diseñadores que iteran en ideas y escenarios rápidamente.

![Proceso de implementación complejo](images/holosketch-image-03-1000px.png)<br>
*Proceso de implementación*

### <a name="simplified-process-with-holosketch"></a>Proceso simplificado con Holo Holo HoloTch

Con Holo Holo HoloTch, queríamos simplificar este proceso sin implicar herramientas de desarrollo ni emparejamiento del portal de dispositivos. Con OneDrive, los usuarios pueden colocar fácilmente recursos 2D/3D en HoloLens.

![Proceso simplificado con Holo Holo HoloTch](images/holosketch-image-04-1000px.png)<br>
*Proceso simplificado con Holo Holo HoloTch*

### <a name="encouraging-three-dimensional-design-thinking-and-solutions"></a>Fomentar soluciones y ideas de diseño tridimensionales

Hemos pensado que esta herramienta ofrecería a los diseñadores una oportunidad para explorar soluciones en un espacio realmente tridimensional y no quedarse atascado en 2D. No tienen que pensar en crear un fondo 3D para su interfaz de usuario, ya que el fondo es el mundo real en el caso de HoloLens. HoloTch abre una manera para que los diseñadores exploren fácilmente el diseño 3D en HoloLens.

## <a name="get-started"></a>Introducción

### <a name="how-to-import-2d-images-jpgpng-into-holosketch"></a>Importación de imágenes 2D (JPG/PNG) en Holo Holo HoloTch

* Upload Imágenes JPG/PNG en OneDrive carpeta "Documents/Holo Holo HoloTch".
* En el OneDrive de holoTipo, podrá seleccionar y colocar la imagen en el entorno.

![Importación de imágenes 2D](images/import-2d-images-1000px.jpg)<br>
*Importación de imágenes y objetos 3D mediante OneDrive*

### <a name="how-to-import-3d-objects-into-holosketch"></a>Importación de objetos 3D en Holo HoloTch

Antes de cargar en la OneDrive, siga los pasos que se indican a continuación para empaquetar los objetos 3D en un conjunto de recursos de Unity. Con este proceso puede importar los archivos FBX/OBJ desde software 3D como Maya, Cine 4D y Microsoft Paint 3D.

>[!IMPORTANT]
>Actualmente, la creación de lotes de recursos se admite con la versión 5.4.5f1 de Unity.

1. Descargue y abra el proyecto de Unity ["AssetBunlder_Unity".](https://github.com/Microsoft/MRDesignLabs/tree/master/ReleasedApps/HoloSketch/AssetBundler_Unity) Este proyecto de Unity incluye el script para la generación de recursos de agrupación.
2. Cree un elemento GameObject.
3. Asigne el nombre GameObject en función del contenido.
4. En el panel Inspector, haga clic en "Agregar componente" y agregue "Box Collider". 

   ![En el panel Inspector, haga clic en "Agregar componente" y agregue "Box Collider".](images/holosketch-10a-assetbundles-1000px.png)
   
   ![En el panel Inspector, haga clic en "Agregar componente" y agregue "Box Collider" #2](images/holosketch-10b-assetbundles-1000px.png)

5. Importe el archivo FBX 3D arrastrándolo al panel del proyecto.
6. Arrastre el objeto al panel Jerarquía **bajo el nuevo GameObject**.

   ![Arrastre el objeto al panel Jerarquía debajo del nuevo GameObject.](images/holosketch-12-assetbundles-1000px.png)

7. Ajuste la dimensión del colisionador si no coincide con el objeto . Gira el objeto para dar la **cara al eje Z.**

   ![Ajuste la dimensión del colisionador si no coincide con el objeto .](images/holosketch-13-assetbundles-1000px.png)

8. Arrastre el objeto desde el panel Jerarquía hasta Project panel para que **sea prefab.**
9. En la parte inferior del panel del inspector, haga clic en la lista desplegable, cree y asigne un nuevo nombre único. En el ejemplo siguiente se muestra cómo agregar y asignar "brownchair" para assetBundle Name. 

   ![En la parte inferior del panel del inspector, haga clic en la lista desplegable y asigne un nuevo nombre único.](images/holosketch-14-assetbundles-1000px.png)

10. Prepare una imagen en miniatura para el objeto de modelo. 
   ![Arrastre una imagen al panel del proyecto y asigne el nombre usado para el objeto.](images/holosketch-15-assetbundles-1000px.png)

11. Cree una carpeta denominada "Assetbundles" en la carpeta "Asset" del proyecto de Unity.

12. En el menú Activos, seleccione "Compilar assetBundles" para generar el archivo. 
   ![En el menú Activos, seleccione "Compilar assetBundles" para generar el archivo.](images/holosketch-15a-assetbundles.png)


13. **Upload el archivo generado en la carpeta /Files/Documents/Holo Holo HoloTch en OneDrive.** Upload solo asset_unique_name archivo. No es necesario cargar archivos de manifiesto ni archivos AssetBundles. <br>
![Agregar archivos a la carpeta Files/Documents/Holo Holo HoloTch/ Verá que se ha agregado un objeto 3D en el menú de OneDrive ](images/holosketch-onedriveupload-1000px.png)
 ![ HoloTch.](images/holosketch-14-onedriveexample-1000px.jpg)

## <a name="how-to-manipulate-the-objects"></a>Cómo manipular los objetos

Holo HoloTch admite la interfaz tradicional que se usa ampliamente en software 3D. Puede usar mover, girar y escalar los objetos con gestos y un mouse. Puede cambiar rápidamente entre diferentes modos con voz o teclado.

### <a name="object-manipulation-modes"></a>Modos de manipulación de objetos

![Cómo manipular los objetos](images/holosketch-image-06-1000px.png)<br>
*Cómo manipular los objetos*

### <a name="contextual-and-tool-belt-menus"></a>Menús contextuales y de la cinta de herramientas

**Uso del menú contextual**

Pulse dos veces en el aire para abrir el menú contextual. 

Elementos de menú:
* **Superficie de diseño:** Se trata de un sistema de cuadrícula 3D donde puede crear varios objetos y administrarlos como un grupo. Pulse dos veces en la superficie de diseño para agregarle objetos.
* **Primitivas:** Use cubos, esferas, cilindros y conos para realizar estudios de masa.
* **OneDrive:** Abra el menú OneDrive para importar objetos.
* **Ayuda:** Muestra la pantalla de ayuda.

![Menú contextual](images/holosketch-image-07.png)<br>
*Menú contextual*

**Uso del menú de la cinta de herramientas**

Move, Rotate, Scale, Save y Load Scene están disponibles en el menú Tool Belt (Cinta de herramientas). 

## <a name="using-keyboard-gestures-and-voice-commands"></a>Uso de teclado, gestos y comandos de voz

![Teclado, gestos y comandos de voz](images/holosketch-image-08-1000px.png)<br>
*Teclado, gestos y comandos de voz*

## <a name="download-the-app"></a>Descargar la aplicación

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="HoloSketch app icon" width="60" height="60" src="images/holosketch-app-icon.png">
</td>
<td style="border-style: none"><a href="https://www.microsoft.com/store/p/holosketch/9p3br4t5m4tv">Descargue e instale la aplicación HoloTch de forma gratuita desde el Microsoft Store</a>
</td>
</tr>
</table>

## <a name="known-issues"></a>Problemas conocidos
* Actualmente, la creación de paquetes de recursos es compatible con **la versión 5.4.5f1 de Unity.**
* Dependiendo de la cantidad de datos de la OneDrive, la aplicación podría aparecer como si se hubiera detenido al cargar OneDrive contenido.
* Actualmente, la característica Guardar y cargar solo admite objetos primitivos
* Los menús Texto, Sonido, Vídeo y Foto están deshabilitados en el menú contextual
* El botón Reproducir del menú Tool Belt (Cinta de herramientas) borra los gizmos de manipulación

## <a name="sharing-your-sketches"></a>Uso compartido de los bocetos

Puede usar la característica de grabación de vídeo en HoloLens decir "Hey Cortana, Start/Stop recording". Presione la tecla de subir o bajar volumen juntas para tomar una imagen del boceto.

## <a name="about-the-authors"></a>Acerca de los autores

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><a href="http://dongyoonpark.com" target="_blank"><b>Yoon Park</b></a><br>Diseñador de experiencias de usuario @Microsoft</td>
</tr>
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Patrick Sebring" width="60" height="60" src="images/paseb-60px.jpg"></td>
<td style="border-style: none"><b>Patrick Sebring</b><br>Desarrollador @Microsoft</td>
</tr>
</table> 