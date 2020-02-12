# Apuntes SQL-DQL
> Estos apuntes han sido preparados recopilando información en clase y por mi cuenta para facilitarme el entendimiento de las distintas fórmulas de cara al examen.
## Índice
- [Función WHERE](#WHERE)
	- [Función BETWEEN](#BETWEEN)
	- [Función IN](#IN)

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
