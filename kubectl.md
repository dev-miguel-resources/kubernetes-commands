# Kubectl Commands

### 1. Para verificar la versión de nuestro CLI

```
kubectl version
```

### 2. Para listar todos los objetos de mi espacio de trabajo independiente de su tipo

```
kubectl get all
```

### 3. Para listar los pods de mi espacio de trabajo y uno en específico

```
kubectl get pods
kubectl get po
kubectl get po nginx-pod (nombre)
```

### 4. Para crear un pod

```
kubectl run nginx-pod --image=nginx
```

### 5. Para inspeccionar la interna del pod

```
kubectl run describe po nginx-pod
```

### 6. Para hacerle una solicitud interna a un pod desde el cluster

```
kubectl exec -it nginx-pod -- curl localhost
```

### 7. Para disponibilizar un recurso fuera del cluster

```
kubectl expose pod nginx-pod --port=80 --type=NodePort
```

### 8. Para ejecutar un recurso hacia el exterior mediante NodePort

```
kubectl service nginx-pod
```

### 8. Para eliminar un pod

```
kubectl delete po nginx-pod
```

### 9. Para eliminar un servicio

```
kubectl delete service nginx-pod
```

### 10. Para eliminar todos los pods

```
kubectl delete po --all
```

### 11. Para exponer un pod de manera declarativa

```
kubectl apply -f pod.yml
```

### 12. Para eliminar un pod mediante referencia del manifiesto

```
kubectl delete -f pod.yml
```

### 13. Para editar un manifiesto desde terminal

```
kubectl edit po myapp
```

### 14. Para ver el detalle de etiquetas de un pod

```
kubectl get po myapp --show-labels
```

### 14. Para filtar pods mediante etiquetas

```
kubectl get po -l env=dev
kubectl get po -l team=txalcala,run=my-app-nginx,type=backend (filtrado múltiple)
kubectl get po -l run!=nginx-pod3 (filtrado por negación de label)
```

### 15. Para ver el api de objetos de kubernetes
```
kubectl api-resources
```

### 16. Para filtrar una columna del api-resources
```
kubectl api-resources --namespaced=true
kubectl api-resources | findStr apps/v1 (windows)
kubectl api-resources | grep apps/v1 (linux/mac)
```

### 17. Para obtener mayor información de mis pods o de un pod en específico
```
kubectl get po -o wide
kubectl get po nginx-pod2 -o wide
kubectl get po -o wide --show-labels (incorporando las etiquetas)
```

### 18. Para eliminar una o más etiquetas de un pod
```
kubectl label po myapp2 type-
kubectl label po myapp2 env- team- (eliminado múltiple)
```

### 19. Para exportar el resultado de un comando hacia un archivo
```
kubectl get po -o wide --show-labels > pods.txt
```

### 20. Para exponer una aplicación mediante emparejamiento de puertos
```
kubectl port-forward pod/myapp2 8080:80
```

### 21. Para listar los namespaces
```
kubectl get namespaces
```

### 22. Para crear un namespace
```
kubectl create ns dev
```

### 23. Para listar mis namespaces
```
kubectl get ns
```

### 24. Para obtener todos los objetos de un namespace
```
kubectl get all -n dev
```

### 25. Para obtener los nodos sanos
```
kubectl get lease -n kube-node-lease
```

### 26. Para obtener las configuraciones de uso del cluster
```
kubectl get configmaps -n kube-public
```

### 27. Para filtrar una lista de namespaces
```
kubectl get ns | findStr public (windows)
kubectl get ns | grep public (windows)
```

### 27. Para crear un objeto dentro de un namespace
```
kubectl run nginx --image=nginx -n dev
```

### 28. Para obtener todos mis objetos de un determinado namespace
```
kubectl get all -n dev
```

### 29. Para obtener objetos especificos de un namespace
```
kubectl get po -n dev
```

### 30. Para hacer cambio de contexto entre namespaces
```
kubectl config set-context --current --namespace=dev
```

### 31. Para asignar un namespace imperativamente a un manifiesto
```
kubectl apply -f pod.yml -n dev
```

### 32. Para generar la exposición de un recurso de un determinado namespace
```
kubectl port-forward pod/myapp2 8080:80 -n qa
```

### 33. Para eliminar un namespace
```
kubectl delete ns qa
```

### 34. Para disponibilizar un replicaset
```
kubectl apply -f replicaset.yml
```

### 35. Para listar mis replicasets
```
kubectl get replicasets
kubectl get rs
```

### 36. Para eliminar un replicaset
```
kubectl delete rs rs-test
```

### 37. Para filtrar pods asociados a replicasets mediante el selector
```
kubectl get po --selector=app=test
```

### 38. Para visualizar un manifiesto de un replicaset por terminal
```
kubectl get rs rs-test -o yaml
```

### 39. Para escalar la cantidad de replicas de un replicaset
```
kubectl scale rs rs-test --replicas=5
```

### 40. Para lanzar un deployment mediante manifiesto
```
kubectl apply -f deployment.yml
```

### 41. Para listar los deployments
```
kubectl get deployment
kubectl get deployments
kubectl get deploy
```

### 42. Para obtener un deployment especifico
```
kubectl get deployment nginx-deploy
kubectl get deployments nginx-deploy
kubectl get deploy nginx-deploy
```

### 43. Para filtrar deploys por texto y labels
```
kubectl get deploy | findStr 2 (windows)
kubectl get deploy | grep 2 (linux/mac)
kubectl get deploy -l app=deploy
```

### 44. Para inspeccionar un deployment
```
kubectl describe deploy nginx-deploy
```

### 45. Para eliminar un deployment
```
kubectl delete deploy nginx-deploy2
kubectl delete -f deployment.yml
```

### 46. Para verificar el despliegue exitoso de un deploy
```
kubectl rollout status deploy nginx-deploy
```

### 47. Para revisar el historial de versiones de mis deploy
```
kubectl rollout history deploy nginx-deploy
```

### 48. Para hacer un rollback directamente hacia la anterior y a una en específico
```
kubectl rollout undo deploy nginx-deploy
kubectl rollout undo deploy nginx-deploy --to-revision=3
```

### 48. Para modificar directamente la imagen de un deploy
```
kubectl set image deployment/nginx-deploy nginx=nginx:latest --record
record será deprecado en el futuro
```

### 49. Para exponer un pod de un replicaset asociado a un deploy
```
kubectl port-forward pod/nginx-deploy-f576985cc-cntk2 8080:80
```


### 50. Para obtener los nodos disponibles
```
minikube start --nodes 2
```

### 51. Para hacer la verificación de nodos de mis daemonsets
```
kubectl get pods -n logging -o wide
```

### 51. Para listar los daemonsets
```
kubectl get ds log-agent -n logging
```

### 52. Para ver los resultados de logs en tiempo real
```
kubectl logs -f log-agent-2z4jt
```

### 53. Para verificar la persistencia de los logs desde el volumen del contenedor
```
kubectl exec log-agent-2z4jt -- cat /var/log/agent/log.json
```

### 54. Para agregar etiquetas a un objeto
```
kubectl label nodes minikube-m02 disktype=ssd
```

### 55. Para asignar clausulas (tains) a un nodo
```
kubectl taint nodes minikube-m02 env=production:NoSchedule
```

### 56. Para inspeccionar el node y revisar el taint
```
kubectl describe node minikube-m02
```

### 57. Para crear un taint flexible por key y sin value
```
kubectl taint nodes minikube-m03 gpu:NoSchedule
```

### 58. Para evitar asignaciones forzadas a un tolerations
```
kubectl taint nodes server:NoExecute
```

### 59. Para obtener las estadísticas de consumo real de mis nodos
```
kubectl top nodes
```

### 60. Para actualizar en tiempo de ejecución llaves de config-map
```
kubectl edit cm app-config
```

### 61. Para generar un reinicio de un deploy
```
kubectl rollout restart deploy web
```

