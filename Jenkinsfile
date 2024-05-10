pipeline {
    agent any
    stages {
        stage("Maven Build") {
            steps {
                sh 'mvn package'
            }
        }
        stage("Build Docker Image") {
            steps {
                script {
                    // Use the Docker Pipeline syntax to build the Docker image
                    docker.build("ram/apache:2.0")
                }
            }
        }
    }
}
