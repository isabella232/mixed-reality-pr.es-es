---
title: 6. Empaquetado e implementación en el dispositivo o emulador
description: Parte 6 de 6 de una serie de tutoriales para compilar una aplicación de ajedrez con Unreal Engine 4 y el complemento UX Tools de Mixed Reality Toolkit
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, tutorial, getting started, mrtk, uxt, UX Tools, documentation, mixed reality headset, windows mixed reality headset, virtual reality headset
ms.openlocfilehash: 7b706cf2a8685954ed916c825c3617ade190f1e0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2021
ms.locfileid: "98583653"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a>6. Empaquetado e implementación en el dispositivo o emulador

En el tutorial anterior, agregó un botón sencillo que restablece la pieza de ajedrez a su posición original. En esta última sección, preparará la aplicación para que se ejecute en HoloLens 2 o en un emulador. Si tiene HoloLens 2, puede transmitir en secuencias desde el equipo o el paquete la aplicación para ejecutarla directamente en el dispositivo. Si no tiene un dispositivo, deberá empaquetar la aplicación para que se ejecute en el emulador. Al final de esta sección, tendrá una aplicación de realidad mixta implementada que se puede reproducir, terminada con interacciones e interfaz de usuario.

## <a name="objectives"></a>Objetivos

* [Solo dispositivo] Transmisión en secuencias a HoloLens 2 con el control remoto de holografías de la aplicación
* Empaquetado e implementación de la aplicación en un dispositivo o emulador de HoloLens 2

## <a name="device-only-streaming"></a>[Solo dispositivo] Transmisión en secuencias

El [control remoto de holografías](/windows/mixed-reality/add-holographic-remoting) significa la transmisión en secuencias de datos desde un equipo o dispositivo UWP independiente a HoloLens 2, sin cambiar el canal. Una aplicación host de control remoto recibe una transmisión en secuencias de datos de entrada de HoloLens, representa el contenido en una vista envolvente virtual y vuelve a transmitir en secuencia los fotogramas de contenido a HoloLens a través de Wi-Fi. La transmisión en secuencias le permite agregar vistas envolventes remotas al software del equipo de escritorio existente y tener acceso a más recursos del sistema.

Si va a realizar esta ruta con la aplicación de ajedrez, necesitará algunos elementos:

1.  Instale **Holographic Remoting Player** desde Microsoft Store en HoloLens 2 y ejecute la aplicación. Anote la dirección IP que se muestra en la aplicación.
    * Vaya a **Editar > Configuración del proyecto** y asegúrese de que **Default RHI** (RHI predeterminado) de Windows está establecido en **Predeterminado** o **D3D11**:

![RHI predeterminado](../images/unreal/performance-recommendations-img-09.png)

2.  Cuando vuelva a estar en el editor de Unreal, vaya a **Edit > Project Settings** (Editar > Configuración del proyecto) y marque la opción **Habilitar la comunicación remota** en la sección **Holographic Remoting** (Comunicación remota de holografías).

3.  Reinicie el editor y, a continuación, escriba la dirección IP del dispositivo (como se muestra en la aplicación Holographic Remoting Player) y haga clic en **Conectar**.

Una vez conectado, haga clic en la flecha desplegable situada a la derecha del botón **Play** (Jugar) y seleccione **VR Preview** (Vista previa de VR). La aplicación se ejecutará en la ventana Vista previa de VR, de la que se hace streaming al casco de HoloLens.

## <a name="packaging-and-deploying-the-app-via-device-portal"></a>Empaquetado e implementación de la aplicación mediante el Portal de dispositivos

>[!NOTE]
>Si esta es la primera vez que empaquetas una aplicación de Unreal para HoloLens, deberás descargar los archivos auxiliares desde el iniciador de Epic.
>- Vaya a **Preferencias del editor > General > Código fuente > Editor de código fuente** y compruebe que se haya seleccionado Visual Studio 2019.
>- Vaya a la pestaña **Biblioteca** en Selector de juegos Epic, seleccione la flecha desplegable situada junto a **Lanzar** > y haga clic en **Opciones**.
>- En **Target Platforms** (Plataformas de destino), selecciona **HoloLens 2** y haz clic en **Aplicar**.
>![Cambio de la plataforma de destino en la configuración del proyecto](images/unreal-uxt/6-installationoptions.PNG)

1.  Ve a **Edit > Project Settings** (Editar > Configuración del proyecto).
    * Añada un nombre de proyecto en **Project > Description > About > Project Name** (Proyecto > Descripción > Acerca de > Nombre del proyecto).
    * Añada **CN=NombreDeLaEmpresa** en **Project > Description > Publisher > Company Distinguished Name** (Proyecto > Descripción > Editor > Nombre distintivo de la empresa).
    * Seleccione **Iniciar en VR** en **Proyecto > Descripción > Configuración**.

> [!IMPORTANT]
> Si deja alguno de estos campos en blanco, se producirá un error al intentar generar un nuevo certificado en el paso 3.

> [!IMPORTANT]
> El nombre del editor debe tener el [formato de nombres distintivos de LADPv3](https://www.ietf.org/rfc/rfc2253.txt). Un nombre de editor con un formato incorrecto dará lugar al error "Signing key not found. The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.) al realizar el empaquetado.

> [!IMPORTANT]
> Si no selecciona "Iniciar en VR", la aplicación intentará iniciarse en una claqueta.

![Configuración del proyecto: descripción](images/unreal-uxt/6-cn-new.PNG)

2.  Habilite **Build for HoloLens Emulation** (Compilar para emulación de HoloLens) y/o **Build for HoloLens Device** (Compilar para dispositivo HoloLens) en **Platforms > HoloLens** (Plataformas > HoloLens).

3.  Haga clic en **Generate new** (Generar nuevo) en la sección **Packaging** (Empaquetado) [junto a **Signing Certificate** (Certificado de firma)].

> [!IMPORTANT]
> Si utiliza un certificado ya generado, el nombre del editor del certificado debe ser el mismo que el nombre del editor de la aplicación. En caso contrario, se producirá el error "Signing key not found. The app could not be digitally signed." (Clave de firma no encontrada. No se pudo firmar digitalmente la aplicación.) error.

![Configuración del proyecto - Plataformas - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. Haga clic en **None** (Ninguno) con fines de prueba cuando se le pida que cree una contraseña de clave privada.

![Generación de un nuevo certificado](images/unreal-uxt/6-private-key-testing.png)

5. Ve a **File > Package Project** (Archivo > Proyecto de paquete) y selecciona **HoloLens**.
    * Crea una nueva carpeta en la que guardar el paquete y haz clic en **Select Folder** (Seleccionar carpeta).

6.  Abra el [Portal de dispositivos Windows](/windows/mixed-reality/using-the-windows-device-portal) después de empaquetar la aplicación, vaya a **Vistas > Aplicaciones** y busque la sección **Implementar aplicación**.

7.  Haga clic en **Examinar...** , vaya al archivo **ChessApp.appxbundle** y haga clic en **Abrir**.

    * Active la casilla situada junto a **Permitirme seleccionar paquetes de marcos** si es la primera vez que instala la aplicación en el dispositivo.
    * En el siguiente cuadro de diálogo, incluya los archivos **VCLibs** y **appx** adecuados (**arm64** para el dispositivo y **x64** para el emulador). Puede encontrar los archivos en **HoloLens** dentro de la carpeta donde ha guardado el paquete.

8.  Haz clic en **Instalar**
    * Ahora puede ir a **Todas las aplicaciones** y pulsar la aplicación recién instalada para ejecutarla, o inicie la aplicación directamente desde el **Portal de dispositivos Windows**. 

Enhorabuena. La aplicación de realidad mixta de HoloLens está finalizada y lista para utilizarse. Sin embargo, esto no es todo. MRTK tiene muchas características independientes que puede agregar a los proyectos, como el mapeo espacial, la entrada de mirada y voz, e incluso los códigos QR. Puede encontrar más información sobre estas características en [Introducción al desarrollo con Unreal](/windows/mixed-reality/unreal-development-overview).

## <a name="next-development-checkpoint"></a>Siguiente punto de control de desarrollo

Si sigue el recorrido de desarrollo de Unreal que hemos diseñado, significa que ya se encuentra en proceso de explorar los bloques de compilación principales de MRTK. Desde aquí, puede continuar con el siguiente bloque de compilación:

> [!div class="nextstepaction"]
> [Entrada de mirada](../unreal-gaze-input.md)

O bien puede saltar a las funcionalidades y las API de la plataforma de realidad mixta:

> [!div class="nextstepaction"]
> [Cámara de HoloLens](../unreal-hololens-camera.md)

Puede volver a los [puntos de control de desarrollo de Unreal](../unreal-development-overview.md#2-core-building-blocks) en cualquier momento.