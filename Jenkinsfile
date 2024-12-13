
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
                sh 'docker tag jenkinsimage toxicmoel/jenkinsimage'
                sh 'docker login -u="toxicmoel" -p="Jesuisroot123@"'
                sh 'docker push toxicmoel/jenkinsimage '
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                
            }
        }
    }
}
