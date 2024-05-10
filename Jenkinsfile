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
                    docker.build("testrameshnew458:0.1")
                }
            }
        }
    }
}
