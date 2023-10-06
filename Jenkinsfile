pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
        checkout scm
        sh 'docker build -t my-react-app .'
        sh 'docker push my-react-app'
      }
    }

    stage('Deploy') {
      steps {
        sh 'docker pull my-react-app'
        sh 'docker run -d -p 80:80 my-react-app'
      }
    }
  }
}
