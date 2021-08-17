---
title: 'HoloLens de primera generación y Azure (313): servicio IoT Hub'
description: Obtenga información sobre cómo implementar Azure IoT Hub Service en una máquina virtual que ejecuta Ubuntu 16.4 y visualizar los datos del mensaje mediante Microsoft HoloLens casco de realidad virtual.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, mixed reality, academy, edge, iot edge, tutorial, api, notification, functions, tables, hololens, immersive, vr, iot, virtual machine, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905759"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (1.ª generación) y Azure 313: IoT Hub Service

>[!NOTE]
>Los tutoriales de Mixed Reality Academy se han diseñado teniendo en cuenta HoloLens (1.ª generación) y los cascos envolventes de realidad mixta.  Por lo tanto, creemos que es importante conservar estos tutoriales para los desarrolladores que sigan buscando instrucciones sobre el desarrollo para esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para que sigan funcionando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro y que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

![resultado del curso](images/AzureLabs-Lab313-00.png)

En este curso, aprenderá a implementar un servicio **Azure IoT Hub en** una máquina virtual que ejecute el sistema operativo Ubuntu 16.4. A **continuación,** se usará una aplicación de función de Azure para recibir mensajes de la máquina virtual Ubuntu y almacenar el resultado en una instancia de **Azure Table Service.** A continuación, podrá ver  estos datos mediante Power BI casco Microsoft HoloLens envolvente (VR).

El contenido de  este curso es aplicable IoT Edge los dispositivos de IoT Edge, aunque para este curso, el foco estará en un entorno de máquina virtual, por lo que no es necesario acceder a un dispositivo perimetral físico.

Al completar este curso, aprenderá a:

- Implemente **un IoT Edge en** una máquina virtual (sistema operativo Ubuntu 16), que representará el dispositivo IoT.
- Agregue un **modelo Custom Vision Tensorflow de Azure** al módulo Edge, con código que analizará las imágenes almacenadas en el contenedor.
- Configure el módulo para devolver el mensaje de resultado del análisis a su **IoT Hub Service**.
- Use una **instancia de Azure Function App** para almacenar el mensaje en una tabla de **Azure.**
- Configure **Power BI** para recopilar el mensaje almacenado y crear un informe.
- Visualice los datos del mensaje de IoT **en Power BI**.

Los servicios que usará incluyen:

- **Azure IoT Hub es** un servicio Microsoft Azure que permite a los desarrolladores conectar, supervisar y administrar recursos de IoT. Para obtener más información, visite la [ **página Azure IoT Hub Service**](https://azure.microsoft.com/services/iot-hub/).

- **Azure Container Registry** es un servicio Microsoft Azure que permite a los desarrolladores almacenar imágenes de contenedor para varios tipos de contenedores. Para obtener más información, visite la [ **página Azure Container Registry Service**](https://azure.microsoft.com/services/container-registry/).

- **Azure Function App** es un servicio Microsoft Azure, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "functions", en Azure. Esto proporciona una manera de delegar el trabajo en la nube, en lugar de en la aplicación local, lo que puede tener muchas ventajas. **Azure Functions** admite varios lenguajes de desarrollo, incluidos \# C, \# F, Node.js, Java y PHP. Para obtener más información, visite la [ **página Azure Functions** .](/azure/azure-functions/functions-overview)

- **Azure Storage: Tables** es un servicio de Microsoft Azure, que permite a los desarrolladores almacenar datos estructurados, no SQL, en la nube, lo que hace que sea fácilmente accesible en cualquier lugar. El servicio ofrece un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible. Para más información, visite la página [ **Tablas de Azure.**](/azure/cosmos-db/table-storage-overview)

Este curso le enseñará a configurar y usar el servicio IoT Hub y, a continuación, visualizará una respuesta proporcionada por un dispositivo. Será el usuario el que aplique estos conceptos a una configuración IoT Hub Service personalizada, que es posible que esté creando.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td> Realidad mixta y Azure (313): Servicio IoT Hub</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

Para conocer los requisitos previos más actualizados para desarrollar con Mixed Reality, incluido el Microsoft HoloLens, visite el artículo Instalación de [las](../../install-the-tools.md) herramientas.

> [!NOTE]
> Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Python. Tenga en cuenta también que los requisitos previos y las instrucciones escritas de este documento representan lo que se ha probado y comprobado en el momento de escribir (julio de 2018). Puede usar el software más reciente, [](../../install-the-tools.md) como se muestra en el artículo instalación de las herramientas, aunque no se debe suponer que la información de este curso coincida perfectamente con lo que encontrará en el software más reciente que el que se muestra a continuación.

Se requiere el siguiente hardware y software:

- Windows 10 Fall Creators Update (o posterior), modo **de desarrollador habilitado**

    > [!WARNING]
    > No se puede ejecutar una máquina virtual mediante Hyper-V en Windows 10 Home Edition.

- Windows 10 SDK (versión más reciente)
- Un HoloLens, **modo de desarrollador habilitado**
- Visual Studio 2017.15.4 (solo se usa para acceder a Azure Cloud Explorer)
- Acceso a Internet para Azure y para IoT Hub Service. Para obtener más información, siga este [vínculo a la página IoT Hub servicio.](https://azure.microsoft.com/services/iot-hub/)
- Un modelo de Machine Learning. Si no tiene su propio modelo listo para usar, puede usar el modelo [proporcionado con este curso](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip).
- **Software de Hyper-V** habilitado en la máquina Windows 10 desarrollo.
- Una máquina virtual que ejecuta Ubuntu (16.4 o 18.4), que se ejecuta en la máquina de desarrollo o, como alternativa, puede usar un equipo independiente que ejecute Linux (Ubuntu 16.4 o 18.4). Puede encontrar más información sobre cómo crear una máquina virtual en Windows mediante Hyper-V en el capítulo "Antes de [empezar".](#before-you-start) (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Antes de comenzar

1. Configure y pruebe el HoloLens. Si necesita soporte técnico para configurar el HoloLens, asegúrese de visitar el artículo [HoloLens instalación de .](/hololens/hololens-setup)
2. Es una buena idea  realizar la calibración y el ajuste del **sensor** al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).

Para obtener ayuda sobre la calibración, siga este vínculo al artículo HoloLens [Calibración](/hololens/hololens-calibration#hololens-2).

Para obtener ayuda sobre la optimización de sensores, siga este vínculo al artículo HoloLens Sensor Tuning (Ajuste [de sensores).](/hololens/hololens-updates)

3. Configure la máquina **virtual Ubuntu** mediante **Hyper-V.** Los siguientes recursos le ayudarán con el proceso.
    1.  En primer lugar, siga este vínculo para descargar la [ISO de Ubuntu 16.04.4 LTS (Xenial Xerus).](https://au.releases.ubuntu.com/16.04/) Seleccione la **imagen de escritorio de PC de 64 bits (AMD64).**
    2.  Asegúrese de **que Hyper-V** está habilitado en Windows 10 máquina. Puede seguir este vínculo para obtener instrucciones sobre [cómo instalar y habilitar Hyper-V en Windows 10](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Inicie Hyper-V y cree una nueva máquina virtual Ubuntu. Puede seguir este vínculo para obtener una guía paso a paso sobre cómo crear [una máquina virtual con Hyper-V.](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine) Cuando se le solicite "Instalar un sistema operativo desde un archivo de imagen de **arranque",** seleccione la ISO de **Ubuntu** que descargó anteriormente.

    > [!NOTE]
    > No se sugiere el uso de creación rápida de **Hyper-V.**  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capítulo 1: Recuperación del Custom Vision modelo

Con este curso, tendrá acceso [a](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) un modelo de Custom Vision creado previamente que detecta teclados y mouse a partir de imágenes. Si lo usa, continúe con el [capítulo 2.](#chapter-2---the-container-registry-service)

Sin embargo, puede seguir estos pasos si desea usar su propio modelo de Custom Vision:

1. En la **Custom Vision Project** vaya a la **pestaña** Rendimiento.

    > [!WARNING]
    > El modelo debe usar un *dominio compacto* para exportar el modelo. Puede cambiar el dominio de modelos en la configuración del proyecto.

    ![pestaña de rendimiento](images/AzureLabs-Lab313-01.png)

2. Seleccione la **iteración** que desea exportar y haga clic en **Exportar.** Aparecerá una hoja.

    ![hoja de exportación](images/AzureLabs-Lab313-02.png)

3. En la hoja, haga clic **en Archivo de Docker.**

    ![selección de Docker](images/AzureLabs-Lab313-03.png)

4. Haga **clic en Linux** en el menú desplegable y, a continuación, haga clic en **Descargar.**

    ![Haga clic en Descargar.](images/AzureLabs-Lab313-04.png)

5. Descomprima el contenido. Lo usará más adelante en este curso.

## <a name="chapter-2---the-container-registry-service"></a>Capítulo 2: El servicio de Container Registry

El **Container Registry service es** el repositorio que se usa para hospedar los contenedores.

El **IoT Hub que** va a compilar y usar en este curso hace referencia a Container Registry **Service** para obtener los contenedores que se van a implementar en el dispositivo Perimetral.

1. En primer lugar, siga [este vínculo a Azure Portal](https://portal.azure.com/)e inicie sesión con sus credenciales.

2. Vaya **a Crear un recurso** y busque **Container Registry**.

    ![registro de contenedor](images/AzureLabs-Lab313-05.png)

3. Haga clic en **Crear**.

    ![](images/AzureLabs-Lab313-06.png)

4. Establezca los parámetros de configuración del servicio:

    1. Inserte un nombre para el proyecto; en este ejemplo, se llama **IoTCRegistry.**

    2. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

    3. Establezca la ubicación del servicio.

    4. Establezca **Usuario administrador en** **Habilitar**.

    5. Establezca **SKU** en **Básico.** 

    ![](images/AzureLabs-Lab313-07.png)

5. Haga **clic en** Crear y espere a que se creen los servicios. 

6. Una vez que se muestra la notificación que le informa de la creación correcta de la Container Registry *,* haga clic en **Ir** al recurso para que se le redirija a la página servicio.

    ![](images/AzureLabs-Lab313-08.png)

7. En la página *Container Registry* Servicio, haga clic en **Claves de acceso**.

8. Tenga en cuenta (podría usar su Bloc de notas) de los parámetros siguientes:
    1. **Servidor de inicio de sesión**
    2. **Nombre de usuario**
    3. **Contraseña**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capítulo 3: The IoT Hub Service

Ahora comenzará la creación y configuración de su IoT Hub **Service**.

1. Si aún no ha iniciado sesión, inicie sesión en [Azure Portal.](https://portal.azure.com)

2.  Una vez que  haya iniciado sesión, haga clic en Crear un recurso en la esquina superior izquierda, busque IoT Hub **y** haga clic en **Entrar.**

 ![buscar cuenta de almacenamiento](images/AzureLabs-Lab313-10.png)

3.  La nueva página proporcionará una descripción del servicio **de Storage cuenta.** En la parte inferior izquierda de este símbolo del sistema, haga clic en **el botón** Crear para crear una instancia de este servicio.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-11.png)

4.  Una vez que haya hecho clic en **Crear,** aparecerá un panel:

    1. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal).


    2. Seleccione una ubicación **adecuada** (use la misma ubicación en todos los servicios que cree en este curso).

    3. Inserte el nombre **deseado para** esta instancia de servicio.    

5.  En la parte inferior de la página, haga clic en **Siguiente: Tamaño y escala.**

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-12.png)

6.  En esta página, seleccione **el** plan de tarifa y escalado (si se trata de la primera instancia de IoT Hub Service, debe estar disponible un nivel gratuito).  

7.  Haga clic **en Revisar y crear.**

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-13.png)

8.  Revise la configuración y haga clic en **Crear**.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-14.png)

9. Una vez que se muestra la notificación que le informa de la creación correcta del servicio *IoT Hub,* haga clic en **Ir** al recurso para que se le redirija a la página servicio.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-15.png)

10. Desplácese por el panel lateral de la izquierda hasta que vea *Automático Administración de dispositivos*, haga clic **en IoT Edge**.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-16.png)

11. En la ventana que aparece a la derecha, haga clic en **Agregar IoT Edge Dispositivo**. Aparecerá una hoja a la derecha.

12. En la hoja, proporcione al nuevo dispositivo un identificador **de** dispositivo (un nombre de su elección). A continuación, haga clic en **Guardar**. Las *claves principal* y *secundaria* se generarán automáticamente, si tiene la opción Generar **automáticamente** marcada.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-17.png)

13. Volverá a la sección *IoT Edge dispositivos,* donde se mostrará el nuevo dispositivo. Haga clic en el nuevo dispositivo (descrito en rojo en la imagen siguiente). 

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-18.png)

14. En la *página Detalles del* dispositivo que aparece, tome una copia de la cadena de **conexión** (clave principal).

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-19.png)

15. Vuelva al panel de la izquierda y haga clic en *Directivas de acceso compartido* para abrirlo. 

16. En la página que aparece, haga clic **en iothubowner** y aparecerá una hoja a la derecha de la pantalla. 

17. Tome nota (en la Bloc de notas) de la cadena de conexión **(clave** principal) para su uso posterior al establecer la cadena de *conexión* en el dispositivo.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capítulo 4: Configuración del entorno de desarrollo

Para crear e implementar módulos *para IoT Hub Edge,* necesitará los siguientes componentes instalados en la máquina de desarrollo que ejecuta Windows 10:

1.  [Docker para Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), le pedirá que cree una cuenta para poder descargarla. 

    [![descargar Docker para Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker requiere *Windows 10 PRO*, *Enterprise 14393* o *Windows Server 2016 RTM*, para ejecutarse. Si está ejecutando otras versiones de Windows 10, puede intentar instalar Docker mediante el cuadro [de herramientas de Docker.](https://docs.docker.com/toolbox/toolbox_install_windows/)

2.  [Python 3.6.](https://www.python.org/downloads/)

    [![descargar Python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (también conocido como VS Code).](https://code.visualstudio.com/download)

    [![descargar VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Después de instalar el software mencionado anteriormente, deberá reiniciar la máquina.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capítulo 5: Configuración del entorno de Ubuntu

Ahora puede pasar a configurar el dispositivo que ejecuta el sistema **operativo Ubuntu.** Siga estos pasos para instalar el software necesario para implementar los contenedores en la placa:

> [!IMPORTANT]
> Siempre debe preceder a los comandos de terminal con **sudo** para que se ejecuten como usuario administrador. I.e:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Abra el **terminal de Ubuntu** y use el siguiente comando para instalar **pip**:

    > [! HINT] Puede abrir *Terminal* muy fácilmente mediante el método abreviado de teclado: **Ctrl + Alt + T**.

    ```bash
        sudo apt-get install python-pip
    ```

2.  A lo largo de este capítulo, es posible que terminal le pida permiso para usar el almacenamiento del dispositivo y que escriba **y/n** (sí o no), escriba  **"y"** y, a continuación, presione la tecla **Entrar** para aceptar.

3.  Una vez completado ese comando, use el siguiente comando para instalar **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Una **vez instalados pip** y **curl,** use el siguiente comando para instalar el entorno de ejecución de **IoT Edge**, esto es necesario para implementar y controlar los módulos en la placa:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. En este momento se le pedirá que abra el archivo de configuración en tiempo de ejecución *,* para insertar la cadena de conexión del dispositivo , que anotó (en su Bloc de notas), al crear el servicio **IoT Hub** ( en el paso [14, del capítulo 3](#chapter-3---the-iot-hub-service)). Ejecute la siguiente línea en el terminal para abrir ese archivo:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Se **mostrará el archivo config.yaml,** listo para su edición:

    > [!WARNING]
    > Cuando se abre este archivo, puede resultar un poco confuso. Se editará texto en este archivo, dentro del *propio terminal.* 

    1.  Use las teclas de dirección del teclado para desplazarse hacia abajo (tendrá que desplazarse hacia abajo un poco) para llegar a la línea que contiene":

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. Sustituya la línea, **incluidos los corchetes**, por la **cadena de conexión del dispositivo** que anotó anteriormente.

7. Con la cadena de conexión en su lugar, en el teclado, presione las **teclas Ctrl-X** para guardar el archivo. Se le pedirá que confirme escribiendo **Y**. A continuación, presione **la tecla Entrar** para confirmar. Volverá al *terminal normal.* 

8. Una vez que todos estos comandos se han ejecutado correctamente, habrá instalado el IoT Edge **runtime**. Una vez inicializado, el tiempo de ejecución se iniciará por sí solo cada vez que el dispositivo esté encendido y se pondrá en segundo plano, esperando a que los módulos se implementen desde IoT Hub **Service**.

9.  Ejecute la siguiente línea de comandos para inicializar el *IoT Edge runtime*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Si realiza cambios en el archivo .yaml o en la configuración anterior, deberá volver a ejecutar la línea de reinicio anterior, en *Terminal*.

10. Compruebe el estado *IoT Edge runtime mediante* la ejecución de la siguiente línea de comandos. El tiempo de ejecución debe aparecer con el estado **activo (en ejecución)** en texto verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Presione las **teclas Ctrl+C** para salir de la página de estado. Puede comprobar que el IoT Edge *runtime* está extracndo los contenedores correctamente escribiendo el siguiente comando:

    ```bash
        sudo docker ps
    ```

12. Debe aparecer una lista con dos (2) contenedores. Estos son los módulos predeterminados que crea automáticamente IoT Hub Service (edgeAgent y edgeHub). Una vez que cree e implemente sus propios módulos, aparecerán en esta lista, debajo de los predeterminados.

## <a name="chapter-6---install-the-extensions"></a>Capítulo 6: Instalación de las extensiones

> [!IMPORTANT]
> Los siguientes capítulos (6-9) se realizarán en el Windows 10 máquina.

1. Abra **VS Code**.

2. Haga clic en **el botón Extensiones** (cuadrado) de la barra izquierda de VS Code, para abrir el panel **Extensiones**.

3. Busque e instale las siguientes extensiones (como se muestra en la imagen siguiente):

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![Creación del contenedor](images/AzureLabs-Lab313-24.png)

4. Una vez instaladas las extensiones, cierre y vuelva a abrir VS Code.

5. Con VS Code abrir una vez más, vaya a **Ver**  >  **terminal integrado.**

6. Ahora instalará **Cookiecutter.** En el terminal, ejecute el siguiente comando de Bash:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT] Si tiene problemas con este comando: 
    >1. Reinicie VS Code o el equipo.
    >2. Puede que sea necesario cambiar el terminal de **VS Code al** que ha estado usando para instalar Python, es decir, **PowerShell** (especialmente en caso de que el entorno de Python ya esté instalado en el equipo). Con terminal abierto, encontrará el menú desplegable en el lado derecho del terminal.
     ![Creación del contenedor](images/AzureLabs-Lab313-24b.png) 
    >3. Asegúrese de que la **ruta de instalación** de Python se agrega como variable de **entorno** en el equipo. Cookiecutter debe formar parte de la misma ruta de acceso de ubicación. Siga este vínculo [para obtener más información sobre las variables de entorno](/windows/win32/procthread/environment-variables), 

7. Una **vez que Cookiecutter** haya terminado de instalarse, debe reiniciar la máquina para que **Cookiecutter** se reconozca como un comando en el entorno del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capítulo 7: Creación de la solución de contenedor

En este momento, debe crear el contenedor, con el módulo , para insertarlo en el *Container Registry*. Una vez que haya insertado el contenedor, usará el servicio *IoT Hub Edge* para implementarlo en el dispositivo, que ejecuta el entorno de ejecución *IoT Edge .*

1. En VS Code, haga clic **en Ver paleta** de  >  **comandos**.

2. En la paleta, busque y ejecute **Azure IoT Edge: New Iot Edge Solution**.

3. Vaya a la ubicación en la que desea crear la solución. Presione la **tecla Entrar** para aceptar la ubicación.

4. Asigne un nombre a la solución. Presione la **tecla Entrar** para confirmar el nombre proporcionado.

5. Ahora se le pedirá que elija el marco de trabajo de plantilla para la solución. Haga clic **en Módulo de Python.** Presione la **tecla Entrar** para confirmar esta opción.

6. Asigne un nombre al módulo. Presione la **tecla Entrar** para confirmar el nombre del módulo. Asegúrese de tomar una nota (con la Bloc de notas) del nombre del módulo, ya que se usa más adelante.

7. Observará que aparecerá una dirección del repositorio de imágenes *de Docker pre-creada* en la paleta. Tendrá el siguiente aspecto:

    **localhost:5000/-THE NAME OF YOUR MODULE-**. 

8. Elimine **localhost:5000** y, en su lugar, inserte la dirección del servidor de inicio de sesión de Container Registry, que *anotó*  al crear el servicio **Container Registry** ( en el paso [8,](#chapter-2---the-container-registry-service)del capítulo 2 ). Presione la **tecla Entrar** para confirmar la dirección.

9. En este momento, se creará la solución que contiene la plantilla para el módulo de Python y su estructura se mostrará en la pestaña Explorar **,** de VS Code, en el lado izquierdo de la pantalla. Si la **pestaña Explorar** no está abierta, puede abrirla haciendo clic en el botón de nivel superior, en la barra de la izquierda.

    ![Creación del contenedor](images/AzureLabs-Lab313-25.png)

10. El último paso de este capítulo es hacer clic y abrir el archivo **.env**, desde la pestaña Explorar y agregar el nombre de usuario y la contraseña Container Registry   **.** Git omite este archivo, pero al compilar el contenedor, establecerá las credenciales para acceder al **Container Registry Service**.

    ![Creación del contenedor](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capítulo 8: Edición de la solución de contenedor

Ahora completará la solución de contenedor mediante la actualización de los siguientes archivos:

- *script <span></span> de Python .py* principal.
- *requirements.txt*.
- *deployment.template.jsen*.
- *Dockerfile.amd64*

A continuación, creará la *carpeta images,* que usa el script de Python para comprobar si hay imágenes que coincidan con *el Custom Vision modelo*. Por último, agregará el archivo *labels.txt,* para ayudar a leer el modelo, y el *archivo model.pb,* que es el modelo.

1. Con VS Code, vaya a la carpeta del módulo y busque el script denominado **<span></span> principal .py**. Haga doble clic para abrirlo.

2. Elimine el contenido del archivo e inserte el código siguiente:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Abra el archivo denominado **requirements.txt** y sustituya su contenido por lo siguiente:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Abra el archivo denominado **deployment.template.jsen** y sustituya su contenido siguiendo las instrucciones siguientes:

    1. Dado que tendrá su propia estructura JSON única, deberá editarla a mano (en lugar de copiar un ejemplo). Para facilitar esto, use la imagen siguiente como guía.
    2. Las áreas que tendrán un aspecto diferente al de usted, pero que **NO debe cambiar, se resaltan en amarillo.**
    3. **Las secciones que debe eliminar son un rojo resaltado.**
    4. Tenga cuidado de eliminar los corchetes correctos y también quite las comas.

        ![Creación del contenedor](images/AzureLabs-Lab313-27.png)

    5. Sin embargo, el JSON completado debe ser parecido a la imagen siguiente (con sus diferencias únicas: nombre *de usuario, contraseña,* nombre de módulo o referencias de módulo):

        ![Creación del contenedor](images/AzureLabs-Lab313-28.png)

5.  Abra el archivo denominado **Dockerfile.amd64** y sustituya su contenido por lo siguiente:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Haga clic con el botón derecho en la carpeta situada debajo de **los** módulos (tendrá el nombre que proporcionó anteriormente; en el ejemplo más abajo, se denomina *pythonmodule*) y haga clic en **Nueva carpeta**. Asigne a las imágenes de **carpeta el nombre**.

7.  Dentro de la carpeta , agregue algunas imágenes que contengan el mouse o el teclado. Estas serán las imágenes que analizará el modelo de Tensorflow.

    > [!WARNING]
    > Si usa su propio modelo, deberá cambiarlo para reflejar los datos de sus propios modelos.

8.  Ahora deberá recuperar los archivos **labels.txt** y **model.pb** de la carpeta model, que descargó anteriormente (o creó a partir de su propio **servicio de Custom Vision),** en el capítulo [1.](#chapter-1---retrieve-the-custom-vision-model) Una vez que tenga los archivos, colóqlos dentro de la solución, junto con los demás archivos. El resultado final debe ser parecido a la imagen siguiente:

    ![Creación del contenedor](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capítulo 9: Empaquetado de la solución como contenedor

1.  Ahora está listo para "empaquetar" los archivos como un contenedor e insertarlo en el **Azure Container Registry**. En VS Code, abra el Terminal integrado **(Ver** *terminal* integrado o Ctrl) y use la siguiente línea para iniciar sesión en Docker (sustituya los valores del comando por las credenciales de su  >    + **\`** **Azure Container Registry (ACR)**  ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Haga clic con el botón derecho en el **archivodeployment.template.jsen** y haga clic en Compilar IoT Edge **solución**. Este proceso de compilación tarda bastante tiempo (dependiendo del dispositivo), por lo que debe estar preparado para esperar. Una vez que finalice el proceso de compilación, **sedeployment.js** en el archivo dentro de una nueva carpeta denominada **config**.

    ![crear implementación](images/AzureLabs-Lab313-30.png)

3. Vuelva a **abrir la paleta de** comandos y busque **Azure: Iniciar sesión.** Siga las indicaciones con las credenciales de la cuenta de Azure. VS Code le proporcionará una opción para Copiar y abrir *,* que copiará el código del dispositivo que necesitará pronto y abrirá el explorador web predeterminado. Cuando se le pida, pegue el código del dispositivo para autenticar la máquina.

    ![copiar y abrir](images/AzureLabs-Lab313-31.png)

4. Una vez que haya iniciado sesión, observará que, en la parte inferior del *panel* Explorar, hay una nueva sección denominada Azure IoT **Hub Devices**. Haga clic en esta sección para expandirla.

    ![dispositivo perimetral](images/AzureLabs-Lab313-32.png)

5. Si el dispositivo no está aquí, deberá hacer clic con el botón derecho en *Azure IoT Hub Devices* y, a continuación, hacer clic en Establecer IoT Hub cadena de **conexión**. A continuación, verá que **la** paleta de comandos (en la parte superior de VS Code), le pedirá que escriba la cadena *de conexión*. Esta es la *cadena de conexión* que anotó al final del capítulo [3.](#chapter-3---the-iot-hub-service) Presione la **tecla Entrar,** una vez que haya copiado la cadena.    

6. El dispositivo debe cargarse y aparecer. Haga clic con el botón derecho en el nombre del dispositivo y, a continuación, haga clic **en Crear implementación para un único dispositivo.**

    ![crear implementación](images/AzureLabs-Lab313-33b.png)

7. Recibirá un mensaje *de Explorador de archivos,* donde puede ir a la carpeta **config** y, a continuación, seleccionar el **deployment.jsen el** archivo. Con ese archivo seleccionado, haga clic en **el botón Seleccionar manifiesto de implementación** perimetral.

    ![crear implementación](images/AzureLabs-Lab313-34.png)

8. En este punto, ha proporcionado a **IoT Hub Service** el manifiesto para que implemente el contenedor, como un módulo, desde el Azure Container Registry **,** implementando de forma eficaz en el dispositivo.

9. Para ver los mensajes enviados desde el dispositivo al IoT Hub, vuelva a hacer clic con el botón derecho en el nombre del dispositivo en la sección Azure IoT Hub Devices (Dispositivos **de Azure IoT Hub),** en el **panel** Explorer (Explorador) y haga clic en Start Monitoring D2C Message (Iniciar supervisión del mensaje **D2C).** Los mensajes enviados desde el dispositivo deben aparecer en el terminal de VS. Tenga paciencia, ya que esto puede tardar algún tiempo. Consulte el siguiente capítulo para depurar y comprobar si la implementación se ha realizado correctamente.

Este módulo iterará ahora entre las imágenes de la carpeta **images** y las analizará, con cada iteración. Obviamente, esto es simplemente una demostración de cómo conseguir que el modelo de aprendizaje automático básico funcione en un entorno IoT Edge dispositivo. 

Para ampliar la funcionalidad de este ejemplo, puede continuar de varias maneras. Una manera podría ser incluir código en el contenedor, que captura fotos de una cámara web conectada al dispositivo y guarda las imágenes en la carpeta images. 

Otra manera podría ser copiar las imágenes del dispositivo IoT en el contenedor. Una manera práctica de hacerlo es ejecutar el siguiente comando en el terminal del dispositivo IoT (quizás una aplicación pequeña podría realizar el trabajo, si quisiera automatizar el proceso). Puede probar este comando ejecutándose manualmente desde la ubicación de la carpeta donde se almacenan los archivos:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capítulo 10: Depuración de IoT Edge Runtime

A continuación se muestra una lista de líneas de comandos y sugerencias para ayudarle a supervisar y depurar la actividad de mensajería de *IoT Edge Runtime*, desde el **dispositivo Ubuntu**. 

- Compruebe el *estado IoT Edge runtime* mediante la ejecución de la siguiente línea de comandos:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > No olvide presionar **Ctrl + C** para terminar de ver el estado.

- Enumera los contenedores que están implementados actualmente. Si el *IoT Hub service* ha implementado correctamente los contenedores, se mostrarán mediante la ejecución de la siguiente línea de comandos:

    ```bash
        sudo iotedge list
    ```

    Or

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Lo anterior es una buena manera de comprobar si el módulo se ha implementado correctamente, como aparecerá en la lista. De lo **contrario, solo verá** *edgeHub* y *edgeAgent.*

- Para mostrar los registros de código de un contenedor, ejecute la siguiente línea de comandos:

    ```bash
        journalctl -u iotedge
    ```

**Comandos útiles para administrar el entorno IoT Edge runtime:**

-  Para eliminar todos los contenedores del host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Para detener el IoT Edge *runtime*:

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capítulo 11: Creación de Table Service 

Vuelva a Azure Portal, donde creará una instancia de Azure Tables Service mediante la creación de un recurso de Almacenamiento.

1. Si aún no ha iniciado sesión, inicie sesión en [Azure Portal.](https://portal.azure.com)

2. Una vez que haya iniciado sesión, haga clic en Crear un recurso , en la esquina superior izquierda, busque Cuenta de almacenamiento y presione la tecla **Entrar** para iniciar la búsqueda.

3. Una vez que haya aparecido, haga clic **en Cuenta de almacenamiento: blob, archivo, tabla, cola** en la lista.

    ![buscar cuenta de almacenamiento](images/AzureLabs-Lab313-35.png)

4. La nueva página proporcionará una descripción del servicio **de la cuenta de** almacenamiento. En la parte inferior izquierda de este símbolo del sistema, haga clic en **el botón** Crear para crear una instancia de este servicio.

    ![creación de una instancia de almacenamiento](images/AzureLabs-Lab313-36.png)

5. Una vez que haya hecho clic en **Crear,** aparecerá un panel:

    1. Inserte el nombre **deseado para** esta instancia de servicio ( debe estar todo *en minúsculas).*

    2. En **Modelo de implementación ,** haga clic en Administrador de **recursos.**

    3. En **Tipo de cuenta**, mediante el menú desplegable, haga clic en Almacenamiento **(uso general v1).**

    4. Haga clic en una **ubicación adecuada.**
    
    5. En el **menú desplegable Replicación,** haga clic en Almacenamiento con redundancia geográfica con acceso de **lectura (RA-GRS).**

    6. En **Rendimiento ,** haga clic en **Estándar.**

    7. En la sección **Se requiere transferencia** segura, haga clic en **Deshabilitado.**

    8. En el **menú desplegable Suscripción,** haga clic en una suscripción adecuada.

    9. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    10. Deje **Redes virtuales** como **Deshabilitado,** si esta es una opción para usted.

    11. Haga clic en **Crear**.

        ![rellenar los detalles de almacenamiento](images/AzureLabs-Lab313-37.png)

6. Una vez que haya hecho clic en **Crear**, tendrá que esperar a que se cree el servicio, esto puede tardar un minuto.

7. Una vez creada la instancia de servicio, aparecerá una notificación en el portal. Haga clic en las notificaciones para explorar la nueva instancia del servicio.

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab313-38.png)

8. Haga clic **en el botón Ir** al recurso de la notificación y se le llevará a la nueva página de información general de la instancia del servicio de almacenamiento.

    ![ir al recurso](images/AzureLabs-Lab313-39.png)

9. En la página de información general, en el lado derecho, haga clic en **Tablas**.
    
    ![Tablas](images/AzureLabs-Lab313-40.png)

10. El panel de la derecha cambiará para mostrar la información de **Table Service,** donde debe agregar una nueva tabla. Para ello, haga clic en **el botón + Tabla** situado en la esquina superior izquierda.

    ![abrir tablas](images/AzureLabs-Lab313-41.png)

11. Se mostrará una nueva página, en la que debe escribir un nombre **de tabla**. Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores (creación de function app y Power BI). Inserte **IoTMessages** como nombre (puede elegir el suyo propio, solo tiene que recordarlo cuando lo utilice más adelante en este documento) y haga clic en **Aceptar.** 

12. Una vez creada la nueva tabla, podrá verla en la página **Table Service** (en la parte inferior).

    ![nueva tabla creada](images/AzureLabs-Lab313-42.png)  

13. Ahora haga **clic** en Claves de  acceso y tome una copia del nombre y la clave **de** la cuenta de almacenamiento (mediante el Bloc de notas), usará estos valores más adelante en este curso, al crear la aplicación de función **de Azure**.

    ![nueva tabla creada](images/AzureLabs-Lab313-43.png) 

14. Con el panel de la izquierda de nuevo, desplácese hasta la sección *Table Service* y haga clic en Tablas **(o** Examinar tablas **,** en los portales más recientes) y tome una copia de la dirección **URL** de tabla (mediante el Bloc de notas). Usará este valor más adelante en este curso, al vincular la tabla a la **Power BI** aplicación.

    ![nueva tabla creada](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capítulo 12: Finalización de la tabla de Azure

Ahora que se ha configurado la cuenta de almacenamiento de **Table Service,** es el momento de agregarle datos, que se usarán para almacenar y recuperar información. La edición de las tablas se puede realizar a través **Visual Studio**.

1. Abra **Visual Studio** (**no Visual Studio Code).**

2. En el menú, haga clic **en**  >  **Ver Cloud Explorer**.

    ![abrir Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. El **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, ya que la carga puede tardar tiempo).

    > [!WARNING] 
    > Si la suscripción que usó para crear las cuentas *de almacenamiento* no está visible, asegúrese de que tiene: 
    > - Ha iniciado sesión en la misma cuenta que la que usó para Azure Portal.
    > - Seleccione la suscripción en la página Administración de cuentas (es posible que tenga que aplicar un filtro desde la configuración de la cuenta):  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab313-46.png)

4. Se mostrarán los servicios en la nube de Azure. Busque **Cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda para expandir las cuentas.

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab313-47.png)

5. Una vez expandida, la cuenta de **Almacenamiento recién creada** debe estar disponible. Haga clic en la flecha situada a la izquierda del  almacenamiento y, después, una vez  que se expanda, busque Tablas y haga clic en la flecha situada junto a eso para mostrar la tabla que creó en el último capítulo. Haga doble clic en la **tabla**.

6. La tabla se abrirá en el centro de la Visual Studio ventana. Haga clic en el icono de tabla **+** con el signo (más) en ella.

    ![agregar nueva tabla](images/AzureLabs-Lab313-48.png)

7. Aparecerá una ventana en la que se le pedirá que *agregue la entidad*. Solo creará una entidad, aunque tendrá tres propiedades. Observará que Ya se *proporcionan PartitionKey* y *RowKey,* ya que la tabla los usa para buscar los datos. 

    ![partición y clave de fila](images/AzureLabs-Lab313-49.png)

8. Actualice los siguientes valores:

    - Nombre: **PartitionKey**, Valor: **PK_IoTMessages** 

    - Nombre: **RowKey**, Valor: **RK_1_IoTMessages** 

9. A continuación, **haga clic en Agregar** propiedad (en la parte inferior izquierda de la ventana *Agregar* entidad) y agregue la siguiente propiedad:

    - **MessageContent**, como una *cadena*, deje el valor vacío.

10. La tabla debe coincidir con la de la imagen siguiente:

    ![agregar valores correctos](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > La razón por la que la entidad tiene el número 1 en la clave de fila es porque es posible que quiera agregar más mensajes, en caso de que desee experimentar más con este curso.

11. Haga **clic en** Aceptar cuando haya terminado. La tabla ya está lista para usarse.

## <a name="chapter-13---create-an-azure-function-app"></a>Capítulo 13: Creación de una instancia de Azure Function App 

Ahora es el momento de crear una instancia de *Azure Function App,* a la que llamará el servicio *IoT Hub* para almacenar los mensajes del dispositivo *IoT Edge* en **Table** Service, que creó en el capítulo anterior.

En primer lugar, debe crear un archivo que permita a la función de Azure cargar las bibliotecas que necesita.

1.  Abra **Bloc de notas** (presione la *tecla Windows y* escriba el Bloc de *notas).*

    ![abrir el Bloc de notas](images/AzureLabs-Lab313-51.png)

2.  Con Bloc de notas, inserte la estructura JSON siguiente en ella. Una vez hecho esto, guárdelo en el escritorio como **project.jsen**. Este archivo define las bibliotecas que usará la función. Si ha usado NuGet, le resultará familiar.
    
    > [!WARNING]
    > Es importante que la nomenclatura sea correcta; asegúrese de que **NO tiene una extensión .txt** archivo. Consulte a continuación como referencia:
    >
    > ![Guardado de JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Inicie sesión en [Azure Portal](https://portal.azure.com).

4.  Una vez que haya  iniciado sesión, haga clic en Crear un recurso en la esquina superior izquierda y busque **Function App** y presione la **tecla Entrar** para buscar. Haga *clic en Function App* en los resultados para abrir un nuevo panel.

    ![buscar aplicación de función](images/AzureLabs-Lab313-53.png)

5.  El nuevo panel proporcionará una descripción de **Function App** Service. En la parte inferior izquierda de este panel, haga clic en **el botón** Crear para crear una asociación con este servicio.

    ![instancia de function app](images/AzureLabs-Lab313-54.png)

6.  Una vez que haya hecho clic en **Crear,** rellene lo siguiente:

    1. En **Nombre de la** aplicación, inserte el nombre que desee para esta instancia de servicio.

    2. Seleccione una opción en **Suscripción**.

    3. Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea una función **App Service,** debe estar disponible un nivel gratis.

    4. Elija un **grupo de recursos** o cree uno nuevo. Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure. Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común.

        > Si desea obtener más información sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](/azure/azure-resource-manager/resource-group-portal).

    5. Para **el sistema operativo**, haga Windows, ya que esa es la plataforma prevista.

    6. Seleccione un **plan de hospedaje** (en este tutorial se usa un plan de **consumo).**

    7. Seleccione una **ubicación** (elija la misma ubicación que el almacenamiento que ha creado en el paso anterior).

    8. Para la **Storage,** debe seleccionar el servicio **Storage que creó en el paso anterior.**

    9. No necesitará *application* Ideas en esta aplicación, así que no dude en dejarla **desactivada.**

    10. Haga clic en **Crear**.

        ![creación de una nueva instancia](images/AzureLabs-Lab313-55.png)

7.  Una vez que haya hecho clic en **Crear,** tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.

8.  Una vez creada la instancia de servicio, aparecerá una notificación en el portal.

    ![nueva notificación](images/AzureLabs-Lab313-56.png)

9.  Haga clic en la notificación, una vez que la implementación se haya realizado correctamente (ha finalizado).

10. Haga clic **en el botón Ir** al recurso de la notificación para explorar la nueva instancia de servicio. 

    ![ir al recurso](images/AzureLabs-Lab313-57.png)

11. En el lado izquierdo del nuevo panel, haga clic en el icono (más) situado junto **+** a *Funciones* para crear una función.

    ![agregar nueva función](images/AzureLabs-Lab313-58.png)

12. En el panel central, aparecerá **la ventana Creación** de funciones. Desplácese hacia abajo y haga clic en **Función personalizada**.

    ![función personalizada](images/AzureLabs-Lab313-59.png)

13. Desplácese hacia abajo en la página siguiente, hasta que IoT Hub (Centro de **eventos)** y, a continuación, haga clic en él.

    ![función personalizada](images/AzureLabs-Lab313-60.png)

14. En la **hoja IoT Hub (Centro de eventos),** establezca **el** lenguaje en **C#** y, a continuación, haga clic en **nuevo**.

    ![función personalizada](images/AzureLabs-Lab313-61.png)

15. En la ventana que aparecerá,  asegúrese de que IoT Hub está seleccionado y el nombre del campo IoT Hub corresponde *al* nombre del servicio *IoT Hub* que ha creado anteriormente ( en el paso [8, del capítulo 3](#chapter-3---the-iot-hub-service)). A continuación, haga **clic en el botón** Seleccionar.

    ![función personalizada](images/AzureLabs-Lab313-62.png)

16. De nuevo en la **IoT Hub (Centro de eventos),** haga clic en **Crear**.

    ![función personalizada](images/AzureLabs-Lab313-63.png)

17. Se le redirigirá al editor de funciones.

    ![función personalizada](images/AzureLabs-Lab313-64.png)

18. Elimine todo el código que incluye y reemplácelo por lo siguiente:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Cambie las siguientes variables para que se correspondan con los valores adecuados **(valores** de tabla y **Storage,** del paso [11 y 13, respectivamente,](#chapter-11---create-table-service)del capítulo 11), que encontrará en la cuenta de Storage **:**

    - **tableName**, con el nombre de la **tabla ubicada** en la **Storage cuenta.**
    - **tableURL**, con la dirección URL de **la tabla** ubicada en la **Storage cuenta.**
    - **storageAccountName**, con el nombre del valor correspondiente con el nombre de la cuenta **Storage cuenta.**
    - **storageAccountKey**, con la clave que ha obtenido en el Storage que ha creado anteriormente.

    ![función personalizada](images/AzureLabs-Lab313-65.png)

20. Con el código en su lugar, haga clic **en Guardar.**

21. A continuación, **\<** haga clic en el icono (flecha) del lado derecho de la página.

    ![función personalizada](images/AzureLabs-Lab313-66.png)

22. Un panel se deslizará desde la derecha. En ese panel, haga **clic Upload** y aparecerá un Explorador *de* archivos.

23. Vaya a y haga  clic en elproject.jsen el archivo que creó en **Bloc de notas** anteriormente y, a continuación, haga clic en **el botón** Abrir. Este archivo define las bibliotecas que usará la función.

    ![función personalizada](images/AzureLabs-Lab313-67.png)

24. Cuando se haya cargado el archivo, aparecerá en el panel de la derecha. Al hacer clic en él, se abrirá en el Editor **de** funciones. Debe tener exactamente **el mismo** aspecto que la imagen siguiente.

    ![función personalizada](images/AzureLabs-Lab313-68.png)

25. En este momento, sería bueno probar la capacidad de la función para almacenar el mensaje en la *tabla*. En la parte superior derecha de la ventana, haga clic en **Probar**.

    ![función personalizada](images/AzureLabs-Lab313-69.png)

26. Inserte un mensaje en el cuerpo **de la solicitud**, como se muestra en la imagen anterior, y haga clic en **Ejecutar**. 

27. La función se ejecutará y mostrará el estado del resultado (observará  el estado **verde 202 Aceptado,** encima de la ventana Salida, lo que significa que se ha realizado una llamada correcta):

    ![resultado de salida](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capítulo 14: Visualización de mensajes activos

Si ahora abre Visual Studio **(** no Visual Studio Code), puede visualizar el resultado del mensaje de prueba, ya que se almacenará en el área de cadena *MessageContent.*

![función personalizada](images/AzureLabs-Lab313-71.png)

Con Table Service y Function App en su lugar, los mensajes del dispositivo Ubuntu aparecerán en la *tabla IoTMessages.* Si aún no se está ejecutando, vuelva a iniciar el dispositivo y podrá ver los mensajes de resultados del dispositivo y el módulo, dentro de la tabla, mediante Visual Studio *Cloud Explorer*.

![visualizar datos](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capítulo 15: Power BI configuración

Para visualizar los datos desde el dispositivo IOT, configurará Power BI **(versión** de escritorio) para recopilar los datos de *Table* Service, que acaba de crear. La *HoloLens* de la Power BI usará los datos para visualizar el resultado.

1.  Abra el Microsoft Store en Windows 10 y busque **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Descargue la aplicación. Una vez que haya terminado de descargarse, ábralo.

3.  Inicie sesión *Power BI* con su **Microsoft 365 cuenta**. Es posible que se le redirija a un explorador para registrarse. Una vez que se haya registrado, vuelva a la aplicación Power BI e inicie sesión de nuevo.

4.  Haga clic **en Obtener datos** y, a continuación, haga clic en **Más...**.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Haga clic **en Azure**, Tabla de **Azure Storage** y, a continuación, haga clic **en Conectar**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Se le pedirá que inserte la dirección **URL** de tabla que recopiló anteriormente ( en el paso [13 del capítulo 11](#chapter-11---create-table-service)), al crear table service. Después de insertar la dirección URL, elimine la parte de la ruta de acceso que hace referencia a la "sub carpeta" de la tabla (que era IoTMessages, en este curso). El resultado final debe ser el que se muestra en la imagen siguiente. A continuación, haga clic **en Aceptar**.

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Se le pedirá que inserte la clave de **Storage que** anotó anteriormente ( en el paso 11 del capítulo [11)](#chapter-11---create-table-service)al crear la tabla Storage. A continuación, **haga clic Conectar**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Se **mostrará un panel** navegador, marque la casilla situada junto a la tabla y haga clic en **Cargar**.

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabla ahora se ha cargado en Power BI, pero requiere una consulta para mostrar los valores en ella. Para ello, haga clic con el botón derecho en el nombre de la tabla que se encuentra en el **panel CAMPOS** del lado derecho de la pantalla. A continuación, haga **clic en Editar consulta.**

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Se **abrirá Power Query Editor**  de archivos como una nueva ventana, mostrando la tabla. Haga clic en la **palabra Registro** en la *columna Contenido* de la tabla para visualizar el contenido almacenado.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Haga clic **en Into Table**(En tabla), en la parte superior izquierda de la ventana. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Haga clic **en Cerrar & Aplicar**.

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Una vez que haya terminado de cargar la consulta, en el **panel CAMPOS**, en el lado derecho de la pantalla, marque las casillas correspondientes a los parámetros **Nombre** y Valor **para** visualizar el contenido de la columna **MessageContent.**

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Haga clic en **el icono de disco azul** situado en la parte superior izquierda de la ventana para guardar el trabajo en la carpeta que prefiera.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. Ahora puede hacer clic en el botón Publicar para cargar la tabla en el área de trabajo. Cuando se le solicite, haga clic en **Mi área de trabajo** y en *Seleccionar.* Espere a que muestre el resultado correcto del envío.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> El siguiente capítulo es HoloLens específico. Power BI no está disponible actualmente como una aplicación envolvente, pero puede ejecutar la versión de escritorio en el portal de Windows Mixed Reality (también conocido como Casa sobre el acantilado), a través de la aplicación de escritorio.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capítulo 16: Mostrar Power BI datos en HoloLens

1. En el HoloLens, inicie sesión en la **Microsoft Store**, pulsando en su icono en la lista de aplicaciones.

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. Busque y, a **continuación, descargue Power BI** aplicación.

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. Inicie **Power BI** desde la lista de aplicaciones. 

4. **Power BI** puede pedirle que inicie sesión en su **cuenta de Microsoft 365 .**

5. Una vez dentro de la aplicación, el área de trabajo debe mostrarse de forma predeterminada, como se muestra en la imagen siguiente. Si esto no ocurre, simplemente haga clic en el icono del área de trabajo en el lado izquierdo de la ventana.

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>Ha finalizado la IoT Hub aplicación.

Enhorabuena, ha creado correctamente IoT Hub Service, con un dispositivo Virtual Machine Edge simulado. El dispositivo puede comunicar los resultados de un modelo de aprendizaje automático a una instancia de Azure Table Service, facilitado por una aplicación de función de Azure, que se lee en Power BI y se visualiza dentro de un Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Ejercicios extra

### <a name="exercise-1"></a>Ejercicio 1

Expanda la estructura de mensajería almacenada en la tabla y mostrarla como un gráfico. Es posible que quiera recopilar más datos y almacenarlo en la misma tabla, para que se muestre más adelante.

### <a name="exercise-2"></a>Ejercicio 2

Cree un módulo de "captura de cámara" adicional que se implementará en la placa de IoT, para que pueda capturar imágenes a través de la cámara que se analizarán.
