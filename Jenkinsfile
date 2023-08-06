pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage('Clone') {
            steps {
                git branch: 'develop', credentialsId: 'github', url: 'https://github.com/khaitk/config-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {         
            steps{                
	            sh 'docker build -t khraiteka/jenkins-docker:$BUILD_NUMBER .'           
                echo 'Build Image Completed'                
            }           
        }

        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push khraiteka/jenkins-docker:$BUILD_NUMBER'
            }
        }
    }
}