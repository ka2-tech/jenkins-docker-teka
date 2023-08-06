## Docker

```angular2html
docker build -t jenkins-docker .
```

```angular2html
docker run -p 8081:8080 -p 50000:50000 --restart=on-failure -d -v jenkins:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkins-docker
```

```angular2html
docker kill $(docker ps -q)
```

```angular2html
docker rm $(docker ps -a -q)
```

```angular2html
docker rmi $(docker images -q)
```