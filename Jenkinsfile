pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Lint') {
            steps {
                echo "Running code lint checks..."
                sh 'echo "Pretend linter here"'
            }
        }
        stage('Unit Tests') {
            steps {
                echo "Running unit tests..."
                sh 'echo "Pretend tests running"'
            }
        }
        stage('Build') {
            steps {
                echo "Building the application..."
                sh 'echo "Pretend build here"'
            }
        }
    }
    post {
        success {
            echo "Jenkins validation PASSED"
        }
        failure {
            echo "Jenkins validation FAILED"
        }
    }
}
