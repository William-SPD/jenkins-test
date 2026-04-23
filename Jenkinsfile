pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Webhook triggered successfully'
                sh 'echo hello from jenkins'
            }
        }
    }
    post {
        success {
            githubNotify status: 'SUCCESS', description: 'Build passed'
        }
        failure {
            githubNotify status: 'FAILURE', description: 'Build failed'
        }
    }
}
