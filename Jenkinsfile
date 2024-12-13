
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example build command
                sh 'docker build -t jenkinsimage .'
            }
        }
        stage('push') {
            steps {
                echo 'Running push...'
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                
            }
        }
    }
}
