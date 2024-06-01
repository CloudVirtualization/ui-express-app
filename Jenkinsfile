pipeline {
    agent any
    
    stages {

        stage('Build') {
            steps {
                sh "npm install"
            }
        }

        stage('Unit Test') {
            steps {
                sh "npm test:unit"
            }
        }

        stage('Integration Test') {
            steps {
                sh "npm test:integration"
            }
        }
    }
}