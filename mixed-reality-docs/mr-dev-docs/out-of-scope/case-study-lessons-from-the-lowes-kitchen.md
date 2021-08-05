---
title: 'Caso práctico: lecciones de la cocina de Lowe'
description: El HoloLens quiere compartir algunos de los procedimientos recomendados derivados del proyecto de HoloLens Lowe.
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe's, HoloLens, cocina, caso práctico
ms.openlocfilehash: f2428a23e07d62156d38f43dfd5d6ddda20d57340d17908cf326ca9f37d223b9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210395"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a>Caso práctico: lecciones de la cocina de Lowe

El HoloLens quiere compartir algunos de los procedimientos recomendados derivados del proyecto de HoloLens Lowe. A continuación se muestra un vídeo de la HoloLens de Lowe que se muestra en la nota clave de Satya Ignite de 2016.
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a>Procedimientos recomendados HoloLens Lowe

Los dos vídeos cubren los procedimientos recomendados derivados de lowe's HoloLens Pilot que se encuentra en dos tiendas de Lowe's desde abril de 2016. Los temas clave son:
* Maximizar el rendimiento de un dispositivo móvil
* Creación de métodos de experiencia de usuario con un marco holográfico completo (segunda charla)
* Alineación de precisión (segunda charla)
* Experiencias holográficas compartidas (segunda charla)
* Interacción con los clientes (segunda charla)

## <a name="video-1"></a>Vídeo 1

**Maximizar el rendimiento de un dispositivo** HoloLens es un dispositivo no asociado con todo el procesamiento que tiene lugar en el dispositivo. Esto requiere una plataforma móvil y requiere una mentalidad similar a la creación de aplicaciones móviles. Microsoft recomienda que la aplicación HoloLens mantenga 60FPS para proporcionar una experiencia increíble para los usuarios. Tener fps bajo puede dar lugar a hologramas inestables.

Algunos de los aspectos más importantes que hay que tener en cuenta al desarrollar en HoloLens es la optimización y descimación de recursos, mediante sombreadores personalizados (disponibles de forma gratuita en [el HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)). Otra consideración importante es medir la velocidad de fotogramas desde el principio del proyecto. En función del proyecto, el orden de visualización de los recursos también puede ser un gran colaborador.
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a>Vídeo 2

**Creación de métodos de experiencia de usuario con un marco holográfico completo** Es importante comprender la colocación de hologramas en un mundo físico. Con Lowe's se habla de diferentes métodos de experiencia de usuario que ayudan a los usuarios a experimentar hologramas de cerca mientras siguen viendo el entorno más grande de los hologramas.

**Alineación de precisión** Para el escenario de Lowe, era fundamental para la experiencia tener una alineación de precisión de los hologramas con la cocina física. Analizamos técnicas que ayudan a garantizar una experiencia que convencía a los usuarios de que su entorno físico ha cambiado.

**Experiencias holográficas compartidas** Las parejas son la forma principal de consumir la experiencia de Lowe. Una persona puede cambiar el contador y la otra verá los cambios. Esto se denomina "experiencias compartidas".

**Interacción con los clientes** Los diseñadores de Lowe no usan una HoloLens, pero necesitan ver lo que ven los clientes. Mostramos cómo capturar lo que el cliente ve en una aplicación para UWP.
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
