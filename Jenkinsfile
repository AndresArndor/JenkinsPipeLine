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
	sh 'docker run --rm -v /home/vagrant/build:/usr/src/myapp -w /usr/src/myapp gcc:4.9 gcc -o myapp myapp.c'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy to production'
        input(message: 'Deploy to QA', id: 'qa', ok: 'Deploy', submitter: 'sree', submitterParameter: 'Deploy')
        waitUntil() {
          echo 'Deploy to QA'
	  sh 'mv /home/vagrant/build/myapp /home/vagrant/binary'
        }

      }
    }
    stage('Deploy To NA1') {
      steps {
        input(message: 'Deploy to NA1', id: 'na1', ok: 'Deploy To NA1', submitter: 'sree', submitterParameter: 'NA1')
        echo 'Deploy to NA1'
	sh './home/vagrant/binary/myapp'
      }
    }
  }
}
