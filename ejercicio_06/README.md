Ejercicio 06.
===================0
# Caso de uso balanceador

Para este caso se utiliza un archivo de configuración de nginx que permite facilitar la información relacionada con cada app. Para ello se utiliza docker-compose.

- webapp1
- webapp2

Se utiliza el balanceador por default de nginx sobre cada app. A fin de observar mejor la funcionalidad se puede realizar un procedimiento de carga en un endpoint de proesamiento y ver como es posible que el balaceador realiza un switch de carga con los request en cada webapp.

También se utliza una red externa que nos sirve para conectarnos con otros servicios para realizar pruebas.
