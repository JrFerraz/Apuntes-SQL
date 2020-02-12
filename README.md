# Apuntes SQL-DQL

## Índice
- [Función WHERE](#WHERE)
	- [Función BETWEEN](#BETWEEN)

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
