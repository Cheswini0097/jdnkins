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
        stage('Read the Version') {
            steps {
                script {
                    
                    def packageJson = readJSON file: 'package.json'
                    env.APP_VERSION = packageJson.version
                    echo "App Version from package.json: ${env.APP_VERSION}"
                }
            }
        }
        stage('Build the Docker image'){
            steps {
                sh '''
                docker build -t chethankumar6:v2
                docker images
                '''
            }
        }
    }
}