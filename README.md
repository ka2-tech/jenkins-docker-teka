docker build -t jenkins-docker .

docker run -p 8081:8080 -p 50000:50000 --restart=on-failure -d -v jenkins:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkins-docker

docker kill $(docker ps -q)
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)