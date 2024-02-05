pipeline {
    agent {
        node {
            label 'agent-1'
        }
    }
    environment {
        JENKINS_URL = "jenkins.learninguser.shop"
    }
    options {
        timeout(time: 10, unit: 'SECONDS')
        disableConcurrentBuilds()
    }
    parameters {
        parameters {
            choice(name: 'action', choices: ['apply', 'destroy'], description: 'Pick something')
        }
    }
    // Build stage
    stages {
        stage('Build'){
            steps {
                sh """
                    echo "${JENKINS_URL}"
                    env
                """
            }
        }
        stage('Test'){
            steps {
                sh """
                    sleep 2
                """
            }
        }
        stage('Deploy'){
            when {
                expression { 
                    params.action == 'apply'
                }
            }
            input {
                message "Should we continue?"
                ok "Yes, we should."
            }
            steps {
                echo "Hello ${params.PERSON}"
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