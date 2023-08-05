docker build -t jenkins-docker .

docker run -p 8081:8080 -p 50000:50000 --restart=on-failure -d -v jenkins_home:/var/jenkins_home jenkins-docker