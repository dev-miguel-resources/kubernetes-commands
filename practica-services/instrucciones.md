Armar un ejercicio donde trabajen los services de Kubernetes:

ClusterIP -> Comunicación interna de un nodo
NodePort -> exposición externa del cluster mediante puerto del nodo
LoadBalancer -> exposición tipo balanceador externo de cara a internet

Objetivos:
Crear un entorno de trabajo
Trabajar con deployments de Kubernetes
Exponer apps mediante servicios
Comprender las diferencias de dichos servicios
Probar conectividad interna y externa
Analizar ciertos casos de usos reales

Escenario:
Desplegar una app web con nginx con 3 replicas.
Será expuesto mediante todos los tipos de servicios.