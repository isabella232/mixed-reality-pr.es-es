---
title: Instalación de PIX para HoloLens 2
description: Obtenga información sobre cómo instalar LAV para HoloLens 2 dispositivos.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIXEL, capture, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 2e5e66ea5a1a2b68d91213c38d88d815f54a28fa5328ab3b2d93f1e267f6f994
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217392"
---
# <a name="installing-pix-for-hololens-2"></a>Instalación de PIX para HoloLens 2

[HEXADECIMAL](https://devblogs.microsoft.com/pix) es una herramienta de optimización y depuración del rendimiento para aplicaciones directX 12 en Windows. 

## <a name="setup"></a>Configurar

1. Tome la versión más [reciente de]( https://devblogs.microsoft.com/pix/download) LAV desde el equipo host y conecte la HoloLens 2 al equipo a través de un cable USB.

2. Si el HoloLens 2 está en una compilación de [Windows Insider](https://insider.windows.com) o tiene una configuración que interrumpe LAV, [](/hololens/hololens-recovery) vuelva a actualizar el dispositivo para borrar todos los datos.

3. Habilite **el modo de** desarrollador y **Portal de dispositivos**:

* Abra **Configuración** desde Mixed Reality Inicio:

![Captura de pantalla del menú HoloLens con el botón de configuración resaltado](images/pix-img-01.jpg)

* Seleccione **Actualizar & seguridad:**

![Captura de pantalla de la ventana de configuración abierta HoloLens con el botón de actualización y seguridad resaltado](images/pix-img-02.jpg)

* Seleccione **Para desarrolladores:**

![Captura de pantalla de la ventana de seguridad y actualizaciones abierta con el botón para desarrolladores resaltado](images/pix-img-03.jpg)

* Active Usar **características para desarrolladores** **y Habilitar Portal de dispositivos**

![Captura de pantalla de la ventana para desarrolladores abierta en la configuración con el botón Habilitar portal de dispositivos resaltado](images/pix-img-04.jpg)

![Captura de pantalla de la ventana para desarrolladores abierta en la configuración con el botón de alternancia Usar características de desarrollo resaltado](images/pix-img-05.jpg)

* Con el dispositivo aún conectado, activo y con el usuario conectado, inicie Visual Studio.

> [!IMPORTANT]
> Asegúrese de que el dispositivo no está en modo de espera o inactivo. Si tiene problemas con este paso, consulte las Windows Portal de dispositivos [instrucciones](./using-the-windows-device-portal.md).

## <a name="preparing-for-deployment"></a>Preparación para la implementación

1. En Visual Studio, establezca **ARM64** como plataforma y **Dispositivo** como dispositivo:

![Captura de pantalla de la solución Visual Studios con la configuración de plataforma y dispositivo resaltada](images/pix-img-06.png)

2. Cuando Visual Studio le pida un **PIN** del dispositivo:

![Captura de pantalla de la ventana emergente de Visual Studio en la que se solicita el PIN](images/pix-img-07.png)

* Selección **de Configuración** desde Shell
* Seleccione Update & Security (Actualizar **& seguridad).**
* Seleccione **Para desarrolladores y** presione Emparejar en **Detección de dispositivos.** 

![Captura de pantalla de la ventana para desarrolladores abierta en la configuración con la detección de dispositivos resaltada](images/pix-img-08.jpg)

![Captura de pantalla de la ventana emergente del dispositivo de pago con el código de registro resaltado](images/pix-img-09.jpg)

* Escriba el número de PIN generado en Visual Studio

3. Visual Studio implementará la aplicación en el HoloLens 2 conectado, lo que puede tardar unos minutos en función de la aplicación.

## <a name="launching-pix"></a>Inicio de LAN

En primer lugar, Portal de dispositivos para comprobar que la aplicación no se ejecuta en el HoloLens 2. A continuación, inicie LAV, conéctese al dispositivo y seleccione **Inicio:**

![Captura de pantalla de la pantalla principal de la aplicación DESA](images/pix-img-10.png)

* Seleccione **Conectar** en el menú de la izquierda:

![Captura de pantalla del menú del lado izquierdo de la aplicación DE LAV con el botón Conectar resaltado](images/pix-img-11.png)

2. En la **pestaña Equipo,** seleccione **Agregar** y escriba las credenciales siguientes:
    * Alias: hasta el criterio del usuario
    * Nombre de host o dirección IP: 127.0.0.1

3. Seleccione **Conectar** en la parte inferior derecha de la **pestaña** Equipo:

![Captura de pantalla de la ventana de conexión de la aplicación DEDA con el alias, el nombre de host, la dirección IP y el botón Agregar resaltados](images/pix-img-12.png)

> [!NOTE]
> La primera conexión siempre es más lenta porque se copian los archivos binarios.

4. Cuando ESTÉ CONECTADO a la HoloLens 2, busque la aplicación en la sección **Seleccionar** proceso de destino de la pestaña Iniciar UWP y seleccione **Iniciar:**

![Captura de pantalla de la aplicación DEV con la ventana seleccionar proceso de destino y el botón iniciar resaltados](images/pix-img-13.png)

## <a name="gpu-captured"></a>Gpu capturada

1. Para iniciar la captura de GPU, haga clic **en Foto** en la sección Captura **de GPU:**

![Captura de pantalla de la aplicación DEG con el panel de conexión de PC abierto con la captura de GPU resaltada](images/pix-img-14.png)

2. Abra la captura para su análisis haciendo clic en la captura de pantalla generada en el panel **Captura de GPU:**

![Captura de pantalla de la aplicación GPU con la sección captura de GPU abierta con el panel de captura de GPU resaltado](images/pix-img-15.png)

3. Presione **Iniciar** para comenzar el análisis:

![Captura de pantalla de la aplicación DEV con el botón Iniciar resaltado](images/pix-img-16.png)

> [!IMPORTANT]
> Si recopila datos de tiempo después de realizar una captura de GPU, se le obligará a reiniciar el casco. Se trata de un reinicio único del dispositivo y es necesario para la recopilación de datos de control de tiempo.

¡YA ESTÁ LISTO PARA SU USO!

## <a name="see-also"></a>Consulte también
* [Página principal de PIXEL](https://devblogs.microsoft.com/pix)