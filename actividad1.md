En esta primera actividad respecto al FTP vamos a aprender a instalar nuestro propio servidor y además aprender a discriminar sitios FTP tanto por IP como por puertos.

Antes de empezar vamos a necesitar un máquina virtual Ubuntu 18.04 e instalar Webmin y FileZilla.

*En este [enlace](https://clouding.io/kb/como-instalar-webmin-en-ubuntu-18-04/) tienes una guía sobre como instalar Webmin paso a paso.*

**1.** En este primera paso vamos a aprender a instalar nuestro servidor que en este caso instalaremos el **PROFTPD server**, tendremos que acceder al Webmin, que con ingresar un usuario con permisos de sudo nos permite entrar, a continuación tenemos que acceder al apartado de Webmin que se llama **Un-used Modules**.

![imagen1](/imagenes/Captura1.PNG)

Y obviamente buscar ProFTPD Server que el servidor que queremos instalar. Cuando lo encontremos la primera opción que nos aparece es la siguiente:

![imagen2](/imagenes/Captura2.PNG)

Le damos a **Install Now** y nos aparecerá una nueva pantalla:

![imagen3](/imagenes/Captura3.PNG)

Esta pantalla nos va a decir que paquetes son los que va instalar junto al servidor, simplemente volvemos a darle a **Install Now**.

Después nos aparecerán las típicas líneas de texto que nos aparecerían si usáramos el comando *apt-get*, una vez instalado le damos a **Return to ProFTPD Server**.

Cuando volvamos veremos que efectivamente ya podemos configurar nuestro servidor. 

![imagen4](/imagenes/Captura4.PNG)

El siguiente paso será aprender a discriminar los distintos sitios FTP.

***Discrimación sitios FTP por IP solamente***

Tenemos que ir al apartado que se llama **Virtual Servers** y donde pone Create virtual server es donde le asignaremos la IP al servidor:

![imagen5](/imagenes/Captura5.PNG)

En **Address** pondremos la dirección IP que queramos dentro de nuestro rango de IPs claro, el FTP port lo veremos luego para la discriminación por puerto, y la última de las opcines que nos aparecen es **Server name**, el nombre realmente puede ser el que vosotros queráis.

Cuando clickemos en Create se nos abrirá una pestaña muy parecida a la de la configuración general del servidor, la única diferencia es que aparece una opción llamada **Configure Virtual Server** que simplemente tiene las opciones de antes para cambiarle la dirección, nombre, puerto o incluso eliminar el servidor.

*Importante volver al primer menú de configuración general del servidor y darle a aplicar changes si no no funcionará.*

Ahora vamos a probar a conectarnos a través de FileZilla:

![imagen6](/imagenes/Captura6.PNG)

En el apartado de servidor ponemos la dirección del servidor, nombre de usuario el usuario de nuestra máquina virtual ya que los usuarios de la máquina donde instalemos el servidor por defecto ya se pueden conectar al servidor, contraseña la contraseña del usuario y el puerto en este caso lo dejaremos en blanco, pero antes de conectarnos nos mandará un mensaje diciendo que por defecto se va a conectar por el puerto 21.
Y una vez pulsemos la tecla "Intro" veremos que efectivamente se ha conectado.

![imagen7](/imagenes/Captura7.PNG)

***Discriminación sitios FTP por puerto***

Ya hemos hablado antes de la discriminación por puerto pero ahora vamos a ponerla en práctica, lo primero que vamos a hacer es crear otro servidor virtual igual que antes, le pondremos la misma IP, el mismo nombre, pero ahora activaremos la opción de FTP port como se ve en este ejemplo:

![imagen8](/imagenes/Captura8.PNG)

Yo en este caso he puesto el puerto 700 pero podéis poner el que queráis, y ahora igual que antes le damos a **Create** y por último **Apply changes**

Y ahora vamos a probar a conectar desde el FileZilla, ingresamos todos los datos exactamente de la misma manera, pero en este caso en el apartado de puerto pondremos el que le hemos asignado, *si vemos que nos da error al conectar al servidor, simplemente desde Webmin le damos a **Stop server** y luego lo volvemos a iniciar, o poniendo en la terminal sudo /etc/init.d/proftpd restart.*

![imagen9](/imagenes/Captura9.PNG)

Y como vemos se conecta perfectamente al servidor.







