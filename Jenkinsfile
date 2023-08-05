pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/khaitk/config-jenkins-docker.git'
            }
        }

        stage('Build image') {
            dockerImage = docker.build("khraiteka/jenkins-docker:latest")
        }
    
        stage('Push image') {
            withDockerRegistry([ credentialsId: "dockerhubaccount", url: "" ]) {
                dockerImage.push()
            }
        }
    }
}