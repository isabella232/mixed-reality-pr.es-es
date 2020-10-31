---
title: Instale el software de Windows Mixed Reality
description: Después de conectar el casco de la realidad mixta de Windows, use la aplicación del portal de realidad mixta para empezar a trabajar y descargar las características de Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, introducción, configuración, portal de realidad mixta
appliesto:
- Windows 10
ms.openlocfilehash: a9333e9f4d80ea73724e2530f2e94c3d0e32d0d4
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132109"
---
# <a name="install-windows-mixed-reality-software"></a>Instale el software de Windows Mixed Reality

> [!div class="nextstepaction"]
> [Obtener portal de realidad mixta](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m?activetab=pivot:overviewtab)

## <a name="launch-mixed-reality-portal"></a>Inicio del portal de realidad mixta

Después de conectar el casco de la realidad mixta de Windows y de que el controlador se instala correctamente, el portal de realidad mixta (PRM) se iniciará automáticamente en el escritorio. Si esto no ocurre automáticamente, siempre puede iniciar el portal de realidad mixta desde el menú Inicio ( **iniciar > portal de realidad mixta** ). Una vez que se haya iniciado el portal, haga clic en **Introducción** .

![Le damos la bienvenida a Mixed Reality](images/1050px-mixedrealityportal.png)

En el portal de realidad mixta, puede:

* Mostrar un streaming en vivo de la vista en el casco (Windows Mixed Reality ultra Only). Para activar y desactivar esta opción, seleccione "detener vista previa" o "iniciar vista previa". (También puede activar y desactivar la vista previa en el menú Inicio de realidad mixta).
* Vea el estado de los auriculares y los controladores. Seleccione "menú" para ver toda la información.
* Configurar nuevos controladores. Seleccione **menú > configurar controladores** .
* Activar o desactivar el límite. Activar **o desactivar el límite de > de menús** . (Si lo desactiva, deberá permanecer en un lugar por seguridad).
* Cree un nuevo límite. Seleccione el **menú > ejecutar el programa de instalación** .
* Llegue a sus fotos de realidad mixta. Seleccione **menú > consulte fotos de realidad mixta** .
* Obtenga aplicaciones y juegos de realidad mixta. Seleccione **menú > obtener aplicaciones de realidad mixta** .

## <a name="download-windows-mixed-reality"></a>Descargar Windows Mixed Reality

Windows Mixed Reality tiene aproximadamente 1 GB de tamaño y los tiempos de descarga variarán en función de la conexión a Internet. Si encuentra un mensaje que dice "no pudimos descargar el software de realidad mixta", consulte [los pasos de solución de problemas](installation_errors.md#we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading).

## <a name="general-troubleshooting"></a>Solución general de problemas

Si experimenta problemas u obtiene un mensaje de error al usar el portal de realidad mixta, Pruebe estas soluciones.

**Reiniciar Windows Mixed Reality**

1. Desconecte el casco del equipo (ambos cables).
2. Reinicie el equipo y, a continuación, vuelva a conectar el casco.

**Asegúrese de que el equipo reconoce los auriculares**

Si el reinicio no funciona, asegúrese de que el equipo reconoce el casco. Seleccione Inicio, escriba administrador de dispositivos en el cuadro de búsqueda y, a continuación, selecciónelo en la lista. Expanda dispositivos de realidad mixta y compruebe si aparece el casco.

Si no aparece, intente lo siguiente:

* Conecte los auriculares a puertos diferentes en el equipo, si está disponible.
* Busque las actualizaciones de software más recientes desde [Windows Update](https://support.microsoft.com/help/12373).
* Desinstalar y reinstalar Windows Mixed Reality:
    1. Desconecte el casco del equipo (ambos cables).
    2. Seleccione **configuración > realidad mixta > desinstalar** .
    3. Desemparejar los controladores de movimiento: seleccione la **configuración > dispositivos > Bluetooth & otros dispositivos** . Seleccione cada controlador y, a continuación, seleccione **quitar dispositivo** .
    4. Para volver a instalar Windows Mixed Reality, conecte el casco a su PC.

## <a name="common-error-messages"></a>Mensajes comunes de error

A continuación se indican algunas cosas para probar [los mensajes de error](error-codes.md) que puede ver.

| Si ve este mensaje | Pruebe esto |
| --- | --- |
| Comprobar el cable USB | Conecte los auriculares a otro puerto USB (y asegúrese de que es un SuperSpeed USB 3,0). Además, pruebe a quitar cualquier dispositivo extender o concentrador entre los auriculares y el equipo. |
| Comprobar el cable para mostrar | Pruebe lo siguiente: <ul><li>Conecte los auriculares a un DisplayPort 1,2 o posterior, o HDMI 1,4 o posterior. Asegúrese de que el puerto corresponde a la tarjeta de gráficos más avanzada del equipo.</li><li>Si utiliza un adaptador, asegúrese de que sea compatible con 4K</li><li>Pruebe a usar un puerto HDMI diferente</li><li>Si tiene un monitor externo conectado a un puerto HDMI, intente conectarlo a un DisplayPort en su lugar y use el puerto HDMI para sus auriculares</li></ul> |
| Hubo un problema | Siga los pasos de solución de problemas generales anteriores. |

## <a name="review-and-accept-terms-and-conditions"></a>Revisar y aceptar los términos y condiciones

Para continuar con la instalación, debe tener 2 GB de espacio disponible en el equipo. Revisar **y presionar acepto** los términos y condiciones para continuar

![Aceptación de los términos y condiciones](images/1050px-mixedrealityportalpage2.png)

## <a name="compatibility-check"></a>Comprobación de compatibilidad

A continuación se encuentra la comprobación compatible. El portal de realidad mixta comprobará que el equipo sea compatible con la realidad mixta. Las comprobaciones **verdes** indican que el equipo ha pasado el elemento necesario. Los triángulos **naranja** significan que puede haber problemas con el equipo para el requisito determinado. Si tiene problemas, es posible que tenga que solucionar problemas o actualizar el equipo. **Red** La X significa que el equipo no cumple los requisitos del elemento especificado.

![Comprobación de compatibilidad](images/1050px-compatcheck.png)

## <a name="getting-ready"></a>Preparación

Verá un mensaje de "preparación para configurar" en la pantalla con un icono de giro. Esto solo tardará unos minutos:

![Preparación para configurar](images/1050px-gettingsetup.png)

## <a name="see-also"></a>Consulte también

* [Preguntar a la comunidad](https://answers.microsoft.com)
* [Póngase en contacto con nosotros para obtener soporte técnico](https://support.microsoft.com/contactus/)
* [Solución de problemas de instalación](installation_errors.md)
* [Solución de problemas de configuración](wmr-setup-faq.md)
* [Configuración de Windows Mixed Reality](set-up-windows-mixed-reality.md)
