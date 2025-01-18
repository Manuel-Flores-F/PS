# 02 Lab: 2FA simple bypass

## Objetivo

> 
> 
> 
> This lab's two-factor authentication can be bypassed. You have already obtained a valid username and password, but do not have access to the user's 2FA verification code. To solve the lab, access Carlos's account page.
> 
> - Your credentials: `wiener:peter`
> - Victim's credentials `carlos:montoya`

## Solución

1. Exploramos el inicio de sesión, nos damos cuenta que, en el correo recibimos el OTP para acceder a la web, sin embargo, una vez ingresamos el codigo correcto, accedemos a un *endpoint* , el cual luego verificaremos
    
    [https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/login2](https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/login2) [enlace que pide MFA]
    
    ![image.png](02%20Lab%202FA%20simple%20bypass%2013afab5460ec8094986def3f977334b7/image.png)
    
    ![image.png](02%20Lab%202FA%20simple%20bypass%2013afab5460ec8094986def3f977334b7/image%201.png)
    
    [https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/my-account?id=](https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/my-account?id=carlos)wiener [Pagina de usuario]
    
    ![image.png](02%20Lab%202FA%20simple%20bypass%2013afab5460ec8094986def3f977334b7/image%202.png)
    
2. El endpoint al que accedemos, no hace una validación en la fase del OTP. por lo que si accedemos directamente al endpoint [Página de usuario] habremos evadido el MFA.
    
    > -> Inicio sesión
    -> -> Valido MFA | Genere un token
    -> -> -> Página de usuario | Me verifique el token del paso 2
    > 

[https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/my-account?id=carlos](https://0ab700da0307875c88f942a100f3008a.web-security-academy.net/my-account?id=carlos)

![image.png](02%20Lab%202FA%20simple%20bypass%2013afab5460ec8094986def3f977334b7/image%203.png)

![image.png](02%20Lab%202FA%20simple%20bypass%2013afab5460ec8094986def3f977334b7/image%204.png)