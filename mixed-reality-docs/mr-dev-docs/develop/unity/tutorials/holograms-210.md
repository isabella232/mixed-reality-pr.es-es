---
title: 'Entrada de HoloLens de primera generación (210): mirada'
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los detalles de los conceptos de mirada.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, gaze, HoloLens, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset, Windows 10
ms.openlocfilehash: e0d761c6292502f381618f8efa1bed9d26f0e6fbac8dbdafa8085e0bb41676ce
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220984"
---
# <a name="hololens-1st-gen-input-210-gaze"></a>HoloLens (1ª generación) Entrada 210: Mirada

>[!IMPORTANT]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (1ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se actualizarán_** con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

[La](../../../design/gaze-and-commit.md) mirada es la primera forma de entrada y revela la intención y el reconocimiento del usuario. Mr Input 210 (también conocido como Project Explorer) es un análisis profundo de los conceptos relacionados con la mirada para Windows Mixed Reality. Vamos a agregar reconocimiento contextual a nuestro cursor y hologramas, aprovechando al máximo lo que la aplicación sabe sobre la mirada del usuario.

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

Aquí tenemos un astronauta descriptivo para ayudarle a aprender los conceptos de mirada. En [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md), teníamos un cursor simple que acaba de seguir la mirada. Hoy vamos a avanzar un paso más allá del cursor simple:

* Estamos haciendo que el cursor y nuestros hologramas conste de mirada: ambos cambiarán en función de dónde esté buscando el usuario o de dónde no *lo* esté buscando el usuario. Esto los hace conscientes del contexto.
* Agregaremos comentarios a nuestro cursor y hologramas para proporcionar al usuario más contexto sobre lo que se va a dirigir. Estos comentarios pueden ser audio y objetos visuales.
* Le mostraremos técnicas de destino para ayudar a los usuarios a alcanzar objetivos más pequeños.
* Le mostraremos cómo llamar la atención del usuario sobre los hologramas con un indicador direccional.
* Le enseñaremos técnicas para llevar los hologramas con el usuario a medida que se mueve por su mundo.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el Mixed Reality Toolkit. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la pósteridad y porque los conceptos tratados siguen siendo aplicables.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Aspectos básicos de realidad mixta (210): Mirar</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../../develop/install-the-tools.md)
* Alguna capacidad básica de programación de C#.
* Debe haber completado [Mr Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Un HoloLens configurado [para el desarrollo.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) requeridos por el proyecto. Requiere Unity 2017.2 o posterior.
* Des archive los archivos en el escritorio u otra ubicación de fácil acceso.

>[!NOTE]
>Si desea buscar en el código fuente antes de descargarlo, está [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).

### <a name="errata-and-notes"></a>Errata y Notes

* En Visual Studio, "Solo mi código" debe deshabilitarse (desactivada) en Herramientas->Opciones->Depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-1---unity-setup"></a>Capítulo 1: Configuración de Unity

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a>Objetivos

* Optimizar Unity para el desarrollo de HoloLens.
* Importar recursos y configurar la escena.
* Vea al astronauta en la HoloLens.

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **Nuevo proyecto**.
3. Asigne al proyecto **el nombre ModelExplorer.**
4. Escriba location (Ubicación) como **la carpeta Gaze** (Mirada) que anteriormente des archivó.
5. Asegúrate de que el proyecto esté establecido en **3D** (3D).
6. Haga **clic en Crear Project**.

### <a name="unity-settings-for-hololens"></a>Configuración de Unity para HoloLens

Necesitamos que Unity sepa que la aplicación que estamos intentando exportar debe crear una vista [inmersiva](../../../design/app-views.md) en lugar de una vista 2D. Para ello, agregamos HoloLens como un dispositivo de realidad virtual.

1. Vaya a **Editar > Project Configuración > Player**.
2. En el **panel Inspector para** player Configuración, seleccione el icono Windows **Store.**
3. Expanda el grupo **XR Settings** (Configuración de XR).
4. En la sección **Rendering** (Representación), active la casilla **Virtual Reality Supported** (Se admite Virtual Reality) para agregar una nueva lista de **SDK de Virtual Reality**.
5. Compruebe que **Windows Mixed Reality** (Mixed Reality de Windows) aparece en la lista. Si no es así, seleccione el botón situado en la parte inferior de la lista y **+** **elija Windows Holographic**.

A continuación, es necesario establecer el back-end de scripting en .NET.

1. Vaya a **Editar > Project Configuración > Player** (es posible que todavía tenga esto en el paso anterior).
2. En el **panel Inspector para** player Configuración, seleccione el icono Windows **Store.**
3. En la **sección Otros Configuración** configuración, asegúrese de que El back-end de **scripting** está establecido en **.NET.**

Por último, actualizaremos la configuración de calidad para lograr un rendimiento rápido en HoloLens.

1. Vaya a **Editar > Project Configuración > calidad**.
2. Haga clic en la flecha hacia abajo en la **fila** Predeterminada debajo del icono Windows Store.
3. Seleccione **Very Low (Muy** **bajo) para Windows Store Apps (Aplicaciones de la Tienda).**

### <a name="import-project-assets"></a>Importación de recursos de proyecto

1. Haga clic con el **botón derecho** en la carpeta **Activos Project** panel.
2. Haga clic **en Importar paquete > paquete personalizado**.
3. Vaya a los archivos del proyecto que descargó y haga clic **en ModelExplorer.unitypackage**.
4. Haga clic en **Abrir**.
5. Una vez cargado el paquete, haga clic en **el botón** Importar.

### <a name="setup-the-scene"></a>Configuración de la escena

1. En la jerarquía, elimine la **cámara principal**.
2. En la **carpeta HoloToolkit,** abra la **carpeta Entrada** y, a continuación, abra la **carpeta Prefabs.**
3. Arrastre y coloque el prefab **MixedRealityCameraParent** de la **carpeta Prefabs** en **hierarchy**.
4. Haga clic con el botón **derecho en la luz** direccional de la jerarquía y seleccione **Eliminar.**
5. En la **Hologramas,** arrastre y coloque los siguientes recursos en la raíz de la **jerarquía**:
    * **AstroMan**
    * **Luces**
    * **SpaceAudioSource**
    * **SpaceBackground**
6. Inicie **el modo de** ▶ para ver al astronauta.
7. Haga **clic en Modo** de ▶ de nuevo para **detener**.
8. En la **Hologramas,** busque el **recurso fitbox** y arrástrelo a la raíz de **la jerarquía**.
9. Seleccione **fitbox en** el panel **Jerarquía.**
10. Arrastre la **colección AstroMan** desde **la jerarquía hasta** la propiedad Colección de **hologramas** de Fitbox en el **panel** Inspector.

### <a name="save-the-project"></a>Guardar el proyecto

1. Guarde la nueva escena: **Archivo > Guardar escena como**.
2. Haga clic **en Nueva carpeta** y asigne a la carpeta el nombre **Scenes**.
3. Asigne al archivo el nombre **"ModelExplorer"** y guárdelo en la **carpeta Scenes.**

### <a name="build-the-project"></a>Compilar el proyecto

1. En Unity, seleccione **File > Build Configuración**.
2. Haga **clic en Agregar escenas abiertas** para agregar la escena.
3. Seleccione **Universal Windows Platform en** la lista **Plataforma** y haga clic en **Cambiar plataforma.**
4. Si está desarrollando específicamente para HoloLens, establezca **Dispositivo de** destino en **HoloLens**. De lo contrario, déjelo en **Cualquier dispositivo.**
5. Asegúrese **de que Tipo** de compilación está establecido en **D3D** y **sdk** está establecido en Instalado más reciente **(que** debe ser SDK 16299 o posterior).
6. Haga clic en **Generar**.
7. Cree una **nueva carpeta** denominada "App".
8. Haga clic en la **carpeta Aplicación.**
9. Presione **Seleccionar carpeta.**

Cuando unity haya terminado, aparecerá Explorador de archivos ventana.

1. Abra la **carpeta** Aplicación.
2. Abra la **solución ModelExplorer Visual Studio .**

Si se implementa en HoloLens:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x86.**
2. Haga clic en la flecha desplegable situada junto al botón Equipo local y seleccione **Equipo remoto.**
3. Escriba **la HoloLens IP del dispositivo y** establezca Modo de autenticación en Universal **(protocolo sin cifrar).** Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en Configuración > **Network & Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin** depurar o presione Ctrl + **F5**. Si es la primera vez que se implementa en el dispositivo, deberá emparejar [con Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Cuando la aplicación se haya implementado, descarte **fitbox** con un **gesto select**.

Si se implementa en un casco envolvente:

1. Con la barra de herramientas superior Visual Studio, cambie el destino de Depurar a **Versión** y de ARM a **x64.**
2. Asegúrese de que el destino de implementación está establecido en **Máquina local.**
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin** depurar o presione Ctrl + **F5**.
4. Cuando la aplicación se haya implementado, descarte **fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

## <a name="chapter-2---cursor-and-target-feedback"></a>Capítulo 2: Comentarios de cursor y destino

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a>Objetivos

* Comportamiento y diseño visual del cursor.
* Comentarios de cursor basados en mirada.
* Comentarios sobre hologramas basados en mirada.

Vamos a basar nuestro trabajo en algunos principios de diseño de cursor, es decir:

* El cursor siempre está presente.
* No permita que el cursor sea demasiado pequeño o grande.
* Evite la obstruir el contenido.

### <a name="instructions"></a>Instrucciones

1. En la **carpeta HoloToolkit\Input\Prefabs,** busque el **recurso InputManager.**
2. Arrastre y coloque **inputManager** en la **jerarquía**.
3. En la **carpeta HoloToolkit\Input\Prefabs,** busque el **recurso Cursor.**
4. Arrastre y coloque el **cursor** en la **jerarquía**.
5. Seleccione el **objeto InputManager** en **la jerarquía**.
6. Arrastre el objeto **Cursor** desde **la** jerarquía al campo **Cursor de SimpleSinglePointerSelector** de InputManager, en la parte inferior del **inspector**. 

![Configuración del selector de puntero único simple](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a>Compilación e implementación

1. Recompile la aplicación **desde File > Build Configuración**.
2. Abra la **carpeta App**.
3. Abra la **solución ModelExplorer Visual Studio .**
4. Haga **clic en Depurar -> Iniciar sin depurar o** presione Ctrl + **F5**.
5. Observe cómo se dibuja el cursor y cómo cambia su apariencia si está tocándose un holograma.

### <a name="instructions"></a>Instrucciones

1. En el panel **Jerarquía,** expanda el objeto GEO_G Back_Center  ->  ->  AstroMan.
2. Haga doble clic **en Interactible.cs** para abrirlo en Visual Studio.
3. Descomprima las líneas de las devoluciones de llamada **IFocusable.OnFocusEnter()** **e IFocusable.OnFocusExit()** en **Interactible.cs.** El InputManager del Mixed Reality Toolkit llama a estos cuando el foco (ya sea mediante mirada o apuntando el controlador) entra y sale del colisionador de GameObject específico.

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
>Usamos `EnableKeyword` y `DisableKeyword` superiores. Para poder usarlos en su propia aplicación con el sombreador Estándar de Toolkit, deberá seguir las directrices de Unity para acceder a los materiales a través del [script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html). En este caso, ya hemos incluido las tres variantes de [material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) resaltado necesarios en la carpeta Recursos (busque los tres materiales con resaltado en el nombre).

### <a name="build-and-deploy"></a>Compilación e implementación

1. Como antes, compile el proyecto e impleméntese en el HoloLens.
2. Observe lo que sucede cuando la mirada está dirigida a un objeto y cuando no lo está.

## <a name="chapter-3---targeting-techniques"></a>Capítulo 3: Técnicas de destino

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a>Objetivos

* Facilitar el destino de hologramas.
* Estabilizar los movimientos naturales de la cabeza.

### <a name="instructions"></a>Instrucciones

1. En el panel **Jerarquía,** seleccione el **objeto InputManager.**
2. En el **panel Inspector,** busque el script **Gaze Stabilizer (Estabilizador de mirada).** Haga clic en él para abrir Visual Studio, si desea echar un vistazo.
    * Este script recorre en iteración ejemplos de datos de Raycast y ayuda a estabilizar la mirada del usuario para la precisión de destino.
3. En el **inspector**, puede editar el valor **Ejemplos de estabilidad almacenados.** Este valor representa el número de muestras en las que el estabilizador recorre en iteración para calcular el valor estabilizado.

## <a name="chapter-4---directional-indicator"></a>Capítulo 4: Indicador direccional

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a>Objetivos

* Agregue un indicador direccional en el cursor para ayudar a encontrar hologramas.

### <a name="instructions"></a>Instrucciones

Vamos a usar el archivo **DirectionIndicator.cs,** que hará lo siguiente:

1. Muestra el indicador direccional si el usuario no está mirando los hologramas.
2. Oculte el indicador direccional si el usuario está mirando los hologramas.
3. Actualice el indicador direccional para que apunte a los hologramas.

Comencemos.

1. Haga clic en **el objeto AstroMan** en el panel **Jerarquía** y haga clic en **la flecha** para expandirlo.
2. En el panel **Jerarquía,** seleccione el **objeto DirectionalIndicator** en **AstroMan**.
3. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
4. En el menú, escriba en el cuadro de búsqueda **Indicador de dirección**. Seleccione el resultado de la búsqueda.
5. En el panel **Jerarquía,** arrastre y coloque el **objeto Cursor** en la **propiedad Cursor** del **inspector**.
6. En el **panel Project,** en la carpeta **Hologramas,** arrastre y coloque el recurso **DirectionalIndicator** en la propiedad **Indicador** direccional del **inspector**.
7. Compile e implemente la aplicación.
8. Vea cómo el objeto de indicador direccional le ayuda a encontrar al astronauta.

## <a name="chapter-5---billboarding"></a>Capítulo 5: Afición

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a>Objetivos

* Use la tecnología de diseño para que los hologramas siempre se acomenten hacia usted.

Usaremos el archivo **Billboard.cs** para mantener un GameObject orientado de forma que esté orientado al usuario en todo momento.

1. En el panel **Jerarquía,** seleccione el **objeto AstroMan.**
2. En el **panel Inspector,** haga clic en **el botón Agregar** componente.
3. En el menú, escriba en el cuadro de búsqueda **Dedón**. Seleccione el resultado de la búsqueda.
4. En el **inspector,** establezca **eje dinámico** en **Y.**
5. ¡Pruébelo! Compile e implemente la aplicación como antes.
6. Vea cómo se enfrenta el objeto DeÓn, independientemente de cómo cambie el punto de vista.
7. Elimine el script de **AstroMan** por ahora.

## <a name="chapter-6---tag-along"></a>Capítulo 6: Tag-Along

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a>Objetivos

* Use Tag-Along para que nuestros hologramas nos sigan por la sala.

A medida que trabajemos en este problema, nos guiaremos por las siguientes restricciones de diseño:

* El contenido siempre debe estar de un vistazo.
* El contenido no debe estar en el camino.
* El contenido del bloqueo de la cabeza no está disponible.

La solución que se usa aquí es usar un enfoque de "etiqueta".

Un objeto de etiquetas nunca sale completamente de la vista del usuario. Puede pensar que una etiqueta es un objeto asociado a la cabeza del usuario mediante bandas de almohadillas. A medida que el usuario se mueve, el contenido permanecerá de un vistazo sencillo deslizándose hacia el borde de la vista sin salir por completo. Cuando el usuario mira hacia el objeto de etiqueta, se ve de forma más completa.

Vamos a usar el archivo **SimpleTagalong.cs** que:

1. Determine si el objeto Tag-Along está dentro de los límites de la cámara.
2. Si no está dentro del frustum de vista, coloque el Tag-Along parcialmente dentro del frustum de vista.
3. De lo contrario, coloque el Tag-Along a una distancia predeterminada del usuario.

Para ello, primero debemos cambiar el script **Interactible.cs** para llamar a **TagalongAction**.

1. Edite **Interactible.cs** completando el ejercicio de codificación 6.a (descomprimiendo las líneas 84 a 87).

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

El script **InteractibleAction.cs,** emparejado con **Interactible.cs,** realiza acciones personalizadas al pulsar en hologramas. En este caso, usaremos uno específicamente para la etiqueta.

* En la **carpeta Scripts,** haga clic **en el recurso TagalongAction.cs** para abrir en Visual Studio.
* Complete el ejercicio de codificación o cámbielo a lo siguiente:
  * En la parte superior de **la jerarquía**, en la barra de **búsqueda, escriba ChestButton_Center** y seleccione el resultado.
  * En el **panel Inspector,** haga clic en **el botón Agregar** componente.
  * En el menú, escriba en el cuadro de búsqueda **Acción tagalong**. Seleccione el resultado de la búsqueda.
  * En **Hologramas** carpeta, busque el **recurso Tagalong.**
  * Seleccione el **ChestButton_Center** en **hierarchy**. Arrastre y coloque el **objeto TagAlong** desde el **panel Project** el inspector **en** la propiedad Object **To Tagalong** .
  * Arrastre el **objeto Acción tagalong** desde **el inspector** hasta el campo **Acción interactuable** del script **Interactible.**
* Haga doble clic en el script **TagalongAction** para abrirlo en Visual Studio.

![Configuración interactuable](images/holograms210-interactible.png)

Es necesario agregar lo siguiente:

* Agregue funcionalidad a la función PerformAction en el script TagalongAction (heredado de InteractibleAction).
* Agregue la afición al objeto con mirada y establezca el eje de pivote en XY.
* A continuación, agregue Tag-Along al objeto .

Esta es nuestra solución, de **TagalongAction.cs:**

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* ¡Pruébelo! Compile e implemente la aplicación.
* Observe cómo el contenido sigue el centro del punto de mirada, pero no continuamente y sin bloquearlo.