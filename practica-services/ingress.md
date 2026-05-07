Usaremos:

webapp-clusterip como backend.

Paso 1 - Habilitar ingress controller en minikube

minikube addons list

Ejecutar:
minikube addons enable ingress

Verificamos:

kubectl get pods -n ingress-nginx

Ese Pod es el portero.

kubectl apply -f ingress.yml

kubectl get ing -n laboratorio-services

Buscamos la siguiente dirección y registramos en hosts
C:\Windows\System32\drivers\etc\hosts

Agregamos:
127.0.0.1 webapp.local

Luego, ejecutamos: curl http://webapp.local
para ver como responde el tráfico interno.