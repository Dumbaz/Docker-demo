1. Apache 2.2 in einem Container
2. Volumes / Mounts
3. Apache 2.2 und 2.4 im Parallelbetrieb

4. Elasticsearch Container
5. Filebeat Sidecar Container zu Apache
6. Kibana Container

0. Docker Machine (z.B auf Windows und Mac)
Wenn keine native Möglichkeit besteht, Docker zu betreiben kommt die Docker-Machine zum Einsatz. Es ist eine virtuelle Maschine, welche den Kernel und die Docker Software bereitstellt. `docker-machine ip`

1. Apache 2.2 in einem Container
```
cd apache22
docker build -t apache22 .
# Aus den Inhalten des Ordners "Dockerfile" baue ein Image und vergebe den Tag "apache22"
docker run -dit --name apache22-1 -p 8080:80 apache22
# Starte einen Container mit dem Namen apache22-1 aus dem Image apache22. \
#   Forwarde den Port 80 des Containers auf localhost:8080
```

2. Volumes / Mounts
Problem: Docker Container sind flüchtig. Sie enthalten nur 1 Prozess, bei Beendigung desselben ist der Container auch nicht mehr vorhanden.
```
docker volume create --name ApacheData
docker run -ti --rm -v ApacheData:/apacheData centos
# Volume ApacheData wird gemounted nach /apacheData
```

```
# Im Container:
echo "Hallo, Welt" > /apacheData/test.txt
cat /apacheData/test.txt
exit
```

# Außerhalb des Containers
```
docker volume inspect ApacheData
docker run -ti --rm -v ApacheData:/apacheData centos
cat /apacheData/test.txt
```

3. Apache 2.2 und 2.4 im Parallelbetrieb
```
cd apache24
docker build -t apache24 .
docker image ls
```
