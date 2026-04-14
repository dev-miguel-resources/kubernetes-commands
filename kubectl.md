# Kubectl Commands

### 1. Para verificar la versión de nuestro CLI

```
kubectl version
```

### 2. Para listar todos los objetos de mi espacio de trabajo independiente de su tipo

```
kubectl get all
```

### 3. Para listar los pods de mi espacio de trabajo

```
kubectl get pods
kubectl get po
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
```