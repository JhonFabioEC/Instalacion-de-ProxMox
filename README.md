# ¿Que es Proxmox VE?

Proxmox Virtual Environment o mejor conocido como [Proxmox VE][1_0] o PVE, es un servidor de [código abierto][1_1] que nos permite virtualizar y gestionar otros sistemas operativos, este servidor fue desarrollado por medio de una distribución de [GNU/Linux][1_2] basada en [Debian][1_3], la cual usa también un kernel modificado de [Ubuntu][1_4] LTS para así poder ejecutar varias [máquinas virtuales][1_5] y [contenedores][1_6] en un solo servidor, Proxmox VE también incluye una consola web y  herramientas de líneas de comandos qué garantizan una accesibilidad simple y rápida.

[1_0]:https://es.wikipedia.org/wiki/Proxmox_Virtual_Environment

[1_1]:https://es.wikipedia.org/wiki/Software_de_c%C3%B3digo_abierto

[1_2]:https://es.wikipedia.org/wiki/Distribuci%C3%B3n_Linux

[1_3]:https://es.wikipedia.org/wiki/Debian_GNU/Linux

[1_4]:https://es.wikipedia.org/wiki/Ubuntu

[1_5]:https://es.wikipedia.org/wiki/M%C3%A1quina_virtual

[1_6]:https://es.wikipedia.org/wiki/Virtualizaci%C3%B3n_a_nivel_de_sistema_operativo

## Requisitos Mínimo

* Intel VT / AMD-V CPU capaz / Mainboard (para soporte KVM completa de virtualización).

* CPU x64 bits (EMT64 Intel o AMD64).

* Mínimo 1 GB de RAM.

* Unidad de disco duro.

* Una NIC.

## Requisitos recomendados

Desde la página oficial de Proxmox la recomendación es la siguiente:

* Dual o Quad Socket Server (Quad / Six / Hexa Core CPUs’).

* CPU: 64 bits (EMT64 Intel o AMD64).

* Intel VT / AMD-V CPU capaz / Mainboard (para soporte KVM completa de virtualización).

* 8 GB de RAM es bueno, más es mejor (grab tanto como sea posible).

* Hardware RAID con caché pilas protegido contra escritura (BBU) o la protección de flash.

* Discos duros rápidos y mejores resultados con 15k rpm SAS, RAID 10.

* Dos Gbit NIC (para la vinculación), NIC’s adicionales dependiendo de la tecnología de almacenamiento preferido y configuración del clúster.

* Hardware de Esgrima (sólo es necesario para HA).

## 1. Descarga de la imagen ISO
Para dar inicio a este tutorial, primero tendremos que descargar el servidor [Proxmox VE][2_0] desde su página oficial.

**1.1.** Una ven estamos en la página nos vamos a ubicar en el apartado de ***Downloads*** para acto seguido dar un clic izquierdo en la opción que dice ***Proxmox Virtual Environment***.

[2_0]:https://www.proxmox.com/en/

![img_01](img/img_01.png)

![img_02](img/img_02.png)

**1.2.** Una vez que le dimos clic en Proxmox Virtual Environment nos saldrán unas opciones en las cuales podremos encontrar las opciones de ISO Images,  Documentation y Agreements y procederemos a darle clic izquierdo en la primera opción que dice ***ISO Images***.

![img_03](img/img_03.png)

**1.3.** Luego de darle clic izquierdo en la opción de ISO Images, nos saldrá una opción para descargar el instalador de la versión 7.1 de Proxmox VE y luego procederemos a darle clic izquierdo en el botón que dice ***Download*** que esta debajo del instalador.

![img_04](img/img_04.png)

**1.4.** Luego de darle clic izquierdo en el botón de Downdload, se nos desplegara una ventana en la cual podremos elegir en que carpeta queremos guardar el instalador. En mi caso elegiré una carpeta que cree previamente llamada ***Proxmox*** y que está ubicada en la carpeta de descarga de mi ordenador, y acto seguido le date clic izquierdo en el botón de ***Abrir*** y una vez dentro de la carpeta Proxmox, le daremos clic izquierdo en el botón que dice ***Guardar***.

![img_05](img/img_05.png)

![img_06](img/img_06.png)

**1.5.** Una vez hecho esto, se dará inicio al proceso de descarga del instalador.

![img_07](img/img_07.png)

**1.6.** Luego de que se haya descargado por completo nuestro instalador que pesa aproximadamente unos ***986 MB***, ya lo tendríamos listo para seguir con nuestro proceso de instalación.

![img_08](img/img_08.png)

## Creación de la máquina virtual