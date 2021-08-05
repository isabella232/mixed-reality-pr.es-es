---
title: Mixed Reality de Spatial Data Packager
description: La Mixed Reality Spatial Data Packager está en desuso y ya no funciona en ninguna plataforma. En su lugar, se recomienda la herramienta Map Manager.
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe, MixedRealitySpatialDataPackager.exe, MixedRealitySpatialDataPackager
ms.openlocfilehash: 914e22c4e80385c93696ebd978000978e1e03f57706d466bdbb3cfcd5843f69e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213179"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Mixed Reality de Spatial Data Packager

>[!NOTE]
> EN DESUSO 
> 
> A partir del 1/8/2020, esta herramienta está en desuso y ya no funciona en ninguna plataforma. Se recomienda usar la [herramienta Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) en la Portal de dispositivos en su lugar. 
> 
> Esta herramienta y su funcionamiento se ofrecen tal y como están. Está sujeto a cambios sin previo aviso y es posible que no sea compatible con futuras versiones Windows o Windows Mixed Reality HMD. 


## <a name="download"></a>Descargar
 Descargue [MixedRealitySpatialDataPackager aquí](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mixed Reality Spatial Data Packager</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>Inicio rápido

La Mixed Reality Spatial Data Packager copia los datos espaciales de una aplicación de destino de un equipo a otro a través de un proceso de exportación e importación en dos pasos. La herramienta debe ejecutarse con privilegios de administrador y elimina los datos espaciales existentes durante la importación. La exportación deja intactos los datos espaciales existentes.

Requisitos y limitaciones clave:

1. La herramienta debe ejecutarse con privilegios de administrador 
2. Es posible que tenga que reiniciar el equipo si Portal de realidad mixta es inestable después de ejecutar la herramienta.
3. La herramienta no se ejecutará cuando se encuentren discrepancias o incompatibilidades en la versión de datos espaciales
4. La herramienta borrará los datos espaciales existentes durante la importación
5. Si se produce un error en el proceso de importación, los datos anteriores no se pueden restaurar a menos que se haya realizado una copia de seguridad mediante la exportación anterior.
6. La calidad de la funcionalidad de importación depende del modo de "solo lectura" para los datos del mapa espacial
***

## <a name="mapping-best-practices"></a>Procedimientos recomendados de asignación

1. Borrar mapas existentes de la Panel de control (Configuración -> Mixed Reality -> Environment -> Clear environment data)
2. Asegúrese de una iluminación suficiente para un buen seguimiento y, si ejecuta el modo de mapa bloqueado, intente mantener la misma iluminación.
3. Siempre que sea posible, mantenga bajo el intervalo dinámico de iluminación evitando áreas de iluminación alta junto a áreas oscuras y con sombra.
4. Minimizar superficies vacías y sin textura, por ejemplo, colocar una variedad de pósteres diferentes en las paredes blancas
5. Asignar el espacio sin objetos dinámicos en la escena, como mover personas
6. Bloquear el mapa al importar (disponible a través de Insider Preview)
7. Desbloquee el mapa y vuelva a examinar el entorno cuando el seguimiento de la calidad se degrada o cuando haya cambios en el entorno (iluminación o cambios en el diseño de objetos).
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>Ejecución Mixed Reality Spatial Data Packager con script complementario

Hemos proporcionado MRSpatialPackagerHelperScript.ps1 que ejecuta el empaquetador de mapas de las herramientas. 


Los parámetros de script se definen a continuación:

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Ejemplo de uso y salida del script de PowerShell

.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>Cómo exportar mediante MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

La exportación de mapas fuera del dispositivo genera dos archivos mapx, het.mapx y sa.mapx. Durante el proceso de exportación, se quitan todos los delimitadores espaciales, excepto la aplicación especificada y el límite creado por el usuario (si existe). El nombre de familia del paquete de origen debe coincidir con una aplicación instalada existente o se producirá un error en el archivo exe.

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>Cómo importar mediante MixedRealitySpatialDataPackager.exe
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
Import elimina los datos espaciales existentes y los reemplaza por los datos del directorio especificado. La entrada de nombre de la aplicación especifica el nombre del paquete de la aplicación de destino para el que se deben importar los delimitadores espaciales y el SID del usuario de destino especifica el usuario que debe tener acceso a los anclajes espaciales importados. El nombre de familia del paquete de destino y los SID de usuario deben coincidir con los valores existentes en el equipo o se producirá un error en el archivo exe.


***
## <a name="error-messages"></a>mensajes de error
Además, los mensajes de error siguientes también irán acompañados de un HRESULT.

### <a name="if-there-was-an-error-invalid-arguments"></a>Si se produjo un error, argumentos no válidos
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>Si el ejecutable no se ha ejecutado en modo de administrador
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>Si se produjo un error al habilitar o deshabilitar el controlador
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>Si se produjo un error al validar la versión de la base de datos espacial
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>Si se produjo un error al validar el nombre de familia del paquete proporcionado para la aplicación de importación y exportación de destino
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>Si se produjo un error al validar el SID del usuario
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>Si se produjo un error relacionado con los archivos de datos espaciales de destino o de origen
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>Si se produjo un error relacionado con el inicio y la detención de Spectrum/SharedRealitySvc
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```