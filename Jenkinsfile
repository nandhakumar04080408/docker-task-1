pipeline {
    agent any

    environment {
        // Change these to your actual Docker Hub details
        DOCKER_USER = "nandha0408"
        IMAGE_NAME  = "webstatus"
        REGISTRY_ID = "docker"
    }

    stages {
        stage('Build') {
            steps {
                script {
                    // Builds the image using the Dockerfile we just wrote
                    customImage = docker.build("${DOCKER_USER}/${IMAGE_NAME}:${env.BUILD_ID}")

                    //Stop and remove the old container if it exists
                    sh "docker stop ${IMAGE_NAME} || true"
                    sh "docker rm ${IMAGE_NAME} || true"

                    // 2. Run the new image indefinitely in detached mode
                    // We map host port 8085 to container port 80
                    sh "docker run -d --name ${IMAGE_NAME} -p 8085:80 ${DOCKER_USER}/${IMAGE_NAME}:latest"
                }
            }
        }

        stage('Test Run') {
            steps {
                script {
                    // This runs the container, checks if port 80 is responsive, then stops it
                    customImage.withRun('-p 8081:80') { c ->
                        sh "sleep 5" // Wait for Nginx to initialize
                        sh "curl http://localhost:8081 | grep 'Online'"
                    }
                }
            }
        }

        stage('Push') {
            steps {
                script {
                    docker.withRegistry('', REGISTRY_ID) {
                        customImage.push("${env.BUILD_ID}")
                        customImage.push("latest")
                    }
                }
            }
        }

        stage('Cleanup') {
            steps {
                // Removes the local image to save disk space on your HP Victus
                sh "docker rmi ${DOCKER_USER}/${IMAGE_NAME}:${env.BUILD_ID}"
                sh "docker rmi ${DOCKER_USER}/${IMAGE_NAME}:latest"
            }
        }
    }
}
