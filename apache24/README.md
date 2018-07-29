Step 1:
`docker build -t my-apache2 .` 

Build a container-image tagged "my-apache2" from the Dockerfile in the directory


Step 2:
`docker run -dit --name my-running-app -p 8080:80 my-apache2`

Run a container from my-apache2 and call it "my-running-app". Expose the container port 80 to your localhost 8080

`docker ps`

```
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
1cba5c30bc8d        my_apache24         "httpd-foreground"   6 seconds ago       Up 6 seconds        0.0.0.0:8080->80/tcp   my-running-httpd
```
