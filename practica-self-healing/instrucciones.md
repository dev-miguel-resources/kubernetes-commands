🧪 Laboratorio Kubernetes: Self-Healing con Liveness y Readiness Probes
🎯 Objetivos

Al finalizar el laboratorio el alumno podrá:

Entender qué es Self-Healing en Kubernetes
Diferenciar:
Liveness Probe
Readiness Probe
Ver cuándo Kubernetes:
reinicia contenedores
deja de enviar tráfico a Pods no listos
Diagnosticar fallos con:
kubectl get pods
kubectl describe pod
kubectl logs

Parte 1 — Self-Healing básico
Concepto

Self-Healing significa:

Si la app falla, Kubernetes intenta recuperarla automáticamente.

Ejemplos:

contenedor caído → reinicio
probe falla → reinicio
Pod muerto → Deployment crea otro
nodo cae → scheduler reprovisiona

Crear namespace
kubectl create namespace laboratorio-health

Parte 2 — Liveness Probe (reinicio automático)
Objetivo

Provocar una falla y ver cómo Kubernetes reinicia el contenedor.

Parte 4 - Probar Readness Probe
Parte 4 — Readiness Probe (tráfico)
Concepto

Readiness responde:

¿Está listo para recibir requests?

Si falla:

✅ contenedor sigue vivo
❌ Service deja de enviar tráfico

No reinicia.