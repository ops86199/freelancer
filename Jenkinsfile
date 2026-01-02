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
        stage(Build image) {
            steps {
                sh '''
                     docker build -t myapp:latest .
                     docker run --name con1 -d -p 8081:80 myapp:latest
                 '''
           }
       }
    }
}  
