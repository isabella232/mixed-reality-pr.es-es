---
title: Instrucciones de contribución
description: Obtenga información sobre los pasos básicos y las directrices para contribuir a la Windows Mixed Reality Defiendo. Agradecemos sus comentarios, ediciones, adiciones y ayuda.
author: mattwojo
ms.author: mattwoj
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, Virtual Reality, VR, MR, Feedback, Centro de opiniones, bugs
appliesto:
- Windows 10
ms.openlocfilehash: fd47e806a1ac14d85f503d7d4f799b232cbd3e102c3d4494d5704082bf0e08ea
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188166"
---
# <a name="contributing-to-the-mixed-reality-enthusiast-guide"></a>Contribución a la guía Mixed Reality de Mixed Reality

Gracias por su interés en la Guía para seguidores. Agradecemos sus comentarios, ediciones, adiciones y ayuda para mejorar nuestros documentos. En esta página se tratan los pasos básicos y las directrices para contribuir.

> [!IMPORTANT]
> Todos los repositorios que publican en docs.microsoft.com han adoptado el [Código de conducta de código abierto de Microsoft](https://opensource.microsoft.com/codeofconduct/). Para más información, consulte las [preguntas más frecuentes del código de conducta](https://opensource.microsoft.com/codeofconduct/faq/) o póngase en contacto con [opencode@microsoft.com](mailto:opencode@microsoft.com) si tiene cualquier pregunta o comentario.<br>
>
> Las correcciones menores o aclaraciones de la documentación y los ejemplos de código de los repositorios públicos se rigen por los [Términos de uso del sitio docs.microsoft.com](/legal/termsofuse). Los cambios importantes o nuevos generarán un comentario en la solicitud de incorporación de cambios para solicitarle que acepte el contrato de licencia de colaboración (CLA, por sus siglas en inglés) si no es un empleado de Microsoft. Necesitamos que rellene el formulario en línea para aceptar su solicitud de incorporación de cambios.

## <a name="before-you-start"></a>Antes de comenzar

Si aún no tiene una, deberá crear una cuenta [de GitHub .](https://github.com/join)

>[!NOTE]
>Si es empleado de Microsoft, vincule su cuenta de GitHub a su alias de Microsoft en el [portal de código abierto de Microsoft](https://repos.opensource.microsoft.com/). Únase a **las organizaciones "Microsoft"** **y "MicrosoftDocs".**

Al configurar la cuenta GitHub, también se recomiendan estas precauciones de seguridad:
- Cree una [contraseña segura para la cuenta de GitHub.](https://github.com/settings/admin)
- Habilite [la autenticación en dos fases.](https://github.com/settings/two_factor_authentication/configure)
- Guarde los [códigos de recuperación](https://github.com/settings/auth/recovery-codes) en un lugar seguro.
- Actualice la [configuración del perfil público.](https://github.com/settings/profile)
   - Establezca su nombre y considere la posibilidad de establecer el correo *electrónico público* en No mostrar mi dirección de *correo electrónico.*
   - Se recomienda cargar una imagen de perfil porque se muestra una miniatura en las páginas de documentos a las que contribuye.
- Si tiene previsto usar la línea de comandos, considere la posibilidad de configurar [Git Administrador de credenciales para Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest). De este modo, no tendrá que escribir la contraseña cada vez que realice una contribución.

El sistema de publicación está asociado a GitHub, por lo que estos pasos son importantes. Aparecerá como autor o colaborador de cada artículo mediante el alias GitHub usuario.

## <a name="how-to-make-a-change"></a>Cómo realizar un cambio

| Para sugerir un cambio en los documentos, siga estos pasos: | Capturas de pantalla |
| :------------------- | :--------: |
| 1. Si está viendo una página Docs.microsoft.com,  haga clic en el botón Editar situado en la esquina superior derecha de la página.  Se le redirigirá al archivo de origen Markdown correspondiente en el [repositorio de GitHub](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide). | ![Botón Editar](images/edit_button.jpg) |
| 2. Si aún no tiene una cuenta de  GitHub, haga clic en Registrarse en la esquina superior derecha y cree una nueva cuenta. | ![Botón De registro](images/signup-for-github-button.png)|
| 3. En la página de GitHub correspondiente que se abre, haga clic en Editar (el icono de lápiz). | ![Botón Lápiz](images/pencil_button.jpg)|
| 4. En el panel Editar archivo, [actualice los metadatos](#updating-metadata) de los archivos y use el lenguaje Markdown para cambiar el contenido. ([Cómo escribir markdown.](https://help.github.com/articles/basic-writing-and-formatting-syntax/))| ![Editar archivo](images/edit-in-github.png)|
| 5. Haga clic en Vista previa de los cambios para comprobar que el formato es el esperado. | ![Vista previa de los cambios](images/edit-in-github.png)|
| 6. Cuando haya terminado, desplácese hasta la parte inferior de la página y haga clic en "Propose file change" (Proponer cambio de archivo), aparecerá una página "Comparar cambios", lo que le permitirá comprobar los cambios. A continuación, haga clic en el botón "Crear solicitud de extracción" para enviar los cambios. Después de este paso, ya habrá terminado. | ![Proponer un cambio](images/propose.jpg)|

Después de enviar los cambios (a través de una solicitud de extracción), un miembro del equipo de documentación los revisará. Si se acepta la solicitud, las actualizaciones se publican en [https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide](/windows/mixed-reality/enthusiast-guide) .

*Solo para revisión interna, puede ver los cambios en [https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide](https://review.docs.microsoft.com/en-us/windows/mixed-reality/enthusiast-guide/?branch=master) .

### <a name="updating-metadata"></a>Actualizar metadatos

Actualice los metadatos en la parte superior de cada artículo:
   * **title:** título de la página que aparece en la pestaña del explorador cuando se está visualizando el artículo. Los títulos de página se usan para SEO e indexación, por lo que no cambie el título a menos que sea necesario (aunque esto es menos crítico antes de que la documentación se haga pública).
   * **description:** escriba una breve descripción del contenido del artículo, lo que aumenta el SEO y la detección.
   * **author:** si es el propietario principal de la página, agregue el alias GitHub aquí.
   * **ms.author:** si es el propietario principal de la página, agregue el alias de Microsoft aquí (no necesita , solo @microsoft.com el alias).
   * **ms.date:** actualice la fecha si va a agregar contenido principal a la página, pero no para correcciones como aclaración, formato, gramática o ortografía.
   * **keywords:** las palabras clave ayudan en SEO (optimización del motor de búsqueda). Agregue palabras clave, separadas por una coma y un espacio, que sean específicas del artículo, pero sin signos de puntuación después de la última palabra clave de la lista. No es necesario agregar palabras clave globales que se apliquen a todos los artículos, ya que se administran en otro lugar. 

### <a name="renaming-or-deleting-an-existing-article"></a>Cambiar el nombre o eliminar un artículo existente

Si el cambio cambiará el nombre o eliminará un artículo existente, asegúrese de agregar una redirección. De este modo, cualquier persona con un vínculo al artículo existente seguirá en el lugar correcto. Las redirecciones se administran mediante .openpublishing.redirection.jsen el archivo en la raíz del repositorio.

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

- es la ruta de acceso relativa del repositorio `source_path` al artículo anterior que va a quitar. Asegúrese de que la ruta de acceso `mixed-reality-docs/enthusiast-guide` comienza por y termina con `.md` .
- es `redirect_url` la dirección URL pública relativa del artículo anterior al nuevo. Asegúrese de que esta dirección URL **no contiene** o , ya que hace referencia a la dirección URL pública y no a la ruta de acceso `mixed-reality-docs/enthusiast-guide` del `.md` repositorio. Se permite la vinculación a una sección del nuevo artículo `#section` mediante . También puede usar una ruta de acceso absoluta a otro sitio aquí, si es necesario.
- `redirect_document_id` indica si desea conservar el identificador del documento del archivo anterior. El valor predeterminado es `false`. Use `true` si desea conservar el valor del atributo del artículo `ms.documentid` redirigido. Si conserva el identificador del documento, los datos, como las vistas de página y las clasificaciones, se transferirán al artículo de destino. Use esta solución si el redireccionamiento es principalmente un cambio de nombre y no un puntero a un artículo diferente que solo cubre parte del mismo contenido.

Si agrega un redireccionamiento, asegúrese de eliminar también el archivo antiguo.

### <a name="creating-a-new-article"></a>Creación de un nuevo artículo

Use el siguiente flujo de trabajo *para crear nuevos artículos en* el repositorio de documentación a través GitHub en un explorador web:

1. Cree una bifurcación fuera de la rama "master" de MicrosoftDocs/mixed-reality/tree/docs/enthusiast-guide (con el botón **Bifurcar** de la parte superior derecha).

   ![Bifurcar la rama maestra.](images/forkbranch.png)
2. En la carpeta "mixed-reality/enthusiast-guide", seleccione **Crear nuevo archivo** en la parte superior derecha.
3. Cree un nombre de página para el artículo (use guiones en lugar de espacios y no use signos de puntuación ni apóstrofos) y anexe ".md".

   ![Asigne un nombre a la nueva página.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   >Asegúrese de crear el nuevo artículo desde la carpeta "mixed-reality-docs/enthusiast". Para confirmarlo, compruebe "/mixed-reality-docs/enthusiast-guide" en la nueva línea de nombre de archivo.

4. En la parte superior de la nueva página, agregue el siguiente bloque de metadatos:

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

5. Rellene los campos de metadatos pertinentes según las instrucciones de la [sección anterior.](#updating-metadata)
6. Escribir contenido del artículo con [los conceptos básicos de Markdown.](#markdown-basics)
7. Agregue una `## See also` sección en la parte inferior del artículo con vínculos a otros artículos pertinentes.
8. Cuando termine, seleccione **Commit new file (Confirmar nuevo archivo).**
9. Seleccione **Nueva** solicitud de extracción y combine la rama "maestra" de la bifurcación en MicrosoftDocs/mixed-reality/enthusiast-guide "master" (asegúrese de que la flecha apunta de la manera correcta).

   ![Creación de una solicitud de extracción desde la bifurcación en MicrosoftDocs/mixed-reality/enthusiast-guide](images/pr_to_master.PNG)

## <a name="working-with-branches"></a>Trabajo con ramas

El repositorio GitHub [de](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide) la Guía para el Mixed Reality de Mixed Reality usa dos ramas principales [principales:](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/master)Master , este contenido se puede revisar en el sitio de ensayo [y](https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide) [Live](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/tree/live), para ver el contenido que aparece en el sitio en [directo.](/windows/mixed-reality/enthusiast-guide)

Al realizar contribuciones, envíe la solicitud de extracción (PR) a la **rama** maestra. Esta rama se puede ver en el sitio de ensayo y solo debe contener las contribuciones que están listas para ser publicadas. También puede crear y enviar una rama con su propio nombre de rama único que se puede seleccionar y ver en el sitio de ensayo. (La **rama Live** solo está permitida para que la usen los administradores de contenido).

## <a name="markdown-basics"></a>Aspectos básicos de Markdown

Los siguientes recursos le ayudarán a aprender a editar la documentación mediante el lenguaje Markdown:

- [Markdown basics](https://help.github.com/articles/basic-writing-and-formatting-syntax/) (Conceptos básicos de Markdown)
- [Póster de referencia de Markdown-at-a-glance](images/MarkdownPoster.pdf)
- [Recursos adicionales para escribir Markdown para docs.microsoft.com](/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a>Agregar tablas

Debido a la forma docs.microsoft.com tablas de estilos, no tendrán bordes ni estilos personalizados, incluso si se prueba CSS en línea. Parecerá que funciona durante un breve período de tiempo, pero finalmente la plataforma quitará el estilo de la tabla. Por lo tanto, planee con antelación y mantenga las tablas sencillas. [Este es un sitio que facilita las tablas de Markdown.](https://www.tablesgenerator.com/markdown_tables)

La [extensión Docs Markdown para Visual Studio Code](/teamblog/docs-extension) también facilita la generación de tablas si usa Visual Studio Code (consulte a continuación) para editar la documentación. [](#using-visual-studio-code)

### <a name="adding-images"></a>Incorporación de imágenes

Deberá cargar las imágenes en la carpeta "mixed-reality-docs/images" del repositorio y, a continuación, hacer referencia a ellas correctamente en el artículo. Las imágenes se mostrarán automáticamente a tamaño completo, lo que significa que las imágenes grandes rellenarán todo el ancho del artículo. Se recomienda realizar un tamaño previo de las imágenes antes de cargarlas. El ancho recomendado es de entre 600 y 700 píxeles, aunque debe cambiar de tamaño si es una captura de pantalla densa o una fracción de una captura de pantalla, respectivamente.

>[!IMPORTANT]
>Solo puede cargar imágenes en el repositorio bifurcado antes de la combinación. Por lo tanto, si planea agregar imágenes a un artículo, deberá usar Visual Studio Code para agregar primero las imágenes [a](#using-visual-studio-code) la carpeta "images" de la bifurcación o asegúrese de que ha hecho lo siguiente en un explorador web:
>
>1. Se ha bifurcado el repositorio MicrosoftDocs/mixed-reality.
>2. Editó el artículo en la bifurcación.
>3. Ha cargado las imágenes a las que hace referencia en el artículo en la carpeta "mixed-reality-docs/images" de la bifurcación.
>4. Ha creado **una solicitud de** extracción para combinar la bifurcación en la rama "maestra" de MicrosoftDocs/mixed-reality.
>
>Para obtener información sobre cómo configurar su propio repositorio bifurcado, siga las instrucciones para [crear un nuevo artículo](#creating-a-new-article).

## <a name="previewing-your-work"></a>Vista previa del trabajo

Al editar en GitHub a través de un  explorador web, puede seleccionar la pestaña Vista previa cerca de la parte superior de la página para obtener una vista previa del trabajo antes de confirmar. 

>[!NOTE]
>La vista previa de los cambios review.docs.microsoft.com solo está disponible para los empleados de Microsoft

Empleados de Microsoft: una vez que sus contribuciones se hayan combinado en la rama "maestra", puede revisar el contenido antes de que se haga público en https://review.docs.microsoft.com/windows/mixed-reality/enthusiast-guide?branch=master . Busque el artículo con la tabla de contenido de la columna izquierda.

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a>Edición en el explorador frente a edición con un cliente de escritorio

La edición en el explorador es la manera más fácil de realizar cambios rápidos; sin embargo, hay algunas desventajas:

- No se le hace una revisión ortótrea.
- No se obtiene ninguna vinculación inteligente a otros artículos (tiene que escribir manualmente el nombre de archivo del artículo).
- Puede ser complicado cargar y hacer referencia a imágenes.

Si prefiere no tratar estos problemas, use un cliente de escritorio como [Visual Studio Code](https://code.visualstudio.com/) con un par de extensiones [útiles](#useful-extensions) al contribuir.

## <a name="using-visual-studio-code"></a>Uso de Visual Studio Code

Por los motivos [mencionados anteriormente,](#editing-in-the-browser-vs-editing-with-a-desktop-client)puede que prefiera usar un cliente de escritorio para editar la documentación en lugar de un explorador web. Se recomienda usar [Visual Studio Code](https://code.visualstudio.com/).

### <a name="setup"></a>Configurar

Siga estos pasos para configurar Visual Studio Code para trabajar con este repositorio:

1. En un explorador web:
    1. Instale [Git para el equipo.](https://git-scm.com/downloads)
    2. Instale [Visual Studio Code](https://code.visualstudio.com/).
    3. Si aún no lo ha hecho, puede bifurcar [MicrosoftDocs/mixed-reality.](#creating-a-new-article)
    4. En la bifurcación, seleccione **Clone or download (Clonar o descargar)** y copie la dirección URL.
2. Cree un clon local de la bifurcación en Visual Studio Code:
    1. En el **menú Ver,** seleccione **Paleta de comandos.**
    2. Escriba "Git: Clone".
    3. Pegue la dirección URL que copió.
    4. Elija dónde guardar el clon en el equipo.
    5. Seleccione **Abrir repositorio** en el menú emergente.

### <a name="editing-documentation"></a>Edición de documentación

Use el siguiente flujo de trabajo para realizar cambios en la documentación con Visual Studio Code:

>[!NOTE]
>Todas las instrucciones para [editar](#how-to-make-a-change) [y](#creating-a-new-article) crear [artículos,](#markdown-basics)y los conceptos básicos de la edición de Markdown , de arriba, también se aplican al Visual Studio Code.

1. Asegúrese de que la bifurcación clonada está actualizada con el repositorio oficial.
   1. En un explorador web, cree una solicitud de extracción para sincronizar los cambios recientes de otros colaboradores de MicrosoftDocs/mixed-reality 'master' con la bifurcación (asegúrese de que la flecha apunta a la derecha).
      
      ![Sincronización de cambios de MicrosoftDocs/mixed-reality a la bifurcación](images/sync_repos.PNG)
   2. En Visual Studio Code, seleccione el botón sincronizar para sincronizar la bifurcación recién actualizada con el clon local.
      
      ![Haga clic en la imagen del botón sincronizar.](images/sync_clone.png)
2. Cree o edite artículos en el repositorio clonado mediante Visual Studio Code.
   1. Edite uno o varios artículos (agregue imágenes a la carpeta "images" si es necesario).
   2. **Guarde los** cambios en el **Explorador** de .
      
      ![Elija "Guardar todo" en el Explorador](images/explorer_save.png)
   3. **Confirme todos los** cambios en **control de código fuente** (escriba el mensaje de confirmación cuando se le solicite).
      
      ![Elija "Confirmar todo" en control de código fuente](images/source_control_commit.png)
   4. Seleccione el **botón** sincronizar para volver a sincronizar los cambios en el origen (la bifurcación en GitHub).
      
      ![Haga clic en el botón Sync (Sincronizar).](images/sync_back.png)
3. En un explorador web, cree una solicitud de extracción para sincronizar nuevos cambios en la bifurcación con MicrosoftDocs/mixed-reality 'master' (asegúrese de que la flecha apunta de la manera correcta).

   ![Creación de una solicitud de extracción desde la bifurcación en MicrosoftDocs/mixed-reality](images/pr_to_master.PNG)

### <a name="useful-extensions"></a>Extensiones útiles

Las siguientes extensiones Visual Studio Code son útiles al editar la documentación:

- [Extensión Markdown de Docs para Visual Studio Code:](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) use **Alt+M** para abrir un menú de opciones de creación de documentos como:
   - Busque y haga referencia a las imágenes que ha cargado.
   - Agregue formatos como listas, tablas y llamadas específicas de documentos, como `>[!NOTE]` .
   - Buscar y hacer referencia a vínculos internos y marcadores (vínculos a secciones específicas dentro de una página).
   - Los errores de formato están resaltados (mantenga el mouse sobre el error para obtener más información).
- [Corrector ortográfico de código:](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) las palabras mal escritas se subrayan; Haga clic con el botón derecho en una palabra mal escrita para cambiarla o guárdela en el diccionario.

## <a name="using-issues-to-provide-feedback-on-windows-mixed-reality-enthusiast-guide"></a>Uso de problemas para proporcionar comentarios sobre la Windows Mixed Reality de seguidores

Para proporcionar comentarios o señalar un problema, en lugar de modificar directamente las páginas de documentación [reales,](https://github.com/MicrosoftDocs/mixedreality-enthusiast-guide/issues) cree un problema y los propietarios de contenido harán todo lo posible para solucionar el problema de forma oportuna.

Asegúrese de incluir el título del tema y la dirección URL si está creando un problema con respecto a una página específica.

Gracias por admitir este contenido.