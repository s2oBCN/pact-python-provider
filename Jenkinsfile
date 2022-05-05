pipeline {
    agent {
        docker {
            image 'python:3.10.4-slim-bullseye'
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
               // cleanWs()
              //  checkout scm
               // sh 'python3 -m venv environment'
               // sh 'python3 source environment/bin/activate'
                sh 'pip install --user --no-cache-dir -r requirements.txt'
            }
        }
        stage('Verify') {
            steps {
                sh script:'./verify_pact.sh 1'
            }
        }
    }
}
