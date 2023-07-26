pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control system (e.g., Git)
                // For example:
                // git 'https://github.com/your/repo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build the Docker image using the Dockerfile in the repository root
                script {
                    docker.withRegistry('https://registry.example.com', 'docker_credentials_id') {
                        def dockerImage = docker.build("image-from-jenkins:v1")
                        dockerImage.push()
                    }
                }
            }
        }
    }
}

