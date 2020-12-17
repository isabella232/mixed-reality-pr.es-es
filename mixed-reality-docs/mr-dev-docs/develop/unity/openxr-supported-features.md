---
title: Características compatibles con el complemento OpenXR en Unity
description: Descubra las características que OpenXR admite para el desarrollo de la realidad mixta en Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, reality Mixed, MRTK, kit de herramientas de realidad mixta, realidad aumentada, realidad virtual, auriculares de realidad mixta, información, tutorial, introducción
ms.openlocfilehash: dc908762d6e44e04f56b8ff82b90394106ca42e5
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2020
ms.locfileid: "97623009"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a>Características admitidas de OpenXR de realidad mixta en Unity

El paquete de **Complementos OpenXR de realidad mixta** es una extensión del **complemento OpenXR** de Unity y admite un conjunto de características para los auriculares HoloLens 2 y Windows Mixed Reality. Antes de continuar, asegúrese de que ha instalado **unity 2020,2** o posterior, **OpenXR plugin versión 0.1.1** o posterior y el proyecto de Unity está [configurado para OpenXR](openxr-getting-started.md).

## <a name="whats-supported"></a>Lo que se admite

Actualmente se admiten las siguientes características:

* Admite aplicaciones para UWP para aplicaciones de HoloLens 2 y Win32 VR para auriculares con Windows Mixed Reality.
* Optimiza el paquete UWP y la interacción con CoreWindow para aplicaciones de HoloLens 2.
* Seguimiento de escala mundial con delimitadores y espacio sin enlazar.
* Delimite la API de almacenamiento para conservar los delimitadores en el almacenamiento local de HoloLens 2.
* Control de movimiento y interacciones de mano, incluido el nuevo controlador de HP reverberación G2.
* Seguimiento de mano articulado mediante 26 uniones y entradas de radio uniones.
* Interacción de ojo mirada en HoloLens 2.
* Buscar la cámara de foto/vídeo (PV) en HoloLens 2.
* Captura de realidad mixta mediante la representación de la tercera vista a través de la cámara PV.
* Admite "Play" para HoloLens 2 mediante la aplicación de comunicación remota holográfica, lo que permite a los desarrolladores depurar scripts sin compilar e implementar en el dispositivo.
* Compatible con MRTK Unity 2.5.2 a través de MRTK paquete de adaptador OpenXR. <missing link>
* Compatible con Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) o posterior

## <a name="holographic-remoting-in-unity-editor-play-mode"></a>Holographic Remoting en el modo de reproducción del editor de Unity

Compilar un proyecto de Unity de UWP en un proyecto de Visual Studio y, luego, empaquetarlo e implementarlo en un dispositivo HoloLens 2 puede tardar algún tiempo. Una solución es habilitar la comunicación remota del editor holográfica, que le permite depurar el script de C# mediante el modo "reproducir" directamente en un dispositivo HoloLens 2 a través de la red. En este escenario se evita la sobrecarga de crear e implementar un paquete de UWP en un dispositivo remoto.

1. En primer lugar, debe [instalar la aplicación de reproductor de comunicación remota holográfica](https://www.microsoft.com/store/productId/9NBLGGH4SV40) desde la tienda en HoloLens 2.  
2. Ejecute la aplicación holográfica Remoting Player en HoloLens 2 y verá el número de versión y la dirección IP a la que se conectará.
    * Necesitará v 2.4 o posterior para trabajar con el complemento OpenXR

![Captura de pantalla del reproductor de acceso remoto holográfica que se ejecuta en HoloLens](images/openxr-features-img-01.png)

3. Abra **configuración del proyecto de edición >**, vaya a **Administración de complementos de XR** y active la casilla **conjunto de características de Windows Mixed Reality** :

![Captura de pantalla del panel de configuración del proyecto abrir en el editor de Unity con la administración de complementos de XR resaltada](images/openxr-features-img-02.png)

4. Expanda la sección **características** en **OpenXR** y seleccione **Mostrar todas**
5. Active la casilla de **comunicación remota del editor holográfica** y escriba la dirección IP que obtiene de la aplicación de acceso remoto holográfica:

![Captura de pantalla del panel de configuración del proyecto abierta en el editor de Unity con características resaltadas](images/openxr-features-img-03.png)

Ahora puede hacer clic en el botón "reproducir" para reproducir la aplicación de Unity en la aplicación de acceso remoto holográfica en HoloLens. También puede [adjuntar Visual Studio a Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts de C# en el modo de reproducción.

> [!NOTE]
> A partir de la versión 0.1.0 de Holographic Remoting, el runtime no admite la característica de delimitador, y las funcionalidades de ARAnchorManager no funcionarán a través de la comunicación remota.  Esta característica está disponible en futuras versiones.

## <a name="motion-controller-and-hand-interactions"></a>Interacciones de controlador de movimiento y mano
Para conocer los aspectos básicos sobre las interacciones de la realidad mixta en Unity, visite el [manual de Unity para la entrada de Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentación de Unity cubre las asignaciones de entradas específicas del controlador a s más generalizables `InputFeatureUsage` , cómo se pueden identificar y clasificar las entradas de XR disponibles, cómo leer datos de estas entradas, etc. 
 
El complemento OpenXR de realidad mixta proporciona perfiles de interacción de entrada adicionales, asignados a los estándares estándar, `InputFeatureUsage` como se detalla a continuación: 
 
| `InputFeatureUsage` | Controlador de HP reverberación G2 (OpenXR) | Mano de HoloLens (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Joystick | |
| primary2DAxisClick | Joystick: haga clic | |
| desencadenador | Desencadenador  | |
| sujeta | Sujeta | Puntear o comprimir el aire |
| primaryButton | [X/A]-presionar | Pulsar en el aire |
| secondaryButton | [Y/B]-Presione | |
| gripButton | Agarre: presionar | |
| triggerButton | Desencadenador: Presione | |
| menuButton | Menú | |

#### <a name="haptics"></a>Hápticos
Para obtener información sobre el uso de hápticos en el sistema de entrada XR de Unity, puede encontrar documentación en el [manual de Unity para entrada-hápticos de Unity](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics). 


## <a name="whats-coming-soon"></a>Novedades próximamente

Los siguientes problemas y las características que faltan se conocen con la **versión 0.1.0** del complemento OpenXR de realidad mixta. Estamos trabajando en ellos y publicará correcciones y nuevas características en las próximas versiones.

* **ARPlaneSubsystem** todavía no se admite. **ARPlaneManager**, **ARRaycastManager** y API relacionada como **ARAnchorManager. AttachAnchor** tampoco se admiten en HoloLens 2.
* El **delimitador** no es compatible aún con la comunicación remota holográfica, pero está próximamente en un futuro.
* Todavía no se admite el seguimiento de **mallas de mano** , los **códigos QR** y los **XRMeshSubsystem** .
* La compatibilidad con los **anclajes espaciales de Azure** está disponible en una versión futura.
* **ARM64** es la única plataforma admitida para las aplicaciones de HoloLens 2. La plataforma **ARM** está próximamente en una versión futura.

## <a name="troubleshooting"></a>Solución de problemas 

Al suspender y reanudar una aplicación de Unity en HoloLens 2, la aplicación no se puede reanudar correctamente, lo que conduce a 4 puntos de giro en la vista de HoloLens. 
* Establezca el **modo de envío de profundidad** en **ninguno** en la configuración del proyecto OpenXR como solución alternativa.
