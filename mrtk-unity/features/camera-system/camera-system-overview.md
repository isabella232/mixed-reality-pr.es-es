---
title: Información general del sistema de cámara
description: Página de aterrizaje del sistema de cámara en MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK, cámara,
ms.openlocfilehash: 1dc5328f2a6390246918063b6564837f150d28d8
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144478"
---
# <a name="camera-system"></a>Sistema de cámara

El sistema de cámara permite que Microsoft Mixed Reality Toolkit configure y optimice la cámara de la aplicación para su uso en aplicaciones de realidad mixta. Con el sistema de cámara, las aplicaciones se pueden escribir para admitir dispositivos opacos (por ejemplo, de realidad virtual) y transparentes (por ejemplo, Microsoft HoloLens) sin necesidad de escribir código para distinguir y adaptarse a cada tipo de pantalla.

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

### <a name="settings-providers"></a>Proveedores de configuración

![Proveedores de configuración de cámara](../images/camera-system/CameraSettingsProviders.png)

Los proveedores de configuración de cámara habilitan la configuración específica de la plataforma de la cámara. Esta configuración puede incluir pasos de configuración personalizados o componentes.

Los proveedores se pueden agregar haciendo clic en el **botón Agregar proveedor de configuración de** cámara. Se pueden quitar haciendo clic en **-** el botón situado a la derecha del nombre del proveedor.

> [!Note]
> No todas las plataformas requerirán un proveedor de configuración de cámara. Si no hay proveedores compatibles con la plataforma en la que se ejecuta la aplicación, Microsoft Mixed Reality Toolkit aplicará los valores predeterminados básicos.

### <a name="display-settings"></a>Configuración de pantalla

![Configuración de la pantalla de la cámara](../images/camera-system/CameraDisplaySettings.png)

La configuración de pantalla se especifica para las pantallas opacas (por ejemplo, Virtual Reality) y transparentes (por ejemplo, Microsoft HoloLens). La cámara se configura, en tiempo de ejecución, con esta configuración.

**Near Clip**

El plano de recorte cercano es el más cercano, en metros, que un objeto virtual puede estar en la cámara y representarse. Para mayor comodidad del usuario, se recomienda que este valor sea mayor que cero. La imagen anterior contiene valores que se han encontrado cómodos en una variedad de dispositivos.

**Recorte lejano**

El plano de recorte lejano es el más alejado, en metros, que un objeto virtual puede estar en la cámara y representarse todavía. En el caso de los dispositivos transparentes, se recomienda que este valor sea relativamente cercano, ya que no supere demasiado el espacio real y que se rompa la calidad inmersiva de la aplicación.

**Borrar marcas**

El valor clear flags indica cómo se borra la presentación a medida que se dibuja. En el caso de las experiencias de realidad virtual, este valor suele establecerse en Skybox. Para las pantallas transparentes, se recomienda establecer esta opción en Color.

**Color de fondo**

Si las marcas sin borrar no están establecidas en Skybox, se mostrará la propiedad de color de fondo.

**Configuración de calidad**

El valor de configuración de calidad indica la calidad de los gráficos que Unity debe usar al representar la escena. El nivel de calidad es una configuración de nivel de proyecto y no es específico de ninguna cámara. Para más información, consulte el artículo [Calidad en](https://docs.unity3d.com/Manual/class-QualitySettings.html) la documentación de Unity.

## <a name="see-also"></a>Consulte también

- [Documentación de la API del sistema de cámara](xref:Microsoft.MixedReality.Toolkit.CameraSystem)
- [Crear un proveedor de configuración de cámara](create-settings-provider.md)
