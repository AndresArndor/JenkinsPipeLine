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
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy to production'
        input(message: 'Deploy to QA', id: 'qa', ok: 'Deploy', submitter: 'Sree', submitterParameter: 'Deploy')
      }
    }
  }
  environment {
    mvnHome = ''
  }
}