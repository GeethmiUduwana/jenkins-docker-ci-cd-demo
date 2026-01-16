pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/GeethmiUduwana/jenkins-docker-ci-cd-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ci-cd-demo:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop ci-cd-demo || true
                docker rm ci-cd-demo || true
                docker run -d -p 8081:80 --name ci-cd-demo ci-cd-demo:latest
                '''
            }
        }
    }
}
