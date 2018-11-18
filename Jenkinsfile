pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Taking source checkout'
      }
    }
    stage('Build') {
      steps {
        echo 'Preparing Build'
        input(message: 'Deploy', id: 'deploy', ok: 'OK')
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy to production'
      }
    }
  }
  environment {
    mvnHome = ''
  }
}