---
title: Asesor manual
description: Obtenga información sobre cómo se desencadenan las manos 3D mediante el entrenador de la mano cuando el sistema no detecta las manos del usuario para ayudarles.
author: grayclee
ms.author: glee
ms.date: 09/25/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, manual, casco envolvente, MRTK, manos, manos de ayuda, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, casco de realidad virtual, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: baf1dab7d73f4e5fca9078717b43dab7b71632f4aa7c36dcac280c029b05d58b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208606"
---
# <a name="hand-coach"></a>Asesor manual

![Ejemplo: Técnico de mano](images/HandCoach/MRTK_handCoach.jpg)<br>

El preparador de manos desencadena las manos modeladas en 3D cuando el sistema no detecta las manos del usuario. Esta característica es un componente de "enseñanza" que ayuda a guiar al usuario cuando no se ha enseñado el gesto. Si los usuarios no han realizado el gesto especificado durante un período, las manos se pondrán en bucle con un retraso. El entrenador de la mano podría usarse para representar la pulsación de un botón o la selección de un holograma.  

## <a name="hand-coach-provided"></a>Técnico de mano proporcionado

El modelo de interacción actual representa una amplia variedad de controles de gestos, como el desplazamiento, la selección lejana y la pulsación próxima. A continuación se muestra una lista completa de los gestos de mano existentes proporcionados<a href="https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets"> en MRTK:</a>

:::row:::
    :::column:::
       ![Ejemplo de selección próxima](images/HandCoach/NearSelect.gif)<br>
       **Ejemplo de selección cercana: se usa para mostrar cómo seleccionar botones o cerrar objetos interactuables**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de pulsación en el aire](images/HandCoach/AirTap.gif)<br>
        **Ejemplo de pulsación en el aire: se usa para mostrar cómo seleccionar objetos que están lejos**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de movimiento](images/HandCoach/Move.gif)<br>
       **Ejemplo de movimiento de un objeto en el espacio usado para mostrar cómo mover un holograma en el espacio**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de rotación](images/HandCoach/Rotate.gif)<br>
       **Ejemplo de Rotate-Used para mostrar cómo girar hologramas u objetos**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![Ejemplo de escala](images/HandCoach/Scale.gif)<br>
       **Ejemplo de escala: se usa para mostrar cómo manipular hologramas para que sean más grandes o más pequeños.**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de Pie Up](images/HandCoach/PalmUp.gif)<br>
        **Ejemplo de La mano arriba: uso sugerido para mostrar menús de mano**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de HandFlip](images/HandCoach/HandFlip.gif)<br>
       **Exmaple of Hand Flip : otra manera de mostrar menús de mano**<br>
    :::column-end:::
    :::column:::
       ![Ejemplo de desplazamiento](images/HandCoach/Scoll.gif)<br>
       **Ejemplo de desplazamiento: se usa para desplazar una lista o un documento largo**<br>
    :::column-end:::
:::row-end:::

## <a name="design-concepts"></a>Conceptos de diseño

Para Hololens2, hemos diseñado interacciones a mano basadas en gestos instintivo y naturales de la mano. Creemos que son intuitivas para la mayoría de los usuarios, por lo que no creamos momentos dedicados de aprendizaje de gestos. En su lugar, creamos el entrenador de la mano para ayudar a los usuarios a obtener información sobre estos gestos si se atasca o no están familiarizados con las interacciones de hologramas. Sin un momento de aprendizaje, creemos que mostrar a los usuarios cómo realizar una acción demostrando que sería la mejor opción. Hemos descubierto que los usuarios pudieron averiguar el gesto, pero necesitaron una pequeña guía. Si detectamos que un usuario no interactúa con un objeto durante un período, se desencadenaría un carro de la mano que mostrara la colocación correcta de la mano y el dedo. 

### <a name="intuitive"></a>Intuitiva

Al animar las manos, debe ser obvio y no debe causar confusión. La animación con la mano es una representación del gesto que intenta pedir al usuario que lo entienda. 

Por ejemplo, si desea que un usuario presione un botón, se desencadenará una mano presionando un botón.

![Ejemplo: Hand Coach Near Tap](images/HandCoach/NearSelect_unity.gif)<br>
*Hand Coach que se muestra cerca de pulsar una gema*  

### <a name="hand-scale"></a>Escala de la mano

Hemos probado varios tamaños de mano con los menús de la interfaz de usuario y creemos que, si las manos eran verdaderas al tamaño, daba una sensación amenazante. Si eran demasiado pequeños, era difícil ver y comprender el gesto. 

**Voz y manos**

No espere que los usuarios puedan escuchar un conjunto de instrucciones a través de la voz y ver instrucciones diferentes a través de Hand Coach. Secuencia las instrucciones para ayudar a los usuarios a centrarse frente a competir por su atención para reducir la sobrecarga del sensor.


## <a name="can-i-create-my-own"></a>¿Puedo crear los suyos propios?

Sí. Le animamos a crear su propio gesto único para su juego y contribuir de nuevo a la comunidad.
Hemos proporcionado un archivo Maya de una mano desasistido que se puede usar para la aplicación, que se puede descargar aquí: <a href="files/HandCoach_MRTK.zip"> Descargar HandCoach_MRTK.zip </a>

![Ejemplo de manos animadas en Maya](images/HandCoach/MayaSelect_Gif.gif)<br>
*Ejemplo de caja de mano animada en Maya*


**Herramienta de creación recomendada**

Entre los intérpretes en 3D, muchos deciden usar Maya de [Autodesk,](https://www.youtube.com/watch?v=q0K3n0Gf8mA) que puede usar HoloLens para transformar la forma en que se crean los recursos. El archivo de manos proporcionado es un archivo binario maya, por lo que se recomienda usar Maya para animar y exportar las manos. Si prefiere usar otro programa 3D, este es un <b>. FBX:</b> <a href="files/HandCoachMRTK_FBX.zip"> descargue HandCoachMRTK_FBX.zip </a> para crear su propia configuración de controlador. 

Si usa el archivo de mano maya descargable proporcionado, se recomienda reducir verticalmente las manos de Unity a 0,6.

![Ejemplo: equipo de carros de mano en Maya](images/HandCoach/MayaExample.png)<br>
*Manos desapareadas*

### <a name="technical-specs"></a>Especificaciones técnicas

*   El archivo con dos manos está disponible en formato Maya Ascii
*    La mano derecha e izquierda está disponible en formato binario maya
*   Establecer el archivo Maya en 24 FPS
*   Dentro del archivo, hay una mano izquierda y derecha, que se puede usar para gestos con dos manos o con una sola mano. La mano derecha solo estará visible de forma predeterminada.
*   Se recomienda dejar un búfer de unos 10 fotogramas al principio y al final para atenuaciones.
*   Si anima un objeto con un destino especificado, su procedimiento recomendado es animar a un cuadro Predeterminado o Null.
*   Si la mano anima un objeto físico como un cuadro, su procedimiento recomendado es no animar la traducción en Maya, sino esperar a animarlo en Unity o en código.
*   La animación visible debe ser de 1,5 segundos para que se transmita cualquier información significativa
*   Cuando se sienta satisfecho con la animación:
    *   Seleccionar todas las uniones y hacer "bake key frames"
    *   Eliminar los controladores, seleccionar las uniones y la malla y exportar como FBX
    *  Si hay varias animaciones, puede usar el exportador de juegos integrado de Maya: https://knowledge.autodesk.com/support/maya/learn-explore/caas/CloudHelp/cloudhelp/2015/ENU/Maya/files/Game-Exporter-htm.html

## <a name="exporting-from-maya"></a>Exportación desde Maya

Una vez que esté satisfecho con la animación
* Seleccionar todas las uniones: seleccione > jerarquía

     ![Ejemplo: Jerarquía en el menú](images/HandCoach/Hierarchy.png)<br>
* Bake out your animation (Bake out your animation): cambiar a Animation > Key > Bake Animation

     ![Ejemplo: Ubicación del menú De animación de "bake"](images/HandCoach/BakeAnimation.png)<br>
* Eliminar el equipo del controlador: esquema > MainR_Grp o MainL_Grp

     ![Ejemplo: Ubicación del menú Del controlador](images/HandCoach/ControllerRig.png)<br>

* Exportar como FBX: Seleccione JNT + Malla: Selección > exportar archivos (cuadro de opciones) > exportar selección

     ![Ejemplo: Exportar ubicación del menú de selección](images/HandCoach/OptionBox.png)<br>

     ![Ejemplo: Ubicación del menú](images/HandCoach/SelectionExport.png)<br>

     ![Ejemplo: Ubicación del menú Opciones de exportación](images/HandCoach/FBXSelection.png)<br>


 Al exportar como FBX y pasar a Unity, escale las manos hacia abajo a 0,6. Encontramos que esto era un equilibrio perfecto para mostrar las manos. 

![Ejemplo: Unity Configuración](images/HandCoach/HandHintScale.png)<br>
*Unity Configuración para HandCoach_R prefab encontrado en MRTK*


## <a name="implementing-hands-into-your-unity-project"></a>Implementación de manos en el proyecto de Unity

### <a name="best-practices"></a>Procedimientos recomendados

* Se recomienda reducir verticalmente las manos en Unity a 0,6
* Las manos se deben reproducir dos veces y, si no se completan, se recorren continuamente en bucle hasta que se completa el gesto. Las manos se deben recorrer en bucle dos veces para asegurarse de que el usuario tiene tiempo para registrarse y ver el gesto. Las manos deben atenuarse entre bucles. 
 *  Si las manos del usuario son visibles por las cámaras HL2, pero los usuarios no están realizando la interacción necesaria de ellas, las manos aparecerán después de 10 segundos.
*   Si las manos del usuario NO son visibles por las cámaras HL2, las manos aparecerán después de 5 segundos.  
*   Si las cámaras HL2 del centro de la animación realiza un seguimiento visible de las manos del usuario, la animación se completará y se atenuará.
*   Si va a incluir la voz en exceso, se recomienda que se corresponda con el gesto de la mano.
*   Si ha enseñado las manos al menos una vez, repita el gesto solo si se detecta que el usuario está atascado.
*   Si las posiciones específicas de los dedos y las manos son críticas, asegúrese de que los usuarios puedan ver claramente estos matices en la animación. Pruebe a usar las manos para que las partes más importantes sean claramente visibles. 
* Si observa distorsión en las manos, debe ir a La configuración de calidad de Unity aumenta el número de pies. 
 Vaya a Edit (Editar) de Unity > Project Configuración > Quality > Other > Blend Weights (Otros pesos > Blend). Asegúrese de que se seleccionan "4 esqueletos" para ver Smooth Joints (Juntas suavizadas).

   ![Ejemplo: Project Configuración ventana](images/HandCoach/ProjectSettings.png)<br>


### <a name="what-to-avoid"></a>Qué evitar

* Escalado de las manos demasiado grandes
* colocar las manos demasiado cerca del usuario
* Las manos solo se deben enseñar una vez. La enseñanza excesiva puede provocar confusión y desorden
* Para incorporarlo a Unity, descargue la versión más reciente de MRTK aquí: https://github.com/microsoft/MixedRealityToolkit-Unity
  * Material: Teaching_Hand2
  * Scripts: consulte las directrices de MRTK para <a href= "/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-coach"> el técnico de MRTK. </a>
  * Configuración por proyecto
    * Escena establecida en UWP: la instrucción se puede encontrar en la página [Configurar unity Project](../develop/unity/Configure-Unity-Project.md) para Windows Mixed Reality

## <a name="see-also"></a>Consulte también

* [Aspectos básicos de la interacción](interaction-fundamentals.md)
* [Proceso de creación de recursos](asset-creation-process.md)
* [Gestos](./interaction-fundamentals.md)
* [Instalar las herramientas](../develop/install-the-tools.md)
* [Configuración de unity Project](../develop/unity/Configure-Unity-Project.md)
* [Introducción al desarrollo de Unity](../develop/unity/unity-development-overview.md)
* [MRTK 101](/windows/mixed-reality/mrtk-unity/)