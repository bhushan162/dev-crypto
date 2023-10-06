// pipeline {
//   agent any

//   stages {
//     stage('Build') {
//       steps {
//         checkout scm
//         sh 'docker build -t my-react-app .'
//         sh 'docker push my-react-app'
//       }
//     }

//     stage('Deploy') {
//       steps {
//         sh 'docker pull my-react-app'
//         sh 'docker run -d -p 80:80 my-react-app'
//       }
//     }
//   }https://github.com/bhushan162/dev-crypto


//------------------------------------------------------------------------------------------------------------------------

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
                docker.build('my-website:latest')
            }
        }

        stage('Push to Docker Hub') {
            steps {
                docker.withRegistry('https://index.docker.io/v1/', 'my-username') {
                    docker.push('my-website:latest')
                }
            }
        }

        stage('Deploy to AWS S3') {
            steps {
                aws s3 cp build s3:devcrypto
            }
        }
    }
}
