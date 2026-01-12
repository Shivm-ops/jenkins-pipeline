pipeline {
    agent any 

    stages {
        stage('Checkout') {
            steps {
                // This pulls your index.html and Jenkinsfile
                checkout scm
            }
        }
        stage('Quality Check') {
            steps {
                echo 'Checking if index.html exists...'
                sh 'test -f index.html'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to web server folder...'
                // This simulates deployment by copying the file
                sh 'mkdir -p ./deploy'
                sh 'cp index.html ./deploy/index.html'
            }
        }
    }
    post {
        always {
            // This saves the file in Jenkins so you can view it later
            archiveArtifacts artifacts: 'deploy/index.html', fingerprint: true
        }
    }
}