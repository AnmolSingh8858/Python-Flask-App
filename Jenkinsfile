pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-ci-cd-app .'
            }
        }

        stage('Cleanup Old Containers') {
            steps {
                sh '''
                docker ps -aq --filter "name=flask-app" | xargs -r docker stop
                docker ps -aq --filter "name=flask-app" | xargs -r docker rm
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --restart always --name flask-app -p 5000:5000 flask-ci-cd-app'
            }
        }
    }
}
