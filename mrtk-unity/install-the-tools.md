---
title: Instalación de las herramientas
description: MRTK-Unity, página de documentación de instalación de las herramientas
author: polar-kev
ms.author: kesemple
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, realidad mixta, desarrollo, MRTK, kit de herramientas de realidad mixta, instalación, actualización, herramientas, introducción, conceptos básicos, unity, visual studio, kit de herramientas, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, instalación, Windows, HoloLens, emulador
ms.openlocfilehash: 117b34ae858e789b1366ce5338e23b8f366377ae
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550565"
---
# <a name="install-the-tools"></a>Instalación de las herramientas

Consigue las herramientas necesarias para compilar aplicaciones para Microsoft HoloLens y los cascos envolventes de Windows Mixed Reality (VR). No hay ningún SDK independiente para el desarrollo con Windows Mixed Reality. Tendrás que usar Visual Studio con el SDK de Windows 10.

¿No tienes un dispositivo de realidad mixta? Puede instalar el [emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) para probar algunas funciones de las aplicaciones de realidad mixta sin necesidad de un dispositivo HoloLens. También puede usar el [simulador de Windows Mixed Reality](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator) para probar las aplicaciones de realidad mixta con unos cascos envolventes.

Esta página le guiará por la instalación de las herramientas que necesita para usar MRTK con Unity. Si está interesado en explorar otras plataformas de desarrollo con Mixed Reality, consulte la página [Introducción al desarrollo con Mixed Reality](/windows/mixed-reality/develop/development?tabs=unity).

Puede usar la simulación de entrada de [Mixed Reality Toolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) para probar distintos tipos de interacciones de entrada, como el seguimiento de la mano y el seguimiento ocular.

|SUGERENCIA: Marque esta página como favorita y consúltela periódicamente para estar al día de la versión más reciente de cada herramienta recomendada para el desarrollo con Mixed Reality.|
|---|

## <a name="installation-checklist"></a>Lista de comprobación de la instalación

| Herramienta | Notas |
|---------|---------|
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (vínculo de instalación manual)</a><br><br>Instala la versión más reciente de Windows 10 para que el sistema operativo del equipo coincida con la plataforma para la que vas a compilar las aplicaciones de realidad mixta.  | **Instalación de Windows 10** <br> Puedes instalar la versión más reciente de Windows 10 mediante Windows Update en Configuración o mediante la creación de soportes de instalación a través del vínculo de la columna izquierda. <br><br>Consulta las [notas de la versión actual](/windows/mixed-reality/enthusiast-guide/mixed-reality-software) para más información acerca de las características de realidad mixta más recientes disponibles en cada versión de Windows 10. **Habilita el modo para desarrolladores en el equipo** en Configuración > Actualización y seguridad > Para programadores. <br><br> **Nota para equipos empresariales y de administración corporativa**<br>Si administra el equipo un departamento de TI de la organización, es posible que deba ponerse en contacto con ellos para la actualización. <br><br> **Versiones "N" de Windows**<br> Los cascos envolventes de Windows Mixed Reality no son compatibles con las versiones "N" de Windows. |
| ![Imagen del logotipo de Visual Studio](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 o superior)** (vínculo de instalación)</a> <br><br>Entorno de desarrollo integrado (IDE) completo para Windows, etc. Vas a utilizar Visual Studio para escribir código, depurar, realizar pruebas e implementar. | **Instalación de Visual Studio 2019** <br> Asegúrate de instalar las siguientes cargas de trabajo: <br><br>*● Desarrollo de escritorio con C++*<br>*● Desarrollo para la Plataforma universal de Windows (UWP)*<br><br>En la carga de trabajo de UWP, asegúrate de comprobar el siguiente componente opcional si vas a desarrollar para HoloLens:<br><br>*● Conectividad con dispositivo USB*<br><br>**Nota acerca de Unity**<br>A menos que esté intentando instalar de manera intencionada una versión más reciente (no LTS) de Unity para un propósito específico, le recomendamos que *no* instale la carga de trabajo de Unity como parte de la instalación de Visual Studio y que, en su lugar, instale el flujo **Unity 2019 LTS** como se indica a continuación.<br><br>**Problemas conocidos**<br>Hay algunos problemas conocidos con la depuración de aplicaciones de realidad mixta en Visual Studio 2019, versión 16.0.  Asegúrate de actualizar a **Visual Studio 2019, versión 16.8 o superior**. |
| ![Logotipo de Windows](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**SDK de Windows 10 (10.0.18362.0)** (vínculo de instalación manual)</a> <br><br>Proporciona los encabezados, bibliotecas, metadatos y herramientas más recientes para compilar aplicaciones de Windows 10 en HoloLens 2. | **Para compilar aplicaciones de HoloLens 2, debe instalar Windows SDK, compilación 18362 o posterior.**<br> <br> Si solo va a desarrollar aplicaciones para cascos de Windows Mixed Reality o HoloLens (1.ª generación), puede usar el SDK de Windows que instala Visual Studio 2019. |
| ![Logotipo de Visual Studio](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2154784" target="_blank">**Emulador de HoloLens 2 (Windows Holographic, versión 20H2, actualización de febrero de 2021)** (vínculo de instalación: 10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**Emulador de HoloLens (Gen 1)** (vínculo de instalación: 10.0.17763.134)</a> <br><br>El emulador te permite ejecutar aplicaciones en una imagen de máquina virtual de HoloLens sin necesidad de un dispositivo HoloLens físico.<br> <br> | Consulta [Uso del emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) para más información sobre cómo empezar a trabajar con el emulador.<br> <br> **El sistema debe admitir Hyper-V** para que la instalación del emulador se realice correctamente. Consulta la sección Requisitos del sistema que aparece a continuación para obtener los detalles. <br> <br> **Nota sobre el emulador de HoloLens (1.ª generación)** <br>. Si va a instalar el emulador de HoloLens (1.ª generación) con Visual Studio 2019, debe anular la selección de las plantillas de VS e [instalarlas desde Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX). |

## <a name="unity"></a>Unity

Ahora que tiene Windows 10, Visual Studio y el SDK de Windows 10 listos para usar, vamos a usar Unity como motor con el cual crear.

### <a name="1-download-the-latest-version"></a>1. Descargar la última versión

Se recomienda la versión [Unity LTS (soporte técnico a largo plazo)](https://unity3d.com/unity/qa/lts-releases) como la mejor versión para usar al empezar nuevos proyectos, y actualizarla a la revisión más reciente para aprovechar las actualizaciones más estables.

* La recomendación actual es usar [Unity 2019.4 LTS](https://unity3d.com/unity/qa/lts-releases?version=2019.4). También se admite Unity 2018.4 LTS.
* Si quiere usar las características en versión preliminar de [Mixed Reality OpenXR](/windows/mixed-reality/develop/unity/openxr-getting-started) con MRTK, necesitará Unity 2020.2 o superior.
* Si necesita usar una versión diferente de Unity por motivos específicos, Unity admite instalaciones de distintas versiones en paralelo.

### <a name="2-install-the-mixed-reality-feature-tool"></a>2. Instalar la herramienta de características de Mixed Reality

La [herramienta de características de Mixed Reality](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) es una nueva manera de que los desarrolladores detecten y agreguen paquetes de características de Mixed Reality en proyectos de Unity.

Puede buscar paquetes por nombre o categoría, consultar sus dependencias e incluso ver los cambios propuestos en el archivo de manifiesto de sus proyectos antes de realizar la importación. Una vez que haya validado los paquetes que quiere, la herramienta de características de Mixed Reality los descargará en el proyecto de Unity que elija.

#### <a name="importing-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

Puede descargar el paquete de Mixed Reality Toolkit según las [instrucciones de instalación y uso](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool#system-requirements) y seleccionando el paquete Mixed Reality Toolkit Foundation.

Si prefiere descargar manualmente los paquetes de MRTK desde GitHub, visite la página de la versión en [Mixed Reality Toolkit-Unity (GitHub)](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar el equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores.

| Nota: Puede desarrollar e implementar las aplicaciones para HoloLens, cascos envolventes de VR o ambos. Asegúrese de cumplir los requisitos siguientes en función de sus necesidades. |
|---|

#### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configures el equipo para el desarrollo de HoloLens, asegúrate de que cumple con los requisitos del sistema de [Unity](https://docs.unity3d.com/Manual/system-requirements.html) y de Visual Studio. Si quiere ejecutar la aplicación en un dispositivo HoloLens, debe seguir las [instrucciones de configuración del portal de dispositivos Windows](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#setting-up-hololens-to-use-windows-device-portal). Si tienes previsto usar el [emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator), deberás asegurarte de que el equipo también cumpla con los [requisitos del sistema del emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator#hololens-emulator-system-requirements).

Para empezar a trabajar con el emulador de HoloLens, consulta [Uso del emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes (VR) de Windows Mixed Reality, usa los requisitos y las recomendaciones del sistema que aparecen en la siguiente sección.

### <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

La configuración del modo de desarrollador está atenuada

Si tiene problemas para habilitar el modo de desarrollador en el dispositivo, es posible que no sea el [propietario del dispositivo](/hololens/security-adminless-os). En el modo multiusuario, la persona que usa el dispositivo primero es el propietario del dispositivo: los usuarios posteriores no tendrán los permisos necesarios para habilitar el modo de desarrollador ni realizar otros cambios de configuración. Sin embargo, hay una excepción en la que el primer usuario puede no ser el propietario del dispositivo en un entorno de AutoPilot, como se detalla en la [documentación de seguridad de HoloLens](/hololens/hololens2-compliance).

Entre las posibles soluciones se incluyen:

* Hacer que el propietario del dispositivo active el modo de desarrollador antes de pasar el dispositivo a otros usuarios o desarrolladores
* Sugerir que su administrador de TI/MDM habilite la [directiva de CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) para el dispositivo específico o para un grupo de dispositivos de desarrollador.
Esta directiva se puede establecer mediante [paquetes de aprovisionamiento](/hololens/hololens-provisioning) o mediante [MDM para dispositivos de HoloLens](/hololens/hololens-mdm-configure)
* Uso del complemento [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

| Nota: Puede obtener más información sobre la administración del dispositivo en la introducción a la administración de dispositivos de HoloLens.|
|---|

No puedo implementar mediante USB

Si no puede implementar una aplicación directamente mediante USB, asegúrese de que cumple todos los requisitos de instalación indicados anteriormente y siga nuestro [tutorial detallado](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02#building-your-application-to-your-hololens-2).

Requisitos del casco envolvente (VR)

| Nota: Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el equipo de desarrollo para cascos envolventes (VR), y puede que se actualicen periódicamente.|
|---|

| Advertencia: No confunda esto con las [instrucciones de compatibilidad mínima con el hardware del equipo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que describe las especificaciones del equipo del usuario de las que debes disponer para desarrollar aplicaciones o juegos con destino a cascos envolventes (VR).|
|---|

Si el equipo de desarrollo para cascos envolventes no dispone de una HDMI completa o de puertos USB 3.0, necesitará [adaptadores](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los cascos.

Existen en la actualidad [problemas conocidos](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente en portátiles que tienen gráficos híbridos.

. | Mínima | Recomendado
--- |--- |---
Procesador | Portátil: Intel Mobile Core i5 de con CPU de séptima generación, de doble núcleo con Hyper Threading Dispositivo de escritorio: Intel Desktop i5 con CPU de sexta generación, de doble núcleo con Hyper Threading O AMD FX4350 4.2Ghz Quad-Core equivalente| Dispositivo de escritorio: Intel Desktop i7 de 6.ª generación (6 núcleos) o AMD Ryzen 5 1600 (6 núcleos, 12 subprocesos) | Portátil: NVIDIA GTX 965M, AMD RX 460M (2GB) con GPU compatible con DX12 equivalente o superior Dispositivo de escritorio: NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) con GPU compatible con DX12 equivalente o superior | Dispositivo de escritorio: NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) con GPU compatible con DX12 equivalente o superior
Versión de WDDM del controlador de GPU | Controlador WDDM 2.2
Potencia de diseño térmico | 15 W o más
Puertos de pantalla gráfica | 1 puerto de pantalla gráfica disponible para casco (HDMI 1.4 o DisplayPort 1.2 para cascos de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para cascos de 90 Hz)
Resolución de pantalla | Solución: SVGA (800 x 600) o con mayor profundidad de bits: 32 bits de color por píxel
Memory | 8 GB de RAM o más | 16 GB de RAM o más
Almacenamiento | > 10 GB de espacio libre adicional
Puertos USB | 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) Nota: el USB debe proporcionar un mínimo de 900 mA
Bluetooth | Bluetooth 4.0 (para la conectividad de los accesorios)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Ahora que tiene instaladas las herramientas, se recomienda seguir nuestra serie de tutoriales de MRTK HoloLens 2.
> [!div class="nextstepaction"]
> [Serie de tutoriales de HoloLens 2](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)