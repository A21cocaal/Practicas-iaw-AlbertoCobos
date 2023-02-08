**Alberto Cobos Camacho – 2ºASIR** 



![](Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.001.png)



|<p>Implantación de aplicaciones web</p><p></p><p>Práctica 4.2 Instalar Wordpress en una arquitectura de tres niveles</p><p></p><p>Alberto Cobos Camacho</p><p>2º Administración de sistemas informáticos en red</p>|
| :-: |







# **Las direcciones IPs de cada maquina correspondiente**
Balanceador: 44.205.224.103

Server 1: 52.5.243.95

Server 2: 3.234.155.253

Server 3: 54.84.46.106
#
# **Balanceador**
Instalaremos apache y le pondremos la siguiente configuración en el archivo de configuración para poder balancear

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.002.png)

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.003.png)

Una vez hecho eso reiniciamos apache y ponemos la página del balancer-manager y veremos como balancea las 3 maquinas

![](Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.004.png)


# **Base de datos**
Crearemos una base de Datos MYSQL en RDS

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.005.png)

Y crearemos una base de datos llamada wordpress para poder acceder al wordpress

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.006.png)


# **Servidores**
Tendrán las siguientes características 

Ubuntu 20.04

Seguridad HTTP y SSH abierta

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.007.png)

Wordpress instalado junto a apache y php

Instalaremos wordpress en todos los servidores con la misma base de datos almacenando la misma pagina 

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.008.png)


# **Seguridad**
Pondremos los 3 servidores (Que están con el mismo grupo de seguridad) con acceso a http solo al balanceador

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.009.png)

Y el balanceador tendrá acceso público a http

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.010.png)

# **Servidor nfs**
Lo instalaremos el servidor nfs en la maquina NFS

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.011.png)

# **Cliente nfs**
Instalaremos nfs-common en los clientes

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.012.png)
# **Archivo exports**
Pondremos lo siguiente en el archivo /etc/exports

Pondremos la línea por cada cliente que vaya a usar nfs

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.013.png)

Ahora reiniciaremos el servicio

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.014.png)
# **Creación de punto de montaje para el cliente NFS**
Haremos eso en todos los clientes

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.015.png)

Y para comprobar que se ha montado correctamente usamos el comando df -h para ver si se ha montado

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.016.png)![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.017.png)

Para hacer que se monte cada vez que se inicie la maquina pondremos esta línea en el /etc/fstab para que se monte automáticamente al iniciar

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.018.png)![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.019.png)

Y por último instalaremos WordPress en el nfs

![](./imagenes/Aspose.Words.d59cfd22-f78d-4c60-b08f-c7a2650b76f9.020.png)


