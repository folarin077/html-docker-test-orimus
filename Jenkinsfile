
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example build command
                sh 'docker build --no-cache -t jenkinsimage  .'
            }
        }
        stage('push') {
            steps {
                echo 'Running push...'
                sh 'docker tag jenkinsimage folarin077/jenkinsimage:${BUILD_ID}'
                sh 'docker login -u="folarin077" -p="Gunnerfemi!23"'
                sh 'docker push folarin077/jenkinsimage:${BUILD_ID} '
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                
                sh 'ssh -o StrictHostKeyChecking=no -i "../yellow.pem" ec2-user@ec2-18-130-203-29.eu-west-2.compute.amazonaws.com -t "docker ps -aq | xargs docker rm -f; docker run -p 80:80 -d folarin077/jenkinsimage:${BUILD_ID}"'
                
            }
        }
    }
}
