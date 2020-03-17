# Apuntes SQL-DQL
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas funciones de SQL de cara al examen.
## Índice
- [Función WHERE](#WHERE)
	- [Función BETWEEN](#BETWEEN)
	- [Función IN](#IN)
	- [Función JOIN](#JOIN)
		- [Función RIGHT JOIN](#RIGHT-JOIN)
		- [Función LEFT JOIN](#LEFT-JOIN)
- [Función SELECT](#SELECT)
	- [Función DISTINCT](#DISTINCT)
	- [Función SUM](#SUM)
	- [Función AVG](#AVG)
	- [Función COUNT](#COUNT)
	- [Función MAX/MIN](#MAX/MIN)
- [Función NOT NULL](#NOT-NULL)
- [Función ORDER BY](#ORDER-BY)
- [Función GROUP BY](#GROUP-BY)
- [Función AS](#AS)
- [Orden de ejecución](#ORDEN-DE-EJECUCION)
- [Alternativas a in](#ALTERNATIVAS-A-IN)
- [Cómo se escribe que no sea igual (!=)](#COMO-SE-ESCRIBE-QUE-NO-SEA-IGUAL)
- [BETWEEN sin incluir ambos extremos](#BETWEEN-SIN-INCLUIR-AMBOS-EXTREMOS)
- [Uso de caracteres especiales](#USO-DE-CARACTERES-ESPECIALES)
- [Diferencia entre like e igual](#DIFERENCIA-ENTRE-LIKE-E-IGUAL)
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
## AVG
La función SUM se utiliza en el SELECT para reducir a la media los valores de una columna que irá entre paréntesis.

 > Fórmula de ejemplo
 
 ```sql
 SELECT AVG(id)
 FROM departamentos
 
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
## NOT NULL
La función NOT NULL se utiliza para especificar que una columna no acepta valores vacíos.

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre
 FROM profesores
 nombre IS NOT NULL
```
## ORDER BY
La función ORDER BY se utiliza para ordenar los resultados de una consulta, en ASC (ascendente) o DESC (descendente)

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre
 FROM profesores
 ORDER BY nombre ASC
```
## GROUP BY
La función GROUP BY se utiliza para para agrupar tuplas de resultados que coincidan en el valor de la columna a seleccionar. Se suele utilizar junto a funciones agregadas (SUM,COUNT,AVG, MIN, MAX) 

 > Fórmula de ejemplo
 
 ```sql
SELECT pais, SUM(poblacion)
FROM world
GROUP BY pais
```
## AS
La función AS se utiliza para renombrar tablas

 > Fórmula de ejemplo
 
 ```sql
 SELECT nombre
 FROM profesores AS PR
 
```
## ORDEN DE EJECUCION
`1) WHERE`
`2) GROUP BY`
`3) HAVING`
`4) SELECT`

## ALTERNATIVAS A IN 
La función IN se puede poner de otras dos maneras diferentes:
```sql
 WHERE NAME = ‘’ OR NAME = ‘’ OR NAME = ‘’
 
```
o
```sql
 WHERE NAME OR ‘’ LIKE 
 
```
## COMO SE ESCRIBE QUE NO SEA IGUAL 
La forma correcta de escribirlo es con '<>' , la forma incorrecta es !=.
> Fórmula de ejemplo
 
 ```sql
 SELECT alumno 
 FROM colegio
 WHERE nombre <> 'Antonio'
```
## BETWEEN SIN INCLUIR AMBOS EXTREMOS
BETWEEN sin incluir ambos extremos se puede escribir con:
```sql
WHERE NAME >= ‘’ AND NAME <= ‘’
```
## USO DE CARACTERES ESPECIALES
Para el uso de caracteres especiales en las consultas SQL como ' dentro de una cadena o expresión, tiene que ponerse antes /

## DIFERENCIA ENTRE LIKE E IGUAL
La diferencia entre like ‘’ y = ‘’ , es que like es una expresión regular  y = es una cadena
