pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    // Build stage
    stages {
        stage('Build'){
            steps {
                echo 'Building...'
            }
        }
        stage('Test'){
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy'){
            steps {
                echo 'Deploying...'
            }
        }
    }
    // post build
    post {
        always {
            echo "I will always run"
        }
        success {
            echo "Runs only if pipeline is succeded"
        }
        failure {
            echo "Runs only if pipeline is failed"
        }
        changed {
            echo "Runs only if there is change in state compared to previous"
        }
    }
}