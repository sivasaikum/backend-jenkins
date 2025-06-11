pipeline {
    agent { label 'STAGE-1'}
    environment {
        PROJECT = 'EXPENSE'
        COMPONENT = 'BACKEND'
        appVersion = ''
        ACC_ID = '344060441143'
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
                    withAWS(region: 'us-east-1', credentials: 'aws-cred') {
                        sh """
                            aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com
                        """
                    }
                    
                }
            }
        }
    }
}