**Alberto Cobos Camacho – 2ºASIR** 


![](Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.001.png)



|<p>Implantación de aplicaciones Web</p><p></p><p>Práctica 4.4: Despliegue de una base de datos Multi AZ</p><p></p><p>Alberto Cobos Camacho</p><p>2º Administración de sistemas informáticos en red</p>|
| :-: |




# **Creación de base de datos**
Crearemos una base de datos en RDS, usaremos el motor de mysql

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.002.png)

La plantilla que usaremos será Produccion para valores de alto rendimiento y la disponibilidad que pondremos es que será una instancia de BDD tipo Multi-AZ, esto consiste en que se creara una base de datos primaria y una base de datos en una zona de disponibilidad diferente

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.003.png)



Crearemos las credenciales y asignaremos un identificador a la instancia

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.004.png)

La configuración de la instancia será con una dbt.t3.micro que tiene 2vCPUs, 1 GB de RAM y Red:2085 Mbps

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.005.png)



Y el tipo de almacenamiento lo pondremos de la siguiente forma ya que no vamos a usar muchos recursos y no nos interesa tampoco por temas de cobro de aws

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.006.png)

Y crearemos un grupo de seguridad con el puerto de mysql habilitado dentro de un grupo de seguridad para securizar la RDS y solo puedan acceder nuestros servidores web

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.007.png)

Añadiremos el grupo de seguridad de nuestros servidores web para que solo ellos tengan acceso

![](Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.008.png)
# **Instalación y configuración maquina Windows**
Creación de máquina Windows

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.009.png)



La pondremos en el grupo de seguridad de web

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.010.png)

En el grupo segweb añadiremos la regla RDP

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.011.png)



Y sacaremos la contraseña del Windows cuando se haya creado

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.012.png)

Ejecutaremos el archivo y nos pedirá contraseña

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.013.png)



Y nos conectaremos mediante la contraseña y el archivo de escritorio remoto descargado previamente

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.014.png)

Nos descargaremos heidisql

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.015.png)



Lo iniciaremos y nos conectaremos

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.016.png)

Nos saldrá el siguiente mensaje le daremos que si 

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.017.png)

Y ya estaremos conectados correctamente al RDS desde la instancia de Windows

![](./imagenes/Aspose.Words.000816ac-892b-455d-88b8-2f8a3e405a4e.018.png)



Alberto Cobos Camacho		       2ºASIR – 22/23
