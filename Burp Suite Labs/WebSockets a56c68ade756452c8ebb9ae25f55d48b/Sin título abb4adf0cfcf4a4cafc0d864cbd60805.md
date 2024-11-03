# Sin título

**Lab: Manipulating WebSocket messages to exploit vulnerabilities**

```jsx
This online shop has a live chat feature implemented using WebSockets.

Chat messages that you submit are viewed by a support agent in real time.

To solve the lab, use a WebSocket message to trigger an alert() popup in the support agent's browser.
```

![image.png](Sin%20ti%CC%81tulo%20abb4adf0cfcf4a4cafc0d864cbd60805/image.png)

Vamos a probar payloads para ejecutar un alert en el navegador del Hal Pline, la idea es que, cuando se acceda al chat, se lance automaticamente el alert, por eso usamos como pruea el img, para que en el chat quede un archivo

```jsx
<img src='' onerror='alert()'>
```

![image.png](Sin%20ti%CC%81tulo%20abb4adf0cfcf4a4cafc0d864cbd60805/image%201.png)

![image.png](Sin%20ti%CC%81tulo%20abb4adf0cfcf4a4cafc0d864cbd60805/image%202.png)

![image.png](Sin%20ti%CC%81tulo%20abb4adf0cfcf4a4cafc0d864cbd60805/image%203.png)

![image.png](Sin%20ti%CC%81tulo%20abb4adf0cfcf4a4cafc0d864cbd60805/image%204.png)