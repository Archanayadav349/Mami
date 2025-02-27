pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from version control
                git branch: 'main', url: 'https://github.com/Archanayadav349/Mami.git'
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    sh 'docker build -t my-nginx-app .'
                }
            }
        }
        
        stage('Run Container') {
            steps {
                script {
                    // Stop and remove existing container if it exists
                    sh 'docker rm -f my-nginx-container || true'
                    
                    // Run the new container
                    sh 'docker run -d -p 80:80 --name my-nginx-container my-nginx-app'
                }
            }
        }
        
        stage('Verify') {
            steps {
                // Simple verification that container is running
                sh 'docker ps | grep my-nginx-container'
            }
        }
    }
}
