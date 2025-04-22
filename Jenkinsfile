pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/javaid100/dockerized-flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'docker run --rm flask-app pytest test_app.py'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop flask-app || true
                docker rm flask-app || true
                docker run -d -p 5000:5000 --name flask-app flask-app
                '''
            }
        }
    }
}
