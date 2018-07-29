1. Apache 2.2 in einem Container
2. Volumes / Mounts
3. Apache 2.2 und 2.4 im Parallelbetrieb

4. Elasticsearch Container
5. Filebeat Sidecar Container zu Apache
6. Kibana Container

1. Apache 2.2 in einem Container
```
cd apache22
docker build -t apache22 .
# Aus den Inhalten des Ordners "Dockerfile" baue ein Image und vergebe den Tag "apache22"
docker run -dit --name apache22-1 -p 8080:80 apache22
# Starte einen Container mit dem Namen apache22-1 aus dem Image apache22. \
#   Forwarde den Port 80 des Containers auf localhost:8080
```


