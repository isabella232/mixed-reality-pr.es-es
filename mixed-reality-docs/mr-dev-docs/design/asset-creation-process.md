---
title: Proceso de creación de recursos
description: Aprenda a crear, comprar y portabilidad recursos para experiencias de realidad mixta.
author: shengkait
ms.author: shentan
ms.date: 03/21/2018
ms.topic: article
keywords: asset, creation, process, budget, polygons, textures, shaders, performance, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit, assets
ms.openlocfilehash: 5c5dcdbe24a8028bb8a3c57e57b9d95079f9e832954d12aa31421dd75f1b6982
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214118"
---
# <a name="asset-creation-process"></a>Proceso de creación de recursos

Windows Mixed Reality se basa en las décadas de inversión que Microsoft ha realizado en DirectX. Toda la experiencia y las aptitudes que tienen los desarrolladores con la creación de gráficos 3D sigue siendo valiosa con HoloLens.

Los recursos que se crean para un proyecto tienen muchas formas y formas. Pueden estar compuestos por una serie de texturas o imágenes, audio, vídeo, modelos 3D y animaciones. No podemos empezar a cubrir todas las herramientas que están disponibles para crear los distintos tipos de recursos usados en un proyecto. En este artículo, nos centraremos en los métodos de creación de recursos 3D.

![Flujo de concepto, creación, integración e iteración](images/concept-creation-integration-iteration-flow-640px.jpg)<br>
*Flujo de concepto, creación, integración e iteración*

## <a name="things-to-consider"></a>Aspectos que se deben tener en cuenta:

Al mirar la experiencia, está intentando crearla,  piense en ella como un presupuesto que puede gastar para intentar crear la mejor experiencia. No hay necesariamente límites en el número de **polígonos** o tipos de **material** que puede usar en los recursos. Conséndalo más como un conjunto presupuestado de recompensas.

A continuación se muestra un presupuesto de ejemplo para su experiencia. El rendimiento no es un único punto de error, sino la muerte por miles de cortes.
<br>

<table style="float:right; margin-left: 10px;">
<tr>
<th style="text-align:left;"><b>Recursos</b></th><th style="text-align:right;"> CPU</th><th> GPU</th><th> Memoria</th>
</tr><tr>
<td> Polígonos</td><td> 0 %</td><td> 5 %</td><td> 10 %</td>
</tr><tr>
<td> Texturas</td><td> 5 %</td><td> 15 %</td><td>25 %</td>
</tr><tr>
<td> Sombreadores</td><td> 15 %</td><td> 35 %</td><td> 0 %</td>
</tr><tr>
<td> <b>Dynamics</b></td><td></td><td></td><td></td>
</tr><tr>
<td> Física</td><td> 5 %</td><td> 15 %</td><td> 0 %</td>
</tr><tr>
<td> Iluminación en tiempo real</td><td> 10 %</td><td> 0 %</td><td> 0 %</td>
</tr><tr>
<td> Medios (audio y vídeo)</td><td> -</td><td> 15 %</td><td> 25 %</td>
</tr><tr>
<td> Script/lógica</td><td> 25 %</td><td> 0 %</td><td> 5 %</td>
</tr><tr>
<td> Sobrecarga general</td><td> 5 %</td><td> 5 %</td><td> 5 %</td>
</tr><tr>
<td> <b>Total</b></td><td> <b>65%</b></td><td> <b>90 %</b></td><td> <b>70%</b></td>
</tr>
</table>

**Número total de recursos**
* ¿Cuántos recursos están activos en la escena?

**Complejidad de los recursos**
* ¿Cuántos triángulos o polígonos?
* ¿Qué complejidad tiene el sombreador? Al usar el Mixed Reality Toolkit, se recomienda usar el [sombreador Mixed Reality Toolkit estándar](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md) para reducir la complejidad del sombreador.

Tanto los desarrolladores como los creadores tienen que tener en cuenta las funcionalidades del dispositivo y el motor de gráficos. Microsoft HoloLens todos los gráficos y computacionales integrados en el dispositivo. Comparte las funcionalidades que los desarrolladores encontrarían en una plataforma móvil.

El proceso de creación de recursos es el mismo si la experiencia tiene como destino un [dispositivo holográfico o un dispositivo inmersivo.](../discover/mixed-reality.md#the-mixed-reality-spectrum) Lo principal que debe tener en cuenta es la funcionalidad y la escala del dispositivo. Puede ver el mundo real en realidad mixta, por lo que querrá mantener la escala correcta en función de la experiencia.

## <a name="authoring-assets"></a>Creación de recursos

Comenzaremos con las formas de obtener recursos para el proyecto:
1. Crear recursos (herramientas de creación y captura de objetos)
2. Adquisición de recursos (compra de recursos en línea)
3. Porte de recursos (tomar recursos existentes)
4. Outsourcing Assets (Importar recursos de terceros)

### <a name="creating-assets"></a>Creación de recursos

**Herramientas de creación**<br>
En primer lugar, puede crear sus propios recursos de varias maneras diferentes. Los dibujantes 3D usan diversas aplicaciones y herramientas para crear modelos, que constan de **mallas, texturas** y **materiales.** A continuación, se guarda en un formato de archivo que puede importar o usar el motor de gráficos utilizado por la aplicación, como **. FBX** o **. OBJ**. Cualquier herramienta que genere un modelo compatible con el motor de gráficos elegido funcionará en **HoloLens**. Entre los intérpretes en 3D, muchos deciden usar Maya de [Autodesk](https://www.youtube.com/watch?v=q0K3n0Gf8mA) porque puede usar HoloLens transformar la forma en que se crean los recursos. Si desea obtener algo rápidamente, también puede usar 3D Builder [que](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) se incluye con Windows para exportar . OBJ para su uso en la aplicación.

**Captura de objetos**<br>
También existe la opción de capturar objetos en 3D. La captura de objetos inanimados en 3D y su edición con software de creación de contenido digital es cada vez más popular con el aumento de la impresión 3D. Con el **sensor Kinect 2** y [3D Builder](https://developer.microsoft.com/windows/hardware/3d-print/3d-builder-resources) puede usar la característica de captura para crear recursos a partir de objetos del mundo real. También se trata de un [conjunto de herramientas para](https://en.wikipedia.org/wiki/Comparison_of_photogrammetry_software) hacer lo mismo con la **fotogrametría** mediante el procesamiento de varias imágenes para unir y mallar y texturas.

### <a name="purchasing-assets"></a>Compra de recursos

Otra excelente opción es comprar recursos para su experiencia. Hay una gran cantidad de recursos disponibles a través de servicios como [Unity Asset Store](https://www.assetstore.unity3d.com/) o [TurboSquid,](https://www.turbosquid.com/) entre otros.

Al comprar recursos de un tercero, siempre quiere comprobar las siguientes propiedades:
* **¿Cuál es el recuento de polis?**
  * ¿Se ajusta a su presupuesto?
* **¿Hay niveles de detalle (LOD) para el modelo?**
  * Un nivel de detalle de modelos permite escalar los detalles de un modelo para mejorar el rendimiento.
* **¿Está disponible el archivo de código fuente?**
  * No se incluye [con Unity Asset Store,](https://www.assetstore.unity3d.com/) pero siempre se incluye con servicios [como TurboSquid.](https://www.turbosquid.com/)
  * Sin el archivo de código fuente, no se puede modificar el recurso.
  * Asegúrese de que las herramientas 3D pueden importar el archivo de origen proporcionado.
* **Saber lo que está obteniendo**
  * ¿Se proporcionan animaciones?
  * Asegúrese de comprobar la lista de contenido del recurso que está comprando.

### <a name="porting-assets"></a>Porte de recursos

En algunos casos, se le entregarán los recursos existentes que se han creado originalmente para otros dispositivos y aplicaciones diferentes. En la mayoría de los casos, estos recursos se pueden convertir en formatos compatibles con el motor de gráficos que usa su aplicación.

Al portear recursos para usarlos en HoloLens aplicación, querrá hacer las siguientes preguntas:
* **¿Puede importar directamente o debe convertirse a otro formato?** Compruebe el formato que va a importar con el motor de gráficos que está usando.
* **¿Si se pierde algo al convertir a un formato compatible?** A veces, los detalles se pueden perder o la importación puede provocar artefactos que deben limpiarse en una herramienta de creación 3D.
* **¿Cuál es el número de triángulos o polígonos para el recurso?** En función del presupuesto de la aplicación, puede usar [Simplygon](https://www.simplygon.com/) o herramientas similares para desacociar (por procedimientos o manualmente el recuento de polis) el recurso original para ajustarlo al presupuesto de las aplicaciones.

### <a name="outsourcing-assets"></a>Externalización de recursos

Otra opción para proyectos más grandes que requieren más recursos de los que el equipo está equipado para crear es externalizar la creación de recursos. El proceso de externalización implica encontrar el estudio o la agencia adecuados que se especializan en externalizar recursos. Puede ser la opción más costosa, pero también la más flexible en lo que se obtiene.
* **Defina claramente lo que está solicitando.**
  * Proporcione tantos detalles como sea posible.
  * Imágenes de concepto frontal, lateral y posterior
  * Arte de referencia que muestra el recurso en contexto
  * Escala del objeto (normalmente se especifica en centímetros)
* **Proporcionar un presupuesto**
  * Intervalo de recuento de poli
  * Número de texturas
  * Tipo de sombreador (para Unity y HoloLens siempre debe usar primero los sombreadores móviles de forma predeterminada)
* **Comprender los costos**
  * ¿Cuál es la directiva de externalización para las solicitudes de cambio?

La externalización puede funcionar bien en función de la escala de tiempo de los proyectos, pero requiere más supervisión para garantizar que obtiene los recursos adecuados que necesita la primera vez.
