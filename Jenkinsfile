pipeline {
    agent any

    // Environment variables available to all stages
    environment {
        VERSION = "1.0.5"
        APP_NAME = "StaticApp"
    }

    // Tools installation (Maven name must match Jenkins Global Tools)
    tools {
        maven "Maven_3.9"   // must match the name configured in Jenkins → Tools
    }

    stages {

        stage('Build') {
            steps {
                echo "Building version: ${VERSION} for app: ${APP_NAME}"
                sh 'mvn -version'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example: sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version: ${VERSION}"
                // Example deploy steps
            }
        }
    }

    post {
        always {
            echo 'Post build condition running'
        }
        success {
            echo 'This runs only if the build succeeded'
        }
        failure {
            echo 'Post action if build failed'
        }
        unstable {
            echo 'This runs if the build is unstable'
        }
    }
}
