# Apuntes SQL-DDL
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.
## Índice
- [Qué es el sublenguaje DDL](#QUÉ-ES-EL-SUBLENGUAJE-DDL)
- [Tipos de datos](#TIPOS-DE-DATOS)
- [Sentencia CREATE](#SENTENCIA-CREATE)
  - [Crear bases de datos](#CREAR-BASE-DE-DATOS)
  - [Crear dominio](#CREAR-DOMINIO)
  - [Crear tablas](#CREAR-TABLA)
- [Sentencia DROP](#SENTENCIA-DROP)
  - [Borrar una base de datos](#BORRAR-BASE-DE-DATOS)
  - [Borrar tablas dentro de una base de datos](#BORRAR-TABLAS)
- [Sentencia ALTER](#SENTENCIA-ALTER)
  - [Modificar tablas de una base de datos](#MODIFICAR-UNA-TABLA)
- [Constraints](#CONSTRAINTS)
- [Ejemplo de como aplicar las sentencias](#EJEMPLO)
## QUÉ ES EL SUBLENGUAJE DDL
EL ```DDL``` (Data Definition Language) permite dentro de un sistema gestor de base de datos definir las estructuras de la base de datos como también los procedimientos de consulta de esos datos.
Las tres principales sentencias dentro de este sublenguaje son:
- ```CREATE```
- ```ALTER```
- ```DROP```

## TIPOS DE DATOS
Dentro del DDL, hay muchísima variedad de datos, pero varias según el gestor que estemos utilizando. A Continuación se mostrará una tabla de una selección de los que vamos a usar.
| Dato          | Función                                                                                  |
|---------------|------------------------------------------------------------------------------------------|
| **texto**     |                                                                                          |
| CHAR(n)       | de longitud fija                                                                         |
| VARCHAR(n)    | de longitud variable                                                                     |
| TEXT          | de longitud variable e ilimitada                                                           |
| **numeros**   |                                                                                          |
| INTEGER       | número entero                                                                            |
| DECIMAL(n,m)  | número decimal con precisión (n=entero, m=decimal)                                       |
| REAL          | número aproximado                                                                        |
| **fecha**     |                                                                                          |
| DATE          | 'aaaa-mm-dd', formato de sólo de fecha                                                   |
| TIME          | 'hh:mm:ss', formato solo de hora                                                         |
| TIMESTAMP     | 'aaaa-mm-dd hh:mm:ss', combinación de las dos anteriores                                 |
| **otros**     |                                                                                          |
| BOOLEAN       | TRUE[1] o FALSE[0]                                                                       |
| MONEY         | Uso para moneda de hasta 4 cifras decimales                                              |
| UUID          | identificador universal único de 128 bits                                                |
| JSON          | para archivos JSON (JavaScript Object Notation)                                          |

## SENTENCIA CREATE
Es la sentencia que se utiliza para crear una base de datos u objetos dentro de esa base de datos (tabla, usuario,dominio, vista ...) 

## CREAR BASES DE DATOS
La sentencia CREATE permite crear bases de datos de dos formas:
- ```CREATE DATABASE```
 ```sql
  CREATE DATABASE
       [IF NOT EXIST] nombrebase
       [CHARACTER SET nombredecharset] ;

```
> CREATE DATABASE tiene permisos muy restrictivos

- ```CREATE SCHEMA```
 ```sql
  CREATE SCHEMA
       [IF NOT EXIST] nombrebase 
       [CHARACTER SET nombredecharset] ;

```
> CREATE SCHEMA tiene permisos menos restrictivos

## CREAR DOMINIO
La sentencia ```CREATE DOMAIN``` se utiliza para crear dominios. Estos dominios se utilizan para gestionar de manera más ordenada y eficiente distintos atributos que comparten un mismo tipo de datos.
Su sintaxis:
 ```sql
  CREATE DOMAIN <nombredominio> <tipodato>;

```

## CREAR TABLA
La sentencia ```CREATE TABLE``` se utiliza para crear tablas dentro de una base de datos con la siguiente sintaxis:

 ```sql
 CREATE TABLE <nombretabla>
( <atributo1> <dominio1> [NOT NULL] [DEFAULT <X>] ,
[RESTRICCIÓN1], … ]
);


```
## SENTENCIA DROP
Es la sentencia que se utiliza para eliminar una base de datos u objetos dentro de esa base de datos como una tabla.

## BORRAR BASE DE DATOS
Las sentencias ```DROP SCHEMA``` y ```DROP DATABASE``` se utiliza para borrar bases de datos con la siguiente sintaxis:

 ```sql
 DROP SCHEMA [IF EXISTS] <nombrebasededatos>
[CASCADE | RESTRICT ] ;

```
Hay dos opciones para borrar la base de datos:
- ``` RESTRICT ```: Protege los datos almacenados en la base de datos si no está vacía. Es la opción por defecto.
- ``` CASCADE ```: Borra la totalidad de la base de datos aunque no esté vacía.

## BORRAR TABLA
La sentencia ```DROP TABLE``` se utiliza para borrar tablas dentro de una base de datos con la siguiente sintaxis:

 ```sql
 DROP TABLE [IF EXISTS] <nombretabla>
[CASCADE | RESTRICT ] ;

```
Hay dos opciones para borrar la tabla:
- ``` RESTRICT ```: Protege los datos almacenados en la tabla si no está vacía. Es la opción por defecto.
- ``` CASCADE ```: Borra la totalidad de la tabla aunque no esté vacía.

## SENTENCIA ALTER
Es la sentencia que se utiliza para modificar o agregar columnas,restricciones... en las tablas de una base de datos.

## MODIFICAR UNA TABLA
La sentencia ```ALTER TABLE``` se utiliza para borrar, modificar o agregar tanto columnas como restricciones de las tablas dentro de una base de datos con la siguiente sintaxis:

 ```sql
ALTER TABLE [IF EXISTS] <nombretabla>
	 [RENAME TO <nuevonombre>],
	 [RENAME [COLUMN | CONSTRAINT] <nombreantiguo> TO <nombrenuevo>],
	 [SET SCHEMA <basededatos>],
	 [ADD | DROP [COLUMN | CONSTRAINT] <nombre>] ... ;

```
## CONSTRAINTS
Los ``` CONSTRAINT ``` son restricciones que se pueden agregar en las sentencias ``` CREATE TABLE ``` y ``` ALTER TABLE ``` y permiten establecer claves primarias, claves foráneas, checks, unicidad, límite de valores ...

### - ``` PRIMARY KEY ```
Restricción de clave principal, sólo puede exitir una por tabla.
Hay tres formas de establecer la clave principal:
> Indicarla en la propia línea
```sql
CREATE TABLE <nombre> (
    <atributo1> <dominio1> PRIMARY KEY,
    <atributoN> <dominioN>
    );

```
> Indicarla al final de la sentencia, por ejemplo, cuando es una clave compuesta.
```sql
CREATE TABLE <nombre> (
    <atributo1> <dominio1>,
    <atributoN> <dominioN>,
    PRIMARY KEY (atributo1[, atributoN])
);

```
> Indicarla al final de la sentencia y asignandole un nombre a la restricción.

```sql
CREATE TABLE <nombre> (
    <atributo1> <dominio1>,
    <atributoN> <dominioN>,
    CONSTRAINT <nombreconstraint>
    PRIMARY KEY (atributo1[, atributoN])
);

```
### - ``` FOREIGN KEY ```
Restricción de clave foránea. Sirve para interrelacionar tablas de una base de datos y pueden existir varias por tabla.
Hay varias formas de establecer esta restricción:

> Indicarla en la propia línea.
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1> 
  REFERENCES <nombretablaquequeremosreferenciar> [(<nombreatributoreferenciado>]),  ...
	[MATCH FULL | PARTIAL] 
	[ON DELETE CASCADE|NO ACTION|SET NULL|SET DEFAULT]
	[ON UPDATE CASCADE|NO ACTION|SET NULL|SET DEFAULT]

);

```
> Declararlo al final de la sentencia
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  FOREIGN KEY (<atributo1>[, <atributo2>, ...])
    REFERENCES <nombretablaareferenciar> (<nombreatributoreferenciado1>,[<atributoreferenciado2>...]>)
    ON DELETE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
    ON UPDATE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
);

```
> Declararlo al final de la sentencia asignandole un nombre a la restricción
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  CONSTRAINT <nombreconstraint>
  FOREIGN KEY (<atributo1>[, <atributo2>, ...])
    REFERENCES <nombretablaareferenciar> (<nombreatributoreferenciado1>,[<atributoreferenciado2>...]>)
    ON DELETE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
    ON UPDATE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
);
```
> Usando Alter
```sql
ALTER TABLE <nombretabla>
 ADD CONSTRAINT <nombreconstraint>
  FOREIGN KEY (<atributo1>[, <atributo2>, ...])
    REFERENCES <nombretablaareferenciar> (<nombreatributoreferenciado1>,[<atributoreferenciado2>...]>)
    ON DELETE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
    ON UPDATE [CASCADE | NO ACTION | SET NULL | SET DEFAULT <x>]
);
```
Para la restricción de clave foránea, se debe indicar la forma en la que se modificarán o borraran los datos en la interrelación:
- NO ACTION (R) : Por Defecto. No altera datos durante el proceso.
- CASCADE (C) : Borra en las tablas donde el dato esté presente.
- SET NULL (N) : Se establecen valores nulos cuando se borran datos.
- SET DEFAULT (D) : Agrega valores por defecto, puede comprometer la integridad de las tablas afectadas.

### -  ``` CHECKS ```
Esta restricción permite limitar los valores que se le pueden indicar a un atributo. Una de las grandes ventajas de los checks es que se pueden realizar en su interior predicados WHERE (siempre y cuando los datos estén en la misma tabla). 


> Indicarla en la propia línea.
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>  CHECK (<predicado> EJ: <atributo1> >= <atributo2>) , ...
[NOT DEFERRABLE | DEFERRABLE]
	         [INITIALLY IMMEDIATE | INITIALLY DEFERRED]
);

```
> Declararlo al final de la sentencia
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  CHECK (<predicado>
[NOT DEFERRABLE | DEFERRABLE]
	         [INITIALLY IMMEDIATE | INITIALLY DEFERRED]
);

```
> Declararlo al final de la sentencia asignandole un nombre a la restricción
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  CONSTRAINT <nombreconstraint>
  CHECK (<predicado>
[NOT DEFERRABLE | DEFERRABLE]
	         [INITIALLY IMMEDIATE | INITIALLY DEFERRED]
);
```
> Usando Alter
```sql
ALTER TABLE <nombretabla>
 ADD CONSTRAINT <nombreconstraint>
  CHECK (<predicado>
[NOT DEFERRABLE | DEFERRABLE]
	         [INITIALLY IMMEDIATE | INITIALLY DEFERRED]
);
```
> 🚩 NOTA IMPORTANTE: LOS PARÁMETROS OPCIONALES INDICAN SI EL CHECK SE EJECUTA INMEDIAMENTE O AL FINAL.

## -  ``` UNIQUE ``` y ``` NOT NULL ```
Restricción que permite que un atributo tenga unicidad, que tome un valor único. Usando UNIQUE + NOT NULL se pueden crear claves alternativas.

> Indicarla en la propia línea.
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1> UNIQUE,
 
);

```
> Declararlo al final de la sentencia
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  UNIQUE (<atributo1>, [<atributo2>...])
);

```
> Declararlo al final de la sentencia asignandole un nombre a la restricción
```sql
CREATE TABLE <nombretabla> (
  <atributo1> <dominio1>,
  <atributo2> <dominio2>,  ...
  CONSTRAINT <nombreconstraint>
  UNIQUE (<atributo1>[, <atributo2>...])
);
```
> Usando Alter
```sql
ALTER TABLE <nombretabla>
 ADD CONSTRAINT <nombreconstraint>
  UNIQUE (<atributo1>[, <atributo2>...])
);
```
## EJEMPLO
Partiendo del siguiente ejercicio hecho en clase, pondremos en práctica las sentencias de los apuntes.

![ejercicio_](./img/ddl/ejercicio.jpeg)

> 1º PASO: Creación de la base de datos.
```sql
 CREATE SCHEMA
       IF NOT EXIST proxectoinvestigacion;
     
```
> 2º PASO: Creación de los dominios
```sql
CREATE DOMAIN Nome_Válido VARCHAR(30);
CREATE DOMAIN Tipo_Código CHAR(5);
CREATE DOMAIN Tipo_DNI    CHAR(9);
     
```
> 3º PASO: Creación de la tabla Sede con sus respectivos campos y la restricción de clave principal
```sql
CREATE TABLE Sede (
  Nome_Sede Nome_Válido,
  Campus    Nome_Válido  NOT NULL,
  CONSTRAINT PK_Sede
    PRIMARY KEY (Nome_Sede)
);
     
```
> 4º PASO: Creación de la tabla Departamento con sus campos con restricciones de clave principal y teléfono no puede ser nulo.
```sql
CREATE TABLE Departamento (
  Nome_Departamento Nome_Válido  PRIMARY KEY,
  Teléfono          CHAR(9)      NOT NULL,
  Director          Tipo_DNI
);
     
```
> 5º PASO: Creación de la tabla Ubicación con sus campos, restriccion de clave principal compuesta, y dos claves foráneas.
```sql
CREATE TABLE Ubicación (
  Nome_Sede         Nome_Válido,
  Nome_Departamento Nome_Válido,
  CONSTRAINT PK_Ubicación
    PRIMARY KEY (Nome_Sede, Nome_Departamento),
  CONSTRAINT FK_Sede
    FOREIGN KEY (Nome_Sede)
    REFERENCES Sede (Nome_Sede)
    ON DELETE CASCADE
    ON UPDATE CASCADE,
  CONSTRAINT FK_Departamento
    FOREIGN KEY (Nome_Departamento)
    REFERENCES Departamento (Nome_Departamento)
    ON DELETE CASCADE
    ON UPDATE CASCADE
);
     
```
> 6º PASO: Creación de la tabla Grupo con sus campos, restriccion de clave principal compuesta, clave foránea, y el atributo área no puede ser nulo.
```sql
CREATE TABLE Grupo (
  Nome_Grupo        Nome_Válido,
  Nome_Departamento Nome_Válido,
  Área              Nome_Válido NOT NULL,
  Lider             Tipo_DNI,
  PRIMARY KEY (Nome_Grupo, Nome_Departamento)
  FOREIGN KEY (Nome_Departamento) REFERENCES Departamento
    ON DELETE CASCADE 
    ON UPDATE CASCADE
);
     
```
> 7º PASO: Creación de la tabla profesor con sus campos, restriccion de clave principal, clave foránea compuesta , y los atributos nome_profesor y titulación no pueden ser nulos.
```sql
CREATE TABLE Profesor (
  DNI            Tipo_DNI    PRIMARY KEY,
  Nome_Profesor  Nome_Válido NOT NULL, 
  Titulación     VARCHAR(20) NOT NULL,
  Experiencia    Integer,
  N_Grupo        Nome_Válido,
  N_Departamento Nome_Válido,
  CONSTRAINT FK_Grupo_Profesor
    FOREIGN KEY      (N_Grupo,    N_Departamento)
    REFERENCES Grupo (Nome_Grupo, Nome_Departamento)
    ON DELETE SET NULL
    ON UPDATE Cascade
);
   
```
> 8º PASO: Creación de la tabla proxecto con sus campos, restriccion de clave principal, clave foránea compuesta , los atributos nome_proxecto,orzamento y data_inicio no pueden ser nulos y unicidad en el atributo Nome_Proxecto.
```sql
CREATE TABLE Proxecto (
  Código_Proxecto Tipo_Código  PRIMARY KEY,
  Nome_Proxecto   Nome_Válido  NOT NULL,
  Orzamento       MONEY        NOT NULL,
  Data_Inicio     DATE         NOT NULL,
  Data_Fin        DATE,
  N_Gr            Nome_Válido,
  N_Dep           Nome_Válido,
  UNIQUE (Nome_Proxecto),
  CONSTRAINT Check_Dates
    CHECK (Data_Inicio < Data_Fin),
  CONSTRAINT FK_Grupo_Proxecto
    FOREIGN KEY (N_Gr, N_Dep)
    REFERENCES Grupo
    ON DELETE SET NULL
    ON UPDATE CASCADE
);
  
```
> 9º PASO: Para tener ejemplos del funcionamiento de la sentencia Alter, la usaremos para agregar una clave foránea en las tablas Departamento y Grupo.
```sql
ALTER TABLE Departamento
  ADD CONSTRAINT FK_Profesor_Departamento
    FOREIGN KEY (Director)
    REFERENCES Profesor (DNI)
    ON DELETE SET NULL
    ON UPDATE CASCADE;

ALTER TABLE Grupo
  ADD CONSTRAINT FK_Profesor_Grupo
    FOREIGN KEY (Lider)
    REFERENCES Profesor (DNI)
    ON DELETE SET NULL
    ON UPDATE CASCADE;
  
```
> 10º PASO: Creación de la tabla participa con sus campos, restriccion de clave principal, clave foránea , los atributos data_inicio y dedicación no pueden ser nulos y un check.
```sql
CREATE TABLE Participa (
  DNI             Tipo_DNI,
  Código_Proxecto Tipo_Código,
  Data_Inicio     DATE        NOT NULL,
  Data_Cese       DATE,
  Dedicación      INTEGER     NOT NULL,
  PRIMARY KEY (DNI, Código_Proxecto),
  CHECK (Data_Inicio < Data_Cese),
  FOREIGN KEY (DNI)
    REFERENCES Profesor (DNI)
    ON DELETE NO ACTION
    ON UPDATE CASCADE
  FOREIGN KEY (Código_Proxecto)
    REFERENCES Proxecto (Código_Proxecto)
    ON DELETE NO ACTION
    ON UPDATE CASCADE
);
  
```
> 11º PASO: Creación de la tabla programa con su campo, restriccion de clave principal.
```sql
CREATE TABLE Programa (
  Nome_Programa Nome_Válido PRIMARY KEY
); 
  
```
> 12º PASO: Creación de la tabla Financia con sus campos, restriccion de clave principal compuesta , los atributos numero_programa y cantidade_financiada no pueden ser nulos.
```sql
CREATE TABLE Financia (
  Nome_Programa        Nome_Válido,
  Código_Proxecto      Tipo_Código,
  Número_Programa      Tipo_Código NOT NULL,
  Cantidade_Financiada MONEY       NOT NULL,
  PRIMARY KEY (Nome_Programa, Código_Proxecto)
);
  
```
> 13º PASO: Como ejemplo de la sentencia Alter, modificamos la tabla Financia y le agregamos dos claves foráneas.
```sql
ALTER TABLE Financia
  ADD CONSTRAINT FK_Proxecto_Financia
    FOREIGN KEY (Código_Proxecto)
    REFERENCES Proxecto
    ON DELETE Cascade
    ON UPDATE Cascade;

ALTER TABLE Financia
  ADD CONSTRAINT FK_Programa_Financia
    FOREIGN KEY (Nome_Programa)
    REFERENCES Programa
    ON DELETE Cascade
    ON UPDATE Cascade;
  ```
