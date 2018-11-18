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
        input(message: 'Deploy to QA', id: 'qa', ok: 'Deploy', submitter: 'sree', submitterParameter: 'Deploy')
      }
    }
    stage('Deploy To NA1') {
      steps {
        input(message: 'Deploy to NA1', id: 'na1', ok: 'Deploy To NA1', submitter: 'sree', submitterParameter: 'NA1')
        echo 'Deploy to NA1'
      }
    }
  }
}