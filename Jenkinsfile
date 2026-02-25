pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    environment {
        IMAGE_NAME = "jenkins-demo-app"
    }

    stages {

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %IMAGE_NAME% .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop demo-container || exit 0'
                bat 'docker rm demo-container || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:8081 --name demo-container %IMAGE_NAME%'
            }
        }
    }
}
