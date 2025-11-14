pipeline {
    agent any

    tools {
        maven 'Maven 3.9.11' // Use the name of your configured Maven version in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build & Deploy') {
            steps {
                sh 'mvn clean deploy'
            }
        }
    }

    post {
        success {
            echo '✅ Maven build and Nexus deployment completed successfully.'
        }
        failure {
            echo '❌ Build or deployment failed. Check console output for details.'
        }
    }
}
