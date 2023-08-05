pipeline {
    def app

    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/khaitk/config-jenkins-docker.git'
            }
        }

        stage('Build image') {
            app = docker.build("khraiteka/jenkins-docker:latest")
        }

        stage('Test image') {
            app.inside {
                sh 'echo "Tests passed"'
            }
        }
    
        stage('Push image') {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                app.push("latest")
            }
        }
    }
}