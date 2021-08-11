---
title: Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)
description: Aprenda a crear selectores de aplicaciones 3D y logotipos para aplicaciones y juegos de Win32 VR para el entorno menú Inicio y el hogar.
author: thmignon
ms.author: thmignon
ms.date: 07/12/2018
ms.topic: article
keywords: 3D, logotipo, icono, modelado, iniciador, iniciador 3D, icono, cubo en directo, win32, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, manifiesto
ms.openlocfilehash: 60eb4f543f287e833033c8e1852e2a85c6040d3c76455aadaca4b37c0a632573
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198771"
---
# <a name="implement-3d-app-launchers-win32-apps"></a>Implementación de iniciadores de aplicaciones 3D (aplicaciones Win32)

> [!NOTE]
> Esta característica solo está disponible para equipos que ejecutan la versión [más reciente de Windows Insider](https://insider.windows.com) (RS5), compilación 17704 y versiones más recientes.

La [Windows Mixed Reality principal es](../discover/navigating-the-windows-mixed-reality-home.md) el punto de partida en el que los usuarios se desatensan antes de iniciar aplicaciones. De forma predeterminada, debe iniciar aplicaciones y juegos envolventes de Win32 VR desde fuera del casco y no aparecerá en la lista "Todas las aplicaciones" de la Windows Mixed Reality menú Inicio. Si sigue las instrucciones de este artículo para implementar un iniciador de aplicaciones 3D, la experiencia envolvente de win32 VR se puede iniciar desde el entorno Windows Mixed Reality menú Inicio inicio.

Esto solo se aplica a las experiencias envolventes de Realidad virtual win32 distribuidas fuera de Steam. En el caso de las experiencias de realidad virtual distribuidas a través de [Steam,](../develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)hemos actualizado la versión beta de Windows Mixed Reality para [AirVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con los vuelos más recientes de Windows Insider RS5 para que los títulos de SteamVR se muestren en el Windows Mixed Reality menú Inicio en la lista "Todas las aplicaciones" automáticamente mediante un iniciador predeterminado. En otras palabras, el método descrito en este artículo no es necesario para los títulos de SteamVR y se reemplazará por el Windows Mixed Reality para la funcionalidad Beta de SteamVR.

## <a name="3d-app-launcher-creation-process"></a>Proceso de creación del iniciador de aplicaciones 3D

Hay tres pasos para crear un iniciador de aplicaciones 3D:
1. [Diseño y conceptos](3d-app-launcher-design-guidance.md)
2. [Modelado y exportación](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. Integrarlo en la aplicación (este artículo)

Los recursos 3D que se usarán como iniciadores de la aplicación deben crearse con las Windows Mixed Reality de creación [para](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md) garantizar la compatibilidad. Los recursos que no cumplan esta especificación de creación no se representarán en el Windows Mixed Reality principal.

## <a name="configuring-the-3d-launcher"></a>Configuración del iniciador 3D

Las aplicaciones Win32 aparecerán en la lista "Todas las aplicaciones" de la Windows Mixed Reality menú Inicio si crea un iniciador de aplicaciones 3D para ellas. Para ello, cree un archivo XML de manifiesto de [elementos](/previous-versions/windows/apps/dn393983(v=win.10)) visuales que haga referencia a la aplicación 3D Selector siga estos pasos:

1. Cree una **aplicación 3D para Selector GLB** de recursos (consulte Modelado [y exportación).](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
2. Cree un **[manifiesto de elementos visuales](/previous-versions/windows/apps/dn393983(v=win.10))** para la aplicación.
    1. Puede empezar con el ejemplo [siguiente.](#sample-visual-elements-manifest)  Consulte la documentación [completa del manifiesto de Visual Elements](/previous-versions/windows/apps/dn393983(v=win.10)) para obtener más detalles.
    2. Actualice **Square150x150Logo** y **Square70x70Logo** con un archivo PNG/JPG/GIF para la aplicación.
        * Se usarán para el logotipo 2D de la aplicación en la lista Windows Mixed Reality Todas las aplicaciones y para el menú Inicio en el escritorio.
        * La ruta de acceso del archivo se basa en la carpeta que contiene el manifiesto de Visual Elements.
        * Todavía debe proporcionar un icono de menú Inicio de escritorio para la aplicación a través de los mecanismos estándar. Puede estar directamente en el archivo ejecutable o en el acceso directo que cree. Por ejemplo, a través de IShellLink::SetIconLocation.
        * *Opcional:* Puede usar un archivo resources.pri si quiere que MRT proporcione varios tamaños de recursos para diferentes escalas de resolución y temas de contraste alto.
    3. Actualice la **ruta de acceso de MixedRealityModel** para que apunte al GLB de la aplicación 3D Selector
    4. Guarde el archivo con el mismo nombre que el archivo ejecutable, con una extensión de ".VisualElementsManifest.xml" y guárdelo en el mismo directorio. Por ejemplo, para el archivo ejecutable "contoso.exe", el archivo XML adjunto se denomina "contoso.visualelementsmanifest.xml".
3. **Agregue un acceso directo** a la aplicación al escritorio Windows menú Inicio. Vea el [ejemplo siguiente para](#sample-app-launcher-shortcut-creation) obtener un ejemplo de implementación de C++. 
    * Crearlo en %ALLUSERSPROFILE%\Microsoft\Windows\Menú Inicio\Programas (equipo) o %APPDATA%\Microsoft\Windows\Menú Inicio\Programas (usuario)
    * Si una actualización cambia el manifiesto de elementos visuales o los recursos a los que hace referencia, el actualizador o el instalador deben actualizar el acceso directo para que se vuelva a realizar el análisis del manifiesto y se actualicen los recursos almacenados en caché.
4. *Opcional:* Si el acceso directo de escritorio no apunta directamente al archivo EXE de la aplicación (por ejemplo, si invoca un controlador de protocolo personalizado como "myapp://"), el menú Inicio no encontrará automáticamente el archivo de VisualElementsManifest.xml de la aplicación. Para resolver este problema, el acceso directo debe especificar la ruta de acceso al archivo del manifiesto de Visual Elements mediante System.AppUserModel.VisualElementsManifestHintPath (). Esto se puede establecer en el acceso directo mediante las mismas técnicas que System.AppUserModel.ID. No es necesario usar System.AppUserModel.ID, pero puede hacerlo si desea que el acceso directo coincida con el identificador de modelo de usuario de aplicación explícito de la aplicación si se usa uno.  Consulte la sección [de creación de accesos directos del iniciador](#sample-app-launcher-shortcut-creation) de aplicaciones de ejemplo a continuación para obtener un ejemplo de C++.

### <a name="sample-visual-elements-manifest"></a>Manifiesto de elementos visuales de ejemplo

```xml
<Application xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance">
  <VisualElements
    ShowNameOnSquare150x150Logo="on"
    Square150x150Logo="YOUR_APP_LOGO_150X150.png"
    Square70x70Logo=" YOUR_APP_LOGO_70X70.png"
    ForegroundText="light"
    BackgroundColor="#000000">
    <MixedRealityModel Path="YOUR_3D_APP_LAUNCHER_ASSET.glb">
        <SpatialBoundingBox Center="0,0,0" Extents="Auto" />
    </MixedRealityModel>
  </VisualElements>
</Application>
```

### <a name="sample-app-launcher-shortcut-creation"></a>Creación de métodos abreviados de iniciador de aplicaciones de ejemplo

El código de ejemplo siguiente muestra cómo puede crear un acceso directo en C++, incluida la invalidación de la ruta de acceso al archivo XML del manifiesto de Visual Elements. Tenga en cuenta que la invalidación solo es necesaria en los casos en los que el acceso directo no apunta directamente al archivo EXE asociado al manifiesto (por ejemplo, el acceso directo usa un controlador de protocolo personalizado como "myapp://").

#### <a name="sample-lnk-shortcut-creation-c"></a>Muestra. Creación de accesos directos de LNK (C++)

```cpp
#include <windows.h>
#include <propkey.h>
#include <shlobj_core.h>
#include <shlwapi.h>
#include <propvarutil.h>
#include <wrl.h>

#include <memory>

using namespace Microsoft::WRL;

#define RETURN_IF_FAILED(x) do { HRESULT hr = x; if (FAILED(hr)) { return hr; } } while(0)
#define RETURN_IF_WIN32_BOOL_FALSE(x) do { DWORD res = x; if (res == 0) { return HRESULT_FROM_WIN32(GetLastError()); } } while(0)

int wmain()
{
    RETURN_IF_FAILED(CoInitializeEx(nullptr, COINIT_APARTMENTTHREADED));

    ComPtr<IShellLink> shellLink;
    RETURN_IF_FAILED(CoCreateInstance(__uuidof(ShellLink), nullptr, CLSCTX_INPROC_SERVER, IID_PPV_ARGS(&shellLink)));
    RETURN_IF_FAILED(shellLink->SetPath(L"MyLauncher://launch/app-identifier"));

    // It is also possible to use an icon file in another location. For example, "C:\Program Files (x86)\MyLauncher\assets\app-identifier.ico".
    RETURN_IF_FAILED(shellLink->SetIconLocation(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.exe", 0 /*iIcon*/));

    ComPtr<IPropertyStore> propStore;
    RETURN_IF_FAILED(shellLink.As(&propStore));

    {
        // Optional: If the application has an explict Application User Model ID, then you should usually specify it in the shortcut.
        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"ExplicitAppUserModelID", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_ID, propVar));
        PropVariantClear(&propVar);
    }

    {
        // A hint path to the manifest is only necessary if the target path of the shortcut is not a file path to the executable.
        // By convention the manifest is named <executable name>.VisualElementsManifest.xml and is in the same folder as the executable
        // (and resources.pri if applicable). Assets referenced by the manifest are relative to the folder containing the manifest.

        //
        // PropKey.h
        //
        //  Name:     System.AppUserModel.VisualElementsManifestHintPath -- PKEY_AppUserModel_VisualElementsManifestHintPath
        //  Type:     String -- VT_LPWSTR  (For variants: VT_BSTR)
        //  FormatID: {9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}, 31
        //  
        //  Suggests where to look for the VisualElementsManifest for a Win32 app
        //
        // DEFINE_PROPERTYKEY(PKEY_AppUserModel_VisualElementsManifestHintPath, 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3, 31);
        // #define INIT_PKEY_AppUserModel_VisualElementsManifestHintPath { { 0x9F4C2855, 0x9F79, 0x4B39, 0xA8, 0xD0, 0xE1, 0xD4, 0x2D, 0xE1, 0xD5, 0xF3 }, 31 }

        PROPVARIANT propVar;
        RETURN_IF_FAILED(InitPropVariantFromString(L"C:\\Program Files (x86)\\MyLauncher\\apps\\app-identifier\\game.visualelementsmanifest.xml", &propVar));
        RETURN_IF_FAILED(propStore->SetValue(PKEY_AppUserModel_VisualElementsManifestHintPath, propVar));
        PropVariantClear(&propVar);
    }

    constexpr PCWSTR shortcutPath = L"%APPDATA%\\Microsoft\\Windows\\Start Menu\\Programs\\game.lnk";
    const DWORD requiredBufferLength = ExpandEnvironmentStrings(shortcutPath, nullptr, 0);
    RETURN_IF_WIN32_BOOL_FALSE(requiredBufferLength);

    const auto expandedShortcutPath = std::make_unique<wchar_t[]>(requiredBufferLength);
    RETURN_IF_WIN32_BOOL_FALSE(ExpandEnvironmentStrings(shortcutPath, expandedShortcutPath.get(), requiredBufferLength));

    ComPtr<IPersistFile> persistFile;
    RETURN_IF_FAILED(shellLink.As(&persistFile));
    RETURN_IF_FAILED(persistFile->Save(expandedShortcutPath.get(), FALSE));

    return 0;
}
```

#### <a name="sample-url-launcher-shortcut"></a>Muestra. Acceso directo del iniciador de direcciones URL 

```
[{9F4C2855-9F79-4B39-A8D0-E1D42DE1D5F3}]
Prop31=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.visualelementsmanifest.xml
Prop5=ExplicitAppUserModelID

[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,0

[InternetShortcut]
IDList=
URL=MyLauncher://launch/app-identifier
IconFile=C:\Program Files (x86)\MyLauncher\apps\app-identifier\game.exe
IconIndex=0
```

## <a name="see-also"></a>Consulte también

* [Ejemplo de modelo de realidad mixta](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/MixedRealityModel) que contiene un iniciador de aplicaciones 3D.
* [Guía de diseño del iniciador de aplicaciones 3D](3d-app-launcher-design-guidance.md)
* [Creación de modelos 3D para su uso en el Windows Mixed Reality principal](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [Implementación de iniciadores de aplicaciones 3D (aplicaciones para UWP)](implementing-3d-app-launchers.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](../discover/navigating-the-windows-mixed-reality-home.md)