Ejercicio 07
=================
En este ejemplo se realiza la ejecución de tres instancias de password api a la cual se realizar un attach de servicio.

```
# Deploy ejer7

kubectl apply -f deployment/ejer7.yml

# Run service sobre el puerto 8082

kubectl apply -f service/service-ejer7.yml

# Mostrar los endpoints que a los que dispara el servicio

kubectl get endpoints

```

Para realizar un check del servicio es necesario ejecutar una instancia que tenga acceso al rango de direccionamiento virtual.


