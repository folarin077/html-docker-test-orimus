pipeline {
    agent any

    stages {
    stage('cleanup') {
            steps {
               sh 'docker stop $(docker ps -a -q)' 
            }
        }
    stage('Checkout external proj') {
        steps {
            git branch: 'main',
                url: 'https://github.com/tatahnoellimnyuy/html-docker-test.git'
        }
    }
        stage('Build') {
            steps {
               sh 'docker  build -t image2 .' 
            }
        }
        stage('push artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable:'PASSWORD')]){sh 'docker login -u $USER -p $PASSWORD'
                sh 'docker tag image2:latest toxicmoel/image2'
                sh 'docker push  toxicmoel/image2'
                    
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 8888:80 testimage'
            }
        }
    }
}