pipeline {
    agent none

    environment {
        IMAGE_NAME = "devops-app"
    }

    stages {

        stage('Checkout') {
            agent any
            steps {
                git branch: 'main',
                    url: 'https://github.com/NessX4/devops-ci-cd-app.git'
            }
        }

        stage('Build & Test') {
            agent {
                docker {
                    image 'maven:3.9.6-eclipse-temurin-17'
                }
            }
            steps {
                sh 'mvn clean verify'
            }
        }

        stage('Archive Artifact') {
            agent any
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Build Docker Image') {
            agent any
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }
    }

    post {
        success {
            echo 'CI/CD Pipeline Successful!'
        }
        failure {
            echo 'Pipeline Failed!'
        }
    }
}

