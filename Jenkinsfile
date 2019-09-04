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
	sh 'docker run --rm -v /tmp/jenkins_builds:/tmp/jenkins_builds -v /home/vagrant/build:/usr/src/myapp -w /usr/src/myapp gcc:4.9 gcc -o /tmp/jenkins_builds/myapp myapp.c'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy to NA1'
	sh './tmp/jenkins_builds/myapp'
      }
    }
  }
}
