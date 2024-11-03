# 02 Lab: Blind OS command injection with time delays

## Objetivo

> This lab contains a blind OS command injection vulnerability in the feedback function.
> 
> 
> The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response.
> 
> To solve the lab, exploit the blind OS command injection vulnerability to cause a 10 second delay.
> 

## Solución

1. Evaluamos la sección de Feedback a travez del repeater, los campos `name` y `email`
    
    ![image.png](02%20Lab%20Blind%20OS%20command%20injection%20with%20time%20delays%20132fab5460ec8048bbb8d1e9037ae471/image.png)
    
2. Añadimos `& sleep 10 #` en los campos, con el espacio an inicio, para añadir una instrucción extra, recordemos codificar esta sección CTRL+U, resultando en `+%26+sleep+10+%23`
    
    ![image.png](02%20Lab%20Blind%20OS%20command%20injection%20with%20time%20delays%20132fab5460ec8048bbb8d1e9037ae471/image%201.png)