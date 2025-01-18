# 01 Lab: Username enumeration via different responses

## Objetivo

> This lab is vulnerable to username enumeration and password brute-force attacks. It has an account with a predictable username and password, which can be found in the following wordlists:
> 
> - [Candidate usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
> - [Candidate passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)
> 
> To solve the lab, enumerate a valid username, brute-force this user's password, then access their account page.
> 

## Solución

1. El inicio de sesión lo mandamos al *INTRUDER*
    
    ![image.png](01%20Lab%20Username%20enumeration%20via%20different%20response%2013afab5460ec8025944beb9d1281cd7b/image.png)
    
2. Asignamos los diccionarios y le damos Iniciar ATAQUE
    
    ![image.png](01%20Lab%20Username%20enumeration%20via%20different%20response%2013afab5460ec8025944beb9d1281cd7b/image%201.png)
    
3. Verificamos las credenciales correctas
    
    ![image.png](01%20Lab%20Username%20enumeration%20via%20different%20response%2013afab5460ec8025944beb9d1281cd7b/image%202.png)
    
    ![image.png](01%20Lab%20Username%20enumeration%20via%20different%20response%2013afab5460ec8025944beb9d1281cd7b/image%203.png)