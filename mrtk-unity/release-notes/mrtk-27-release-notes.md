---
title: Notas de la versión de MRTK 2.7
description: Notas de la versión de MRTK 2.7
author: RogPodge
ms.author: roliu
ms.date: 06/16/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, XRSDK, XR heredado, Leap Motion, Ultraleap, OpenXR
ms.localizationpriority: high
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 921cdb4d9643e55841bc7c979066c276f5fd80998ad97d19332c528cebe05c37
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203530"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notas de la versión de Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-272"></a>Novedades de la versión 2.7.2

### <a name="fixed-a-upm-package-dependency-issue"></a>Se corrigió un problema de dependencia del paquete UPM.

Hay un problema con los paquetes UPM de MRTK 2.7.1 en el que las dependencias no se configuraron correctamente. El problema provocó que la característica de Mixed Reality no importara correctamente los paquetes de MRTK 2.7.1. Ahora se ha resuelto en la versión 2.7.2. No hay ningún cambio de código en esta versión en comparación con la 2.7.1.


## <a name="whats-new-in-271"></a>Novedades de la versión 2.7.1

### <a name="show-version"></a>Mostrar versión

El menú `Mixed Reality` > `Toolkit` ahora contiene una entrada `Show version...` que examina el paquete de Mixed Reality Toolkit Foundation para determinar la versión de MRTK que utiliza el proyecto.

![Menú Mostrar versión](images/ShowVersionMenu.png)

![Cuadro de diálogo de la versión de MRTK](images/VersionDialog.png)

> [!NOTE]
> Si MRTK se clonó desde el [repositorio de GitHub](https://aka.ms/mrtk), no se habrá establecido la información de la versión.
>
> ![No se puede determinar la versión.](images/CannotDetermineVersion.png)

### <a name="authors-list"></a>Lista de autores

A partir de la versión 2.7.1 de MRTK, el archivo de la lista de autores se incluirá en el paquete Mixed Reality Toolkit Foundation.

### <a name="integrated-openxr-project-setup-into-the-configurator-setup-flow"></a>Configuración integrada del proyecto OpenXR en el flujo de configuración del configurador

A partir de la versión 2.7.1 de MRTK, los usuarios del complemento OpenXR de Mixed Reality recibirán instrucciones sobre cómo configurar dicho complemento con MRTK. Hay una opción para que los usuarios que tienen como destino HoloLens 2 apliquen automáticamente la configuración recomendada.

![Ventana del configurador con instrucciones de configuración de OpenXR](images/configuratorMROpenXR.png)

### <a name="notable-bugfixes-and-changes"></a>Correcciones de errores y cambios importantes

- El administrador de joystick de Unity se ha marcado como compatible con la canalización del SDK de XR. [#9954](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9954), [#9994](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9994)
- Se agregaron comprobaciones al código de inspector interactuable para evitar errores nulos. [ #9943](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9943)
- Se agregó el proveedor de malla OpenXR para la escena de ejemplo de sombreador de pulsos. [#9902](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9902)
- Se restauró el perfil de física de manos para la escena de ejemplo. [#9915](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9915)
- Se completó una limpieza en los scripts HandConstraint*. [#9935](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9935)
- Se corrigieron algunos errores que afectan a la creación y clonación de perfiles. [#9982](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9982)


## <a name="whats-new-in-270"></a>Novedades de la versión 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR ahora se admite oficialmente en MRTK.

Como parte del proceso de consolidación de los nuevos complementos de OpenXR, ahora MRTK admite oficialmente OpenXR. En comparación con las versiones anteriores, agregamos las siguientes funcionalidades a los proyectos mediante OpenXR:

- [Compatibilidad con el modelo de controlador de movimiento proporcionado por el sistema](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Compatibilidad con gestos de WinMR (selección, mantener presionado, manipulación y navegación) [#9843](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843)
- [Compatibilidad con los hápticos del controlador](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Compatibilidad con la malla de mano articulada en HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Compatibilidad con la asignación espacial en HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Compatibilidad con la descripción de escenas en HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

Si tiene como destino los cascos de HoloLens 2 o Windows Mixed Reality mediante OpenXR, asegúrese de instalar o actualizar el **complemento de OpenXR de Mixed Reality a la versión 0.9.5 o posterior** mediante la [herramienta de características de Mixed Reality](https://aka.ms/MRFeatureTool); de lo contrario, es posible que pierda algunas de las mejoras anteriores.

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Los proveedores de datos del SDK de XR y XR heredado ahora se pueden usar en el mismo perfil.

Además, ahora, los proveedores de datos solo se cargarán cuando se seleccione la canalización adecuada, lo que permite que los proveedores de datos del SDK de XR y XR heredado coexistan en el mismo perfil. Para ajustarse a este cambio, los proveedores de datos del SDK de XR y XR heredado ahora se organizan en pestañas diferentes dentro de la vista de perfil, lo que ayuda a los usuarios a determinar si tienen el perfil correcto para su canalización de XR de destino.

![Los proveedores de datos del SDK de XR y XR heredado ahora se pueden unificar en un único perfil.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Para ajustarse a este cambio, los proveedores de datos nulos ya no se cargarán ni se mostrarán en el inspector de perfil. Los usuarios pueden alternar `Show null data providers in the profile inspector` en **Editar -> Configuración del proyecto -> Mixed Reality Toolkit** para depurar comportamientos inesperados con proveedores de datos que faltan.

![Los proveedores de datos nulos ahora están ocultos de forma predeterminada ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
![ Alterne la opción Show null data providers in the profile inspector](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png) (Mostrar proveedores de datos NULL en el inspector de perfiles).

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Se ha agregado la configuración de experiencia y un comportamiento asociado del contenido de la escena de Mixed Reality

Los usuarios ahora pueden establecer la [configuración de la experiencia](../features/experience-settings/experience-settings.md), lo que permitirá que MRTK muestre el [contenido de la escena de Mixed Reality](../features/experience-settings/scene-content.md) correctamente en función de la experiencia de destino.

Si la configuración anterior de la escala de experiencia del usuario no coincide con el nuevo perfil de configuración de la experiencia, se le pedirá que la corrija en el inspector.

![Migración de la escala de experiencia](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>El configurador rediseñado ahora guía al usuario a través del proceso de configuración.

El nuevo configurador de MRTK proporciona a los usuarios instrucciones paso a paso para configurar correctamente el proyecto para el desarrollo de XR y su uso con MRTK. Incluye la selección de la canalización de XR, la obtención de los complementos específicos de la plataforma, la importación de TextMesh Pro, la visualización de los ejemplos (al usar UPM) y otras configuraciones recomendadas previamente incluidas para el proyecto.

![Configurador que muestra la lista de canalizaciones](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Punto de acceso de teletransporte graduado

Se ha graduado un nuevo [componente de punto de acceso de teletransporte](../features/teleport-system/teleport-hotspot.md). Puede agregar un punto de acceso de teletransporte a GameObject para asegurarse de que el usuario está en una determinada posición y orientación cuando se teletransporta a esa ubicación.

![Ejemplo de un punto de acceso de teletransporte](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Permanencia graduada

El ejemplo y la característica de permanencia ahora han pasado de ser experimentales a graduados. En la escena de ejemplo se incluyen nuevos ejemplos de botones de estilo de HoloLens 2 volumétricos.

![Elemento principal de permanencia](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Se agregó compatibilidad con los módulos de Unity de Leap Motion de las versiones 4.6.0, 4.7.0, 4.7.1 y 4.8.0.

Las versiones más recientes de los [módulos de Unity de Leap Motion](https://developer.leapmotion.com/unity) ahora son compatibles con MRTK 2.7.0. Consulte [Cómo configurar MRTK para Leap Motion](../supported-devices/leap-motion-mrtk.md) para obtener más información.

Muchas gracias a @jackyangzzh por contribuir en la nueva escena LeapMotionOrientationExample.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Los eventos de voz dirigidos ya no están restringidos a los punteros de mirada

Anteriormente, los eventos de voz dirigidos solo podían generarse en objetos que tenían el foco del puntero de mirada. Ahora, los objetos pueden recibir eventos de voz si reciben el foco de cualquier puntero.

![Eventos de voz con punteros lejanos](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>TextToSpeech portado de HTK a MRTK

El apreciado script TextToSpeech ya está disponible en MRTK para ayudarle a generar voz a partir de texto en la plataforma UWP mediante [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . También se ha agregado una escena de ejemplo para mostrar la característica.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Compatibilidad con el modelo de controlador de movimiento proporcionado por el sistema en OpenXR

Se agregó compatibilidad, tanto en el editor como en tiempo de ejecución, con el modelo de controlador de movimiento proporcionado por el sistema en OpenXR.

![Ventana del editor que muestra dos modelos de controlador de movimiento](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Compatibilidad con la malla de mano articulada de HoloLens 2 en OpenXR

![Malla de mano que se ejecuta en el dispositivo en una escena de ejemplo de MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Compatibilidad con los hápticos de controlador en WMR heredado, el complemento XR de Windows y OpenXR

Se agregó compatibilidad con los hápticos de controlador en WMR heredado, el complemento XR de Windows y OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Compatibilidad con el seguimiento de los ojos en el complemento XR de Windows

Se agregó compatibilidad con el seguimiento de los ojos para las versiones mínimas del complemento XR de Windows 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) y 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Correcciones de errores y cambios importantes

- La detección de la acción de reducir se ha mejorado. Ahora es más difícil anular accidentalmente el gesto de acercar. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Ahora, los objetos con el componente Manipulador de objetos mantienen la velocidad de forma coherente en la versión cuando se establece la marca. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Ahora, el desplazamiento hacia atrás comprueba si hay algún suelo, lo que ayuda a evitar situaciones en las que la cámara grabe el entorno o en las que el usuario quede flotando en un espacio vacío. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject ahora es una propiedad virtual, lo que proporciona más flexibilidad al extender la esfera o el puntero de toque. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- En los botones ahora aparece la palabra clave adecuada al mostrar el comando de voz disponible. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Los controladores de Oculus ahora usan su propio visualizador independiente, lo que impide que la visualización de MRTK entre en conflicto con la visualización del paquete de integración de Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Los scripts relacionados con el teclado se han cambiado para ajustarse al comportamiento de las versiones más recientes de Unity (2019.4.25 y posteriores y 2020.3.2 y posteriores). A partir de la versión, todavía hay un error de finalización automática y un error de campo de entrada de TMP (ambos son externos a MRTK) que afecta a HoloLens. Para obtener más información, consulte [#9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) y [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Se ha mejorado el rendimiento de la colección de objetos de desplazamiento. También se ha corregido un problema que provocaba que GameObject de la colección perdiera material cuando se duplicaba. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- En el script de demostración de descripción de escenas, se ha agregado la función `GetSceneObjectsOfType` para recuperar todo el objeto de escena observado de un tipo determinado. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- En la herramienta de compilación de línea de comandos, solo se incluirán las escenas especificadas por las marcas `sceneList` o `sceneListFile` (cuando haya alguna marca) en la compilación. [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- En la herramienta de compilación, hay una nueva opción para especificar una ruta de acceso a `nuget.exe` y usarla para realizar la restauración de paquetes en lugar de usar `msbuild` (la opción predeterminada). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Se corrigió un problema por el que el uso del complemento XR de Windows podía dar lugar a uniones de mano obsoletas y mallas de mano dobles. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Se corrigió un problema en el que, al usar la característica de comunicación remota automática del complemento XR de Windows, faltaban entradas e interacciones. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Se corrigió un problema en el que BuildDeployWindow intentaba consultar una clave del Registro no válida para la ruta de acceso de Windows SDK. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Los importadores glTF de MRTK ahora son opcionales. Si hay varios importadores glTF, los de MRTK se pueden deshabilitar al agregar `MRTK_GLTF_IMPORTER_OFF` a los símbolos de definición de scripting personalizados. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Se corrigió un problema en el que los controladores de Knuckles en OpenVR no se detectaban correctamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Se redujo el número de asignaciones por fotograma al visualizar la malla de mano. [#9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Se agregó un elemento de menú para iniciar el paquete de ejemplos de MRTK (en el administrador de paquetes de Unity) para facilitar la importación de ejemplos. [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Se redujo el número de advertencias de tiempo de carga al usar Unity 2020.3.
- Se agregó la documentación de la característica de la ventana de compilación: [visite la página](../features/tools/build-window.md)

## <a name="known-issues"></a>Problemas conocidos

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>Falta un archivo asmdef (paquete UPM) en las demostraciones de audio.

Al importar MRTK a través de la herramienta de características de Mixed Reality, se agregan ejemplos y demostraciones al proyecto mediante la interfaz de usuario del administrador de paquetes de Unity. Después de importar las demostraciones de audio, la escena `WindowsMicrophoneStreamDemo.unity` no se comportará correctamente. Esto se debe a que falta un archivo .asmdef para el ejemplo.

Para evitar este [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908), realice los pasos siguientes:

- Copie la carpeta Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...]/MRTK.Examples.asmdef into your "Assets/Samples/Mixed Reality Toolkit Examples".
- Cambie el nombre del archivo copiado a Examples.
- Abra el archivo Examples.
- En el cuadro Nombre, reemplace el contenido por Examples.
- Haga clic en Aplicar.
- Compilación e implementación

Este problema se corregirá en una versión futura de Visual Studio 2017.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La ventana de compilación de MRTK desencadena el cuadro de diálogo "Importación de recursos" indefinido en Unity 2020.3.

Hay un [problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) conocido con la ventana de compilación de MRTK en Unity 2020.3 en el que, después de realizar correctamente una compilación de UWP, el cuadro de diálogo "Importar recursos" no se completa. Este problema se está investigando con la colaboración de Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Advertencias del representador de lienzo de TextMesh Pro en Unity 2020

La advertencia siguiente se registra en la mayoría de las escenas de ejemplo de MRTK mientras se usa Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

La advertencia de lienzo se agregó en [la versión 3.0.3 de TextMesh Pro](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3). Estas advertencias no afectan a las escenas de ejemplo de MRTK y se pueden borrar desde la consola. Consulte el [problema 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) para obtener más detalles.