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
        appVersion = ''
    }
    stages {
        stage('Read the Version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = package.Json.version
                    echo "App Version: ${appVersion}"
                    echo "App Version: ${env.APP_VERSION}"
                }
            }
        }
    }
}