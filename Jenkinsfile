pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/PrajwalKesargoppa2457/Hotel-Management-System'


 // Replace with your repo URL or local repo path
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hotel-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name hotel-app-container hotel-app || true'
            }
        }

        stage('Selenium Test') {
            steps {
                sh 'python3 test_homepage.py'
            }
        }

        stage('Cleanup') {
            steps {
                sh 'docker stop hotel-app-container || true'
                sh 'docker rm hotel-app-container || true'
            }
        }
    }
}
