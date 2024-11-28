pipeline {
    agent {
        label 'AGENT-1'
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo This is the build stage'
            }
        }
        stage('Test') {
            steps {
                sh 'echo This is the test stage'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo This is the deployment stage'
            }
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
