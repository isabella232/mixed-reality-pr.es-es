---
title: Introducción al sistema de cámara
description: Página de aterrizaje del sistema de cámara en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara,
ms.openlocfilehash: cfb40b00d81133ad40e0e4d7a7b2ad87ee645e36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177047"
---
# <a name="camera-system-overview"></a>Introducción al sistema de cámara

El sistema de cámara permite a microsoft Mixed Reality Toolkit configurar y optimizar la cámara de la aplicación para su uso en aplicaciones de realidad mixta. Mediante el sistema de cámara, las aplicaciones se pueden escribir para admitir dispositivos opacos (por ejemplo, de realidad virtual) y transparentes (por ejemplo, Microsoft HoloLens) sin necesidad de escribir código para distinguir y adaptarse a cada tipo de pantalla.

## <a name="enabling-the-camera-system"></a>Habilitación del sistema de cámara

El sistema de cámaras se administra mediante el objeto MixedRealityToolkit (u otro componente registrador de servicios).

En los pasos siguientes se supone que se usa el objeto MixedRealityToolkit. Los pasos necesarios para otros registradores de servicios pueden ser diferentes.

1. Seleccione el objeto MixedRealityToolkit en la jerarquía de escena.

    ![Jerarquía de escena configurada de MRTK](../images/MRTK_ConfiguredHierarchy.png)

2. Vaya al panel Inspector a la sección del sistema de cámara y asegúrese de **que habilitar el sistema de cámara** está activado.

    ![Habilitación del sistema de cámara](../images/camera-system/EnableCameraSystem.png)

3. Seleccione la implementación del sistema de cámara. La implementación de clase predeterminada proporcionada por MRTK es `MixedRealityCameraSystem` .

    ![Selección de la implementación del sistema de cámara](../images/camera-system/SelectCameraSystemType.png)

4. Selección del perfil de configuración deseado

    ![Selección del perfil del sistema de cámara](../images/camera-system/SelectCameraProfile.png)

## <a name="configuring-the-camera-system"></a>Configuración del sistema de cámara

### <a name="settings-providers"></a>Configuración proveedores

![Proveedores de Configuración cámara](../images/camera-system/CameraSettingsProviders.png)

Los proveedores de configuración de cámara habilitan la configuración específica de la plataforma de la cámara. Esta configuración puede incluir pasos de configuración personalizados o componentes.

Los proveedores se pueden agregar haciendo clic en el botón **Add Camera Configuración Provider (Agregar Configuración proveedor).** Se pueden quitar haciendo clic en **-** el botón situado a la derecha del nombre del proveedor.

> [!Note]
> No todas las plataformas requerirán un proveedor de configuración de cámara. Si no hay ningún proveedor que sea compatible con la plataforma en la que se ejecuta la aplicación, microsoft Mixed Reality Toolkit aplicará los valores predeterminados básicos.

### <a name="display-settings"></a>Configuración de pantalla

![Pantalla de la cámara Configuración](../images/camera-system/CameraDisplaySettings.png)

La configuración de pantalla se especifica para las pantallas opacas (por ejemplo, Virtual Reality) y transparentes (por ejemplo, Microsoft HoloLens). La cámara se configura, en tiempo de ejecución, con esta configuración.

**Near Clip**

El plano de recorte cercano es el más cercano, en metros, que un objeto virtual puede estar en la cámara y seguir representando. Para mayor comodidad del usuario, se recomienda que este valor sea mayor que cero. La imagen anterior contiene valores que se han encontrado cómodos en diversos dispositivos.

**Recorte lejano**

El plano de recorte lejano es el más alejado, en metros, que un objeto virtual puede estar en la cámara y seguir representando. En el caso de los dispositivos transparentes, se recomienda que este valor sea relativamente cercano a no superar demasiado el espacio real y interrumpir las calidades inmersivas de la aplicación.

**Borrar marcas**

El valor clear flags indica cómo se borra la presentación a medida que se dibuja. En el caso de las experiencias de realidad virtual, este valor suele establecerse en Skybox. En el caso de las pantallas transparentes, se recomienda establecer esta opción en Color.

**Color de fondo**

Si las marcas sin borrar no están establecidas en Skybox, se mostrará la propiedad de color de fondo.

**Calidad Configuración**

El valor de configuración de calidad indica la calidad de los gráficos que Unity debe usar al representar la escena. El nivel de calidad es una configuración de nivel de proyecto y no es específico de ninguna cámara. Para más información, consulte el artículo [Calidad en](https://docs.unity3d.com/Manual/class-QualitySettings.html) la documentación de Unity.

## <a name="see-also"></a>Consulte también

- [Documentación de la API del sistema de cámara](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Creación de un proveedor de Configuración cámara](create-settings-provider.md)
