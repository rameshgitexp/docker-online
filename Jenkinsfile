pipeline {
    agent any
    
    environment {
        // Define environment variables here if needed
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
                // Build Docker image using the Docker Pipeline plugin
                script {
                    // Replace 'testrameshnew458:0.1' with your desired image name and tag
                    docker.build("testrameshnew458:0.1")
                }
            }
        }
    }
    
    post {
        success {
            // Actions to perform after a successful build
            // For example, Docker login
            stage('Docker Login') {
                steps {
                    script {
                        // Perform Docker login
                        // Replace 'testrameshnew458' and 'Meshra@123' with your Docker username and password
                        sh 'docker login -u testrameshnew458 -p Meshra@123'
                    }
                }
            }
        }
    }
}
