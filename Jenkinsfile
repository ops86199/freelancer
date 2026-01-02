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
                sh 'mvn clean package'
            }
        }

        stage('Build image') {
            steps {
                sh '''
                    docker build -t myapp:latest .
                '''
            }
        }

        stage('Run container') {
            steps {
                sh '''
                    docker rm -f myapp_container || true
                    docker run -d --name myapp_container -p 8081:8080 myapp:latest
                '''
            }
        }

    }
}

