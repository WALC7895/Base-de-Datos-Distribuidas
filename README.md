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













