pipeline {
    agent {
        docker {
            image 'python:3.9.8-slim-buster'
        }
    }
    parameters { string(name: 'DEPLOY_ENV', defaultValue: 'staging', description: '') }
    environment {
        PACT_BROKER_URL = 'http://172.29.240.1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'pip install --no-cache-dir -r requirements.txt'
            }
        }
        stage('Verify') {
            steps {
                sh script:'./verify_pact.sh 1'
            }
        }
    }
}