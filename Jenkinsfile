pipeline {
    agent any
    stages {
        stage('Hello') {
            steps {
                echo 'Webhook triggered successfully'
                sh 'echo hello from jenkins'
                error 'Simulated failure'
            }
        }
    }
    post {
        success {
            githubNotify credentialsId: 'github-token',
                         account: 'William-SPD',
                         repo: 'jenkins-test',
                         sha: env.GIT_COMMIT,
                         status: 'SUCCESS',
                         description: 'Build passed'
        }
        failure {
            githubNotify credentialsId: 'github-token',
                         account: 'William-SPD',
                         repo: 'jenkins-test',
                         sha: env.GIT_COMMIT,
                         status: 'FAILURE',
                         description: 'Build failed'
        }
    }
}
