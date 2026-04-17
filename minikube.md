# Minikube Commands

### 1. Para verificar la versión instalada

```
minikube version
```

### 2. Para arrancar el cluster de Minikube

```
minikube start
```

### 3. Para verificar el status de los componentes del cluster

```
minikube status
```

### 4. Para detener el cluster mi minikube

```
minikube stop
```

### 5. Para eliminar el cluster mi minikube

```
minikube delete
```

### 6. Para eliminar un cluster corrupto y dejarlo limpio para un nuevo levantamiento

```
minikube delete --all --purge
```

### 6. Para obtener la ip actual del nodo de minikube

```
minikube ip
```

### 7. Para obtener la lista de comandos de minikube

```
minikube --help
```

### 8. Para obtener la lista de comandos de arranque de minikube

```
minikube start --help
```

### 9. Para obtener la lista de plugins (complementos)

```
minikube addons list
```

### 10. Para acceder a la terminal del cluster mediante ssh

```
minikube ssh
```

### 11. Para levantar un cluster con una x cantidad de nodos

```
minikube start --nodes 2
```

### 12. Para conectarme a un nodo especifico por terminal

```
minikube ssh -n minikube-m02
```