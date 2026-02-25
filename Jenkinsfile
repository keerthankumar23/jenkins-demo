pipeline {
    agent any

    tools {
        maven 'Maven-3'
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }
    }
}
