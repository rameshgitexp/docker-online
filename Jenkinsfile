pipeline {
    agent any
    environment {
        // Define AWS region and ECR repository URL
        AWS_DEFAULT_REGION = 'ap-south-1'
        ECR_REPOSITORY = '211125669141.dkr.ecr.ap-south-1.amazonaws.com/ramesh.repo'
    }
    stages {
        stage("Maven Build") {
            steps {
                // Run Maven package command
                sh 'mvn package'
            }
        }
        stage("Build Docker Image") {
            steps {
                script {
                    docker.build("testrameshnew458:0.1")
                }
            }
        }
        stage('Docker Login') {
            steps {
                script {
                    sh 'docker login -u testrameshnew458 -p Meshra@123'
                }
            }
        }
        stage('Push Docker Image to ECR') {
            steps {
                script {
                    // Tag the built image with ECR repository URL and 'latest' tag
                    docker.image("testrameshnew458:0.1").tag("${ECR_REPOSITORY}:latest")
                    // Push the tagged image to ECR repository
                    docker.image(docker tag ramesh.repo:latest 211125669141.dkr.ecr.ap-south-1.amazonaws.com/ramesh.repo:latest).push()
                }
            }
        }
    }
}
