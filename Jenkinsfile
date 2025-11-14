pipeline {
    agent any

    environment {
        MAVEN_HOME = tool 'Maven 3.9.11' // Adjust to match your Jenkins Maven tool name
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'jenkins-ssh-key',
                    url: 'git@github.com:Zapstremon/my-gs-spring-boot.git'
            }
        }

        stage('Build') {
            steps {
                sh "${MAVEN_HOME}/bin/mvn clean package"
            }
        }

        stage('Upload to Nexus') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'nexus-cred-id', usernameVariable: 'NEXUS_USER', passwordVariable: 'NEXUS_PASS')]) {
                    sh '''
                        curl -u $NEXUS_USER:$NEXUS_PASS \
                        --upload-file target/my-gs-spring-boot-0.0.1-SNAPSHOT.jar \
                        http://10.17.92.44:8081/repository/homeworksix/my-gs-spring-boot-0.0.1-SNAPSHOT.jar
                    '''
                }
            }
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}
