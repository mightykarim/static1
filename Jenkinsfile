pipeline {
    agent any

    environment {
        JAVA_VERSION = '21'
        RUN_TESTS = 'true'
    }

    tools {
        maven 'Maven_3.9'  // <-- use the exact Maven name from Jenkins
    }

    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run the Test stage?')
    }

    stages {
        stage('Build') {
            steps {
                echo "Building with Maven ${env.MAVEN_HOME}"
                sh 'mvn -version'  // bat 'mvn -version' on Windows
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
