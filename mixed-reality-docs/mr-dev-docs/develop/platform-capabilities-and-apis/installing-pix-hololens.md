---
title: Instalación de PIX para HoloLens 2
description: Obtenga información sobre cómo instalar PIX para dispositivos HoloLens 2.
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens, HoloLens 2, PIX, captura, auriculares de realidad mixta, auriculares de realidad mixta de Windows, auriculares de realidad virtual
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615426"
---
# <a name="installing-pix-for-hololens-2"></a>Instalación de PIX para HoloLens 2

[PIX](https://devblogs.microsoft.com/pix) es una herramienta de optimización y depuración del rendimiento para aplicaciones DirectX 12 en Windows. 

## <a name="setup"></a>Configuración

1. Grabe la última [versión]( https://devblogs.microsoft.com/pix/download) de PIX del equipo host y conecte HoloLens 2 a su PC a través de un cable USB.

2. Si HoloLens 2 está en una [compilación de Windows Insider](https://insider.windows.com) o tiene una configuración que interrumpe pix, vuelva a hacer que  [el dispositivo](https://docs.microsoft.com/hololens/hololens-recovery) borre todos los datos.

3. Habilite el **modo de desarrollador** y el portal de **dispositivos**:

* Abra **configuración** desde Shell:

![Captura de pantalla del menú de HoloLens con el botón configuración resaltado](images/pix-img-01.jpg)

* Seleccione **actualizar & seguridad**:

![Captura de pantalla de la ventana de configuración abierta en HoloLens con el botón actualizar y seguridad resaltado](images/pix-img-02.jpg)

* Haga clic en **para desarrolladores**:

![Captura de pantalla de la ventana de seguridad y actualizaciones abierto con para desarrolladores botón resaltado](images/pix-img-03.jpg)

* Activar **usar características de desarrollador** y **Habilitar el portal de dispositivos**

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con el botón habilitar el portal de dispositivos resaltado](images/pix-img-04.jpg)

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con la opción usar desarrollo de características alternancia resaltada](images/pix-img-05.jpg)

* Con el dispositivo todavía conectado, activo y con el usuario que ha iniciado sesión, inicie Visual Studio.

> [!IMPORTANT]
> Asegúrese de que el dispositivo no está en modo de espera o en suspensión. Si tiene problemas con este paso, consulte las [instrucciones del portal de dispositivos de Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).

## <a name="preparing-for-deployment"></a>Preparación para la implementación

1. En Visual Studio, establezca **ARM64** como la plataforma y el **dispositivo** como el dispositivo:

![Captura de pantalla de la solución de Visual Studio con la configuración de plataforma y de dispositivo resaltada](images/pix-img-06.png)

2. Cuando Visual Studio le pide un **PIN** del dispositivo:

![Captura de pantalla de la ventana emergente de Visual Studio que solicita el PIN](images/pix-img-07.png)

* Seleccionar **configuración** de Shell
* Seleccionar **Actualizar seguridad de &**
* Haga clic en **para desarrolladores** y pulse emparejar en **detección de dispositivos** . 

![Captura de pantalla de la ventana para desarrolladores abierta en configuración con la detección de dispositivos resaltada](images/pix-img-08.jpg)

![Captura de pantalla del elemento emergente del dispositivo de pago con código de registro resaltado](images/pix-img-09.jpg)

* Escriba el número de PIN generado en Visual Studio

3. Visual Studio implementará la aplicación en la HoloLens conectada, que puede tardar unos minutos en función de la aplicación.

## <a name="launching-pix"></a>Iniciar PIX

En primer lugar, use el portal de dispositivos para comprobar que la aplicación no se está ejecutando en HoloLens 2. Después, inicie PIX, conéctese a su dispositivo y haga clic en **Inicio**:

![Captura de pantalla de la pantalla principal de la aplicación PIX](images/pix-img-10.png)

* Seleccione **conectar** en el menú de la izquierda:

![Captura de pantalla del menú de la izquierda de la aplicación PIX con el botón conectar resaltado](images/pix-img-11.png)

2. En la pestaña **equipo** , haga clic en **Agregar** y escriba las credenciales siguientes:
    * Alias: según el criterio del usuario
    * Nombre de host o dirección IP: 127.0.0.1

3. Haga clic en **conectar** en la parte inferior derecha de la ficha **equipo** :

![Captura de pantalla de la ventana conectar aplicación PIX con el alias, el nombre de host, la dirección IP y el botón Agregar resaltados](images/pix-img-12.png)

> [!NOTE]
> La primera conexión siempre es más lenta porque se están copiando los archivos binarios.

4. Cuando PIX se haya conectado a HoloLens 2, busque la aplicación en la sección **seleccionar el proceso de destino** en la pestaña iniciar UWP y haga clic en **iniciar**:

![Captura de pantalla de la aplicación PIX con la ventana seleccionar el proceso de destino y el botón Launch resaltado](images/pix-img-13.png)

## <a name="gpu-captured"></a>GPU capturada

1. Inicie la captura de GPU; para ello, haga clic en **Photo** en la sección **captura de GPU** :

![Captura de pantalla de la aplicación PIX con el panel de conexión de PC abierto con captura de GPU resaltada](images/pix-img-14.png)

2. Abra la captura para el análisis; para ello, haga clic en la captura de pantalla generada en el panel de **captura de GPU** :

![Captura de pantalla de la aplicación PIX con la sección captura de GPU abierta con el panel de captura de GPU resaltado](images/pix-img-15.png)

3. Presione **Inicio** para iniciar el análisis:

![Captura de pantalla de la aplicación PIX resaltada en el botón Inicio](images/pix-img-16.png)

> [!IMPORTANT]
> Si recopila datos de control de tiempo después de realizar una captura de GPU, deberá reiniciar el casco. Se trata de un reinicio único del dispositivo y es necesario para la recopilación de datos de control de tiempo.

PIX ya está listo para su uso.

## <a name="see-also"></a>Consulte también
* [Página principal de PIX](https://devblogs.microsoft.com/pix)