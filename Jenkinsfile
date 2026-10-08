pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Deeksha-03120/PersonalProfile.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '"C:\\Users\\SENTHIL\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" build -t Deeksha-03120/personal-profile:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat '"C:\\Users\\SENTHIL\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin\\docker.exe" push Deeksha-03120/personal-profile:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get svc'
            }
        }
    }
}