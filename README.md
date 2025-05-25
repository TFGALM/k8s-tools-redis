# Instalación

1. Crear el namespace donde se quiera instalar redis, en este caso se llama: redis
2. Modificar los id de los manifest para asignar el ID correspondiente de openStack.
3. Ejecutar

```bash
kubectl create namespace redis
kubectl apply -f manifest
helm install redis . -f simple-values.yaml -n redis
```
> Nota: La versión de donde se ha partido para editar el chart ha sido la 19.3.2

# TODO

1. WARNING: There are "resources" sections in the chart not set. Using "resourcesPreset" is not recommended for production. For production installations, please set the following values according to your workload needs:
  - replica.resources
  - master.resources


# Test de la conexión

1. Abrir un port-forwading <code>kubectl port-forward svc/redis-service-name 6379:6379</code>
2. redis-cli -h localhost -p 6379 -a 'PASSWORD_ADMIN'
3. SET mykey "TEST"
4. GET mykey
5. DEL mykey