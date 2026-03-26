pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "chittulurinaveen/node-calculator:v1"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/ChittuluriNaveen/node-calculator.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }

    }
}
