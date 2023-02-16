**Alberto Cobos Camacho – 2ºASIR** 
|<p>Implantación de aplicaciones web</p><p></p><p>Finalizar escenario Cluster Web</p><p></p><p>Alberto Cobos Camacho</p><p>2º Administración de sistemas informáticos en red</p>|
| :-: |


# **Índice**
[IPs de las maquinas/Identificadores	](#_Toc127437917)

[Creación de BDD	](#_Toc127437918)

[Instalación PHP	](#_Toc127437919)

[Introduccion/Creacion código PHP	](#_Toc127437920)



# **IPs de las maquinas/Identificadores**
Balanceador: 35.153.79.34

Web1: 107.22.72.3

Web2 : 50.19.115.32

BDD: bdd-rds.ctbmdjl2bw2x.us-east-1.rds.amazonaws.com
#
# **Creación de BDD**
![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.002.png)
# **Instalación PHP**
Ejecutaremos los siguientes comandos en las dos maquinas WEB

Veremos en amazon Linux extra las versiones ultimas de PHP

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.003.png)



Aunque no usemos la ultima vamos a usar la versión 7.4 de PHP

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.004.png)

Borraremos los metadatos con yum clean metadata

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.005.png)

Y instalaremos php con los siguientes complementos

Código:

sudo yum install php-cli php-pdo php-fpm php-json php-mysqlnd php-gd

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.006.png)



Comprobaremos la versión con php -v

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.007.png)
# **Introduccion/Creacion código PHP**
index.php

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.008.png)

Conexión.php

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.009.png)

Donación.php

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.010.png)



Grabar.php

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.011.png)


# **Ejemplo de funcionamiento**
Le damos a donativos de siria y Turquía Observamos que los euros donados son 20

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.012.png)

Y a nombre de Anonimo pondremos una donación

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.013.png)

Nos mandará un mensaje de donación hecha correctamente y le daremos volver a inicio

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.014.png)



Y vemos como ha subido la donación de 20 a 220

![](./imagenes/Aspose.Words.30f71988-4821-4c3d-83f8-3a6a2c0528bd.015.png)


Alberto Cobos Camacho		       2ºASIR – 22/23
