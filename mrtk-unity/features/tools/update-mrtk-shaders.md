---
title: Herramienta de actualización de sombreador
description: Documentación sobre cómo actualizar sombreadores estándar de MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, desarrollo, MRTK
ms.openlocfilehash: 1f943d8ac7050b8607ae3a85af0a377a7460eb3b
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647101"
---
# <a name="updating-shaders"></a><span data-ttu-id="7441e-104">Actualizar sombreadores</span><span class="sxs-lookup"><span data-stu-id="7441e-104">Updating Shaders</span></span>

<span data-ttu-id="7441e-105">A partir de la versión 2.6.0, los sombreadores MRTK se están control de versiones a través de MRTK. Archivo Shaders.sentinel.</span><span class="sxs-lookup"><span data-stu-id="7441e-105">Starting with version 2.6.0, the MRTK shaders are being versioned via the MRTK.Shaders.sentinel file.</span></span> <span data-ttu-id="7441e-106">Al actualizar a una nueva versión de MRTK, puede aparecer el mensaje siguiente.</span><span class="sxs-lookup"><span data-stu-id="7441e-106">When upgrading to a new version of MRTK, the following message may appear.</span></span>

![Actualización del símbolo del sistema de sombreadores](../images/tools/UpdateShaderPrompt.png)

<span data-ttu-id="7441e-108">Al seleccionar **Sí** se indica a MRTK que sobrescriba el contenido de **los** sombreadores  >  **MRTK** de recursos con la versión más  >   reciente.</span><span class="sxs-lookup"><span data-stu-id="7441e-108">Selecting **Yes** instructs MRTK to overwrite the contents of **Assets** > **MRTK** > **Shaders** with the latest version.</span></span> <span data-ttu-id="7441e-109">Al seleccionar **No,** se conservarán los archivos actuales.</span><span class="sxs-lookup"><span data-stu-id="7441e-109">Selecting **No** will preserve the current files.</span></span> <span data-ttu-id="7441e-110">**Omitir** creará un archivo ( ) en `IgnoreUpdateCheck.sentinel`   >  **Sombreadores MRTK** de recursos  >  , lo que suprimirá futuras comprobaciones de actualización del sombreador.</span><span class="sxs-lookup"><span data-stu-id="7441e-110">**Ignore** will create a file (`IgnoreUpdateCheck.sentinel`) in **Assets** > **MRTK** > **Shaders**, which will suppress future shader update checks.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7441e-111">Al sobrescribir los archivos del sombreador, se perderán las modificaciones personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7441e-111">When overwriting the shader files, any custom modifications will be lost.</span></span> <span data-ttu-id="7441e-112">Asegúrese de realizar una copia de seguridad de los archivos de sombreador modificados antes de actualizar.</span><span class="sxs-lookup"><span data-stu-id="7441e-112">Be sure to backup any modified shader files before upgrading.</span></span>
>
> <span data-ttu-id="7441e-113">Si el proyecto se ha configurado para usar la canalización de representación universal (URP), anteriormente canalización de representación ligera (LWRP), vuelva **a** ejecutar Mixed Reality > **Toolkit** > **Utilities** >
>  **Upgrade MRTK Standard Shader for Lightweight Render Pipeline**(Actualizar el sombreador estándar de MRTK para la canalización de representación ligera).</span><span class="sxs-lookup"><span data-stu-id="7441e-113">If the project has been configured to use the Universal Render Pipeline (URP) - formerly Lightweight Render Pipeline (LWRP), please re-run **Mixed Reality** > **Toolkit** > **Utilities** >
**Upgrade MRTK Standard Shader for Lightweight Render Pipeline**.</span></span>

<span data-ttu-id="7441e-114">At también es posible comprobar si hay actualizaciones de sombreador en cualquier momento mediante **Mixed Reality** Toolkit Utilities Check for Shader Updates (Comprobar actualizaciones del sombreador) en la barra de menús del  >    >    >   Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="7441e-114">At is also possible to check for shader updates at any time using **Mixed Reality** > **Toolkit** > **Utilities** > **Check for Shader Updates** on the Unity Editor's menu bar.</span></span>

![Comprobación de actualizaciones del sombreador](../images/tools/ShaderUpdateMenu.png)

<span data-ttu-id="7441e-116">**La comprobación de actualizaciones del sombreador** no tiene en `IgnoreUpdateCheck.sentinel` cuenta el archivo y permite la actualización del sombreador a petición.</span><span class="sxs-lookup"><span data-stu-id="7441e-116">**Check for Shader Updates** disregards the `IgnoreUpdateCheck.sentinel` file and allows on-demand shader updating.</span></span>

> [!NOTE]
> <span data-ttu-id="7441e-117">No es necesario comprobar las actualizaciones del sombreador al importar los archivos .unitypackage de MRTK.</span><span class="sxs-lookup"><span data-stu-id="7441e-117">Checking for shader updates is not required when importing the MRTK .unitypackage files.</span></span>
