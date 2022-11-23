# SISTEMAS INFORMÁTICOS

## COMANDOS

### PWD

- Sintaxis: pwd

- Viene de "Print Work Directory" y sirve para saber el directorio donde estamos situados
- El prompt suele mostrar esa información, pero utiliza el símbolo "~" cuando nos encontramos en nuestro directorio personal

- Ejemplos

```sh
pwd
```

### WHOAMI

- Sintaxis:
whoami

- Muestra el usuario de la sesión

- Ejempos

```sh
whoami
```

### HOSTNAME

- Sintaxis:

hostname

- Muestra el nombre del equipo

- Ejempos

```sh
hostname
```

### CD

- Sintaxis:
cd [directorio]

- (Change directory) Permite cambiar de directorio

- Ejemplo:

```sh
cd /home
cd .. # Para ir al directorio padre
cd /tmp/
cd ~ # Para ir al directorio personal
```

### HISTORY

- Sintaxis:
history [opcion ...]

- Muestra el historial de comandos introducidos por el usuario
- El fichero `.bash_history` contiene el listado de todos los comandos ejecutados en sesiones anteriores, este fichero se encuentra en cada uno de los directorios personales de los usuarios
- Podemos mostrar el contenido del fichero con

```sh
cat .bash_history
```

- Cuando nosotros cerramos la sesión se almacenan en este fichero todos los comandos ejecutados durante la sesión
- El comando `history` muestra la información del fichero `.bash_history` y los comandos ejecutados durante la sesión, todos los comandos mostrados van precedidos de un número.
Podemos ejecutar el comando del historial mediante ese número como se muestra a continuación

```sh
!5 # Ejecuta el comando número 5 del listado
```

- Opciones:
  - -c => Borra el historial
  - -w => Guarda el historial de comandos de sesión en el fichero

- Ejemplos

```sh
history
history -c # Borra el historial
history -w # Guarda el historial de la sesión
```

### UNAME

- Sintaxis:
uname [opcion ...]

- Muestra la información sobre nuestro linux

- Opciones:
  - -a => Muestra toda la información del sistema
  - -r => Muestra la versión de nuestro núcleo linux
  - -n => Muestra el nombre de la máquina
  - -m => Muestra la arquitectura de la máquina

- Ejemplos:

```sh
uname
uname -r # Versión del núcleo
uname -a # Toda la información
uname -n # Nombre de la máquina
uname -m # Arquitectura de la máquina
```

### MAN

- Muestra la ayuda de comandos y ficheros:
  - Muestra el propósito de comando
  - Sintaxis
  - Opciones

- Sintaxis:
man [seccion] termino

- Las páginas del man están almacendas en un directorio `/usr/share/man`

- Cuando instalamos un programa instala también las páginas de ayuda dentro de `/usr/share/man/manX`, donde la X corresponde a las distantes secciones del man

- El término buscado puede ser:
  - Comandos. De cada comando muestra:
    - Propósito del comando
    - Sintaxis
    - Opciones
  - Ficheros (Mostrará la estructura del fichero)
  - Ficheros especiales.


- Secciones:
  - 1) Comandos generales Ej: ls, cd, ...
  - 2) Llamadas al sistema
  - 3) Biblioteca de funciones
  - 4) Ficheros especiales Ej: /dev/null
  - 5) Ficheros de configuración Ej: /etc/passwd
  - 6) Juegos y salvapantallas
  - 7) Miscelania
  - 8) Comandos de administración del sistema (Trata como crear particiones en disco, reinicios, ...)

- Ejemplos:

```bash
man ls
man 5 passwd # Mostraría información sobre el fichero passwd
man passwd # Mostraría información sobre el comando passwd
```

### CAT

- Muestra el contenido por pantalla del fichero

- Sintaxis: cat [opciones] fichero [ficheros]

- Opciones:
  - -n => Muestra los números de línea
  - -b => Numerá las líneas menos las vacías

- Ejemplos:

```sh
cat numeros.txt
cat -n numeros.txt
cat -b numeros.txt
```

- El comando `tac` muestra el contenido del fichero al revés

### NL

- Sintaxis:
nl [opciones] fichero [ficheros]

- Numera las líneas, es exactamente igual que `cat -n`

- Opciones:
  - -ba -> Numera las líneas en blanco

- Ejemplos:

```bash
seq 1 10 > numeros.txt # Para generar el fichero
nl numeros.txt # Numéra las líneas menos líneas en blanco
nl -ba numeros.txt # Numera todo
```

### HEAD

- Muestra las líneas iniciales del fichero (Por defecto 10 líneas)

- Sintaxis: head [opciones] fichero [ficheros]

- Opciones:
  - -n => Indica el número de líneas a mostrar

- Ejemplos:

```bash
head numeros.txt
head -n 10 nombres.txt
```

### TAIL

- Sintaxis: tail [opciones] fichero [ficheros]

- Muestra las líneas FINALES del fichero

- Opciones:
  - -n => Indica el número de líneas a mostrar
  - -f => No cierra el fichero y espera a mostrar las núevas líneas introducidas

- Ejemplos

```bash
tail -n 10 numeros.txt
tail -f numeros.txt
```

### WC

- Cuenta líneas, palabras y caractéres

- Sintaxis: wc [opciones ...] fichero [ficheros]

- Opciones:
  - -l => Muestra solamente el número de líneas
  - -w => Muestra solamente el número de palabras
  - -m => Muestra solamente el número de caractéres

- Ejemplos:

```sh
wc numeros.txt
wc -l numeros.txt
wc -wnumeros.txt
wc -m numeros.txt
```

### SORT

- Sintaxis: sort [opciones...] fichero [ficheros]

- Ordena las líneas del fichero
- Si especificamos más de un fichero ordena todo, no cada fichero por separado

- Opciones:
  - -k numero => Número de columna a cordenar
  - -t separador => Indica el separador de columnas
  - -n => Realiza la ordenación númerica (por defecto es alfabética)
  - -r => Ordena en orden inverso
  - -f => Ignora entre mayúsculas y minúsculas
  
- Ejemplos:

```sh
sort -r nombres.txt
sort -k 2 -t' ' nombres.txt
sort -n nombres.txt
```

### UNIQ

- Sintaxis: uniq [opciones] fichero

- Muesta el contenido de un fichero quitando las líneas repetidas.
- Para quitar las líneas repetidas dichas líneas deben estar contiguas (podemos apoyarnos en el comando `sort` para esta labor)

- Opciones:
  - -c => Muestra el número de repeticiones
  - -d => Muestra solo las líneas repetidas
  - -u => Muestra solo las líneas no repetidas
- Ejemplos:

```sh
uniq numeros.txt # No quita las repeticiones discontinuas
sort numeros.txt | uniq # Quita las repeticiones aún siendo discontinuas
uniq -c numeros.txt 
```

### CUT

- Sintaxis: cut [opciones] fichero

- Cut extrae columnas de un fichero,es decir, corta un fichero por columnas

- Opciones:
  - -f numeros => Determina las columnas que quiero extraer, siendo números los números de columna separados por comas
  - -d separador => Indica el separador de columnas
  - -c numeros => Determina los caracteres o secuencia de caracteres a extraer

- Ejemplos:

```sh
cut -f2,3 -d':' nombres.txt
cut -f2-5 -d':' nombres.txt
cut -c 5-10 nombres.txt
```

### SPLIT

- Sintaxis: split [opciones] fichero [prefijo]

- Divide un fichero en ficheros más pequeños, enta división puede ser por líneas o por tamaño
- El comando split nombrará los ficheros resultado de la división como xaa, xab, xac, ...
- Se puede indicar un prefijo con el que nombrará a los ficheros

- Opciones:
  - -l numero => Indica el número de líneas por las que realizará la división
  - -b tamaño => Indica el tamaño (B,K,M,G, ...) por el que realizará la división

- Ejemplos:

```sh
split -l 20 numeros.txt # Cada fichero resultado de la división tendrá 20 líneas
split -b 10K nombres.txt # Cada fichero resultado de la división tendrá 10K
split -l 10 numeros.txt num # Los ficheros se nombrarán como numaa, numab, numac, ...
```

- Se pueden unir los ficheros mediante el comando `cat`

```sh
cat x*
```

### COMANDO JOIN

- Sintaxis: join [opciones] fichero1 fichero2

- Une dos ficheros con un campo en común

- Opciones
  - -t => Delimitador de los campos del fichero
  - -1 num => Posición del campo en común en el primer fichero
  - -2 num => Posición del campo en común en el segundo fichero

### GREP

- Sintaxis: grep patron [ficheros]

- Muestra las líneas en donde se encuentra el patrón

- Opciones:
  - -i => No distingue entre mayúsculas y minúsculas
  - -c => Cuenta el número de líneas donde aparece el patrón
  - -v => Muestra las líneas donde NO encuentra el patrón
  - -A numero => Muestra el número de líneas indicado después de la coincidencia del patrón
  - -B numero => Muestra el número de líneas indicado antes de la coincidencia del patrón
  - -H => Incluye el nombre del fichero en el resultado de la búsqueda
  - -h => Quita el nombre del fichero en el resultado de la búsqueda

## LS

- Sintaxis: ls [opciones] [ficheros/patron]

- Listar el contenido de uno o varios directorios

- Opciones
  - -a => Muestra los archivos ocultos / o que comienzan por punto
  - -l => Muestra de cada archivo sus propiedades
  - -h => Muestra el formato leible para el usuario la cantidad de bytes
  - -R => Lista recursivo
  - -t => Lista ordenadamente por fecha de modificación
  - -S => Lista ordenadamente por tamaño
  - -r => Invierte el orden

## MKDIR

- Sintaxis: mkdir [opciones] <directorios>

- Crea directorio o directorios

- Opciones
  - -p => Crea directorios anidados
  - -v => Muestra una traza de las operaciones

## RMDIR

- Sistaxis: rmdir <directorios>

- Borrar directorios SOLO VACÍOS

## RM

- Sistaxis: rm [opciones] [ficheros|directorios/patron]

- Borra ficheros y/o directorios

- Opciones
  - -r => Borra recursivamente
  - -i => Pregunta antes de borrar
  - -f => Fuerza eliminación

## STAT

- Sintaxis: stat <ficheros>

- Muetra información sobre el fichero
  

## FIND

- Sintaxis: find <path> [patron] [opciones]

- Busca ficheros o directorios
























