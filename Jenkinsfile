pipeline {
    agent any

    environment {
        // Define environment variables
        DOCKER_HUB_CREDENTIALS = credentials('Meshra@123')
        DOCKER_IMAGE_NAME = 'testrameshnew458/ramesh:1.0'
    }

    stages {
        stage('Build Maven Project') {
            steps {
                // Build Maven project
                sh 'mvn clean install'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image
                sh "docker build -t ${DOCKER_IMAGE_NAME} ."
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                // Log in to Docker Hub
                withCredentials([usernamePassword(credentialsId: DOCKER_HUB_CREDENTIALS, passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                    sh "docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD"
                }

                // Push Docker image to Docker Hub
                sh "docker push ${DOCKER_IMAGE_NAME}"
            }
        }
    }
}
