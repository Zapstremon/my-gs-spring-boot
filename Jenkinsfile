pipeline {
    agent any

    tools {
        maven 'Maven 3.8.6' // Replace with your configured Maven version name in Jenkins
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
            echo '✅ Build and deployment to Nexus completed successfully.'
        }
        failure {
            echo '❌ Build or deployment failed. Check console output for details.'
        }
    }
}
