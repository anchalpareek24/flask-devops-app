pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-project .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop flask-container || true
                docker rm flask-container || true
                docker run -d -p 5000:5000 --name flask-container my-project
                '''
            }
        }
    }
}