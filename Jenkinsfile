pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from the repository
                git credentialsId: 'your-git-credentials', url: 'https://github.com/yourusername/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                // Build the Node.js application
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Dockerize') {
            steps {
                // Create a Docker image
                script {
                    def dockerImage = docker.build('your-docker-image-name:latest', '.')
                }
            }
        }

        stage('Push to Docker Registry') {
            steps {
                // Push the Docker image to a registry (e.g., Docker Hub)
                script {
                    docker.withRegistry('https://registry.example.com', 'your-docker-hub-credentials') {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}
