pipeline {
    agent any
    stages {
        stage('Majdi') {
            steps {
                git branch: 'main', credentialsId: '6f8cfc13-6914-4410-bf35-0b0fc254d08a', url: 'https://github.com/khalilshahin01/orange.git'
            }
        }
        stage('Khalil') {
            steps {
                sh 'docker build -t khalilshahin01/image-from-jenkins:v1 .'
            }
        }
        
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'DockerHub') {
                        docker.image('khalilshahin01/image-from-jenkins:v1').push()
                    }
                }
            }
        }
        
        stage('Omar') {
            steps {
                sh 'echo done image creation'
            }
        }
    }
}

