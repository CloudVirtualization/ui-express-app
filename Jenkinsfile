pipeline {
    agent any
    environment {
        S3_BUCKET = 'express-js-apps'
    }
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
                sh "npm run test:unit"
            }
        }

        stage('Integration Test') {
            steps {
                sh "npm run test:integration"
            }
        }

        stage('Package') {
            steps {
                sh 'zip -r expressapp.zip *'
            }
        }

        stage('Upload') {
            steps {
                withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'binary-script-creds', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                    sh 'aws s3 cp expressapp.zip s3://${S3_BUCKET}/'
                }    
            }
        }
    }
}