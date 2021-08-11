---
title: Notas de la versión (agosto de 2016)
description: Manténgase al día con las notas de la HoloLens de lanzamiento de Windows 10 anniversary release for Fall 2016 (Versión de aniversario de Windows 10 para el año 2016).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, notas de la versión, sistema operativo, plataforma, características, conjunto comercial
ms.openlocfilehash: 2cb6153877b27ce0e1260696447bd4c5c851c6f00a20a7889b855c5646e8871f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202470"
---
# <a name="release-notes---august-2016"></a>Notas de la versión (agosto de 2016)

El HoloLens escucha los comentarios de los desarrolladores de la Windows Programa Insider priorizar nuestro trabajo. Continúe para [enviarnos comentarios a](/windows/mixed-reality/give-us-feedback) través de los Centro de opiniones, los foros para desarrolladores [y](https://forums.hololens.com) Twitter a [través @HoloLens de ](https://twitter.com/hololens). Como Windows 10 la actualización de aniversario, el equipo de HoloLens está encantado de mejorar aún más la experiencia holográfica. En esta actualización, nos centramos en correcciones importantes, mejoras e introducción a las características solicitadas por las empresas y disponibles en el Microsoft HoloLens Commercial Suite.

**Versión más reciente:** Windows holographic de agosto de 2016 (**10.0.14393.0**, Windows 10 anniversary release)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

Para actualizar a la versión  [actual,](/windows/mixed-reality/updating-hololens)abra la aplicación Configuración, vaya a Actualizar & Security y, *a* continuación, seleccione el botón *Buscar* actualizaciones.

## <a name="new-features"></a>Nuevas características

**Asociar a la depuración de** HoloLens ahora admite la depuración de asociación a proceso. Puede usar Visual Studio 2015 Update 3 para conectarse a una aplicación en ejecución en un HoloLens y empezar a [depurarla.](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-visual-studio#debugging-an-installed-or-running-app) Esto funciona sin necesidad de implementar desde un Visual Studio proyecto.

**Actualización HoloLens Emulator** También hemos publicado una versión actualizada de la HoloLens Emulator.

**Compatibilidad con Gamepad** Ahora puede emparejar y usar Bluetooth para juegos con HoloLens. El recientemente publicado Xbox Wireless Controller S ofrece Bluetooth funcionalidades y se puede usar para reproducir sus aplicaciones y juegos favoritos habilitados para el controlador para juegos. Se [debe aplicar una](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) actualización del controlador para poder conectar el controlador inalámbrico de Xbox S con HoloLens. [XInput](/windows/win32/xinput/xinput-game-controller-apis-portal) y Windows admiten el controlador inalámbrico S de [Xbox. API de Gaming.Input.](/uwp/api/Windows.Gaming.Input) Puede acceder a más modelos Bluetooth controladores a través del [Windows. Gaming.Input](/uwp/api/Windows.Gaming.Input) API.

## <a name="improvements-and-fixes"></a>Mejoras y correcciones

Estamos sincronizados con el resto de la actualización de aniversario de Windows 10, por lo que además de las correcciones específicas de HoloLens, también recibe todas las novedades de la actualización de Windows para aumentar la confiabilidad y el rendimiento de la plataforma. Sus comentarios son muy valiosos y tienen prioridad para las correcciones de la versión.

Hemos mejorado las siguientes experiencias:
* experiencias de inicio de sesión.
* se unen a los lugares de trabajo.
* eficacia de energía para las transiciones de estado de energía del dispositivo.
* estabilidad con Mixed Reality captures.
* confiabilidad de Bluetooth conectividad
* persistencia de hologramas en escenarios de varias aplicaciones.

Hemos corregido los siguientes problemas:
* los Visual Studio de perfiles y el depurador de gráficos no se pueden conectar.
* las & los documentos no se muestran en el explorador de archivos en el portal del dispositivo.
* La barra de la aplicación puede parpadear cuando el cursor se coloca encima de él mientras está en modo de ajuste.
* Cuando está en modo de ajuste, el cursor de punto de mirada con los ojos cambiará al cursor de 4 flechas más lentamente.
* "Hey Cortana play music" no se inicia Groove.
* después de la actualización anterior, el mensaje "Ir a casa" no muestra el panel de pines correctamente.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Introducción a Microsoft HoloLens Commercial Suite

El Microsoft HoloLens Commercial Suite está listo para la implementación empresarial. Hemos agregado varias características comerciales muy [solicitadas](/windows/mixed-reality/commercial-features) de nuestros primeros socios comerciales.

Póngase en contacto con el administrador de cuentas de Microsoft local para comprar Microsoft HoloLens Commercial Suite.

### <a name="key-commercial-features"></a>Características comerciales clave 

* **Pantalla completa**. Con HoloLens pantalla completa, puede limitar las aplicaciones que se ejecutarán para habilitar la demostración o mostrar experiencias.<br>
  ![Con el modo de pantalla completa, HoloLens se inicia directamente en la aplicación que prefiera.](images/201608-kioskmode-400px.png)
* **Administración de dispositivos móviles (MDM) para HoloLens**. El departamento de TI puede administrar varios dispositivos HoloLens simultáneamente mediante soluciones como Microsoft Intune. Puede administrar la configuración, seleccionar aplicaciones para instalar y establecer configuraciones de seguridad adaptadas a las necesidades de su organización.<br>
  ![Mobile Administración de dispositivos en HoloLens proporciona administración de dispositivos de nivel empresarial en varios dispositivos.](images/201608-enterprisemanagement-400px.png)
* **Windows Update para empresas**. Actualizaciones controladas del sistema operativo para dispositivos y compatibilidad con la rama de mantenimiento a largo plazo.
* **Seguridad de los datos**. El cifrado de datos de BitLocker está habilitado en HoloLens para proporcionar el mismo nivel de protección de seguridad que cualquier otro dispositivo Windows.
* **Acceso al trabajo**. Cualquier persona de su organización puede conectarse de forma remota a la red corporativa a través de una red privada virtual en HoloLens. HoloLens también puede acceder a redes Wi-Fi que requieren credenciales.
* **Microsoft Store para Empresas**. El departamento de TI también puede configurar una tienda privada empresarial, que contiene solo las aplicaciones de su empresa para su uso HoloLens cliente. Distribuya de manera segura el software empresarial a un grupo seleccionado de usuarios empresariales.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition frente a Commercial Suite

<table>
<tr>
<th>Características</th><th>Development Edition</th><th>Conjunto de aplicaciones comercial</th>
</tr><tr>
<td>Cifrado de dispositivo (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Red privada virtual (VPN)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal#kiosk-mode">Pantalla completa</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Administración e implementación</th>
</tr><tr>
<td>Administración de dispositivos móviles (MDM)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Posibilidad de bloquear la anulación de la inscripción</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Acceso corporativo basado en Wi-Fi certificado</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (consumidor)</td><td style="text-align: center;">Consumidor</td><td style="text-align: center;">Filtrado a través de MDM</td>
</tr><tr>
<td><a href="/microsoft-store/working-with-line-of-business-apps">Portal de Store para empresas</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Seguridad e identidad</th>
</tr><tr>
<td>Iniciar sesión con Azure Active Directory (AAD)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Iniciar sesión con la cuenta Microsoft (MSA)</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Credenciales de próxima generación con desbloqueo de PIN</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows-hardware/design/device-experiences/oem-secure-boot">Arranque seguro</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> Mantenimiento y soporte técnico</th>
</tr><tr>
<td>Actualizaciones automáticas del sistema a medida que llegan</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="/windows/deployment/update/waas-manage-updates-wufb">Windows Update para empresas</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Rama de mantenimiento a largo plazo</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>Notas de la versión anterior
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Problemas conocidos de HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Características comerciales](/windows/mixed-reality/commercial-features)
* [Instalación de las herramientas](/windows/mixed-reality/develop/install-the-tools)
* [Uso del emulador de HoloLens](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)