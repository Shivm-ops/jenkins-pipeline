pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-web-app"
        REGISTRY_USER = "your_dockerhub_username" // Change this
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Builds the image with a tag matching the Jenkins Build Number
                    sh "docker build -t ${IMAGE_NAME}:${BUILD_ID} ."
                }
            }
        }

        stage('Test Container') {
            steps {
                script {
                    // Run the container in detached mode to test it
                    sh "docker run -d --name test_container -p 8081:80 ${IMAGE_NAME}:${BUILD_ID}"
                    
                    // Simple curl check to see if the web server is up
                    sh "sleep 5 && curl localhost:8081"
                    
                    // Stop and remove the test container
                    sh "docker stop test_container && docker rm test_container"
                }
            }
        }

        stage('Cleanup') {
            steps {
                echo "Removing local image to save space..."
                sh "docker rmi ${IMAGE_NAME}:${BUILD_ID}"
            }
        }
    }
}