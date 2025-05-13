pipeline {
    agent any
    
    triggers {
        githubPullRequest(
            events: [
                opened(),
                synchronize(),
                reopened()
            ]
        )
    }

    stages {
        stage('PR Build') {
            steps {
                script {
                    // This will only run for PRs
                    if (env.CHANGE_ID) {
                        echo "Building PR #${env.CHANGE_ID}: ${env.CHANGE_TITLE}"
                        echo "Target branch: ${env.CHANGE_TARGET}"
                    }
                }
                checkout scm
                sh 'echo "Running build for branch: ${GIT_BRANCH}"'
                // Add your build/test steps here
            }
        }
    }
    
    post {
        success {
            script {
                if (env.CHANGE_ID) {
                    // Update GitHub PR status
                    updateGitHubCommitStatus(
                        name: "Jenkins CI", 
                        state: "SUCCESS",
                        context: "jenkins-ci/pr"
                    )
                }
            }
        }
        failure {
            script {
                if (env.CHANGE_ID) {
                    updateGitHubCommitStatus(
                        name: "Jenkins CI", 
                        state: "FAILURE",
                        context: "jenkins-ci/pr"
                    )
                }
            }
        }
    }
}
