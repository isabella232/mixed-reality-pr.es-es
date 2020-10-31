---
title: Habilitación de la seguridad de conexión para Holographic Remoting
description: En esta página se explica cómo configurar la comunicación remota holográfica para usar conexiones cifradas y autenticadas entre el reproductor y las aplicaciones remotas.
author: markkeinz
ms.author: makei
ms.date: 10/29/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: fcacac76e65fa884433afca9f568c5c0211dd570
ms.sourcegitcommit: 979967d6841d8fa64cf1d6cf3ae532b736ed3bd1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102304"
---
# <a name="enabling-connection-security-for-holographic-remoting"></a>Habilitación de la seguridad de conexión para Holographic Remoting

>[!IMPORTANT]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

Esta página proporciona información general sobre la seguridad de red para Holographic Remoting. Encontrará información sobre

* seguridad en el contexto de Holographic Remoting y por qué podría necesitarlo
* medidas recomendadas basadas en diferentes casos de uso
* implementación de la seguridad en la solución de Holographic Remoting

## <a name="overview"></a>Información general

Holographic Remoting intercambia información a través de una red. Si no se aplica ninguna medida de seguridad, los adversarios en la misma red puede poner en peligro la integridad de la comunicación o acceder a la información confidencial.

Las aplicaciones de ejemplo y el reproductor de comunicación remota holográfica en la tienda Windows tienen la seguridad deshabilitada. Esto hace que los ejemplos sean más fáciles de entender. También le ayuda a empezar a trabajar más rápidamente con el desarrollo.

Sin embargo, para las pruebas de campo o el uso de producción, se recomienda encarecidamente habilitar la seguridad en la solución de acceso remoto holográfica.

La seguridad de Holographic Remoting, cuando se configura correctamente para su caso de uso, ofrece las siguientes garantías:

* **Autenticidad:** tanto el reproductor como la aplicación remota pueden estar seguros de que el otro lado es quien dice ser
* **Confidencialidad:** ningún tercero puede leer la información intercambiada entre el reproductor y la aplicación remota
* **Integridad:** el reproductor y el remoto pueden detectar cualquier cambio en tránsito a su comunicación

>[!TIP]
>Para poder usar las características de seguridad, debe implementar un [reproductor personalizado](holographic-remoting-create-player.md) y una [aplicación remota personalizada](holographic-remoting-create-host.md).

## <a name="planning-the-security-implementation"></a>Planeación de la implementación de seguridad

Cuando se habilita la seguridad en Holographic Remoting, la biblioteca remota habilitará automáticamente el cifrado y las comprobaciones de integridad de todos los datos intercambiados a través de la red.

Sin embargo, garantizar la correcta autenticación requiere algún trabajo adicional. Lo que debe hacer exactamente depende de su caso de uso y el resto de esta sección trata de determinar los pasos necesarios.

>[!IMPORTANT]
> Este artículo solo puede proporcionar instrucciones generales. Si no está seguro, considere la posibilidad de consultar a un experto en seguridad que pueda proporcionarle orientación específica para su caso de uso.

En primer lugar, se usa la terminología siguiente: al describir las conexiones de red, se utilizarán los términos _cliente_ y _servidor_ . El servidor es el lado que escucha las conexiones entrantes en una dirección de extremo conocida y el cliente es el que se conecta al punto de conexión del servidor.

>[!NOTE]
> Los roles de servidor y cliente no están asociados a si una aplicación actúa como un reproductor o como remota. Aunque los ejemplos tienen el reproductor en el rol de servidor, es fácil invertir los roles si se adapta mejor a su caso de uso.

### <a name="planning-the-server-to-client-authentication"></a>Planeación de la autenticación de servidor a cliente

El servidor utiliza certificados digitales para demostrar su identidad al cliente. El cliente valida el certificado del servidor durante la fase de protocolo de enlace de la conexión. Si el cliente no confía en el servidor, finalizará la conexión en este momento.

El modo en que el cliente valida el certificado de servidor y los tipos de certificados de servidor que se pueden usar dependen del caso de uso.

**Caso de uso 1:** El nombre de host del servidor no es fijo, o bien el servidor no se dirige en absoluto.

En este caso de uso, no es práctico (ni siquiera posible) emitir un certificado para el nombre de host del servidor. La recomendación aquí es validar la huella digital del certificado en su lugar. Al igual que una huella digital humana, la huella digital identifica de forma única un certificado.

Es importante comunicar la huella digital al cliente fuera de banda. Esto significa que no se puede enviar a través de la misma conexión de red que se usa para la comunicación remota. En su lugar, puede escribirlo manualmente en la configuración del cliente o para que el cliente examine un código QR.

**Caso de uso 2:** Se puede tener acceso al servidor a través de un nombre de host estable.

En este caso de uso, el servidor tiene un nombre de host específico y sabe que este nombre no es probable que cambie. Después, puede usar un certificado emitido para el nombre de host del servidor. La confianza se establecerá en función del nombre de host y la cadena de confianza del certificado.

Si elige esta opción, el cliente necesita conocer el nombre de host del servidor y el certificado raíz de antemano.

### <a name="planning-the-client-to-server-authentication"></a>Planeación de la autenticación de cliente a servidor

Los clientes se autentican en el servidor mediante un token de forma libre. Lo que debe contener este token dependerá de nuevo en el caso de uso:

**Caso de uso 1:** Solo tiene que comprobar la identidad de la aplicación cliente.

En este caso de uso, un secreto compartido puede ser suficiente. Este secreto debe ser lo suficientemente complejo como para que no se pueda adivinar.

Un secreto compartido bueno es un GUID aleatorio, que se especifica manualmente tanto en la configuración del cliente como del servidor. Para crear uno, por ejemplo, puede usar el `New-Guid` comando en PowerShell.

Asegúrese de que este secreto compartido nunca se comunica a través de canales no seguros. La biblioteca remota garantiza que el secreto compartido siempre se envíe cifrado y solo a los elementos del mismo nivel de confianza.

**Caso de uso 2:** También debe comprobar la identidad del usuario de la aplicación cliente.

Un secreto compartido no será suficiente para cubrir este caso de uso. En su lugar, puede usar tokens creados por un proveedor de identidades. Un flujo de trabajo de autenticación mediante un proveedor de identidades sería similar al siguiente:

* El cliente autoriza al proveedor de identidades y solicita un token
* El proveedor de identidades genera un token y lo envía al cliente.
* El cliente envía este token al servidor mediante la comunicación remota holográfica
* El servidor valida el token del cliente con el proveedor de identidades

Un ejemplo de un proveedor de identidades es la [plataforma de Microsoft Identity](https://docs.microsoft.com/azure/active-directory/develop/).

Al igual que en el caso de uso anterior, asegúrese de que estos tokens no se envían a través de canales no seguros o expuestos de otro modo.

## <a name="implementing-holographic-remoting-security"></a>Implementación de la seguridad de Holographic Remoting

Recuerde que debe implementar aplicaciones de reproductor y remotas personalizadas si desea habilitar la seguridad de la conexión. Puede usar los ejemplos proporcionados como puntos de partida para sus propias aplicaciones.

Para habilitar la seguridad, llame a `ListenSecure()` en lugar de `Listen()` y en `ConnectSecure()` lugar de `Connect()` para establecer la conexión remota.

Estas llamadas requieren que proporcione implementaciones de ciertas interfaces para proporcionar y validar información relacionada con la seguridad:

* El servidor debe implementar un proveedor de certificados y un validador de autenticación
* El cliente debe implementar un proveedor de autenticación y un validador de certificado.

Todas las interfaces tienen una función que le solicita que realice una acción, que recibe un objeto de devolución de llamada como parámetro. Con este objeto, puede implementar fácilmente el control asincrónico de la solicitud. Mantenga una referencia a este objeto y llame a la función de finalización cuando se complete la acción asincrónica. Se puede llamar a la función de finalización desde cualquier subproceso.

>[!TIP]
>La implementación de interfaces de WinRT se puede realizar fácilmente con C++/WinRT. En el capítulo [API de autor con C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) se describe con más detalle.

>[!IMPORTANT]
>`build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl`En el paquete de NuGet se incluye documentación detallada sobre la API relacionada con las conexiones seguras.

### <a name="implementing-a-certificate-provider"></a>Implementación de un proveedor de certificados

Los proveedores de certificados proporcionan a la aplicación de servidor el certificado que se va a usar. La implementación consta de dos partes:

1) Un objeto de certificado, que implementa la `ICertificate` interfaz:

    * `GetCertificatePfx()` debe devolver el contenido binario de un `PKCS#12` almacén de certificados. Un `.pfx` archivo contiene `PKCS#12` datos, por lo que su contenido se puede usar directamente aquí.
    * `GetSubjectName()` debe devolver el nombre descriptivo que identifica el certificado que se va a usar. Si no se ha asignado ningún nombre descriptivo al certificado, esta función debe devolver el nombre de sujeto del certificado.
    * `GetPfxPassword()` debe devolver la contraseña necesaria para abrir el almacén de certificados (o una cadena vacía si no se requiere ninguna contraseña).

2) Un proveedor de certificados que implementa la `ICertificateProvider` interfaz:
    * `GetCertificate()` debe construir un objeto de certificado y devolverlo llamando a `CertificateReceived()` en el objeto de devolución de llamada.

### <a name="implementing-an-authentication-validator"></a>Implementar un validador de autenticación

Los validadores de autenticación reciben el token de autenticación enviado por el cliente y responden con el resultado de la validación.

Implemente la `IAuthenticationReceiver` interfaz de la siguiente manera:

* `GetRealm()` debe devolver el nombre del dominio Kerberos de autenticación (un dominio HTTP usado durante el protocolo de enlace de la conexión remota).
* `ValidateToken()` debe validar el token de autenticación del cliente y llamar a `ValidationCompleted()` en el objeto de devolución de llamada con el resultado de la validación.

### <a name="implementing-an-authentication-provider"></a>Implementación de un proveedor de autenticación

Los proveedores de autenticación generan o recuperan el token de autenticación que se va a enviar al servidor.

Implemente la `IAuthenticationProvider` interfaz de la siguiente manera:

* `GetToken()` debe generar o recuperar el token de autenticación que se va a enviar. Una vez que el token esté listo, llame al `TokenReceived()` método en el objeto de devolución de llamada.

### <a name="implementing-a-certificate-validator"></a>Implementar un validador de certificado

Los validadores de certificado reciben la cadena de certificados enviada por el servidor y determinan si se puede confiar en el servidor.

Para validar los certificados, puede utilizar la lógica de validación del sistema subyacente. Esta validación del sistema puede admitir su propia lógica de validación o reemplazarla por completo. Si no pasa su propio validador de certificado al solicitar una conexión segura, se usará automáticamente la validación del sistema.

En Windows, la validación del sistema comprobará:

* Integridad de la cadena de certificados: los certificados forman una cadena coherente que termina en un certificado raíz de confianza
* Validez del certificado: el certificado del servidor se encuentra dentro del intervalo de tiempo de validez y se emite para la autenticación del servidor.
* Revocación: no se ha revocado el certificado
* Coincidencia de nombre: el nombre de host del servidor coincide con uno de los nombres de host para los que se emitió el certificado.

Implemente la `ICertificateValidator` interfaz de la siguiente manera:

 * `PerformSystemValidation()` debe devolver `true` si se debe realizar una validación del sistema tal y como se ha descrito anteriormente. En este caso, el resultado de la validación del sistema se pasa como entrada al `ValidateCertificate()` método.
* `ValidateCertificate()` debe validar la cadena de certificados y, a continuación, llamar a `CertificateValidated()` en la devolución de llamada pasada con el resultado de la validación final. Este método acepta la cadena de certificados, el nombre del servidor con el que se establece la conexión y si se debe forzar una comprobación de revocación. Si la cadena de certificados contiene varios certificados, el primero es el certificado del firmante.

>[!NOTE]
>Si el caso de uso requiere una forma de validación diferente (consulte el caso de uso de certificados #1 anterior), omita completamente la validación del sistema. En su lugar, use cualquier API o biblioteca que pueda controlar los certificados X. 509 con codificación DER para descodificar la cadena de certificados y realizar las comprobaciones necesarias para su caso de uso.

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación remota de control remoto de holografías](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
