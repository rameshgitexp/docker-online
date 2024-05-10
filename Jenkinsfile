pipeline {
    agent any
    environment {
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
            stages {
        stage('Docker Login') {
            steps {
                script {
                        sh "docker login -u ${testrameshnew458} -p ${} ${https://hub.docker.com/u/testrameshnew458}"
                    }
                }
        }
    }
}
