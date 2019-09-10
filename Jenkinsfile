pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        echo 'Taking source checkout'
	sh 'touch /home/vagrant/build/runner.sh'
	sh 'cat > runner.sh << EOF
	./home/vagrant/build/myapp
	EOF'
      }
    }
    stage('Build') {
      steps {
        echo 'Preparing Build'
	sh 'docker run --rm -v /home/vagrant/build:/tmp/jenkins_builds -v /home/vagrant/src:/usr/src/myapp -w /usr/src/myapp gcc:4.9 gcc -o /tmp/jenkins_builds/myapp myapp.c'
      }
    }
    stage('Test_Build') {
      steps {
        echo 'Run the binary file'
	sh 'bash /home/vagrant/build/runner.sh'
      }
    }
  }
}
