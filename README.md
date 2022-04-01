# ¿Que es Proxmox VE?

Proxmox Virtual Environment o mejor conocido como [Proxmox VE][1_0] o PVE, es un servidor de [código abierto][1_1] que nos permite virtualizar y gestionar otros sistemas operativos, este servidor fue desarrollado por medio de una distribución de [GNU/Linux][1_2] basada en [Debian][1_3], la cual usa también un kernel modificado de [Ubuntu][1_4] LTS para así poder ejecutar varias [máquinas virtuales][1_5] y [contenedores][1_6] en un solo servidor, Proxmox VE también incluye una consola web y  herramientas de líneas de comandos qué garantizan una accesibilidad simple y rápida.

[1_0]:https://es.wikipedia.org/wiki/Proxmox_Virtual_Environment

[1_1]:https://es.wikipedia.org/wiki/Software_de_c%C3%B3digo_abierto

[1_2]:https://es.wikipedia.org/wiki/Distribuci%C3%B3n_Linux

[1_3]:https://es.wikipedia.org/wiki/Debian_GNU/Linux

[1_4]:https://es.wikipedia.org/wiki/Ubuntu

[1_5]:https://es.wikipedia.org/wiki/M%C3%A1quina_virtual

[1_6]:https://es.wikipedia.org/wiki/Virtualizaci%C3%B3n_a_nivel_de_sistema_operativo

# Requisitos del sistema
Para servidores de producción, se necesita equipo de servidor de alta calidad. Proxmox VE admite la agrupación en clústeres, lo que significa que varias instalaciones de Proxmox VE se pueden administrar de forma centralizada gracias a la funcionalidad de clúster integrada. Proxmox VE puede usar almacenamiento local como (DAS), SAN, NAS, así como almacenamiento compartido y distribuido (Ceph).

## Hardware recomendado

* Intel EMT64 o AMD64 con indicador de CPU Intel VT/AMD-V.

* Memoria, mínimo 2 GB para servicios OS y Proxmox VE. Más memoria designada para invitados. Para Ceph o ZFS se requiere memoria adicional, aproximadamente 1 GB de memoria por cada TB de almacenamiento utilizado.

* Almacenamiento rápido y redundante, mejores resultados con discos SSD.

* Almacenamiento del sistema operativo: RAID de hardware con caché de escritura protegida por baterías ("BBU") o no RAID con caché ZFS y SSD.

* Almacenamiento de VM: para el almacenamiento local, use un RAID de hardware con caché de escritura respaldada por batería (BBU) o no RAID para ZFS. Ni ZFS ni Ceph son compatibles con un controlador RAID de hardware. El almacenamiento compartido y distribuido también es posible.

* NIC Gbit redundantes, NIC adicionales según la tecnología de almacenamiento preferida y la configuración del clúster: también se admiten 10 Gbit y más.

* Para el paso a través de PCI(e), se necesita una CPU con indicador de CPU VT-d/AMD-d.

## Hardware mínimo (solo para pruebas)

* CPU: 64 bits (Intel EMT64 o AMD64).

* CPU/placa base compatible con Intel VT/AMD-V (para soporte de virtualización completa de KVM)

* Mínimo 1 GB de RAM.

* Disco duro.

* ellos NADA.

## Navegadores webs compatibles para acceder a la interfaz web

Para usar la interfaz web, necesita un navegador moderno, esto incluye:

* Firefox, una versión del año en curso o la última versión de soporte extendido.

* Chrome, un lanzamiento del año en curso.

* Versión compatible actualmente de Microsoft de Edge.

* Safari, un lanzamiento del año en curso.

# 1. Descarga de la imagen ISO

Para dar inicio a este tutorial, primero tendremos que descargar el servidor [Proxmox VE][2_0] desde su página oficial.

Una ven estamos en la página nos vamos a ubicar en el apartado de <b>Downloads</b> para acto seguido dar un click izquierdo en la opción que dice <b>Proxmox Virtual Environment</b>.

[2_0]:https://www.proxmox.com/en/

![img_01](img/img_01.png)

![img_02](img/img_02.png)

Una vez que le dimos click en Proxmox Virtual Environment nos saldrán unas opciones en las cuales podremos encontrar las opciones de ISO Images,  Documentation y Agreements y procederemos a darle click izquierdo en la primera opción que dice <b>ISO Images</b>.

![img_03](img/img_03.png)

Luego de darle click izquierdo en la opción de ISO Images, nos saldrá una opción para descargar el instalador de la versión 7.1 de Proxmox VE y luego procederemos a darle click izquierdo en el botón que dice <b>Download</b> que esta debajo del instalador.

![img_04](img/img_04.png)

Luego de darle click izquierdo en el botón de Downdload, se nos desplegara una ventana en la cual podremos elegir en que carpeta queremos guardar el instalador. En mi caso elegiré una carpeta que cree previamente llamada <b>Proxmox</b> y que está ubicada en la carpeta de descarga de mi ordenador, y acto seguido le date click izquierdo en el botón de <b>Abrir</b> y una vez dentro de la carpeta Proxmox, le daremos click izquierdo en el botón que dice <b>Guardar</b>.

![img_05](img/img_05.png)

![img_06](img/img_06.png)

Una vez hecho esto, se dará inicio al proceso de descarga del instalador.

![img_07](img/img_07.png)

Luego de que se haya descargado por completo nuestro instalador que pesa aproximadamente unos <b>986 MB</b>, ya lo tendríamos listo para seguir con nuestro proceso de instalación.

![img_08](img/img_08.png)

# 2. Máquina virtual

Para este caso vamos a crear nuestra máquina virtual por medio de un programa conocido como [Virtual Box][3_0], el cual es un [Hipervisor][3_1] que nos permitirá correr nuestro sistema Proxmox VE dentro de nuestra computadora por medio de una proceso conocido como virtualización.

[3_0]:https://www.virtualbox.org/wiki/Downloads

[3_1]:https://es.wikipedia.org/wiki/Hipervisorhttps://www.virtualbox.org/wiki/Downloads

## 2.1. Crear una nueva máquina virtual

Lo primero que vamos a hacer es abrir Virtual Box y le daremos click izquierdo en <b>nueva</b> para crear una máquina virtual.

![img_09](img/img_09.png)

## 2.2. Nombre y sistema operativo

Una vez que le dimos en crear se nos desplegara una ventana en la que tendremos unas opción de <b>Nombre</b> en la que le podremos dar un nombre a nuestra máquina virtual, una opción de <b>Carpeta maquina</b> en la que podremos seleccionar la carpeta en la que vamos a crear nuestra máquina virtual, una opción de <b>Tipo</b> en la que podremos definir el tipo de sistema que vamos a instalar y una última opción llamada <b>Versión</b> en la cual podremos definir la versión que tendrá nuestro sistema. 

En mi caso hare las siguientes configuraciones:

* <b>Nombre</b>: Proxmox.

* <b>Carpeta de maquina</b>: C:\User\Docente\VirtualBox VMs.

* <b>Tipo</b>: Linux.

* <b>Versión</b>: Other Linux (64-bit).

Luego de esto procederé a dar un click izquierdo en <b>Next</b>.

![img_10](img/img_10.png)

## 2.3. Tamaño de memoria

Una vez que le dimos click en Next, nos saldrá una ventana en la que le podemos asignar la cantidad de memoria RAM que va a tener nuestra máquina virtual, teniendo en cuanta la cantidad de memoria RAM que tiene nuestro ordenador. En mi caso mi ordenador tiene <b>4GB (4069MB)</b> de memoria RAM y procederé a asignar <b>1500MB</b> de memoria que equivalen a aproximadamente <b>1.5GB</b> de memoria y una vez hecho esto procederé a dar un click izquierdo en <b>Next</b>.

<b>NOTA:</b> Al momento de asignar la memoria RAM hay que tener en cuenta los requisitos mínimos del software y aparte de eso se debe tener en cuenta que si le asignamos más de la mitad de la memoria RAM que hay en nuestro ordenador esto podría ocasionar que nuestro sistema operativo principal se ponga un poco lento.

![img_11](img/img_11.png)

## 2.4. Disco Duro

En esta ventana podremos seleccionar una de las 3 opciones que hay para añadir un [disco duro virtual][4_0], las cuales son:

* No añadir un disco duro virtual.

* Crear un disco duro virtual ahora.

* Usar un archivo de disco duro virtual ya 
existente.

En nuestro caso seleccionaremos la opción de <b>Crear un disco duro virtual ahora</b> y le daremos un click izquierdo en <b>Next</b>.

[4_0]:https://es.wikipedia.org/wiki/Disco_virtual

![img_12](img/img_12.png)

## 2.5. Tipo de archivo de disco duro

En esta ventana nos saldrán 3 opción en las que podremos seleccionar el [tipo de archivo][5_0] que queremos usar en nuestro disco duro virtual, dichas opciones son:

* <b>VDI (VirtualBox Disk Image):</b> es la selección por defecto, es la imagen de un disco duro virtual o el disco lógico asociado con una máquina virtual.

* <b>VHD (Virtual Hard Disk):</b> es la opción a elegir si lo que queremos es crear un disco virtual versátil, que podamos recuperar cualquier archivo en su interior fácilmente. Se podrá utilizar como unidad de lmacenamiento habitual y soporta particiones de todo tipo, como cualquier otro disco duro, además de varios usuarios por cada sistema operativo virtual instalado en él. Se utiliza sobre  todo para Microsoft Virtual PC.

* <b>VMDK (VirtualBox Machine Disk):</b> es el formato típico de VMWare (otro software de virtualización, semejante a VirtualBox). Se escogerá esta opción para contar con plena compatibilidad entre VMWare y VirtualBox y poder pasar Sistemas Operativos virtuales entre ambos softwares sin mayor problema.

En nuestro caso, seleccionaremos la primera opción y le daremos click izquierdo en <b>Next</b>.

[5_0]:https://megazona.com/software/tipos-de-archivo-de-disco-duro-virtual-en-virtualbox

![img_13](img/img_13.png)

## 2.6 Almacenamiento en unidad de disco duro física

En esta ventana nos saldrán las opciones para seleccionar si queremos que nuestro disco duro este <b>reservado dinámicamente </b> es decir que solo se usara espacio en el disco físico a medida que se llena (hasta un máximo tamaño fijo), sin embargo, no se reducirá de nuevo automáticamente cuando el espacio en él se libere, también tendremos la opción de <b>Tamaño fijo</b> que puede tomar más tiempo para su creación en algunos sistemas, pero normalmente es más rápido al usarlo.

En nuestro caso utilizaremos la primera opción puesto que queremos una cantidad específica para nuestro Sistema Operativo y luego procederemos a dar un click izquierdo en <b>Next</b>.

![img_14](img/img_14.png)

## 2.7 Ubicación del archivo y tamaño

En este paso ya prácticamente tendremos configurada la parte de almacenamiento de nuestro disco, ahora solamente faltara asignarle la cantidad de almacenamiento que queremos que tenga nuestro disco duro y posterior a ello le asignaremos la ubicación donde este se creara.

En nuestro caso le asignaremos <b>250GB</b> de memoria y la ubicaremos en la carpeta <b>C:\Users\Docente\VirtualBox VMs\Proxmox\Proxmox.vdi</b> y posterior a ello le daremos click izquierdo en <b>Crear</b>.

![img_15](img/img_15.png)

De esta manera ya tendríamos creada nuestra máquina virtual.

![img_16](img/img_16.png)

# 3. Configuraciones

Una vez creada nuestra máquina virtual, accedemos a las configuraciones de la misma para poder cargar la imagen ISO que descargamos inicialmente; a continuación, mostraremos el paso a paso de la carga de la imagen ISO.

## 3.1. Almacenamiento

Una vez creada nuestra máquina virtual nos vamos a ubicar en el apartado de almacenamiento y le vamos a dar click izquierdo sobre este.

![img_17](img/img_17.png)

Una vez que le hemos dado click a la opción de almacenamiento se nos desplegara una ventana en la que tendremos la opción de <b>Controlador IDE</b> en la que podremos crear una sea unidad óptica o disco duro, también debajo de esta tendremos el disco duro que creamos anteriormente y tendremos una unidad óptica que dice <b>vacío</b>.

En nuestro caso seleccionaremos la opción de vacío y le un daremos click izquierdo.

![img_18](img/img_18.png)

Una vez que le hemos dado click nos aparecerá una opción en forma de disco en la que podremos seleccionar nuestra imagen ISO, dicho esto procederemos a dar un click izquierdo sobre esta para que así se nos desplieguen las demás opciones, las cuales son <b>Seleccionar/crear un disco óptico virtual</b> y <b>Seleccionar un archivo de disco</b>.

En nuestro caso le daremos un click izquierdo en la segunda opción.

![img_19](img/img_19.png)

![img_20](img/img_20.png)

Luego de que le demos en la segunda opción se nos desplegara una ventana en la que podremos buscar y seleccionar la <b>imagen ISO</b> que hemos descargado anteriormente.

En nuestro caso, seleccionaremos la imagen ISO llamada <b>proxmox-ve-7.1-2.iso</b> y luego daremos un click izquierdo en <b>Abrir</b>.

![img_21](img/img_21.png)

Por último, una vez que hemos seleccionado nuestra imagen ISO, le vamos a dar un click en <b>Aceptar</b> para que se guarden los cambios.

![img_22](img/img_22.png)

y así de esta manera ya tendríamos cargada nuestra imagen ISO.

![img_23](img/img_23.png)

## 3.2. Pantalla

La siguiente configuración que vamos a realizar va a ser la de seleccionar la opción de <b>Habilitar aceleración 3D</b>, la cual podremos encontrar al dar un clic izquierdo en el apartado de <b>Pantalla</b> y acto seguido nos ubicaremos en <b>Aceleración</b> y luego procederemos a habilitar la opción de <b>aceleración 3D</b>.

Una vez que hemos habilitado la opción le daremos un click izquierdo en <b>Aceptar</b> para que se guarden los cambios.

![img_24](img/img_24.png)

![img_25](img/img_25.png)

y así de esta manera tendremos habilitada la opción de aceleración 3D.

![img_26](img/img_26.png)

## 3.3. Red

Para finalizar con las configuraciones, lo siguiente que tendremos que configurar es la opción de adaptador puente, en la cual podremos seleccionar donde va a estar conectada nuestra máquina virtual, esta opción la podremos encontrar al dar click izquierdo en el apartado de <b>Red</b> y luego de esto nos ubicaremos en la opción de <b>Conectado a</b> para acto seguido seleccionar en nuestro caso la opción de <b>Adaptador sólo – anfitrión</b>.

![img_27](img/img_27.png)

![img_28](img/img_28.png)

![img_29](img/img_29.png)

Por último, una vez que hemos seleccionado el adaptador, procederemos a dar un click izquierdo en <b>Aceptar</b> para que se guarden los cambios.

![img_30](img/img_30.png)

y así de esta manera tendremos seleccionado nuestro adaptador de red.

![img_31](img/img_31.png)

# 4. Ejecutar e instalar

Para iniciar nuestra máquina virtual, nos ubicaremos en la opción que dice <b>Iniciar</b> y luego procederemos a dar click izquierdo sobre este para así poder continuar con nuestro proceso de instalación.

![img_32](img/img_32.png)

## 4.1. Proxmox

Una vez que hemos iniciado nuestra máquina virtual, nos aparecerá una ventana que dirá <b>Welcome to Proxmox Virtual Environment</b> donde en esta tendremos las opciones de:

* <b>Install Proxmox VE</b>.

* <b>Install Proxmox VE (Debug mode)</b>.

* <b>Rescue Boot</b>.

* <b>Test memory (Legacy BIOS)</b>.

En la que nosotros procederemos a darle en nuestro caso un click izquierdo en la primera opción.

![img_33](img/img_33.png)

Luego de que le hemos dado click en la primera opción nos saldrá un mensaje que dice <b>No support for KVM virtualization detected</b> y procederemos a darle un click izquierdo en <b>Ok</b>.

![img_34](img/img_34.png)

## 4.2. END USER LICENSE AGREEMENT (EULA)

Luego de darle click en ok, nos aparecerá una ventana en la que podremos leer la licencia del sistema para acto seguido darle click izquierdo en <b>I agree</b> para asi aceptar sus términos y condiciones.

![img_35](img/img_35.png)

## 4.3. Proxmox Virtual Environment (PVE)
Una vez que le dimos click en i agree, nos aparecerá una ventana en la que podremos seleccionar el disco duro virtual en el que vamos a instalar nuestro sistema operativo, aparte de este, nos aparecerá un botón de <b>Opcións</b> en el cual al darle click izquierdo nos saldrán las opciones para crear de forma manual las particiones que va a tener nuestro disco duro virtual.

![img_36](img/img_36.png)

## 4.3.1. Harddisk options
Luego de que le dimos click en opcions, se nos desplegara una ventana en la que tendremos unas opciones a las cuales le podremos asignar una cantidad de memoria, dichas opciones son:

* <b>hdsize</b>.
* <b>swapsize</b>.
* <b>maxroot</b>.
* <b>minfree</b>.
* <b>maxvz</b>.

Para nuestro caso, en <b>hdsize</b> lo vamos a dejar en <b>250GB</b>, en <b>swapsize</b> le vamos a asignar <b>4.5GB</b>, en <b>maxroot</b> le vamos a asignar <b>60GB</b>, a <b>minfree</b> le vamos a asignar <b>35.5GB</b> y a <b>maxvz</b> le vamos a asignar <b>150GB</b>, seguido de esto procederemos a dar click izquierdo en <b>Ok</b> para que se guarden los cambios.

<b>NOTA: </b> Al momento de hacer las asignaciones se debe tener en cuenta que la suma de las cuatro ultimas opciones tiene que dar igual que la memoria asignada en <b>hdsize</b>.

![img_37](img/img_37.png)

Acto seguido, una vez que le hemos dado click en ok, procederemos a dar click izquierdo en <b>Next</b>

![img_38](img/img_38.png)

