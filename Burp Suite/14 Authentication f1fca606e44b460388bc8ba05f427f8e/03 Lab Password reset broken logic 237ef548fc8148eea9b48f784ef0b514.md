# 03 Lab: Password reset broken logic

## Objetivo

> This lab's password reset functionality is vulnerable. To solve the lab, reset Carlos's password then log in and access his "My account" page.
> 
> - Your credentials: `wiener:peter`
> - Victim's username: `carlos`

## Solución

Vamos a probar el cambio de contraseña del usuario wiener

![image.png](03%20Lab%20Password%20reset%20broken%20logic%20237ef548fc8148eea9b48f784ef0b514/image.png)

Vemos los correos, el proceso de cambio de contraseña pasa como parametro el usuario, este podemos modificarlo para poder cambiar la contraseña de otros usuarios.

![image.png](03%20Lab%20Password%20reset%20broken%20logic%20237ef548fc8148eea9b48f784ef0b514/image%201.png)

![image.png](03%20Lab%20Password%20reset%20broken%20logic%20237ef548fc8148eea9b48f784ef0b514/image%202.png)

![image.png](03%20Lab%20Password%20reset%20broken%20logic%20237ef548fc8148eea9b48f784ef0b514/image%203.png)

![image.png](03%20Lab%20Password%20reset%20broken%20logic%20237ef548fc8148eea9b48f784ef0b514/image%204.png)