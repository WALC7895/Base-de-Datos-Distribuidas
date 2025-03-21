# Base-de-Datos-Distribuidas

prueba 16 de abril -> 2
prueba 7 de julio -> 2

Ejercicio: Para modelar una base de datos con la empresa nova publicado en Ambato se dedica a construir o diseñar zapatos deportivos, la empresa tiene dos sucursales, Latacunga y en Riobamba, las ventas en Ambato crecen en 10% diarios, en Latacunga el 20% y en Riobamba el 30%,necesitamos diseñar una cuarta sucursal que tenga la ganancia en ventas del 40%. Donde seria esta sucursal?
diagrama de flujo

EMPRESA=(ID_EMP, NOM_EMP, DES_EMP)

CIUDAD=(ID_CIU, NOM_CIU, DES_CIU)

SUCURSAL=(ID_SUC, NOM_SUC, DIR_SUC, ID_CIU_SUC, ID_EMP_PER)

MARCAS_ZAPATOS=(ID_MAR, NOM_MAR, DES_MAR)

ZAPATOS=(ID_ZAP, NOM_ZAP, COL_ZAP, PRE_ZAP, TALL_ZAP, ID_MAR)

VENTAS=(ID_VEN, FEC_VEN, ID_SUC_VEN, ID_ZAP_VEN, CANT_PAR_VEN, TOTAL_VEN)

HISTORIAL_VENTAS=(ID_HIS, ID_SUC_PER, PORC_CRE_VEN)

 ------------------------------------------------------------------------------------------
| 21/03/2024 |
 ------------
													BASE DE DATOS
TABLAS: Son estructuras, entidades o conceptos en especifico
CAMPOS: Son los atributos especificos de los datos almacenados
REGISTRO: Conocidos como filas, instancias dindividuales de cada datos de una tabla. 
CLAVES PRIMARIAS: Campos o conjunto de campos que identifican de manera unica cada registro.
CLAVES FORÁNEAS: Son campos de una tabla utilizadas para establecer relaciones.
CONSULTAS: Son instrucciones utilizados para recuperar, actualizar, manipular datos dentro de una base de datos
ÍNDICES: Estructuras adicionales que mejoran el rendimiento de las consultas.
VISTAS: Actuan como tablas virtuales.
.
                                  ARQUITECTURA DE LOS SISTEMAS DE BASES DE DATOS
		 
BASE DE DATOS CENTRALIZADA: Arquitectura donde se almacenan todos los datos
Son aquellos que se ejecutan en un mismo sistema informatico, sin iteraccionar sin ninguna otra computadora. Tales sistemas comprenden 
el rango desde los sistemas de bases de datos monousuario ejecutándose en computadoras personales hasta los sistemas de bases de datos 
de alto rendimiento ejecutándose en grandes sistemas.
                                      SISTEMAS DISTRIBUIDOS
Se almacena la base de datos en varias computadoras. Los medios de comunicación como las redes de alta velocidad o las líneas telefónicas
pueden poner en contacto las distintas computadoras de un sistema distribuido. Existen varias razones para construir sistemas distribuidos de
bases de datos, incluyendo el comportimiento de los datos, la autonomía y la disponibilidad.

BASE DE DATOS DISTRIBUIDAS: Es una base de datos donde los datos almacenados se encuentran o almacenan en varios servidores que estan conectados por una red.
.
                                   ARQUITECTURA CLIENTE SERVIDOR
Tienen su funcionalidad dividida entre el sistema servidor y múltiples sistemas clientes. La funcionalidad se puede
dividir en dos partes: la fachada y el sistema subyacente. El sistema subyacente gestiona el acceso a las
estructuras. La fachada de un sistema de base de datos está formado por herramientas como la interfaz de usuario con SQL.
.
                                       SISTEMAS PARALELOS
Mejoran la velocidad de procesamiento y de E/S porque la CPU y los discos funcionan en paralelo. En el
procesamiento paralelo se realizan muchas operaciones simultáneamente mientras que en el procesamiento
secuencial, los distintos pasos computacionales han de ejecutarse en serie.
.
                               ARQUITECTURAS DE SISTEMAS SERVIDORES
Los sistemas servidores de transacciones proporcionan una interfaz a través de la cual los clientes pueden enviar peticiones 
para realizar una acción que el servidor ejecutará y cuyos resultados se devolverán al cliente. Los sistemas servidores de 
datos permiten a los clientes interaccionar con los servidores reali¬ zando peticiones de lectura o modificación de datos en
unidades tales como archivos o páginas.

ARQUITECTURA DISTRIBUIDA: tiene alta escabilidad.
Latencia: 
Base de datos distribuidas: Los datos, que se pueden almacenar mediante nodos.
NODO: Cada máquina que forma parte del sistema distribuido.
CLUSTER: Conjunto de nodos que trabajan juntos.
REPLICA: Copia de los datos en diferentes nodos.
PARTICIONAMIENTO: Divide los datos para almacenarlos en diferentes nodos.
CONSISTENCIA, DISPONIBILIDAD Y TOLERANCIA A PARTICIONES: Explicar las limitaciones y elecciones que deben hacerce en un sistema distribuido.

ARQUITECTURAS COMUNES
- AMO-ESCLAVO: Un nodo principal (master) y varios esclavos (slaves).
- PEER TO PEER: Todos los nodos son iguales.
- MULTI-MASTER: Varios nodos pueden ser "master" y aceptar escrituras.
- ILUSTRACION: Dibujar las tres arquitecturas y explicar las ventajas y desventajas de cada una.

REPLICACION Y SINCRONIZACION 
- Replicacion sincrona y asincrona.
- Como los datos se mantienen actualizados entre nodos.















