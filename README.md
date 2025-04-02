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












