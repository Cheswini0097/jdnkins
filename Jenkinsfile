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
    stages {
        stage('Read the version'){
            steps {
                script
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
