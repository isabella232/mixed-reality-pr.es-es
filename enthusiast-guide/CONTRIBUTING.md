---
title: Instrucciones de colaboración
description: Obtenga información sobre los pasos básicos y las directrices para contribuir a la guía del entusiasta de la realidad de Windows Mixed Reality. Agradecemos sus comentarios, ediciones, adiciones y ayuda.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, comentarios, centro de comentarios, errores
appliesto:
- Windows 10
ms.openlocfilehash: afb559937c2bde06d3c74c1c572aefec50502884
ms.sourcegitcommit: 9a93c9e9b3b088da942ac4386813ecf263c2e324
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97865440"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribución a la guía del entusiasta de la realidad mixta

Gracias por su interés en la guía de entusiastas. Agradecemos sus comentarios, ediciones, adiciones y ayuda para mejorar nuestros documentos. En esta página se describen los pasos básicos y las instrucciones para contribuir.

> [!IMPORTANT]
> Todos los repositorios que publican en docs.microsoft.com han adoptado el [Código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/). Para más información, consulte las [preguntas más frecuentes del código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene cualquier pregunta o comentario.<br>
>
> Las correcciones menores o aclaraciones de la documentación y los ejemplos de código de los repositorios públicos se rigen por los [Términos de uso del sitio docs.microsoft.com](https://docs.microsoft.com/legal/termsofuse). Los cambios importantes o nuevos generarán un comentario en la solicitud de incorporación de cambios para solicitarle que acepte el contrato de licencia de colaboración (CLA, por sus siglas en inglés) si no es un empleado de Microsoft. Necesitamos que rellene el formulario en línea para aceptar su solicitud de incorporación de cambios.

## <a name="before-you-start"></a>Antes de comenzar

Si aún no tiene una, deberá [crear una cuenta de github](https://github.com/join).

>[!NOTE]
>Si es un empleado de Microsoft, vincule su cuenta de GitHub a su alias de Microsoft en el [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/). Únase a las organizaciones **"Microsoft"** y **"MicrosoftDocs"** .

Al configurar la cuenta de GitHub, también se recomiendan estas precauciones de seguridad:
- Cree una [contraseña segura para la cuenta de github](https://github.com/settings/admin).
- Habilitar [la autenticación en dos fases](https://github.com/settings/two_factor_authentication/configure).
- Guarde los [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.
- Actualice la [configuración del perfil público](https://github.com/settings/profile).
   - Establezca su nombre y considere la posibilidad de establecer el *correo electrónico público* para *no mostrar la dirección de correo electrónico*.
   - Se recomienda cargar una imagen de perfil porque se muestra una miniatura en las páginas de docs en las que contribuye.
- Si tiene previsto usar la línea de comandos, considere la posibilidad de configurar el [Administrador de credenciales de Git para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). De este modo, no tendrá que escribir la contraseña cada vez que realice una contribución.

El sistema de publicación está asociado a GitHub, por lo que estos pasos son importantes. Aparecerá como autor o colaborador en cada artículo mediante el alias de GitHub.

## <a name="how-to-make-a-change"></a>Cómo hacer un cambio

| Para sugerir un cambio en los documentos, siga estos pasos: | Capturas de pantalla |
| :------------------- | :--------: |
| 1. Si está viendo una página de Docs.microsoft.com, haga clic en el botón **Editar** situado en la parte superior derecha de la página.  Se le redirigirá al archivo de origen Markdown correspondiente en el [repositorio de GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Botón Editar](images/edit_button.jpg) |
| 2. Si aún no tiene una cuenta de GitHub, haga clic en **registrarse** en la esquina superior derecha y cree una cuenta nueva. | ![Botón de suscripción](images/signup-for-github-button.png)|
| 3. en la página de GitHub correspondiente que se abre, haga clic en Editar (el icono de lápiz). | ![Botón de lápiz](images/pencil_button.jpg)|
| 4. en el panel Editar archivo, [actualice los metadatos de los archivos](#updating-metadata) y use el lenguaje Markdown para cambiar el contenido. ([Cómo escribir Markdown).](https://help.github.com/articles/basic-writing-and-formatting-syntax/)| ![Editar archivo](images/edit-in-github.png)|
| 5. Haga clic en vista previa de cambios para comprobar que el formato es el esperado. | ![Vista previa de los cambios](images/edit-in-github.png)|
| 6. cuando haya terminado, desplácese hasta la parte inferior de la página y haga clic en "proponer cambio de archivo"; se mostrará la página "comparando cambios", donde podrá comprobar los cambios. A continuación, haga clic en el botón "crear solicitud de incorporación de cambios" para enviar los cambios. Después de este paso, ya habrá terminado. | ![Propuesta de cambio](images/propose.jpg)|

Después de enviar los cambios (a través de una solicitud de incorporación de cambios), los revisará un miembro del equipo de documentación. Si se acepta la solicitud, las actualizaciones se publican en [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide) .

* Solo para la revisión interna, puede ver los cambios en [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Actualizar metadatos

Actualice los metadatos en la parte superior de cada artículo:
   * **título**: título de la página que aparece en la pestaña del explorador cuando se está viendo el artículo. Los títulos de página se utilizan para SEO e indexación, por lo que no cambie el título a menos que sea necesario (aunque esto es menos crítico antes de que la documentación sea pública).
   * **Descripción**: escriba una breve descripción del contenido del artículo, que aumenta la SEO y la detección.
   * **autor**: si es el propietario principal de la página, agregue aquí su alias de github.
   * **MS. Author**: si es el propietario principal de la página, agregue aquí su alias de Microsoft (no es necesario @microsoft.com , solo el alias).
   * **MS. Date**: actualice la fecha Si va a agregar contenido principal a la página, pero no para correcciones como aclaración, formato, gramática o ortografía.
   * **palabras clave**: ayuda de palabras clave en SEO (optimización del motor de búsqueda). Agregue palabras clave, separadas por una coma y un espacio, específicas de su artículo, pero sin puntuación después de la última palabra clave de la lista. No es necesario agregar palabras clave globales que se apliquen a todos los artículos, ya que se administran en otro lugar. 

### <a name="renaming-or-deleting-an-existing-article"></a>Cambiar el nombre o eliminar un artículo existente

Si el cambio cambiará el nombre o eliminará un artículo existente, asegúrese de agregar una redirección. De este modo, todos los usuarios con un vínculo al artículo existente seguirán en el lugar correcto. Las redirecciones las administra el .openpublishing.redirection.jsen el archivo en la raíz del repositorio.

Para agregar una redirección a .openpublishing.redirection.js, agregue una entrada a la `redirections` matriz:

```json
{
    "redirections": [
        {
            "source_path": "mixed-reality-docs/enthusiast-guide/old-article.md",
            "redirect_url": "new-article#section-about-old-topic",
            "redirect_document_id": false
        },
```

- `source_path`Es la ruta de acceso relativa del repositorio al artículo anterior que se va a quitar. Asegúrese de que la ruta de acceso comienza con `mixed-reality-docs/enthusiast-guide` y termina con `.md` .
- `redirect_url`Es la dirección URL pública relativa del artículo anterior al nuevo artículo. Asegúrese de que esta dirección URL **no** contiene `mixed-reality-docs/enthusiast-guide` o `.md` , ya que hace referencia a la dirección URL pública y no a la ruta de acceso del repositorio. Se permite la vinculación a una sección del nuevo artículo con `#section` . También puede usar una ruta de acceso absoluta a otro sitio, si es necesario.
- `redirect_document_id` indica si desea conservar el identificador de documento del archivo anterior. El valor predeterminado es `false`. Use `true` si desea conservar el `ms.documentid` valor de atributo del artículo redirigido. Si conserva el identificador de documento, los datos, como las vistas de página y las clasificaciones, se transferirán al artículo de destino. Haga esto si el redireccionamiento es principalmente un cambio de nombre y no un puntero a un artículo diferente que solo trata parte del mismo contenido.

Si agrega un redireccionamiento, asegúrese de eliminar también el archivo antiguo.

### <a name="creating-a-new-article"></a>Creación de un nuevo artículo

Use el siguiente flujo de trabajo para *crear nuevos artículos* en el repositorio de documentación a través de github en un explorador Web:

1. Cree una bifurcación fuera de la rama MicrosoftDocs/Mixed-Reality/Tree/docs/entusiasta-Guide "Master" (con el botón **bifurcar** en la parte superior derecha).

   ![Bifurcar la bifurcación principal.](images/forkbranch.png)
2. En la carpeta "Mixed-Reality/entusiasta-Guide", seleccione **crear nuevo archivo** en la parte superior derecha.
3. Crear un nombre de página para el artículo (usar guiones en lugar de espacios y no usar signos de puntuación ni apóstrofos) y anexar ". MD"

   ![Asigne un nombre a la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Asegúrese de crear el nuevo artículo desde la carpeta "Mixed Reality-docs/entusiastas". Puede confirmarlo comprobando "/Mixed-Reality-docs/Enthusiast-Guide" en la nueva línea de nombre de archivo.

4. En la parte superior de la página nueva, agregue el siguiente bloque de metadatos:

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. Rellene los campos de metadatos pertinentes según las instrucciones de la [sección anterior](#updating-metadata).
6. Escriba el contenido del artículo con los [conceptos básicos de Markdown](#markdown-basics).
7. Agregue una `## See also` sección en la parte inferior del artículo con vínculos a otros artículos relevantes.
8. Cuando termine, seleccione **confirmar nuevo archivo**.
9. Seleccione **nueva solicitud de incorporación** de cambios y mezcle la rama ' maestra ' de la bifurcación en MicrosoftDocs/Mixed-Reality/entusiasta-guía ' maestra ' (Asegúrese de que la flecha señala la manera correcta).

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality/entusiasta-Guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Trabajo con ramas

El [repositorio de github guía para entusiastas de realidad mixta](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) utiliza dos bifurcaciones principales: [maestra](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master), este contenido se puede revisar en el [sitio de ensayo](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide)y en [directo](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), para el contenido que aparece en el [sitio activo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide).

Al realizar contribuciones, envíe su solicitud de incorporación de cambios (PR) a la rama **Master** . Esta rama se puede ver en el sitio de ensayo y solo debe contener las contribuciones que están listas para ser publicadas. También puede crear y enviar una rama con su propio nombre de rama único que se puede seleccionar y ver en el sitio de ensayo. (La rama en **directo** solo se permite para el uso por parte de los administradores de contenido).

## <a name="markdown-basics"></a>Aspectos básicos de Markdown

Los siguientes recursos le ayudarán a aprender a editar la documentación con el lenguaje Markdown:

- [Markdown basics](https://help.github.com/articles/basic-writing-and-formatting-syntax/) (Conceptos básicos de Markdown)
- [Póster de referencia de Markdown a un vistazo](images/MarkdownPoster.pdf)
- [Recursos adicionales para escribir Markdown para docs.microsoft.com](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Agregar tablas

Debido a la forma en que docs.microsoft.com las tablas de estilos, no tendrán bordes ni estilos personalizados, aunque pruebe CSS en línea. Parecerá que funciona durante un breve período de tiempo, pero finalmente la plataforma eliminará el estilo de la tabla. Por tanto, planee con facilidad y mantenga las tablas sencillas. [Este es un sitio que facilita las tablas de Markdown](https://www.tablesgenerator.com/markdown_tables).

La [extensión docs Markdown para Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) también facilita la generación de tablas si usa [Visual Studio Code (consulte a continuación)](#using-visual-studio-code) para editar la documentación.

### <a name="adding-images"></a>Agregar imágenes

Tendrá que cargar las imágenes en la carpeta "Mixed Reality-docs/Images" del repositorio y, a continuación, hacer referencia a ellas correctamente en el artículo. Las imágenes se mostrarán automáticamente a tamaño completo, lo que significa que las imágenes grandes llenarán todo el ancho del artículo. Se recomienda ajustar el tamaño de las imágenes antes de cargarlas. El ancho recomendado es de entre 600 y 700 píxeles, aunque debe ajustarse verticalmente o reducirse si es una captura de pantalla densa o una fracción de una captura de pantalla, respectivamente.

>[!IMPORTANT]
>Solo puede cargar imágenes en el repositorio bifurcado antes de la combinación. Por lo tanto, si planea agregar imágenes a un artículo, deberá [usar Visual Studio Code](#using-visual-studio-code) para agregar las imágenes a la carpeta "images" de la bifurcación en primer lugar o asegurarse de que ha realizado lo siguiente en un explorador Web:
>
>1. Se ha bifurcado el repositorio MicrosoftDocs/Mixed Reality.
>2. Editó el artículo en la bifurcación.
>3. Cargó las imágenes a las que hace referencia en el artículo en la carpeta "Mixed Reality-docs/Images" de la bifurcación.
>4. Se creó una **solicitud de incorporación** de cambios para fusionar mediante combinación la bifurcación en la rama "principal" de MicrosoftDocs/Mixed Reality.
>
>Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Obtener una vista previa del trabajo

Mientras edita en GitHub a través de un explorador Web, puede seleccionar la pestaña de **vista previa** situada cerca de la parte superior de la página para obtener una vista previa del trabajo antes de confirmar. 

>[!NOTE]
>La vista previa de los cambios en review.docs.microsoft.com solo está disponible para los empleados de Microsoft

Empleados de Microsoft: una vez que las contribuciones se han combinado en la rama "principal", puede revisar el contenido antes de que se haga público en https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Busque el artículo mediante la tabla de contenido de la columna izquierda.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Edición en el explorador frente a edición con un cliente de escritorio

La edición en el explorador es la forma más sencilla de realizar cambios rápidos; sin embargo, hay algunas desventajas:

- No obtiene la revisión ortográfica.
- No obtiene ninguna vinculación inteligente a otros artículos (tiene que escribir manualmente el nombre de archivo del artículo).
- Puede ser una molestia para cargar y hacer referencia a las imágenes.

Si prefiere no tratar estos problemas, use un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par de [extensiones útiles](#useful-extensions) al contribuir.

## <a name="using-visual-studio-code"></a>Uso de Visual Studio Code

Por los motivos mencionados [anteriormente](#editing-in-the-browser-vs-editing-with-a-desktop-client), es posible que prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador Web. Se recomienda el uso de [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configurar

Siga estos pasos para configurar Visual Studio Code para trabajar con este repositorio:

1. En un explorador Web:
    1. Instale [git para su PC](https://git-scm.com/downloads).
    2. Instale [Visual Studio Code](https://code.visualstudio.com/).
    3. [Bifurcación MicrosoftDocs/Mixed-Reality](#creating-a-new-article) si todavía no lo ha hecho.
    4. En la bifurcación, seleccione **clonar o descargar** y copiar la dirección URL.
2. Cree un clon local de la bifurcación en Visual Studio Code:
    1. En el menú **Ver** , seleccione **paleta de comandos**.
    2. Escriba "git: Clone".
    3. Pegue la dirección URL que ha copiado.
    4. Elija dónde desea guardar el clon en su PC.
    5. Seleccione **abrir repositorio** en el menú emergente.

### <a name="editing-documentation"></a>Editar documentación

Use el siguiente flujo de trabajo para realizar cambios en la documentación con Visual Studio Code:

>[!NOTE]
>Todas las instrucciones para [Editar](#how-to-make-a-change) y [crear](#creating-a-new-article) artículos, y los [aspectos básicos de la edición de Markdown](#markdown-basics), de lo anterior se aplican también cuando se usa Visual Studio Code.

1. Asegúrese de que la bifurcación clonada esté actualizada con el repositorio oficial.
   1. En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar los cambios recientes de otros colaboradores en MicrosoftDocs/mixed-reality ' maestra ' en la bifurcación (Asegúrese de que la flecha señala el modo correcto).
      
      ![Sincronización de los cambios de MicrosoftDocs/Mixed-Reality en la bifurcación](images/sync_repos.PNG)
   2. En Visual Studio Code, seleccione el botón sincronizar para sincronizar la bifurcación recién actualizada con el clon local.
      
      ![Haga clic en la imagen del botón sincronizar](images/sync_clone.png)
2. Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.
   1. Edite uno o varios artículos (agregue imágenes a la carpeta "images" si es necesario).
   2. **Guarde** los cambios en el **Explorador**.
      
      ![Elija "guardar todo" en el explorador.](images/explorer_save.png)
   3. **Confirmar todos** los cambios en el **control de código fuente** (escribir mensaje de confirmación cuando se le solicite).
      
      ![Elegir "confirmar todo" en el control de código fuente](images/source_control_commit.png)
   4. Seleccione el botón **sincronizar** para volver a sincronizar los cambios con el origen (la bifurcación en GitHub).
      
      ![Haga clic en el botón sincronizar](images/sync_back.png)
3. En un explorador Web, cree una solicitud de incorporación de cambios para sincronizar nuevos cambios en la bifurcación de nuevo en MicrosoftDocs/mixed-reality ' maestra ' (Asegúrese de que la flecha señala la manera correcta).

   ![Cree una solicitud de incorporación de cambios de la bifurcación en MicrosoftDocs/Mixed-Reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensiones útiles

Las siguientes extensiones de Visual Studio Code son útiles al editar la documentación:

- La [extensión de Markdown de docs para Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) : use **Alt + M** para abrir un menú de opciones de creación de docs como:
   - Imágenes de búsqueda y de referencia que ha cargado.
   - Agregue formato como listas, tablas y llamadas específicas de documentos como `>[!NOTE]` .
   - Buscar y hacer referencia a vínculos internos y marcadores (vínculos a secciones específicas de una página).
   - Los errores de formato se resaltan (mantenga el mouse sobre el error para obtener más información).
- [Corrector ortográfico de código](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) : las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guardarla en el diccionario.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Uso de problemas para proporcionar comentarios sobre la guía entusiasta de la realidad de Windows Mixed Reality

Para proporcionar comentarios, o señalar un problema, en lugar de modificar directamente las páginas de documentación reales, [cree un problema](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) y los propietarios de contenido lo mejor para abordar el problema a tiempo.

Asegúrese de incluir el título del tema y la dirección URL si va a crear un problema con respecto a una página específica.

Gracias por apoyar este contenido.
