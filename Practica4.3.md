**Alberto Cobos Camacho – 2ºASIR** 


![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.001.png)



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

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.002.png)

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.003.png)

Una vez hecho eso reiniciamos apache y ponemos la página del balancer-manager y veremos como balancea las 3 maquinas

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.004.png)

# **Base de datos**
Crearemos una base de Datos MYSQL en RDS

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.005.png)



Y crearemos una base de datos llamada wordpress para poder acceder al wordpress

![](Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.006.png)
# **Servidores**
Tendrán las siguientes características 

Ubuntu 20.04

Seguridad HTTP y SSH abierta

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.007.png)



Wordpress instalado junto a apache y php

Instalaremos wordpress en todos los servidores con la misma base de datos almacenando la misma pagina 

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.008.png)
# **Seguridad**
Pondremos los 3 servidores con acceso a http solo al balanceador

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.009.png)

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.010.png)

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.011.png)

Y el balanceador tendrá acceso público a http

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.012.png)

# **Servidor nfs**

Lo instalaremos el servidor nfs en la maquina NFS

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.013.png)
#

# **Cliente nfs**
Instalaremos nfs-common en los clientes

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.014.png)

# **Archivo exports**

Pondremos lo siguiente en el archivo /etc/exports

Pondremos la línea por cada cliente que vaya a usar nfs

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.015.png)

Ahora reiniciaremos el servicio

![](./imagenes/Aspose.Words.a73ab31d-213c-46ca-8535-d3a8d03ed425.016.png)

# **Creación de punto de montaje para el cliente NFS**

Haremos eso en todos los clientes

![](./imagenes/Aspose.Words.8747ee55-9aa1-49cc-a349-64c1c96b7d69.001.png)

Y para comprobar que se ha montado correctamente usamos el comando df -h para ver si se ha montado

![](./imagenes/Aspose.Words.8747ee55-9aa1-49cc-a349-64c1c96b7d69.003.png)

Para hacer que se monte cada vez que se inicie la maquina pondremos esta línea en el /etc/fstab para que se monte automáticamente al iniciar

![](./imagenes/Aspose.Words.8747ee55-9aa1-49cc-a349-64c1c96b7d69.005.png)

Y por último instalaremos WordPress en el nfs

![](./imagenes/Aspose.Words.8747ee55-9aa1-49cc-a349-64c1c96b7d69.006.png)




