pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-docker-ci"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                powershell 'docker build -t $env:IMAGE_NAME .'
            }
        }

        stage('Run Tests in Container') {
            steps {
                powershell 'docker run --rm $env:IMAGE_NAME'
            }
        }
    }

    post {
        always {
            powershell 'docker system prune -f'
        }
    }
}
