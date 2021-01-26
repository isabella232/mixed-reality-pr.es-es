---
ms.openlocfilehash: b6e75419ef9cdd4595e23e6217ab1b1762cd134e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/20/2021
ms.locfileid: "98605119"
---
# <a name="unity"></a>[Unity](#tab/unity)

![Banner del logotipo de Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a>1. Descargar la última versión

Se recomienda la versión [Unity LTS (soporte técnico a largo plazo)](https://unity3d.com/unity/qa/lts-releases) como la mejor versión para usar al empezar nuevos proyectos, y actualizarla a la revisión más reciente para aprovechar las actualizaciones más estables.
* La recomendación actual es usar **Unity 2019**, que es la compilación LTS necesaria para MRTK v2 que se describe a continuación.
* Si necesita usar una versión diferente de Unity por motivos específicos, Unity admite instalaciones de distintas versiones en paralelo.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importar Mixed Reality Toolkit (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

[Mixed Reality Toolkit](../unity/mrtk-getting-started.md) (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales. El kit de herramientas está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.

Para la instalación, se recomienda que complete la sección Introducción de nuestros recorridos de desarrollo de [HoloLens](../unity/unity-development-overview.md#1-getting-started) o [VR](../unity/unity-development-wmr-overview.md#1-getting-started) seleccionados. Si ya sigue el recorrido de desarrollo de Unity para HoloLens, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](../unity/tutorials/mr-learning-base-01.md).

> [!IMPORTANT]
> Tenga en cuenta que las instrucciones de instalación están destinadas a la combinación estable más reciente de las versiones de MRTK y Unity, que son **MRTK 2.4.0** y **Unity 2019.3.15**.

> [!NOTE]
> Si no desea usar MRTK para Unity, tendrá que crear scripts para todas las interacciones y comportamientos.

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Banner de Unity](../images/MRTK-Unity-Banner.png)<br>**Mixed Reality Toolkit - Unity (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

#### <a name="other-tools-optional"></a>Otras herramientas [opcional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bits y componentes de código que no se pueden ejecutar directamente en HoloLens o en cascos envolventes (VR), sino que se emparejan con estos para generar experiencias destinadas a Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Común (GitHub)</a>: colección de componentes y scripts compartidos.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar el equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores.

> [!NOTE]
> Puede desarrollar e implementar las aplicaciones para HoloLens, cascos envolventes de VR o ambos. Asegúrese de cumplir los requisitos siguientes en función de sus necesidades.

#### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configures el equipo para el desarrollo de HoloLens, asegúrate de que cumple con los requisitos del sistema de <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> y de <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si quiere ejecutar la aplicación en un dispositivo HoloLens, debe seguir las [instrucciones de configuración del portal de dispositivos Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si tienes previsto usar el [emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), deberás asegurarte de que el equipo también cumpla con los [requisitos del sistema del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Para empezar a trabajar con el emulador de HoloLens, consulta [Uso del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes (VR) de Windows Mixed Reality, usa los requisitos y las recomendaciones del sistema que aparecen en la siguiente sección.

#### <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>La configuración del modo de desarrollador está atenuada

Si tiene problemas para habilitar el modo de desarrollador en el dispositivo, es posible que no sea el [propietario del dispositivo](/hololens/security-adminless-os). En el modo multiusuario, la persona que usa el dispositivo primero es el propietario del dispositivo: los usuarios posteriores no tendrán los permisos necesarios para habilitar el modo de desarrollador ni realizar otros cambios de configuración. Sin embargo, hay una excepción en la que el primer usuario puede no ser el propietario del dispositivo en un entorno de AutoPilot, como se detalla en la [documentación de seguridad de HoloLens](/hololens/security-adminless-os#device-owner).

Entre las posibles soluciones se incluyen:

* Hacer que el propietario del dispositivo active el modo de desarrollador antes de pasar el dispositivo a otros usuarios o desarrolladores
* Sugerir que su administrador de TI/MDM habilite la [directiva de CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) para el dispositivo específico o para un grupo de dispositivos de desarrollador. 
    * Esta directiva se puede establecer mediante [paquetes de aprovisionamiento](/hololens/hololens-provisioning) o mediante [MDM para dispositivos de HoloLens](/hololens/hololens-mdm-configure)
* Uso del complemento [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Puede aprender más información sobre la administración del dispositivo en **[Introducción a la administración de dispositivos de HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>No puedo implementar mediante USB

Si no puede implementar una aplicación directamente mediante USB, asegúrese de que cumple todos los requisitos de instalación indicados anteriormente y siga nuestro [tutorial detallado](../unity/tutorials/mr-learning-base-02.md#building-your-application-to-your-hololens-2).

#### <a name="immersive-vr-headset-requirements"></a>Requisitos del casco envolvente (VR)

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el *equipo de desarrollo* para cascos envolventes (VR) y puede que se actualicen con regularidad.

>[!WARNING]
>No confundas esto con las [instrucciones de compatibilidad con el hardware del equipo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que describe las *especificaciones del equipo del usuario* de las que debes disponer para desarrollar aplicaciones o juegos con destino a cascos envolventes.

Si el equipo de desarrollo para cascos envolventes no dispone de una HDMI completa o de puertos USB 3.0, necesitarás [adaptadores](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los cascos.

Existen en la actualidad [problemas conocidos](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente en portátiles que tienen gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Procesador</td><td> <b>Portátil:</b> Intel Mobile Core i5 de con CPU de séptima generación, de doble núcleo con Hyper Threading <b>Dispositivo de escritorio:</b> Intel Desktop i5 con CPU de sexta generación, de doble núcleo con Hyper Threading <b>O</b> AMD FX4350 4.2Ghz Quad-Core equivalente</td><td> <b>Dispositivo de escritorio:</b> Intel Desktop i7 de sexta generación (6 núcleos) <b>O</b> AMD Ryzen 5 1600 (6 núcleos, 12 subprocesos)</td>
</tr><tr>
<td> GPU</td><td> <b>Portátil:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) con GPU compatible con DX12 equivalente o superior <b>Dispositivo de escritorio:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) con GPU compatible con DX12 equivalente o superior</td><td><b>Dispositivo de escritorio:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) con GPU compatible con DX12 equivalente o superior</td>
</tr><tr>
<td> Versión de WDDM del controlador de GPU</td><td colspan="2"> Controlador WDDM 2.2</td>
</tr><tr>
<td> Potencia de diseño térmico</td><td colspan="2"> 15 W o más</td>
</tr><tr>
<td> Puertos de pantalla gráfica</td><td colspan="2"> 1 puerto de pantalla gráfica disponible para casco de realidad mixta (HDMI 1.4 o DisplayPort 1.2 para cascos de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para cascos de 90 Hz)</td>
</tr><tr>
<td> Resolución de pantalla</td><td colspan="2"> Solución: SVGA (800 x 600) o con mayor profundidad de bits: 32 bits de color por píxel</td>
</tr><tr>
<td> Memory</td><td> 8 GB de RAM o más</td><td> 16 GB de RAM o más</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;Espacio libre adicional de 10 GB</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) <b>Nota: el USB debe proporcionar un mínimo de 900 mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de los accesorios)</td>
</tr>
</table>

Si no está familiarizado con el desarrollo de MRTK con Unity, le recomendamos seguir nuestro recorrido de desarrollo de Unity seleccionado:

> [!div class="nextstepaction"]
> [Inicio del recorrido de Unity para HoloLens](../unity/unity-development-overview.md)

> [!div class="nextstepaction"]
> [Inicio del recorrido de Unity para VR](../unity/unity-development-wmr-overview.md)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si ya sigue el recorrido de puntos de control de desarrollo de Unity para HoloLens que hemos diseñado, su siguiente tarea es completar nuestra serie de tutoriales de HoloLens 2.

> [!div class="nextstepaction"]
> [Serie de tutoriales de HoloLens 2](../unity/tutorials/mr-learning-base-01.md)

Si está siguiendo el recorrido de Unity para VR, su siguiente tarea consiste en configurar el proyecto.

> [!div class="nextstepaction"]
> [Configuración del proyecto para WMR](../unity/configure-unity-project.md)

Puede volver a los puntos de control de desarrollo de Unity para [HoloLens](../unity/unity-development-overview.md#1-getting-started) y [VR](../unity/unity-development-wmr-overview.md#1-getting-started) en cualquier momento.

# <a name="unreal"></a>[Unreal](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a>1. Descargar la última versión

Se recomienda instalar [Unreal Engine, versión 4.25 ](https://docs.unrealengine.com//GettingStarted/Installation/index.html) o posterior, para aprovechar al máximo la compatibilidad integrada de HoloLens.

### <a name="2-import-mixed-reality-toolkit-mrtk"></a>2. Importar Mixed Reality Toolkit (MRTK)
![MRTK](../../design/images/MRTK_UX_Hero.png)

Mixed Reality Toolkit (MRTK) es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta. MRTK proporciona un sistema de entrada multiplataforma, componentes fundamentales y bloques de creación comunes para interacciones espaciales. El kit de herramientas está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR.

Para la instalación, le recomendamos que complete la [sección Introducción](../unreal/unreal-development-overview.md#1-getting-started) de nuestro [recorrido de desarrollo de Unreal](../unreal/unreal-development-overview.md) seleccionado. Si ya sigue el recorrido de desarrollo de Unreal, finalice el resto de los pasos de configuración que se indican a continuación y continúe con los [tutoriales de Introducción a HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md).

:::row:::
    :::column:::
        <a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Imagen del logotipo de Unity](../images/MRTK-Unreal-Banner.png)<br>**Mixed Reality Toolkit - Unreal (GitHub)** </a><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> Si no desea usar MRTK para Unreal, tendrá que crear scripts para todas las interacciones y comportamientos.

#### <a name="other-tools-optional"></a>Otras herramientas [opcional]
* <a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a>: bits y componentes de código que no se pueden ejecutar directamente en HoloLens o en cascos envolventes (VR), sino que se emparejan con estos para generar experiencias destinadas a Windows Mixed Reality.
* <a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Común (GitHub)</a>: Colección de componentes y scripts compartidos.

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a>3. Configurar el equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores.

> [!NOTE]
> Puede desarrollar e implementar las aplicaciones para HoloLens, cascos envolventes de VR o ambos. Asegúrese de cumplir los requisitos siguientes en función de sus necesidades.

#### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configure el equipo para el desarrollo de HoloLens, asegúrese de cumplir con los requisitos del sistema de [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) y <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si quiere ejecutar la aplicación en un dispositivo HoloLens, debe seguir las [instrucciones de configuración del portal de dispositivos Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si tienes previsto usar el [emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), deberás asegurarte de que el equipo también cumpla con los [requisitos del sistema del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes (VR) de Windows Mixed Reality, usa los requisitos y las recomendaciones del sistema que aparecen en la siguiente sección.

#### <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>La configuración del modo de desarrollador está atenuada

Si tiene problemas para habilitar el modo de desarrollador en el dispositivo, es posible que no sea el [propietario del dispositivo](/hololens/security-adminless-os). En el modo multiusuario, la persona que usa el dispositivo primero es el propietario del dispositivo: los usuarios posteriores no tendrán los permisos necesarios para habilitar el modo de desarrollador ni realizar otros cambios de configuración. Sin embargo, hay una excepción en la que el primer usuario puede no ser el propietario del dispositivo en un entorno de AutoPilot, como se detalla en la [documentación de seguridad de HoloLens](/hololens/security-adminless-os#device-owner).

Entre las posibles soluciones se incluyen:

* Hacer que el propietario del dispositivo active el modo de desarrollador antes de pasar el dispositivo a otros usuarios o desarrolladores
* Sugerir que su administrador de TI/MDM habilite la [directiva de CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) para el dispositivo específico o para un grupo de dispositivos de desarrollador. 
    * Esta directiva se puede establecer mediante [paquetes de aprovisionamiento](/hololens/hololens-provisioning) o mediante [MDM para dispositivos de HoloLens](/hololens/hololens-mdm-configure)
* Uso del complemento [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Puede aprender más información sobre la administración del dispositivo en **[Introducción a la administración de dispositivos de HoloLens](/hololens/hololens-csp-policy-overview)** .

##### <a name="i-cant-deploy-over-usb"></a>No puedo implementar mediante USB

Si no puede implementar una aplicación directamente mediante USB, asegúrese de que cumple todos los requisitos de instalación indicados anteriormente y siga nuestro [tutorial detallado](../unreal/tutorials/unreal-uxt-ch6.md).

#### <a name="immersive-vr-headset-requirements"></a>Requisitos del casco envolvente (VR)

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el *equipo de desarrollo* para cascos envolventes (VR) y puede que se actualicen con regularidad.

>[!WARNING]
>No confundas esto con las [instrucciones de compatibilidad con el hardware del equipo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que describe las *especificaciones del equipo del usuario* de las que debes disponer para desarrollar aplicaciones o juegos con destino a cascos envolventes.

Si el equipo de desarrollo para cascos envolventes no dispone de una HDMI completa o de puertos USB 3.0, necesitarás [adaptadores](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los cascos.

Existen en la actualidad [problemas conocidos](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente en portátiles que tienen gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Procesador</td><td> <b>Portátil:</b> Intel Mobile Core i5 de con CPU de séptima generación, de doble núcleo con Hyper Threading <b>Dispositivo de escritorio:</b> Intel Desktop i5 con CPU de sexta generación, de doble núcleo con Hyper Threading <b>O</b> AMD FX4350 4.2Ghz Quad-Core equivalente</td><td> <b>Dispositivo de escritorio:</b> Intel Desktop i7 de sexta generación (6 núcleos) <b>O</b> AMD Ryzen 5 1600 (6 núcleos, 12 subprocesos)</td>
</tr><tr>
<td> GPU</td><td> <b>Portátil:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) con GPU compatible con DX12 equivalente o superior <b>Dispositivo de escritorio:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) con GPU compatible con DX12 equivalente o superior</td><td><b>Dispositivo de escritorio:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) con GPU compatible con DX12 equivalente o superior</td>
</tr><tr>
<td> Versión de WDDM del controlador de GPU</td><td colspan="2"> Controlador WDDM 2.2</td>
</tr><tr>
<td> Potencia de diseño térmico</td><td colspan="2"> 15 W o más</td>
</tr><tr>
<td> Puertos de pantalla gráfica</td><td colspan="2"> 1 puerto de pantalla gráfica disponible para casco de realidad mixta (HDMI 1.4 o DisplayPort 1.2 para cascos de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para cascos de 90 Hz)</td>
</tr><tr>
<td> Resolución de pantalla</td><td colspan="2"> Solución: SVGA (800 x 600) o con mayor profundidad de bits: 32 bits de color por píxel</td>
</tr><tr>
<td> Memory</td><td> 8 GB de RAM o más</td><td> 16 GB de RAM o más</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;Espacio libre adicional de 10 GB</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) <b>Nota: el USB debe proporcionar un mínimo de 900 mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de los accesorios)</td>
</tr>
</table>

Si no está familiarizado con el desarrollo de MRTK con Unreal, le recomendamos seguir nuestro recorrido de desarrollo de Unreal seleccionado:

> [!div class="nextstepaction"]
> [Inicio del recorrido de Unreal](../unreal/unreal-development-overview.md)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de este punto de control de desarrollo de Unreal que hemos diseñado, su siguiente tarea es completar nuestra serie de tutoriales de HoloLens 2.

> [!div class="nextstepaction"]
> [Serie de tutoriales de HoloLens 2](../unreal/tutorials/unreal-uxt-ch1.md)

Puede volver a los [puntos de control de desarrollo de Unreal](../unreal/unreal-development-overview.md#1-getting-started) en cualquier momento.

# <a name="native-openxr"></a>[Nativo (OpenXR)](#tab/native)

 ![Desarrollo de aplicaciones nativas](../images/native_logo_banner.png)

El desarrollo nativo en OpenXR no tiene un motor que descargar. Puede encontrar todo lo necesario para empezar a desarrollar en el documento [Introducción a OpenXR](../native/openxr-getting-started.md).

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a>1. Configurar el equipo para el desarrollo de realidad mixta

El SDK de Windows 10 funciona mejor en el sistema operativo Windows 10. Este SDK también es compatible con: Windows 8.1, Windows 8, Windows 7, Windows Server 2012 y Windows Server 2008 R2. Ten en cuenta que no todas las herramientas son compatibles con sistemas operativos anteriores.

#### <a name="for-hololens-development"></a>Para el desarrollo de HoloLens

Cuando configure el equipo para el desarrollo de HoloLens, asegúrese de cumplir con los requisitos del sistema de <a href="//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>. Si quiere ejecutar la aplicación en un dispositivo HoloLens, debe seguir las [instrucciones de configuración del portal de dispositivos Windows](../platform-capabilities-and-apis/using-the-windows-device-portal.md#setting-up-hololens-to-use-windows-device-portal). Si tienes previsto usar el [emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md), deberás asegurarte de que el equipo también cumpla con los [requisitos del sistema del emulador de HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-emulator-system-requirements).

Si tienes previsto desarrollar aplicaciones para HoloLens y para los cascos envolventes (VR) de Windows Mixed Reality, usa los requisitos y las recomendaciones del sistema que aparecen en la siguiente sección.

> [!NOTE]
> Puede desarrollar e implementar las aplicaciones para HoloLens, cascos envolventes de VR o ambos. Asegúrese de cumplir los requisitos siguientes en función de sus necesidades.

#### <a name="hololens-troubleshooting"></a>Solución de problemas de HoloLens

##### <a name="setting-developer-mode-is-grayed-out"></a>La configuración del modo de desarrollador está atenuada

Si tiene problemas para habilitar el modo de desarrollador en el dispositivo, es posible que no sea el [propietario del dispositivo](/hololens/security-adminless-os). En el modo multiusuario, la persona que usa el dispositivo primero es el propietario del dispositivo: los usuarios posteriores no tendrán los permisos necesarios para habilitar el modo de desarrollador ni realizar otros cambios de configuración. Sin embargo, hay una excepción en la que el primer usuario puede no ser el propietario del dispositivo en un entorno de AutoPilot, como se detalla en la [documentación de seguridad de HoloLens](/hololens/security-adminless-os#device-owner).

Entre las posibles soluciones se incluyen:

* Hacer que el propietario del dispositivo active el modo de desarrollador antes de pasar el dispositivo a otros usuarios o desarrolladores
* Sugerir que su administrador de TI/MDM habilite la [directiva de CSP ApplicationManagement/AllowDeveloperUnlock](/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock) para el dispositivo específico o para un grupo de dispositivos de desarrollador. 
    * Esta directiva se puede establecer mediante [paquetes de aprovisionamiento](/hololens/hololens-provisioning) o mediante [MDM para dispositivos de HoloLens](/hololens/hololens-mdm-configure)
* Uso del complemento [Advanced Recovery Companion (ARC)](/hololens/hololens-recovery)

> [!NOTE]
> Puede aprender más información sobre la administración del dispositivo en **[Introducción a la administración de dispositivos de HoloLens](/hololens/hololens-csp-policy-overview)** .

#### <a name="immersive-vr-headset-requirements"></a>Requisitos del casco envolvente (VR)

>[!NOTE]
>Las instrucciones siguientes son las especificaciones actuales mínimas y recomendadas para el *equipo de desarrollo* para cascos envolventes (VR) y puede que se actualicen con regularidad.

>[!WARNING]
>No confundas esto con las [instrucciones de compatibilidad con el hardware del equipo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), que describe las *especificaciones del equipo del usuario* de las que debes disponer para desarrollar aplicaciones o juegos con destino a cascos envolventes.

Si el equipo de desarrollo para cascos envolventes no dispone de una HDMI completa o de puertos USB 3.0, necesitarás [adaptadores](/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) para conectar los cascos.

Existen en la actualidad [problemas conocidos](/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) con algunas configuraciones de hardware, especialmente en portátiles que tienen gráficos híbridos.

<table>
<tr>
<th></th><th> Mínimo</th><th> Recomendado</th>
</tr><tr>
<td> Procesador</td><td> <b>Portátil:</b> Intel Mobile Core i5 de con CPU de séptima generación, de doble núcleo con Hyper Threading <b>Dispositivo de escritorio:</b> Intel Desktop i5 con CPU de sexta generación, de doble núcleo con Hyper Threading <b>O</b> AMD FX4350 4.2Ghz Quad-Core equivalente</td><td> <b>Dispositivo de escritorio:</b> Intel Desktop i7 de sexta generación (6 núcleos) <b>O</b> AMD Ryzen 5 1600 (6 núcleos, 12 subprocesos)</td>
</tr><tr>
<td> GPU</td><td> <b>Portátil:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) con GPU compatible con DX12 equivalente o superior <b>Dispositivo de escritorio:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) con GPU compatible con DX12 equivalente o superior</td><td><b>Dispositivo de escritorio:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) con GPU compatible con DX12 equivalente o superior</td>
</tr><tr>
<td> Versión de WDDM del controlador de GPU</td><td colspan="2"> Controlador WDDM 2.2</td>
</tr><tr>
<td> Potencia de diseño térmico</td><td colspan="2"> 15 W o más</td>
</tr><tr>
<td> Puertos de pantalla gráfica</td><td colspan="2"> 1 puerto de pantalla gráfica disponible para casco de realidad mixta (HDMI 1.4 o DisplayPort 1.2 para cascos de 60 Hz, HDMI 2.0 o DisplayPort 1.2 para cascos de 90 Hz)</td>
</tr><tr>
<td> Resolución de pantalla</td><td colspan="2"> Solución: SVGA (800 x 600) o con mayor profundidad de bits: 32 bits de color por píxel</td>
</tr><tr>
<td> Memory</td><td> 8 GB de RAM o más</td><td> 16 GB de RAM o más</td>
</tr><tr>
<td> Almacenamiento</td><td colspan="2"> &gt;Espacio libre adicional de 10 GB</td>
</tr><tr>
<td> Puertos USB</td><td colspan="2"> 1 puerto USB disponible para casco de realidad mixta (USB 3.0 Type-A) <b>Nota: el USB debe proporcionar un mínimo de 900 mA</b></td>
</tr><tr>
<td> Bluetooth</td><td colspan="2"> Bluetooth 4.0 (para la conectividad de los accesorios)</td>
</tr>
</table>

Si no está familiarizado con el desarrollo nativo con MRTK, le recomendamos seguir nuestro recorrido de desarrollo nativo seleccionado:

> [!div class="nextstepaction"]
> [Inicio del recorrido nativo](../native/directx-development-overview.md)

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de puntos de control de desarrollo nativo que hemos diseñado, su siguiente tarea es configurar el entorno de desarrollo de HoloLens 2.

> [!div class="nextstepaction"]
> [Configuración de HoloLens 2](../native/openxr-getting-started.md#getting-started-with-openxr-for-hololens-2)

Puede volver a los [puntos de control de desarrollo nativo](../native/directx-development-overview.md#1-getting-started) en cualquier momento.