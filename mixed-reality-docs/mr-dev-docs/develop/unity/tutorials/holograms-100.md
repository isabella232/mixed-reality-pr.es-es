---
title: 'Aspectos básicos de HoloLens de primera generación (100): introducción a Unity'
description: Aprenda a crear su primera aplicación básica de realidad mixta "hola mundo" para HoloLens y Windows Mixed Reality dispositivos.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality, Windows Mixed Reality, HoloLens, immersive, vr, mr, get started, hologram, academy, tutorial, Mixed Reality Academy, unity, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 518be5642304b6307f0b26f30f37315eba4164448493d928f6effb3027f7d611
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196514"
---
# <a name="hololens-1st-gen-basics-100-getting-started-with-unity"></a>HoloLens (1.ª generación) Conceptos básicos 100: Introducción a Unity

>[!IMPORTANT]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (1ª generación), Unity 2017 y Mixed Reality cascos envolventes en mente.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos. Estos tutoriales no **_se actualizarán_** con los conjuntos de herramientas o interacciones más recientes que se usan para HoloLens 2 y es posible que no sean compatibles con las versiones más recientes de Unity.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

Este tutorial le ayudará a crear una aplicación de realidad mixta básica creada con Unity.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Aspectos básicos de realidad mixta (100): Introducción a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

* Un Windows 10 configurado con las [herramientas correctas instaladas.](../../install-the-tools.md)

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1: Crear un nuevo Project

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para compilar una aplicación con Unity, primero debe crear un proyecto. Este proyecto se organiza en algunas carpetas, la más importante de las cuales es la carpeta Assets. Se trata de la carpeta que contiene todos los recursos que importa desde herramientas de creación de contenido digital como Maya, MaxIsmo 4D o Photoshop, todo el código que cree con Visual Studio o su editor de código favorito, y cualquier número de archivos de contenido que Unity cree a medida que crea escenas, animaciones y otros tipos de recursos de Unity en el editor.

Para compilar e implementar aplicaciones para UWP, Unity puede exportar el proyecto como una solución Visual Studio que contendrá todos los archivos de código y recursos necesarios.

1. Inicio de Unity
2. Seleccione **Nuevo paso**.
3. Escriba un nombre de proyecto (por ejemplo, "MixedRealityIntroduction")
4. Escriba una ubicación para guardar el proyecto.
5. Asegúrese de que está seleccionado el botón de alternancia **3D.**
6. Seleccione **Crear proyecto.**

Gracias, ya está todo configurado para empezar a trabajar con las personalizaciones de realidad mixta.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2: Configuración de la cámara

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La cámara principal de Unity controla el seguimiento de la cabeza y la representación estereomática. Hay algunos cambios que se deben realizar en la cámara principal para usarla con realidad mixta.

1. Selección del archivo > nueva escena

En primer lugar, será más fácil crear la aplicación si se imagine la posición inicial del usuario como (**X**: 0, **Y**: 0, **Z**: 0). Puesto que la cámara principal está haciendo un seguimiento del movimiento de la cabeza del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.

1. Seleccione **Cámara principal** en el panel **Jerarquía.**
2. En el panel **Inspector,** busque el  componente **Transformar** y cambie la posición de (**X**: 0, **Y**: 1, **Z**: -10) a (**X**: 0, **Y**: 0, **Z**: 0)

En segundo lugar, el fondo predeterminado de la cámara necesita algo de reflexión.

**Para HoloLens aplicaciones**, el mundo real debe aparecer detrás de todo lo que representa la cámara, no una textura de Skybox.

1. Con la cámara **principal** aún seleccionada en  el **panel** Jerarquía, busque  el componente Cámara en el **panel Inspector** y cambie la lista desplegable Borrar marcas de **Skybox** a **Color sólido.**
2. Seleccione el **selector** color de fondo y cambie los **valores RGBA** a (0, 0, 0, 0)

En el caso de las aplicaciones de realidad mixta destinadas a **cascos envolventes,** podemos usar la textura de Skybox predeterminada que proporciona Unity.

1. Con la cámara **principal** aún seleccionada en el **panel** Jerarquía, busque  el componente **Cámara** en el **panel Inspector** y mantenga la lista desplegable Borrar marcas en **Skybox.**

En tercer lugar, veamos el plano de recorte cercano en Unity y evitaremos que los objetos se represente demasiado cerca de los ojos de los usuarios a medida que un usuario se aproxima a un objeto o a un objeto que se aproxima a un usuario.

**Para HoloLens aplicaciones**, el plano de recorte cercano se puede establecer en el HoloLens recomendado de 0,85 metros. [](../camera-in-unity.md#using-clipping-planes)

1. Con la **cámara** principal aún seleccionada en  el **panel** Jerarquía, busque el componente Cámara en el **panel Inspector** y cambie el campo **Plano** de recorte cercano del valor predeterminado **0.3** al HoloLens **recomendado 0.85.**

En el caso de las aplicaciones de realidad mixta destinadas a **cascos envolventes,** podemos usar la configuración predeterminada que proporciona Unity.

1. Con la cámara **principal** aún seleccionada en  el **panel** Jerarquía, busque el componente Cámara en el **panel Inspector** y mantenga el campo **Plano** de recorte cercano en el valor **predeterminado 0.3.**

Por último, vamos a guardar nuestro progreso hasta ahora. Para guardar los cambios de la escena, seleccione **Archivo > Guardar** escena como , asigne a la escena el nombre **Main** y seleccione **Guardar.**

## <a name="chapter-3---setup-the-project-settings"></a>Capítulo 3: Configuración del Project Configuración

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

En este capítulo, estableceremos algunas opciones de configuración del proyecto de Unity que nos ayudarán a dirigirnos al SDK Windows Holographic para el desarrollo. También estableceremos algunos valores de calidad para nuestra aplicación. Por último, nos aseguraremos de que nuestros destinos de compilación estén establecidos en Universal Windows Platform.

### <a name="unity-performance-and-quality-settings"></a>Configuración de rendimiento y calidad de Unity

**Configuración de calidad de Unity para HoloLens**

![Configuración de calidad de Unity para HoloLens](images/qualitysettings.png)

Puesto que mantener una velocidad de fotogramas alta HoloLens es tan importante, queremos que la configuración de calidad se ajuste para obtener un rendimiento más rápido. Para obtener información de rendimiento más detallada, consulte [Recomendaciones de rendimiento para Unity.](../performance-recommendations-for-unity.md)

1. Seleccione **Editar > Project Configuración > calidad**
2. Seleccione la **lista desplegable** bajo el logotipo **Windows plataforma** universal y seleccione **Muy bajo.** Sabrá que la configuración se ha aplicado correctamente cuando el cuadro de la columna Universal Windows Platform (Plataforma universal de Windows) y la fila **Very Low** (Muy baja) estén en color verde.

**En el caso de las aplicaciones de realidad mixta** destinadas a pantallas oclusadas, puede dejar la configuración de calidad en sus valores predeterminados.

### <a name="target-windows-10-sdk"></a>SDK de Windows 10 destino

**SDK Windows Holographic**

![SDK Windows Holographic](../images/xrsettings.png)

Necesitamos que Unity sepa que la aplicación que estamos intentando exportar debe crear una vista [envolvente](../../../design/app-views.md) en lugar de una vista 2D. Para ello, habilitamos la compatibilidad con virtual Reality en Unity para el SDK de Windows 10.

1. Vaya a **Editar > Project Configuración > Player**.
2. En el **panel Inspector para** player Configuración, seleccione el icono Universal Windows Platform **(Plataforma** universal).
3. Expanda el grupo **XR Settings** (Configuración de XR).
4. En la sección **Rendering** (Representación), active la casilla **Virtual Reality Supported** (Se admite Virtual Reality) para agregar una nueva lista de **SDK de Virtual Reality**.
5. Compruebe que **Windows Mixed Reality** (Mixed Reality de Windows) aparece en la lista. En caso contrario, seleccione el botón **+** situado en la parte inferior de la lista y elija **Windows Mixed Reality** (Mixed Reality de Windows).

>[!NOTE]
>Si no ve el icono Plataforma Windows universal, compruebe de nuevo que ha seleccionado **Compatibilidad** con la compilación de la plataforma Windows universal durante la instalación. Si no, es posible que deba volver a instalar Unity con la instalación correcta de Windows.

Trabajo impresionante al aplicar toda la configuración del proyecto. A continuación, vamos a agregar un holograma.

## <a name="chapter-4---create-a-cube"></a>Capítulo 4: Creación de un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Crear un cubo en el proyecto de Unity es igual que crear cualquier otro objeto en Unity. Colocar un cubo delante del usuario es fácil porque el sistema de coordenadas de Unity está asignado al mundo real, donde un medidor de Unity es aproximadamente un medidor en el mundo real.

1. En la esquina superior izquierda del  panel **Jerarquía,** seleccione la lista desplegable Crear y elija **Objeto 3D > Cubo.**
2. Seleccione el cubo recién **creado en** el panel **Jerarquía.**
3. En el **inspector,** busque el **componente Transformar** y cambie **Posición** a (**X**: 0, **Y**: 0, **Z**: 2). *Esto coloca el cubo 2 metros delante de la posición inicial del usuario.*
4. En  el componente  Transformar, cambie Rotación a (**X**: 45, **Y**: 45, **Z**: 45) y cambie Escala **a** (**X**: 0,25, **Y**: 0,25, **Z**: 0,25). *Esto escala el cubo a 0,25 metros.*
5. Para guardar los cambios de la escena, **seleccione Archivo > Guardar escena.**

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5: Comprobación en el dispositivo desde el editor de Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Ahora que hemos creado el cubo, es el momento de realizar una comprobación rápida del dispositivo. Puede hacerlo directamente desde el editor de Unity.

### <a name="initial-setup"></a>Configuración inicial

1. En el equipo de desarrollo, en Unity, abra archivo > **ventana Configuración** compilación.
2. Cambie **Plataforma a** Plataforma universal Windows **y** haga clic en **Cambiar plataforma**

### <a name="for-hololens-use-unity-remoting"></a>Para HoloLens uso de la comunicación remota de Unity

1. En el HoloLens, instale y ejecute [holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md), disponible en Windows Store. Inicie la aplicación en el dispositivo y especificará un estado de espera y mostrará la dirección IP del dispositivo. Anote la dirección IP.
2. Abra **Ventana > XR > emulación holográfica**.
3. Cambie **el modo de emulación** de **Ninguno** a Remoto **a Dispositivo**.
4. En **Equipo remoto,** escriba la dirección IP de la HoloLens anotó anteriormente.
5. Haga clic en **Conectar**.
6. Asegúrese de que **el estado de la** conexión cambia a verde **Conectado.**
7. Ahora puede hacer clic en **Reproducir en** el editor de Unity.

Ahora podrá ver el cubo en el dispositivo y en el editor. Puede pausar, inspeccionar objetos y depurar igual que está ejecutando una aplicación en el editor, porque eso es básicamente lo que sucede, pero con entrada de vídeo, audio y dispositivo transmitidos de un lado a otro a través de la red entre el equipo host y el dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para otros cascos compatibles con la realidad mixta

1. Conectar el casco al equipo de desarrollo mediante el cable USB y el cable hdmi o de puerto de pantalla.
2. Inicie el **Portal de realidad mixta** y asegúrese de que ha completado la primera experiencia de ejecución.
3. Desde Unity, ahora puede presionar el botón Reproducir.

Ahora podrá ver la representación del cubo en el casco de realidad mixta y en el editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6: Compilación e implementación en el dispositivo desde Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Ahora estamos listos para compilar el proyecto para Visual Studio e implementar en el dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportación a la solución Visual Studio personalizada

1. Abra **la ventana > compilar Configuración** archivo.
1. Haga **clic en Agregar escenas abiertas** para agregar la escena.
1. Cambie **Plataforma a** Plataforma Windows **y** haga clic en **Cambiar plataforma.**
1. En **La configuración Windows plataforma** universal, asegúrese de que el **SDK** es **Universal 10.**
1. En Dispositivo de destino, vaya **a Cualquier dispositivo para** las pantallas ocluida o cambie a **HoloLens**.
1. **El tipo de compilación de UWP** debe **ser D3D.**
1. **El SDK de UWP** se puede dejar en **La versión más reciente instalada.**
1. Haga clic en **Generar**.
1. En el explorador de archivos, haga clic **en Nueva carpeta y** asigne a la carpeta el nombre **"App".**
1. Con la **carpeta Aplicación** seleccionada, haga clic en el **botón Seleccionar** carpeta.
1. Cuando Unity termine de compilarse, aparecerá Windows Explorador de archivos ventana.
1. Abra la carpeta **Aplicación** en el Explorador de archivos.
1. Abra la solución Visual Studio generada (MixedRealityIntroduction.sln en este ejemplo)

### <a name="compile-the-visual-studio-solution"></a>Compilación de Visual Studio solución

Por último, compilaremos la solución Visual Studio exportada, la implementaremos y la probaremos en el dispositivo.

1. Con la barra de herramientas superior Visual Studio, cambie el destino de **Depurar** a **Versión** y de **ARM** a **X86.**

Las instrucciones difieren para la implementación en un dispositivo frente al emulador. Siga las instrucciones que coincidan con la configuración.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implementación en un dispositivo de realidad mixta a través de Wi-Fi

1. Haga clic en la flecha situada junto al **botón Máquina local** y cambie el destino de implementación a Máquina **remota.**
2. Escriba la dirección IP del dispositivo de  realidad mixta y cambie Modo de autenticación a Universal (protocolo sin cifrar) para HoloLens y **Windows** para otros dispositivos.
3. Haga **clic en Depurar > iniciar sin depurar**.

**Por HoloLens**, si es la primera vez que se implementa en el dispositivo, deberá emparejar [mediante Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implementación en un dispositivo de realidad mixta a través de USB

Asegúrese de que el dispositivo está conectado a través del cable USB.

1. **Para HoloLens**, haga clic en la flecha situada junto al botón **Máquina local** y cambie el destino de implementación a **Dispositivo**.
2. **Para dirigirse a dispositivos ocluido conectados al equipo,** mantenga la configuración en Máquina local. Asegúrese de que tiene el **Portal de realidad mixta** en ejecución.
3. Haga **clic en Depurar > iniciar sin depurar**.

### <a name="deploy-to-emulator"></a>Implementación en Emulator

1. Haga clic en la flecha situada junto al **botón Dispositivo** y, en la lista **desplegable, seleccione HoloLens Emulator**.
2. Haga **clic en Depurar > iniciar sin depurar**.

### <a name="try-out-your-app"></a>Prueba de la aplicación

Ahora que la aplicación está implementada, intente desplazarse por todo el cubo y observe que permanece en el mundo delante de usted.

## <a name="see-also"></a>Consulte también

* [Introducción al desarrollo de Unity](../unity-development-overview.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](../best-practices-for-working-with-unity-and-visual-studio.md)
* [Aspectos básicos de realidad mixta (101)](holograms-101.md)
* [Aspectos básicos de realidad mixta (101E)](holograms-101e.md)