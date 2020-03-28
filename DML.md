# Apuntes SQL-DML
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.

## Índice
- [Qué es el sublenguaje DML](#QUÉ-ES-EL-SUBLENGUAJE-DML)
- [Sentencia INSERT](#INSERT)
## QUÉ ES EL SUBLENGUAJE DML
EL ```DML``` (Data Manipulation Language) permite dentro de un sistema gestor de base de datos llevar a cabo tareas de consulta o de modificación/eliminación de los datos de una base de datos.

Las tres principales sentencias dentro de este sublenguaje son:
- ```INSERT```
- ```UPDATE```
- ```DELETE```

## INSERT
Es la sentencia que se utiliza para agregar tuplas a una tabla dentro de una base de datos con la siguiente sintaxis:
 ```sql
  INSERT INTO <nombretabla>
	    [(<atributoA>, <atributoB> ...]
	    VALUES
		(<valor1A>, <valor1B>, <valor1X>),
		(<valor2A>, <valor2B>, <valor2X>), ...
	;
```
> EJEMPLO: Agregamos a la tabla alumnos (que tiene los atributos nif, nombre y apellidos) a Adrián Merino con NIF 12345678P, Jacinto Losada con NIF 87654321Q y Maria Corrubedo con NIF 88888888O.
 ```sql
  INSERT INTO alumnos
  (nif, nombre, apellidos)
  VALUES
    ('12345678P', 'Adrián', 'Merino'),
    ('87654321Q', 'Jacinto', 'Losada'),
    ('88888888O', 'Maria', 'Corrubedo')
;

```
