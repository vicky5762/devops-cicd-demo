pipeline {
    agent any

    environment {
        APP_NAME = "devops-cicd-demo"
        DEPLOY_ENV = "production"
        BUILD_VERSION = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/vicky5762/devops-cicd-demo.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME} version ${BUILD_VERSION}"
                sh 'echo Compiling application'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                sh 'echo Test execution complete'
            }
        }

        stage('PR Validation') {
            when {
                not { branch 'main' }
            }
            steps {
                echo "Pull Request validation successful"
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying ${APP_NAME} to ${DEPLOY_ENV}"
                sh 'echo Deployment finished'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully"
        }
        failure {
            echo "Pipeline failed"
        }
    }
}