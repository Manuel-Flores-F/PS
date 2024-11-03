# Lab: Host header authentication bypass

```jsx
This lab makes an assumption about the privilege level of the user based on the HTTP Host header.

To solve the lab, access the admin panel and delete the user carlos.
```

[https://0a3900d804b29449821397ea001500d4.web-security-academy.net/robots.txt](https://0a3900d804b29449821397ea001500d4.web-security-academy.net/robots.txt)

Aqui podemos visualizar que el directorio /admin está oculto

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image.png)

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image%201.png)

Admin interface only available to local users

Este error nos indica que podriamos acceder utilizando el [localhost](http://localhost) como parámetro

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image%202.png)

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image%203.png)

A partir de aqui, nuestras consultas deben tener el parametro host con el valor de localhost

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image%204.png)

![image.png](Lab%20Host%20header%20authentication%20bypass%2090a1ef6e69e54ff585daee91a4d25a02/image%205.png)