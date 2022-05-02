# SistemasOperativosII-P3
Repositorio de la práctica 3 de Sistemas Operativos II, la cual describe cómo compilar una versión del kernel de Linux.

## Paso 1 ¿Cómo hacer un respaldo de una máquina virtual? y ¿cómo levantar ese respaldo?

Antes de compilar el kernel, se realizará un respaldo en caso de que surja alguna falla. Para esto en el VirtualBox le daremos click derecho a la máquina virtual, y le daremos click a la opción que dice clonar. Marcaremos los dos checkboxs, y guardaremos el clon donde queramos. Le damos siguiente, y verificamos que esté marcada la opción de full clone. Le damos a clonar. Una vez hecho esto debería aparecer así el respaldo:

![Imagen1](Capture.PNG)

Captura del respaldo corriendo: 

![Imagen1](Capture2.PNG)

## Paso 2 Explicar la nomenclatura del kernel.

La nomenclatura moderna para la versión del kernal de Linux consiste en:
major#.minor#[.patchlevel][-ExtraVersion]
donde patchlevel y extraversion son números opcionales.

El major number es el número principal de la versión.

El minor number es el número jerárquicamente debajo del número principal, el cual representa cambios hechos a la versión principal actual. 

El patchlevel, también llamado ABI o revisión, es aplicado a una versión estable del kernel cuando se necesitan hacer pequeñas actualizaciones de bugs o seguridad.

El extraversion es típicamente utilizado por los distribuidores de los kernels para mantener un registro de sus cambios internos. Es utilizado para manejar múltiples variantes de la misma versión de un kernel.

## Paso 3 Investigar y enlistar los paquetes requeridos para la compilación y ¿cómo instalarlos desde terminal?.

Antes de realizar la compilación del kernel es necesaria la instalación de paquetes a través de la terminal, estos paquetes son: 

-git
-fakeroot
-build-essential
-ncurses-dev
-xz-utils
-libssl-dev
-bc
-flex
-libelf-dev
-bison

Para la instalación de estos paquetes se ocupa el comando:

```
sudo apt-get install git fakeroot build-essential ncurses-dev xz-utils libssl-dev bc flex libelf-dev bison
```

Capturas de la instalación de los paquetes:

![Imagen1](6.png)

![Imagen1](7.png)

## Paso 4 ¿Cómo descargar una versión de kernel desde terminal?

Para realizar este paso se utiliza el comando wget, y se le pasa el link de descarga de la versión de kernal deseada:

```
wget https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-5.17.5.tar.xz
```

![Imagen1](2.png)

Captura de la descarga del kernel: 

![Imagen1](3.png)

Captura de la descarga finalizada:

![Imagen1](4.png)

## Paso 5 ¿Cómo extraer el código comprimido del kernel desde terminal?

Para descomprimir el código se utiliza el comando tar, el cual nos ayuda a comprimir y descomprimir archivos en linux:
```
tar xvf linux-5.17.5.tar.xz
```
Captura en terminal del comando: 
![Imagen1](5.png)

## Paso 6 ¿Cómo configurar el kernel?

Primero hay que moverse a la carpeta descomprimida del kernel:

```
cd linux-5.17.5
```

![Imagen1](8.png)

Después es necesario realizar una copia del archivo de configuración del kernel instalado actualmente para modificarlo con la nueva versión.
```
cp -v /boot/config-$(uname -r) .config
```
![Imagen1](9.png)

Por último, se realiza el make de menuconfig.

```
make menuconfig
```

![Imagen1](10.png)

El make construirá el menú de configuración; al terminar se abrirá la siguiente interfaz la cual sirve para modificar los parámetros del kernel. Hay que tener cuidado pues modificar algo de forma incorrecta puede resultar en una compilación errónea del kernel.

![Imagen1](11.png)

Al terminar de configurar los parámetros que se deseen, hay que ir a la opción de guardar y dejar el mismo nombre que nos indica.

![Imagen1](12.png)

## Paso 7 ¿Cómo compilar el código del kernel?

El siguiente paso es compilar el kernel, el cual puede llegar a tardar varias horas dependiendo de la velocidad del CPU de la computadora. También es indispensable tener mínimo 40 GB de espacio libre en la máquina virtual. 
Para realizar la compilación se ejecuta el make estando en la carpeta del kernel:

```
make 
```
Es posible realizar la compilación con paralelismo, utilizando make con el modificador -j y después el número de procesos que queremos que se realicen en paralelo.

```
make -j 4
```
Así el comando va a realizar 4 procesos en paralelo.
Este número no debe superar el número de núcleos que se tenga en el CPU, pues puede salir contraproducente para la velocidad de la compilación.

![Imagen1](13.png)

Captura de la compilación en proceso:

![Imagen1](14.png)

Captura de la compilación terminada.

![Imagen1](16.png)

## Paso 8 ¿Cómo instalar módulos?

El siguiente paso es terminar de compilar e instalar módulos necesarios para la instalación final del kernel con el siguiente comando: 

```
sudo make modules_install
```
![Imagen1](17.png)

## Paso 9 ¿Cómo instalar el kernel?


