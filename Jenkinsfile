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
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
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