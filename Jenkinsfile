pipeline {
    agent any

    // This block tells Jenkins to look for the 'docker' tool you just configured
    tools {
        dockerTool 'docker' 
    }

    environment {
        IMAGE_NAME = "my-web-app"
    }

    stages {
        stage('Build Docker Image') {
            steps {
                // Now Jenkins will know what 'docker' is
                sh "docker build -t ${IMAGE_NAME}:${BUILD_ID} ."
            }
        }
        
        stage('Test') {
            steps {
                sh "docker --version"
            }
        }
    }
}