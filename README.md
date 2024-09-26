Ejemplo Vagrant 1


Realiza el proyecto que aparece en la figura en Vagrant, teniendo en cuenta los siguientes datos:

Equipo --> revproxy
Sistema Operativo --> debian/bullseye64
Interfaces de red --> Puerto reenviado desde 8080 del host al 80 del guest | 192.168.57.10
Software instalado --> Nginx


Equipo --> database
Sistema Operativo --> rockylinux/9
Interfaces de red --> 192.168.57.11
Software instalado --> mariadb


Equipo --> app
Sistema Operativo --> ubuntu/focal64
Interfaces de red --> 192.168.57.13
Software instalado --> flask

Al final tendremos los siguientes ficheros:
    • Vagrantfile
    • .gitignore (ignorar directorio .vagrant)
    
Notas
    • Debemos actualizar la lista de paquetes en la provisión antes de instalar el software o el sistema operativo no lo encontrará. 
    • Tendremos que buscar el nombre del paquete que instala el software ya que el nombre no tiene que coincidir con el que aparece en la tabla.
    • Podemos buscar información en tutoriales acerca de la instalación del software. En nuestro ejemplo sólo haremos la instalación básica sin llegar a configurarlo completamente, ya que todavía no sabemos hacerlo.
    • Probar que tenemos conexión (ping) entre los equipos y que podemos acceder al menos al servidor web (proxy inverso o revproxy).
