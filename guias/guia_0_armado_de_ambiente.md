# Práctica 0: Armado de ambiente

## Objetivos: 
 * Tener un ambiente de Kali disponible en la máquina de los alumnos
 * Refrescar conocimientos de uso de linux (comandos de administración)

## Referencias utiles:
 * [Vagrant](https://developer.hashicorp.com/vagrant/intro)
 * [Kali](https://www.kali.org/docs/introduction/what-is-kali-linux/)
 * [Comandos basicos de Linux](https://kinsta.com/blog/linux-commands/)

## Ejercicios:

1. Instalar VirtualBox: https://www.virtualbox.org/wiki/Downloads
    1. Instalar version 7.0 (7.0.14 en Febrero 2024)
1. Instalar vagrant: https://www.vagrantup.com/ 
    1. Instalar version 2.4 (2.4.1 en Febrero 2024)
1. Clonar el repositorio de git donde están las definiciones de las máquinas virtuales: https://github.com/pablorubinstein/utdt-introsec 
1. Instalar la imagen de Kali usando vagrant
    ```
    cd vagrant
    cd kali
    vagrant up
    ```
1. Loguearse a la vm (a través de la GUI de VirtualBox) con el usuario `vagrant/vagrant` y obtener la siguiente información:
    1. La versión del kernel de linux que está utilizando:
    `uname -a`
    1. La lista de usuarios logueados:
    `who`
    1. La lista de procesos corriendo:
    `ps -efa`
    1. La lista de servicios corriendo:
    `netstat -anp | grep “LISTEN ”`
    1. La lista de las interfaces de red y sus configuraciones:
    `ip address`
    `ifconfig -a`
1. Desde la máquina física, loguearse por SSH a la vm con Kali
    1. Chequear la lista de usuarios logueados
    1. Notar la diferencia en las terminales de cada usuario
1. Loguearse via SSH desde la misma sesión:
    `ssh localhost`
1. Loguearse via SSH usando vagrant ssh:
    `vagrant ssh`
1. El banner de login se encuentra en `/etc/motd`
    1. Mostrar el contenido del archivo por pantalla:
    `cat /etc/motd`
    1. Contar la cantidad de líneas del archivo:
    `wc -l /etc/motd`
    1. Determinar si la cadena "kali" está en el archivo:
    `grep “kali” /etc/motd`
    1. Listar los permisos del archivo:
    `ls -l /etc/motd`
    1. Modificar el banner de login (/etc/motd)
    1. Modificarlo para agregarle un texto propio. Pueden usar el editor de texto desde la GUI (desde línea de comando pueden usar nano o vi)

    *NOTA:* por que no puede modificarlo? pista: `chmod`
1. Listar los procesos como el usuario kali y como el usuario root:
  `netstat -anp | grep “LISTEN “`
    1. ¿Qué diferencias encuentra en ambos casos?
    1. ¿Cómo se llama el servicio que se encuentra escuchando en el port 22?
    1. ¿Puede localizar el binario del servicio? pista: `type`/`which`
1. Levantar el servicio `postgresql` y configurarlo para que levante automáticamente en cada reinicio:
    ```
    sudo service postgresql start
    sudo update-rc.d postgresql enable
    ```
1. Otros comandos útiles:
   `man [comando]`
1. Usar vagrant scp para copiar archivos hacia/desde la vm
    1. Subir un archivo de la máquina física a `/tmp` en la vm
    1. Bajar el file `/etc/passwd` de la vm a la máquina física

Instalar las otras vms:
 * Ubuntu 14 vulnerable
 * Ubuntu 14 fsperm ssh
 * Windows 2008 vulnerable

*NOTA:* no es posible loguearse usando vagrant ssh a la vm “Ubuntu 14 fsperm ssh”, pero esto es por diseño y está relacionado con el tipo de ejercicios que vamos a realizar
