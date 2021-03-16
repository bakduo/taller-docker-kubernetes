Resumen de sentencias:
===========================

# HEALTHCHECK: 

Me permite generar un *daemon de salud* a partir de la versión 1.12, a fin de ejecutar un comando que verifique el funcionamiento de un servicio durante un tiempo determinado y una cantidad de reintentos finitos.

Un template de uso válido:

HEALTHCHECK [options] CMD <command>

Ejemplo:

```
HEALTHCHECK --interval==1m --timeout=3s CMD "comando"
```

Siendo comandó un script o simplemente un comando de consola realizando una tarea de check sobre un servicio activo.

Esta sentencia se puede agregar en el Dockerfile. Es posible ver el estado del servicio por medio de *docker container inspect name* o también más accesible por medio de *docker ps* para ver la leyenda del servicio con el resultado de *salud*.

Este último comando nos muestra un estado *unhealthy* si nuestro servicio no esta saludable, con los detalles como: la marca de tiempo de inicio y fin, así como la respuesta de salida.

También es posible utilizarlo por medio de cmdline cli en lugar de declarativo, como en el siguiente ejemplo:

```
sudo docker run --rm -d --health-cmd='$comando' namecontainer
```

# ONBUILD

Me permite ejecutar un tarea como *trigger* al construir una imagen nueva que utilice un from de una imagen base que soporte *ONBUILD*. Se puede ver como un concepto de herencia en la cual ejecutó la instrucción super de la implementación original en lugar de self, con la diferencia que aquí se ejecuta siempre, con cada invocación de construcción de la imagen base original.

```
IMAGEN X
ONBUILD RUN echo "IMAGEN que soporte onbuild"


IMAGEN Y
FROM X
```

Al construir esta imagen *Y* se ejecuta el trigger que corresponde con el comando de la sentencia ONBUILD de la imagen X.

Puede ser útil a la hora de construir imágenes con capas de dependencias o tambien para realizar algún test de implementación.


# VOLUMES
Esta sentencia permite al contenedor agregar persistencia y también dar acceso a los datos al servicio que se esté ejecutando.

```
VOLUMES ["dir","file",...]. 
```

Permite ingresar una cantidad finita de recursos de acceso, a fin de exponer y realizar un enlace hacia archivos/directorios, similar al comando mount de GNU/Linux. Su uso es útil por ejemplo en caso de uso de una DB, en la cual necesito guardar los datos en un directorio en un tier de disco determinado, de forma tal que me permita mantener la información del servicio luego de destruir el contenedor. Otro caso podría ser el ingreso de configuración de una aplicación, por ejemplo se puede centralizar un directorio donde los servicios que se ejecutan en distintos contenedores lean un directorio particular centralizado al que todos tengan acceso y lograr configurar lo justo y necesario para funcionar, puede ser un archivo.properties, un certificado de acceso, el resultado de un repo modificado y también es posible utilizarlo como acceso hacia un mapeo de logs de servicio.

