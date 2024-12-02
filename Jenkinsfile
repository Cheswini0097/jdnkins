pipeline {
    agent {
        label 'AGENT-1'
    }
    oprtions{
        timeout(time: 30, unit: 'MINUTES')
        disableConcurentbuilds()
    }
    envinorment {
        DEBUG = 'true'
        appVersion = ''
        }
    stage('Read the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    def appVersion = packageJson.version
                    echo "AppVersion: ${appVersion}"
                }
            }
        }
        stage('Install the Depndenceies') {
            steps {
                sh 'npm install'
                dnf module disable nodejs -y
                dnf module enable nodejs:20 -y
                dnf install nodejs -y
            }
        }
       
    post {
        always {
            echo "This section runs always"
            deleteDir()
        }
        success {
            echo "This section runs when the pipeline succeeds"
        }
        failure {
            echo "This section runs when the pipeline fails"
        }
    }
}
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
        APP_VERSION = '' // Use consistent casing for environment variables
    }

    stages {
        stage('Read the version') {
            steps {
                script {
                    // Read package.json and extract the version
                    def packageJson = readJSON file: 'package.json'
                    env.APP_VERSION = packageJson.version
                    echo "App Version: ${env.APP_VERSION}"
                }
            }
        }

        stage('Install the Dependencies') {
            steps {
                script {
                    // Use shell commands to install dependencies and update Node.js
                    sh '''
                        npm install
                        dnf module disable nodejs -y
                        dnf module enable nodejs:20 -y
                        dnf install nodejs -y
                    '''
                }
            }
        }
        stage('Docker build and push'){
            steps {
                sh """
                docker build -t ${backend}:${v2} .
                docker tag ${backend}:${v2} . chethankumar6/backend:v2
                """
                docker push ${chethankumar6/backend:v2}
            }
        }

    post {
        always {
            echo "Cleaning up workspace..."
            deleteDir() // Deletes the workspace directory
        }

        success {
            echo "Pipeline completed successfully!"
        }

        failure {
            echo "Pipeline failed."
        }
    }
}
