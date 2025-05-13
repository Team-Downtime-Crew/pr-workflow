pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }

    post {
        success {
            script {
                githubNotify context: 'Jenkins CI', description: 'Build succeeded', status: 'SUCCESS'
            }
        }
        failure {
            script {
                githubNotify context: 'Jenkins CI', description: 'Build failed', status: 'FAILURE'
            }
        }
    }
}
