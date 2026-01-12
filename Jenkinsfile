pipeline {
    agent any 

    stages {
        stage('Fetch Code') {
            steps {
                echo 'Checking out code from Git...'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'uptime'
            }
        }
        stage('Finish') {
            steps {
                echo 'Pipeline completed successfully!'
            }
        }
    }
}