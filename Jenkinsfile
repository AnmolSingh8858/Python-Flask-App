pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-ci-cd-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop flask-app || true
                docker rm flask-app || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name flask-app -p 5000:5000 flask-ci-cd-app'
            }
        }
    }
}
