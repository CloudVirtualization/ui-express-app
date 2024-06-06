pipeline {
    agent any
    tools {
        nodejs '18.17.0'
    }
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