
pipeline {
    agent any

    stages {

        stage('Checkout Source Code') {
            steps {
                echo 'Retrieving source code from GitHub'
            }
        }

        stage('Build Application') {
            steps {
                echo 'Building REST API application'
                bat 'mvnw.cmd clean compile'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Executing unit tests'
                bat 'mvnw.cmd test'
            }
        }

        stage('Package Application') {
            steps {
                echo 'Packaging REST API application'
                bat 'mvnw.cmd package -DskipTests'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving generated JAR files'
                archiveArtifacts artifacts: 'target/*.jar',
                                 fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'REST API pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
        always {
            echo 'Pipeline execution completed.'
        }
    }
}
