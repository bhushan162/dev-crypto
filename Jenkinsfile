pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Dockerize') {
            steps {
                script {
                    docker.build('my-website:latest', '-f path/to/Dockerfile .')
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', 'my-username') {
                        docker.push('my-website:latest')
                    }
                }
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                script {
                    sh 'aws s3 cp -r build/ s3://my-website/'
                }
            }
        }
    }
}
