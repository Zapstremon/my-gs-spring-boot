pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Upload to Nexus') {
            steps {
                sh '''
                curl -v -u admin:admin123 \
                --upload-file target/helloworld-1.0.0.jar \
                http://10.17.92.44:8081/repository/homeworksix/com/example/helloworld/1.0.0/helloworld-1.0.0.jar
                '''
            }
        }
    }
}
