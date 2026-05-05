Laboratorio: ConfigMap + Secrets + Variables de entorno + Montaje de volúmenes

Escenario:

Tenemos una app que necesita:

Configuración pública (ConfigMap):

nombre app
ambiente
puerto
archivo de configuración

Configuración sensible (Secret):

usuario bd
password bd
API Key

La app leerá:

variables de entorno
archivos montados en volumen