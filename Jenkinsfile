pipeline {
    agent any

    environment {
        DOCKERHUB_USER = "nandha0408"
        IMAGE_NAME = "webstatus"
        IMAGE_TAG = "latest"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/nandhakumar04080408/docker-task-1.git'
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                  docker build -t $DOCKERHUB_USER/$IMAGE_NAME:$IMAGE_TAG .
                '''
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                      echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin
                    '''
                }
            }
        }

        stage('Push Image') {
            steps {
                sh '''
                  docker push $DOCKERHUB_USER/$IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker stop webstatus || true
                  docker rm webstatus || true
                  docker run -d --name webstatus -p 8085:3000 $DOCKERHUB_USER/$IMAGE_NAME:$IMAGE_TAG
                '''
            }
        }
    }
}

