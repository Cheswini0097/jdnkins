pipeline {
    agent {
        label 'AGENT-1'
    }

    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
    }

    environment {
        DEBUG = 'true'
        APP_VERSION = '' 
    }

    stages {
        stage('Read the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    env.APP_VERSION = packageJson.version
                    echo "App Version: ${env.APP_VERSION}"
                }
            }
        }

        stage('Install the Dependencies') {
            steps {
                script {
                    sh '''
                        npm install
                        dnf module disable nodejs -y
                        dnf module enable nodejs:20 -y
                        dnf install nodejs -y
                    '''
                }
            }
        }

        stage('Docker build and push') {
            steps {
                script {
                    sh """
                        docker build -t ${backend}:${v2} .
                        docker tag ${backend}:${v2} chethankumar6/backend:v2
                    """
                    sh 'docker push chethankumar6/backend:v2'
                }
            }
        }
    }

    post {
        always {
            echo "Cleaning up workspace..."
            deleteDir() 
        }

        success {
            echo "Pipeline completed successfully!"
        }

        failure {
            echo "Pipeline failed."
        }
    }
}
