TRIGGER PARA VERIFICAR EL VENCIMIENTO DE LA LICENCIA 
CREATE TRIGGER trg_VerificarLicenciaVencida
ON CONDUCTORES
FOR INSERT, UPDATE
AS
BEGIN
    -- Verifica si la licencia está vencida
    IF EXISTS (
        SELECT 1 
        FROM inserted
        WHERE FEC_VEN_LIC < GETDATE()
    )
    BEGIN
        -- Lanza un error si la licencia ya está vencida
        RAISERROR ('No se puede registrar un conductor con licencia vencida.', 16, 1);
        ROLLBACK TRANSACTION;
    END
END;

TRIGGER PARA VERIFICAR EL CONTROL Y ESTADO DEL VEHICULO

CREATE OR REPLACE FUNCTION verificar_vehiculo_disponible()
RETURNS TRIGGER AS $$
DECLARE
    estado CHAR(1);
BEGIN
    SELECT ESTADO_DISP INTO estado FROM VEHICULO WHERE ID_VEH = NEW.ID_VEH_CON;
    IF estado IS DISTINCT FROM 'A' THEN
        RAISE EXCEPTION 'El vehículo con ID % no está disponible para asignación.', NEW.ID_VEH_CON;
    END IF;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

TRIGGER PARA VERIFICAR EL COSTO DEL VIAJE

CREATE TRIGGER trg_calcular_costo_viaje
ON RUTAS
AFTER INSERT, UPDATE
AS
BEGIN
    UPDATE r
    SET r.COSTO_VIAJE = (g.PRECIO_X_GALON / 3.785) * r.DIS_RRE_KM
    FROM RUTAS r
    JOIN INSERTED i ON r.ID_RUT = i.ID_RUT
    JOIN VEHICULO v ON r.ID_VEH_PER = v.ID_VEH
    JOIN GASOLINA g ON v.ID_VEH = g.ID_VEH_PER;
END;

BASE DE DATOS CENTRALIZADA Y MODELOS DE ARQUITECTURA 

 Componentes 

Servidor central: Un unico servidor que almacena toda la base de datos. 

Clientes: Acceden al servidor central para consultar o modificar los datos 

Caracteristicas  

Centralizacion: Todos los datos se encuentran en un unico lugar(Servidor central) 

Acceso: Los clientes se comunican directamente con el servidor para realizar operaciones. 

Ventajas 

Simplicidad: Facil administracion y mantenimiento de la base de datos 

Consistencia: Todos los clientes ven los mismo datos en todo el mundo 

Desventajas  

Punto unico de fallo: Si el servidor central falla, toda la base de datos se vuelve inaccesible. 

Escalamiento limitado. 

CLASIFICACION DE BASE DE DATOS DISTRIBUIDAS 

  

FRAGMENTADAS 

  

Los datos de una base de datos distribuidas deberían estar fragmentadas 

Fragmentación Horizontal: Divide los registros (Fila de datos organizados) por filas (se tomara en cuenta la fila que será transmitida) según condiciones específicas. 

Otra clave para la fragmentación es que está basada en encontrar condiciones de selección. 

Fragmentación Vertical: Divide los registros por columnas (manteniendo la clave primaria en cada fragmento para poder reconstruir la tabla original si es necesario) según el uso de los atributos 

Basada en encontrar conjunto de atributos. 

Fragmentación Mixta: Es una combinación de ambas fragmentaciones, tanto horizontal como vertical. Se usa cuando la BD es muy grande. 

Cuando hay partes de la base de datos que deben estar en diferentes ubicaciones físicas por razones de seguridad o acceso. 

  

REPLICADAS 

  

Replicación completa: Cada nodo contiene un respaldo completo de los datos. 

Replicación parcial: Algunos datos se respaldan dependiendo de las necesidades requeridas o específicas. 

  

HIBRIDAS 

  

Combina la fragmentación y replicación según los requerimientos operativos y estratégicos. 

Cuando se necesita optimizar el rendimiento y la organización de los datos 

En bases de datos muy grandes y distribuidas, donde un solo tipo de fragmentación no es suficiente. 

Cuando se quiere minimizar la redundancia y mejorar la eficiencia del acceso a datos. 

Para sistemas donde diferentes usuarios o aplicaciones requieren diferentes subconjuntos de datos. 

 

 SEGUN LA AUTONOMIA DEL NODO 

  

Bases de datos federadas  

Alta autonomía local, cada nodo mantiene control propio de sus datos.  

Gestión descentralizada.  

Bases de datos multidatabase  

Colección de bases de datos independientes que cooperan mediante acuerdos explícitos.  

Autonomía y heterogeneidad son características esenciales.  

  

VENTAJAS DE UNA BDDD 

Mayor disponibilidad y confiabilidad.  

Escalabilidad eficiente.  

Distribución de carga.  

Flexibilidad y adaptación geográfica.  

UN ESCHEMA ES UN ARCHIVO PLANO 

Fragmentación Horizontal  

Ventajas:  

Reduce la cantidad de datos que cada nodo debe procesar.  

Mejora el rendimiento de las consultas al acceder solo a los datos relevantes para cada sitio.  

Facilita la paralelización de procesos y el mantenimiento de la base de datos.  

Fragmentación Vertical  

Ventajas:  

Permite optimizar el acceso a datos cuando las aplicaciones requieren solo ciertos campos.  

Mejora la seguridad al separar información sensible en fragmentos diferentes.  

Facilita la gestión del ancho de banda, ya que se transfieren solo los datos necesarios.  

Fragmentación Mixta (o Híbrida)  

Ventajas:  

Ofrece una mayor flexibilidad para adaptar la distribución de los datos a las necesidades específicas de las aplicaciones y usuarios.  

Permite aprovechar las ventajas de ambos métodos, optimizando tanto el rendimiento como la seguridad. 
NSTANCIAS EN UNA BASE DE DATOS DISTRIBUIDAS 

 

En un servidor Ubuntu como principal, al darles instancias (servidores virtuales) 

Una instancia es el entorno de ejecución del motor de base de datos. Es decir, es el conjunto de procesos, memoria y archivos que permite que puedas crear, consultar y administrar bases de datos. Una instancia en una base de datos es un entorno que gestiona bases de datos, archivos y memoria 

 

Para comunicarse con el SQL se comunicara por el puerto 1433. 










