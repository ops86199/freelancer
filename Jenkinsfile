pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Build docker image') {
            steps {
                sh '''
                     docker build -t myapp:latest .
                '''
           }
       }
       stage('Run container') {
           steps {
               sh '''
                    docker rm -f con1 || true
                    docker run --name con1 -d -p 8081:80 myapp:latest
               '''
           }
       }
    }
}  
