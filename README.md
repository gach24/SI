# SISTEMAS INFORMÁTICOS

## COMANDOS

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
cd ..
cd /tmp/
cd ~
```

### HISTORY

- Sintaxis:
history [opcion ...]

- Muestra el historial de comandos introducidos por el usuario

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
uname -r
uname -a
uname -n
uname -m
```

## CAT

- Muestra el contenido por pantalla del fichero

- Sintaxis:
cat [opcion ...]

- Opciones:
  - -n => Muestra los números de línea
  - -b => Numerá las líneas menos las vacías

- Ejemplos:

```sh
cat numeros.txt
cat -n numeros.txt
cat -b numeros.txt
```

## MAN

- Muestra la ayuda de comandos y ficheros:
  - Muestra el propósito de comando
  - Sintaxis
  - Opciones

- Sintaxis:
man [seccion] termino

- Las páginas del man están almacendas en un directorio `/usr/share/man`

- Cuando instalamos un programa instala también las páginas de ayuda dentro de `/usr/share/man/manX`, donde la X corresponde a las distantes secciones del man

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

## NL

- Numera las líneas, es exactamente igual que `cat -n`

- Sintaxis:
nl [opciones] fichero

- Opciones:
  - -ba -> Numera las líneas en blanco

- Ejemplos:

```bash
seq 1 10 > numeros.txt # Para generar el fichero
nl numeros.txt # Numéra las líneas menos líneas en blanco
nl -ba numeros.txt # Numera todo
```

## HEAD

- Muestra las líneas iniciales del fichero

- Sintaxis:
head [opciones] fichero

- Opciones:
  - -n => Indica el número de líneas a mostrar

- Ejemplos

```bash
head -n 10 
```

## TAIL

- Muestra las líneas FINALES del fichero

- Tanto el head como el tail permiten varios parametros

- Sintaxis:
tail [opciones] fichero

- Opciones:
  - -n => Indica el número de líneas a mostrar
  - -f => No cierra el fichero y espera a mostrar las núevas líneas introducidas

- Ejemplos

```bash
tail -n 10 numeros.txt
tail -f numeros.txt
```

## WC

- Cuenta líneas, palabras y caractéres

- Sintaxis: 
wc [opciones ...] ficheros

- Opciones:
  - -n => Número de líneas
  - -w => Número de palabras
  - -m => Número de caractéres

- Ejemplos:

```bash
wc numeros.txt
wc -l numeros.txt
wc -wnumeros.txt
wc -m numeros.txt
```

## SORT

- Ordena las líneas del fichero

- Sintaxis:
sort [opciones...] ficheros

- Opciones:
  - -k numero => Número de columna a cordenar
  - -t separador => Indica el separador de columnas
  - -n => Realiza la ordenación númerica (por defecto es alfabética)
  - -r => Ordena en orden inverso
  - -f => Ignora entre mayúsculas y minúsculas
  
- Ejemplos:

```bash
sort -r nombres.txt
sort -k 2 -t' ' nombres.txt
sort -n nombres.txt
```

## UNIQ

- Sintaxis: uniq [opciones] [ficheros]

- Quita las líneas repetidas

- Opciones:
  - -c => Muestra el número de repeticiones
  - -d => Muestra solo las líneas repetidas
  - -u => Muestra solo las líneas no repetidas
- Ejemplos:

```sh
uniq numeros.txt # No quita las repeticiones discontinuas
sort numeros.txt | uniq # Quita las repeticiones aun siendo discontinuas
uniq -c numeros.txt 

```

## CUT

- Sintaxis: cut [opciones] [fichero]

- Cut extrae columnas de un fichero

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

## GREP

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



















