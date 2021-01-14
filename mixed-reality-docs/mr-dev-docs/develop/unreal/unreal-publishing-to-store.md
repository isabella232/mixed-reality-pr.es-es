---
title: Publicación en Microsoft Store
description: Obtenga información acerca de cómo empaquetar, certificar y publicar aplicaciones de Mixed Reality de Unreal en Microsoft Store.
author: hferrone
ms.author: jacksonf
ms.date: 12/3/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidad mixta, desarrollo, documentación, guías, características, casco de realidad mixta, casco de windows mixed reality, casco de realidad virtual, publicación, distribución, Microsoft Store
ms.openlocfilehash: 41f081f11cdb9ac2fdf96a81bb761a1321d1776f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010025"
---
# <a name="publishing-to-the-microsoft-store"></a>Publicación en Microsoft Store

Cuando esté listo para lanzar al mundo la aplicación Unreal, hay algunas opciones de configuración del proyecto que deben actualizarse antes de enviarla a Microsoft Store. Todos estas opciones tienen valores predeterminados, pero se deben cambiar para producción para que representen mejor la aplicación.

## <a name="project-settings-for-the-store-packaging"></a>Configuración del proyecto para el empaquetado del almacén

1. En primer lugar, seleccione **Configuración del proyecto > Descripción** y actualice la información del juego y del editor: 
    * El **nombre del juego** aparecerá en el icono de la aplicación en HoloLens.
    * El **nombre distintivo de la empresa** se usa al generar el certificado del proyecto y debe tener el siguiente formato: 
        * **CN=CommonName, O=OrganizationName, L=LocalityName, S=StateOrProvinceName, C=CountryName**:

![Captura de pantalla del editor de Unreal con la sección de descripción expandida en la configuración del proyecto](images/unreal-publishing-img-01.png)

2. Expanda la sección **HoloLens** de la configuración del proyecto y actualice los recursos de empaquetado.  Estos nombres de recursos se mostrarán en la página de la tienda de la aplicación:

![Captura de pantalla del editor de Unreal con la sección de empaquetado expandida en la configuración del proyecto](images/unreal-publishing-img-02.png)

3. Expanda la sección **Imágenes** y actualice las imágenes de almacenamiento predeterminadas con las texturas que representan la aplicación de la Tienda.  También puede activar la casilla **logotipo 3D** para cargar un archivo .glb para usarlo como un cubo dinámico 3D al iniciar la aplicación:

![Captura de pantalla del editor de Unreal con la sección de imágenes expandida en la configuración del proyecto](images/unreal-publishing-img-03.png)

4. Por último, seleccione **Generar nuevo** para generar un certificado de firma a partir del nombre del proyecto y el nombre distintivo de la empresa.  
    * Establezca un **color de fondo de icono**, que aparecerá en lugar de los píxeles transparentes en las imágenes de la tienda.
    * Expanda la lista desplegable y habilite la opción **Usar el entorno de Windows Store comercial** para ejecutarlo en dispositivos con bloqueo comercial y no desbloqueados para desarrollo.

![Captura de pantalla del editor de Unreal con la sección de generación de certificado expandida en la configuración del proyecto](images/unreal-publishing-img-04.png)

## <a name="optional-app-installer"></a>Instalador de aplicaciones opcionales

Se puede crear un archivo instalador de aplicación desde **Configuración del proyecto > HoloLens**, que se puede usar para distribuir la aplicación fuera del almacén.  Habilite la casilla **Debe crear el instalador de aplicación** y establezca una dirección URL o una ruta de acceso de red donde quiera que se almacene el appxbundle del juego.  

![Captura de pantalla del editor de Unreal con la sección de instalador de aplicación expandida en la configuración del proyecto](images/unreal-publishing-img-05.png)

Cuando se empaqueta la aplicación, se generan los tipos appxbundle y appinstaller.  Cargue el appxbundle en la dirección URL de instalación y, a continuación, inicie appinstaller para instalar la aplicación desde la ubicación de red.

## <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Windows 10 SDK se incluye con el kit para la certificación de aplicaciones en Windows (WACK) para validar problemas comunes que podrían afectar a la carga de un paquete en el almacén.  Puede encontrar WACK en el directorio de kits de Windows, normalmente en la siguiente ruta de acceso: 

```
C:\Program Files (x86)\Windows Kits\10\App Certification Kit.
```

1. Una vez que el archivo appx esté empaquetado para su publicación, ejecute **appcertui.exe** y siga las indicaciones para examinar el archivo appx:

![Captura de pantalla de la aplicación que se selecciona para la validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-06.png)

2. Seleccione **Validar aplicación de la Tienda**:

![Captura de pantalla de la selección de validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-07.png)

3. Examine el appx en la sección superior y seleccione **Siguiente**:

![Captura de pantalla de la selección de prueba en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-08.png)

4. Seleccione **Siguiente** para ejecutar las pruebas y crear un informe:
    * Todas las pruebas disponibles que se pueden ejecutar en el equipo host estarán habilitadas de manera predeterminada.

![Captura de pantalla del progreso de la validación en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-09.png)

5. Espere a que finalicen las pruebas. Una vez que haya finalizado, la ventana final mostrará un resultado de superación o error, que se puede ver en el informe guardado.

![Captura de pantalla de los resultados del informe final en el kit para la certificación de aplicaciones en Windows](images/unreal-publishing-img-10.png)

## <a name="known-wack-failure-with-425"></a>Error conocido WACK con la versión 4.25

El complemento de Windows Mixed Reality en Unreal 4.25 producirá un error WACK porque algunos archivos binarios x64 se incluyen durante el empaquetado de HoloLens. El error tendrá el siguiente aspecto:

![Captura de pantalla de un resultado erróneo debido al analizador binario y a las API admitidas del kit para la certificación de aplicaciones de Windows](images/unreal-publishing-img-11.png)

Para solucionar el problema:
1. Para ir a la raíz del directorio de origen o instalación de Unreal, abra un proyecto de Unreal y haga clic con el botón derecho en el icono de Unreal de la barra de tareas.
2. Haga clic con el botón derecho en UE4Editor, seleccione Propiedades y vaya a la ruta de acceso de la entrada de **Ubicación**:

```
Open Engine\Plugins\Runtime\WindowsMixedReality\Source\WindowsMixedRealityHMD\WindowsMixedRealityHMD.Build.cs.
```

3. En **WindowsMixedRealityHMD.Build.cs**, modifique la **línea 32** de:

```cpp
if(Target.Platform != UnrealTargetPlatform.Win32)
```

a:

```cpp
if(Target.Platform == UnrealTargetPlatform.Win64)

```

4. Cierre Unreal, vuelva a abrir el proyecto y vuelva a empaquetarlo para HoloLens.  Vuelva a ejecutar WACK y el error habrá desaparecido. 

## <a name="see-also"></a>Consulte también

* [Envío de aplicaciones a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Kit para la certificación de aplicaciones en Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit)
* [Creación manual de un archivo Instalador de aplicación](https://docs.microsoft.com/windows/msix/app-installer/how-to-create-appinstaller-file)