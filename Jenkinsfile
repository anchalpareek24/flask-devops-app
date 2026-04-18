pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bay 'docker build -t flask-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                docker stop flask-container || true
                docker rm flask-container || true
                docker run -d -p 5000:5000 --name flask-container flask-app
                '''
            }
        }
    }
}