pipeline {
    agent any
    stages {
        stage('CheckOut') {
            steps {
                git branch: 'main', credentialsId: '6f8cfc13-6914-4410-bf35-0b0fc254d08a', url: 'https://github.com/khalilshahin01/orange.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t khalilshahin01/image-from-jenkins:${BUILD_NUMBER} .'
            }
        }
        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'DockerHub') {
                        docker.image('khalilshahin01/image-from-jenkins:${BUILD_NUMBER}').push()
                    }
                }
            }
        }
        
        stage('Build to Kubernetes') {
            steps {
                sh "kubectl apply -f . --kubeconfig KubeConfig"
            }
        }
    }
}
