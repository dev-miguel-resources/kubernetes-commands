Parte 6 - Ver balanceos

Entrar a los pods:

kubectl get po -n laboratorio-services -o wide

Pod 1:

kubectl exec -it webapp-59b8959f79-s4d5p -n laboratorio-services -- sh
echo "POD1" > /usr/share/nginx/html/index.html

Pod 2:
kubectl exec -it webapp-59b8959f79-v2qvr -n laboratorio-services -- sh
echo "POD2" > /usr/share/nginx/html/index.html

Pod 3:
kubectl exec -it webapp-59b8959f79-ww4nl -n laboratorio-services -- sh
echo "POD3" > /usr/share/nginx/html/index.html

Ahora viene la prueba real
Prueba contra el Service, no directo a la IP del Pod
ClusterIP
wget -qO- webapp-clusterip
wget -qO- webapp-clusterip
wget -qO- webapp-clusterip
Podrías ver:
POD1
POD3
POD2

NodePort:
wget -qO- http://192.168.49.2:30080

Ejemplo:

miempresa.cl

resulve a: 200.50.10.20

esa IP es la del load balancer

Su trabajo:
"Recibo tráfico de afuera y lo ingreso al cluster".

La idea es por consiguiente, incorporar un Ingress = portero inteligente dentro del cluster

Una vez que el tráfico entró:

Ingress mira:

hostname
path
headers
TLS
redirecciones

Ejemplos:
Si llega:
empresa.cl/login
manda a:
auth-service

Si llega:
empresa.cl/pagos

manda a:
payment-service

Si llega:
empresa.cl/admin

manda a:
admin-service

Casa:

calle -> reja principal -> conserje -> departamento correcto

En Kubernetes: Internet -> Load balancer -> Ingress -> Service -> Pod
Pruebas locales: Internet -> NodePort -> Ingress -> Service -> Pod

"El LoadBalancer da la cara a internet; el Ingress, dentro del cluster, recibe ese tráfico y decide
a que servicio interno enviarlo".