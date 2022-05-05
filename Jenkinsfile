pipeline {
    agent {
        docker {
            image 'python:3.10.4-bullseye'
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
                sh 'python3 -m pip install --upgrade pip'
                sh 'pip3 install virtualenv'
                sh 'sudo virtualenv enviroment_name -p python3'
                sh 'source enviroment_name/bin/activate'
                sh 'pip install --no-cache-dir -r requirements.txt --user'
            }
        }
        stage('Verify') {
            steps {
                sh script:'./verify_pact.sh 1'
            }
        }
    }
}
