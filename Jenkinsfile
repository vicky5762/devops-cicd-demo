pipeline {
    agent any

    environment {
        APP_NAME = "devops-cicd-demo"
        DEPLOY_ENV = "production"
        BUILD_VERSION = "${env.BUILD_NUMBER}"
    }

    stages {

        stage('Build') {
            steps {
                echo "Building ${APP_NAME} version ${BUILD_VERSION}"
                sh 'echo compiling code'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests"
                sh 'echo test execution'
            }
        }

        stage('PR Validation') {
            when {
                not { branch 'main' }
            }
            steps {
                echo "PR validation successful"
            }
        }

     stage('Deploy') {
    when { branch 'main' }
    steps {
        sh '''
        echo "Deploying to Tomcat"
        cp target/app.war /var/lib/tomcat10/webapps/
        '''
    }
}

    }
}
