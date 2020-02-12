# Apuntes SQL-DQL
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.
## Índice
- [Función WHERE](#WHERE)
	- [Función BETWEEN](#BETWEEN)
	- [Función IN](#IN)
	- [Función JOIN](#JOIN)
		- [Función RIGHT JOIN](#RIGHT_JOIN)
		- [Función LEFT JOIN](#LEFT_JOIN)
- [Función SELECT](#SELECT)
	- [Función DISTINCT](#DISTINCT)
	- [Función SUM](#SUM)
	- [Función COUNT](#COUNT)
	- [Función MAX/MIN](#MAX/MIN)
- [Función NOT NULL](#NOT_NULL)
## WHERE
La función WHERE se utiliza para hacer filtrar en las consultas, seleccionar las tablas que cumplan la condición deseada.

 > Fórmula de ejemplo
 
 ```sql
 SELECT alumno 
 FROM colegio
 WHERE nombre = 'Antonio'
```

## BETWEEN
La función BETWEEN se utiliza dentro del WHERE y se usa para filtrar valores dentro de un rango de datos.

 > Fórmula de ejemplo
 
 ```sql
 SELECT alumno 
 FROM colegio
 WHERE nombre 
 BETWEEN 'Antonio' AND 'Raquel'
```
## IN
La función IN se tiene que utilizar dentro del WHERE y se usa para seleccionar varios valores, entre paréntesis y separados por comas.
 > 🚩IMPORTANTE: SE DEBEN USAR COMILLAS SIMPLES Y NO COMILLAS DOBLES, SUELE DAR ERROR!

 > Fórmula de ejemplo
 
 ```sql
 SELECT alumno 
 FROM colegio
 WHERE nombre 
 IN ('Antonio, Rosalía, Raquel)
```

## INNER_JOIN
La función INNER JOIN o JOIN se utiliza para combinar varias filas de varias tablas distintas a través de las claves principales o foráneas.

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre, departamento
 FROM profesores JOIN departamentos ON iddep.profesores = id.departamentos
 WHERE departamento = 'ciencias'
```
## RIGHT_JOIN
La función RIGHT JOIN es lo mismo que INNER JOIN con la diferencia que los datos de la columna derecha aparecen aunque los de la izquierda sean nulos.

## LEFT_JOIN
La función LEFT JOIN es lo mismo que INNER JOIN con la diferencia que los datos de la columna izquierda aparecen aunque los de la derecha sean nulos.

## SELECT
La función SELECT se utiliza para mostrar en la consulta SQL las columnas que queremos consultar de una tabla.

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre
 FROM profesores
```
## DISTINCT
La función DISTINCT se utiliza en el SELECT para evitar que se repitan los valores en una columna.

 > Fórmula de ejemplo
 
 ```sql
 SELECT DISTINCT nombre
 FROM profesores
 
```
## SUM
La función SUM se utiliza en el SELECT para obtener una suma de totales de los valores de una columna que irá entre paréntesis.

 > Fórmula de ejemplo
 
 ```sql
 SELECT SUM(nombre)
 FROM profesores
 
```
## COUNT
La función COUNT se utiliza en el SELECT para devolver el numero de filas que se usan en una consulta. la columna que se usará para esta función tiene que ir entre paréntesis

 > Fórmula de ejemplo
 
 ```sql
 SELECT COUNT(nombre)
 FROM profesores
 
```
## MAX/MIN
La función MAX o MIN  se utiliza en el SELECT para el valor mayor o menor en una columna. Dicha columna tiene que ir entre paréntesis.

 > Fórmulas de ejemplo
 
 ```sql
 SELECT MAX(id)
 FROM departamento
 
```
 ```sql
 SELECT MIN(id)
 FROM departamento
 
```
## NOT_NULL
La función NOT NULL se utiliza para especificar que una columna no acepta valores vacíos.

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre
 FROM profesores
 nombre IS NOT NULL
```
