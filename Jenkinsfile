pipeline {
    agent any
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
    }
}