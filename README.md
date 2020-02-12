# Apuntes SQL-DQL
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.
## Índice
- [Función WHERE](#WHERE)
	- [Función BETWEEN](#BETWEEN)
	- [Función IN](#IN)
	- [Función JOIN](#JOIN)
		- [Función RIGHT JOIN](#RIGHT JOIN)
		- [Función LEFT JOIN](#LEFT JOIN)
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

## INNER JOIN
La función INNER JOIN o JOIN se utiliza para combinar varias filas de varias tablas distintas a través de las claves principales o foráneas.

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre, departamento
 FROM profesores JOIN departamentos ON iddep.profesores = id.departamentos
 WHERE departamento = 'ciencias'
```
## RIGHT JOIN
La función RIGHT JOIN es lo mismo que INNER JOIN con la diferencia que los datos de la columna derecha aparecen aunque los de la izquierda sean nulos.

## LEFT JOIN
La función LEFT JOIN es lo mismo que INNER JOIN con la diferencia que los datos de la columna izquierda aparecen aunque los de la derecha sean nulos.