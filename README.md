# SistemasOperativosII-P3
Repositorio de la práctica 3 de Sistemas Operativos II, la cual consiste en cómo compilar una versión del kernel de Linux.

## Paso 1 ¿Cómo hacer un respaldo de una máquina virtual? y ¿cómo levantar ese respaldo?

Antes de compilar el kernel, se realizará un respaldo en caso de que surja alguna falla. Para esto en el VirtualBox le daremos click derecho a la máquina virtual, y le daremos click a la opción que dice clonar. Marcaremos los dos checkboxs, y guardaremos el clon donde queramos. Le damos siguiente, y verificamos que esté marcada la opción de full clone. Le damos a clonar. Una vez hecho esto debería aparecer así el respaldo:

![Imagen1](Capture.PNG)

Captura del respaldo corriendo: 

![Imagen1](Capture2.PNG)

## Paso2 Explicar la nomenclatura del kernel.

2. La nomenclatura moderna para la versión del kernal de Linux consiste en:
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

![Imagen1](6.png)

