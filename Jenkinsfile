pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/fulldrill/resumesitemac.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t resume-app:latest ./app'
            }
        }

      stage('Run Container') {
            steps {
                sh '''
                docker rm -f resume-app || true
                docker run -d -P --name resume-app resume-app:latest
                '''
            }
        }

    }
}