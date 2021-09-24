---
title: Vista del espectador
description: Visualice los hologramas de un dispositivo externo para mostrar o grabar una experiencia de realidad mixta en una pantalla externa.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Vista del espectador, iPhone, iOS, iPad, OpenCV, cámara, ARKit, HoloLens, realidad mixta, MixedRealityToolkit, demo, grabar
ms.openlocfilehash: f30c745154056cda6b5ccf052efbbd0bb7f094ea
ms.sourcegitcommit: 5d13ff165f4d08a3b028935fb39539a45a30f7e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/15/2021
ms.locfileid: "127779471"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Vista del espectador para HoloLens y HoloLens 2

> [!WARNING]
> Microsoft retirará la vista del espectador de muestra debido a incompatibilidades con la versión del paquete del SDK de Azure Spatial Anchors en que se basa el ejemplo. Además, es posible que esta muestra deje de funcionar debido a otros cambios en el entorno de Unity a medida que los clientes se trasladan a compilaciones de LTS compatibles de 2019.
>
> Aunque, actualmente, Microsoft no invierte recursos para solucionar los problemas anteriores, es posible quitar la funcionalidad de Azure Spatial Anchors del ejemplo y confiar en tecnologías como códigos QR para la alineación.   Si los miembros de la comunidad envían solicitudes de incorporación de cambios para solucionar estos problemas, las revisaremos y aceptaremos por el momento.

![Marcador](images/SpecViewPhoneHero.jpg)

Cuando tiene un dispositivo HoloLens, es fácil olvidarse de que aquellos que no tienen ninguno no pueden ver las mismas maravillas de las que está disfrutando. Gracias a la vista de espectador, otros usuarios pueden ver lo que ve un usuario de HoloLens en una pantalla 2D. También es un enfoque rápido y asequible para grabar hologramas en HD con dispositivos móviles y obtener grabaciones de los hologramas de gran calidad con cámaras de vídeo.

## <a name="key-resources"></a>Recursos clave

* [**Vista del espectador en GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentación de la vista del espectador**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Ejemplos de la vista del espectador**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casos de uso

* Puedes grabar una experiencia de realidad mixta mediante un dispositivo iPhone o Android. Grabe en Full HD y aplique el suavizado de contornos y un sombreado a los hologramas para conseguir una forma rentable y rápida de grabar vídeos de los mismos.
* Haz streaming de experiencias de realidad mixta en directo a Apple TV directamente desde tu iPhone o iPad y sin retrasos.
* Comparte la experiencia con los invitados: permite que los usuarios sin HoloLens experimenten los hologramas directamente desde sus teléfonos o tabletas.

## <a name="current-features"></a>Características actuales

* Sincronización espacial de los hologramas, para que todos los usuarios vean los hologramas exactamente en el mismo lugar.
* Compatibilidad con iOS (dispositivos habilitados para ARKit) y Android (dispositivos habilitados para ARCore).
Varios invitados de iOS.
Grabación de vídeo + hologramas + sonido de ambiente + sonido del holograma.
Hoja compartida para que puedas guardar un vídeo, enviarlo por correo electrónico o compartirlo con otras aplicaciones compatibles.

![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)

En la tabla siguiente se muestran varias funcionalidades de la vista de espectador y sus características. Elige la opción que mejor se adapte a tus necesidades de grabación de vídeo:

|      Funcionalidad                                | Móvil                  |                    Cámara de vídeo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Calidad HD                           |         Full HD         |        Filmación de calidad profesional (determinada por la cámara de vídeo)      |
| Movimiento de la cámara simplificado                 |            ✔            |                      ✔                      |
| Vista en tercera persona                    |            ✔            |                      ✔                      |
| Se puede hacer streaming a pantallas           |            ✔            |                      ✔                      |
| Portátil                             |            ✔            |                                             |
| Inalámbrico                             |            ✔            |                                             |
| Hardware adicional necesario         |     Teléfono Android, iPhone    | HoloLens + plataforma + trípode + cámara de vídeo + equipo + Unity |
| Inversión en hardware                  |           Bajo            |                     Alto                    |
| Multiplataforma                       |           Android, iOS   |                                             |
| Contenido sincronizado                 |            ✔            |                      ✔                      |
| Duración de la instalación en tiempo de ejecución               |         Instantánea          |                     Lenta                    |
## <a name="see-also"></a>Consulte también

* [Captura de realidad mixta](/hololens/holographic-photos-and-videos) 
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)