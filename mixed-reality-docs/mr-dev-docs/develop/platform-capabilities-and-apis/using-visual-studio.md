---
title: Uso de Visual Studio para implementaciones y depuraciones
description: Obtén información sobre cómo crear, depurar e implementar aplicaciones para HoloLens y Windows Mixed Reality con Visual Studio.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, realidad mixta, depurar, implementar
ms.openlocfilehash: 5510646c058f683babff5e9e34dd296f88cd06c3
ms.sourcegitcommit: b4bdac2c4d7315902712ce74fd909fb8383d4bfd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2021
ms.locfileid: "110543231"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a>Uso de Visual Studio para implementaciones y depuraciones

Tanto si usa DirectX como Unity para desarrollar su aplicación de realidad mixta, Visual Studio será una herramienta imprescindible para realizar la depuración y la implementación. En esta sección, aprenderás a:
* Implementar aplicaciones en tu casco envolvente de HoloLens o Windows Mixed Reality a través de Visual Studio.
* Usar el emulador de HoloLens integrado en Visual Studio.
* Depurar aplicaciones de realidad mixta.

## <a name="prerequisites"></a>Requisitos previos

1. Consulta [Instalar las herramientas](../../develop/install-the-tools.md#installation-checklist) para obtener instrucciones de instalación.
2. Crea un proyecto de aplicación universal de Windows en Visual Studio.  Para HoloLens (1.ª generación), usa Visual Studio 2017 o una versión más reciente.  Para Hololens 2, use Visual Studio 2019 16.2 o una versión más reciente. Se admiten los lenguajes C# y C++. (También puedes seguir las instrucciones para [crear una aplicación en Unity](../../develop/unity/tutorials/holograms-100.md)).

## <a name="enabling-developer-mode"></a>Habilitar el modo de desarrollador

Para empezar, habilita el **Modo de desarrollador** en tu dispositivo, para que Visual Studio pueda conectarse a él.

### <a name="hololens"></a>HoloLens

1. Enciende tu HoloLens y colócate el dispositivo.
2. Realice el [gesto de inicio](../../design/system-gesture.md) para iniciar el menú principal.
3. Selecciona el icono **Configuración** para iniciar la aplicación en tu entorno.
4. Selecciona el elemento de menú **Actualizar**.
5. Selecciona el elemento de menú **Para desarrolladores**.
6. Habilite **Usar las funciones de desarrollador** para implementar aplicaciones de Visual Studio en HoloLens. Si el dispositivo ejecuta Windows Holographic, versión 21H1 o posterior, habilite también **Detección de dispositivos**.
7. Opcional: Desplácese hacia abajo y habilite el **Portal de dispositivos**, que le permitirá conectarse al [Portal de dispositivos Windows](using-the-windows-device-portal.md) en HoloLens desde un explorador web.

### <a name="windows-pc"></a>Equipo Windows

Si trabaja con un casco de Windows Mixed Reality conectado al equipo, debe habilitar el **Modo de desarrollador** en el equipo.
1. Ve a **Configuración**.
2. Selecciona **Actualización y seguridad**.
3. Selecciona **Para desarrolladores**.
4. Habilite el **Modo de desarrollador**, lea el aviso de declinación de responsabilidades para la configuración elegida y, a continuación, haga clic en Sí para aceptar el cambio.

## <a name="deploying-a-hololens-app-over-wi-fi"></a>Implementación de una aplicación de HoloLens a través de Wi-Fi 

Configure el proyecto de Visual Studio con las siguientes propiedades:

1. Seleccione las opciones de compilación de las aplicaciones:
    * En el caso de los proyectos de Unity, elija **Versión** o **Maestro**. 
    * Para todos los demás proyectos, elija **Versión**.

> [!NOTE]
> Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Seleccione la configuración de compilación en función del dispositivo:

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Selecciona **Máquina remota** en el menú desplegable de destino de la implementación.

![Destino de implementación de la máquina remota en Visual Studio](images/remotemachinesetting_arm64.png)

A continuación, debe establecer la conexión remota. Para proyectos de C++ y JavaScript, ve a **Proyecto > Propiedades > Propiedades de configuración > Depuración**. Si está trabajando en un proyecto de C#, debe aparecer automáticamente un cuadro de diálogo.

> [!NOTE]
> Si el cuadro de diálogo de conexión remota no aparece en el proyecto de C#, puede abrirlo manualmente desde **Propiedades > Depurar**.

1. Escribe la dirección IP del dispositivo en el campo **Dirección** o **Nombre de la máquina**. 
    * Puede encontrar la dirección IP de su dispositivo HoloLens en **Configuración > Red e Internet > Opciones avanzadas**.
    * Siempre se recomienda especificar manualmente la dirección IP en lugar de depender de la característica Detección automática.

2. Establezca **Modo de autenticación** en **Universal (protocolo sin cifrar)** .

  ![Cuadro de diálogo de conexión remota en Visual Studio](images/remotedeploy.png)

3. Compile, implemente y depure la aplicación en función de sus necesidades:
    * Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.
    * Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

4. La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

## <a name="deploying-a-hololens-app-over-usb"></a>Implementación de una aplicación de HoloLens a través de USB 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. Seleccione las opciones de compilación de las aplicaciones:
    * En el caso de los proyectos de Unity, elija **Versión** o **Maestro**. 
    * Para todos los demás proyectos, elija **Versión**.

> [!NOTE]
> Puede encontrar definiciones completas para cada opción de compilación en [Exportación y creación de soluciones de Visual Studio](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).

2. Seleccione la configuración de compilación en función del dispositivo:

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Selecciona **Dispositivo** en el menú desplegable de destino de la implementación.

![Implementación de dispositivos en Visual Studio](images/buildsettingsusbdeploy_arm64.png)

4. Compile, implemente y depure la aplicación en función de sus necesidades:
    * Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.
    * Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)</br>

5. La primera vez que implemente una aplicación en HoloLens desde el equipo, deberá escribir un PIN. Sigue las instrucciones de la sección **Emparejamiento del dispositivo** que hay a continuación.

> [!NOTE]
> Si observa un tiempo de retardo considerable en la implementación de aplicaciones a través de USB, se recomienda usar las [instrucciones para la máquina remota](#deploying-a-hololens-app-over-wi-fi) de la sección anterior.

## <a name="deploying-an-app-to-the-hololens-emulator"></a>Implementación de una aplicación en el emulador de HoloLens

1. Asegúrese de haber **[instalado el emulador de HoloLens 2 o HoloLens (1.ª generación)](../install-the-tools.md#installation-checklist)**
2. Seleccione la configuración de compilación y el emulador en función del dispositivo:

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. Compile, implemente y depure la aplicación en función de sus necesidades:
    * Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.
    * Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.

![Iniciar sin depuración en Visual Studio](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a>Implementación de una aplicación de VR en el equipo local 

A la hora de usar un casco envolvente de Windows Mixed Reality que se conecte al equipo o al [simulador de Mixed Reality](using-the-windows-mixed-reality-simulator.md):
1. Selecciona una configuración de compilación **x86** o **x64** para tu aplicación.
2. Selecciona **Máquina local** en el menú desplegable de destino de la implementación.
3. Compile, implemente y depure la aplicación en función de sus necesidades:
    * Selecciona **Depuración > Iniciar depuración** para implementar tu aplicación e iniciar la depuración.
    * Seleccione **Compilar > Implementar** para compilarla e implementarla sin depuración.

## <a name="pairing-your-device"></a>Emparejamiento del dispositivo

La primera vez que implemente una aplicación desde Visual Studio en HoloLens, deberá escribir un PIN. Para generar un PIN en HoloLens, inicie la aplicación Configuración, vaya a **Actualizar > Para desarrolladores** y pulse **Emparejar**. Cuando el PIN se muestre en HoloLens, escríbalo en Visual Studio. Una vez completado el emparejamiento, pulsa **Listo** en HoloLens para descartar el cuadro de diálogo. En ese momento, el equipo estará emparejado con HoloLens y podrá implementar aplicaciones automáticamente. Repita estos pasos para todos los equipos que se usen para implementar aplicaciones en HoloLens.

Para desemparejar HoloLens de todos los equipos emparejados:
* Inicie la aplicación de **Configuración**, vaya a **Actualizar > Para desarrolladores** y pulse **Borrar**.

## <a name="graphics-debugger-for-hololens-1st-gen"></a>Depurador de gráficos para HoloLens (1.ª generación)

Las herramientas de Diagnóstico de gráficos de Visual Studio son muy útiles a la hora de escribir y optimizar una aplicación holográfica. Consulta [Diagnóstico de gráficos de Visual Studio en MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) para obtener todos los detalles.

**Para iniciar el depurador de gráficos**
1. Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.
2. Ve a **Depurar > Gráficos > Iniciar diagnóstico**.
3. Es posible que la primera vez que realice un diagnóstico con HoloLens obtenga un error de tipo "Acceso denegado". Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.

## <a name="profiling"></a>Generación de perfiles

Las herramientas de generación de perfiles de Visual Studio te permiten analizar el rendimiento y el uso de recursos de tu aplicación. Esto incluye herramientas para optimizar el uso de la CPU, la memoria, los gráficos y la red. Consulta [Ejecutar las herramientas de diagnóstico sin depuración en MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) para obtener todos los detalles.

**Para iniciar las herramientas de generación de perfiles con HoloLens**
1. Sigue las instrucciones anteriores para usar un dispositivo o un emulador como destino.
2. Ve a **Depurar > Iniciar herramientas de diagnóstico sin depuración...** .
3. Selecciona las herramientas que quieres utilizar.
4. Seleccione **Inicio**.
5. Es posible que la primera vez que realice un diagnóstico sin depuración con HoloLens obtenga un error de tipo "Acceso denegado". Reinicie HoloLens para permitir que se apliquen los permisos actualizados y vuelva a intentarlo.

## <a name="debugging-an-installed-or-running-app"></a>Depuración de una aplicación instalada o en ejecución

Puede usar Visual Studio para depurar una aplicación universal de Windows instalada sin implementarla desde un proyecto de Visual Studio. Esto resulta útil si quiere depurar un paquete de la aplicación instalado o si quiere depurar una aplicación que ya se esté ejecutando.
1. Ve a **Depurar > Otros destinos de depuración > Depurar paquete de aplicaciones instalado**.
2. Selecciona el destino **Máquina remota** para HoloLens o **Máquina local** para los cascos envolventes.
3. Escribe la **dirección IP** de tu dispositivo.
4. Selecciona el modo de autenticación **Universal**.
5. En la ventana se muestran las aplicaciones en ejecución e inactivas. Elige la que quieras depurar.
6. Elige el tipo de código que quieras depurar (administrado, nativo, mixto).
7. Seleccione **Adjuntar** o **Iniciar**.

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo de Unity que hemos diseñado, significa que ya se encuentra a la mitad de la fase de implementación. Desde aquí, puede continuar con el siguiente tema:

> [!div class="nextstepaction"]
> [Implementación en el emulador de HoloLens](using-the-hololens-emulator.md)

O bien puede ir directamente a agregar servicios avanzados:

> [!div class="nextstepaction"]
> [Servicios avanzados](../../develop/unity/unity-development-overview.md#5-adding-services)

Puede volver a los [puntos de control de desarrollo de Unity](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) en cualquier momento.

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](../install-the-tools.md)
* [Uso del emulador de HoloLens](using-the-hololens-emulator.md)
* [Implementación y depuración de aplicaciones para la Plataforma universal de Windows (UWP)](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [Habilitar el dispositivo para el desarrollo](/windows/uwp/get-started/enable-your-device-for-development)
