pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                curl -v -u admin:admin123 \
                --upload-file target/spring-boot-complete-0.0.1-SNAPSHOT.jar \
                http://10.17.92.44:8081/repository/homeworksix/com/example/springboot/0.0.1/spring-boot-complete-0.0.1-SNAPSHOT.jar
                '''
            }
        }
    }
}
