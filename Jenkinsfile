pipeline {
    agent any

    environment {
        JAVA_VERSION = '21'
        MAVEN_VERSION = '3.9.2'
    }

    tools {
        maven 'Maven 3.9.2'
    }

    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the Test stage?')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building with Java ${env.JAVA_VERSION} and Maven ${env.MAVEN_VERSION}"
                sh 'mvn -version'   // Use 'bat' on Windows
            }
        }

        stage('Test') {
            when {
                expression { params.executeTests }
            }
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying project...'
            }
        }
    }

    post {
        always {
            echo 'Post build actions running'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
