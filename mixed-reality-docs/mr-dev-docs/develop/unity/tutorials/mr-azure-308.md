---
title: 'HoloLens de primera generación y Azure (308): notificaciones entre dispositivos'
description: Complete este curso para aprender a implementar Azure Notification Hubs, Azure Functions y Azure Storage y tablas en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, notification, functions, tables, notification hubs, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205854"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (1.ª generación) y Azure 308: notificaciones entre dispositivos

<br>

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

![final product -start](images/AzureLabs-Lab8-00.png)

En este curso, aprenderá a agregar funcionalidades de Notification Hubs a una aplicación de realidad mixta mediante Azure Notification Hubs, Tablas de Azure y Azure Functions.

**Azure Notification Hubs** es un servicio de Microsoft, que permite a los desarrolladores enviar notificaciones push personalizadas y dirigidas a cualquier plataforma, todo ello con tecnología dentro de la nube. Esto puede permitir de forma eficaz a los desarrolladores comunicarse con los usuarios finales o incluso comunicarse entre varias aplicaciones, en función del escenario. Para obtener más información, visite la **página de Notification Hubs** [Azure](/azure/notification-hubs/notification-hubs-push-notification-overview).

**Azure Functions** es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "functions", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de en la aplicación local, lo que puede tener muchas ventajas. **Azure Functions** admite varios lenguajes de desarrollo, incluidos \# C, \# F, Node.js, Java y PHP. Para obtener más información, visite la **página Azure Functions** [.](/azure/azure-functions/functions-overview)

**Azure Tables** es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos estructurados no SQL en la nube, lo que facilita el acceso a ellos en cualquier lugar. El servicio ofrece un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para más información, visite la página **Tablas de Azure.** [](/azure/cosmos-db/table-storage-overview)

Una vez completado este curso, tendrá una aplicación de casco envolvente de realidad mixta y una aplicación de PC de escritorio, que podrá hacer lo siguiente:

1. La aplicación pc de escritorio permitirá al usuario mover un objeto en espacio 2D (X e Y) mediante el mouse.

2. El movimiento de objetos dentro de la aplicación de PC se enviará a la nube mediante JSON, que tendrá el formato de una cadena, que contiene un identificador de objeto, un tipo y una información de transformación (coordenadas X e Y). 

3. La aplicación de realidad mixta, que tiene una escena idéntica a la aplicación de escritorio, recibirá notificaciones sobre el movimiento de objetos desde el servicio Notification Hubs (que acaba de actualizar la aplicación de PC de escritorio). 

4. Al recibir una notificación, que contendrá el identificador de objeto, el tipo y la información de transformación, la aplicación de realidad mixta aplicará la información recibida a su propia escena.

En la aplicación, es usted el que tiene que ver con cómo va a integrar los resultados con el diseño. Este curso está diseñado para enseñar a integrar un servicio de Azure con su cuenta de Unity Project. Es su trabajo usar el conocimiento que obtiene de este curso para mejorar la aplicación de realidad mixta. Este curso es un tutorial independiente, que no implica directamente a ningún otro Mixed Reality Labs.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (308): Notificaciones entre dispositivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Aunque este curso se centra principalmente Windows Mixed Reality cascos envolventes (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens. A medida que siga el curso, verá notas sobre los cambios que tenga que emplear para admitir HoloLens. Al usar HoloLens, es posible que observe algún eco durante la captura de voz.

## <a name="prerequisites"></a>Requisitos previos

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (mayo de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente de lo que se muestra a continuación.

Se recomienda el siguiente hardware y software para este curso:

- Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de cascos envolventes (VR)
- [Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado](../../install-the-tools.md#installation-checklist)
- [El SDK de Windows 10 más reciente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Windows Mixed Reality envolvente envolvente (VR)](../../../discover/immersive-headset-hardware-details.md) o Microsoft HoloLens con el modo de desarrollador habilitado [](/hololens/hololens1-hardware)
- Acceso a Internet para la instalación de Azure y para acceder a Notification Hubs

## <a name="before-you-start"></a>Antes de comenzar

- Para evitar problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cercana a la raíz (las rutas de acceso de carpeta largas pueden causar problemas en tiempo de compilación).
- Debe ser el propietario de Desarrollador de Microsoft Portal y el Portal de registro de aplicaciones; de lo contrario, no tendrá permiso para acceder a la aplicación en el [capítulo 2.](#chapter-2---retrieve-your-new-apps-credentials)

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capítulo 1: Creación de una aplicación en Desarrollador de Microsoft Portal

Para usar **azure Notification Hubs** Service, deberá crear una aplicación en el portal de Desarrollador de Microsoft, ya que la aplicación tendrá que estar registrada, para que pueda enviar y recibir notificaciones.

1.  Inicie sesión en el [Desarrollador de Microsoft Portal.](https://developer.microsoft.com/dashboard)

    > Tendrá que iniciar sesión en su cuenta Microsoft.

2.  En el panel, haga clic **en Crear una nueva aplicación.**

    ![creación de una aplicación](images/AzureLabs-Lab8-01.png)

3.  Aparecerá un elemento emergente, en el que deberá reservar un nombre para la nueva aplicación. En el cuadro de texto, inserte un nombre adecuado; si el nombre elegido está disponible, aparecerá un tic a la derecha del cuadro de texto. Una vez que haya insertado un nombre disponible, haga clic en el botón **Reservar nombre** de producto situado en la parte inferior izquierda del elemento emergente.

    ![invertir un nombre](images/AzureLabs-Lab8-02.png)

4.  Con la aplicación ahora creada, está listo para pasar al siguiente capítulo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capítulo 2: Recuperación de las credenciales de las nuevas aplicaciones

Inicie sesión en el Portal de registro de aplicaciones, donde se mostrará la nueva aplicación, y recupere las credenciales que se usarán para configurar el servicio Notification Hubs **en** **Azure Portal.**

1.  Vaya al Portal [de registro de aplicaciones.](https://apps.dev.microsoft.com)

    ![portal de registro de aplicaciones](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > Tendrá que usar su cuenta Microsoft para iniciar sesión.  
    > Debe **ser** la cuenta Microsoft que usó en el [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)anterior, con el portal para desarrolladores Windows Store.

2.  Encontrará la aplicación en la **sección Mis aplicaciones.** Una vez que lo haya encontrado, haga clic en él y se le llevará a una nueva página que tenga el nombre de la aplicación más **Registro.**

    ![la aplicación recién registrada](images/AzureLabs-Lab8-04.png)

3.  Desplácese hacia abajo en la página de registro para buscar la **sección Secretos de aplicación** y el **SID del paquete** de la aplicación. Copie ambos para usarlos con la configuración de **Azure Notification Hubs Service** en el capítulo siguiente.

    ![secretos de aplicación](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capítulo 3: Configuración de Azure Portal: creación de Notification Hubs Service

Con las credenciales de las aplicaciones recuperadas, deberá ir a Azure Portal, donde creará una instancia de Azure Notification Hubs Service.

1.  Inicie sesión en [Azure Portal](https://portal.azure.com).

    > [!NOTE] 
    > Si aún no tiene una cuenta de Azure, deberá crear una. Si está siguiendo este tutorial en una situación de clase o laboratorio, pida ayuda a su instructor o a uno de los procedimientos para configurar la nueva cuenta.

2.  Una vez que haya iniciado sesión, haga clic en **Nuevo** en la esquina superior izquierda, busque **Centro** de notificaciones y haga clic **_en Entrar._**

    ![buscar el centro de notificaciones](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > Es posible que **la palabra*** New _ se haya reemplazado por _*Create a resource**, en los portales más recientes.

3.  La nueva página proporcionará una descripción del *Notification Hubs* servicio. En la parte inferior izquierda de este símbolo del sistema, seleccione el **botón** Crear para crear una asociación con este servicio.

    ![creación de una instancia de Notification Hubs](images/AzureLabs-Lab8-07.png)

4.  Una vez que haya hecho clic en ***Crear:***

    1.  Inserte el nombre deseado para esta instancia de servicio.

    2.  Proporcione un **espacio de** nombres que podrá asociar a esta aplicación.

    3.  Seleccione una **ubicación.**

    4.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal). 

    5.  Seleccione una suscripción **adecuada.**

    6.  También deberá confirmar que ha comprendido los Términos y condiciones aplicados a este servicio.

    7. Seleccione **Crear**.

        ![rellenar los detalles del servicio](images/AzureLabs-Lab8-08.png)

5.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

6.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![notificación](images/AzureLabs-Lab8-09.png)

7.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva instancia del servicio **Notification Hub.**

    ![ir al recurso](images/AzureLabs-Lab8-10.png)
    
8.  En la página de información general, a la mitad de la página, haga clic **Windows (WNS).** El panel de la derecha cambiará para mostrar dos campos de texto, que requieren el **SID** del paquete y la clave de **seguridad,** desde la aplicación que ha configurado anteriormente.

    ![servicio hubs recién creado](images/AzureLabs-Lab8-11.png)

9. Una vez que haya copiado los detalles en los campos correctos, haga clic en Guardar y recibirá una notificación cuando el Centro de notificaciones se haya actualizado correctamente.

    ![copiar detalles de seguridad](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capítulo 4: Configuración de Azure Portal: creación de Table Service

Después de crear la instancia de Notification Hubs Service, vuelva a Azure Portal, donde creará una instancia de Azure Tables Service mediante la creación de Storage Resource.

1.  Si aún no ha iniciado sesión, inicie sesión en [Azure Portal.](https://portal.azure.com)

2.  Una vez que haya iniciado sesión, haga clic en **Nuevo** en la esquina superior izquierda, busque Storage **cuenta y** haga clic en **Entrar.**

    > [!NOTE] 
    > Es posible que la palabra ***Nuevo** _ se haya reemplazado por _*Crear un recurso**, en los portales más recientes.

3.  Seleccione **Storage de la lista: blob, archivo, tabla** y cola.

    ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab8-13.png)

4.  La nueva página proporcionará una descripción del servicio **Storage cuenta.** En la parte inferior izquierda de este símbolo del sistema, seleccione **el botón** Crear para crear una instancia de este servicio.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab8-14.png)

5.  Una vez que haya hecho clic en **Crear,** aparecerá un panel:

    1. Inserte el nombre **deseado** para esta instancia de servicio (debe estar todo en minúsculas).

    2. En **Modelo de implementación,** haga clic **en Resource Manager.**

    3.  En **Tipo de cuenta,** mediante el menú desplegable, **seleccione Storage (uso general v1).**

    4. Seleccione una ubicación **adecuada.**
    
    5.  En el **menú desplegable** Replicación, seleccione Almacenamiento con redundancia geográfica con acceso de **lectura (RA-GRS).**

    6.  En **Rendimiento,** haga clic en **Estándar.**

    7.  En la **sección Se requiere transferencia** segura, seleccione **Deshabilitado.**

    8.  En el **menú desplegable** Suscripción, seleccione una suscripción adecuada.

    9.  Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. Deje **Redes virtuales** como **Deshabilitado** si esta es una opción para usted.

    11. Haga clic en **Crear**.

        ![rellenar los detalles de almacenamiento](images/AzureLabs-Lab8-15.png)

6.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

7.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal. Haga clic en las notificaciones para explorar la nueva instancia de servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab8-16.png)

8.  Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. Se le llevará a la nueva página de información general de Storage Service.

    ![ir al recurso](images/AzureLabs-Lab8-17.PNG)

9. En la página de información general, en el lado derecho, haga clic en **Tablas**.
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. El panel de la derecha cambiará para mostrar la información de **Table service,** donde debe agregar una nueva tabla. Para ello, haga clic en **+** **el botón** Tabla situado en la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab8-19.png)

11. Se mostrará una nueva página, en la que debe escribir un nombre **de tabla**. Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores. Inserte un nombre adecuado y haga clic en **Aceptar.**

    ![crear nueva tabla](images/AzureLabs-Lab8-20.png)    

12. Una vez creada la nueva tabla, podrá verla en la página **Table service** (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capítulo 5: Finalización de la tabla de Azure en Visual Studio

Ahora que se **ha configurado** la cuenta de Table service Storage, es el momento de agregarle datos, que se usarán para almacenar y recuperar información. La edición de las tablas se puede realizar a través **Visual Studio**.

1.  Abra **Visual Studio**.

2.  En el menú, haga clic **en**  >  **Ver Cloud Explorer**.

    ![abrir Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  La **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, ya que la carga puede tardar tiempo).

    > [!NOTE] 
    > Si la suscripción que usó para crear *las Storage no* está visible, asegúrese de que tiene: 
    > - Ha iniciado sesión en la misma cuenta que la que usó para Azure Portal.
    > - Ha seleccionado la suscripción en la página Administración de cuentas (es posible que tenga que aplicar un filtro de la configuración de la cuenta):  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab8-22-5.png)

4.  Se mostrarán los servicios en la nube de Azure. Busque **Storage y** haga clic en la flecha situada a la izquierda para expandir las cuentas.

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab8-23.png)

5.  Una vez expandido, la cuenta de **Storage recién** creada debe estar disponible. Haga clic en la flecha situada a la izquierda del almacenamiento y, después, una vez  que se expanda, busque **Tablas** y haga clic en la flecha situada junto a eso para mostrar la tabla que creó en el último capítulo. Haga doble clic en la **tabla**.

    ![tabla de objetos de escena abierta](images/AzureLabs-Lab8-24.png)

6.  La tabla se abrirá en el centro de la Visual Studio ventana. Haga clic en el icono de tabla **+** con el signo (más) en ella.

    ![agregar nueva tabla](images/AzureLabs-Lab8-25.png)

7.  Aparecerá una ventana en la que se le pedirá que *agregue la entidad*. Creará tres entidades en total, cada una con varias propiedades. Observará que *Ya se proporcionan PartitionKey* y *RowKey,* ya que la tabla los usa para buscar los datos. 

    ![clave de partición y fila](images/AzureLabs-Lab8-26.png)

8. Actualice el *valor de* **PartitionKey** y **RowKey** como se muestra a continuación (recuerde hacerlo para cada propiedad de fila que agregue, aunque incremente RowKey cada vez):

    ![agregar valores correctos](images/AzureLabs-Lab8-26-5.png)

9.  Haga **clic en Agregar propiedad** para agregar filas de datos adicionales. Haga que la primera tabla vacía coincida con la tabla siguiente.

10. Haga **clic en** Aceptar cuando haya terminado.

    ![Haga clic en Aceptar cuando haya terminado.](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Asegúrese de que ha cambiado el **tipo de** las **entradas X**, **Y** y **Z** a **Double**. 

11. Observará que la tabla ahora tiene una fila de datos. Vuelva a **+** hacer clic en el icono (más) para agregar otra entidad.

    ![primera fila](images/AzureLabs-Lab8-27-5.png)

12. Cree una propiedad adicional y, a continuación, establezca los valores de la nueva entidad para que coincidan con los que se muestran a continuación.

    ![agregar cubo](images/AzureLabs-Lab8-28.png)

13. Repita el último paso para agregar otra entidad. Establezca los valores de esta entidad en los que se muestran a continuación.

    ![agregar cilindro](images/AzureLabs-Lab8-29.png)

14. La tabla debería tener ahora un aspecto parecido al siguiente.

    ![tabla completa](images/AzureLabs-Lab8-30.png)

15. Ha completado este capítulo. Asegúrese de guardar.

## <a name="chapter-6---create-an-azure-function-app"></a>Capítulo 6: Creación de una aplicación de funciones de Azure

Cree una instancia de Azure Function App, a la que llamará la aplicación de escritorio para actualizar **Table** service y enviar una notificación a través del **Centro de notificaciones.**

En primer lugar, debe crear un archivo que permita a la función de Azure cargar las bibliotecas que necesita.

1.  Abra **Bloc de notas** (presione la tecla Windows y escriba el Bloc de notas).

    ![abrir el Bloc de notas](images/AzureLabs-Lab8-31.png)

2.  Con Bloc de notas, inserte la estructura JSON siguiente en ella. Una vez hecho esto, guárdelo en el escritorio como **project.jsen**. Es importante que la nomenclatura sea correcta: asegúrese de que **NO tiene una extensión .txt** archivo. Este archivo define las bibliotecas que usará la función, si ha usado NuGet le será familiar.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Inicie sesión en [Azure Portal](https://portal.azure.com).

4.  Una vez que haya iniciado sesión, haga clic en **Nuevo en** la esquina superior izquierda y busque **Function App** y presione **Entrar.**

    ![buscar aplicación de función](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > Es posible que **la palabra Nuevo** se haya reemplazado por Crear un **recurso** en los portales más recientes.

5.  La nueva página proporcionará una descripción de **Function App** Service. En la parte inferior izquierda de este símbolo del sistema, seleccione el **botón** Crear para crear una asociación con este servicio.

    ![instancia de function app](images/AzureLabs-Lab8-33.png)

6.  Una vez que haya hecho clic en **Crear,** rellene lo siguiente:

    1. En **Nombre de la** aplicación , inserte el nombre deseado para esta instancia de servicio.

    2. Seleccione una opción en **Suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted. Si es la primera vez que crea una función **App Service**, debe estar disponible un plan gratuito.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Para **el sistema operativo**, haga Windows, ya que esa es la plataforma prevista.

    6. Seleccione un **plan de hospedaje** (en este tutorial se usa un plan de **consumo).**

    7. Seleccione una **ubicación** **(elija la misma ubicación que el almacenamiento que ha creado en el paso anterior).**

    8. Para la **Storage,** debe seleccionar el servicio **Storage que creó en el paso anterior.**

    9. No necesitará *application* Ideas en esta aplicación, así que no dude en dejarla **desactivada.**

    10. Haga clic en **Crear**.

        ![creación de una nueva instancia](images/AzureLabs-Lab8-34.png)

7.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

8.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación](images/AzureLabs-Lab8-35.png)

9.  Haga clic en las notificaciones para explorar la nueva instancia del servicio.

10. Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. 

    ![ir al recurso](images/AzureLabs-Lab8-36.png)

11. Haga clic **+** en el icono (más) situado junto *a Funciones* para *crear nuevo*.

    ![agregar nueva función](images/AzureLabs-Lab8-37.png)

12. En el panel central, aparecerá **la ventana Creación** de funciones. Ignore la información de la mitad superior del panel y haga clic en Función personalizada **,** que se encuentra cerca de la parte inferior (en el área azul, como se muestra a continuación).

    ![función personalizada](images/AzureLabs-Lab8-38.png)

13. La nueva página dentro de la ventana mostrará varios tipos de función. Desplácese hacia abajo para ver los tipos púrpura y haga clic **en el elemento HTTP PUT.**

    ![http put link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Es posible que tenga que desplazarse más hacia abajo por la página (y es posible que esta imagen no tenga exactamente el mismo aspecto si se han realizado actualizaciones de Azure Portal), pero está buscando un elemento denominado *HTTP PUT*.

14. Aparecerá **la ventana HTTP PUT,** donde debe configurar la función (consulte a continuación para la imagen).

    1.  En **Idioma,** mediante el menú desplegable, seleccione C \# .

    2.  En **Nombre,** introduzca un nombre adecuado.

    3.  En el menú **desplegable Nivel de** autenticación, seleccione **Función**.

    4.  En la **sección Table name** (Nombre de tabla), debe usar el nombre exacto que usó para crear **table** service anteriormente (incluido el mismo caso de letra).

    5.  En la **Storage conexión de la cuenta** de almacenamiento, use el menú desplegable y seleccione la cuenta de almacenamiento desde allí. Si no está ahí,  haga clic en el hipervínculo Nuevo junto al título de la sección para mostrar otro panel, donde debe aparecer la cuenta de almacenamiento.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-40.png)

15. Haga **clic en** Crear y recibirá una notificación de que la configuración se ha actualizado correctamente.

    ![create (función)](images/AzureLabs-Lab8-41.png)

16. Después de **hacer clic en** Crear, se le redirigirá al editor de funciones.

    ![actualizar código de función](images/AzureLabs-Lab8-42.png)

17. Inserte el código siguiente en el editor de funciones (reemplazando el código de la función):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Con las bibliotecas incluidas, la función recibe el nombre y la ubicación del objeto que se movió en la escena de Unity (como un objeto de C#, denominado **UnityGameObject).** A continuación, este objeto se usa para actualizar los parámetros del objeto dentro de la tabla creada. A continuación, la función realiza una llamada al servicio notification hub creado, que notifica a todas las aplicaciones suscritas.

18. Con el código en su lugar, haga clic **en Guardar.**

19. A continuación, haga **\<** clic en el icono (flecha), en el lado derecho de la página.

    ![abrir el panel de carga](images/AzureLabs-Lab8-43.png)

20. Un panel se deslizará desde la derecha. En ese panel, haga **clic Upload** y aparecerá un Explorador de archivos.

21. Vaya a y haga  clic en elproject.jsen el archivo que creó en **Bloc de notas** anteriormente y, a continuación, haga clic en **el botón** Abrir. Este archivo define las bibliotecas que usará la función.

    ![cargar json](images/AzureLabs-Lab8-44.png)

22. Cuando se haya cargado el archivo, aparecerá en el panel de la derecha. Al hacer clic en él, se abrirá en el editor **de** funciones. Debe tener exactamente **el mismo aspecto** que la siguiente imagen (paso 23 siguiente).

23. A continuación, en el panel de la izquierda, debajo de **Funciones**, haga clic en **el vínculo Integrar.**

    ![función integrate](images/AzureLabs-Lab8-45.png)

24. En la página siguiente, en la esquina superior derecha, haga clic **en Editor avanzado** (como se muestra a continuación).

    ![Abrir el editor avanzado](images/AzureLabs-Lab8-46.png)

25. Se **function.jsen** el archivo en el panel central, que debe reemplazarse por el siguiente fragmento de código. Esto define la función que está creando y los parámetros pasados a la función.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. El editor debería tener ahora un aspecto parecido al de la imagen siguiente:

    ![volver al editor estándar](images/AzureLabs-Lab8-47.png)

27. Es posible que observe que los parámetros de entrada que acaba de insertar podrían no coincidir con los detalles de la tabla y el almacenamiento y, por tanto, tendrán que actualizarse con la información. **No haga esto aquí,** ya que se trata a continuación. Simplemente haga clic **en el vínculo Editor** estándar, en la esquina superior derecha de la página, para volver atrás.

28. De nuevo en el **editor estándar,** haga clic en **Tabla de Azure Storage (tabla)**, en **Entradas**. 
    
    ![Entradas de tabla](images/AzureLabs-Lab8-47-5.png)

29. Asegúrese de que la siguiente coincidencia **con la** información puede ser diferente (hay una imagen debajo de los pasos siguientes):

    1.  **Nombre de** tabla: el nombre de la tabla que creó en el Azure Storage, Servicio de tablas.

    2.  **Storage cuenta: haga** **clic** en nuevo , que aparece junto al menú desplegable y aparecerá un panel a la derecha de la ventana.

        ![nuevo almacenamiento](images/AzureLabs-Lab8-48.png)

        1.  Seleccione la **Storage que** creó anteriormente para hospedar **Function Apps.**

        2. Observará que se **ha creado Storage de** conexión de la cuenta.

        3. Asegúrese de presionar Guardar **una** vez que haya terminado.

    3.  La **página Entradas** debe coincidir ahora con la siguiente, que muestra **la** información.

        ![entradas completadas](images/AzureLabs-Lab8-49.png)

30. A continuación, **haga clic en Centro de notificaciones de Azure (notificación):** en **Salidas**. Asegúrese de que lo siguiente coincide **con su** información, ya que pueden ser diferentes (hay una imagen debajo de los pasos siguientes):

    1.  **Nombre del centro de** notificaciones: es el nombre de la instancia del servicio **Notification Hub** que creó anteriormente.

    2.  **Notification Hubs de espacio de nombres:** haga clic **en nuevo**, que aparece junto al menú desplegable.

        ![comprobar salidas](images/AzureLabs-Lab8-50.png)

    3. Aparecerá **el** menú emergente Conexión (consulte la imagen  siguiente), donde debe seleccionar el espacio de nombres del centro de **notificaciones,** que ha configurado anteriormente.

    4. Seleccione el nombre **del centro de notificaciones** en el menú desplegable central.

    5.  Establezca el **menú desplegable** Directiva en **DefaultFullSharedAccessSignature**.

    6. Haga clic en **el botón** Seleccionar para volver atrás.

        ![actualización de salida](images/AzureLabs-Lab8-51.png)

31.  La **página Salidas** ahora debe coincidir con lo siguiente, pero con **su** información en su lugar. Asegúrese de presionar **Guardar.**

> [!WARNING]
> *No edite el nombre del centro* de notificaciones directamente (todo esto debe realizarse mediante el Editor avanzado , siempre que haya seguido los pasos anteriores correctamente. 

![salidas completadas](images/AzureLabs-Lab8-50.png)

32. En este momento, debe probar la función para asegurarse de que funciona. Para ello: 

    1. Vaya a la página de función una vez más:

        ![salidas completadas](images/AzureLabs-Lab8-50-1.png)

    2. De nuevo en la página de funciones, haga clic en **la pestaña Prueba** en el lado derecho de la página para abrir la *hoja* Prueba:

        ![salidas completadas](images/AzureLabs-Lab8-50-2.png)

    3. En el **cuadro de texto Cuerpo** de la solicitud de la hoja, pegue el código siguiente:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Con el código de prueba en su lugar, haga clic en **el botón Ejecutar** situado en la parte inferior derecha y se ejecutará la prueba. Los registros de salida de la prueba aparecerán en el área de la consola, debajo del código de la función.

        ![salidas completadas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Si se produce un error en la prueba anterior, deberá comprobar que ha seguido exactamente los pasos anteriores, especialmente la configuración del **panel de integración**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capítulo 7: Configuración de unity de escritorio Project

> [!IMPORTANT]
> La aplicación de escritorio que está creando ahora **no funcionará** en el Editor de Unity. Debe ejecutarse fuera del Editor, siguiendo la creación de la aplicación, mediante Visual Studio (o la aplicación implementada). 

A continuación se muestra una configuración típica para el desarrollo con Unity y la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

Configure y pruebe los cascos envolventes de realidad mixta.

> [!NOTE] 
> No necesitará **controladores** de movimiento para este curso. Si necesita soporte técnico para configurar el casco envolvente, siga este vínculo sobre cómo [configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Abra **Unity y** haga clic en **Nuevo.**

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-52.png)

2.  Debe proporcionar un nombre de Project Unity, inserte **UnityDesktopNotifHub**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca la **ubicación en** un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![creación de proyecto](images/AzureLabs-Lab8-53.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar**  >  **preferencias** y, a continuación, en la nueva ventana, vaya **a Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![establecer herramientas externas de VS](images/AzureLabs-Lab8-54.png)

4.  A continuación, vaya a **File** Build Configuración seleccione Universal Windows Platform y, a continuación, haga clic en el botón Cambiar plataforma para  >   aplicar la selección.  

    ![cambiar plataformas](images/AzureLabs-Lab8-55.png)

5.  Mientras sigue en **la**  >  **compilación de Configuración**, asegúrese de que:

    1.  **El dispositivo de** destino se establece **en Cualquier dispositivo.**

        > Esta aplicación será para el escritorio, por lo que debe ser **Cualquier dispositivo.**

    2.  **Tipo de** compilación se establece en **D3D**

    3.  **El SDK** se establece en **Instalado más reciente**

    4.  **Visual Studio versión está** establecida en **La versión más reciente instalada**

    5.  **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**

    6.  Mientras esté aquí, merece la pena guardar la escena y agregarla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab8-56.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![carpeta de escenas nuevas](images/AzureLabs-Lab8-57.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo Nombre de **archivo:** texto, escriba **NH Desktop \_ \_ Scene** y, a continuación, **presione Guardar.**

            ![nueva NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  El resto de la configuración, **en Build Configuración**, se debe dejar como valor predeterminado por ahora.

6.  En la misma ventana, haga clic en el botón Player Configuración (Player **Configuración),** se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.**

7.  En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión del entorno de** ejecución de scripting debe ser experimental **(equivalente a .NET 4.6)**

        2. **El back-end de** scripting debe **ser .NET**

        3. **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![Versión 4.6 net](images/AzureLabs-Lab8-59.png)

    2.  En la **pestaña Configuración,** en **Funcionalidades**, compruebe:

        - **InternetClient**

            ![cliente de Internet de tic](images/AzureLabs-Lab8-60.png)

8.  De nuevo en **Build Configuración** Unity C Projects (Proyectos de *C \# de Unity)* ya no está en gris; marque la casilla situada junto a este.

9.  Cierre la ventana **Build Settings** (Configuración de compilación).

10. Guarde la escena y guarde Project **guardar** la escena  >  **o el** archivo  >  **Project**.

    > [!IMPORTANT]
    > Si desea omitir el componente De configuración de *Unity* para este proyecto (aplicación de escritorio) y continuar directamente en el código, no dude en descargar este [.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)importarlo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continuar desde el capítulo [9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)  Todavía tendrá que agregar los componentes de script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capítulo 8: Importación de archivos DLL en Unity

Va a usar Azure Storage para Unity (que a su vez aprovecha el SDK de .NET para Azure). Para obtener más información, siga [este vínculo sobre Azure Storage para Unity.](/sandbox/gamedev/unity/azure-storage-unity)

Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (del 4 al 7 de esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [**archivo .unitypackage**](https://aka.ms/azstorage-unitysdk) más reciente de GitHub. A continuación, haga lo siguiente:

1.  Agregue el **paquete .unitypackage** a Unity mediante la opción de **menú Importar paquete personalizado \> \> de** recursos.

2.  En el **cuadro Importar paquete de Unity** que aparece, puede seleccionar todo en **_Complemento_ \> *Storage)..  Desactive todo lo demás, ya que no es necesario para este curso.

    ![importar al paquete](images/AzureLabs-Lab8-61.png)

3.  Haga clic ***en el*** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta Storage** en **Complementos** en la Project y seleccione solo los siguientes *complementos:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![desactive Cualquier plataforma.](images/AzureLabs-Lab8-62.png)

5.  Con *estos complementos específicos seleccionados,* **desactive Cualquier** **plataforma** **y** **desactive WSAPlayer** y haga clic **en Aplicar.**

    ![aplicar archivos DLL de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Vamos a marcar estos complementos concretos para que solo se utilicen en el editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la **carpeta Storage** complemento, seleccione solo:

    -   Microsoft.Data.Services.Client

        ![set don't process for dlls](images/AzureLabs-Lab8-64.png)

7.  Active la casilla **No procesar en** Plataforma Configuración haga clic en **_Aplicar_**. 

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Vamos a marcar este complemento como "No procesar", porque el patcher de ensamblado de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se procese.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capítulo 9: Creación de la clase TableToScene en el proyecto de Unity de escritorio

Ahora debe crear los scripts que contienen el código para ejecutar esta aplicación.

El primer script que debe crear es **TableToScene,** que es responsable de:

-   Lectura de entidades dentro de la tabla de Azure.
-   Con los datos de tabla, determine qué objetos se generan y en qué posición.

El segundo script que debe crear es **CloudScene,** que es responsable de:

-   Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos por la escena.
-   Serializar los datos del objeto de esta escena de Unity y enviarlos a azure Function App.

Para crear esta clase:

1.  Haga clic con el botón derecho **en la carpeta de** recursos que se encuentra en Project panel, **Crear**  >  **carpeta**. Asigne a la carpeta el **nombre Scripts**.

    ![crear carpeta de scripts](images/AzureLabs-Lab8-66.png)

    ![crear la carpeta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  Haga doble clic en la carpeta que acaba de crear para abrirla.

3.  Haga clic con el botón derecho en **la carpeta Scripts** y haga clic en **Crear** script  >  **de C#.** Asigne al script **el nombre TableToScene.**

    ![Nuevo script de c# ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene rename](images/AzureLabs-Lab8-69.png)

4.  Haga doble clic en el script para abrirlo en Visual Studio 2017.

5.  Agregue los siguientes espacios de nombres:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  Dentro de la clase , inserte las siguientes variables:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Sustituya el **valor accountName** por el nombre del servicio de Azure Storage y el valor **accountKey** por el valor de clave que se encuentra en el servicio Azure Storage, en Azure Portal (consulte la imagen siguiente). 
    >
    > ![clave de la cuenta de captura](images/AzureLabs-Lab8-70.png)

7.  Ahora agregue los **métodos Start()** **y Awake()** para inicializar la clase .

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  Dentro de **la clase TableToScene,** agregue el método que recuperará los valores de la tabla de Azure y los usará para generar las primitivas adecuadas en la escena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  Fuera de **la clase TableToScene,** debe definir la clase utilizada por la aplicación para serializar y deserializar **las entidades de tabla**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Asegúrese de guardar **antes** de volver al Editor de Unity.

11. Haga clic **en la cámara** principal del panel **Jerarquía** para que sus propiedades aparezcan en el **inspector**.

12. Con la **carpeta Scripts** abierta, seleccione el archivo **TableToScene del** script y arrástrelo a la cámara **principal.** El resultado debe ser el siguiente:

    ![agregar script a la cámara principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capítulo 10: Creación de la clase CloudScene en el escritorio de Unity Project

El segundo script que debe crear es **CloudScene,** que es responsable de:

-   Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos por la escena.

-   Serializar los datos del objeto de esta escena de Unity y enviarlos a azure Function App.

Para crear el segundo script:

1.  Haga clic con el botón derecho en **la carpeta Scripts,** haga clic **en Crear**, **Script \# C**. Asigne al script **el nombre CloudScene.**
    
    ![nuevo script de c# ](images/AzureLabs-Lab8-72.png)
     ![ para cambiar el nombre de CloudScene](images/AzureLabs-Lab8-73.png)

2.  Agregue los siguientes espacios de nombres:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Sustituya el **valor azureFunctionEndpoint** por la dirección URL de azure Function App que se encuentra en azure Function App Service, en Azure Portal, como se muestra en la imagen siguiente:

    ![get function URL](images/AzureLabs-Lab8-74.png)

5.  Ahora agregue los **métodos Start()** **y Awake()** para inicializar la clase .

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  Dentro del **método Update(),** agregue el código siguiente que detectará la entrada del mouse y arrastrará, lo que a su vez moverá GameObjects en la escena. Si el usuario ha arrastrado y eliminado un objeto, pasará el nombre y las coordenadas del objeto al método **UpdateCloudScene(),** que llamará a Azure Function App Service, que actualizará la tabla de Azure y desencadenará la notificación.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Ahora agregue el **método UpdateCloudScene(),** como se indica a continuación:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Guardar el código y volver a Unity

9.  Arrastre el script **CloudScene** a la **cámara principal.** 

    1. Haga clic **en la cámara** principal del panel **Jerarquía** para que sus propiedades aparezcan en el **inspector**. 

    2. Con la **carpeta Scripts** abierta, seleccione el script **CloudScene** y arrástrelo a la **cámara principal.** El resultado debe ser el siguiente:

        > ![arrastrar el script en la nube a la cámara principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capítulo 11: Compilación de la aplicación de Project a UWP

Ahora se ha completado todo lo necesario para la sección de Unity de este proyecto.

1.  Vaya a **Build Configuración** **(File**  >  **Build Configuración**).

2.  En la ventana **Compilar Configuración,** haga clic en **Compilar**.

    ![proyecto de compilación](images/AzureLabs-Lab8-76.png)

3.  Aparecerá **Explorador de archivos** ventana emergente, en la que se le pedirá una ubicación para Compilar. Cree una nueva carpeta (haciendo clic en **Nueva carpeta en** la esquina superior izquierda) y asínquela **COMPILACIONES.**

    ![nueva carpeta para la compilación](images/AzureLabs-Lab8-77.png)

    1.  Abra la nueva **carpeta BUILDS** y cree otra carpeta (con Nueva carpeta **una** vez más) y así den su nombre a NH **Desktop \_ \_ App**.

        ![nombre de carpeta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con la **aplicación de escritorio NH \_ \_** seleccionada. Haga clic **en Seleccionar carpeta.** El proyecto va a tardar un minuto más o menos en compilarse.

4.  Después de la **compilación, Explorador de archivos** mostrará la ubicación del nuevo proyecto. Sin embargo, no es necesario abrirlo, ya que primero debe crear el otro proyecto de Unity, en los siguientes capítulos.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capítulo 12: Configuración de Mixed Reality Unity Project

A continuación se muestra una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.

1.  Abra **Unity y** haga clic en **Nuevo.**

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-79.png)

2.  Ahora deberá proporcionar un nombre de Project Unity, inserte **UnityMRNotifHub**. Asegúrese de que el tipo de proyecto está establecido en **3D.** Establezca la **ubicación en** un lugar adecuado para usted (recuerde que más cerca de los directorios raíz es mejor). A continuación, haga **clic en Crear proyecto.**

    ![name UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity abierto, merece la pena comprobar que el **editor de scripts** predeterminado está establecido en **Visual Studio**. Vaya a **Editar**  >  **preferencias** y, a continuación, en la nueva ventana, vaya **a Herramientas externas.** Cambie **Editor de scripts externos** a Visual Studio **2017**. Cierre la **ventana Preferencias.**

    ![establecer el editor externo en VS](images/AzureLabs-Lab8-81.png)

4.  A continuación, vaya a **File** Build Configuración y cambie la plataforma a Universal Windows Platform ; para ello, haga clic en  >   el botón Switch **Platform (Cambiar plataforma).** 

    ![cambiar plataformas a UWP](images/AzureLabs-Lab8-82.png)

5.  Vaya a **File**  >  **Build Configuración (Compilación** de archivos) y asegúrese de que:

    1.  **El dispositivo de** destino se establece **en Cualquier dispositivo**

        > Para la Microsoft HoloLens, establezca **Dispositivo de destino** en *HoloLens*.

    2.  **Tipo de** compilación se establece en **D3D**

    3.  **El SDK** se establece en **Instalado más reciente**

    4.  **Visual Studio versión está** establecida en **La versión más reciente instalada**

    5.  **Build and Run (Compilar y** ejecutar) está establecido en **Local Machine (Máquina local).**

    6.  Mientras esté aquí, merece la pena guardar la escena y agregarla a la compilación.

        1. Para ello, seleccione **Agregar escenas abiertas.** Aparecerá una ventana guardar.

            ![agregar escenas abiertas](images/AzureLabs-Lab8-83.png)

        2. Cree una nueva carpeta para esta y cualquier  escena futura y, a continuación, seleccione el botón Nueva carpeta para crear una carpeta, así como el nombre **Scenes**.

            ![carpeta de escenas nuevas](images/AzureLabs-Lab8-84.png)

        3. Abra la carpeta **Scenes** recién creada y, a continuación, en el campo Nombre de **archivo:** texto, escriba **NH MR \_ \_ Scene** y, a continuación, **presione Guardar.**

            ![nueva escena: NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  El resto de la configuración, **en Build Configuración**, se debe dejar como valor predeterminado por ahora.

6.  En la misma ventana, haga clic en el botón Player Configuración (Player **Configuración),** se abrirá el panel relacionado en el espacio donde se encuentra **el inspector.**    

    ![abrir la configuración del reproductor](images/AzureLabs-Lab8-86.png)

7.  En este panel, es necesario comprobar algunas configuraciones:

    1.  En la **pestaña Otros Configuración** datos:

        1.  **La versión del entorno de** ejecución de scripting debe ser **experimental** (equivalente a .NET 4.6)
        2.  **El back-end de** scripting debe **_ser .NET_**
        3.  **El nivel de compatibilidad de** API debe ser **.NET 4.6**

            ![compatibilidad con api](images/AzureLabs-Lab8-87.png)

    2.  Más abajo en el panel, en **XR Configuración** (que se encuentra debajo de **Publicar Configuración),** marque **Virtual Reality Supported (Compatible con Virtual Reality)** y asegúrese de que se agrega el **SDK** Windows Mixed Reality virtual.

        ![actualizar la configuración de xr](images/AzureLabs-Lab8-88.png)        

    3.  En la **pestaña Configuración,** en **Funcionalidades**, haga lo siguiente:

        - **InternetClient**           

            ![cliente de Internet de tic](images/AzureLabs-Lab8-89.png)

8.  De nuevo en **Build Configuración**, Unity C# Projects (Proyectos de C# de **Unity)** ya no está en gris: marque la casilla situada junto a esta.

9.  Una vez realizados estos cambios, cierre la ventana Configuración compilación.

10. Guarde la escena y guarde Project **guardar** la escena  >  **o el** archivo  >  **Project**.

    > [!IMPORTANT]
    > Si desea omitir el componente de configuración de *Unity* para este proyecto (aplicación de realidad mixta) y continuar directamente en el código, no dude en descargar este [.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)importarlo en el proyecto como un paquete personalizado y, [**a**](https://docs.unity3d.com/Manual/AssetPackages.html)continuación, continuar desde el capítulo [14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project). Todavía tendrá que agregar los componentes de script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capítulo 13: Importación de los archivos DLL en el Mixed Reality Unity Project

Usará la biblioteca Azure Storage para Unity (que usa el SDK de .NET para Azure). Siga este [vínculo sobre cómo usar Azure Storage con Unity.](/sandbox/gamedev/unity/azure-storage-unity)
Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación. Estos pasos (del 4 al 7 de esta sección) ya no serán necesarios una vez resuelto el error.

Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [archivo .unitypackage más reciente.](https://aka.ms/azstorage-unitysdk) A continuación, haga lo siguiente:

1.  Agregue el paquete .unitypackage que descargó anteriormente a Unity mediante la opción de menú **Importar** paquete personalizado  >    >  **de** recursos.

2.  En el **cuadro Importar paquete de Unity** que aparece, puede seleccionar todo en **Complemento**  >  **Storage**.

    ![importar paquete](images/AzureLabs-Lab8-90.png)

3.  Haga clic **en el** botón Importar para agregar los elementos al proyecto.

4.  Vaya a la **carpeta Storage** en **Complementos** en la Project y seleccione solo los siguientes *complementos:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![seleccionar complementos](images/AzureLabs-Lab8-91.png)

5.  Con *estos complementos específicos seleccionados,* **desactive Cualquier** **plataforma** **y** **desactive WSAPlayer** y haga clic **en Aplicar.**

    ![aplicar cambios en la plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Está marcando estos complementos concretos para que solo se utilicen en el Editor de Unity. Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.

6.  En la **carpeta Storage** complemento, seleccione solo:

    -   Microsoft.Data.Services.Client

        ![seleccionar cliente de servicios de datos](images/AzureLabs-Lab8-93.png)

7.  Active la casilla **No procesar en** Plataforma Configuración haga clic en **Aplicar**. 

    ![no procesar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Está marcando este complemento como "No procesar" porque el patcher de ensamblados de Unity tiene dificultades para procesar este complemento. El complemento seguirá funcionando aunque no se procese.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capítulo 14: Creación de la clase TableToScene en el proyecto de Unity de realidad mixta

La **clase TableToScene** es idéntica a la que se explica en [el capítulo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project) Cree la misma clase en mixed reality Unity Project siguiendo el mismo procedimiento que se explica en [el capítulo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)

Una vez que haya completado este capítulo, ambos proyectos **de Unity** tendrán esta clase configurada en la cámara principal.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capítulo 15: Creación de la clase NotificationReceiver en el Mixed Reality Unity Project

El segundo script que debe crear es **NotificationReceiver,** que es responsable de:

-   Registro de la aplicación en el Centro de notificaciones durante la inicialización.
-   Escuchar las notificaciones procedentes del Centro de notificaciones.
-   Deserializar los datos del objeto de las notificaciones recibidas.
-   Mueva los Objetos GameObject de la escena, en función de los datos deserialados.

Para crear el script **NotificationReceiver:**

1.  Haga clic con el botón derecho en **la carpeta Scripts,** haga clic **en Crear**, **Script \# C**. Asigne al script el nombre **NotificationReceiver.**

    ![crear un nuevo script de c# ](images/AzureLabs-Lab8-95.png)
     ![ con el nombre NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Haga doble clic en el script para abrirlo.

3.  Agregue los siguientes espacios de nombres:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Inserte las siguientes variables:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Sustituya el **valor hubName** por el nombre del servicio Notification Hub y el valor **hubListenEndpoint** por el valor de punto de conexión que se encuentra en la pestaña Directivas de acceso del servicio Azure Notification Hub en Azure Portal (consulte la imagen siguiente).

    ![Insertar punto de conexión de directiva de Notification Hubs](images/AzureLabs-Lab8-97.png)

6.  Ahora agregue los **métodos Start()** **y Awake()** para inicializar la clase .

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Agregue el **método WaitForNotification** para permitir que la aplicación reciba notificaciones de la biblioteca del centro de notificaciones sin conflictos con el subproceso principal:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  El método siguiente, **InitNotificationAsync()**, registrará la aplicación con el servicio de centro de notificaciones en la inicialización. El código se marca como comentario, ya que Unity no podrá compilar el proyecto. Quitará los comentarios al importar el paquete NuGet de mensajería de Azure en Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  El siguiente controlador, **Channel \_ PushNotificationReceived()**, se desencadenará cada vez que se reciba una notificación. Deserializará la notificación, que será la entidad de tabla de Azure que se ha movido en la aplicación de escritorio y, a continuación, moverá el GameObject correspondiente de la escena de MR a la misma posición. 
    
    > [!IMPORTANT]
    > El código se ha comentado porque hace referencia a la biblioteca de mensajería de Azure, que agregará después de compilar el proyecto de Unity mediante el Administrador de paquetes Nuget, dentro de Visual Studio. Por lo tanto, el proyecto de Unity no podrá compilarse, a menos que se comente. Tenga en cuenta que si compila el proyecto y, a continuación, desea volver a Unity, tendrá que volver a **comentar** ese código.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Recuerde guardar los cambios antes de volver al Editor de Unity.

11. Haga clic **en la cámara** principal del panel **Jerarquía** para que sus propiedades aparezcan en el **inspector**.

12. Con la **carpeta Scripts** abierta, seleccione el script **NotificationReceiver** y arrástrelo a la **cámara principal.** El resultado debe ser el siguiente:

    ![arrastrar el script del receptor de notificaciones a la cámara](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Si va a desarrollar esto para el Microsoft HoloLens, deberá actualizar el  componente de cámara de la cámara principal, de modo que:
    > - Marcas claras: Color sólido
    > - Fondo: Negro

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capítulo 16: Compilación del Mixed Reality Project a UWP

Este capítulo es idéntico al proceso de compilación del proyecto anterior. Ahora se ha completado todo lo necesario para la sección de Unity de este proyecto, por lo que es el momento de compilarlo desde Unity.

1.  Vaya a **Build Configuración** **(File**  >  **Build Configuración** ).

2.  En el **menú Compilar Configuración,** asegúrese de que proyectos de **C#** de Unity * está marcado (lo que le permitirá editar los scripts de este proyecto, después de la compilación).

3.  Una vez hecho esto, haga clic en **Compilar**.

    ![proyecto de compilación](images/AzureLabs-Lab8-99.png)

4.  Aparecerá **Explorador de archivos** ventana emergente, en la que se le pedirá una ubicación para Compilar. Cree una nueva carpeta (haciendo clic en **Nueva carpeta en** la esquina superior izquierda) y así denóquela **COMPILACIONES.**

    ![carpeta create builds](images/AzureLabs-Lab8-100.png)

    1.  Abra la nueva **carpeta BUILDS** y cree otra carpeta (con Nueva carpeta **una** vez más) y así denle el nombre NH **MR \_ \_ App**.

        ![crear NH_MR_Apps carpeta](images/AzureLabs-Lab8-101.png)

    2.  Con la **aplicación \_ NH MR \_ seleccionada.** Haga clic **en Seleccionar carpeta.** El proyecto va a tardar un minuto más o menos en compilarse.

5.  Después de la compilación, **Explorador de archivos** ventana se abrirá en la ubicación del nuevo proyecto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capítulo 17: Agregar NuGet paquetes a la solución UnityMRNotifHub

> [!WARNING] 
> Recuerde que, una vez que agregue los siguientes paquetes NuGet (y descomprima el código en el capítulo [siguiente),](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)el código, cuando se vuelva a abrir en el Project de Unity, presentará errores. Si desea volver atrás y continuar con la edición en el Editor de Unity, necesitará comentar ese código errosome y, a continuación, descomprima la comentario más adelante, una vez que vuelva a Visual Studio. 

Una vez completada la compilación de realidad mixta, vaya al proyecto de realidad mixta que ha creado y haga doble clic en el archivo de solución (.sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.
Ahora deberá agregar el paquete de NuGet **WindowsAzure.Messaging.managed;** se trata de una biblioteca que se usa para recibir notificaciones del Centro de notificaciones.

Para importar el NuGet paquete:

1.  En la **Explorador de soluciones**, haga clic con el botón derecho en la solución.

2.  Haga clic en **Administrar NuGet paquetes**.

    ![abrir el administrador de NuGet](images/AzureLabs-Lab8-102.png)

3.  Seleccione la pestaña ***Examinar** _ y busque _*WindowsAzure.Messaging.managed**.

    ![buscar paquete de mensajería de Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Seleccione el resultado (como se muestra a continuación) y, en la ventana situada a la derecha, active la casilla situada junto **a Project**. Esto colocará un tic en la casilla situada junto a **Project**, junto con la casilla situada junto al proyecto **Assembly-CSharp** y **UnityMRNotifHub.**

    ![Tic all projects (Marcar todos los proyectos)](images/AzureLabs-Lab8-104.png)

5.  Es posible que la versión proporcionada **inicialmente no** sea compatible con este proyecto. Por lo tanto, haga clic en el menú desplegable situado junto a **Versión** y en **Versión 0.1.7.9** y, a continuación, haga clic **en Instalar.**

6.  Ya ha terminado de instalar el NuGet paquete. Busque el código comentado que escribió en la **clase NotificationReceiver** y quite los comentarios.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capítulo 18: Edición de la aplicación UnityMRNotifHub, clase NotificationReceiver

Después de haber agregado **NuGet paquetes**,  deberá descomprimar parte del código dentro de la **clase NotificationReceiver.**

Esto incluye:

1. El espacio de nombres en la parte superior:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Todo el código del **método InitNotificationsAsync():**

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> El código anterior tiene un comentario en él: asegúrese de que no ha *descomprimido* accidentalmente ese comentario (ya que el código no se compilará si lo tiene).

3. Y, por último, el **Channel_PushNotificationReceived** evento:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Con estos sin comentario, asegúrese de guardar y, a continuación, continúe con el siguiente capítulo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capítulo 19: Asociación del proyecto de realidad mixta a la aplicación store

Ahora debe asociar el proyecto **de realidad mixta** a la aplicación de la Tienda en la que creó al principio del laboratorio.

1.  Abra la solución.

2.  Haga clic con el botón derecho en la aplicación para UWP Project en el panel de Explorador de soluciones, vaya a Tienda y Asociar aplicación con **la Tienda...**. 

    ![asociación de tiendas abiertas](images/AzureLabs-Lab8-105.png)

3.  Aparecerá una nueva ventana denominada **Associate Your App with the Windows Store**. Haga clic en **Siguiente**.

    ![ir a la siguiente pantalla](images/AzureLabs-Lab8-106.png)

4.  Cargará todas las aplicaciones asociadas a la cuenta en la que ha iniciado sesión. Si no ha iniciado sesión en su cuenta, puede **iniciar sesión** en esta página.

5.  Busque el **nombre de la aplicación de** la Tienda que creó al principio de este tutorial y selecciónelo. A continuación, haga clic en **Siguiente**.

    ![buscar y seleccionar el nombre de la tienda](images/AzureLabs-Lab8-107.png)

6.  Haga clic en **Asociar**.

    ![asociar la aplicación](images/AzureLabs-Lab8-108.png)

7.  La aplicación ahora está **asociada a** la aplicación de la Tienda. Esto es necesario para habilitar las notificaciones.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capítulo 20: Implementación de aplicaciones UnityMRNotifHub y UnityDesktopNotifHub

Este capítulo puede ser más fácil con dos personas, ya que el resultado incluirá ambas aplicaciones en ejecución, una que se ejecuta en el escritorio del equipo y la otra dentro del casco envolvente.

La aplicación de casco envolvente está esperando recibir cambios en la escena (cambios de posición de los GameObjects locales) y la aplicación de escritorio realizará cambios en su escena local (cambios de posición), que se compartirán con la aplicación de mr. Tiene sentido implementar primero la aplicación de MR, seguida de la aplicación de escritorio, para que el receptor pueda empezar a escuchar.

Para implementar la **aplicación UnityMRNotifHub** en la máquina local:

1.  Abra el archivo de solución de **la aplicación UnityMRNotifHub** **Visual Studio 2017**.

2.  En la **Plataforma de soluciones,** **seleccione x86, Máquina local.**

3.  En Configuración **de la solución,** **seleccione Depurar**.

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-109.png)

4.  Vaya al **menú Compilar y** haga clic en Implementar **solución** para realizar la instalación local de la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

Para implementar la **aplicación UnityDesktopNotifHub** en la máquina local:

1.  Abra el archivo de solución de **la aplicación UnityDesktopNotifHub** **Visual Studio 2017**.

2.  En la **Plataforma de soluciones,** **seleccione x86, Máquina local.**

3.  En Configuración **de la solución,** **seleccione Depurar**.

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-110.png)

4.  Vaya al **menú Compilar y** haga clic en Implementar **solución** para realizar la instalación local de la aplicación en el equipo.

5.  La aplicación debería aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.

6.  Inicie la aplicación de realidad mixta, seguida de la aplicación de escritorio.

Con ambas aplicaciones en ejecución, mueva un objeto en la escena de escritorio (mediante el botón izquierdo del mouse). Estos cambios posicionales se realizarán localmente, se serializarán y se enviarán a Function App Service. Después, Function App Service actualizará la tabla junto con el Centro de notificaciones. Una vez recibida una actualización, el Centro de notificaciones enviará los datos actualizados directamente a todas las aplicaciones registradas (en este caso, la aplicación de casco envolvente), que deserializará los datos entrantes y aplicará los nuevos datos posicionales a los objetos locales, y los trasladará a la escena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>La aplicación de Azure Notification Hubs finalizada
 
Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Notification Hubs Service y permite la comunicación entre aplicaciones.
 
![final del producto](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

¿Puede averiguar cómo cambiar el color de los GameObjects y enviar esa notificación a otras aplicaciones que ven la escena?

### <a name="exercise-2"></a>Ejercicio 2

¿Puede agregar el movimiento de gameObjects a la aplicación de MR y ver la escena actualizada en la aplicación de escritorio?