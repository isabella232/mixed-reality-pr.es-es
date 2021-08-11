---
title: Envío de aplicaciones a Microsoft Store
description: Explora el proceso de empaquetado, prueba y envío de aplicaciones de realidad mixta al Microsoft Store.
author: hferrone
ms.author: mazeller
ms.date: 11/13/2020
ms.topic: article
keywords: Microsoft Store, HoloLens, cascos envolventes, aplicación, uwp, envío, envío, filtros, metadatos, requisitos del sistema, palabras clave, wack, certificación, paquete, appx, merchandising, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual
ms.openlocfilehash: 5ea0d48b96ff91f51ff565c652d5ec294e994692dcc7881e626ea7817b05d876
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197760"
---
# <a name="submitting-an-app-to-the-microsoft-store"></a>Envío de aplicaciones a Microsoft Store

> [!IMPORTANT]
> Si va a enviar una aplicación de Unreal, asegúrese de seguir las instrucciones **[de publicación](../develop/unreal/unreal-publishing-to-store.md)** antes de continuar.

## <a name="prerequisites"></a>Requisitos previos

Tanto [HoloLens](/hololens/hololens1-hardware) como el equipo Windows 10 que encendido el casco envolvente [ejecutan](../discover/immersive-headset-hardware-details.md) aplicaciones de plataforma Windows universal. Tanto si va a enviar una aplicación que admita HoloLens, PC o ambos, el envío de la aplicación pasa por el [Centro de partners](https://partner.microsoft.com/dashboard).

Si aún no tiene una cuenta de Centro de partners [desarrollador,](https://developer.microsoft.com/store/register) regístrese para obtener una antes de pasar. Puede encontrar más información sobre las directrices de envío y las listas de comprobación en este [artículo de envíos de aplicaciones](/windows/uwp/publish/app-submissions).

> [!IMPORTANT]
> No podrá enviar ninguna aplicación a la cuenta de Microsoft Store si su cuenta de desarrollador de Centro de partners no puede realizar la comprobación de empleo. Póngase en contacto con el Centro de partners [de soporte técnico para](https://developer.microsoft.com/windows/support) obtener más detalles.

## <a name="packaging-a-mixed-reality-app"></a>Empaquetado de una Mixed Reality aplicación

Hay varios pasos para empaquetar una Mixed Reality aplicación, entre los que se incluyen:

* Preparar correctamente todos los recursos de imagen
* Elección de la imagen de icono que se muestra en el HoloLens menú Inicio
* Establecer el destino y la versión Windows mínima para la aplicación
* Establecimiento de las familias de dispositivos de destino en las dependencias de la aplicación
* Agregar metadatos para asociar la aplicación con el Microsoft Store
* Creación de un paquete de carga

Cada una de estas fases de envío se trata en su propia sección a continuación: se recomienda pasar por ellas secuencialmente y no dejar ninguna fuera en el primer intento de envío.

### <a name="prepare-image-assets-included-in-the-appx"></a>Preparación de los recursos de imagen incluidos en appx

Los siguientes recursos de imagen son necesarios para que las herramientas de creación de appx compilen la aplicación en un paquete appx, que es necesario para el envío al Microsoft Store. Puede obtener más información sobre las [directrices para los recursos de icono e icono](/windows/uwp/app-resources/images-tailored-for-scale-theme-contrast) en MSDN.

| Recurso requerido | Escala recomendada | Formato de imágenes | ¿Dónde se muestra el recurso? | 
|----------|----------|----------|------------------|
| Logotipo de Square 71x71 | Any |  PNG | N/D | 
| Logotipo de Square 150x150 | 150 x 150 (escala del 100 %) o 225 x 225 (escala del 150 %) | PNG | Inicio de pins y Todas las aplicaciones (si no se proporciona 310 x 310), Sugerencias de búsqueda en la tienda, Página de descripción de la tienda, Examinar tienda, Búsqueda de tienda | 
|  Logotipo ancho de 310 x 150 |  Any  |  PNG  |  N/D | 
|  Logotipo de la Tienda |  75 x 75 (escala del 150 %)  |  PNG  |  Centro de partners, Aplicación de informes, Escribir una revisión, Mi biblioteca | 
|  Pantalla de presentación |  930x450 (escala del 150 %)  |  PNG  |  Iniciador de aplicaciones 2D (pizarra) | 

Si va a desarrollar para HoloLens, hay otros recursos recomendados que puede aprovechar:

| Recursos recomendados | Escala recomendada | ¿Dónde se muestra el recurso? | 
|----------|----------|----------|
|  Logotipo de Square 310x310 |  310 x 310 (escala del 150 %) |  Inicio de pins y Todas las aplicaciones | 

### <a name="live-tile-requirements"></a>Icono dinámico requisitos

El menú Inicio en HoloLens usará la imagen de mosaico cuadrado incluida más grande de forma predeterminada. Las aplicaciones publicadas por Microsoft tienen un iniciador 3D opcional, que puede agregar a la aplicación siguiendo las instrucciones de implementación del iniciador de aplicaciones [3D.](implementing-3d-app-launchers.md)

### <a name="specifying-target-and-minimum-version-of-windows"></a>Especificar el destino y la versión mínima de Windows

Si la Mixed Reality incluye características específicas de una versión de Windows, es importante especificar las versiones de plataforma mínimas y de destino admitidas.

**Preste especial atención a las aplicaciones [destinadas Windows Mixed Reality cascos envolventes,](../discover/immersive-headset-hardware-details.md)que requieren al menos el Windows 10 Fall Creators Update (10.0; Compilación 16299) para funcionar correctamente.**

Se le pedirá que establezca el destino y la versión mínima de Windows cuando cree una nueva aplicación universal Windows Project en Visual Studio. Para los proyectos existentes, puede cambiar esta configuración en  el menú **Project** seleccionando<Propiedades de> nombre de la aplicación en la parte inferior del menú desplegable.

![Establecimiento de versiones mínimas y de plataforma de destino Visual Studio 2019](images/visual-studio-min-version-500px.png)<br>
*Establecer versiones de plataforma mínimas y de destino en Visual Studio*

### <a name="specifying-target-device-families"></a>Especificar familias de dispositivos de destino

Windows Mixed Reality aplicaciones (tanto para [HoloLens](/hololens/hololens1-hardware) como para [cascos envolventes)](../discover/immersive-headset-hardware-details.md)forman parte de la Plataforma universal de Windows, por lo que cualquier paquete de aplicación **con un Windows. La familia** [de dispositivos de](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily) destino universal se puede ejecutar HoloLens o Windows 10 equipos con cascos envolventes. Si no especifica una familia de dispositivos de destino en el manifiesto de aplicación, puede abrir accidentalmente la aplicación en dispositivos Windows 10 deseados. Siga los pasos que se indican a continuación para especificar la familia de dispositivos Windows 10 prevista y, a continuación, compruebe que ha establecido las familias de [dispositivos correctas](submitting-an-app-to-the-microsoft-store.md#submitting-your-mixed-reality-app-to-the-store) al cargar el paquete de aplicación en Centro de partners para Microsoft Store envío.

* Para establecer este campo en Visual Studio, haga clic con el botón derecho en **Package.appxmanifest** y seleccione **Ver** código y, a continuación, busque el **campo TargetDeviceFamily Name** . De forma predeterminada, debería tener un aspecto parecido al de la entrada siguiente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Si va a crear una **aplicación HoloLens,** puede asegurarse de que solo está instalada en HoloLens estableciendo la familia de dispositivos de **destino en Windows. Holográfica:** 

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

* Si la  aplicación requiere una funcionalidad de HoloLens 2, como el seguimiento de los ojos o las manos, puede asegurarse de que está destinada Windows la versión 18362 o posterior estableciendo la familia de dispositivos de destino **en Windows. Holographic** con **una versión MinVersion** de 10.0.18362.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.18362.0" MaxVersionTested="10.0.18362.0" />
</Dependencies>
```

* Si la aplicación se crea para **cascos envolventes** de Windows Mixed Reality , puede asegurarse de que solo está instalada en equipos de Windows 10 con el Windows 10 Fall Creators Update (necesario para Windows Mixed Reality) estableciendo la familia de dispositivos de destino **en Windows. Escritorio** con **minversion** de 10.0.16299.0:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
</Dependencies>
```

* Por último, si la aplicación está pensada para ejecutarse en **cascos envolventes** de **HoloLens** y Windows Mixed Reality , puede asegurarse de que la aplicación solo está disponible para esas dos familias de dispositivos y, al mismo tiempo, asegurarse de que cada destino tiene la versión de Windows mínima correcta mediante la inclusión de una línea para cada familia de dispositivos de destino con su MinVersion correspondiente:

```
<Dependencies>
   <TargetDeviceFamily Name="Windows.Desktop" MinVersion="10.0.16299.0" MaxVersionTested="10.0.16299.0" />
   <TargetDeviceFamily Name="Windows.Holographic" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
</Dependencies>
```

Para obtener más información sobre las familias de dispositivos de destino, lea la documentación [de TargetDeviceFamily para UWP.](/uwp/schemas/appxpackage/uapmanifestschema/element-targetdevicefamily)

### <a name="associate-app-with-the-store"></a>Asociación de una aplicación a la Tienda

Al asociar la aplicación a la Microsoft Store, se descargan los siguientes valores en el archivo de manifiesto de aplicación local de proyectos actuales:

* Nombre para mostrar del paquete
* Nombre del paquete
* Id. de publicador
* Nombre para mostrar del publicador
* Versión

Si va a reemplazar el archivo package.appxmanifest predeterminado por su propio archivo .xml personalizado, no puede asociar la aplicación con el Microsoft Store. La asociación de un archivo de manifiesto personalizado con store producirá un mensaje de error.

También puede probar los escenarios de compra y notificación si va a la solución de Visual Studio y selecciona Project > Store > Associate App with the Store (Asociar aplicación con la **Tienda).**

### <a name="creating-an-upload-package"></a>Creación de un paquete de carga

Siga las instrucciones de [Packaging Universal Windows apps for Windows 10](/previous-versions/windows/apps/hh454036(v=vs.140)#Anchor_2).

El último paso para crear un paquete de carga es validar el paquete mediante el kit Windows [App Certification Kit](#windows-app-certification-kit).

Si va a agregar un paquete específico HoloLens a un producto existente que está disponible en otras familias de dispositivos Windows 10, preste atención a: 

* [Cómo pueden afectar los números de versión a qué paquetes se entregan a clientes específicos](/windows/uwp/publish/package-version-numbering)
* [Cómo se distribuyen los paquetes a distintos sistemas operativos](/windows/uwp/publish/guidance-for-app-package-management)

La guía general es que el paquete con el número de versión más alto para un dispositivo es el distribuido por store.

En un escenario en el que hay una **Windows. Paquete** universal y un **Windows. Paquete holográfico** y el Windows. El paquete universal tiene un número de versión mayor, HoloLens usuario descargará el número de versión más alto Windows. Paquete universal en lugar del Windows. Paquete holográfico. 

En los casos en los que el escenario anterior no es el resultado que busca, hay varias soluciones disponibles:

* Asegúrese de que los paquetes específicos de la plataforma, como Windows. Holographic, siempre tiene un número de versión mayor que los paquetes independientes de la plataforma, como Windows. Universal
* No empaquete aplicaciones como Windows. Universal si también tiene paquetes específicos de la plataforma: en su lugar, empaquete el Windows. Paquete universal para las plataformas específicas en las que desea que esté disponible.
* Cree un único Windows. Paquete universal que funciona en todas las plataformas. La compatibilidad con esta opción no es excelente en este momento, por lo que se recomiendan las soluciones anteriores.

>[!NOTE]
> Para admitir la aplicación en HoloLens (1.ª generación) y HoloLen 2, debe cargar dos paquetes de aplicación. uno que contiene x86 para HoloLens (1.ª generación) y otro que contiene ARM o ARM64 para HoloLens 2. 
> 
> Si incluye ARM y ARM64 en el paquete, la versión ARM64 será la que se usa en HoloLens 2. 

>[!NOTE]
> Puede declarar un único paquete para que sea aplicable a varias familias de dispositivos de destino.

## <a name="testing-your-app"></a>Prueba de la aplicación

### <a name="windows-app-certification-kit"></a>Kit para la certificación de aplicaciones en Windows

Al crear paquetes de aplicación para enviarlos a Centro de partners a través de Visual Studio, el Asistente para crear paquetes de aplicaciones le pide que ejecute el Kit de certificación de aplicaciones de Windows en los paquetes que se crean. Para tener un proceso de envío sin problemas a la Tienda, es mejor comprobar que la copia local de la aplicación supera las pruebas del Kit de certificación de aplicaciones de Windows antes de enviarlas [a](/previous-versions/windows/apps/jj657973(v=win.10)) store. Actualmente no se Windows la ejecución del Kit de certificación de HoloLens aplicación en un equipo remoto.

### <a name="run-on-all-targeted-device-families"></a>Ejecutar en todas las familias de dispositivos de destino

La Windows universal permite crear una sola aplicación que se ejecuta en todas las familias de Windows 10 dispositivos. Sin embargo, no garantiza que las aplicaciones universales Windows solo funcionen en todas las familias de dispositivos. Es importante probar la [aplicación en cada](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md) una de las familias de dispositivos elegidas para garantizar una buena experiencia.

## <a name="submitting-your-mixed-reality-app-to-the-store"></a>Envío de Mixed Reality aplicación a la Tienda

Si va a enviar una aplicación Mixed Reality basada en un proyecto de Unity, consulte primero [este vídeo.](https://channel9.msdn.com/Blogs/One-Dev-Minute/How-to-publish-your-Unity-game-as-a-UWP-app)

En general, enviar una aplicación Windows Mixed Reality que funcione en HoloLens o cascos envolventes es igual que enviar cualquier aplicación para UWP al Microsoft Store. Una vez que haya creado [la aplicación reservando](/windows/uwp/publish/create-your-app-by-reserving-a-name)su nombre, siga la lista [de comprobación de envío de UWP](/windows/uwp/publish/app-submissions).

Una de las primeras cosas que hará es seleccionar [una categoría y subcategoría](/windows/uwp/publish/category-and-subcategory-table) para la experiencia Mixed Reality usuario. Es importante que elija la **categoría más precisa para la aplicación.** Las categorías ayudan a convertir la aplicación en las categorías de Store correctas y a asegurarse de que se muestra con las consultas de búsqueda pertinentes. **La inclusión** del título de VR como un juego no dará lugar a una mejor exposición para la aplicación y puede impedir que se muestre en categorías que sean más apropiadas y menos abarrotadas.

Sin embargo, hay cuatro áreas clave en el proceso de envío en las que querrá realizar Mixed Reality selecciones específicas:
1. En la **[sección Declaraciones de productos](submitting-an-app-to-the-microsoft-store.md#mixed-reality-product-declarations)** en [Propiedades](/windows/uwp/publish/enter-app-properties).
2. En la sección **[Requisitos del](submitting-an-app-to-the-microsoft-store.md#mixed-reality-system-requirements)** sistema en [Propiedades](/windows/uwp/publish/enter-app-properties).
3. En la sección **[Disponibilidad de la familia de dispositivos](submitting-an-app-to-the-microsoft-store.md#device-family-availability)** en [Paquetes](/windows/uwp/publish/upload-app-packages).
4. En varios de los campos **[descripción de Store página.](submitting-an-app-to-the-microsoft-store.md#store-listing-page)**

### <a name="mixed-reality-product-declarations"></a>Mixed Reality declaraciones de producto

En la **[página Propiedades](/windows/uwp/publish/enter-app-properties)** del proceso de envío de la aplicación, encontrará varias opciones relacionadas con Mixed Reality en la **[sección Declaraciones de](/windows/uwp/publish/app-declarations)** productos.

![Mixed Reality declaraciones de producto](images/product-declarations-900px.png)<br>
Mixed Reality declaraciones de producto

En primer lugar, debe identificar los tipos de dispositivos para los que la aplicación ofrece una Mixed Reality personalizada. La identificación de los tipos de dispositivo garantiza que la aplicación se incluye en Windows Mixed Reality colecciones en la Tienda.

Junto a "Esta experiencia está diseñada para Windows Mixed Reality en:"
* Active la **casilla PC** si la aplicación ofrece una experiencia de realidad virtual cuando hay un casco envolvente conectado al equipo del usuario. Se recomienda marcar esta casilla si la aplicación está configurada para ejecutarse exclusivamente en un casco envolvente o si se trata de un juego o aplicación de PC estándar que ofrece un modo Mixed Reality o contenido adicional cuando se conecta un casco.
* Active la **HoloLens** solo si la aplicación ofrece una experiencia holográfica cuando se ejecuta en HoloLens.
* Active **ambas** casillas si la aplicación ofrece Mixed Reality experiencia en ambos tipos de dispositivo.

Si seleccionó "PC" anteriormente, querrá establecer el "Mixed Reality configuración" (nivel de actividad). Esto solo se aplica Mixed Reality las experiencias de Mixed Reality que se ejecutan en equipos conectados a cascos envolventes, ya que las aplicaciones de Mixed Reality en HoloLens son de escala mundial y el usuario no define un límite durante la instalación.
* Elija **Sentado y de pie** si ha diseñado la aplicación para que el usuario permanezca en una posición. Por ejemplo, en un juego en el que tiene el control de una cabina de avión.
* Elija **Todas las experiencias** si la aplicación está diseñada con la intención de que el usuario se desasocia dentro de un límite establecido definido durante la instalación. Por ejemplo, puede ser un juego en el que se desvía y se evitan ataques.

### <a name="mixed-reality-system-requirements"></a>Mixed Reality requisitos del sistema

En la **[página Propiedades](/windows/uwp/publish/enter-app-properties)** del proceso de envío de la aplicación, encontrará varias opciones relacionadas con Mixed Reality en la **[sección Requisitos del](/windows/uwp/publish/enter-app-properties#system-requirements)** sistema.

![Requisitos del sistema](images/system-reqs-800px.png)<br>
Requisitos del sistema

En esta sección, identificará el hardware mínimo (necesario) y el hardware recomendado (opcional) para la Mixed Reality aplicación.

**Hardware de entrada:**

Use las casillas para saber a  los clientes potenciales si la aplicación admite el micrófono para la entrada de voz [),](../design/voice-input.md)el controlador **[de Xbox](../discover/hardware-accessories.md#bluetooth-gamepads)** o el controlador de juegos, o Windows Mixed Reality **[de movimiento.](../design/motion-controllers.md)** Esta información se mostrará en la página de detalles del producto de la aplicación en la Tienda y ayudará a que la aplicación se incluya en las colecciones de aplicaciones o juegos adecuadas. Por ejemplo, puede existir una colección para todos los juegos que admiten controladores de movimiento.

Tenga cuidado al seleccionar las casillas de "hardware mínimo" o "hardware recomendado" para los tipos de entrada. 

Por ejemplo: 
* Si el juego requiere controladores de movimiento, pero acepta la entrada de voz a través del micrófono, active la casilla "hardware mínimo" junto Windows Mixed Reality "controladores de movimiento", pero la casilla "hardware recomendado" junto a "Micrófono". 
* Si el juego se puede reproducir con un controlador xbox, un controlador de juego o controladores de movimiento, puedes activar la casilla "hardware mínimo" junto a "Controlador de Xbox o controlador de juegos" y seleccionar la casilla "hardware recomendado" junto a "controladores de movimiento de Windows Mixed Reality", ya que es probable que los controladores de movimiento ofrecrán un paso superior en la experiencia del controlador de juegos.

**Windows Mixed Reality casco envolvente:**

Indicar si se necesita un casco envolvente para usar la aplicación, o si es opcional, es fundamental para la satisfacción del cliente y la educación.

Si la aplicación solo *se puede* usar a través de un casco envolvente, active la casilla "hardware mínimo" junto a "Windows Mixed Reality casco envolvente". Esto se mostrará en la página de detalles del producto de la aplicación en la Tienda como una advertencia encima del botón de compra para que los clientes no piensen que están comprando una aplicación que funcionará en su equipo como una aplicación de escritorio tradicional.

Si la aplicación se ejecuta en el escritorio como una aplicación de PC tradicional, pero ofrece una experiencia de realidad virtual cuando se conecta un casco envolvente (si el contenido completo de la aplicación está disponible o solo una parte), active la casilla "hardware recomendado" junto Windows Mixed Reality "casco envolvente". No aparecerá ninguna advertencia encima del botón de compra en la página de detalles del producto de la aplicación si la aplicación funciona como una aplicación de escritorio tradicional sin un casco envolvente conectado.

**Especificaciones de PC:**

Si desea que la aplicación llegue al máximo de Windows Mixed Reality usuarios de casco envolvente [posible,](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) tenga como destino las especificaciones de pc para Windows Mixed Reality equipos con gráficos [integrados.](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

Si la aplicación Mixed Reality tiene como destino los requisitos mínimos de pc de Windows Mixed Reality o necesita una configuración de equipo específica como la GPU dedicada de un [Windows Mixed Reality Ultra PC]( , debe agregar las especificaciones de pc pertinentes en la columna https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines "hardware mínimo".

Si la aplicación Mixed Reality está diseñada para mejorar el rendimiento u ofrece gráficos de mayor resolución en una tarjeta gráfica o configuración de PC determinada, debe incluir las especificaciones de equipo pertinentes en la columna "hardware recomendado".

Esto solo se aplica si la aplicación Mixed Reality usa un casco envolvente conectado a un equipo. Si la Mixed Reality solo se ejecuta en HoloLens, no tendrá que indicar las especificaciones del equipo, ya que HoloLens solo tiene una configuración de hardware.

### <a name="device-family-availability"></a>Disponibilidad de familias de dispositivos

Si ha empaquetado la [aplicación](https://docs.microsoft.com/windows/uwp/publish/app-package-requirements) correctamente en Visual Studio, cargarla en la página Paquetes debe generar una tabla con las familias de dispositivos disponibles.

![Tabla de disponibilidad de la familia de dispositivos](images/device-family-table-900px.png)<br>
Tabla de disponibilidad de la familia de dispositivos

Si la Mixed Reality aplicación funciona en cascos envolventes, se debe seleccionar al menos "Windows 10 Desktop" en la tabla. Si la Mixed Reality aplicación funciona en HoloLens, se debe seleccionar al menos "Windows 10 Holographic". Si la aplicación se ejecuta en ambos tipos Windows Mixed Reality casco, se deben seleccionar "Windows 10 Desktop" y "Windows 10 Holographic".

>[!TIP]
>Muchos desarrolladores se producen errores al cargar el paquete de la aplicación relacionados con discrepancias entre el manifiesto del paquete y la información de la cuenta de la aplicación o del publicador en Centro de partners. Estos errores a menudo se pueden evitar iniciando sesión en Visual Studio con la misma cuenta asociada a la cuenta de desarrollador de Windows (la que se usa para iniciar sesión en Centro de partners). Si usa la misma cuenta, podrá asociar la aplicación a su identidad en el Microsoft Store antes de empaquetarla.

![Asocie la aplicación a la Microsoft Store](images/associate-your-app-700px.png)<br>
Asocie la aplicación a la Microsoft Store en Visual Studio

### <a name="store-listing-page"></a>descripción de Store página

En la [descripción de Store](/windows/uwp/publish/create-app-store-listings) del proceso de envío de la aplicación, hay varios lugares en los que puede agregar información útil sobre la Mixed Reality aplicación.

>[!IMPORTANT]
>Para asegurarse de que la aplicación se clasifica correctamente por la Tienda y se hace reconocible para los clientes de Windows Mixed Reality, debe agregar **"Windows Mixed Reality"** como uno de los "términos de búsqueda" de la aplicación (puede encontrar términos de búsqueda expandiendo la sección "Campos compartidos").

![Agregar Windows Mixed Reality para buscar términos](images/search-terms-800px.png)<br>
Agregar "Windows Mixed Reality" para buscar términos

## <a name="offering-a-free-trial-for-your-game-or-app"></a>Oferta de una evaluación gratuita para el juego o la aplicación

En muchos casos, los consumidores no tendrán experiencia con la realidad virtual antes de comprar un casco Windows Mixed Reality envolvente. Es posible que no sepan qué esperar de juegos intensos o que conozcan su propio umbral de confort en experiencias envolventes. Muchos clientes también pueden probar un casco Windows Mixed Reality envolvente en equipos que no están distintivos [como Windows Mixed Reality equipos](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines). Debido a estas consideraciones, se recomienda [](/windows/uwp/publish/set-app-pricing-and-availability#free-trial) encarecidamente que considere la posibilidad de ofrecer una evaluación gratuita para la aplicación Mixed Reality de pago o juego.

## <a name="see-also"></a>Consulte también
* [¿Qué es Mixed Reality?](../discover/mixed-reality.md)
* [Introducción al desarrollo](../develop/development.md)
* [Vistas de aplicación](../design/app-views.md)
* [Descripción del rendimiento de Mixed Reality](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Rendimiento Recomendaciones para Unity](../develop/unity/performance-recommendations-for-unity.md)
* [Prueba de una aplicación en HoloLens](../develop/platform-capabilities-and-apis/testing-your-app-on-hololens.md)
* [Windows Mixed Reality de compatibilidad de hardware de equipo mínimo](/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)