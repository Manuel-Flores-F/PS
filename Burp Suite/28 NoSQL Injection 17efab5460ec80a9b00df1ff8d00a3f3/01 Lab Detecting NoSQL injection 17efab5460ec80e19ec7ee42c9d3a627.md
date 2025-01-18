# 01 Lab: Detecting NoSQL injection

## Objetivo

> The product category filter for this lab is powered by a MongoDB NoSQL database. It is vulnerable to NoSQL injection.
> 
> 
> To solve the lab, perform a NoSQL injection attack that causes the application to display unreleased products.
> 

## Solución

En el repeater inyectamos un payload, el cuál a traves de los errores, no s muestre que es NoSQL

```bash
Gifts'%2b||1||%2b'
```

![Untitled](01%20Lab%20Detecting%20NoSQL%20injection%2017efab5460ec80e19ec7ee42c9d3a627/Untitled.png)

#