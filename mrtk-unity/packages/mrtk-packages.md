---
title: Paquetes de MRTK
description: Paquetes de MRTK que admiten hardware y plataformas de realidad mixta.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, Unity Administrador de paquetes,
ms.openlocfilehash: 3c92448d99cd67efa0a06feff9b0c7561a6aea79
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143808"
---
# <a name="mixed-reality-toolkit-packages"></a>Mixed Reality Toolkit

Mixed Reality Toolkit (MRTK) es una colección de paquetes que permiten el desarrollo de aplicaciones multiplataforma Mixed Reality proporcionando compatibilidad con hardware y plataformas Mixed Reality aplicaciones.

MRTK está disponible como [paquetes de](#asset-packages) recursos (.unitypackage) y a través de [unity Administrador de paquetes](#unity-package-manager).

## <a name="asset-packages"></a>Paquetes de activos

El recurso de MRTK (.unitypackage) se puede descargar desde [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)

Algunas de las ventajas de usar paquetes de recursos incluyen:

- Disponible para Unity 2018.4 y versiones más recientes
- Fácil de realizar cambios en MRTK
  - MRTK está en la carpeta Assets

Algunos de los desafíos son:

- MRTK forma parte de la carpeta Assets del proyecto, lo que conduce a
  - Proyectos más grandes
  - Tiempos de compilación más lentos
- Sin administración de dependencias
  - Los clientes deben resolver las dependencias de paquetes manualmente
- Proceso de actualización manual
  - Varios pasos
  - Actualizaciones de control de código fuente grandes (más de 3000 archivos)
  - Riesgo de perder los cambios realizados en MRTK
- Importar el paquete de ejemplos normalmente significa incluir todos los ejemplos

Los paquetes disponibles son:

- [Foundation](#foundation-package)
- [Extensiones](#extensions-package)
- [Herramientas](#tools-package)
- [Utilidades de prueba](#test-utilities-package)
- [Ejemplos](#examples-package)

Microsoft lanza y admite estos paquetes desde el código fuente de [la mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) en GitHub.

### <a name="foundation-package"></a>Paquete foundation

La Mixed Reality Toolkit Foundation es el conjunto de código que permite a la aplicación aprovechar la funcionalidad común entre Mixed Reality plataformas.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>Paquete de MRTK Foundation</sup>

El paquete de MRTK Foundation contiene lo siguiente.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Core | | Definiciones de interfaz y tipo, clases base, sombreador estándar. |
| MRTK/Core/Providers | | Proveedores de datos independientes de la plataforma |
| | Manos | Soporte técnico y servicios de clase base para el seguimiento a mano. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Compatibilidad con la grabación del movimiento de la cabeza y los datos de seguimiento de las manos. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Compatibilidad con la simulación en el editor de la entrada de manos y ojos. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Observador de reconocimiento espacial que usa un modelo 3D como datos. |
| | UnityInput | Dispositivos de entrada comunes (ratón, etc.) implementados a través de la API de entrada de Unity. |
| MRTK/Providers | | Proveedores de datos específicos de la plataforma |
| | LeapMotion | Compatibilidad con el controlador Leap Motion de UltraLeap. |
| | OpenVR | Compatibilidad con dispositivos OpenVR. |
| | Oculus | Compatibilidad con dispositivos Oculus, como La Misión. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Experimental) Proveedor de configuración de cámara que permite el uso de MRTK con dispositivos ar móviles. |
| | WindowsMixedReality | Compatibilidad con dispositivos Windows Mixed Reality, incluidos Microsoft HoloLens cascos envolventes. |
| | Windows | Compatibilidad con API específicas de Microsoft Windows, por ejemplo, voz y dictado. |
| | XR SDK | (Experimental) Compatibilidad con [el nuevo marco XR de Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) en Unity 2019.3 y versiones más recientes. |
| MRTK/SDK | | |
| | Habilitación de características | Características experimentales, incluidos sombreadores, controles de interfaz de usuario y administradores del sistema individuales. |
| | Características | Funcionalidad que se basa en el paquete de Foundation. |
| | Profiles | Perfiles predeterminados para los sistemas y servicios de Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Recursos comunes; modelos, texturas, materiales, etc. |
| MRTK/SceneSystemResources | | Recursos y recursos usados por scene system |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema que implementa compatibilidad con límites de VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema que implementa la configuración y administración de la cámara. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Implementación del sistema en diagnósticos de aplicaciones, por ejemplo, un profiler visual. |
| | [InputSystem](../features/input/overview.md) | Sistema que proporciona compatibilidad para acceder a la entrada del usuario y controlarla. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema que proporciona compatibilidad con aplicaciones de varias escenas. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema que proporciona compatibilidad para el reconocimiento del entorno del usuario. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Sistema que proporciona compatibilidad con la teleportación (moverse por la experiencia en saltos). |
| MRTK/StandardAssets | | Sombreador mrtk estándar, materiales básicos y otros recursos estándar para experiencias de realidad mixta |

### <a name="extensions-package"></a>Paquete de extensiones

El paquete opcional Microsoft.MixedRealityToolkit.Unity.Extensions incluye servicios adicionales que amplían la funcionalidad de Microsoft Mixed Reality Toolkit.

> [!NOTE]
> El paquete de extensiones requiere Microsoft.MixedRealityToolkit.Unity.Foundation.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Servicio que agrega compatibilidad física a las manos articuladas. |
| | LostTrackingService | Servicio que simplifica el control de la pérdida de seguimiento en Microsoft HoloLens dispositivos. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Servicio que simplifica la adición de transiciones de escena fluidas. |

### <a name="tools-package"></a>Paquete de herramientas

El paquete opcional Microsoft.MixedRealityToolkit.Unity.Tools incluye herramientas útiles que mejoran la experiencia de desarrollo de realidad mixta mediante Microsoft Mixed Reality Toolkit.
Estas herramientas se encuentran en el menú **Mixed Reality Toolkit > Utilities del** Editor de Unity.

> [!NOTE]
> El paquete de herramientas requiere Microsoft.MixedRealityToolkit.Unity.Foundation.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | Herramienta que ayuda a simplificar el proceso de compilación e implementación de aplicaciones para UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Herramienta que crea un gráfico de dependencias de recursos en un proyecto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Asistente para ayudar a crear servicios de extensión. |
| | [MigrationWindow](../features/tools/migration-window.md) | Herramienta que ayuda a actualizar el código que usa componentes de MRTK en desuso.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilidad para ayudar a automatizar la configuración de un proyecto de realidad mixta para obtener el mejor rendimiento en Unity. |
| | ReserializeAssetsUtility | Proporciona compatibilidad para volver a inicializar archivos específicos de Unity. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilidad que permite a los desarrolladores determinar rápidamente las asignaciones de Unity para controladores de hardware. |
| | ScreenshotUtility | Permite capturar imágenes de aplicación en el editor de Unity. |
| | TextureCombinerWindow | Utilidad para combinar texturas de gráficos. |
| | [Cuadro de herramientas](../features/ux-building-blocks/toolbox.md) | Interfaz de usuario que facilita la de detectar y usar componentes de la experiencia de usuario de MRTK. |

### <a name="test-utilities-package"></a>Paquete de utilidades de prueba

El paquete opcional Microsoft.MixedRealityToolkit.TestUtilities es una colección de scripts auxiliares que permiten a los desarrolladores crear fácilmente pruebas [de modo de reproducción.](../contributing/unit-tests.md#play-mode-tests) Estas utilidades son especialmente útiles para los desarrolladores que crean componentes de MRTK.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Métodos para simplificar la creación de pruebas en modo de reproducción, incluidas las utilidades de simulación a mano. |

### <a name="examples-package"></a>Paquete de ejemplos

El paquete de ejemplos contiene demostraciones, scripts de ejemplo y escenas de ejemplo que ejecutan la funcionalidad en el paquete de base. Este paquete contiene la [escena HandInteractionExample](../features/example-scenes/hand-interaction-examples.md) (que se muestra a continuación) que contiene objetos de ejemplo que responden a varios tipos de entrada de la mano (articulada y no articulada).

![Escena HandInteractionExample](../features/images/MRTK_Examples.png)

Este paquete también contiene demostraciones de seguimiento ocular, que se [documentan aquí.](../features/example-scenes/eye-tracking-examples-overview.md)

Por lo general, cualquier nueva característica de MRTK debe contener un ejemplo correspondiente en el paquete de ejemplos, aproximadamente siguiendo la misma estructura de carpetas y ubicación.

> [!NOTE]
> El paquete de ejemplos requiere Microsoft.MixedRealityToolkit.Unity.Foundation.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Examples | | |
| | Demostraciones | Escenas simples que ilustran una o dos características relacionadas. |
| | Habilitación de características | Escenas de demostración que ilustran características experimentales. |
| | StandardAssets | Recursos comunes compartidos por varias escenas de demostración. |

## <a name="unity-package-manager"></a>Unity Administrador de paquetes

Para las experiencias que se crean con Unity 2019.4 y versiones más recientes, MRTK está disponible a través de [unity Administrador de paquetes](https://docs.unity3d.com/Manual/Packages.html).

Algunas de las ventajas de usar paquetes de recursos incluyen:

- Proyectos más pequeños
  - Soluciones de Visual Studio más limpia
  - Menos archivos para la comprobación (MRTK es una referencia simple en el `Packages/manifest.json` archivo)
- Compilación más rápida
  - Unity no necesita volver a compilar MRTK durante la creación
- Resolución de dependencias
  - Los paquetes MRTK necesarios se instalan automáticamente al especificar paquetes con dependencias
- Actualización sencilla a las nuevas versiones de MRTK
  - Cambio de la versión en el `Packages/manifest.json` archivo

Algunos de los desafíos son:

- MRTK es inmutable
  - No se pueden realizar cambios sin quitarlos durante la resolución de paquetes
- MRTK no admite paquetes UPM con Unity 2018.4

### <a name="foundation-package"></a>Paquete foundation

El paquete de base ( `com.microsoft.mixedreality.toolkit.foundation` ) constituye la base del kit de herramientas Mixed Reality.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Core | | Definiciones de interfaz y tipo, clases base, sombreador estándar. |
| MRTK/Core/Providers | | Proveedores de datos independientes de la plataforma |
| | Manos | Compatibilidad con clases base y servicios para el seguimiento manual. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Compatibilidad con el movimiento de la cabeza y los datos de seguimiento de manos. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Compatibilidad con la simulación en el editor de la entrada de manos y ojos. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Observador de reconocimiento espacial que usa un modelo 3D como datos. |
| | UnityInput | Dispositivos de entrada comunes (mouse, etc.) implementados a través de la API de entrada de Unity. |
| MRTK/Providers | | Proveedores de datos específicos de la plataforma |
| | LeapMotion | Compatibilidad con el controlador UltraLeap Leap Motion. |
| | OpenVR | Compatibilidad con dispositivos OpenVR. |
| | Oculus | Compatibilidad con dispositivos Oculus, como La misión. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Experimental) Proveedor de configuración de cámara que permite el uso de MRTK con dispositivos ar móviles. |
| | WindowsMixedReality | Compatibilidad con Windows Mixed Reality dispositivos, incluidos Microsoft HoloLens cascos envolventes y envolventes. |
| | Windows | Compatibilidad con API específicas de Microsoft Windows, por ejemplo, voz y dictado. |
| | XR SDK | (Experimental) Compatibilidad con [el nuevo marco XR de Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) en Unity 2019.3 y versiones más recientes. |
| MRTK/SDK | | |
| | Habilitación de características | Características experimentales, incluidos sombreadores, controles de interfaz de usuario y administradores de sistema individuales. |
| | Características | Funcionalidad que se basa en el paquete foundation. |
| | Profiles | Perfiles predeterminados para los sistemas y servicios de Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Recursos comunes; modelos, texturas, materiales, etc. |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema que implementa compatibilidad con límites vr. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema que implementa la configuración y administración de la cámara. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Implementación del sistema en diagnósticos de aplicaciones, por ejemplo, un profiler visual. |
| | [InputSystem](../features/input/overview.md) | Sistema que proporciona compatibilidad para acceder a la entrada del usuario y controlarla. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema que proporciona compatibilidad con aplicaciones de varias escenas. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema que proporciona compatibilidad para conocer el entorno del usuario. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Sistema que proporciona compatibilidad con la teleportación (moverse por la experiencia en saltos). |

Dependencias:

- Recursos estándar ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Recursos estándar

El paquete de recursos estándar ( `com.microsoft.mixedreality.toolkit.standardassets)` es una colección de componentes que se recomiendan para todas las experiencias de realidad mixta, incluidos:

- Sombreador estándar de MRTK
- Materiales básicos que usan el sombreador ESTÁNDAR DE MRTK
- Archivos de audio
- Fuentes
- Texturas
- Iconos

> [!Note]
> Para evitar cambios importantes basados en definiciones de ensamblado, los scripts usados para controlar algunas características del sombreador estándar de MRTK no se incluyen en el paquete de recursos estándar. Estos scripts se pueden encontrar en el paquete foundation de la `MRTK/Core/Utilities/StandardShader` carpeta .

Dependencias: ninguna

### <a name="extension-packages"></a>Paquetes de extensión

El paquete de extensiones opcional ( `com.microsoft.mixedreality.toolkit.extensions)` contiene componentes adicionales que amplían la funcionalidad de MRTK.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Servicio que agrega compatibilidad física a las manos articuladas. |
| | LostTrackingService | Servicio que simplifica la entrega de la pérdida de seguimiento en Microsoft HoloLens dispositivos. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Servicio que simplifica la adición de transiciones de escena fluidas. |
| | Ejemplos~ | Una carpeta oculta (en el Editor de Unity) que contiene las escenas y los recursos de ejemplo. |

Puede encontrar más información sobre el proceso de uso de paquetes que contienen proyectos de ejemplo en el artículo Mixed Reality Toolkit and Unity Administrador de paquetes (Kit de herramientas [de Administrador de paquetes Unity).](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

Dependencias:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Paquete de herramientas

El paquete de herramientas opcional ( `com.microsoft.mixedreality.toolkit.tools)` contiene herramientas que son útiles para crear experiencias de realidad mixta. En general, estas herramientas son componentes del editor y su código no se incluye como parte de una aplicación.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | Herramienta que ayuda a simplificar el proceso de compilación e implementación de aplicaciones para UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Herramienta que crea un gráfico de dependencias de recursos en un proyecto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Asistente para ayudar a crear servicios de extensión. |
| | [MigrationWindow](../features/tools/migration-window.md) | Herramienta que ayuda a actualizar el código que usa componentes de MRTK en desuso.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilidad para ayudar a automatizar la configuración de un proyecto de realidad mixta para obtener el mejor rendimiento en Unity. |
| | ReserializeAssetsUtility | Proporciona compatibilidad para volver a inicializar archivos específicos de Unity. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilidad que permite a los desarrolladores determinar rápidamente las asignaciones de Unity para controladores de hardware. |
| | ScreenshotUtility | Permite capturar imágenes de aplicación en el editor de Unity. |
| | TextureCombinerWindow | Utilidad para combinar texturas de gráficos. |
| | [Cuadro de herramientas](../features/ux-building-blocks/toolbox.md) | Interfaz de usuario que facilita la de detectar y usar componentes de la experiencia de usuario de MRTK. |

Dependencias:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Paquete de utilidades de prueba

El paquete de utilidades de prueba opcional ( ) contiene una colección de scripts auxiliares que permiten a los desarrolladores `com.microsoft.mixedreality.toolkit.testutilities` crear fácilmente pruebas en modo de reproducción. Estas utilidades son especialmente útiles para los desarrolladores que crean componentes de MRTK.

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Métodos para simplificar la creación de pruebas en modo de reproducción, incluidas las utilidades de simulación a mano. |

Dependencias:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Paquete de ejemplos

El paquete de ejemplos ( ), está estructurado para permitir a los `com.microsoft.mixedreality.toolkit.examples` desarrolladores importar solo los ejemplos de interés.

Puede encontrar más información sobre el proceso de uso de paquetes que contienen proyectos de ejemplo en el artículo Mixed Reality Toolkit and Unity Administrador de paquetes (Kit de herramientas [de Administrador de paquetes Unity).](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

| Carpeta | Componente | Descripción |
| --- | --- | --- |
| MRTK/Examples | | |
| | Ejemplos~ | Una carpeta oculta (en el Editor de Unity) que contiene las escenas y los recursos de ejemplo. |
| | StandardAssets | Recursos comunes compartidos por varias escenas de demostración. |

Dependencias:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )
- Extensiones (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Consulte también

- [Introducción a la arquitectura](../architecture/overview.md)
- [Sistemas, servicios de extensión y proveedores de datos](../architecture/systems-extensions-providers.md)
- [Mixed Reality Toolkit y Unity Administrador de paquetes](../configuration/usingupm.md)
