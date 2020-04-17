pipeline {
    agent {
        docker {
            image 'node:6-alpine'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'web $env > /etc/hosts'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
    }
}
