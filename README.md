# ETL-CINTE-NestorYaraG
Buen dia, relaciono ETL segun prueba tecnica propuesta. Gracias


Los 2 querys son los siguientes para las BD SQL y ORACLE.
1.Ya existente la tb creada donde alojara la data del archivo, se truncara cada vez que se ejecute con el fin de mantener la inf actualizada del excel.
drop table SQL_CINTE_1; 
NOMBRE_TB= **SQL_CINTE_1- ORA_CINTE_1**
CREATE TABLE [NOMBRE_TB] (
    [Documento] float,
    [Fecha] datetime,
    [Departamento] nvarchar(255),
    [Municipio] nvarchar(255),
    [Dia] nvarchar(255),
    [Hora] datetime,
    [Sitio] nvarchar(255),
    [Agresor] nvarchar(255),
    [Victima] nvarchar(255),
    [Edad] float,
    [Pais_nacimiento] nvarchar(255),
    [Clase_empleado] nvarchar(255),
    [Profesion] nvarchar(255),
    [Escolaridad] nvarchar(255),
    [Codigo_DANE] float
);

2. Una vez la data este cargada, se realiza el borrado tomando referencia la fecha reciente x cada num de Documento.

DELETE T
FROM
(
SELECT *
, DupRank = ROW_NUMBER() OVER (
              PARTITION BY documento
			  order by Fecha desc
            )
FROM NOMBRE_TB
) AS T
WHERE DupRank > 1

Nota:
Se tuvo que realizar la prueba en una MV en Azure, alli se instalo y configuro todo, debido con el instalador cliente de Oracle 12c en mi laptop :c 

Gracias¡
