---
title: Notas de la versión de MRTK 2.7
description: Notas de la versión 2.7 de MRTK
author: RogPodge
ms.author: roliu
ms.date: 05/27/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, XRSDK, XR heredado, Leap Motion, Ultraleap
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 92c8705c70a2a6c1e25f1ed6b1f87eac1e5726e0
ms.sourcegitcommit: 11d5d7c3fdd59c1ebcfca34dbb6d84c05b481e5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/10/2021
ms.locfileid: "111897408"
---
# <a name="microsoft-mixed-reality-toolkit-27-release-notes"></a>Notas de la versión de Microsoft Mixed Reality Toolkit 2.7

## <a name="whats-new-in-270"></a>Novedades de la versión 2.7.0

### <a name="openxr-is-now-officially-supported-in-mrtk"></a>OpenXR ahora se admite oficialmente en MRTK

A medida que los nuevos complementos de OpenXR se están volviendo cada vez más maduros, MRTK ahora admite oficialmente OpenXR. En comparación con las versiones anteriores, agregamos las siguientes funcionalidades a los proyectos mediante OpenXR:

- [Compatibilidad con el modelo de controlador de movimiento proporcionado por el sistema](#support-for-the-system-provided-motion-controller-model-on-openxr)
- Compatibilidad con gestos de WinMR (selección, retención, manipulación y [navegación)](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9843) #9843
- [Compatibilidad con los hápticos del controlador](#support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr)
- [Compatibilidad con malla de mano articulada en HoloLens 2](#support-for-hololens-2-articulated-hand-mesh-on-openxr)
- Compatibilidad con la asignación espacial en HoloLens 2 [#9567](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9567), [#9827](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9827)
- Compatibilidad con Scene Understanding en HoloLens 2 [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)

### <a name="legacy-xr-and-xr-sdk-data-providers-can-now-be-used-within-the-same-profile"></a>Los proveedores de datos del SDK de XR y XR heredados ahora se pueden usar en el mismo perfil.

Ahora, los proveedores de datos solo se cargarán cuando se seleccione la canalización adecuada, lo que permite que los proveedores de datos heredados de XR y del SDK de XR coexistan en el mismo perfil. Para dar cabida a esto, los proveedores de datos del SDK de XR y XR heredados ahora se organizan en pestañas diferentes dentro de la vista de perfil, lo que ayuda a los usuarios a determinar si tienen el perfil correcto para su canalización de XR de destino.

![Los proveedores de datos heredados y del SDK de XR ahora se pueden unificados en un único perfil.](../features/images/xrsdk/LegacyAndXrsdkUnified.png)

Para dar cabida a esto, los proveedores de datos null ya no se cargarán y se mostrarán en el inspector de perfil. Los usuarios pueden alternar en Editar -> configuración del proyecto -> Mixed Reality Toolkit para depurar `Show null data providers in the profile inspector` comportamientos inesperados con proveedores de datos que faltan. 

![Los proveedores de datos NULL ahora están ocultos de forma predeterminada ](https://user-images.githubusercontent.com/39840334/115093658-ead24600-9ecf-11eb-91c2-486a37f69aba.png)
 ![ Toggle show null data providers in the profile inspector (Alternar mostrar proveedores de datos NULL en el inspector de perfiles)](https://user-images.githubusercontent.com/39840334/115093670-f6257180-9ecf-11eb-96ec-ffe44a225a55.png)

### <a name="added-experience-settings-and-an-associated-mixed-reality-scene-content-behavior"></a>Se ha agregado configuración de experiencia y un comportamiento asociado Mixed Reality contenido de la escena

Los usuarios ahora pueden configurar [la configuración](../features/experience-settings/experience-settings.md)de la experiencia , lo que permitirá que MRTK muestre el [Mixed Reality de](../features/experience-settings/scene-content.md) la escena correctamente en función de la experiencia de destino.

Si la configuración anterior de Escala de experiencia del usuario no coincide con el nuevo perfil de configuración de experiencia, se le pedirá que corrija en el inspector.

![Migración de escala de experiencia](https://user-images.githubusercontent.com/39840334/114946863-d70bde80-9e00-11eb-9859-fa40d40d2b36.gif)

### <a name="the-redesigned-configurator-now-guides-the-user-through-the-setup-process"></a>El configurador rediseñado ahora guía al usuario a través del proceso de configuración.

El nuevo configurador de MRTK proporciona a los usuarios instrucciones paso a paso para configurar correctamente el proyecto para el desarrollo de XR y usarlo con MRTK. Trata la selección de la canalización de XR, la obtención de los complementos específicos de la plataforma, la importación de TextMeshPro, la visualización de los ejemplos (al usar UPM) y otras configuraciones recomendadas previamente incluidas para el proyecto.

![Configurador que muestra la lista de canalizaciones](images/Configurator.png)

### <a name="graduated-teleport-hotspot"></a>Zona de teleportada graduada

Se ha titulado un nuevo [componente de punto](../features/teleport-system/teleport-hotspot.md) de acceso de teleport. Puede agregar un punto de acceso de teleport a GameObject para asegurarse de que el usuario está en una determinada posición y orientación cuando se teletransporta a esa ubicación.

![Ejemplo de punto de acceso de teleport](images/TeleportHotspot.gif)

### <a name="graduated-dwell"></a>Permanencia graduada

La característica de permanencia y el ejemplo ahora se han pasado de ser experimentales. En la escena de ejemplo se incluyen nuevos ejemplos de botones HoloLens 2 estilo volumétricos.

![Héroe de permanencia](../features/images/dwell/MRTK_UX_Dwell.png)

### <a name="added-support-for-leap-motion-unity-modules-version-460-470-471-and-480"></a>Se ha agregado compatibilidad con los módulos de Unity Leap Motion, versiones 4.6.0, 4.7.0, 4.7.1 y 4.8.0.

La compatibilidad con las versiones más recientes de los módulos [de Unity leap motion](https://developer.leapmotion.com/unity) ahora es compatible con MRTK 2.7.0.  Consulte [How to Configure MRTK for Leap Motion (Configuración de MRTK para Leap Motion)](../supported-devices/leap-motion-mrtk.md) para obtener más información.

Gracias por contribuir @jackyangzzh a la nueva escena LeapMotionOrientationExample.

### <a name="targeted-speech-events-raised-no-longer-restricted-to-gaze-pointers"></a>Los eventos de voz dirigidos ya no están restringidos a los punteros de mirada

Anteriormente, los eventos de voz dirigidos solo podían generarse en objetos que se centraban en con el puntero de mirada. Ahora, los objetos pueden recibir eventos de voz si se centran en cualquier puntero.

![Eventos de voz con punteros lejanos](https://user-images.githubusercontent.com/39840334/117516612-6fa00500-af4e-11eb-94ba-d5fb2ed4e7de.gif)

### <a name="ported-texttospeech-from-htk-to-mrtk"></a>Texto portadoToSpeech de HTK a MRTK

El gran script TextToSpeech ya está disponible en MRTK para ayudarle a generar voz a partir de texto en la plataforma UWP mediante [`SpeechSynthesizer`](/uwp/api/windows.media.speechsynthesis.speechsynthesizer) . También se ha agregado una escena de ejemplo para mostrar la característica.

### <a name="support-for-the-system-provided-motion-controller-model-on-openxr"></a>Compatibilidad con el modelo de controlador de movimiento proporcionado por el sistema en OpenXR

Se ha agregado compatibilidad, tanto en el editor como en tiempo de ejecución, con el modelo de controlador de movimiento proporcionado por el sistema en OpenXR.

![Ventana del editor que muestra dos modelos de controlador de movimiento](https://user-images.githubusercontent.com/3580640/116493405-89a55d80-a853-11eb-95ae-d430e6fdc8b4.png)

### <a name="support-for-hololens-2-articulated-hand-mesh-on-openxr"></a>Compatibilidad con HoloLens 2 de mano articulada en OpenXR

![La malla de mano que se ejecuta en el dispositivo en una escena de ejemplo de MRTK](https://user-images.githubusercontent.com/3580640/112909923-32bb3580-90a7-11eb-925d-464b135edc61.png)

### <a name="support-for-controller-haptics-across-legacy-wmr-windows-xr-plugin-and-openxr"></a>Compatibilidad con las hapticas de controlador en WMR heredado, el complemento XR de Windows y OpenXR

Se ha agregado compatibilidad con los hápticos de controlador en WMR heredado, el complemento XR de Windows y OpenXR. [#9735](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9735)

### <a name="support-for-eye-tracking-on-windows-xr-plugin"></a>Compatibilidad con el seguimiento de los ojos en el complemento XR de Windows

Se ha agregado compatibilidad con la mirada con los ojos al usar las versiones mínimas del complemento XR de Windows de 2.7.0 (Unity 2019), 4.4.2 (Unity 2020) y 5.2.2 (Unity 2021). [#9609](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9609)

### <a name="notable-bugfixes-and-changes"></a>Correcciones de errores y cambios importantes

- Se ha suavizado la detección de la detección de desenlazados. Ahora es más difícil quitar accidentalmente el gesto de acercar. [#9576](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9576)
- Ahora, los objetos con el componente Manipulador de objetos mantienen la velocidad en la versión cuando se establece la marca. [#9733](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9733)
- Ahora, el desplazamiento hacia atrás comprueba si hay un suelo, lo que ayuda a evitar situaciones en las que la cámara puede recortar en el entorno o en las que el usuario deja el puntero sobre un espacio vacío. [#9697](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9697)
- IsNearObject es ahora una propiedad virtual, lo que permite más flexibilidad al extender la esfera o el puntero de puntero. [#9803](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9803)
- Los botones ahora muestran la palabra clave adecuada al mostrar el comando de voz disponible. [#9824](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9824)
- Los controladores de Oculus ahora usan su propio visualizador independiente, lo que impide que la visualización de MRTK entre en conflicto con la visualización del paquete de integración de Oculus. [#9589](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9589)
- Los scripts relacionados con el teclado se han cambiado para alinearse con el comportamiento de las versiones más recientes de Unity (2019.4.25+ & 2020.3.2+). A partir de la versión, todavía hay un error de finalización automática y un error de campo de entrada de TMP (ambos son externos a MRTK) que afecta a HoloLens. Para obtener más información, [vea #9056](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9056) y [#9724](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9724).
- Se ha mejorado el rendimiento de la colección de objetos de desplazamiento. También se ha corregido un problema que provocaba que GameObject de la colección perdiera material cuando se duplicara. [#9813](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9813), [#9718](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9718)
- En el script de demostración de Scene Understanding, se ha agregado la función para recuperar todo el objeto de escena `GetSceneObjectsOfType` observado de un tipo determinado. [#9524](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9524), [#9744](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9744)
- En la herramienta de compilación de línea de comandos, solo se incluirán en la compilación las escenas especificadas por las marcas o (cuando haya alguna `sceneList` `sceneListFile` marca). [#9695](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9695)
- En la herramienta de compilación, hay una nueva opción para especificar una ruta de acceso a y usarla para realizar la restauración de paquetes en lugar de `nuget.exe` `msbuild` usar (la opción predeterminada). [#9556](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9556)
- Se ha corregido un problema por el que el uso del complemento XR de Windows podía dar lugar a uniones de manos obsoletas y mallas de mano dobles. [#9890](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9890)
- Se ha corregido un problema por el que el uso de la característica de comunicación remota automática del complemento XR de Windows generaba la falta de entradas e interacciones. [#9868](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9868)
- Se ha corregido un problema por el que BuildDeployWindow intentaba consultar una clave reg no válida para la Windows SDK de acceso. [#9664](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9664)
- Los importadores glTF de MRTK ahora son opcionales. Si hay varios importadores glTF presentes, los de MRTK se pueden deshabilitar agregando a los símbolos de `MRTK_GLTF_IMPORTER_OFF` definición de scripting personalizados. [#9658](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9658)
- Se ha corregido un problema por el que los controladores de Knuckles en OpenVR no se detectaba correctamente. [#9881](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9881)
- Reduzca el número de asignaciones por fotograma al visualizar la malla [de mano #9756](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9756)
- Se ha agregado un elemento de menú para iniciar el paquete de ejemplos de MRTK (en Unity Administrador de paquetes) para facilitar la importación de ejemplos [#9798](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/9798)
- Se ha reducido el número de advertencias en tiempo de carga al usar Unity 2020.3.
- Documentación de la característica Ventana de compilación agregada: [Visite la página](/windows/mixed-reality/mrtk-unity/features/tools/build-window)

## <a name="known-issues"></a>Problemas conocidos

### <a name="audio-demos-are-missing-an-asmdef-file-upm-package"></a>A las demostraciones de audio les falta un archivo asmdef (paquete UPM)

Al importar MRTK a través de Mixed Reality Feature Tool, se agregan ejemplos y demostraciones al proyecto mediante la interfaz de usuario Administrador de paquetes Unity. Después de importar las demostraciones de audio, la `WindowsMicrophoneStreamDemo.unity` escena no se comportará correctamente. Esto es el resultado de que falta un archivo .asmdef para el ejemplo.

Para evitar este [problema,](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9908)realice los pasos siguientes:

- Copy Library/PackageCache/com.microsoft.mixedreality.toolkit.examples@[...] /MRTK. Examples.asmdef en la carpeta "Assets/Samples/Mixed Reality Toolkit Examples"
- Cambie el nombre del archivo copiado a Ejemplos.
- Abrir el archivo de ejemplos
- En el cuadro Nombre, reemplace el contenido por Ejemplos.
- Haga clic en Aplicar.
- Compilación e implementación

Este problema se solucionará en una próxima versión de MRTK.

### <a name="mrtk-build-window-triggers-indefinite-importing-assets-dialog-in-unity-20203"></a>La ventana de compilación de MRTK desencadena el cuadro de diálogo "Importar recursos" indefinido en Unity 2020.3

Hay un [](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9723) problema conocido con la ventana de compilación de MRTK en Unity 2020.3 donde, después de realizar correctamente una compilación de UWP, el cuadro de diálogo "Importar recursos" no se completa. Este problema se está investigando en colaboración con Unity.

### <a name="text-mesh-pro-canvas-renderer-warnings-in-unity-2020"></a>Advertencias del representador de lienzo de Text Mesh Pro en Unity 2020

La advertencia siguiente se registra en la mayoría de las escenas de ejemplo de MRTK mientras se usa Unity 2020:

```txt
Please remove the CanvasRenderer component from the [TextMeshPro] GameObject as this component is no longer necessary.
```

La advertencia Representador de lienzo se agregó [en TextMeshPro versión 3.0.3.](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/changelog/CHANGELOG.html#changes-3)  Estas advertencias no afectan a las escenas de ejemplo de MRTK y se pueden borrar desde la consola. Consulte [el problema 9811](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9811) para obtener más detalles.
