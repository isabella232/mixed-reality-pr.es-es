---
title: Habilitación de la seguridad de conexión para la comunicación remota holográfica
description: En esta página se explica cómo configurar la comunicación remota holográfica para usar conexiones cifradas y autenticadas entre el reproductor y las aplicaciones remotas.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota holográfica, casco de realidad mixta, casco de realidad mixta de Windows, casco de realidad virtual, seguridad, autenticación, servidor a cliente
ms.openlocfilehash: 6ac5284bdf9e5984fcf091b6502fb62a494e4fe8
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184656"
---
# <a name="enabling-connection-security-for-holographic-remoting-c"></a>Habilitación de la seguridad de conexión para la comunicación remota holográfica (C++)

>[!IMPORTANT]
>Esta guía es específica de la comunicación remota holográfica en HoloLens 2.

En esta página se proporciona información general sobre la seguridad de red para la comunicación remota holográfica. Encontrará información sobre

* seguridad en el contexto de la comunicación remota holográfica y por qué podría necesitarla
* medidas recomendadas basadas en distintos casos de uso
* implementar la seguridad en la solución de comunicación remota holográfica

## <a name="holographic-remoting-security"></a>Seguridad de comunicación remota holográfica

Holographic Remoting intercambia información a través de una red. Si no hay medidas de seguridad, los adversarios de la misma red pueden poner en peligro la integridad de la comunicación o acceder a información confidencial.

Las aplicaciones de ejemplo y holographic Remoting Player de Windows Store incluyen seguridad deshabilitada. Si lo hace, los ejemplos son más fáciles de entender. También le ayuda a empezar a trabajar más rápidamente con el desarrollo.

Para pruebas de campo o producción, se recomienda encarecidamente habilitar la seguridad en la solución de comunicación remota holográfica.

La seguridad en la comunicación remota holográfica, cuando se configura correctamente para su caso de uso, le ofrece las siguientes garantías:

* **Autenticidad: tanto** el reproductor como la aplicación remota pueden estar seguros de que el otro lado es quien dice ser.
* **Confidencialidad:** ningún tercero puede leer la información intercambiada entre el reproductor y la aplicación remota
* **Integridad: el** reproductor y el equipo remoto pueden detectar cualquier cambio en tránsito en su comunicación.

>[!IMPORTANT]
>Para poder usar características de seguridad, deberá [](holographic-remoting-create-player.md) implementar un reproductor personalizado y una aplicación remota personalizada mediante Windows Mixed Reality [API](holographic-remoting-create-remote-wmr.md) de [OpenXR.](holographic-remoting-create-remote-openxr.md)

>[!NOTE]
> A partir de la [versión 2.4.0,](holographic-remoting-version-history.md#v2.4.0) se pueden crear aplicaciones remotas mediante [la API de OpenXR.](../native/openxr.md) A continuación se puede encontrar información general sobre cómo [](#secure-connection-using-the-openxr-api)establecer una conexión segura en un entorno de OpenXR.

## <a name="planning-the-security-implementation"></a>Planeamiento de la implementación de seguridad

Al habilitar la seguridad en la comunicación remota holográfica, la biblioteca de comunicación remota habilitará automáticamente las comprobaciones de cifrado e integridad de todos los datos intercambiados a través de la red.

Sin embargo, garantizar la autenticación adecuada requiere algún trabajo adicional. Lo que debe hacer exactamente depende de su caso de uso y el resto de esta sección trata de averiguar los pasos necesarios.

>[!IMPORTANT]
> Este artículo solo puede proporcionar instrucciones generales. Si no está seguro, considere la posibilidad de consultar a un experto en seguridad que pueda proporcionar instrucciones específicas para su caso de uso.

En primer lugar, una terminología: al describir  las conexiones de red, se _usarán_ los términos cliente y servidor. El servidor es el lado que escucha las conexiones entrantes en una dirección de punto de conexión conocida y el cliente es el que se conecta al punto de conexión del servidor.

>[!NOTE]
> Los roles de cliente y servidor no están vinculados a si una aplicación actúa como reproductor o como remota. Aunque los ejemplos tienen el reproductor en el rol de servidor, es fácil invertir los roles si se ajusta mejor a su caso de uso.

### <a name="planning-the-server-to-client-authentication"></a>Planeamiento de la autenticación de servidor a cliente

El servidor usa certificados digitales para demostrar su identidad al cliente. El cliente valida el certificado del servidor durante la fase de protocolo de enlace de conexión. Si el cliente no confía en el servidor, finalizará la conexión en este momento.

La forma en que el cliente valida el certificado de servidor y qué tipos de certificados de servidor se pueden usar depende de su caso de uso.

**Caso de uso 1:** El nombre de host del servidor no es fijo o el nombre de host no se dirige al servidor.

En este caso de uso, no es práctico (ni incluso posible) emitir un certificado para el nombre de host del servidor. En su lugar, se recomienda validar la huella digital del certificado. Al igual que una huella digital humana, la huella digital identifica de forma única un certificado.

Es importante comunicar la huella digital al cliente fuera de banda. Esto significa que no se puede enviar a través de la misma conexión de red que se usa para la comunicación remota. En su lugar, podría escribirlo manualmente en la configuración del cliente o hacer que el cliente digitalizara un código QR.

**Caso de uso 2:** Se puede acceder al servidor a través de un nombre de host estable.

En este caso de uso, el servidor tiene un nombre de host específico y sabe que es probable que este nombre no cambie. A continuación, puede usar un certificado emitido para el nombre de host del servidor. La confianza se establecerá en función del nombre de host y la cadena de confianza del certificado.

Si elige esta opción, el cliente debe conocer el nombre de host del servidor y el certificado raíz de antemano.

### <a name="planning-the-client-to-server-authentication"></a>Planeación de la autenticación de cliente a servidor

Los clientes se autentican en el servidor mediante un token de forma libre. Lo que este token debe contener dependerá de nuevo del caso de uso:

**Caso de uso 1:** Solo tiene que comprobar la identidad de la aplicación cliente.

En este caso de uso, un secreto compartido puede ser suficiente. Este secreto debe ser lo suficientemente complejo como para que no se pueda adivinar.

Un buen secreto compartido es un GUID aleatorio, que se introduce manualmente en la configuración del servidor y del cliente. Para crear una, puede, por ejemplo, usar el `New-Guid` comando en PowerShell.

Asegúrese de que este secreto compartido nunca se comunica a través de canales no seguros. La biblioteca de comunicación remota garantiza que el secreto compartido siempre se envía cifrado y solo a pares de confianza.

**Caso de uso 2:** También debe comprobar la identidad del usuario de la aplicación cliente.

Un secreto compartido no será suficiente para cubrir este caso de uso. En su lugar, puede usar tokens creados por un proveedor de identidades. Un flujo de trabajo de autenticación mediante un proveedor de identidades tendría el siguiente aspecto:

* El cliente autoriza al proveedor de identidades y solicita un token.
* El proveedor de identidades genera un token y lo envía al cliente.
* El cliente envía este token al servidor a través de La comunicación remota holográfica
* El servidor valida el token del cliente con el proveedor de identidades.

Un ejemplo de un proveedor de identidades es [el Plataforma de identidad de Microsoft](/azure/active-directory/develop/).

Al igual que en el caso de uso anterior, asegúrese de que estos tokens no se envían a través de canales no seguros ni se exponen de otro modo.

## <a name="implementing-holographic-remoting-security"></a>Implementación de la seguridad de comunicación remota holográfica

Recuerde que debe implementar aplicaciones personalizadas remotas y de reproductor si desea habilitar la seguridad de conexión. Puede usar los ejemplos proporcionados como puntos de partida para sus propias aplicaciones.

Para habilitar la seguridad, llame `ListenSecure()` a en lugar de a y en lugar de a para establecer la conexión `Listen()` `ConnectSecure()` `Connect()` remota.

Estas llamadas requieren que proporcione implementaciones de determinadas interfaces para proporcionar y validar información relacionada con la seguridad:

* El servidor debe implementar un proveedor de certificados y un validador de autenticación
* El cliente debe implementar un proveedor de autenticación y un validador de certificados.

Todas las interfaces tienen una función que le solicita que tome medidas, que recibe un objeto de devolución de llamada como parámetro. Con este objeto, puede implementar fácilmente el control asincrónico de la solicitud. Mantenga una referencia a este objeto y llame a la función de finalización cuando se complete la acción asincrónica. Se puede llamar a la función de finalización desde cualquier subproceso.

>[!TIP]
>La implementación de interfaces de WinRT se puede realizar fácilmente mediante C++/WinRT. En [el capítulo Author APIs with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/author-apis) (Creación de API con C++/WinRT) se describe esto en detalle.

>[!IMPORTANT]
>Dentro del paquete NuGet contiene documentación detallada de `build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl` la API relacionada con conexiones seguras.

### <a name="implementing-a-certificate-provider"></a>Implementación de un proveedor de certificados

Los proveedores de certificados suministran a la aplicación de servidor el certificado que se usará. La implementación consta de dos partes:

1) Objeto de certificado, que implementa la `ICertificate` interfaz :

    * `GetCertificatePfx()` debe devolver el contenido binario de un `PKCS#12` almacén de certificados. Un archivo contiene datos, por lo que su contenido `.pfx` se puede usar directamente `PKCS#12` aquí.
    * `GetSubjectName()` debe devolver el nombre descriptivo que identifica el certificado que se usará. Si no se asigna ningún nombre descriptivo al certificado, esta función debe devolver el nombre de sujeto del certificado.
    * `GetPfxPassword()` debe devolver la contraseña necesaria para abrir el almacén de certificados (o una cadena vacía si no se requiere ninguna contraseña).

2) Un proveedor de certificados que implementa la `ICertificateProvider` interfaz :
    * `GetCertificate()` debe construir un objeto de certificado y devolverlo llamando a `CertificateReceived()` en el objeto de devolución de llamada.

### <a name="implementing-an-authentication-validator"></a>Implementación de un validador de autenticación

Los validadores de autenticación reciben el token de autenticación enviado por el cliente y responden con el resultado de la validación.

Implemente `IAuthenticationReceiver` la interfaz como se muestra a continuación:

* `GetRealm()` debe devolver el nombre del dominio de autenticación (un dominio HTTP usado durante el protocolo de enlace de conexión remota).
* `ValidateToken()` debe validar el token de autenticación de cliente y llamar `ValidationCompleted()` a en el objeto de devolución de llamada con el resultado de la validación.

### <a name="implementing-an-authentication-provider"></a>Implementación de un proveedor de autenticación

Los proveedores de autenticación generan o recuperan el token de autenticación que se va a enviar al servidor.

Implemente `IAuthenticationProvider` la interfaz como se muestra a continuación:

* `GetToken()` debe generar o recuperar el token de autenticación que se va a enviar. Una vez que el token esté listo, llame al `TokenReceived()` método en el objeto de devolución de llamada.

### <a name="implementing-a-certificate-validator"></a>Implementación de un validador de certificado

Los validadores de certificados reciben la cadena de certificados enviada por el servidor y determinan si el servidor puede ser de confianza.

Para validar certificados, puede usar la lógica de validación del sistema subyacente. Esta validación del sistema puede admitir su propia lógica de validación o reemplazarla por completo. Si no pasa su propio validador de certificado al solicitar una conexión segura, la validación del sistema se usará automáticamente.

En Windows, la validación del sistema comprobará lo siguiente:

* Integridad de la cadena de certificados: los certificados forman una cadena coherente que termina en un certificado raíz de confianza.
* Validez del certificado: el certificado del servidor está dentro de su intervalo de tiempo de validez y se emite para la autenticación del servidor.
* Revocación: el certificado no se ha revocado
* Coincidencia de nombre: el nombre de host del servidor coincide con uno de los nombres de host para los que se emitió el certificado.

Implemente `ICertificateValidator` la interfaz como se muestra a continuación:

 * `PerformSystemValidation()` debe devolver si se debe realizar una validación del sistema `true` como se describió anteriormente. En este caso, el resultado de la validación del sistema se pasa como una entrada al `ValidateCertificate()` método .
* `ValidateCertificate()` debe validar la cadena de certificados y, a continuación, llamar `CertificateValidated()` a en la devolución de llamada pasada con el resultado final de la validación. Este método acepta la cadena de certificados, el nombre del servidor con el que se establece la conexión y si se debe forzar una comprobación de revocación. Si la cadena de certificados contiene varios certificados, el primero es el certificado del firmantes.

>[!NOTE]
>Si su caso de uso requiere una forma diferente de validación (consulte el caso de uso del certificado #1 anterior), omita completamente la validación del sistema. En su lugar, use cualquier API o biblioteca que pueda controlar certificados X.509 codificados con DER para descodificar la cadena de certificados y realizar las comprobaciones necesarias para su caso de uso.

## <a name="secure-connection-using-the-openxr-api"></a>Conexión segura mediante la API de OpenXR

Cuando se usa [la API de OpenXR,](../native/openxr.md) todas las API relacionadas con la conexión segura están disponibles como parte de la `XR_MSFT_holographic_remoting` extensión OpenXR.

>[!IMPORTANT]
>Para obtener información sobre la API de extensión OpenXR de Holographic Remoting, consulte la especificación que se puede encontrar en el repositorio de github de ejemplos de [Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)

Los elementos clave para una conexión segura mediante `XR_MSFT_holographic_remoting` la extensión OpenXR son las siguientes devoluciones de llamada.
- `xrRemotingRequestAuthenticationTokenCallbackMSFT`, genera o recupera el token de autenticación que se va a enviar.
- `xrRemotingValidateServerCertificateCallbackMSFT`, valida la cadena de certificados.
- `xrRemotingValidateAuthenticationTokenCallbackMSFT`, valida el token de autenticación de cliente.
- `xrRemotingRequestServerCertificateCallbackMSFT`, proporcione a la aplicación de servidor el certificado que se usará.

Estas devoluciones de llamada se pueden proporcionar al entorno de ejecución de OpenXR de comunicación remota a través `xrRemotingSetSecureConnectionClientCallbacksMSFT` de y `xrRemotingSetSecureConnectionServerCallbacksMSFT` . Además, la conexión segura debe habilitarse a través del parámetro secureConnection en la estructura o la estructura en función de si usa `XrRemotingConnectInfoMSFT` `XrRemotingListenInfoMSFT` o `xrRemotingConnectMSFT` `xrRemotingListenMSFT` .

Esta API es similar a la API basada en IDL que se describe en Implementación de la seguridad [de comunicación remota holográfica.](#implementing-holographic-remoting-security) Sin embargo, en lugar de implementar interfaces, se supone que debe proporcionar implementaciones de devolución de llamada. Puede encontrar un ejemplo detallado en la aplicación [de ejemplo OpenXR](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="see-also"></a>Consulte también
* [Información general sobre la comunicación remota holográfica](holographic-remoting-overview.md)
* [Escritura de una aplicación remota de Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Escritura de una aplicación remota de Holographic Remoting mediante las API de OpenXR](holographic-remoting-create-remote-openxr.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de Holographic Remoting](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)