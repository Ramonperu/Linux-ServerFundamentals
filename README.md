# FUNDAMENTALS LINUX SERVERS

Bienvenidos a la guía para principiantes de Linux Servers realizada por Ramon Peinado Ruiz

## Linux Servers y Clientes

### 1. Comunicación Cliente-Servidor:

Los servidores son computadoras equipadas con software que les permite brindar servicios a los clientes a través de una red. Algunos **proporcionan recursos externos, como archivos, mensajes de correo electrónico o páginas web**, a los clientes cuando estos los solicitan. Otros servicios se encargan de tareas de mantenimiento, como la gestión de registros, la administración de memoria, el escaneo de discos, entre otras. Cada uno de estos servicios requiere su propio software de servidor. 

<img src="/img/1ºimagen.jpg" style="zoom:150%;" />



### 2. Servidores, Servicios y Puertos mas conocidos

Con el fin de permitir que una computadora funcione como servidor para múltiples servicios, se utilizan los puertos. **Un puerto es un recurso de red reservado utilizado por un servicio en particular**. Un servidor se dice que está "escuchando" en un puerto cuando se ha asociado a él.

Si bien el administrador puede decidir qué puerto utilizar para cada servicio, muchos clientes están configurados para utilizar un puerto específico de manera predeterminada. Es práctica común dejar que el servicio se ejecute en su puerto predeterminado. 

La siguiente tabla muestra algunos puertos comúnmente utilizados y los servicios asociados a ellos:

| Puerto  | Descripción                                                  |
| :------ | :----------------------------------------------------------- |
| 20/21   | File Transfer Protocol (FTP) - Protocolo de transferencia de archivos. |
| 22      | Secure Shell (SSH) - Shell Seguro.                           |
| 23      | Telnet - Servicio de inicio de sesión remoto Telnet.         |
| 25      | Simple Mail Transfer Protocol (SMTP) - Protocolo simple de transferencia de correo. |
| 53      | Domain Name System (DNS) - Sistema de nombres de dominio.    |
| 67/68   | Dynamic Host Configuration Protocol (DHCP) - Protocolo de configuración dinámica de host. |
| 69      | Trivial File Transfer Protocol (TFTP) - Protocolo trivial de transferencia de archivos. |
| 80      | Hypertext Transfer Protocol (HTTP) - Protocolo de Transferencia de hipertexto. |
| 110     | Post Office Protocol version 3 (POP3) - Protocolo de oficina de correos . |
| 123     | Network Time Protocol (NTP) - Protocolo de tiempo de red.    |
| 143     | Internet Message Access Protocol (IMAP) - Protocolo de acceso a mensajes de Internet. |
| 161/162 | Simple Network Management Protocol (SNMP) - Protocolo simple de administracion de red. |
| 443     | HTTP Secure (HTTPS) - HTTP Seguro.                           |

### 3. Clientes

Los clientes son programas o aplicaciones diseñados para establecer comunicación con un tipo específico de servidor. También conocidos como aplicaciones cliente, utilizan un protocolo definido para interactuar con el servidor. Por ejemplo, los navegadores web actúan como clientes web al comunicarse con servidores web a través del Protocolo de Transferencia de Hipertexto (HTTP) en el puerto 80. Por otro lado, el cliente del Protocolo de Transferencia de Archivos (FTP) es un software utilizado para conectarse y comunicarse con un servidor FTP.



<img src="/img/2ºimagen.jpg" style="zoom:150%;" />

------



## Administración básica del Servidor

### 1.  Archivos de configuración de Servicios

En el entorno de Linux, la configuración de los servicios se realiza mediante archivos específicos. Estos archivos de configuración contienen opciones comunes, como el número de puerto, la ubicación de los recursos alojados y los detalles de autorización de los clientes. Al iniciarse, el servicio busca sus archivos de configuración, los carga en la memoria y se ajusta según las configuraciones establecidas en ellos. Cabe destacar que, en muchos casos, es necesario reiniciar el servicio para que los cambios realizados en el archivo de configuración surtan efecto.

Dado que los servicios a menudo requieren privilegios de superusuario para ejecutarse, los archivos de configuración del servicio también requieren privilegios de superusuario para su edición.

### 2. Fortalecimiento de Dispositivos 

El fortalecimiento de dispositivos implica implementar métodos probados para asegurar el dispositivo y proteger su acceso administrativo. Algunas de estas medidas incluyen **mantener contraseñas seguras, configurar características avanzadas de inicio de sesión remoto y utilizar SSH para un inicio de sesión seguro.** Asimismo, es importante definir roles administrativos en términos de acceso para garantizar que no todo el personal de tecnología de la información tenga el mismo nivel de acceso a los dispositivos de infraestructura.

En muchas distribuciones de Linux, se habilitan por defecto diversos servicios. Sin embargo, algunos de ellos pueden haber quedado obsoletos y ya no ser necesarios. **Una técnica de fortalecimiento de dispositivos es detener y deshabilitar aquellos servicios que no se utilizan**, evitando así que se inicien automáticamente al arrancar el sistema

Prácticas básicas para el fortalecimiento de dispositivos:

- Asegurar la seguridad física del dispositivo.
- Minimizar la cantidad de paquetes instalados.
- Desactivar los servicios que no se utilizan.
- Utilizar SSH y deshabilitar el inicio de sesión de la cuenta de root a través de SSH.
- Mantener el sistema actualizado.
- Deshabilitar la detección automática de dispositivos USB.
- Implementar contraseñas fuertes.
- Obligar a cambios periódicos de contraseñas.
- Evitar que los usuarios reutilicen contraseñas antiguas.

Existen muchos otros pasos adicionales que pueden variar según el servicio o la aplicación utilizada.



### 3. Monitoreo de Registros/logs de Servicio

Los archivos de registro son los registros que una computadora almacena para realizar un seguimiento de eventos importantes. En ellos se registran eventos del kernel, servicios y aplicaciones. Es fundamental que un administrador revise periódicamente los registros de una computadora para mantenerla en óptimas condiciones. Al monitorear los archivos de registro de Linux, un administrador obtiene una visión clara del rendimiento de la computadora, su estado de seguridad y posibles problemas subyacentes. El análisis de los archivos de registro permite al administrador anticiparse a posibles problemas antes de que ocurran.

En Linux, los archivos de registro se pueden clasificar en diferentes categorías:

- Registros de aplicaciones
- Registros de eventos
- Registros de servicios
- Registros del sistema

Algunos registros contienen información sobre los demonios que se ejecutan en el sistema Linux. Un demonio es un proceso en segundo plano que se ejecuta sin necesidad de interacción del usuario. Por ejemplo, el Demonio de Servicios de Seguridad del Sistema (SSSD) administra el acceso remoto y la autenticación para capacidades de inicio de sesión único.

Archivos de registro populares en Linux y sus funciones correspondientes.

| Linux Log File                            | Description                                                  |
| :---------------------------------------- | :----------------------------------------------------------- |
| /var/log/messages                         | Contiene registros genéricos de actividad de la computadora. Se utiliza principalmente para almacenar mensajes del sistema informativos y no críticos. En las computadoras basadas en Debian, el directorio /var/log/syslog tiene el mismo propósito. |
| /var/log/auth.log                         | Este archivo almacena todos los eventos relacionados con la autenticación en las computadoras Debian y Ubuntu. Todo lo relacionado con el mecanismo de autorización del usuario se puede encontrar en este archivo. |
| /var/log/secure                           | RedHat y CentOS usan este directorio en lugar de /var/log/auth.log. También rastrea los inicios de sesión de Sudo, los inicios de sesión de SSH y otros errores registrados por SSSD. |
| /var/log/boot.log                         | Este archivo almacena información relacionada con el arranque y mensajes registrados durante el proceso de inicio de la computadora. |
| /var/log/dmesg                            | Contiene mensajes del búfer de anillo del núcleo. Aquí se registra información relacionada con los dispositivos de hardware y sus controladores. |
| /var/log/kern.log                         | Este archivo contiene información registrada por el kernel.  |
| /var/log/cron                             | Cron es un servicio utilizado para programar tareas automatizadas en Linux y este directorio almacena sus eventos. Cada vez que se ejecuta una tarea programada (también llamada trabajo cron), toda su información relevante, incluido el estado de ejecución y los mensajes de error, se almacena aquí. |
| /var/log/mysqld.log or /var/log/mysql.log | Este es el archivo de registro de MySQL. Todos los mensajes de depuración, falla y éxito relacionados con el proceso mysqld y el demonio mysqld_safe se registran aquí. Las distribuciones RedHat, CentOS y Fedora Linux almacenan los registros de MySQL en /var/log/mysqld.log, mientras que Debian y Ubuntu mantenga el registro en el archivo /var/log/mysql.log. |

### 4. Uso del terminal

La **Terminal de Linux** es una consola, similar a CMD o PowerShell (pero mucho más avanzada que ambas), utilizada para permitir a los usuarios más avanzados y técnicos controlar hasta el más mínimo detalle del sistema operativo.

La terminal de Linux es ampliamente utilizada en la administración de servidores debido a su flexibilidad, control, capacidad de acceso remoto, capacidades de automatización, eficiencia en recursos y herramientas de registro. 

Motivos por los que se usa en administración de servidores

- **Flexibilidad y control**: La terminal permite a los administradores tener un mayor control y flexibilidad en la administración del servidor. Permite ejecutar comandos y realizar tareas de manera más rápida y eficiente, sin depender de interfaces gráficas que pueden ser más limitadas.
- **Acceso remoto**: La terminal es especialmente útil en entornos de servidores remotos, donde se puede acceder al servidor a través de SSH (Secure Shell). Esto permite administrar el servidor de forma remota, sin necesidad de estar físicamente presente en el lugar donde se encuentra el servidor.
- **Automatización**: La terminal de Linux es altamente programable y se puede utilizar para escribir scripts y automatizar tareas. Esto facilita la administración y el mantenimiento de servidores, ya que se pueden realizar acciones repetitivas de forma automatizada, ahorrando tiempo y reduciendo errores humanos.
- **Eficiencia en recursos**: La terminal utiliza menos recursos del sistema en comparación con las interfaces gráficas. Esto es especialmente importante en entornos de servidores, donde se busca optimizar el rendimiento y la eficiencia de los recursos del sistema.
- **Historial y registro**: La terminal registra un historial de comandos ejecutados, lo que facilita la revisión y reproducción de acciones anteriores. Además, se pueden generar registros (logs) de la actividad de la terminal, lo que resulta útil para el seguimiento y la resolución de problemas.

Puedes aprender mas sobre el terminal de Linux y su uso en mi guia: https://github.com/Ramonperu/Linux-Fundamentals 



## BIBLIOGRAFIA y AGRADECIMIENTOS

Esta guía básica no podía haber sido realizada sin la ayuda de estos dos cursos:

Aprende a usar la línea de comandos de Linux			Esther Yébenes 		Linkedin Learning.

Operating Systems Basics 																					Cisco Networking Academy.

Mencionar también la gran ayuda recibida por parte de toda la comunidad de Linux y sus foros .

