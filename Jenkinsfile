pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/khaitk/config-jenkins-docker.git'
            }
        }

        stage('Install Package') {
            steps{
                dir('Jenkins/') {
                    echo 'Successful installed'
                }
            }
        }
    }
}