pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/javaid100/python-docker-ci-cd.git'
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }

    stage('Run Tests') {
      steps {
        sh 'pip install pytest'
        sh 'pytest tests/'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t python-ci-cd-app .'
      }
    }

    stage('Run Docker Container') {
      steps {
        sh 'docker run -d -p 5000:5000 --name python_app_container python-ci-cd-app || true'
      }
    }
  }
}
