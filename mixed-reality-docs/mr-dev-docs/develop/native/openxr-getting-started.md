---
title: Introducción a OpenXR
description: Introducción al uso del estándar openXR API portátil en Windows Mixed Reality y HoloLens 2 cascos.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Windows Mixed Reality, OpenXR Herramientas de desarrollo, DirectX, native, native, native app, custom engine, middleware, getting started, 101, preview extensions, OpenXR runtime version, system status
ms.openlocfilehash: 6d334b491d231ab5987dd1bc6a3eb43f5e0fe30a82c6525bca1935fbf1cd83bb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189160"
---
# <a name="getting-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco envolvente HoloLens 2 o de Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el HoloLens 2 Emulator o el simulador de Windows Mixed Reality en su lugar.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introducción a OpenXR para HoloLens 2

Para empezar a desarrollar aplicaciones OpenXR para HoloLens 2:

1. Configure un HoloLens 2 o siga las instrucciones para instalar [una versión reciente del emulador de HoloLens 2 .](../platform-capabilities-and-apis/using-the-hololens-emulator.md) Ya debería tener OpenXR 1.0 listo para usarse si usa una imagen reciente del emulador o si el dispositivo ha actualizado su sistema operativo.
2. Asegúrese de que tiene la versión más reciente del entorno de ejecución de OpenXR con todas las extensiones [presentes](openxr.md#roadmap) iniciando la aplicación **store** desde el dispositivo o emulador.
    * Abra el menú de la esquina superior derecha, seleccione **Descargas y actualizaciones** y elija Obtener **actualizaciones.**  

> [!NOTE]
> Si usa el emulador, la imagen del emulador se restablecerá cada vez que la inicie, por lo que su mejor opción es asegurarse de que tiene la versión más reciente de la imagen del emulador [de HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introducción a OpenXR para Windows Mixed Reality cascos

Para empezar a desarrollar aplicaciones OpenXR para cascos envolventes Windows Mixed Reality envolventes:

1. Asegúrese de que ejecuta al menos el Actualización de mayo de 2019 de Windows 10 (1903), que es el requisito mínimo para que los usuarios finales de Windows Mixed Reality ejecuten aplicaciones OpenXR.  Si tiene una versión anterior de Windows 10, puede actualizar mediante el Asistente <a href="https://www.microsoft.com/software-download/windows10" target="_blank">para Windows 10 actualizaciones.</a>
2. Configure un casco Windows Mixed Reality o siga las instrucciones para [habilitar el simulador de Windows Mixed Reality .](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

Eso es todo.  El Windows Mixed Reality tiempo de ejecución de OpenXR se instala y se activa automáticamente para todos Windows Mixed Reality usuarios.  El Microsoft Store mantiene actualizado el tiempo de ejecución.

Para activar el Windows Mixed Reality openXR Runtime de nuevo, inicie Portal de realidad mixta desde el menú Inicio y seleccione "Corregirlo" en la parte superior de la ventana.  Si falta ese botón, el tiempo de ejecución de OpenXR ya está activo.<br>

## <a name="getting-the-openxr-developer-tools-for-windows-mixed-reality"></a>Obtención de las Herramientas de desarrollo OpenXR para Windows Mixed Reality

Para probar el Windows Mixed Reality en tiempo de ejecución de OpenXR, puede instalar <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">openXR Herramientas de desarrollo para Windows Mixed Reality aplicación</a>.  Esta aplicación proporciona una demostración de varias características de OpenXR, junto con una página estado del sistema con información clave sobre el entorno de ejecución activo y el casco actual.

Al usar el emulador HoloLens 2, la manera más fácil de instalar openXR Herramientas de desarrollo for Windows Mixed Reality es a través [del Windows Portal de dispositivos](../platform-capabilities-and-apis/using-the-windows-device-portal.md). Vaya a la página "OpenXR" y, a continuación, haga clic en el botón "Instalar" en "Características del desarrollador", que también funciona en dispositivos HoloLens 2 físicos.

![OpenXR Herramientas de desarrollo para Windows Mixed Reality aplicación](images/mixed-reality-openxr-developer-tools.png)

## <a name="building-a-sample-openxr-app"></a>Creación de una aplicación OpenXR de ejemplo

Asegúrese de instalar [las herramientas](../install-the-tools.md) que necesitará para el desarrollo de OpenXR si aún no lo ha hecho.

El <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">proyecto BasicXrApp</a> muestra un ejemplo simple de OpenXR con Win32 y UWP HoloLens 2 archivos de proyecto en Visual Studio. Dado que la solución contiene un HoloLens de UWP, necesitarás la carga de trabajo Desarrollo de la Plataforma universal de [Windows](../install-the-tools.md#installation-checklist) instalada en Visual Studio para abrirlo por completo.

Aunque los archivos de proyecto de Win32 y UWP son independientes debido a las diferencias en el empaquetado y la implementación, el código de la aplicación dentro de cada proyecto es casi exactamente el mismo.

Después de compilar un dispositivo de escritorio Win32 de OpenXR .EXE, puede usarlo con un casco de realidad virtual en cualquier plataforma de realidad virtual de escritorio que admita OpenXR, sea cual sea el tipo de casco.

Después de compilar un paquete de aplicación [](../platform-capabilities-and-apis/using-visual-studio.md) para UWP de OpenXR, puede implementarlo en un dispositivo HoloLens 2 o en el HoloLens 2 Emulator.

## <a name="learning-the-openxr-api"></a>Learning la API de OpenXR

Para un paseo por la API de OpenXR, consulte este vídeo de 60 minutos del ejemplo <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> en Visual Studio.  En el vídeo se muestra cómo se puede usar cada uno de los componentes principales de la API de OpenXR en su propio motor y también se muestran algunas de las aplicaciones creadas en OpenXR hoy en día:

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/OpenXR-Cross-platform-native-mixed-reality/player?format=ny]

## <a name="integrate-the-openxr-loader-into-a-project"></a>Integración del cargador de OpenXR en un proyecto

Para empezar a trabajar con OpenXR en un proyecto existente, incluirá el cargador de OpenXR.  El cargador detecta el entorno de ejecución activo de OpenXR en el dispositivo y proporciona acceso a las funciones principales y a las funciones de extensión que implementa.

Puede hacer referencia al paquete [de NuGet OpenXR](#reference-official-openxr-nuget-package) oficial desde el proyecto de Visual Studio o incluir el origen oficial del cargador [de OpenXR](#include-official-openxr-loader-source) desde el repositorio de GitHub de Khronos.  Cualquiera de los enfoques le dará acceso a las características principales de OpenXR 1.0, además de las extensiones `KHR` y `EXT` `MSFT` publicadas.

Si también le interesa experimentar con extensiones, puede copiar en la versión preliminar los `MSFT_preview` encabezados [OpenXR](#using-preview-extensions) desde el repositorio Mixed Reality GitHub.

### <a name="reference-official-openxr-nuget-package"></a>Referencia al paquete de NuGet OpenXR oficial

El paquete de NuGet <a href="https://www.nuget.org/packages/OpenXR.Loader/" target="_blank"> **OpenXR.Loader**</a> es la manera más fácil de hacer referencia a un cargador de OpenXR creado previamente .DLL la solución Visual Studio C++.  Esto le dará acceso a las características principales de OpenXR 1.0, además de las extensiones `KHR` `EXT` y `MSFT` publicadas.

Para agregar una referencia de paquete NuGet OpenXR.Loader a la solución Visual Studio C++:
1. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto que usará OpenXR y seleccione **Administrar NuGet paquetes...**.
2. Cambie a la **pestaña Examinar** y busque **OpenXR.Loader.**
3. Seleccione el **paquete OpenXR.Loader** y seleccione Instalar en el panel de detalles de la derecha.
4. Seleccione Aceptar para aceptar los cambios en el proyecto.
5. Agregue `#include <openxr/openxr.h>` a un archivo de código fuente para empezar a usar la API de OpenXR.

Para ver un ejemplo de la API de OpenXR en acción, consulte la aplicación <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">de ejemplo BasicXrApp.</a>

### <a name="include-official-openxr-loader-source"></a>Incluir el origen oficial del cargador de OpenXR

Si quiere compilar el cargador usted mismo, por ejemplo, para evitar la carga adicional .DLL, puede extraer los orígenes oficiales del cargador OpenXR de Khronos en el proyecto.  Esto le dará acceso a las características principales de OpenXR 1.0, además de las extensiones `KHR` `EXT` y `MSFT` publicadas.

Para empezar aquí, siga las instrucciones del repositorio <a href="https://github.com/KhronosGroup/OpenXR-SDK" target="_blank">de OpenXR-SDK de Khronos en GitHub</a>.  El proyecto está configurado para compilarse con CMake: si usa MSBuild, deberá copiar el código en su propio proyecto.

## <a name="using-preview-extensions"></a>Uso de extensiones de versión preliminar

Las extensiones enumeradas en el mapa de ruta de extensión son extensiones de proveedor experimentales que se están visualizando `MSFT_preview` para recopilar comentarios. [](openxr.md#roadmap)  Estas extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuye la extensión real.

Si está interesado en probar las extensiones disponibles, siga estos `MSFT_preview` pasos para actualizar el proyecto:
1. Siga cualquiera de los enfoques anteriores para integrar un cargador de OpenXR en el proyecto.
2. Reemplace los encabezados estándar de OpenXR en el proyecto por los encabezados de vista previa del repositorio Mixed Reality <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/openxr_preview/include/openxr" target="_blank">OpenXR</a>en GitHub .

Para activar la compatibilidad con la extensión de versión preliminar en el equipo de HoloLens 2 o de escritorio:
  1. Para asegurarse de que tiene el entorno de ejecución de OpenXR más reciente con todas las extensiones [presentes,](openxr.md#roadmap) inicie  la aplicación store desde el dispositivo o emulador de destino, abra el menú de la esquina superior derecha, seleccione Descargas y actualizaciones y elija **Obtener actualizaciones.** 
  2. Instale la <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicación openXR Herramientas de desarrollo para Windows Mixed Reality</a> desde el Microsoft Store en el dispositivo de destino y ejecutarla.
  3. Vaya a la **pestaña Developer Configuración** (Desarrollador) y habilite Use latest preview OpenXR runtime (Usar la versión preliminar más reciente del entorno de ejecución de **OpenXR).**  Esto habilita el entorno de ejecución de versión preliminar en el dispositivo, que tiene activadas las extensiones de versión preliminar.
     ![Pestaña Herramientas de desarrollo de Herramientas de desarrollo openXR Windows Mixed Reality app Developer Configuración](images/mixed-reality-openxr-developer-tools-settings.png)
  4. Confirme que **la versión** en tiempo de ejecución que se muestra en la pestaña Estado del sistema de  [OpenXR Herramientas de desarrollo for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) coincide con la versión necesaria de las extensiones en versión preliminar que planea probar.  Si es así, debería ver la extensión en la **lista Extensiones.**  Una vez que haya disponible una extensión estable, se quitará su extensión en versión preliminar.<br />
     ![OpenXR Herramientas de desarrollo para Windows Mixed Reality pestaña Estado del sistema de la aplicación](images/mixed-reality-openxr-developer-tools-status.png)

Consulte el <a href="https://github.com/microsoft/OpenXR-MixedReality#openxr-preview-extensions" target="_blank">Mixed Reality de OpenXR</a> para obtener documentación de estas extensiones en versión preliminar y ejemplos de cómo usarlas.

## <a name="troubleshooting"></a>Solución de problemas

Si tiene problemas para empezar a trabajar con el desarrollo de OpenXR, consulte nuestras sugerencias [de solución de problemas.](openxr-troubleshooting.md)