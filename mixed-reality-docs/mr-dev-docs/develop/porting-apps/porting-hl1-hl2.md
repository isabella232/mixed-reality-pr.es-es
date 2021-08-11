---
title: Portabilidad de aplicaciones de HoloLens (1.ª generación) a HoloLens 2
description: Esta opción está diseñada para desarrolladores que ya tienen una aplicación en HoloLens (1.ª generación) o una versión anterior de MRTK, y quieren realizar la portabilidad a la versión 2 de MRTK y a HoloLens 2.
author: hferrone
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2, unity, porting, HoloLens 1st gen, mixed reality headset, windows mixed reality headset, virtual reality headset, migration, best practices, ARM
ms.openlocfilehash: f7a70a8bd5a6d11d6502b431b17bbd3391d24ce4e19f0a842503ccae834589fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219294"
---
# <a name="porting-hololens-1st-gen-apps-to-hololens-2"></a>Portabilidad de aplicaciones de HoloLens (1.ª generación) a HoloLens 2

Esta guía está diseñada específicamente para ayudar a los desarrolladores que tienen una aplicación existente de Unity para HoloLens (1.ª generación) para realizar la portabilidad de su aplicación al dispositivo HoloLens 2. Hay cuatro pasos clave para portar una aplicación de Unity de HoloLens (1.ª generación) a HoloLens 2. 

En las secciones siguientes se detalla la información de cada fase:

| Paso 1 | Paso 2 | Paso 3 | Paso 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo de Visual Studio](../images/visualstudio_logo.png) | ![Logotipo de Unity](../../design/images/logo-unity.png)| ![Icono de Unity](../unity/images/hololens2_icon.jpg) | ![Logotipo de MRTK](../../design/images/74-12.png) |
| Descarga de las herramientas más recientes | Actualización del proyecto de Unity | Compilación para ARM | Migración a versión 2 de MRTK

## <a name="prerequisites"></a>Requisitos previos

Se **recomienda encarecidamente** usar el control de código fuente para guardar una instantánea del estado original de la aplicación antes de iniciar el proceso de portabilidad. Además, se recomienda *guardar* estados de punto de control en varios momentos durante el proceso. También puede ser útil tener otra instancia de Unity de la aplicación original para compararlas en paralelo durante el proceso de portabilidad. 

> [!NOTE]
> Antes de realizar la portabilidad, asegúrate de que tienes instaladas las herramientas más recientes para el desarrollo de Windows Mixed Reality. Para la mayoría de los desarrolladores de HoloLens existentes, esto implica actualizar a la versión más reciente de Visual Studio 2019 e instalar el Windows SDK adecuado. El contenido siguiente profundiza más en las diferentes versiones de Unity y la versión 2 de Mixed Reality Toolkit (MRTK).
>
> Para más información, consulta [Instalar las herramientas](../install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Migración del proyecto a la última versión de Unity

Si usa [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), se recomienda actualizar a MRTK 2.7 antes de actualizar el proyecto a [Unity 2020.3 LTS](../unity/choosing-unity-version.md). MRTK 2.7 admite Unity 2018, 2019 y 2020, lo que le permite asegurarse de que el proyecto esté listo para Unity 2020 incluso antes de actualizar Unity. Debe evaluar cualquier [dependencia de complemento](https://docs.unity3d.com/Manual/Plugins.html) que exista actualmente en el proyecto, y determinar si estos archivos DLL pueden compilarse para ARM64. En el caso de los proyectos con un complemento dependiente de ARM64, es posible que deba seguir compilando la aplicación para ARM.

## <a name="update-sceneproject-settings-in-unity"></a>Actualización de la configuración de la escena o proyecto en Unity

Después de actualizar a [Unity 2020.3 LTS](https://unity3d.com/unity/qa/lts-releases), se recomienda actualizar valores concretos en Unity para obtener los mejores resultados en el dispositivo. Estos valores se describen en detalle en [Configuración recomendada para Unity](../unity/Recommended-settings-for-Unity.md).

Recuerde que el [back-end de scripting de .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) estará en desuso en Unity 2018 y se habrá **eliminado** a partir de Unity 2019. Es muy recomendable que los desarrolladores consideren la posibilidad de cambiar su proyecto a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html).

> [!NOTE]
> El back-end del scripting de IL2CPP puede aumentar los tiempos de compilación de Unity a Visual Studio, y los desarrolladores deben configurar la máquina de desarrollo para [optimizar los tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> También puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas y activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo, en lugar de que cada desarrollador tenga que procesar localmente la reimportación de los nuevos cambios.

Después de solucionar los cambios importantes tras el cambio a la versión actualizada de Unity, debe compilar y probar sus aplicaciones actuales en HoloLens (1.ª generación). Este es un buen momento para crear y guardar una confirmación en el control de código fuente.

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilación de dependencias/complementos para procesadores ARM

HoloLens (1.ª generación) ejecuta las aplicaciones en un procesador x86, mientras que el dispositivo HoloLens 2 usa un procesador ARM. Por lo tanto, las aplicaciones de HoloLens existentes se tienen que portar para admitir ARM. Como se indicó anteriormente, Unity 2018 LTS admite la compilación para las aplicaciones de ARM32, mientras que Unity 2019 y versiones posteriores admiten la compilación para las aplicaciones de ARM32 y ARM64. Es preferible desarrollar para aplicaciones de ARM64, ya que existe una diferencia sustancial en el rendimiento. Sin embargo, esto requiere que todas [las dependencias de complemento](https://docs.unity3d.com/Manual/Plugins.html) se compilen también para ARM64.

Revisa todas las dependencias DLL en la aplicación. Se recomienda quitar las dependencias que ya no sean necesarias para el proyecto. Para el resto de complementos que son necesarios, se deben ingerir los respectivos archivos binarios de ARM32 o ARM64 en el proyecto de Unity.

Después de la ingesta de las DLL pertinentes, compile una solución de Visual Studio desde Unity y, a continuación, compile un paquete AppX para ARM en Visual Studio para probar que la aplicación se pueda compilar para procesadores ARM. Se recomienda guardar la aplicación como una confirmación en la solución de control de código fuente.

> [!IMPORTANT]
> La aplicación que usa MRTK v1 puede ejecutarse en HoloLens 2 después de cambiar el destino de compilación a ARM, suponiendo que se cumplen todos los demás requisitos. Esto incluye asegurarse de que tiene versiones ARM de todos los complementos. Sin embargo, la aplicación no tendrá acceso a funciones específicas de HoloLens 2, como el seguimiento de la mano articulada y el ojo. MRTK v1 y MRTK v2 tienen distintos espacios de nombres que permiten que ambas versiones estén en el mismo proyecto, lo que resulta útil para realizar la transición de una a otra.

## <a name="update-to-mrtk-version-2"></a>Actualización a la versión 2 de MRTK

[MRTK versión 2](https://github.com/microsoft/MixedRealityToolkit-Unity) es el nuevo kit de herramientas además de Unity que admite tanto HoloLens (1.ª generación) como HoloLens 2. También es donde se agregan todas las nuevas funcionalidades de HoloLens 2, como las interacciones con la mano y el seguimiento de los ojos.

Consulte los recursos siguientes para obtener más información sobre el uso de la versión 2 de MRTK:

- [Página principal de documentación de MRTK](/windows/mixed-reality/mrtk-unity)
- [Guía de instalación](/windows/mixed-reality/mrtk-unity/install-the-tools)
- [Seguimiento de manos de MRTK](/windows/mixed-reality/mrtk-unity/features/input/hand-tracking)
- [Seguimiento de los ojos de MRTK](/windows/mixed-reality/mrtk-unity/features/input/eye-tracking/eye-tracking-main)

### <a name="prepare-for-the-migration"></a>Preparación para la migración

Antes de realizar la ingesta de los nuevos [archivos *.unitypackage para la versión 2 de MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), se recomienda realizar un inventario de **1) cualquier código personalizado que se integre con la versión 1 de MRTK** y **2) cualquier código personalizado para las interacciones de entrada o los componentes de la experiencia de usuario**. El conflicto más común y que se da con más frecuencia para un desarrollador de realidad mixta en relación con la ingesta de la versión 2 de MRTK tiene que ver con las entradas y las interacciones. Se recomienda comenzar a leer el [modelo de entrada de la versión 2 de MRTK](/windows/mixed-reality/mrtk-unity/features/input/overview) para obtener una mejor comprensión del mismo.

Por último, la nueva [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity) ha pasado de un modelo de scripts y objetos de administrador en la escena a una arquitectura de configuración y proveedor de servicios. Esto da como resultado un modelo de arquitectura y jerarquía de escena más limpio, pero requiere una curva de aprendizaje para comprender los nuevos perfiles de configuración. Por ello, le recomendamos que lea [Guía de configuración del kit de herramientas de Mixed Reality](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) para familiarizarse con los perfiles y opciones más importantes con los que podrá ajustarse a las necesidades de la aplicación.

### <a name="migrating-the-project"></a>Migración del proyecto

Después de importar [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), el proyecto de Unity probablemente tenga muchos errores relacionados con el compilador. Generalmente, estos errores se deben a la nueva estructura del espacio de nombres y de los nuevos nombres de componente. Puede resolver estos errores mediante la modificación de los scripts con los espacios de nombres y componentes nuevos.

Para más información sobre las diferencias de API específicas entre HTK/MRTK y MRTK v2, consulta la guía de migración en la [wiki de la versión 2 de MRTK](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide).

### <a name="best-practices"></a>Procedimientos recomendados

- Da preferencia al uso del [sombreador MRTK Standard](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader).
- Trabaja en un solo tipo de cambio importante a la vez (por ejemplo: IFocusable a [IMixedRealityFocusHandler](/dotnet/api/microsoft.mixedreality.toolkit.input.imixedrealityfocushandler)).
- Haz una prueba después de cada cambio y usa el control de código fuente.
- Use experiencias de usuario de MRTK predeterminadas (botones, tabletas táctiles, etc.) cuando sea posible.
- Intenta evitar la modificación de los archivos de MRTK directamente; en su lugar, crea contenedores en torno a los componentes de MRTK.
  - Esta acción facilita las futuras ingestas y actualizaciones de MRTK.
- Revisa y explora escenas de ejemplo proporcionadas en MRTK (especialmente *HandInteractionExamples.scene*).
- Vuelve a generar la interfaz de usuario basada en lienzo con cuadrángulos, colisionadores y texto TextMeshPro.
- Habilita el [uso compartido del búfer de profundidad](../unity/camera-in-unity.md#sharing-depth-buffers) o [establece el punto de enfoque](../unity/focus-point-in-unity.md); es preferible usar un búfer de profundidad de 16 bits para mejorar el rendimiento. Al representar el color, asegúrate de representar también la profundidad. Por lo general, Unity no escribe la profundidad de objetos GameObject de texto y transparentes.
- Establece la ruta de representación de instancia de paso único.
- Use el [perfil de configuración de HoloLens 2 para MRTK](/windows/mixed-reality/mrtk-unity/features/profiles/profiles#hololens-2-profile).

### <a name="testing-your-application"></a>Prueba de la aplicación

En la versión 2 de MRTK, puede simular las interacciones con las manos directamente en Unity, así como desarrollar elementos con las nuevas API para las interacciones con las manos y el seguimiento de los ojos. El dispositivo HoloLens 2 es necesario para crear una experiencia de usuario satisfactoria. Es recomendable que comience examinando la documentación y las herramientas para comprender mejor este tema. La [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity) admite el desarrollo en HoloLens (1.ª generación) y los modelos de entrada tradicionales, como la selección mediante pulsación en el aire, se pueden probar en los dispositivos HoloLens (1.ª generación). 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Actualización del modelo de interacción para HoloLens 2

> [!CAUTION]
> Si el proyecto usa cualquiera de las API XR.WSA, tenga en cuenta que se van a retirar gradualmente en favor de las nuevas API de entrada de XR de Unity en futuras versiones de Unity. Puede encontrar más información sobre estas las [API de entrada de XR aquí](https://docs.unity3d.com/Manual/xr_input.html).

Una vez que la aplicación está portada y preparada para HoloLens 2, ya estás listo para considerar la actualización de las ubicaciones del diseño del holograma y del modelo.
En HoloLens (1ª generación), es muy posible que tu aplicación tenga un modelo de interacción de mirada y confirmación con hologramas relativamente lejanos para encajar en el campo de visión.

Pasos para actualizar el diseño de la aplicación al diseño más adecuado para HoloLens 2:
1.  Componentes de MRTK: por el trabajo previo, si agregas la [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity), hay varios componentes o scripts para aprovechar que se han diseñado y optimizado para HoloLens 2.

2.  Modelo de interacción: Plantéate la posibilidad de actualizar el modelo de interacción. Para la mayoría de los escenarios, se recomienda cambiar de mirada y confirmación a interacciones con las manos. Con tus hologramas normalmente fuera del alcance de la mano, el cambio a las entradas de interacción con las manos produce gestos de agarre y haces apuntadores de interacción lejana.

3.  Ubicación de hologramas: después de cambiar a un modelo de interacción con las manos, considera la posibilidad de acercar algunos hologramas para interactuar directamente con ellos, utilizando gestos de agarre de interacción cercana con las manos. Los tipos de hologramas recomendados para el acercamiento que te permita agarrar o interactuar directamente, son los menús de destino pequeños, controles, botones y los hologramas más pequeños que caben dentro del campo de visión de HoloLens 2 al agarrar e inspeccionar el holograma.
<br>
Cada aplicación y escenario son diferentes, y vamos a seguir mejorando y publicando instrucciones para el diseño basadas en comentarios y en lo que vamos aprendiendo cada día.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Advertencias y aprendizajes adicionales sobre cómo mover aplicaciones de x86 a ARM

- Las aplicaciones directas de Unity son sencillas porque puedes compilar un paquete de aplicaciones de ARM o realizar la implementación directamente en el dispositivo para que se ejecute la agrupación. Algunos complementos nativos de Unity pueden presentar ciertos desafíos de desarrollo. Por este motivo, debes actualizar todos los complementos nativos de Unity a Visual Studio 2019 y, a continuación, volver a generarlos para ARM.

- Una aplicación usó el complemento AudioKinetic Wwise de Unity y esa versión de Unity no tenía ningún complemento de ARM para UWP, lo que exigió un esfuerzo considerable para volver a crear las funcionalidades de sonido en la aplicación en cuestión para su ejecución en ARM. Asegúrate de que todos los complementos necesarios para tus planes de desarrollo están instalados y disponibles en Unity.

- En algunos casos, puede que no exista un complemento de UWP/ARM para los complementos necesarios para la aplicación, lo que bloquea la capacidad de portar la aplicación y ejecutarla en HoloLens 2. Ponte en contacto con tu proveedor de complementos para resolver el problema y obtener compatibilidad con ARM.

- El comando minfloat (y sus variantes, como min16float, minint, etc.) puede comportarse en los sombreadores de manera diferente en HoloLens 2 a como lo hacía en HoloLens (1.ª generación). En concreto, estos garantizan que se utilizará al menos el número especificado de bits. En las GPU de Nvidia o Intel, estos comandos minfloat se tratan generalmente como de 32 bits. En ARM, el número de bits especificado se respeta. En la práctica, esto significa que estos números pueden tener menos precisión o rango en HoloLens 2 del que tenían en HoloLens (1.ª generación).

- Las instrucciones _asm no parecen funcionar en ARM, lo que significa que cualquier código con instrucciones _asm tiene que volverse a escribir.

- ARM no admite el conjunto de instrucciones SIMD, ya que varios encabezados, como xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h, no están disponibles en ARM.

- El compilador del sombreador en ARM se ejecuta durante la primera llamada draw, después de que el sombreador se haya cargado, o algo en lo que se basa sombreador haya cambiado, no en el tiempo de carga de sombreador. El impacto en la velocidad de fotogramas puede ser apreciable, en función de cuántos sombreadores deban compilarse; asimismo, hay que tener en cuenta que los sombreadores se deben controlar, empaquetar y actualizar de forma diferente en HoloLens 2, en comparación con HoloLens (1.ª generación).

## <a name="see-also"></a>Consulta también

* [Instalación de las herramientas](../install-the-tools.md)
* [Guía de instalación de MRTK](/windows/mixed-reality/mrtk-unity/install-the-tools)
* [Página principal de documentación de MRTK](/windows/mixed-reality/mrtk-unity)
* [Migración de HoloToolkit/MRTK a MRTK, versión 2](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
* [Configuración recomendada para Unity](../unity/recommended-settings-for-unity.md)
* [Análisis de rendimiento de la realidad mixta](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)