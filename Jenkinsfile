pipeline {
    agent any

    stages {

        stage('Build with Maven (Docker)') {
            steps {
                sh '''
                docker run --rm \
                  -v $PWD:/app \
                  -w /app \
                  maven:3.9.6-eclipse-temurin-17 \
                  mvn clean package
                '''
            }
        }

    }

    post {
        success {
            echo 'Build Successful!'
        }
        failure {
            echo 'Build Failed!'
        }
    }
}

