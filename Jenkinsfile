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
                sh '/usr/bin/docker build -t image-from-jenkins:v1 .'
            }
        }
        stage('Omar') {
            steps {
                sh 'echo done image creation'
            }
        }
    }
}

