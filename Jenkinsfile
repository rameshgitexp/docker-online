pipeline {
    agent any
  
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
        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub_credentials') {
                        docker.image("testrameshnew458:0.1").push()
                    }
                }
            }
        }
    }
}
