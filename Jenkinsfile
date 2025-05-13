pipeline {
    agent any
    
    stages {
        stage('Build & Test') {
            steps {
                echo 'Building...'
                // Add your build commands here
                // Example: sh 'mvn clean package'
                
                echo 'Running Tests...'
                // Add your test commands here
            }
        }
        stage('Code Quality') {
            steps {
                echo 'Running Code Analysis...'
                // Add code quality checks here
            }
        }
    }
    
    post {
        success {
            // This will mark the PR as successful in GitHub
            updateGitHubCommitStatus name: "Jenkins CI", state: "SUCCESS"
        }
        failure {
            // This will mark the PR as failed in GitHub
            updateGitHubCommitStatus name: "Jenkins CI", state: "FAILURE"
        }
    }
}
