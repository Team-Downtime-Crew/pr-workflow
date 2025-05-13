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
                githubNotify context: 'Jenkins CI', status: 'SUCCESS', description: 'Build passed'
            }
        }
        failure {
            script {
                githubNotify context: 'Jenkins CI', status: 'FAILURE', description: 'Build failed'
            }
        }
    }
}
