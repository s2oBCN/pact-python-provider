pipeline {
    agent {
        docker {
            image 'python:3.9.8-slim-buster'
        }
    }
    parameters { string(name: 'DEPLOY_ENV', defaultValue: 'staging', description: '') }
    environment {
        PACT_BROKER_URL = 'http://172.21.167.170'
    }
     options {
        ansiColor('xterm')
    }
    stages {
        stage('Build') {
            steps {
                sh '/usr/local/bin/python -m pip install --upgrade pip'
                sh 'pip install --no-cache-dir --user -r requirements.txt'
            }
        }
        stage('Verify') {
            steps {
                sh script:'./verify_pact.sh 1'
            }
        }
    }
}
