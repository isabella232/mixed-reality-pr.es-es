---
title: Establecimiento de una conexión segura con Control remoto de holografías
description: En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 4006a317ed2ecfd7a1e67336a80a4e536d45e554
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691383"
---
# <a name="establishing-a-secure-connection-with-holographic-remoting"></a>Establecimiento de una conexión segura con Control remoto de holografías

>[!IMPORTANT]
>Esta guía es específica de Holographic Remoting en HoloLens 2.

En esta página se explica cómo establecer una conexión cifrada segura cuando se usa la comunicación remota holográfica.

Al streaming de contenido a HoloLens 2 a través de una red no segura, como un WiFi abierto o Internet, se recomienda encarecidamente usar una conexión cifrada.

>[!IMPORTANT]
>Incluso cuando se usa una red Wi-Fi local de confianza mediante una conexión cifrada, debe tenerse en cuenta.

Para poder usar una conexión cifrada, debe implementar un [reproductor personalizado](holographic-remoting-create-player.md) y una [aplicación remota personalizada](holographic-remoting-create-host.md).

El cifrado se logra mediante el uso de la implementación de TLS de las plataformas subyacentes.

## <a name="basics-of-an-encrypted-connection"></a>Conceptos básicos de una conexión cifrada

Los objetos siguientes deben implementarse para permitir un intercambio de certificados.

>[!TIP]
>La implementación de interfaces de WinRT se puede realizar fácilmente con C++/WinRT. En el capítulo [API de autor con C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/author-apis) se describe con más detalle.

>[!IMPORTANT]
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```En el paquete de NuGet se incluye documentación detallada sobre la API relacionada con las conexiones seguras.

1) Objeto de certificado, que necesita implementar la ```ICertificate``` interfaz.

    * Devuelve el contenido binario del certificado pfx a través del ```GetCertificatePfx``` método. Igual que el contenido binario de un archivo. pfx.
    * Devuelva el nombre del firmante del certificado a través de ```GetSubjectName``` .
    * Devuelva la contraseña pfx a través de ```GetPfxPassword``` . Devuelve una cadena vacía para un archivo PFX sin protección.

2) Un proveedor de certificados que implementa la ```ICertificateProvider``` interfaz, que proporciona un certificado cuando se le solicita a través del ```GetCertificate``` método.

3) Un validador de certificado que implementa la ```ICertificateValidator``` interfaz. Su tarea consiste en comprobar los certificados entrantes.
    * El ```PerformSystemValidation``` método debe devolver ```true``` cuando la plataforma subyacente debe validar la cadena de certificados entrante; de ```false``` lo contrario,.
    * ```ValidateCertificate``` el contexto del cliente llama a para solicitar la validación de un certificado. Este método acepta la cadena de certificados (con el primer certificado que es el certificado de sujeto), el nombre del servidor con el que se establece la conexión y si se debe forzar una comprobación de revocación. El resultado de la validación del sistema se proporcionará si se ha solicitado la validación por parte del sistema subyacente. Para continuar el procesamiento ```CertificateValidated``` con el resultado adecuado o ```Cancel``` para cancelar la validación, es necesario llamar a en el pasado ```ICertificateValidationCallback``` .

Además, para permitir el intercambio de un token seguro, es necesario implementar los objetos siguientes.

1) Un proveedor de autenticación que implementa la ```IAuthenticationProvider``` interfaz. ```GetToken```El contexto del cliente llama a su método para solicitar un token para la autenticación del cliente. Para continuar con el ```TokenReceived``` fin de proporcionar el token de autenticación y continuar el proceso de conexión o ```Cancel``` para cancelar el proceso, es necesario llamar a en el pasado ```IAuthenticationProviderCallback``` .
2) Receptor de autenticación que implementa la ```IAuthenticationReceiver``` interfaz. Su tarea consiste en validar los tokens entrantes.
    * El ```GetRealm``` método debe devolver el nombre del dominio Kerberos de autenticación.
    * El ```ValidateToken``` contexto de red del servidor llama al método para solicitar la validación de un token de autenticación del cliente. Para continuar con la llamada ```ValidationCompleted``` a la finalización de la validación o ```Cancel``` para rechazar la conexión de cliente. La conexión de cliente se admitirá o rechazará según el resultado de la validación que se haya pasado a ```ValidationCompleted``` . 

Una vez implementados estos objetos ```ListenSecure``` , es necesario llamar a en lugar de ```Listen``` y en ```ConnectSecure``` lugar de hacerlo ```Connect``` en el contexto remoto y en el contexto del reproductor, respectivamente. ```ListenSecure``` requiere un proveedor de certificados adicional y un receptor de autenticación a través de ```Listen``` . ```ConnectSecure``` requiere un proveedor de autenticación adicional y un validador de certificado ```Connect``` .

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación remota de control remoto de holografías](holographic-remoting-create-host.md)
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
