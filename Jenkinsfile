pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    environment {
        JENKINS_URL = "jenkins.learninguser.shop"
    }
    // Build stage
    stages {
        stage('Build'){
            steps {
                sh """
                    echo "${JENKINS_URL}"
                    // to show all environment variables
                    env
                """
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