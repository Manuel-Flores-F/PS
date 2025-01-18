# 03 Lab: Web shell upload via path traversal

## Objetivo

> This lab contains a vulnerable image upload function. The server is configured to prevent execution of user-supplied files, but this restriction can be bypassed by exploiting a [secondary vulnerability](https://portswigger.net/web-security/file-path-traversal).
> 
> 
> To solve the lab, upload a basic PHP web shell and use it to exfiltrate the contents of the file `/home/carlos/secret`. Submit this secret using the button provided in the lab banner.
> 
> You can log in to your own account using the following credentials: `wiener:peter`
> 

## Solución

1. Exploramos el inicio de sesión y nos permite subir imagen

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image.png)

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%201.png)

https://0a9f00a50375fb3782ee154f00be0000.web-security-academy.net/files/avatars/04.png

[https://0a9f00a50375fb3782ee154f00be0000.web-security-academy.net/files/avatars/04.png](https://0a9f00a50375fb3782ee154f00be0000.web-security-academy.net/files/avatars/04.png)

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%202.png)

1. `<?php echo file_get_contents('/home/carlos/secret'); ?>`

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%203.png)

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%204.png)

**The server is configured to prevent execution of user-supplied files**

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%205.png)

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%206.png)

Esto era el secrets:

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%207.png)

Observamos el Admin=False

![image.png](03%20Lab%20Web%20shell%20upload%20via%20path%20traversal%2013afab5460ec81d2a701e16e4c87765c/image%208.png)