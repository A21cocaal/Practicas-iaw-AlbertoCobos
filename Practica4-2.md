**Alberto Cobos Camacho – 2ºASIR** 

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.001.png)



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

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.002.png)

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.003.png)

Una vez hecho eso reiniciamos apache y ponemos la página del balancer-manager y veremos como balancea las 3 maquinas

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.004.png)

# **Base de datos**
Crearemos una base de Datos MYSQL en RDS

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.005.png)



Y crearemos una base de datos llamada wordpress para poder acceder al wordpress

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.006.png)
# **Servidores**
Tendrán las siguientes características 

Ubuntu 20.04

Seguridad HTTP y SSH abierta

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.007.png)



Wordpress instalado junto a apache y php

Instalaremos wordpress en todos los servidores con la misma base de datos almacenando la misma pagina 

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.008.png)
# **Seguridad**
Pondremos los 3 servidores con acceso a http solo al balanceador

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.009.png)

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.010.png)

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.011.png)

Y el balanceador tendrá acceso público a http

![](./imagenes/Aspose.Words.1dbbbdb9-db66-4f0c-8903-5ee3f0933dc0.012.png)




Alberto Cobos Camacho		       2ºASIR – 22/23
