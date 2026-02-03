pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                echo 'Code already cloned by Jenkins'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-nginx-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop nginx-demo || true
                docker rm nginx-demo || true
                docker run -d -p 8081:80 --name nginx-demo jenkins-nginx-demo
                '''
            }
        }
    }
}
