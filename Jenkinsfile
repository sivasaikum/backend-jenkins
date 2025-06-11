pipeline {
    agent { label 'STAGE-1'}
    environment {
        PROJECT = 'EXPENSE'
        COMPONENT = 'BACKEND'
        appVersion = ''
    }

    stages {
        stage('Read Json Version') {
            steps {
                script {
                    def JsonRead = readJSON file: 'package.json'
                    appVersion = JsonRead.version
                    echo " Version is $appVersion"
                }
            }
        }

        stage ('Install Dependencies') {
            steps {
                script {
                    sh """
                        npm install
                    """
                }
            }
        }

        stage ('Docker Build') {
            steps {
                script {
                    sh """
                        docker build -t backend:v1.0.0 .
                    """
                }
            }
        }
    }
}