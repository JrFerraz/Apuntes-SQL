# Apuntes SQL-DML
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.

## Índice
- [Qué es el sublenguaje DML](#QUÉ-ES-EL-SUBLENGUAJE-DML)
- [Sentencia INSERT](#INSERT)
- [Sentencia UPDATE](#UPDATE)
- [Sentencia DELETE](#DELETE)
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
- EJEMPLO:
> Agregamos a la tabla alumnos (que tiene los atributos nif, nombre y apellidos) a Adrián Merino con NIF 12345678P, Jacinto Losada con NIF 87654321Q y Maria Corrubedo con NIF 88888888O.
 ```sql
  INSERT INTO alumnos
  (nif, nombre, apellido)
  VALUES
    ('12345678P', 'Adrián', 'Merino'),
    ('87654321Q', 'Jacinto', 'Losada'),
    ('88888888O', 'Maria', 'Corrubedo')
;

```
## UPDATE
Es la sentencia que se utiliza para actualizar los valores de una tupla o añadirlos si esos datos aceptan nulos, dentro de una tabla de una base de datos, con la siguiente sintaxis:
 ```sql
 UPDATE <nombretabla>
       SET <atributo1> = <valor1>,
	   <atributo2> = <valor2>, ...
      [WHERE <predicado>];
	
```
- EJEMPLO:
> Teniendo la tabla alumnos y suponiendo que el atributo apellidos acepta nulos

| NIF               | nombre      | Apellido       |
|-------------------|-------------|----------------|
| 12345678P         | Adrián      | Merino         |
| 87654321Q         | Jacinto     | Losada         |
| 88888888O         | Maria       | Corrubedo      |
| 33333333Q         | Aitana      |                |

> Queremos cambiar el DNI de Maria y ponerle 22222222A , y colocarle un apellido a Aitana.

 ```sql
UPDATE alumnos
  SET NIF = '22222222A'
  WHERE nombre = 'Maria';
  
UPDATE alumnos
  SET Apellido = 'Martínez'
  WHERE NIF = '33333333Q ';
	
```
> La tabla quedaría de la siguiente forma

| NIF               | nombre      | Apellido       |
|-------------------|-------------|----------------|
| 12345678P         | Adrián      | Merino         |
| 87654321Q         | Jacinto     | Losada         |
| 22222222A         | Maria       | Corrubedo      |
| 33333333Q         | Aitana      | Martínez       |

## DELETE
Es la sentencia que se utiliza para borrar datos de las tuplas, dentro de una tabla de una base de datos, con la siguiente sintaxis:
 ```sql
 DELETE FROM <nombretablaabla>
  WHERE <predicado>;
	
```
- EJEMPLO:
> Teniendo la tabla alumnos

| NIF               | nombre      | Apellido       |
|-------------------|-------------|----------------|
| 12345678P         | Adrián      | Merino         |
| 87654321Q         | Jacinto     | Losada         |
| 22222222A         | Maria       | Corrubedo      |
| 33333333Q         | Aitana      | Martínez       |

> Queremos borrar los alumnos que tengan como apellido Merino

 ```sql
 DELETE FROM alumnos
  WHERE Apellido = 'Merino';
	
```
> La Tabla quedaría de la siguiente manera

| NIF               | nombre      | Apellido       |
|-------------------|-------------|----------------|
| 87654321Q         | Jacinto     | Losada         |
| 22222222A         | Maria       | Corrubedo      |
| 33333333Q         | Aitana      | Martínez       |
