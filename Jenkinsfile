pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "chittulurinaveen/node-calculator:v1"
        CONTAINER_NAME = "calc-container"
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

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d -p 3000:3000 --name $CONTAINER_NAME $DOCKER_IMAGE
                '''
            }
        }

    }
}
