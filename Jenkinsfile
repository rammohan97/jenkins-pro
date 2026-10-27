pipeline {
    agent {
        node { label 'agent-1' }
    }
    environment {
        COURSE_NAME = 'Jenkins'
    }
    options {
        timeout (time: 10, unit: 'MINUTES')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Ram', description: 'Enter your name')
        text(name: 'TEXT', defaultValue: 'Hello', description: 'Enter your text')
        booleanParam(name: 'DEPLOY', defaultValue: false, description: 'Check the box if you want to proceed')
        choice(name: 'CHOICE', choices: ['Option 1', 'Option 2', 'Option 3'], description: 'Select an option')
        password(name: 'PASSWORD', defaultValue: 'password', description: 'Enter your password')
    }


    stages {
        stage ('Build') {
            steps {
                echo 'Building...'
            }
        }
        stage ('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage ('Parameters Display') {
            script {
                sh """
                    echo "Hello ${params.PERSON}"
                    echo "Text: ${params.TEXT}"
                    echo "Toogle: ${params.DEPLOY}"
                    echo "Choice: ${params.CHOICE}"
                    echo "Password: ${params.PASSWORD}"
                """
            }
        }
        stage ('Deploy') {
            /* input {
                message "Do you want to deploy?"
                ok "Yes, I want to deploy"
                submitter "admin"
                parameters {
                    string(name: 'DEPLOY_ENV', defaultValue: 'dev', description: 'Enter the deployment environment')
                }
            } */
            when {
                expression { return params.DEPLOY }
            }


            steps {
                echo 'Deploying...'
            }
        }
    }
}