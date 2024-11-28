pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                sh 'echo hello this is build stage'
            }
        }
        stage('test') {
            steps {
                sh 'echo hello this is the test stage'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo this is deploy step'
            }
        }
    }
}
