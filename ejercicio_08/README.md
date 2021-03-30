Ejercicio 08
===============

En este ejercicio se realiza la ejecución de un bot telegram al cual se conecta la variable de ambiente de su respectivo token.

# Caso 1 clasico env

```
kubectl apply -f ejer8.yml

# ver el feedback

kubectl logs -f pods/ejer8

```

# Caso 2 con secret

```
kubectl apply -f tokensecret.yml

kubectl apply -f ejer8-con-secret.yml

kubectl logs -f pods/ejer8

```
