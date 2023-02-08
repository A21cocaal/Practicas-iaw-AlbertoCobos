**Alberto Cobos Camacho – 2ºASIR** 




|<p>Implantación de aplicaciones Web</p><p></p><p>EFS EC2 StaticWEbURL</p><p></p><p>Alberto Cobos Camacho</p><p>2º Administración de sistemas informáticos en red</p>|
| :-: |







# **Grupos de seguridad**
Crearemos el siguiente grupo de seguridad

Le asignaremos un nombre

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.002.png)

Le pondremos las siguientes reglas de entrada y salida

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.003.png)

Añadiremos el SSH para que podamos acceder a la maquina

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.004.png)


Y crearemos el siguiente grupo de seguridad

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.005.png)

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.006.png)
# **Instancias**
Las 2 instancias tendrán lo siguiente:

SO: Amazon Linux

Tipo: t2.micro

Disco duro 8GB

Y le añadiremos este script

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.007.png)

Pondremos las diferentes zonas de disponibilidad tal y como nos comentaba el tutorial

![](./Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.008.png)![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.009.png)

# **Montaje de sistema de ficheros EFS (NFS)**
Lo crearemos de forma estándar

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.010.png)

Y nos lo creara aws

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.011.png)



Después le pondremos el grupo de seguridad antes creado el SGEFs

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.012.png)

Crearemos la carpeta nfs-mount y ejecutaremos el siguiente comando

El comando es 

sudo mount -t nfs -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-035536e8d2e6e3e36.efs.us-east-1.amazonaws.com:/ efs-mount

La parte marcada es el id de mi efs

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.013.png)![](Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.014.png)



Al ejecutar df-h veremos que se ha ejecutado correctamente

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.015.png)

**Esto lo haremos en AMBAS MAQUINAS**

Y nos descargaremos la página que nos indica el tutorial y hacerlo solo en una maquina ya que esta trabajando en NFS

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.016.png)

Y ya vemos como por ejemplo en la IP de la Linux\_01 funciona la pagina correctamente

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.017.png)



Y en la maquina Linux\_02 exactamente igual

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.018.png)

Para evitar tener que poner toda la url marcando la carpeta y el index.html haremos lo siguiente

Pondremos el document root la carpeta de efs

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.019.png)![](Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.020.png)

Reiniciaremos el servicio 

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.021.png)


y ya ira la página directamente desde la IP y nos ira bien tanto en una IP como la otra al haber configurado el document root en las dos

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.022.png)

## **Hacerlo permanente**
Tendremos que añadir la siguiente línea en el archivo /etc/fstab porque si no habría que hacer el proceso de montar otra vez el efs cada vez que iniciemos la máquina

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.023.png)

Y una vez reiniciemos las maquinas accedemos sin tener que montar 

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.024.png)


## **Quitando SSH**
Ahora para aumentar la Securizacion mas si cabe quitaremos el acceso al puerto 22 de las maquinas web

Quedaran las reglas del grupo de seguridad de las maquinas WEB así

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.025.png)

# **Balanceador de carga**
Crearemos un balanceador de carga con las siguientes características

SO: Linux

Lo demás por defecto

Instalado apache y modulo balancer manager

` `para acceder a la web y balancear

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.026.png)



Y vemos cómo podemos acceder con la IP del balanceador y balancea

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.027.png)

![](./imagenes/Aspose.Words.372f1066-45cd-4763-b611-fe329ecbf146.028.png)





Alberto Cobos Camacho		       2ºASIR – 22/23
