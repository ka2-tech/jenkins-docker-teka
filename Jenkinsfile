pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/khaitk/config-jenkins-docker.git'
            }
        }

        stage('Build Docker Image') {         
            steps{                
                script {
                    def customImage = docker.build("khraiteka/jenkins-docker:$BUILD_NUMBER")
                    customImage.push()
                }  
                echo 'Build Image Completed'             
            }           
        }
    }
}