---
title: Introducción a OpenXR
description: Comience a usar el estándar portable OpenXR API en Windows Mixed Reality y los auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Herramientas de desarrollo, DirectX, nativo, aplicación nativa, motor personalizado, middleware, introducción, 101, extensiones de vista previa, versión de tiempo de ejecución de OpenXR, estado del sistema
ms.openlocfilehash: 918dfb1f336598548735b1699c61d1b350fed293
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613199"
---
# <a name="getting-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introducción a OpenXR para HoloLens 2

Para empezar a desarrollar aplicaciones de OpenXR para HoloLens 2:

1. Configure un HoloLens 2 o siga las instrucciones para [instalar una versión reciente del emulador de hololens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md). Ya debe tener OpenXR 1,0 listo para empezar si usa una imagen de emulador reciente o el dispositivo ha actualizado su sistema operativo.
2. Asegúrese de que tiene el tiempo de ejecución de OpenXR más reciente con todas [las extensiones](openxr.md#roadmap) presentes mediante el inicio de la aplicación de la **tienda** desde el dispositivo o el emulador.
    * Abra el menú de la parte superior derecha, seleccione **descargas y actualizaciones** y elija **obtener actualizaciones**.  

> [!NOTE]
> Si usa el emulador, la imagen del emulador se restablecerá cada vez que la inicie y, por lo tanto, la mejor opción es asegurarse de que tiene [la versión más reciente de la imagen del emulador de HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introducción a OpenXR para auriculares con Windows Mixed Reality

Para empezar a desarrollar aplicaciones de OpenXR para auriculares con Windows de realidad mixta:

1. Asegúrese de que está ejecutando al menos la actualización 2019 de Windows 10 (1903), que es el requisito mínimo para que los usuarios finales de Windows Mixed Reality ejecuten aplicaciones OpenXR.  Si se encuentra en una versión anterior de Windows 10, puede actualizar mediante el Asistente de <a href="https://www.microsoft.com/software-download/windows10" target="_blank">actualización de Windows 10</a>.
2. Configure un casco de realidad mixta de Windows o siga las instrucciones para [Habilitar el simulador de realidad mixta de Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md).

Eso es todo.  Windows Mixed Reality OpenXR Runtime se instala y se activa automáticamente para todos los usuarios de Windows Mixed Reality.  A continuación, el Microsoft Store mantiene actualizado el tiempo de ejecución.

Para activar de nuevo el tiempo de ejecución de Windows Mixed Reality OpenXR, inicie el portal de realidad mixta en el menú Inicio y seleccione "corregirlo" en la parte superior de la ventana.  Si falta ese botón, el tiempo de ejecución de OpenXR ya está activo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtención del Herramientas de desarrollo OpenXR para Windows Mixed Reality

Para probar el tiempo de ejecución de Windows Mixed Reality OpenXR, puede instalar la <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicación OpenXR herramientas de desarrollo para Windows Mixed Reality</a>.  Esta aplicación proporciona una demostración de diversas características de OpenXR, junto con una página de estado del sistema con información clave sobre el tiempo de ejecución activo y el casco actual.

Al usar el emulador de HoloLens 2, la manera más sencilla de instalar el Herramientas de desarrollo OpenXR para Windows Mixed Reality es a través del [portal de dispositivos de Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Vaya a la página "OpenXR" y, a continuación, haga clic en el botón "instalar" en "características para desarrolladores", que también funciona en dispositivos físicos de HoloLens 2.

![OpenXR Herramientas de desarrollo para aplicaciones de Windows Mixed Reality](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Compilación de una aplicación de OpenXR de ejemplo

Asegúrese de [instalar las herramientas](../install-the-tools.md) que necesita para el desarrollo de OpenXR si todavía no lo ha hecho.

En el proyecto <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> se muestra un ejemplo de OpenXR sencillo con archivos de proyecto Win32 y UWP de HoloLens 2 en Visual Studio. Dado que la solución contiene un proyecto de UWP de HoloLens, necesitará la [carga de trabajo de desarrollo de plataforma universal de Windows](../install-the-tools.md#installation-checklist) instalada en Visual Studio para abrirla por completo.

Aunque los archivos de proyecto de UWP y Win32 son independientes debido a las diferencias de empaquetado e implementación, el código de la aplicación dentro de cada proyecto es casi exactamente el mismo.

Después de crear un escritorio de Win32 de OpenXR. EXE, puede usarlo con un casco de VR en cualquier plataforma de escritorio VR que admita OpenXR, sea cual sea el tipo de casco.

Después de compilar un paquete de aplicación de UWP para OpenXR, puede [implementarlo](../platform-capabilities-and-apis/using-visual-studio.md) en un dispositivo hololens 2 o en el emulador de hololens 2.

## <a name="learning-the-openxr-api"></a>Aprendizaje de la API de OpenXR

Para ver un paseo por la API de OpenXR, consulte este vídeo de 60 minutos del ejemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> en Visual Studio.  En el vídeo se muestra cómo se puede usar cada uno de los componentes principales de la API de OpenXR en su propio motor y también se muestran algunas de las aplicaciones compiladas en OpenXR hoy:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integrar el cargador de OpenXR en un proyecto

Para empezar a trabajar con OpenXR en un proyecto existente, incluirá el cargador de OpenXR.  El cargador detecta el tiempo de ejecución de OpenXR activo en el dispositivo y proporciona acceso a las funciones básicas y a las funciones de extensión que implementa.

Puede [hacer referencia al paquete de NuGet OpenXR oficial](#reference-official-openxr-nuget-package) desde el proyecto de Visual Studio o [incluir el origen oficial del cargador de OpenXR](#include-official-openxr-loader-source) desde el repositorio de github de Khronos.  Cualquier enfoque le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Si le interesa experimentar `MSFT_preview` también con las extensiones, puede [Copiar en la vista previa](#using-preview-extensions) de los encabezados de OpenXR desde el repositorio de github de realidad mixta.

### <a name="reference-official-openxr-nuget-package"></a>Referencia a un paquete de NuGet de OpenXR oficial

El <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank">paquete NuGet **OpenXR. Loader**</a> es la forma más fácil de hacer referencia a un cargador de OpenXR creado previamente. DLL en la solución de Visual Studio C++.  Esto le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Para agregar una referencia de paquete NuGet OpenXR. Loader a su solución de Visual Studio C++:
1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto que usará OpenXR y seleccione **administrar paquetes NuGet..**..
2. Cambie a la pestaña **examinar** y busque **OpenXR. Loader**.
3. Seleccione el paquete **OpenXR. Loader** y seleccione instalar en el panel de detalles de la derecha.
4. Seleccione Aceptar para aceptar los cambios en el proyecto.
5. Agregue `#include <openxr/openxr.h>` a un archivo de código fuente para empezar a usar la API de OpenXR.

Para ver un ejemplo de la API de OpenXR en acción, consulte la aplicación de ejemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> .

### <a name="include-official-openxr-loader-source"></a>Incluir origen oficial de cargador de OpenXR

Si desea compilar el cargador por su cuenta, por ejemplo, para evitar el cargador adicional. DLL, puede extraer los orígenes oficiales del cargador de Khronos OpenXR en el proyecto.  Esto le proporcionará acceso a las características principales de OpenXR 1,0, además de las publicadas `KHR` `EXT` y `MSFT` las extensiones.

Para empezar aquí, siga las instrucciones del <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">repositorio Khronos OpenXR-SDK en github</a>.  El proyecto está configurado para compilar con CMake. Si usa MSBuild, deberá copiar el código en su propio proyecto.

## <a name="using-preview-extensions"></a>Uso de extensiones de vista previa

Las `MSFT_preview` extensiones enumeradas en el [mapa de ruta](openxr.md#roadmap) de la extensión son extensiones de proveedor experimentales en las que se obtiene una vista previa para recopilar comentarios.  Estas extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuya la extensión real.

Si está interesado en probar las `MSFT_preview` extensiones disponibles, siga los pasos que se indican a continuación para actualizar el proyecto:
1. Siga uno de los métodos anteriores para integrar un cargador de OpenXR en el proyecto.
2. Reemplace los encabezados OpenXR estándar del proyecto por los <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">encabezados de vista previa del repositorio Mixed Reality OpenXR en github</a>.

Para activar la compatibilidad con la extensión de vista previa en el equipo de escritorio o HoloLens 2 de destino:
  1. Para asegurarse de que tiene el tiempo de ejecución de OpenXR más reciente con todas [las extensiones](openxr.md#roadmap) presentes, inicie la aplicación de la **tienda** desde el emulador o el dispositivo de destino, abra el menú de la parte superior derecha, seleccione **descargas y actualizaciones** y elija **obtener actualizaciones**.
  2. Instale la <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicación OpenXR herramientas de desarrollo para Windows Mixed Reality</a> del Microsoft Store en el dispositivo de destino y ejecútela.
  3. Vaya a la pestaña **configuración del desarrollador** y habilite usar la **versión más reciente de OpenXR Runtime**.  Esto habilita el tiempo de ejecución de vista previa en el dispositivo, que tiene activadas las extensiones de versión preliminar.
     ![OpenXR Herramientas de desarrollo para la pestaña Configuración del desarrollador de aplicaciones de Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Confirme que la **versión en tiempo de ejecución** que se muestra en la pestaña **Estado del sistema** del [herramientas de desarrollo OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) coincide con la versión necesaria de las extensiones de vista previa que planea probar.  En ese caso, debería ver la extensión en la lista de **extensiones** .  Una vez que haya disponible una extensión estable, se quitará su extensión de vista previa.<br />
     ![OpenXR Herramientas de desarrollo para la pestaña Estado del sistema de la aplicación Windows Mixed Reality](images/mixed-reality-openxr-developer-tools-status.png)

Consulte el <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">repositorio de OpenXR de realidad mixta</a> para obtener documentación de estas extensiones de vista previa y ejemplos de cómo usarlas.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para empezar a trabajar con el desarrollo de OpenXR, consulte nuestras [sugerencias sobre solución de problemas](openxr-troubleshooting.md).