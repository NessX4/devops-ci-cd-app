pipeline {
    agent any

    stages {

        stage('Build with Maven (Docker)') {
            steps {
                sh '''
                WORKSPACE_DIR=$(pwd)
                docker run --rm \
                -v "$WORKSPACE_DIR":/app \
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

